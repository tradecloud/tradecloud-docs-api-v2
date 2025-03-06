---
description: How to receive a single delivery order response sent by the supplier
---

# Receive a Single Delivery Order Response

Tradecloud sends purchase order responses to buyers when order events are triggered. This page covers receiving responses with a single delivery per order line.

If you prefer to work with delivery schedules (multiple deliveries per order line), please refer to:

{% page-ref page="README.md" %}

{% hint style="info" %}
When converting between delivery formats:

- Tradecloud internally represents order lines with the same item, prices, and terms as one order line with a delivery schedule
- For single delivery responses, Tradecloud splits the delivery schedule into separate order lines, each with one delivery
- The `deliverySchedule.position` value is mapped to the order response `lines.buyerLine.position`
{% endhint %}

## Receiving Methods

There are two methods to receive order responses with single deliveries:

### Method 1: Order Webhook (Push)

Use the [POST order webhook](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-connector/specs.yaml#/order-webhook%20endpoints/webhookPost) endpoint.

- `eventName` contains the [order event name](https://docs.tradecloud1.com/connectors/webhook-connector/order-events)
- `singleDeliveryOrderEvent` contains the actual order event

### Method 2: Polling (Pull)

Use the [POST poll/single-delivery](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-search/specs.yaml#/order-search/pollOrdersSingleDeliveryRoute) endpoint.

- `order` contains the actual order in its current state

## Response Structure

### Order Header

The order header contains:

- `id` (in `order`) or `orderId` (in `singleDeliveryOrderEvent`): Tradecloud order identifier
- `buyerOrder`: Buyer part of the order (see [Buyer order](#buyer-order))
- `supplierOrder`: Supplier part of the order (see [Supplier order](#supplier-order))
- `indicators.deliveryOverdue`: `true` when at least one order line is overdue
- `status.processStatus`: Aggregate of all line statuses (see [Order process status](#order-process-status))
- `status.logisticsStatus`: Aggregate of all line statuses (see [Order logistics status](#order-logistics-status))
- `version`: Tradecloud order version number
- `eventDates`: Key order event timestamps
- `meta`: Meta information, including source and trace info
- `lastUpdatedAt`: Latest timestamp when the order was changed

### Buyer Order

The `buyerOrder` section mostly echoes your original order fields as explained in [Issue a new order](../issue/#order-body-json-objects).

- `supplierAccountNumber`: Supplier account number as known in your ERP system

### Supplier Order

The `supplierOrder` section contains:

- `companyId`: Supplier's Tradecloud company identifier
- `buyerAccountNumber`: Your account number as known in the supplier's ERP system
- `description`: Additional description of this order by the supplier
- `contact`: Supplier employee responsible for this order
- `properties`: Key-value based custom fields added by the supplier
- `notes`: Simple custom fields added by the supplier
- `documents`: Meta data and links to attached documents from the supplier

{% page-ref page="download-document.md" %}

### Order Status

#### Order Process Status

The order process status is one of:

- `Issued`: Order (re)issued by the buyer
- `InProgress`: Order under negotiation between buyer and supplier
- `Confirmed`: Order completely agreed between buyer and supplier
- `Rejected`: Order completely rejected by supplier
- `Completed`: Order completed at the buyer
- `Cancelled`: Order cancelled by the buyer

#### Order Logistics Status

The order logistics status is one of:

- `Open`: No or partial quantity Produced, ReadyToShip, Shipped or Delivered
- `Produced`: Order full quantity produced by the supplier
- `ReadyToShip`: Order full quantity ready to be shipped by the supplier
- `Shipped`: Order full quantity shipped by the supplier
- `Delivered`: Order full quantity delivered to the buyer
- `Cancelled`: Order cancelled by the buyer

## Order Lines

The `lines` array contains one or more order lines:

- `id`: Tradecloud line identifier
- `buyerLine`: Buyer part of the order line (see [Buyer line](#buyer-line))
- `supplierLine`: Supplier part of the order line (see [Supplier line](#supplier-line))
- `confirmedLine`: Order line as agreed between buyer and supplier
- `statusLine`: Current order line values (see [Status line](#status-line))
- `indicators.deliveryOverdue`: `true` when the order line is overdue
- `status.processStatus`: Order line's [Line process status](#line-process-status)
- `status.inProgressStatus`: Order line's [Line in progress status](#line-in-progress-status)
- `status.logisticsStatus`: Order line's [Line logistics status](#line-logistics-status)
- `eventDates`: Key line event timestamps
- `mergedItemDetails`: Detailed part information (see [Item details](#item-details))
- `lastUpdatedAt`: Latest timestamp when the order line was changed

### Buyer Line

The `lines.buyerLine` section echoes your original order line fields as explained in [Issue a new order](../issue/#lines).

- `position`: Line position within the purchase order (unique and immutable within the order, empty for newly split lines)
- `originalPosition`: Position of the original order line when the current order line was split.

{% hint style="info" %}
When converting from delivery schedules to single deliveries, Tradecloud automatically splits each delivery line into a separate order line. Each order line contains one `lines.statusLine.scheduledDelivery` and maintains the relationship to the original order line through the `originalPosition` value.
{% endhint %}

### Supplier Line

The `lines.supplierLine` section contains:

- `salesOrderNumber`: Sales order number in the supplier's ERP system
- `salesOrderPosition`: Position within the supplier's sales order
- `description`: Additional description of this line by the supplier
- `requests`: Supplier requests for different delivery schedule, prices, or charge lines
- `properties`: Key-value based custom fields added by the supplier
- `notes`: Simple custom fields added by the supplier
- `documents`: Meta data of attached documents from the supplier

{% page-ref page="download-document.md" %}

### Status Line

The `lines.statusLine` represents current order line values related to the current process status. The `InclRequests` fields also include `InProgress` status and related open request values.

#### Single Delivery Fields

- `lines.statusLine.scheduledDelivery`: Current delivery line with `Issued` or `Confirmed` values
- `lines.statusLine.scheduledDeliveryInclRequests`: Current delivery line with `Issued`, `InProgress` requests, or `Confirmed` values

##### Scheduled Delivery Fields

- `date`: Delivery date (ISO 8601 format `yyyy-MM-dd`)
- `quantity`: Quantity (decimal format, e.g. `1234.56`)
- `status`: Optional [Scheduled delivery logistics status](#scheduled-delivery-logistics-status)
- `etd`: Optional Estimated Time of Departure (ISO 8601 date `yyyy-MM-dd`)
- `eta`: Optional Estimated Time of Arrival (ISO 8601 date `yyyy-MM-dd`)

##### Scheduled Delivery Logistics Status

The delivery line logistics status is one of:

- `Open`: No or partial quantity Produced, ReadyToShip, Shipped or Delivered
- `Produced`: Delivery line quantity produced by the supplier
- `ReadyToShip`: Delivery line quantity ready to be shipped by the supplier
- `Shipped`: Delivery line quantity shipped by the supplier
- `Delivered`: Delivery line quantity delivered to the buyer

#### Prices

- `lines.statusLine.prices`: Current prices with `Issued` or `Confirmed` values
- `lines.statusLine.pricesInclRequests`: Current prices with `Issued`, `InProgress` requests, or `Confirmed` values

##### Price Fields

- `grossPrice`: Gross price (used with `discountPercentage`)
- `discountPercentage`: Discount percentage (used with `grossPrice`)
- `netPrice`: Net price
  - `priceInTransactionCurrency`: Price in supplier's transaction currency
    - `value`: Price value (decimal format, e.g. `1234.56`)
    - `currencyIso`: 3-letter currency code (ISO 4217)
  - `priceInBaseCurrency`: Price in your base currency
    - `value`: Price value (decimal format, e.g. `1234.56`)
    - `currencyIso`: 3-letter currency code (ISO 4217)
- `priceUnitOfMeasureIso`: 3-letter price unit (ISO 80000-1)
- `priceUnitQuantity`: Item quantity at which the price applies

{% hint style="info" %}
It is recommended to use `netPrice` for simplicity, or alternatively use `grossPrice` together with `discountPercentage`.
{% endhint %}

### Line Status

#### Line Process Status

The line process status is one of:

- `Issued`: Line (re)issued by the buyer
- `InProgress`: Line under negotiation between buyer and supplier
- `Confirmed`: Line agreed between buyer and supplier
- `Rejected`: Line rejected by supplier
- `Completed`: Line completed at the buyer
- `Cancelled`: Line cancelled by the buyer

#### Line In Progress Status

When an order line's `processStatus` is `InProgress`, the in progress status is one of:

- `OpenSupplierProposal`: Open proposal from the supplier
- `RejectedSupplierProposal`: Supplier proposal was rejected with no other open requests
- `ReissuedRejectedLine`: Rejected order line reissued by the buyer
- `OpenSupplierReopenRequest`: Open reopen request from the supplier
- `OpenBuyerReopenRequest`: Open reopen request from the buyer
- `RevertedCompletedLine`: Line completion was reverted

#### Line Logistics Status

The line logistics status is one of:

- `Open`: No or partial quantity Produced, ReadyToShip, Shipped or Delivered
- `Produced`: Line quantity produced by the supplier
- `ReadyToShip`: Line quantity ready to be shipped by the supplier
- `Shipped`: Line quantity shipped by the supplier
- `Delivered`: Line quantity delivered to the buyer
- `Cancelled`: Line cancelled by the buyer

### Item Details

The `lines.mergedItemDetails` contains item details from both buyer and supplier:

- `countryOfOriginCodeIso2`: ISO 3166-1 alpha-2 country code of origin
- `combinedNomenclatureCode`: Classification code for customs and EU external trade statistics
- `netWeight`: Net weight of one item
- `netWeightUnitOfMeasureIso`: Net weight unit (ISO 80000-1)
- `dangerousGoodsCodeUnece`: UN number for dangerous goods identification
- `serialNumber`: Unique identifier assigned to an item
- `batchNumber`: Identification number assigned to a particular quantity or lot of material

{% hint style="info" %}
The buyer may send item details to inform the supplier about part information.
The supplier may check, change and add item details if they are not correct or incomplete.
The merged details contain the original buyer information combined with supplier changes or additions.
{% endhint %}
