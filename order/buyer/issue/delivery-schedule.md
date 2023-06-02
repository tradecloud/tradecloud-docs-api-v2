---
description: >-
  Choose between the standard or simple delivery schedule
---

# Delivery schedule

## Standard versus simple delivery schedule

Tradecloud works with a delivery schedule per order line.
Each delivery line in a schedule consists of a delivery date and a quantity.

Some ERP systems like SAP work natively with delivery schedules.
Use the Tradecloud [**standard** delivery schedule](#standard-delivery-schedule) in this case.

Other ERP systems can only work with one date and one quantity per order line.
Use the Tradecloud [**simple** delivery schedule](#simple-delivery-schedule) in this case.

## Standard delivery schedule

Use the field `lines.deliverySchedule` for the requested planned delivery schedule of this order line. 

Provide at least one or multiple delivery schedule lines. The total number of delivery schedule lines is limited to 100 lines per order line.

### `deliverySchedule` fields

* `position`: the mandatory position in the delivery schedule. Not to be confused with the `lines.position`.
* `date`: the requested delivery date of this delivery schedule position. Date has ISO 8601 date `yyyy-MM-dd` format. See also [Standards](../../api/standards.md).
* `quantity`: the requested quantity of this delivery schedule position. Quantity has a decimal `1234.56` format with any number of digits.
* `status`: The [logistics status](#logistics-status) of this delivery line according to the buyer.
* `transportMode`: The Mode of Transport used for the delivery of goods as required by the buyer. [UNECE.org Recommendation 19](https://tfig.unece.org/contents/recommendation-19.htm) is advised for Codes for Modes of Transport.

{% hint style="warning" %}
`position` must be unique within the delivery schedule and never change. Never renumber or re-use a `position`.
{% endhint %}

## Simple delivery schedule

{% hint style="warning" %}
The simple delivery schedule is under development. The API and documentation may change.
{% endhint %}

Use the field `lines.scheduledDelivery` for the requested planned delivery of this order line.

Provide one `scheduledDelivery` per order line. The total number of `scheduledDelivery`'s is limited to 100 deliveries per item number.

{% hint style="info" %}
Tradecloud will merge `scheduledDelivery`'s of order lines with the same item number into one order line having a delivery schedule. The `lines.position` will be taken as `deliverySchedule.position`. 

In the order response Tradecloud will do the opposite: expand this order line delivery schedule into order lines having `scheduledDelivery`'s
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
