---
description: >-
  Choose between delivery schedule or single delivery per order line
---

# Send a Delivery Schedule

## Delivery Methods Overview

Tradecloud supports two delivery methods for order lines:

1. **Delivery schedule** - multiple deliveries per order line
2. **Single delivery** - one delivery per order line (currently only available for buyers)

Each delivery contains a position number, delivery date, and quantity.

Some ERP systems like SAP natively support multiple deliveries per order line, while others only support one delivery per order line.

## Delivery Schedule

Use the [Send order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderByBuyerRoute) endpoint with the delivery schedule specified in the `lines.deliverySchedule` field.

You can include multiple delivery lines, up to a maximum of 100 lines per order line.

### `deliverySchedule` Fields

- `position`: Position number in the delivery schedule (distinct from `lines.position`)

{% hint style="warning" %}
The `position` must be unique within the delivery schedule and should never change. Never renumber or reuse a `position` value.
{% endhint %}

- `date`: Requested delivery date (ISO 8601 format `yyyy-MM-dd`)
- `quantity`: Requested quantity (decimal format, e.g. `1234.56`)
- `status`: [Logistics status](#logistics-status) of this delivery line
- `transportMode`: Required mode of transport for goods delivery. We recommend using [UNECE.org Recommendation 19](https://tfig.unece.org/contents/recommendation-19.htm) codes.

## Single Delivery

Use the [Send single delivery order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendSingleDeliveryOrderByBuyerRoute) endpoint with delivery details in the `lines.scheduledDelivery` field.

Provide only one `scheduledDelivery` per order line, with a maximum of 100 deliveries per item number across all order lines.

{% hint style="info" %}
When order lines contain an `originalPosition` reference, Tradecloud automatically merges their `scheduledDelivery` and `actualDelivery` properties into the delivery schedule of the line with the matching position number.
{% endhint %}

### `scheduledDelivery` Fields

- `date`: Requested delivery date (ISO 8601 format `yyyy-MM-dd`)
- `quantity`: Requested quantity (decimal format, e.g. `1234.56`)
- `status`: [Logistics status](#logistics-status) of this scheduled delivery
- `transportMode`: Required mode of transport for goods delivery. We recommend using [UNECE.org Recommendation 19](https://tfig.unece.org/contents/recommendation-19.htm) codes.

## Logistics Status

The logistics status can be one of:

- `ReadyToShip`: The full delivery line quantity is ready for shipment by the supplier
- `Shipped`: The full delivery line quantity has been shipped by the supplier
- `Delivered`: The full delivery line quantity has been delivered to the buyer
