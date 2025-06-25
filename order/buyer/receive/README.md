---
description: How to receive a purchase order response sent by the supplier
---

# Receive an order response

Tradecloud sends purchase order responses to buyers when order events are triggered.

## Receiving methods

### Choose your API method

You must choose between two methods to receive order responses:

- **Webhook API (Push)**: Tradecloud pushes order events to your system.
- **Polling API (Pull)**: Your system periodically checks for order updates.

For details on choosing between these methods:

{% page-ref page="../../../api/webhook-vs-polling.md" %}

### Choose your delivery format

You must also choose between two delivery formats:

- **Delivery schedule**: Multiple scheduled deliveries per order line
- **Single delivery**: One scheduled delivery per order line

For details on choosing between these formats:

{% page-ref page="../../../api/delivery-schedule.md" %}

If you're using single delivery format, please see:

{% page-ref page="single-delivery-order-response.md" %}

## Implementation options

### Using the webhook API

Use the [POST order webhook](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-connector/specs.yaml#/order-webhook%20endpoints/webhookPost) endpoint.

The webhook body contains:

- `eventName`: Contains the [order event name](https://docs.tradecloud1.com/connectors/webhook-connector/order-events)
- `orderEvent`: Contains the actual order event

### Using the polling API

Use the [POST poll orders](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-search/specs.yaml#/order-search/pollOrdersRoute) endpoint.

The polling response body contains:

- `data`: Contains the actual orders in its current state
- `total`: The total no. of matching orders, independent of paging.
- `lastUpdatedAt`: Store the `lastUpdatedAt` value to use as `lastUpdatedAfter` in subsequent requests.

## Response structure

This section assumes you're using delivery schedules with either the `orderEvent` webhook API or the `order` polling API.

### Order header

The order header contains:

* `id` (in `order`) or `orderId` (in `orderEvent`): Tradecloud order identifier
* `buyerOrder`: the buyer part of the order, see [Buyer order](#buyer-order)
* `supplierOrder`: the supplier part of the order, see [Supplier order](#supplier-order)
* `indicators.deliveryOverdue` is true when at least one order line is overdue.
* `status.processStatus`: is the aggregate of all lines [Order process statuses](#order-process-status).
* `status.logisticsStatus`: is the aggregate of all lines [Order logistics statuses](#order-logistics-status).
* `version`: the Tradecloud order version number
* `eventDates`: some key order event date/times
* `meta`: meta information, including source and trace info, about this messsage
* `lastUpdatedAt`: is the latest date time the order has been changed, useful for polling orders.

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

## `orderEvent` or `order` lines

`lines` contains one or more order lines:

* `id`: the Tradecloud line identifier
* `buyerLine`: the buyer part of the order line, see [Buyer line](#buyer-line).
* `supplierLine`: the supplier part of the order line, see [Supplier line](#supplier-line).
* `confirmedLine`: the order line as agreed between buyer and supplier, see [Confirmed line](#confirmed-line).
* `deliverySchedule`: the current aggregated delivery schedule, see [Delivery schedule](#delivery-schedule).
* `deliveryScheduleIncludingRequests`: the current aggregated delivery schedule including requests, see [Delivery schedule](#delivery-schedule).
* `prices`: the current prices, see [Prices](#prices) below.
* `pricesIncludingRequests`: the current prices, including any open supplier or buyer requests, see [Prices](#prices).
* `indicators.deliveryOverdue` is true when the order line is overdue.
* `status.processStatus`: the order line's [Line process status](#line-process-status).
* `status.inProgressStatus` the order line's [Line in progress status](#line-in-progress-status).
* `status.logisticsStatus`: the order line's [Line logistics status](#line-logistics-status).
* `eventDates`: some key line event date/times
* `mergedItemDetails`: detailed part information provided by both buyer and supplier, see [Item details](#item-details).
* `lastUpdatedAt`: is the latest date time the order line has been changed, useful for polling.

### Buyer line

`lines.buyerLine` is an echo of your order line fields as explained in [Issue a new order](../issue/#lines)

* `position`: the line position within the purchase order

### Supplier line

`lines.supplierLine` contains the supplier order line fields:

* `salesOrderNumber`: the sales order number as known in the supplier's ERP system
* `salesOrderPosition`: the position within the supplier's sales order
* `description`: a free format additional description of this line by the supplier
* `requests`: the supplier can request different delivery schedule, prices and charge lines, see below
* `properties`: are key-value based custom fields, added by the supplier
* `notes`: are simple custom fields, added by the supplier
* `documents`: contain meta data, objectId or url, of attached documents by the supplier.

{% page-ref page="download-document.md" %}

#### Supplier requests

`lines.supplierLine.requests.proposal`: the supplier has proposed a different delivery schedule, prices and/or charge lines compared to the issued order line.
`lines.supplierLine.requests.reopenRequest`: the supplier requests to reopen the confirmed order line. The supplier has requested a different delivery schedule, prices and/or charge lines compared to the confirmed order line.

* `deliverySchedule`: the requested alternative delivery schedule
* `prices`: the requested alternative prices
* `chargeLines`: the requested alternative charge lines, see [Charge lines](#charge-lines)
* `reason`: the reason of this request given by the supplier
* `status`: the [Request status](./#request-status).

##### Request status

{% hint style="info" %}
The request status is one of:

* `Open`: Requested by one party. To be approved or rejected by the other party.
* `Approved`: The request is approved by the other party.
* `Rejected`: The request is rejected by the other party.
* `Closed`: The request is closed because it is not relevant anymore.
{% endhint %}

{% hint style="warning" %}
If the request status is `Open` the other party must approve or reject it.
{% endhint %}

### Confirmed line

`lines.confirmedLine`: the agreed order line between buyer and supplier.

{% hint style="warning" %}
Only if the process status is `Confirmed` the line is agreed between buyer and supplier
{% endhint %}

* `lines.confirmedLine.deliverySchedule`: the agreed delivery schedule
* `lines.confirmedLine.prices`: the agreed prices
* `lines.confirmedLine.chargeLines`: the agreed charge lines, see [Charge lines](#charge-lines)

### Delivery schedule

When using `order` or `orderEvent` the delivery schedule is used.

{% hint style="info" %}
The `lines.deliverySchedule` together with the `lines.prices` fields give a simpler alternative for the `deliverySchedule` and `prices` fields in different places like `buyerLine`, `buyerLine.requests`, `supplierLine.requests` and `confirmedLine`.
{% endhint %}

* `lines.deliverySchedule`: the current delivery schedule, either having `Issued` or `Confirmed` values.

{% hint style="warning" %}
The `lines.deliverySchedule` field does **NOT include any open supplier or buyer request**. Be aware that either the `Issued` or `Confirmed` values are returned, dependent on the line status.
{% endhint %}

* `lines.deliveryScheduleIncludingRequests`: the current delivery schedule, either having `Issued`, `In Progress` or `Confirmed` values.

{% hint style="warning" %}
The `lines.deliveryScheduleIncludingRequests` field **does include any open supplier or buyer request**. Be aware that the `Issued`, proposal or reopen request or `Confirmed` values are returned, dependent on the line and request status.
{% endhint %}

#### Delivery schedule fields

* `lines.deliverySchedule[IncludingRequests].position`: the optional position in the delivery schedule. Not to be confused with the `line.position`
* `lines.deliverySchedule[IncludingRequests].date`: the delivery date of this delivery schedule position. Date has ISO 8601 date `yyyy-MM-dd` format. See also [Standards](../../api/standards.md).
* `lines.deliverySchedule[IncludingRequests].quantity`: the quantity of this delivery schedule position. Quantity has a decimal `1234.56` format with any number of digits.

##### Logistics fields

These additional logistics fields are only available in the order line level delivery schedule:

* `lines.deliverySchedule[IncludingRequests].status`: the optional delivery line's [Scheduled delivery logistics status](#scheduled-delivery-logistics-status).
* `lines.deliverySchedule[IncludingRequests].etd`: The optional logistics Estimated Time of Departure \(local date without time zone\). Date has ISO 8601 date `yyyy-MM-dd` format.
* `lines.deliverySchedule[IncludingRequests].eta`: The optional logistics Estimated Time of Arrival \(local date without time zone\). Date has ISO 8601 date `yyyy-MM-dd` format.

##### Scheduled delivery logistics status

{% hint style="info" %}
The delivery line logistics status is one of:

* `Open`: no or partial quantity Produced, ReadyToShip, Shipped or Delivered
* `Produced`: the delivery line quantity is produced by the supplier
* `ReadyToShip`: the delivery line quantity is ready to be shipped by the supplier
* `Shipped`: the delivery line quantity is shipped by the supplier
* `Delivered`: the delivery line quantity is delivered at the buyer
{% endhint %}

### Prices

* `lines.prices`: the current prices, either having `Issued` or `Confirmed` values.

{% hint style="warning" %}
The `lines.prices` field does **NOT include any open supplier or buyer request**. Be aware that either the `Issued` or `Confirmed` values are returned, dependent on the line status.
{% endhint %}

* `lines.pricesIncludingRequests`: the current prices, either having `Issued`, `In Progress` or `Confirmed` values.

{% hint style="warning" %}
The `lines.pricesIncludingRequests` field **includes any open supplier or buyer request**. Be aware that the `Issued`, proposal or reopen request or `Confirmed` values are returned, dependent on the line and request status.
{% endhint %}

#### Prices fields

* `lines.prices[IncludingRequests].grossPrice`: the gross price. Used together with `discountPercentage`.
* `lines.prices[IncludingRequests].discountPercentage`: the discount percentage. Used together with `grossPrice`.
* `lines.prices[IncludingRequests].netPrice`: the net price.
  * `priceInTransactionCurrency`: the price in the transaction currency of the supplier, like `CNY` in China.
    * `value`: the price value has a decimal `1234.56` format with any number of digits.
    * `currencyIso`: the 3-letter currency code according to ISO 4217, like `EUR`, `USD` and `CNY`
  * `priceInBaseCurrency`: the price in your base currency, like `EUR` in the EU.
    * `value`: the price value has a decimal `1234.56` format with any number of digits.
    * `currencyIso`: the 3-letter currency code according to ISO 4217, like `EUR`.
* `lines.prices[IncludingRequests].priceUnitOfMeasureIso`: the 3-letter price unit according to ISO 80000-1. The purchase unit and price unit may be different.
* `lines.prices[IncludingRequests].priceUnitQuantity`: the item quantity at which the price applies. Typically this is 1 \(unit price\) or 100 \(the price applies to 100 items\)

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
* `ReadyToShip`: the line quantity ready to be shipped by the supplier
* `Shipped`: the line quantity shipped by the supplier
* `Delivered`: the line quantity delivered at the buyer
* `Cancelled`: the line is cancelled by the buyer
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
