---
description: How to receive a single delivery order sent by the buyer.
---

# Receive a single delivery order

Tradecloud will send a purchase order, either new or updated, to the supplier when an order event has been triggered.

This page assumes you are using the webhook with a single delivery per order line.

When choosing the delivery schedule please continue on:

{% page-ref page="README.md" %}

## When working with the webhook API

Use the [POST order webhook](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-connector/specs.yaml#/order-webhook%20endpoints/webhookPost) endpoint.

* `eventName` contains the [order event name](https://docs.tradecloud1.com/connectors/webhook-connector/order-events)
* `singleDeliveryOrderEvent` contains the actual order event

## When working with the polling API

Use the [POST poll/single-delivery](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-search/specs.yaml#/order-search/pollOrdersSingleDeliveryRoute) endpoint.

* `order` contains the actual order

## `singleDeliveryOrderEvent` or `order` header

* `id` (in case of an `order`): the Tradecloud order identifier
* `orderId` (in case of an `singleDeliveryOrderEvent`): the Tradecloud order identifier
* `buyerOrder`: the buyer part of the order, see [Buyer order](#buyer-order).
* `supplierOrder`: the supplier part of the order, see [Supplier order](#supplier-order).
* `indicators.deliveryOverdue` is true when at least one order line is overdue.
* `status.processStatus`: is the aggregate of all lines statuses, see [Order process status](#order-process-status).
* `status.logisticsStatus`: is the aggregate of all lines statuses, see [Order logistics status](#order-logistics-status).
* `version`: the Tradecloud order version number.
* `eventDates`: some key order event date/times.
* `meta`: meta information, including source and trace info, about this messsage.
* `lastUpdatedAt`: is the latest date time the order has been changed.

### Buyer order

`buyerOrder` contains the buyer order fields:

* `companyId`: the buyer's Tradecloud company identifier.
* `supplierAccountNumber`: your account number as known in the buyer's ERP system.
* `description`: a free format additional description of this order added by the buyer.
* `contact`: the buyer employee responsible for this order.
* `properties`: are key-value based custom fields, added by the buyer.
* `notes`: are simple custom fields, added by the buyer.
* `labels`: value-added services labels on order level.
* `documents`: contain meta data, objectId or url, of attached documents by the buyer. See:

{% page-ref page="download-document.md" %}

* `orderType`: the order type, one of `Purchase`, `Forecast` or `RFQ`. Default `Purchase`.

### Supplier order

`supplierOrder` is mostly an echo of your order fields as explained in [Send order response](../send-order-response/)​.

* `buyerAccountNumber`: the buyer account number as known in your ERP system.

{% hint style="warning" %}
The `buyerAccountNumber` should be set on forehand in the Tradecloud connection with your buyer. You can set the account code when inviting a new connection or in the connection overview in the portal.
{% endhint %}

### Order status

The order status is the aggregation of all the lines statuses.

#### Order process status

{% hint style="info" %}
The order process status is one of:

* `Issued`: the order is \(re\)issued by the buyer.
* `InProgress`: the order is under negotiation between buyer and supplier
* `Confirmed`: the order is completely agreed between buyer and supplier
* `Rejected`: the order is completely rejected by supplier
* `Completed`: the order is completed at the buyer
* `Cancelled`: the order is cancelled by the buyer
{% endhint %}

#### Order logistics status

{% hint style="info" %}
The order logistics status is one of:

* `Open`: no or partial quantity Produced, ReadyToShip, Shipped or Delivered
* `Produced`: the order full quantity is produced by the supplier
* `ReadyToShip`: the order full quantity is ready to be shipped by the supplier
* `Shipped`: the order full quantity is shipped by the supplier
* `Delivered`: the order full quantity is delivered at the buyer
* `Cancelled`: the order is cancelled by the buyer
{% endhint %}

## `singleDeliveryOrderEvent` lines

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

`buyerLine` contains the buyer order line fields:

* `position`: the line position within the purchase order
* `description`: a free format additional description of this line
* `item`: the item (or article, goods) to be delivered, see [Item](#item)
* `requests`: the buyer can request different delivery schedule, prices and charge lines. Advised is to use the `statusLine.deliveryScheduleInclRequests` and `statusLine.pricesInclRequests` fields instead.
* `terms`: the line terms as agreed with your buyer
  * `contractNumber`: the agreed framework contract number
  * `contractPosition`: the related position within the framework contract
* `projectNumber`: The buyer's project number reference
* `productionNumber`:  The buyer's production number reference
* `salesOrderNumber`:  The buyer's sales order number \(not be confused with your sales order number\)
* `indicators.noDeliveryExpected`: No goods are expected to be delivered to the buyer, for example a service, fee or text line.
* `indicators.delivered`: All goods are delivered at the buyer.
* `properties`: are key-value based custom fields. `\n` may be used for a new line in the value.
* `notes`: are simple custom fields. `\n` may be used for a new line.
* `labels`: value-added services labels on line level.
* `documents`: contain meta data and link of attached documents, see:

{% page-ref page="download-document.md" %}

#### Item

`lines.buyerLine.item`: The item (or article, goods) to be delivered.

* `number`: the item code or number as known in the buyer ERP system.
* `revision`: the revision (or version) of this item number
* `name`: the item short name
* `purchaseUnitOfMeasureIso`: the purchase unit according to ISO 80000-1, a typical example is `PCE`
* `supplierItemNumber`: the item code or number as known at the supplier.

### Supplier line

`supplierLine` is an echo of your order line fields as explained in [Send order response](../send-order-response/)​.

### Status line

`lines.statusLine` represents the current order line values related to the current `Issued`, `Confirmed` or `InProgress` process status. The `InclRequests` fields also include the `InProgress` status and related open buyer or supplier request values.

#### Single delivery

When using `singleDeliveryOrderEvent` one single delivery per order line is used:

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

{% hint style="info" %}
The delivery line logistics status is one of:

* `Open`: no or partial quantity Produced, ReadyToShip, Shipped or Delivered
* `Produced`: the delivery line quantity is produced by the supplier
* `ReadyToShip`: the delivery line quantity is ready to be shipped by the supplier
* `Shipped`: the delivery line quantity is shipped by the supplier
* `Delivered`: the delivery line quantity is delivered at the buyer
{% endhint %}

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

{% hint style="info" %}
The line process status is one of:

* `Issued`: the line is \(re\)issued by the buyer
* `InProgress`: the line is under negotiation between buyer and supplier
* `Confirmed`: the line is agreed between buyer and supplier
* `Rejected`: the line is rejected by supplier
* `Completed`: the line is completed at the buyer
* `Cancelled`: the line is cancelled by the buyer
{% endhint %}

#### Line in Progress status

{% hint style="info" %}
The line in progress status is a more fine-grained status when an order line `processStatus` is `InProgress` and is one of:

* `OpenSupplierProposal`: There is an open proposal from the supplier.
* `RejectedSupplierProposal`: The proposal from the supplier was rejected and no other requests are open.
* `ReissuedRejectedLine`: The rejected order line was reissued by the buyer.
* `OpenSupplierReopenRequest`: There is an open reopen request from the supplier.
* `OpenBuyerReopenRequest`: There is an open reopen request from the buyer.
* `RevertedCompletedLine`: The completion of this line was reverted.
{% endhint %}

#### Line logistics status

{% hint style="info" %}
The line logistics status is one of:

* `Open`: no or partial quantity Produced, ReadyToShip, Shipped or Delivered
* `Produced`: the line quantity is produced by the supplier
* `ReadyToShip`: the line quantity is ready to be shipped by the supplier
* `Shipped`: the line quantity is shipped by the supplier
* `Delivered`: the line quantity is delivered at the buyer
* `Cancelled`: the line is cancelled by the buyer
{% endhint %}

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
