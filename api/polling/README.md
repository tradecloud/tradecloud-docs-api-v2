---
description: >-
  Implementation guide for the polling pattern in Tradecloud API v2
---

# Polling pattern implementation guide

The polling API offers an alternative to the webhook API for retrieving order or shipment updates. Both approaches have different advantages and considerations:

{% page-ref page="../webhook-vs-polling.md" %}

## Overview

The polling pattern consists of three essential steps:

1. **Fetch** - Retrieve orders or shipments changed since the last poll
2. **Process** - Handle the retrieved new or updated data
3. **Persist** - Store the latest timestamp for the next polling cycle

## Implementation steps

### Step 1: Fetch updated data periodically

Set up a scheduled process to fetch all orders or shipments that have been created or changed since your last poll.

#### Polling best practices

- Use a consistent polling interval (typically 5 minutes)
- Include the `lastUpdatedAt` timestamp from previous poll response as the `lastUpdatedAfter` filter
  - **Do not use the current time** (system clock) for `lastUpdatedAfter`
- Set `limit=100` (the maximum allowed value) to control response size
- Handle pagination when needed:
  - If response contains `total` > 100, not all updates were returned
  - Either decrease the polling period (recommended) or use `offset` parameter for paging

#### Available endpoints

| Data Type                  | Endpoint                                                                                                                                                                            | Use Case                                   |
| -------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------ |
| Orders (delivery schedule) | [Poll orders](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-search/specs.yaml#/order-search/pollOrdersRoute)                               | For orders using delivery schedule feature |
| Orders (single delivery)   | [Poll single delivery orders](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-search/specs.yaml#/order-search/pollOrdersSingleDeliveryRoute) | For orders using single delivery per line  |
| Shipments                  | [Poll shipments](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/shipment/specs.yaml#/shipment/pollShipmentsRoute)                                 | For shipment updates                       |

#### Example request

```http
GET /v2/order-search/poll

{
  "filters": {
    "lastUpdatedAfter": "2025-04-23T10:01:53.812Z"
  },
  "limit": 100
}
```

#### Buyer: filter on Confirmed orders

Optionally, the buyer can filter on Confirmed orders and ignore orders with other statuses.

```http
GET /v2/order-search/poll

{
  "filters": {
    "processStatus": ["Confirmed"],
    "lastUpdatedAfter": "2025-04-23T10:01:53.812Z"
  },
  "limit": 100
}
```

The buyer will only receive confirmed orders when **all lines are confirmed**. The buyer may still receive order lines with different process or logistics statuses, such as Cancelled or Delivered. The status fields in the response can be used to filter order lines accordingly.

#### Suppliers: filter on Issued orders

Optionally, the supplier can filter on Issued orders and ignore orders with other statuses.

```http
GET /v2/order-search/poll

{
  "filters": {
    "processStatus": ["Issued"],
    "lastUpdatedAfter": "2025-04-23T10:01:53.812Z"
  },
  "limit": 100
}
```

The supplier may still receive **Issued orders that have been updated** by the buyer. Check if the order already exists and either ignore the update or update the existing order.

### Step 2: Process retrieved data

Implement logic to handle the fetched new or updated orders or shipments.

#### Example response

```http
{
  "data": [
    {
      "supplierAccountNumber": "SUPPLIER12345",
      "purchaseOrderNumber": "PO123456789",
      "lines": [
        {
          "deliverySchedule" ...
          "prices" ...
          "status": {
            "processStatus": "Issued",
            "logisticsStatus": "Open"
          },
          "lastUpdatedAt": "2025-04-23T10:01:53.812Z"
        }
      ],
      "status": {
        "processStatus": "Issued",
        "logisticsStatus": "Open"
      },
      "lastUpdatedAt": "2025-04-23T10:01:53.812Z"
    }
  ],
  "total": 10,
  "lastUpdatedAt": "2025-04-23T10:01:53.812Z"
}
```

{% hint style="warning" %}
Your poll results may include outdated data in case of a request. See [Polling Echo Handling](echo.md) for managing outdated data.
{% endhint %}

#### Order processing tips

When working with order endpoints:

- The supplier must check if the order already exists and either ignore the update or update the existing order
- Use `data.lines.lastUpdatedAt` to identify which specific lines changed since the `lastUpdatedAfter` time you provided.
- Filter by order and line status using `data.status` and `data.lines.status` fields:
  - `processStatus`
  - `inProgressStatus`
  - `logisticsStatus`
  - `deliveryLineStatus`

#### Shipment processing tips

When working with shipment endpoint:

- Use `data.lines.meta.lastUpdatedAt` to identify changed shipment lines since the `lastUpdatedAfter` time you provided.
- Filter by `data.status` to focus on relevant shipment statuses

### Step 3: Persist the timestamp

Store the `lastUpdatedAt` value to use as `lastUpdatedAfter` in subsequent requests.

When the poll response is empty, keep using the same timestamp until you get results.

#### Implementation tips

- The timestamp has format `YYYY-MM-DDThh:mm:ss.SSSZ` (ISO 8601)
- The `Z` timezone indicator must be persisted and applied in the next polling request
- Persisting **the complete timestamp as a string** is recommended to avoid timezone conversion issues
- Store this in **persistent storage** (database or file system)
- Your storage solution **must survive application restarts or crashes**
- If the response contains no data, reuse your current `lastUpdatedAfter` value
- For first-time polling, use a well chosen historical date to fetch or skip existing orders
