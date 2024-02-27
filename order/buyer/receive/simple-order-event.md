---
description: How to receive a simple order response sent by the supplier
---

# Receive an order response

Tradecloud will send a purchase order response to the buyer when an order event has been triggered.

## `simpleOrderEvent`

This page assumes you are using the webhook with the simple delivery schedule in the `simpleOrderEvent`.

* `orderId`: the Tradecloud order identifier
* `buyerOrder`: the buyer part of the order, see [Buyer order](#buyer-order)
* `supplierOrder`: the supplier part of the order, see [Supplier order](#supplier-order)
* `lines`: one or more lines of the order, see [Order lines](#order-lines)
* `indicators.deliveryOverdue` is true when at least one order line is overdue.
* `status.processStatus`: is the aggregate of all lines' [Order process statuses](#order-process-status).
* `status.logisticsStatus`: is the aggregate of all lines' [Order logistics statuses](#order-logistics-status).
* `version`: the Tradecloud order version number
* `eventDates`: some key order event date/times
* `meta`: meta information, including source and trace info, about this messsage
* `lastUpdatedAt`: is the latest date time the order has been changed.

### Buyer order

`buyerOrder` is mostly an echo of your order fields as explained in [Issue a new order](../issue/#order-body-json-objects)

* `supplierAccountNumber`: the supplier account number as known in your ERP system

### Supplier order

`supplierOrder` contains the supplier order fields:

* `companyId`: the supplier's Tradecloud company identifier.
* `buyerAccountNumber`: your account number as known in the supplier's ERP system.
* `description`: a free format additional description of this order by the supplier.
* `contact`: the supplier employee responsible for this order.
* `properties`: are key-value based custom fields, added by the supplier.
* `notes`: are simple custom fields, added by the supplier.
* `documents`: contain meta data and link of attached documents by the supplier.

{% page-ref page="download-document.md" %}

### Order status

#### Order process status

The order **process** status is one of:

* `Issued`: the order is \(re\)issued by the buyer.
* `InProgress`: the order is under negotiation between buyer and supplier
* `Confirmed`: the order is completely agreed between buyer and supplier
* `Rejected`: the order is completely rejected by supplier
* `Completed`: the order is completed at the buyer
* `Cancelled`: the order is cancelled by the buyer

#### Order logistics status

The order **logistics** status is one of:

* `Open`: no or partial quantity Produced, ReadyToShip, Shipped or Delivered
* `Produced`: the order full quantity is produced by the supplier
* `ReadyToShip`: the order full quantity is ready to be shipped by the supplier
* `Shipped`: the order full quantity is shipped by the supplier
* `Delivered`: the order full quantity is delivered at the buyer
* `Cancelled`: the order is cancelled by the buyer

## Order lines

`lines` contains one or more order lines:

* `id`: the Tradecloud line identifier
* `buyerLine`: the buyer part of the order line, see [Buyer line](#buyer-line).
* `supplierLine`: the supplier part of the order line, see [Supplier line](#supplier-line).
* `confirmedLine`: the order line as agreed between buyer and supplier.
* `statusLine`: the order line values representing the current `Issued`, `Confirmed` or `InProgess` status, see [Status line](#status-line).
* `indicators.deliveryOverdue` is true when the order line is overdue.
* `status.processStatus`: the order line's [Line process status](#line-process-status).
* `status.inProgressStatus` the order line's [Line in progress status](#line-in-progress-status).
* `status.logisticsStatus`: the order line's [Line logistics status](#line-logistics-status).
* `eventDates`: some key line event date/times
* `mergedItemDetails`: detailed part information provided by both buyer and supplier, see [Item details](#item-details).
* `lastUpdatedAt`: is the latest date time the order line has been changed.

### Buyer line

`lines.buyerLine` is an echo of your order line fields as explained in [Issue a new order](../issue/#lines)

### Supplier line

`lines.supplierLine` contains the supplier order line fields:

* `salesOrderNumber`: the sales order number as known in the supplier's ERP system
* `salesOrderPosition`: the position within the supplier's sales order
* `description`: a free format additional description of this line by the supplier
* `requests`: the supplier can request different delivery schedule, prices and charge lines. Advised is to use the `statusLine.deliveryScheduleInclRequests` and `statusLine.pricesInclRequests` instead.
* `properties`: are key-value based custom fields, added by the supplier
* `notes`: are simple custom fields, added by the supplier
* `documents`: contain meta data, objectId or url, of attached documents by the supplier.

{% page-ref page="download-document.md" %}

### Status line

`lines.statusLine` represents the current order line values related to the current `Issued`, `Confirmed` or `InProgress` status. The `InclRequests` fields include the `InProgress` status and open buyer or supplier request values.

#### Simple delivery schedule

When using `simpleOrderEvent` the simple delivery schedule is used:

* `lines.statusLine.scheduledDelivery`: the current delivery line, either having `Issued` or `Confirmed` values.
* `lines.statusLine.scheduledDeliveryInclRequests`: the current delivery line, either having `Issued`, `InProgress` requests or `Confirmed` values.

##### Scheduled delivery fields

* `lines.statusLine.scheduledDelivery[InclRequests].date`: the delivery date of this delivery line. Date has ISO 8601 date `yyyy-MM-dd` format. See also [Standards](../../api/standards.md).
* `lines.statusLine.scheduledDelivery[InclRequests].quantity`: the quantity of this delivery line. Quantity has a decimal `1234.56` format with any number of digits.

##### Scheduled delivery logistics fields

These additional logistics fields are only available in the status line scheduled delivery:

* `lines.statusLine.scheduledDelivery[InclRequests].status`: the optional delivery line's [Scheduled delivery logistics status](#scheduled-delivery-logistics-status).
* `lines.statusLine.scheduledDelivery[InclRequests].etd`: The optional logistics Estimated Time of Departure \(local date without time zone\). Date has ISO 8601 date `yyyy-MM-dd` format.
* `lines.statusLine.scheduledDelivery[InclRequests].eta`: The optional logistics Estimated Time of Arrival \(local date without time zone\). Date has ISO 8601 date `yyyy-MM-dd` format.

##### Scheduled delivery logistics status

The delivery line **logistics** status is one of:

* `Open`: no or partial quantity Produced, ReadyToShip, Shipped or Delivered
* `Produced`: the delivery line quantity is produced by the supplier
* `ReadyToShip`: the delivery line quantity is ready to be shipped by the supplier
* `Shipped`: the delivery line quantity is shipped by the supplier
* `Delivered`: the delivery line quantity is delivered at the buyer

#### Prices

* `lines.statusLine.prices`: the current prices, either having `Issued` or `Confirmed` values.
* `lines.statusLine.pricesInclRequests`: the current delivery line, either having `Issued`, `InProgress` requests or `Confirmed` values.

##### Prices fields

* `lines.statusLine.prices[InclRequests].grossPrice`: the gross price. Used together with `discountPercentage`.
* `lines.statusLine.prices[InclRequests].discountPercentage`: the discount percentage. Used together with `grossPrice`.
* `lines.statusLine.prices[InclRequests].netPrice`: the net price.
  * `priceInTransactionCurrency`: the price in the transaction currency of the supplier, like `CNY` in China.
    * `value`: the price value has a decimal `1234.56` format with any number of digits.
    * `currencyIso`: the 3-letter currency code according to ISO 4217, like `EUR`, `USD` and `CNY`
  * `priceInBaseCurrency`: the price in your base currency, like `EUR` in the EU.
    * `value`: the price value has a decimal `1234.56` format with any number of digits.
    * `currencyIso`: the 3-letter currency code according to ISO 4217, like `EUR`.
* `lines.statusLine.prices[InclRequests].priceUnitOfMeasureIso`: the 3-letter price unit according to ISO 80000-1. The purchase unit and price unit may be different.
* `lines.statusLine.prices[InclRequests].priceUnitQuantity`: the item quantity at which the price applies. Typically this is 1 \(unit price\) or 100 \(the price applies to 100 items\)

{% hint style="info" %}
It is advised to only use `netPrice` for its simplicity, or alternatively use `grossPrice` together with `discountPercentage`.
{% endhint %}

### Line status

#### Line process status

The line **process** status is one of:

* `Issued`: the line is \(re\)issued by the buyer
* `InProgress`: the line is under negotiation between buyer and supplier
* `Confirmed`: the line is agreed between buyer and supplier
* `Rejected`: the line is rejected by supplier
* `Completed`: the line is completed at the buyer
* `Cancelled`: the line is cancelled by the buyer

#### Line in Progress status

The line **in progress** status is a more fine-grained status when an order line `processStatus` is `InProgress` and is one of:

* `OpenSupplierProposal`: There is an open proposal from the supplier.
* `RejectedSupplierProposal`: The proposal from the supplier was rejected and no other requests are open.
* `ReissuedRejectedLine`: The rejected order line was reissued by the buyer.
* `OpenSupplierReopenRequest`: There is an open reopen request from the supplier.
* `OpenBuyerReopenRequest`: There is an open reopen request from the buyer.
* `RevertedCompletedLine`: The completion of this line was reverted.

#### Line logistics status

The line **logistics** status is one of:

* `Open`: no or partial quantity Produced, ReadyToShip, Shipped or Delivered
* `Produced`: the line quantity is produced by the supplier
* `ReadyToShip`: the line quantity ready to be shipped by the supplier
* `Shipped`: the line quantity shipped by the supplier
* `Delivered`: the line quantity delivered at the buyer
* `Cancelled`: the line is cancelled by the buyer

### Item details

{% hint style="info" %}
The buyer may send item details to inform the supplier about part information.  
The supplier may check, change and add item details if they are not correct or incomplete.  
`lines.mergedItemDetails` will contain the original item details added by the buyer merged with the changed or added item details by the supplier.
{% endhint %}

* `countryOfOriginCodeIso2`: The ISO 3166-1 alpha-2 country code of manufacture, production, or growth where an article or product comes from.
* `combinedNomenclatureCode`: A tool for classifying goods, set up to meet the requirements both of the Common Customs Tariff and of the EU's external trade statistics.
* `netWeight`: Net weight of one item.
* `netWeightUnitOfMeasureIso`: Net weight unit according to ISO 80000-1.
* `dangerousGoodsCodeUnece`: UN numbers or UN IDs are four-digit numbers that identify dangerous goods, hazardous substances and articles in the framework of international transport.
* `serialNumber`: is an unique identifier assigned incrementally or sequentially to an item, to uniquely identify it.
* `batchNumber`: is an identification number assigned to a particular quantity or lot of material from a single manufacturer
