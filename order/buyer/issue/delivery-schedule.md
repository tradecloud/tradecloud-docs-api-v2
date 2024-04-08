---
description: >-
  Choose between delivery schedule or single delivery per order line
---

# Send a delivery schedule

## Delivery schedule versus single delivery

Tradecloud works with a delivery schedule per order line.
Each delivery line in a schedule consists of a position, delivery date and a quantity.

Some ERP systems like SAP work natively with multiple delivery lines per order line.
Use the [delivery schedule](#delivery-schedule) in this case.

Other ERP systems can only work with only one delivery per order line.
Use the [single delivery](#single-delivery) in this case.

Sending a single delivery per order line is only available for buyers at this moment.

## Delivery schedule

Use the field `lines.deliverySchedule` to issue the requested planned delivery schedule of this order line. 

Provide at least one or multiple delivery schedule lines. The total number of delivery lines is limited to 100 lines per order line.

Use the [Send order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderByBuyerRoute) endpoint.

### `deliverySchedule` fields

* `position`: the mandatory position in the delivery schedule. Not to be confused with the `lines.position`.

{% hint style="warning" %}
The `position` must be unique within the delivery schedule and never change. Never renumber or re-use a `position`.
{% endhint %}

* `date`: the requested delivery date of this delivery schedule position. Date has ISO 8601 date `yyyy-MM-dd` format. See also [Standards](../../api/standards.md).
* `quantity`: the requested quantity of this delivery schedule position. Quantity has a decimal `1234.56` format with any number of digits.
* `status`: The [logistics status](#logistics-status) of this delivery line according to the buyer.
* `transportMode`: The Mode of Transport used for the delivery of goods as required by the buyer. [UNECE.org Recommendation 19](https://tfig.unece.org/contents/recommendation-19.htm) is advised for Codes for Modes of Transport.

## Single delivery

Use the field `lines.scheduledDelivery` to issue the requested planned delivery of this order line.

Provide only one single `scheduledDelivery` per order line. The total number of `scheduledDelivery`'s is limited to 100 deliveries per item number.

Use the [Send single delivery order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendSingleDeliveryByBuyerRoute) endpoint.

{% hint style="info" %}
Tradecloud will merge `scheduledDelivery`'s of order lines with the same item number into one order line having a delivery schedule. The `lines.position` will be taken as `deliverySchedule.position`.
{% endhint %}

### `scheduledDelivery` fields

* `date`: the requested delivery date of this order line. Date has ISO 8601 date `yyyy-MM-dd` format. See also [Standards](../../api/standards.md).
* `quantity`: the requested quantity of this order line. Quantity has a decimal `1234.56` format with any number of digits.
* `status`: The [logistics status](#logistics-status) of this scheduled delivery according to the buyer.
* `transportMode`: The Mode of Transport used for the delivery of goods as required by the buyer. [UNECE.org Recommendation 19](https://tfig.unece.org/contents/recommendation-19.htm) is advised for Codes for Modes of Transport.

## Logistics status

The logistics status is one of:

* `ReadyToShip`: full quantity ready to be shipped by the supplier
* `Shipped`: full quantity shipped by the supplier
* `Delivered`: full quantity delivered at the buyer
