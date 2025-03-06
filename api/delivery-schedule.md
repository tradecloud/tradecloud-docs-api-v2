---
description: >-
  Choose between delivery schedule or single delivery per order line.
---

# Delivery Schedule versus Single Delivery

Tradecloud supports two delivery methods for order lines:

1. Delivery schedule - multiple deliveries per order line
2. Single delivery - one delivery per order line

## Delivery Schedule

The delivery schedule is the default method, where each order line can have multiple delivery lines. Each delivery line contains a position number, delivery date, and quantity.

Some ERP systems like SAP natively support multiple deliveries per order line, while others only support one delivery per order line.

### Sending an Order with a Delivery Schedule

Use the [Send order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderByBuyerRoute) endpoint with the delivery schedule specified in the `lines.deliverySchedule` field.

### Receiving an Order Response with a Delivery Schedule

There are two methods to receive order responses:

#### Method 1: Order Webhook (Push)

- Ensure your "Orders Webhook Integration" setting has "My system supports" set to "**Multiple deliveries per order line**" (this is the default)
- Process the `orderEvent` field in the [order webhook payload](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-connector/specs.yaml#/order-webhook%20endpoints/webhookPost)

#### Method 2: Polling (Pull)

Use the [Poll orders](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-search/specs.yaml#/order-search/pollOrdersRoute) endpoint to periodically check for updates.

With either method, the current delivery schedule will be in the `lines.deliverySchedule` field.

### `deliverySchedule` Fields

- `position`: Position number in the delivery schedule (distinct from `lines.position`)

{% hint style="warning" %}
When a supplier splits a delivery line, the `position` may be unassigned. The buyer's ERP system must assign a position to the split delivery line and update the order line in Tradecloud.
{% endhint %}

- `date`: Requested delivery date (ISO 8601 format `yyyy-MM-dd`)
- `quantity`: Requested quantity (decimal format, e.g. `1234.56`)
- `status`: [Logistics status](#logistics-status) of this delivery line according to the buyer
- `transportMode`: Required mode of transport for goods delivery. We recommend using [UNECE.org Recommendation 19](https://tfig.unece.org/contents/recommendation-19.htm) codes.

## Single Delivery

The single delivery method allows only one delivery per order line.

### Sending an Order with Single Delivery

Use the [Send single delivery order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendSingleDeliveryOrderByBuyerRoute) endpoint with delivery details in the `lines.scheduledDelivery` field.

{% hint style="info" %}
When order lines contain an `originalPosition` reference, Tradecloud automatically merges their `scheduledDelivery` and `actualDelivery` properties into the delivery schedule of the line with the matching position number.
{% endhint %}
### Receiving an Order Response with Single Delivery

There are two methods to receive order responses:

#### Method 1: Order Webhook (Push)

- Set your "Orders Webhook Integration" setting "My system supports" to "**Only one single delivery per order line**"
- Process the `singleDeliveryOrderEvent` field in the [order webhook payload](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-connector/specs.yaml#/order-webhook%20endpoints/webhookPost)

#### Method 2: Polling (Pull)

Use the [Poll single delivery orders](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-search/specs.yaml#/order-search/pollOrdersSingleDeliveryRoute) endpoint to periodically check for updates.

With either method, the current delivery information will be in the `lines.statusLine.scheduledDelivery` field.

{% hint style="warning" %}
When a supplier splits an order line, the `position` may be unassigned. The ERP system must assign a position to the split order line and update it in Tradecloud.
{% endhint %}

{% hint style="info" %}
When converting from delivery schedules to single deliveries, Tradecloud automatically splits each delivery line into a separate order line. Each order line contains one `lines.statusLine.scheduledDelivery` and maintains the relationship to the original order line through the `originalPosition` value.
{% endhint %}

### `scheduledDelivery` Fields

- `date`: Requested delivery date (ISO 8601 format `yyyy-MM-dd`)
- `quantity`: Requested quantity (decimal format, e.g. `1234.56`)
- `status`: [Logistics status](#logistics-status) of this scheduled delivery according to the buyer
- `transportMode`: Required mode of transport for goods delivery. We recommend using [UNECE.org Recommendation 19](https://tfig.unece.org/contents/recommendation-19.htm) codes.

## Logistics Status

The logistics status can be one of:

- `Open`: No quantity or only partial quantity has been Produced, ReadyToShip, Shipped or Delivered
- `Produced`: The full delivery line quantity has been produced by the supplier
- `ReadyToShip`: The full delivery line quantity is ready for shipment by the supplier
- `Shipped`: The full delivery line quantity has been shipped by the supplier
- `Delivered`: The full delivery line quantity has been delivered to the buyer
