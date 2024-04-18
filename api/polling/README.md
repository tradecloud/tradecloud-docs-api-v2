---
description: >-
  How to use the polling pattern.
---

# Polling usage

The polling API is an alternative for the webhook API. The pro's and cons are explained in:

{% page-ref page="../webhook-vs-polling.md" %}

This page explains the polling pattern usage, which consists of 3 steps:

1. Fetch the orders or shipments which are changed after last time.
2. Process the fetched, either new or updated, orders or shipments.
3. Persist the latest `data.lastUpdatedAt`.

## Step 1. Fetch updated orders or shipments periodically

Every polling period, fetch all orders or shipments which are new or changed after last time. A polling period is typically 5 minutes.

* Use the latest `data.lastUpdatedAt` from previous poll request in the `lastUpdatedAfter` filter.
* Sorting is set to `data.lastUpdatedAt` (`asc`) by default when the `lastUpdatedAfter` filter is applied. The last updated order or shipment will be ordered last in the response body.
* Set `limit` to the maximum of `100` orders or shipments.
* If the response body contains a `total` of more than `100`, it means that not all recently updated orders or shipments were returned. You can either:
  * Decrease the polling period (advised)
  * Use `offset` for paging, to receive the next 100 orders or shipments.

Use the [Poll orders](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-search/specs.yaml#/order-search/pollOrdersRoute) endpoint for polling orders.

Use the [Poll shipments](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/shipment/specs.yaml#/shipment/pollShipmentsRoute) endpoint for polling shipments.

## Step 2. Process the orders or shipments in the search response body

Process the fetched new or updated orders or shipments.

{% hint style="warning" %}
You may receive any order or shipment change, including echoed changes from your ERP system. How to handle your own open request is explained in [Polling echo](echo.md).
{% endhint %}

When using the [Poll orders](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-search/specs.yaml#/order-search/pollOrdersRoute) endpoint:

* Optionally use the `data.lines.lastUpdatedAt` field to filter the order lines that have been changed: Only consider lines where `lines.lastUpdatedAt` is after the `lastUpdatedAfter` filter value.
* Optionally use the `data.lines.status` fields to filter the order lines on `processStatus`, `inProgressStatus`, `logisticsStatus` and `deliveryLineStatus` fields.

When using the [Poll shipments](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/shipment/specs.yaml#/shipment/pollShipmentsRoute) endpoint:

* Optionally use the `data.lines.meta.lastUpdatedAt` to filter the shipment lines that have been changed.
* Optionally use the `data.status` field to filter on shipment process and logistics status sub fields.

## Step 3. Persist the `lastUpdatedAt` for the next polling request

Persist the **latest** \(in the last order or shipment in the response body\) `lastUpdatedAt` to be used as `lastUpdatedAfter` in the next polling request.

* `lastUpdatedAt` has type `String` with format `YYYY-MM-DDThh:mm:ss.SSSZ`, but to keep it simple just store it as a `String`.
* The latest `lastUpdatedAt` should be stored **persistent**. When your integration is restarted or crashes, `lastUpdatedAt` should still be available.
* If there is no data in the response body, use the same `lastUpdatedAfter` again in the next polling request.
* In the very first polling request, set the `lastUpdatedAfter` to a date in the past from which you want to receive existing orders or shipments.
