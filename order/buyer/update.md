---
description: How to update an existing purchase order as a buyer
---

# Update an existing order

As buyer you can send either a [new](issue/) or updated purchase order to Tradecloud.

## Order process

{% hint style="danger" %}
Most supplier ERP integrations do not have the capability to automatically process an updated order. It will be processed manually by the supplier and the order will have a longer human response time.
{% endhint %}

* If an order line has order process status `Issued` or `In Progress` and it is updated, it will keep the same status.
* If the line has status `Rejected` \(by supplier\) and it is reissued, it will become `In Progress`.
* If the line has status `Confirmed` and it is reopened, it will become `In Progress`.
* In case of any other status like `Completed` or `Cancelled` the order update will be ignored.

### Endpoints

Use the [Send order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderByBuyerRoute) endpoint when your ERP system supports a delivery schedule natively.

Or use the [Send single delivery order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendSingleDeliveryOrderByBuyerRoute) endpoint for the single delivery per order line feature.

Please see this page to choose between the delivery schedule or single delivery per order line:

{% page-ref page="issue/delivery-schedule.md" %}

Tradecloud will update the order based on the `purchaseOrderNumber` and will add or update lines, delivery schedules and delivery histories where needed.

Order lines will be matched based on `lines.position`, `deliverySchedule.position` and `deliveryHistory.position`.

{% hint style="info" %}
The order update should preferable only contain **order lines** that are **new or changed**. But you can also send all lines anyway.
{% endhint %}

## Additional fields

### Actual delivery history

The actual delivery history may be added in an order update when your ERP system supports a delivery schedule natively. These will be used to calculate the line `Overdue` indicator.

* `lines.deliveryHistory`: the historical actual delivery schedule. Provide zero, one or multiple delivery history lines. Provide all delivery history lines in an update. The total number of delivery history lines is limited to 100 lines per order line. 
* `deliveryHistory.position`: the position in the delivery schedule. Not to be confused with the `line.position`. `deliverySchedule.position` versus `deliveryHistory.position` do not have to use the same values.
* `deliveryHistory.date`: the actual delivery date of this delivery schedule position. Date has ISO 8601 date `yyyy-MM-dd` format. See also [Standards](../api/standards.md).
* `deliveryHistory.quantity`: the actual delivered quantity of this delivery schedule position. Quantity has a decimal `1234.56` format with any number of digits.

### Actual delivery

Or use the actual delivery field when using the single delivery per order line:

* `lines.actualDelivery`: the actual delivery at the buyer for this order line.
* `actualDelivery.date`: the actual delivery date of this delivery. Date has ISO 8601 date `yyyy-MM-dd` format. See also [Standards](../api/standards.md).
* `actualDelivery.quantity`: the actual delivered quantity of this delivery. Quantity has a decimal `1234.56` format with any number of digits.

{% hint style="warning" %}
The `deliveryHistory` (multiple actual deliveries) field is not supported when using the single delivery feature.
Let [support](../support.md) know when you need `deliveryHistory` for single delivery.
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
