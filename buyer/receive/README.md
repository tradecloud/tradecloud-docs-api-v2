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

* `status.processStatus`: is the aggregate of all lines process status, see below
* `status.logisticsStatus`: is the aggregate of all lines logistics status, see below
* `version`: the  Tradecloud order version number
* `eventDates`: some key order event date/times
* `meta`: meta information, including source and trace info, about this messsage
* `lastUpdatedAt`: is the latest date time the order has been changed, usefull for polling.

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
* `indicators.deliveryOverdue` is true when the order line is overdue.

{% hint style="warning" %}
The`deliveryOverdue`feature is planned and API and documentation may change. 
{% endhint %}

* `status.processStatus`: the order line process status, see [status](./#status).
* `status.logisticsStatus`: the order line logistics status, see [status](./#status)
* `eventDates`: some key line event date/times
* `mergedItemDetails`: detailed part information provided by both buyer and supplier, see [item details](./#item-details).
* `lastUpdatedAt`: is the latest date time the order line has been changed, usefull for polling.

### Status

{% hint style="info" %}
Order and line **process** status is one of:

* `Issued`:  \(re\)issued by the buyer.
* `InProgress`: under negotiation between buyer and supplier
* `Confirmed`: agreed between buyer and supplier
* `Rejected`: rejected by supplier
* `Completed`: completed at the buyer
* `Cancelled`: cancelled by either buyer or supplier
{% endhint %}

{% hint style="info" %}
Order and line **logistics** status is one of:

* `Open`: not shipped or delivered
* `Shipped`: shipped by the supplier
* `Delivered`: delivered at the buyer
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

### **Supplier line part**

`supplierLine` contains the supplier order line fields:

* `salesOrderNumber`: the sales order number as known in the supplier's ERP system
* `salesOrderPosition`: the position within the supplier's sales order
* `description`: a free format additional description of this line by the supplier
* `proposal`: the supplier can propose a different delivery schedule and prices, see below
* `properties`: are key-value based custom fields, added by the supplier
* `notes`: are simple custom fields, added by the supplier
* `documents`: contain meta data and link of attached documents by the supplier.  

{% page-ref page="download-document.md" %}

## Supplier proposal

`proposal`: in stead of accepting or rejecting an order line, the supplier can alternatively propose a different delivery schedule and prices.

{% hint style="warning" %}
If the proposal status is `Proposed`the buyer should approve or reject it.
{% endhint %}

* `deliverySchedule`: proposed alternative delivery schedule, see below
* `prices`:proposed alternative prices, see below
* `reason`: the reason of this proposal given by the supplier
* `status`: one of`Proposed`by the supplier, or `Approved` or `Rejected` by the buyer.

## Confirmed line

`confirmedLine`: the agreed order line between buyer and supplier.

{% hint style="warning" %}
Only if the process status is `Confirmed` the line is agreed between buyer and supplier
{% endhint %}

* `deliverySchedule`: agreed delivery schedule, see below
* `prices`: agreed prices, see below

### Confirmed or proposed delivery schedule

`deliverySchedule`: the confirmed or proposed planned delivery schedule.

* `deliverySchedule.position`: the optional position in the delivery schedule. Not to be confused with the `line.position`
* `deliverySchedule.date`: the delivery date of this delivery schedule position. Date has ISO 8601 date `yyyy-MM-dd` format. See also [Standards](../../api/standards.md).
* `deliverySchedule.quantity`: the quantity of this delivery schedule position. Quantity has a decimal `1234.56` format with any number of digits.

### Confirmed or proposed prices

`prices`: the confirmed or proposed price. Advised is to provide only `netPrice` for its simplicity, used by most buyers, or alternatively `grossPrice` together with `discountPercentage`.

* `priceInTransactionCurrency`: the  price in the transaction currency of the supplier, like `CNY` in China.
* `priceInBaseCurrency`: the price in your base currency, like `EUR` in the EU.
* `value`: the price value has a decimal `1234.56` format with any number of digits.
* `currencyIso`: the 3-letter currency code according to ISO 4217, like `EUR`, `USD` and `CNY`
* `priceUnitOfMeasureIso`: the 3-letter price unit according to ISO 80000-1. The purchase unit and price unit may be different.
* `priceUnitQuantity`: the item quantity at which the price applies. Typically this is 1 \(unit price\) or 100 \(the price applies to 100 items\)
