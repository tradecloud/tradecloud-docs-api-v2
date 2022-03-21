---
description: How to receive a purchase order response sent by the supplier
---

# Receive an order response

Tradecloud will send a purchase order response to the buyer when an order event has been triggered.

## Choose the appropriate API to receive the order response

First choose either the webhook API or the polling API to receive order responses:

{% page-ref page="../../api/webhook-vs-polling.md" %}

## Order or OrderEvent

* `id` \(in case of an Order\): the Tradecloud order identifier
* `orderId` \(in case of an OrderEvent\): the Tradecloud order identifier
* `buyerOrder`: the buyer part of the order
* `supplierOrder`: the supplier part of the order, see below
* `indicators.deliveryOverdue` is true when at least one order line is overdue.

{% hint style="warning" %}
The`deliveryOverdue`feature is planned and API and documentation may change.
{% endhint %}

* `status.processStatus`: is the aggregate of all lines' [process statuses](./#process-status).
* `status.logisticsStatus`: is the aggregate of all lines' [logistics statuses](./#logistics-status).
* `version`: the  Tradecloud order version number
* `eventDates`: some key order event date/times
* `meta`: meta information, including source and trace info, about this messsage
* `lastUpdatedAt`: is the latest date time the order has been changed, useful for polling.

### Buyer order part

`buyerOrder` is mostly an echo of your order fields as explained in [Issue a new order](../issue/#order-body-json-objects)

* `supplierAccountNumber`: the supplier account number as known in your ERP system

### Supplier order part

`supplierOrder` contains the supplier order fields:

* `companyId`: the supplier's Tradecloud company identifier.
* `buyerAccountNumber`: your account number as known in the supplier's ERP system
* `description`: a free format additional description of this order by the supplier
* `contact`: the supplier employee responsible for this order. 
* `properties`: are key-value based custom fields, added by the supplier
* `notes`: are simple custom fields, added by the supplier
* `documents`: contain meta data and link of attached documents by the supplier.

  {% page-ref page="download-document.md" %}

## Order lines

`lines` contains one or more order lines:

* `id`: the Tradecloud line identifier
* `buyerLine`: the buyer part of the order line, see [Buyer line part](./#buyer-line-part).
* `supplierLine`: the supplier part of the order line, see [Supplier line part](./#supplier-line-part).
* `confirmedLine`: the order line as agreed between buyer and supplier, see [Confirmed line](./#confirmed-line).
* `deliverySchedule`: the aggregated delivery schedule lines with logistics info, see [Delivery Schedule](./#delivery-schedule) below.
* `indicators.deliveryOverdue` is true when the order line is overdue.

{% hint style="warning" %}
The`deliveryOverdue`feature is planned and API and documentation may change.
{% endhint %}

* `status.processStatus`: the order line's [process status](./#process-status).
* `status.logisticsStatus`: the order line's [logistics status](./#logistics-status).
* `eventDates`: some key line event date/times
* `mergedItemDetails`: detailed part information provided by both buyer and supplier, see [item details](./#item-details).
* `lastUpdatedAt`: is the latest date time the order line has been changed, usefull for polling.

### Status

#### Process status

{% hint style="info" %}
Order and line **process** status is one of:

* `Issued`:  \(re\)issued by the buyer.
* `InProgress`: under negotiation between buyer and supplier
* `Confirmed`: agreed between buyer and supplier
* `Rejected`: rejected by supplier
* `Completed`: completed at the buyer
* `Cancelled`: cancelled by either buyer or supplier
{% endhint %}

#### Logistics status

{% hint style="info" %}
Order, line and delivery line **logistics** status is one of:

* `Open`: no or partial quantity Produced, ReadyToShip, Shipped or Delivered
* `Produced`: full quantity produced by the supplier
* `ReadyToShip`: full quantity ready to be shipped by the supplier
* `Shipped`: full quantity shipped by the supplier
* `Delivered`: full quantity delivered at the buyer
{% endhint %}

### Item details

{% hint style="info" %}
The buyer may send item details to inform the supplier about part information.  
The supplier may check, change and add item details if they are not correct or incomplete.  
`mergedItemDetails` will contain the original item details added by the buyer merged with the changed or added item details by the supplier.
{% endhint %}

* `countryOfOriginCodeIso2`: The ISO 3166-1 alpha-2 country code of manufacture, production, or growth where an article or product comes from.
* `combinedNomenclatureCode`: A tool for classifying goods, set up to meet the requirements both of the Common Customs Tariff and of the EU's external trade statistics.
* `netWeight`: Net weight of one item.
* `netWeightUnitOfMeasureIso`: Net weight unit according to ISO 80000-1.
* `dangerousGoodsCodeUnece`: UN numbers or UN IDs are four-digit numbers that identify dangerous goods, hazardous substances and articles in the framework of international transport.
* `serialNumber`: is an unique identifier assigned incrementally or sequentially to an item, to uniquely identify it.
* `batchNumber`: is an identification number assigned to a particular quantity or lot of material from a single manufacturer

### Buyer line part

`buyerLine` is an echo of your order line fields as explained in [Issue a new order](../issue/#lines)

### Supplier line part

`supplierLine` contains the supplier order line fields:

* `salesOrderNumber`: the sales order number as known in the supplier's ERP system
* `salesOrderPosition`: the position within the supplier's sales order
* `description`: a free format additional description of this line by the supplier
* `requests`: the supplier can request different delivery schedule, prices and charge lines, see below
* `properties`: are key-value based custom fields, added by the supplier
* `notes`: are simple custom fields, added by the supplier
* `documents`: contain meta data and link of attached documents by the supplier.  

{% page-ref page="download-document.md" %}

### Supplier requests

* `requests.proposal`: the supplier has proposed a different delivery schedule, prices and/or charge lines compared to the issued order line.
* `requests.reopenRequest`: the supplier requests to reopen the confirmed order line. The supplier has requested a different delivery schedule, prices and/or charge lines compared to the confirmed order line.
* `deliverySchedule`: requested alternative delivery schedule, see below
* `prices`: requested alternative prices, see below
* `chargeLines`: requested alternative charge lines, see below
* `reason`: the reason of this request given by the supplier
* `status`: the [request status](./#request-status).

#### Request status

{% hint style="info" %}
The **request** status is one of:

* `Open`: Requested by the supplier. To be approved or rejected by the buyer.
* `Approved`: The request is approved by the buyer.
* `Rejected`:  The request is approved by the supplier.
* `Closed`: The request is closed because it is not relevant anymore.
{% endhint %}

{% hint style="warning" %}
If the request status is `Open` the buyer must approve or reject it.
{% endhint %}

## Confirmed line

`confirmedLine`: the agreed order line between buyer and supplier.

{% hint style="warning" %}
Only if the process status is `Confirmed` the line is agreed between buyer and supplier
{% endhint %}

* `deliverySchedule`: agreed delivery schedule, see below
* `prices`: agreed prices, see below

## Delivery schedule

`deliverySchedule`: the requested or confirmed delivery schedule.

* `deliverySchedule.position`: the optional position in the delivery schedule. Not to be confused with the `line.position`
* `deliverySchedule.date`: the delivery date of this delivery schedule position. Date has ISO 8601 date `yyyy-MM-dd` format. See also [Standards](../../api/standards.md).
* `deliverySchedule.quantity`: the quantity of this delivery schedule position. Quantity has a decimal `1234.56` format with any number of digits.

### Logistics fields

{% hint style="warning" %}
The buyer must provide a `deliverySchedule.position` when sending an order to be able to receive additional logistics fields.
{% endhint %}

These additional logistics fields are only available in the order line level delivery schedule:

* `deliverySchedule.status`: the optional delivery line's [logistics status](./#logistics-status).
* `deliverySchedule.etd`: The optional logistics Estimated Time of Departure \(local date without time zone\). Date has ISO 8601 date `yyyy-MM-dd` format.
* `deliverySchedule.eta`: The optional logistics Estimated Time of Arrival \(local date without time zone\). Date has ISO 8601 date `yyyy-MM-dd` format.

## Prices

`prices`: the requested or confirmed price. Advised is to provide only `netPrice` for its simplicity, used by most buyers, or alternatively `grossPrice` together with `discountPercentage`.

* `priceInTransactionCurrency`: the  price in the transaction currency of the supplier, like `CNY` in China.
* `priceInBaseCurrency`: the price in your base currency, like `EUR` in the EU.
* `value`: the price value has a decimal `1234.56` format with any number of digits.
* `currencyIso`: the 3-letter currency code according to ISO 4217, like `EUR`, `USD` and `CNY`
* `priceUnitOfMeasureIso`: the 3-letter price unit according to ISO 80000-1. The purchase unit and price unit may be different.
* `priceUnitQuantity`: the item quantity at which the price applies. Typically this is 1 \(unit price\) or 100 \(the price applies to 100 items\)

### Charge lines

* `lines.chargeLines`: the requested or confirmed additional cost lines of an order line, independent of the order line prices, like transport, packing, administration, inspection and certification costs.
* `chargeLines.position`: the position used to identify a charge line.
* `chargeLines.chargeTypeCode`: the mandatory charge reason code according to [UNCL7161](https://docs.peppol.eu/poacc/upgrade-3/codelist/UNCL7161/)
* `chargeLines.chargeDescription`: a mandatory free text description, like "Transport costs".
* `chargeLines.quantity`: the mandatory quantity of this charge line.
* `chargeLines.price`: the mandatory price of this charge line.
* `priceInTransactionCurrency`: the mandatory price in the transaction currency of the supplier, like `CNY` in China.
* `priceInBaseCurrency`: the optional price in your base currency, like `EUR` in the EU.
* `value`: the price value has a decimal `1234.56` format with any number of digits.
* `currencyIso`: the 3-letter currency code according to ISO 4217, like `EUR`, `USD` and `CNY`.
* `priceUnitOfMeasureIso`: the 3-letter price unit according to ISO 80000-1 which applies to the charge line price.
