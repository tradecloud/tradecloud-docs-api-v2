---
description: How to update an existing purchase order as a buyer
---

# Update an existing order

As buyer you can send either a [new](issue/) or updated purchase order to Tradecloud.

{% hint style="warning" %}
The order should only contain **order lines** that are **new or changed**. Sending an unchanged order line could trigger an unexpected line status change in Tradecloud.
{% endhint %}

## Order process

After sending an updated order to Tradecloud the order line **process status may change**:

A new order line will have status `Issued` and a **confirm** task for the supplier will be created.

When the order line has status `Issued` the **confirm** task for the supplier will be updated.

When the order line has status `InProgress`:

* When the by buyer **requested** `delivery schedule` and `prices` are **equal** to the by supplier **responded** \(either via a proposal or reopen request\)`delivery schedule` and `prices` the order process status will become `Confirmed`
* When the **requested** `delivery schedule` and `prices` are **NOT** equal to the **responded**

  `delivery schedule` and `prices` the order process status will stay `InProgress`.  
  If there is an open reopen request, it will be updated.

When the order line has status `Confirmed`:

* When the by buyer **requested** `delivery schedule` and `prices` are **NOT** equal to the **confirmed** `delivery schedule` and `prices` the process status will become `InProgress` and a **reopen request** to the supplier will be created.
* When the **requested** `delivery schedule` and `prices` are **equal** to the **confirmed** `delivery schedule` and `prices` the process status will stay `Confirmed`

When the order line has status `Rejected`:

* The process status will become `InProgress`and a confirm task for the supplier will be created

When the order line already has process status `Completed` the status will **NOT** change.

When the order line already has process status `Cancelled` the status will **NOT** change.

And the order line **logistics status may change**:

* When the order line already has logistics status  `Delivered` the status will NOT change.

## Send an updated order to Tradecloud

As a buyer you can send an updated purchase order to Tradecloud.

{% hint style="danger" %}
Most supplier ERP integrations do not have the capability to automatically process an updated order. It will be processed manually by the supplier and the order will have a longer human response time.
{% endhint %}

{% hint style="info" %}
If an order line has order process status `Issued` or `In Progress` and it is updated, it will keep the same status. If the line has status `Rejected` \(by supplier\) and it is reissued, it will become `In Progress`. If the line has status `Confirmed` and it is reopened, it will become `In Progress`. In case of any other status like `Completed` or `Cancelled` the order update will be ignored.
{% endhint %}

### Send updated order API method

Using the `/api-connector/order` API method is the same as when [sending a new order](issue/) with additional JSON objects as mentioned below. Tradecloud will update the order based on the `purchaseOrderNumber` and will add or update lines, delivery schedules and delivery histories where needed. Lines will be matched based on `lines.position`, `deliverySchedule.position` and `deliveryHistory.position`.

{% hint style="info" %}
The update is event oriented, you only have to send the lines new or updated. But you can also send all lines anyway.
{% endhint %}

## Additional fields

### Actual delivery history

The actual delivery history may be added in an order update:

* `lines.deliveryHistory`: the historical actual delivery schedule. Provide zero, one or multiple delivery history lines. Provide all delivery history lines in an update. These will be used to calculate the line `Overdue` indicator.
* `deliveryHistory.position`: the position in the delivery schedule. Not to be confused with the `line.position`. `deliverySchedule.position` versus `deliveryHistory.position` do not have to use the same values.
* `deliveryHistory.date`: the actual delivery date of this delivery schedule position. Date has ISO 8601 date `yyyy-MM-dd` format. See also [Standards](../api/standards.md).
* `deliveryHistory.quantity`: the actual delivered quantity of this delivery schedule position. Quantity has a decimal `1234.56` format with any number of digits.

{% hint style="warning" %}
`deliveryHistory.position` should be unique within the delivery history and never change. Never renumber or re-use `deliveryHistory.position`s.
{% endhint %}

### Additional order and line indicators

Additional indicators may be set in an order update:

* `indicators`:

{% page-ref page="receive-goods.md" %}

{% page-ref page="complete.md" %}

{% page-ref page="cancel.md" %}

{% page-ref page="reopen.md" %}

## Updated order meta data

* `erpLastChangeDateTime`: Date and time the order was updated in your ERP system. `DateTime` has ISO 8601 local date/time format `yyyy-MM-ddThh:mm:ss`. See also [Standards](../api/standards.md).
* `erpLastChangedBy`: he user email or user name as known in your ERP system who updated this order

## Response

Only a HTTP status code will be returned

