---
description: How to receive a purchase order sent by the buyer.
---

# Receive an order

Tradecloud will send a new purchase order to the supplier when an order event has been triggered.

## Choose the appropriate API to receive an order

First choose either the webhook API or the polling API to receive order messages:

{% page-ref page="../../../../api/webhook-vs-polling.md" %}

## Order or OrderEvent

* `id` \(in case of an Order\): the Tradecloud order identifier
* `orderId` \(in case of an OrderEvent\): the Tradecloud order identifier
* `buyerOrder`: the buyer part of the order, see below.
* `supplierOrder`: the supplier part of the order.
* `indicators.deliveryOverdue` is true when at least one order line is overdue.
* `status.processStatus`: is the aggregate of all lines [process status](./#process-status).
* `status.logisticsStatus`: is the aggregate of all lines [logistics status](./#logistics-status).
* `version`: the  Tradecloud order version number.
* `eventDates`: some key order event date/times.
* `meta`: meta information, including source and trace info, about this messsage
* `lastUpdatedAt`: is the latest date time the order has been changed, useful for polling orders.
### Buyer order part

`buyerOrder` contains the buyer order fields:

* `companyId`: the buyer's Tradecloud company identifier.
* `supplierAccountNumber`: your account number as known in the buyer's ERP system.
* `description`: a free format additional description of this order added by the buyer.
* `contact`: the buyer employee responsible for this order.
* `properties`: are key-value based custom fields, added by the buyer.
* `notes`: are simple custom fields, added by the buyer.
* `labels`: value-added services labels on order level.
* `documents`: contain meta data, objectId or url, of attached documents by the buyer, see:
* `orderType`: the order type, one of `Purchase` or `Forecast`.

{% page-ref page="download-document.md" %}

### Supplier order part

`supplierOrder` is mostly an echo of your order fields as explained in [Send order response](../send-order-response/)​.

* `buyerAccountNumber`: the buyer account number as known in your ERP system.

{% hint style="warning" %}
The `buyerAccountNumber` should be set on forehand in the Tradecloud connection with your buyer. You can set the account code when inviting a new connection or in the connection overview in the portal.
{% endhint %}

## Order lines

`lines` contains one or more order lines:

* `id`: the Tradecloud line identifier.
* `buyerLine`: the buyer part of the order line, see [Buyer line part](./#buyer-line-part) below.
* `supplierLine`: the supplier part of the order line, see [Supplier line part](./#supplier-line-part) below.
* `confirmedLine`: the order line as agreed between buyer and supplier, see [Confirmed line](./#confirmed-line) below.
* `deliverySchedule`: the actual aggregated delivery schedule line with logistics info, see [Delivery Schedule](./#delivery-schedule) below.
* `deliveryScheduleIncludingRequests`: the actual aggregated delivery schedule line including any open supplier or buyer requests.
* `prices`: the actual prices, see [Prices](./#prices) below.
* `pricesIncludingRequests`: the actual prices, including any open supplier or buyer requests.
* `indicators.deliveryOverdue` is true when the order line is overdue.
* `status.processStatus`: the order line's [process status](./#process-status).
* `status.logisticsStatus`: the order line's [logistics status](./#logistics-status).
* `eventDates`: some key line event date/times.
* `mergedItemDetails`: detailed part information provided by both buyer and supplier, see [Item details](./#item-details).
* `lastUpdatedAt`: is the latest date time the order line has been changed, usefull for polling.

{% hint style="info" %}
It is advised to use `deliverySchedule` or alternatively `deliveryScheduleIncludingRequests` with `prices` or alternatively `pricesIncludingRequests`. These fields give a summary of the current delivery schedule and prices. Use the `IncludingRequests` fields when you also send proposal or reopen requests events to your ERP.

When using these fields it is not necessary to use the `deliverySchedule` and `prices` fields in `buyerLine`, `buyerLine.requests`, `supplierLine.requests` or `confirmedLine`.

`deliveryScheduleIncludingRequests`, `prices` and `pricesIncludingRequests` are only available in the new webhook, using the "Orders Webhook Integration" configuration in your company profile page. The old webhook, using the "Integration" configuration, is deprecated and customers are being migrated.
{% endhint %}

### Status

#### Process status

{% hint style="info" %}
Order and line **process** status is one of:

* `Issued`: \(re\)issued by the buyer.
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

### Buyer line part

`buyerLine` contains the buyer order line fields:

* `position`: the line position within the purchase order

### Item

`item`: the item \(or article, goods\) to be delivered
* `number`: the item code or number as known in the buyer ERP system.
* `revision`: the revision \(or version\) of this item number
* `name`: the item short name
* `purchaseUnitOfMeasureIso`: the purchase unit according to ISO 80000-1, a typical example is `PCE`
* `supplierItemNumber`: the item code or number as known at the supplier. 

### Item details

`lines.itemDetails`: detailed part information initially provided by buyer.

{% hint style="info" %}
The buyer may send item details to inform the supplier about part information.  
The supplier may check, change and add item details if they are not correct or incomplete.  
The `mergedItemDetails` will contain the original item details added by the buyer merged with the changed or added item details by the supplier.
{% endhint %}

* `countryOfOriginCodeIso2`: The ISO 3166-1 alpha-2 country code of manufacture, production, or growth where an article or product comes from.
* `combinedNomenclatureCode`: A tool for classifying goods, set up to meet the requirements both of the Common Customs Tariff and of the EU's external trade statistics.
* `netWeight`: Net weight of one item.
* `netWeightUnitOfMeasureIso`: Net weight unit according to ISO 80000-1.
* `dangerousGoodsCodeUnece`: UN numbers or UN IDs are four-digit numbers that identify dangerous goods, hazardous substances and articles in the framework of international transport.
* `serialNumber`: is an unique identifier assigned incrementally or sequentially to an item, to uniquely identify it.
* `batchNumber`: is an identification number assigned to a particular quantity or lot of material from a single manufacturer

### Requested planned delivery schedule

`lines.deliverySchedule`: the requested delivery schedule by the buyer.
* `position`: the optional position in the delivery schedule. Not to be confused with the `line.position`
* `date`: the requested delivery date of this delivery schedule position. Date has ISO 8601 date `yyyy-MM-dd` format. See also [Standards](../../api/standards.md).
* `quantity`: the requested quantity of this delivery schedule position. Quantity has a decimal `1234.56` format with any number of digits.

### Requested prices

`lines.prices`: the requested price. Buyers are advised to provide only `netPrice` for its simplicity, or alternatively `grossPrice` together with `discountPercentage`. 
* `grossPrice`: the gross price. Used together with `discountPercentage`.
* `discountPercentage`: the discount percentage. Used together with `grossPrice`.
* `netPrice`: the net price.
    * `priceInTransactionCurrency`: the price in the transaction currency, like `CNY` in China.
        * `value`: the price value has a decimal `1234.56` format with any number of digits.
        * `currencyIso`: the 3-letter currency code according to ISO 4217, like `EUR`, `USD` and `CNY`
    * `priceInBaseCurrency`: optional price in the buyer's base currency, like `EUR` in the EU.
        * `value`: the price value has a decimal `1234.56` format with any number of digits.
        * `currencyIso`: the 3-letter currency code according to ISO 4217, like `EUR`.
* `priceUnitOfMeasureIso`: the price unit according to ISO 80000-1. The purchase unit and price unit may be different.
* `priceUnitQuantity`: the item quantity at which the price applies. Typically this is 1 \(unit price\) or 100 \(the price applies to 100 items\)

### Requested charge lines

`lines.chargeLines`: the requested additional cost lines of an order line, independent of the order line prices, like transport, packing, administration, inspection and certification costs.
* `position`: the position used to identify a charge line.
* `chargeTypeCode`: the mandatory charge reason code according to [UNCL7161](https://docs.peppol.eu/poacc/upgrade-3/codelist/UNCL7161/)
* `chargeDescription`: a mandatory free text description, like "Transport costs".
* `quantity`: the mandatory quantity of this charge line.
* `price`: the mandatory price of this charge line.
    * `priceInTransactionCurrency`: the mandatory price in the transaction currency of the supplier, like `CNY` in China.
        * `value`: the price value has a decimal `1234.56` format with any number of digits.
        * `currencyIso`: the 3-letter currency code according to ISO 4217, like `EUR`, `USD` and `CNY`.
    * `priceInBaseCurrency`: the optional price in your base currency, like `EUR` in the EU.
* `priceUnitOfMeasureIso`: the 3-letter price unit according to ISO 80000-1 which applies to the charge line price.

### Buyer requests

`requests.reopenRequest`: the buyer requests to reopen the confirmed order line. The buyer has requested a different delivery schedule, prices and/or charge lines compared to the confirmed order line.
* `deliverySchedule`: requested alternative delivery schedule, see below
* `prices`: requested alternative prices, see below
* `chargeLines`: requested alternative charge lines, see below
* `reason`: the reason of this request given by the buyer
* `status`: the [request status](./#request-status).

#### Request status

{% hint style="info" %}
The **request** status is one of:

* `Open`: Requested by the buyer. To be approved or rejected by the supplier.
* `Approved`: The request is approved by the supplier.
* `Rejected`:  The request is approved by the supplier.
* `Closed`: The request is closed because it is not relevant anymore.
{% endhint %}

{% hint style="warning" %}
If the request status is `Open` the supplier must approve or reject it.
{% endhint %}

#### Other buyer line fields

* `description`: a free format additional description of this line
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

### Supplier line part

`supplierLine` is mostly an echo of your order line fields as explained in [Send order response](../send-order-response/)​.

* `salesOrderNumber`: the sales order number as known in your ERP system
* `salesOrderPosition`: the position within the sales order

## Confirmed line

`confirmedLine`: the agreed order line between buyer and supplier.

{% hint style="warning" %}
Only if the [process status](./#process-status) is `Confirmed`, the line is agreed between buyer and supplier.
{% endhint %}

* `deliverySchedule`: agreed delivery schedule, see below
* `prices`: agreed prices, see below
* `chargeLines`: agreed charge lines, see below

## Delivery schedule

`deliverySchedule`: the actual delivery schedule, either `Issued` or `Confirmed`.

`deliveryScheduleIncludingRequests`: the actual delivery schedule, either `Issued`, `In Progress` (having an open `Proposal` or `Reopen Request`) or `Confirmed`.

* `position`: the optional position in the delivery schedule. Not to be confused with the `line.position`
* `date`: the delivery date of this delivery schedule position. Date has ISO 8601 date `yyyy-MM-dd` format. See also [Standards](../../api/standards.md).
* `quantity`: the quantity of this delivery schedule position. Quantity has a decimal `1234.56` format with any number of digits.

### Logistics fields

These additional logistics fields are only available in the order line level delivery schedule:

`deliverySchedule`: the requested or confirmed delivery schedule.
* `status`: the optional delivery line [logistics status](./#logistics-status).
* `etd`: The optional logistics Estimated Time of Departure \(local date without time zone\). Date has ISO 8601 date `yyyy-MM-dd` format.
* `eta`: The optional logistics Estimated Time of Arrival \(local date without time zone\). Date has ISO 8601 date `yyyy-MM-dd` format.

## Prices

`prices`: the actual prices, either `Issued` or `Confirmed`. 

`pricesIncludingRequests`: the actual prices, either `Issued`, `In Progress` (having an open `Proposal` or `Reopen Request`) or `Confirmed`.

* `grossPrice`: the gross price. Used together with `discountPercentage`.
* `discountPercentage`: the discount percentage. Used together with `grossPrice`.
* `netPrice`: the net price.
    * `priceInTransactionCurrency`: the  price in the transaction currency, like `CNY` in China.
        * `value`: the price value has a decimal `1234.56` format with any number of digits.
        * `currencyIso`: the 3-letter currency code according to ISO 4217, like `EUR`, `USD` and `CNY`
    * `priceInBaseCurrency`: the optional price in your base currency, like `EUR` in the EU.
        * `value`: the price value has a decimal `1234.56` format with any number of digits.
        * `currencyIso`: the 3-letter currency code according to ISO 4217, like `EUR`.    
    * `priceUnitOfMeasureIso`: the 3-letter price unit according to ISO 80000-1. The purchase unit and price unit may be different.
    * `priceUnitQuantity`: the item quantity at which the price applies. Typically this is 1 \(unit price\) or 100 \(the price applies to 100 items\)

{% hint style="info" %}
It is advised to only use `netPrice` for its simplicity, or alternatively use `grossPrice` together with `discountPercentage`.
{% endhint %}

## Charge lines

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
