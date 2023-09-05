---
description: How to update an existing purchase order as a buyer
---

# Update an existing order

As buyer you can send either a [new](issue/) or updated purchase order to Tradecloud.

## Send an updated order to Tradecloud

As a buyer you can send an updated purchase order to Tradecloud.

{% hint style="danger" %}
Most supplier ERP integrations do not have the capability to automatically process an updated order. It will be processed manually by the supplier and the order will have a longer human response time.
{% endhint %}

{% hint style="info" %}
If an order line has order process status `Issued` or `In Progress` and it is updated, it will keep the same status. If the line has status `Rejected` \(by supplier\) and it is reissued, it will become `In Progress`. If the line has status `Confirmed` and it is reopened, it will become `In Progress`. In case of any other status like `Completed` or `Cancelled` the order update will be ignored.
{% endhint %}

### Endpoints

Using the [Send order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderByBuyerRoute) or [Send simple order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendSimpleOrderByBuyerRoute) endpoint is the same as when [sending a new order](issue/) with additional JSON objects as mentioned below. 

Tradecloud will update the order based on the `purchaseOrderNumber` and will add or update lines, delivery schedules and delivery histories where needed. Lines will be matched based on `lines.position`, `deliverySchedule.position` and `deliveryHistory.position`.

{% hint style="info" %}
The order update should preferable only contain **order lines** that are **new or changed**. But you can also send all lines anyway.
{% endhint %}

## Additional fields

### Actual delivery history

The actual delivery history may be added in an order update. These will be used to calculate the line `Overdue` indicator.

* `lines.deliveryHistory`: the historical actual delivery schedule. Provide zero, one or multiple delivery history lines. Provide all delivery history lines in an update. The total number of delivery history lines is limited to 100 lines per order line. 
* `deliveryHistory.position`: the position in the delivery schedule. Not to be confused with the `line.position`. `deliverySchedule.position` versus `deliveryHistory.position` do not have to use the same values.
* `deliveryHistory.date`: the actual delivery date of this delivery schedule position. Date has ISO 8601 date `yyyy-MM-dd` format. See also [Standards](../api/standards.md).
* `deliveryHistory.quantity`: the actual delivered quantity of this delivery schedule position. Quantity has a decimal `1234.56` format with any number of digits.

{% hint style="warning" %}
The simple delivery history variant is under development. For now only the above standard delivery history is available.
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

