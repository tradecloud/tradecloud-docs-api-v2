---
description: >-
  Choose between delivery schedule or single delivery per order line.
---

# Receive a delivery schedule

## Delivery schedule versus single delivery

Tradecloud works with a delivery schedule per order line.
Each delivery line in a schedule consists of a position, delivery date and a quantity.

Some ERP systems like SAP work natively with multiple delivery lines per order line.
Use [**delivery schedule**](#delivery-schedule) in this case.

Other ERP systems can only work with only one delivery per order line.
Use [**single delivery**](#single-delivery) in this case.

## Delivery schedule

The default is to receive a delivery schedule. The "Orders Webhook Integration" setting "My system supports" must be set to the default "**Multiple deliveries per order line**".

Use the `orderEvent` field of the [POST order webhook](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-connector/specs.yaml#/order-webhook%20endpoints/webhookPost) endpoint.

The field `lines.deliverySchedule` contains the current delivery schedule of this order line.

### `deliverySchedule` fields

* `position`: the position in the delivery schedule. Not to be confused with the `lines.position`.

{% hint style="warning" %}
The `position` may be unassigned in case of a delivery line split by a supplier. The buyer ERP system must assign a position to the split delivery line and update the order line to Tradecloud.
{% endhint %}

* `date`: the requested delivery date of this delivery schedule position. Date has ISO 8601 date `yyyy-MM-dd` format. See also [Standards](../../api/standards.md).
* `quantity`: the requested quantity of this delivery schedule position. Quantity has a decimal `1234.56` format with any number of digits.
* `status`: The [logistics status](#logistics-status) of this delivery line according to the buyer.
* `transportMode`: The Mode of Transport used for the delivery of goods as required by the buyer. [UNECE.org Recommendation 19](https://tfig.unece.org/contents/recommendation-19.htm) is advised for Codes for Modes of Transport.

## Single delivery

To receive a single delivery per order line you must have the "Orders Webhook Integration" setting "My system supports" set to "**Only one single delivery per order line**".

Use the `singleDeliveryOrderEvent` field of the [POST order webhook](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-connector/specs.yaml#/order-webhook%20endpoints/webhookPost) endpoint.

The field `lines.scheduledDelivery` contains the current delivery line of this order line.

{% hint style="info" %}
Tradecloud will expand a delivery schedule into order lines with the same item number. The `deliverySchedule.position` will be taken as `lines.position`.
{% endhint %}

{% hint style="warning" %}
The order line `position` may be unassigned in case of an order line split by a supplier. The ERP system must assign a position to the split order line and update the order line to Tradecloud.
{% endhint %}

{% hint style="warning" %}
The single delivery per order line is supported by the POST webhook API and polling API, but not supported by the GET webhook API.
{% endhint %}

### `scheduledDelivery` fields

* `date`: the requested delivery date of this order line. Date has ISO 8601 date `yyyy-MM-dd` format. See also [Standards](../../api/standards.md).
* `quantity`: the requested quantity of this order line. Quantity has a decimal `1234.56` format with any number of digits.
* `status`: The [logistics status](#logistics-status) of this scheduled delivery according to the buyer.
* `transportMode`: The Mode of Transport used for the delivery of goods as required by the buyer. [UNECE.org Recommendation 19](https://tfig.unece.org/contents/recommendation-19.htm) is advised for Codes for Modes of Transport.

## Logistics status

The logistics status is one of:

* `Open`: no or partial quantity Produced, ReadyToShip, Shipped or Delivered
* `Produced`: the delivery line quantity is produced by the supplier
* `ReadyToShip`: the delivery line quantity is ready to be shipped by the supplier
* `Shipped`: the delivery line quantity is shipped by the supplier
* `Delivered`: the delivery line quantity is delivered at the buyer
