---
description: How to reissue an order as a buyer
---

# Reissue order

As buyer you can send either a [new](issue.md) or updated purchase order to Tradecloud.

## Send an updated order to Tradecloud

As a buyer you can send an updated purchase order to Tradecloud.

{% hint style="danger" %}
Most supplier ERP integrations do not have the capability to automatically process an updated order. It will processed manually by the supplier and the order will have a longer human response time.
{% endhint %}

{% hint style="info" %}
If an order line has order process status `Issued` or `In Progress` it will be `Reissued` and keep the same status.
If the line has status `Rejected` (by supplier) it will be `Reissued` and become `In Progress`.
If the line has status `Confirmed` it will be `Reopened` and become `In Progress`.
In case of any other status like `Completed` or `Cancelled` the order update will be ignored.
{% endhint %}

### Send updated order API method

The `/order-integration/order` API method is the same as when [sending a new order](issue.md) with additional JSON objects as mentioned below. Tradecloud will update the order based on the `purchaseOrderNumber` and will update or add lines based on the `lines.position` and will update or add delivery schedule and history based on `deliverySchedule.position` and `deliveryHistory.position`.

{% hint style="tip" %}
The update is event oriented, you only have to send the lines new or updated. But you can also send all lines anyway.
{% endhint %}

### Additional order body JSON objects

#### Historical actual delivery schedule

- `lines.deliveryHistory`: the historical actual delivery schedule. Provide zero, one or multiple delivery schedule lines. These will be used to calculate the line `Overdue` indicator. The fields are similar as in `lines.deliverySchedule`
- `deliveryHistory.position`: the position in the delivery schedule. Not to be confused with the `line.position`. `deliverySchedule.position` versus `deliveryHistory.position` do not have to use the same values.
- `deliveryHistory.date`: the actual delivery date of this delivery schedule position. Date has ISO 8601 date `yyyy-MM-dd` format
- `deliveryHistory.quantity`: the actual delivered quantity of this delivery schedule position. Quantity has a decimal `1234.56` format with any number of digits.

{% hint style="danger" %}
`deliveryHistory.position` should be unique within the delivery history and never change.
Never renumber or re-use `deliveryHistory.position`s.
{% endhint %}

#### Updated order meta data

- `erpLastChangeDateTime`: Date and time the order was updated in your ERP system. `DateTime` has ISO 8601 local date/time format `yyyy-MM-ddThh:mm:ss`
- `erpLastChangedBy`: he user email or user name as known in your ERP system who updated this order
