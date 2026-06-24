---
description: How to receive a single delivery order response sent by the supplier
---

# Receive a single delivery order response

Tradecloud sends purchase order responses to buyers when order events are
triggered. This page covers receiving responses with a single scheduled delivery
per order line.

If you prefer to work with delivery schedules (multiple deliveries per order
line), please refer to:

{% page-ref page="README.md" %}

## Receiving methods

There are two methods to receive order responses with single deliveries:

### Method 1: Order webhook (Push)

Use the [POST order webhook](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-connector/specs.yaml#/order-webhook%20endpoints/webhookPost)
endpoint.

- `eventName` contains the [order event name](https://docs.tradecloud1.com/connectors/webhook-connector/order-events)
- `singleDeliveryOrderEvent` contains the actual order event

### Method 2: Polling (Pull)

Use the [POST poll/single-delivery](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-search/specs.yaml#/order-search/pollOrdersSingleDeliveryRoute)
endpoint.

- `order` contains the actual order in its current state

## Response structure

### Order header

The order header contains:

- `id` (in `order`) or `orderId` (in `singleDeliveryOrderEvent`): Tradecloud
  order identifier
- `buyerOrder`: the buyer part of the order, see [Buyer order](#buyer-order)
- `supplierOrder`: the supplier part of the order, see
  [Supplier order](#supplier-order)
- `indicators.deliveryOverdue` is true when at least one order line is overdue.
- `status.processStatus`: is the aggregate of all lines statuses, see
  [Order process status](../../status.md#order-process-status).
- `status.logisticsStatus`: is the aggregate of all lines statuses, see [Order
  logistics status](../../status.md#order-logistics-status).
- `version`: the Tradecloud order version number
- `eventDates`: some key order event date/times
- `meta`: meta information, including source and trace info, about this message
- `lastUpdatedAt`: is the latest date time the order has been changed.

### Buyer order

`buyerOrder` is mostly an echo of your order fields as explained in
[Issue a new order](../issue/#order-body-json-objects)

- `supplierAccountNumber`: the supplier account number as known in your ERP
  system

### Supplier order

`supplierOrder` contains the supplier order fields:

- `companyId`: the supplier's Tradecloud company identifier.
- `buyerAccountNumber`: your account number as known in the supplier's ERP
  system.
- `description`: a free format additional description of this order by the
  supplier.
- `contact`: the supplier employee responsible for this order.
- `properties`: are key-value based custom fields, added by the supplier.
- `notes`: are simple custom fields, added by the supplier.
- `documents`: contain meta data and link of attached documents by the supplier.

{% page-ref page="download-document.md" %}

### Order status

The order status is the aggregation of all the lines statuses. See
[Order status](../../status.md#order-status) for the complete list of values.

## `singleDeliveryOrderEvent` lines

`lines` contains one or more order lines:

- `id`: the Tradecloud line identifier
- `lineType`: one of `Item`, `Service`, or `Charge`. See [Order line type](../../line-type.md)
- `chargeReasonCode`: optional UNCL7161 code when the buyer set a charge
  reason on the line
- `buyerLine`: the buyer part of the order line, see [Buyer line](#buyer-line).
- `supplierLine`: the supplier part of the order line, see [Supplier
  line](#supplier-line).
- `confirmedLine`: the order line as agreed between buyer and supplier.
- `statusLine`: the order line values representing the current `Issued`,
  `Confirmed` or `InProgress` status, see [Status line](#status-line).
- `indicators.deliveryOverdue` is true when the order line is overdue.
- `status.processStatus`: the order line's [Line process
  status](../../status.md#line-process-status).
- `status.inProgressStatus`: the order line's [Line in progress
  status](../../status.md#line-in-progress-status).
- `status.logisticsStatus`: the order line's [Line logistics
  status](../../status.md#line-logistics-status).
- `eventDates`: some key line event date/times
- `mergedItemDetails`: detailed part information provided by both buyer and
  supplier, see [Item details](#item-details).
- `lastUpdatedAt`: is the latest date time the order line has been changed.

### Buyer line

`lines.buyerLine` is an echo of your order line fields as explained in [Issue a
new order](../issue/#lines)

- `position`: the line position within the purchase order. The position is
  unique and immutable within the order. Position is empty in case of a newly
  split line.
- `originalPosition`: optional position referencing the original order line when
  the line has been split

### Supplier line

`lines.supplierLine` contains the supplier order line fields:

- `salesOrderNumber`: the sales order number as known in the supplier's ERP
  system
- `salesOrderPosition`: the position within the supplier's sales order
- `description`: a free format additional description of this line by the
  supplier
- `requests`: the supplier can request different delivery schedule and prices.
  Advised is to use the `statusLine.deliveryScheduleInclRequests` and
  `statusLine.pricesInclRequests` fields instead.
- `properties`: are key-value based custom fields, added by the supplier
- `notes`: are simple custom fields, added by the supplier
- `documents`: contain meta data, objectId or url, of attached documents by the
  supplier.

{% page-ref page="download-document.md" %}

### Status line

`lines.statusLine` represents the current order line values related to the
current `Issued`, `Confirmed` or `InProgress` process status. The `InclRequests`
fields also include the `InProgress` status and related open buyer or supplier
request values.

#### Single delivery per order line

When using `singleDeliveryOrderEvent` only one single delivery per order line is
used:

- `lines.statusLine.scheduledDelivery`: the current delivery line, either having
  `Issued` or `Confirmed` values.
- `lines.statusLine.scheduledDeliveryInclRequests`: the current delivery line,
  either having `Issued`, `InProgress` requests or `Confirmed` values.

##### Scheduled delivery fields

- `lines.statusLine.scheduledDelivery[InclRequests].date`: the delivery date of
  this delivery line. Date has ISO 8601 date `yyyy-MM-dd` format. See also
  [Standards](../../api/standards.md).
- `lines.statusLine.scheduledDelivery[InclRequests].quantity`: the quantity of
  this delivery line. Quantity has a decimal `1234.56` format with any number of
  digits.

##### Scheduled delivery logistics fields

These additional logistics fields are only available in the status line
scheduled delivery:

- `lines.statusLine.scheduledDelivery[InclRequests].status`: the optional
  delivery line's [Scheduled delivery logistics status](../../status.md#scheduled-delivery-logistics-status).
- `lines.statusLine.scheduledDelivery[InclRequests].etd`: The optional logistics
  Estimated Time of Departure \(local date without time zone\). Date has ISO
  8601 date `yyyy-MM-dd` format.
- `lines.statusLine.scheduledDelivery[InclRequests].eta`: The optional logistics
  Estimated Time of Arrival \(local date without time zone\). Date has ISO 8601
  date `yyyy-MM-dd` format.

#### Prices

- `lines.statusLine.prices`: the current prices, either having `Issued` or
  `Confirmed` values.
- `lines.statusLine.pricesInclRequests`: the current delivery line, either
  having `Issued`, `InProgress` requests or `Confirmed` values.

##### Prices fields

- `lines.statusLine.prices[InclRequests].grossPrice`: the gross price. Used
  together with `discountPercentage`.
- `lines.statusLine.prices[InclRequests].discountPercentage`: the discount
  percentage. Used together with `grossPrice`.
- `lines.statusLine.prices[InclRequests].netPrice`: the net price.
  - `priceInTransactionCurrency`: the price in the transaction currency of the
    supplier, like `CNY` in China.
    - `value`: the price value has a decimal `1234.56` format with any number
      of digits.
    - `currencyIso`: the 3-letter currency code according to ISO 4217, like
      `EUR`, `USD` and `CNY`
  - `priceInBaseCurrency`: the price in your base currency, like `EUR` in the
    EU.
    - `value`: the price value has a decimal `1234.56` format with any number
      of digits.
    - `currencyIso`: the 3-letter currency code according to ISO 4217, like
      `EUR`.
- `lines.statusLine.prices[InclRequests].priceUnitOfMeasureIso`: the price unit
  of measure, passed through as-is. No standard is enforced; UN/ECE
  Recommendation N°20 is recommended if you want a standard. The purchase unit
  and price unit may be different.
- `lines.statusLine.prices[InclRequests].priceUnitQuantity`: the item quantity
  at which the price applies. Typically this is 1 \(unit price\) or 100 \(the
  price applies to 100 items\)

{% hint style="info" %}
It is advised to only use `netPrice` for its simplicity, or alternatively use
`grossPrice` together with `discountPercentage`.
{% endhint %}

### Line status

See [Line status](../../status.md#line-status) for the complete list of line
process, in progress and logistics status values.

### Item details

{% hint style="info" %}
The buyer may send item details to inform the supplier about part information.  
The supplier may check, change and add item details if they are not correct or
incomplete.
`lines.mergedItemDetails` will contain the original item details added by the
buyer merged with the changed or added item details by the supplier.
{% endhint %}

- `countryOfOriginCodeIso2`: The ISO 3166-1 alpha-2 country code of manufacture,
  production, or growth where an article or product comes from.
- `combinedNomenclatureCode`: A tool for classifying goods, set up to meet the
  requirements both of the Common Customs Tariff and of the EU's external trade
  statistics.
- `netWeight`: Net weight of one item.
- `netWeightUnitOfMeasureIso`: Net weight unit of measure, passed through as-is.
  Mandatory when netWeight is provided. No standard is enforced; UN/ECE
  Recommendation N°20 is recommended if you want a standard.
- `dangerousGoodsCodeUnece`: UN numbers or UN IDs are four-digit numbers that
  identify dangerous goods, hazardous substances and articles in the framework
  of international transport.
- `serialNumber`: is an unique identifier assigned incrementally or sequentially
  to an item, to uniquely identify it.
- `batchNumber`: is an identification number assigned to a particular quantity
  or lot of material from a single manufacturer
