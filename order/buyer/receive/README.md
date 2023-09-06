---
description: How to receive a purchase order response sent by the supplier
---

# Receive an order response

Tradecloud will send a purchase order response to the buyer when an order event has been triggered.

## Choose the appropriate API to receive an order response

First choose either the webhook API or the polling API to receive order response messages:

{% page-ref page="../../../api/webhook-vs-polling.md" %}

## Choose to receive the native or simple delivery schedule 

If you choose the POST webhook API, you may choose between the native or simple delivery schedule:

{% page-ref page="../../../api/delivery-schedule.md" %}

## Order or OrderEvent

* `id` \(in case of an Order\): the Tradecloud order identifier
* `orderId` \(in case of an OrderEvent\): the Tradecloud order identifier
* `buyerOrder`: the buyer part of the order
* `supplierOrder`: the supplier part of the order, see below
* `indicators.deliveryOverdue` is true when at least one order line is overdue.
* `status.processStatus`: is the aggregate of all lines' [process statuses](./#process-status).
* `status.logisticsStatus`: is the aggregate of all lines' [logistics statuses](./#logistics-status).
* `version`: the  Tradecloud order version number
* `eventDates`: some key order event date/times
* `meta`: meta information, including source and trace info, about this messsage
* `lastUpdatedAt`: is the latest date time the order has been changed, useful for polling orders.

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
* `prices`: the current prices, see [Prices](./#prices) below.
* `pricesIncludingRequests`: the current prices, including any open supplier or buyer requests.
* `indicators.deliveryOverdue` is true when the order line is overdue.
* `status.processStatus`: the order line's [process status](./#process-status).
* `status.logisticsStatus`: the order line's [logistics status](./#logistics-status).
* `eventDates`: some key line event date/times
* `mergedItemDetails`: detailed part information provided by both buyer and supplier, see [item details](./#item-details).
* `lastUpdatedAt`: is the latest date time the order line has been changed, usefull for polling.

### Current delivery schedule

* `deliverySchedule`: the current aggregated delivery schedule with logistics info, see [Native Delivery Schedule](#native-delivery-schedule) below.
* `deliveryScheduleIncludingRequests`: the current aggregated delivery schedule including any open supplier or buyer requestso, see [Native Delivery Schedule](#native-delivery-schedule) below.

{% hint style="info" %}
It is advised to use `deliverySchedule` with `prices` or alternatively `deliveryScheduleIncludingRequests` with `pricesIncludingRequests`.

These fields give a summary of the current delivery schedule and prices. Use the `IncludingRequests` fields when you also send proposal or reopen request events to your ERP.

When using these fields it is not necessary to use the `deliverySchedule` and `prices` fields in `buyerLine`, `buyerLine.requests`, `supplierLine.requests` or `confirmedLine`.

`deliveryScheduleIncludingRequests`, `prices` and `pricesIncludingRequests` are only available in the new webhook, using the "Orders Webhook Integration" configuration in your company profile page, and are also available in the `order-search` API when using polling.
{% endhint %}

### Current delivery line

* `scheduledDelivery`: the current aggregated delivery line with logistics info, see [Simple Delivery Schedule](#simple-delivery-schedule) below.

In case of the simple delivery schedule, there is no `scheduledDeliveryIncludingRequests` variant available. Please let [support](../../../support.md) know when you need this field.

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
* `documents`: contain meta data, objectId or url, of attached documents by the supplier.  

{% page-ref page="download-document.md" %}

### Supplier requests

`requests.proposal`: the supplier has proposed a different delivery schedule, prices and/or charge lines compared to the issued order line.
`requests.reopenRequest`: the supplier requests to reopen the confirmed order line. The supplier has requested a different delivery schedule, prices and/or charge lines compared to the confirmed order line.
* `deliverySchedule`: the requested alternative delivery schedule
* `prices`: the requested alternative prices
* `chargeLines`: the requested alternative charge lines
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

* `deliverySchedule`: the agreed delivery schedule
* `prices`: the agreed prices
* `chargeLines`: the agreed charge lines

## Native Delivery schedule

`lines.deliverySchedule`: the current delivery schedule, either `Issued` or `Confirmed`.

`lines.deliveryScheduleIncludingRequests`: the current planned delivery schedule, either `Issued`, `In Progress` (having an open `Proposal` or `Reopen Request`) or `Confirmed`. This field is only supported as native delivery schedule.

  * `position`: the optional position in the delivery schedule. Not to be confused with the `line.position`
  * `date`: the delivery date of this delivery schedule position. Date has ISO 8601 date `yyyy-MM-dd` format. See also [Standards](../../api/standards.md).
  * `quantity`: the quantity of this delivery schedule position. Quantity has a decimal `1234.56` format with any number of digits.

### Logistics fields

These additional logistics fields are only available in the order line level delivery schedule:

  * `status`: the optional delivery line's [logistics status](./#logistics-status).
  * `etd`: The optional logistics Estimated Time of Departure \(local date without time zone\). Date has ISO 8601 date `yyyy-MM-dd` format.
  * `eta`: The optional logistics Estimated Time of Arrival \(local date without time zone\). Date has ISO 8601 date `yyyy-MM-dd` format.

## Simple Delivery schedule

`lines.scheduledDelivery`: the current delivery line, when using the simple delivery schedule.

  * `date`: the delivery date of this delivery line. Date has ISO 8601 date `yyyy-MM-dd` format. See also [Standards](../../api/standards.md).
  * `quantity`: the quantity of this delivery line. Quantity has a decimal `1234.56` format with any number of digits.

### Logistics fields

  * `status`: the optional delivery line's [logistics status](./#logistics-status).
  * `etd`: The optional logistics Estimated Time of Departure \(local date without time zone\). Date has ISO 8601 date `yyyy-MM-dd` format.
  * `eta`: The optional logistics Estimated Time of Arrival \(local date without time zone\). Date has ISO 8601 date `yyyy-MM-dd` format.

## Prices

`lines.prices`: the current prices, either `Issued` or `Confirmed`. 

`pricesIncludingRequests`: the current prices, either `Issued`, `In Progress` (having an open `Proposal` or `Reopen Request`) or `Confirmed`.

  * `grossPrice`: the gross price. Used together with `discountPercentage`.
  * `discountPercentage`: the discount percentage. Used together with `grossPrice`.
  * `netPrice`: the net price.
    * `priceInTransactionCurrency`: the  price in the transaction currency of the supplier, like `CNY` in China.
      * `value`: the price value has a decimal `1234.56` format with any number of digits.
      * `currencyIso`: the 3-letter currency code according to ISO 4217, like `EUR`, `USD` and `CNY`
    * `priceInBaseCurrency`: the price in your base currency, like `EUR` in the EU.
      * `value`: the price value has a decimal `1234.56` format with any number of digits.
      * `currencyIso`: the 3-letter currency code according to ISO 4217, like `EUR`.
  * `priceUnitOfMeasureIso`: the 3-letter price unit according to ISO 80000-1. The purchase unit and price unit may be different.
  * `priceUnitQuantity`: the item quantity at which the price applies. Typically this is 1 \(unit price\) or 100 \(the price applies to 100 items\)

{% hint style="info" %}
It is advised to only use `netPrice` for its simplicity, or alternatively use `grossPrice` together with `discountPercentage`.
{% endhint %}

### Charge lines

`chargeLines`: the requested or confirmed additional cost lines of an order line, independent of the order line prices, like transport, packing, administration, inspection and certification costs.
* `position`: the position used to identify a charge line.
* `chargeTypeCode`: the mandatory charge reason code according to [UNCL7161](https://docs.peppol.eu/poacc/upgrade-3/codelist/UNCL7161/)
* `chargeDescription`: a mandatory free text description, like "Transport costs".
* `quantity`: the mandatory quantity of this charge line.
* `price`: the mandatory price of this charge line.
  * `priceInTransactionCurrency`: the mandatory price in the transaction currency of the supplier, like `CNY` in China.
    * `value`: the price value has a decimal `1234.56` format with any number of digits.
    * `currencyIso`: the 3-letter currency code according to ISO 4217, like `EUR`, `USD` and `CNY`.
  * `priceInBaseCurrency`: the optional price in your base currency, like `EUR` in the EU.
    * `value`: the price value has a decimal `1234.56` format with any number of digits.
    * `currencyIso`: the 3-letter currency code according to ISO 4217, like `EUR`.
* `priceUnitOfMeasureIso`: the 3-letter price unit according to ISO 80000-1 which applies to the charge line price.
