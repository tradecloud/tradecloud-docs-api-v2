---
description: How to receive a purchase order response sent by the supplier
---

# Receive an Order Response

Tradecloud sends purchase order responses to buyers when order events are triggered.

## Receiving Methods

### Choose Your API Method

You must choose between two methods to receive order responses:

- **Webhook API (Push)**: Tradecloud pushes responses to your system
- **Polling API (Pull)**: Your system periodically checks for new responses

For details on choosing between these methods:

{% page-ref page="../../../api/webhook-vs-polling.md" %}

### Choose Your Delivery Format

You must also choose between two delivery formats:

- **Delivery Schedule**: Multiple deliveries per order line
- **Single Delivery**: One delivery per order line

For details on choosing between these formats:

{% page-ref page="../../../api/delivery-schedule.md" %}

If you're using single delivery format, please see:

{% page-ref page="single-delivery-order-response.md" %}

## Implementation Options

### Using the Webhook API

Use the [POST order webhook](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-connector/specs.yaml#/order-webhook%20endpoints/webhookPost) endpoint.

- `eventName`: Contains the [order event name](https://docs.tradecloud1.com/connectors/webhook-connector/order-events)
- `orderEvent`: Contains the actual order event

### Using the Polling API

Use the [POST poll](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-search/specs.yaml#/order-search/pollOrdersRoute) endpoint.

- `order`: Contains the actual order in its current state

## Response Structure

This section assumes you're using delivery schedules with either the `orderEvent` webhook API or the `order` polling API.

### Order Header

The order header contains:

- `id` (in `order`) or `orderId` (in `orderEvent`): Tradecloud order identifier
- `buyerOrder`: Buyer part of the order (see [Buyer order](#buyer-order))
- `supplierOrder`: Supplier part of the order (see [Supplier order](#supplier-order))
- `indicators.deliveryOverdue`: `true` when at least one order line is overdue
- `status.processStatus`: Aggregate of all line statuses (see [Order process status](#order-process-status))
- `status.logisticsStatus`: Aggregate of all line statuses (see [Order logistics status](#order-logistics-status))
- `version`: Tradecloud order version number
- `eventDates`: Key order event timestamps
- `meta`: Meta information, including source and trace info
- `lastUpdatedAt`: Latest timestamp when the order was changed (useful for polling)

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
- `confirmedLine`: Order line as agreed between buyer and supplier (see [Confirmed line](#confirmed-line))
- `deliverySchedule`: Current aggregated delivery schedule (see [Delivery schedule](#delivery-schedule))
- `deliveryScheduleIncludingRequests`: Current aggregated delivery schedule including requests
- `prices`: Current prices (see [Prices](#prices))
- `pricesIncludingRequests`: Current prices including any open supplier or buyer requests
- `indicators.deliveryOverdue`: `true` when the order line is overdue
- `status.processStatus`: Order line's [Line process status](#line-process-status)
- `status.inProgressStatus`: Order line's [Line in progress status](#line-in-progress-status)
- `status.logisticsStatus`: Order line's [Line logistics status](#line-logistics-status)
- `eventDates`: Key line event timestamps
- `mergedItemDetails`: Detailed part information (see [Item details](#item-details))
- `lastUpdatedAt`: Latest timestamp when the order line was changed (useful for polling)

### Buyer Line

The `lines.buyerLine` section echoes your original order line fields as explained in [Issue a new order](../issue/#lines).

- `position`: Line position within the purchase order

### Supplier Line

The `lines.supplierLine` section contains:

- `salesOrderNumber`: Sales order number in the supplier's ERP system
- `salesOrderPosition`: Position within the supplier's sales order
- `description`: Additional description of this line by the supplier
- `requests`: Supplier requests for different delivery schedule, prices, or charge lines (see [Supplier requests](#supplier-requests))
- `properties`: Key-value based custom fields added by the supplier
- `notes`: Simple custom fields added by the supplier
- `documents`: Meta data of attached documents from the supplier

{% page-ref page="download-document.md" %}

#### Supplier Requests

- `lines.supplierLine.requests.proposal`: Supplier proposal for different delivery schedule, prices, and/or charge lines
- `lines.supplierLine.requests.reopenRequest`: Supplier request to reopen a confirmed order line with changes

Request details include:

- `deliverySchedule`: Requested alternative delivery schedule
- `prices`: Requested alternative prices
- `chargeLines`: Requested alternative charge lines (see [Charge lines](#charge-lines))
- `reason`: Reason for this request given by the supplier
- `status`: [Request status](#request-status)

##### Request Status

The request status is one of:

- `Open`: Requested by one party, awaiting approval or rejection by the other party
- `Approved`: Request approved by the other party
- `Rejected`: Request rejected by the other party
- `Closed`: Request closed because it is no longer relevant

{% hint style="warning" %}
If the request status is `Open`, the other party must approve or reject it.
{% endhint %}

### Confirmed Line

The `lines.confirmedLine` section represents the agreed order line between buyer and supplier.

{% hint style="warning" %}
Only if the process status is `Confirmed` is the line agreed between buyer and supplier.
{% endhint %}

- `lines.confirmedLine.deliverySchedule`: Agreed delivery schedule
- `lines.confirmedLine.prices`: Agreed prices
- `lines.confirmedLine.chargeLines`: Agreed charge lines (see [Charge lines](#charge-lines))

### Delivery Schedule

When using `order` or `orderEvent`, the delivery schedule is used.

{% hint style="info" %}
The `lines.deliverySchedule` and `lines.prices` fields provide a simpler alternative to the delivery schedule and prices fields in different places like `buyerLine`, `buyerLine.requests`, `supplierLine.requests`, and `confirmedLine`.
{% endhint %}

- `lines.deliverySchedule`: Current delivery schedule with either `Issued` or `Confirmed` values

{% hint style="warning" %}
The `lines.deliverySchedule` field does **NOT include any open supplier or buyer request**. Either the `Issued` or `Confirmed` values are returned, depending on the line status.
{% endhint %}

- `lines.deliveryScheduleIncludingRequests`: Current delivery schedule with either `Issued`, `In Progress`, or `Confirmed` values

{% hint style="warning" %}
The `lines.deliveryScheduleIncludingRequests` field **does include any open supplier or buyer request**. The `Issued`, proposal or reopen request, or `Confirmed` values are returned, depending on the line and request status.
{% endhint %}

#### Delivery Schedule Fields

- `position`: Optional position in the delivery schedule (distinct from `line.position`)
- `date`: Delivery date (ISO 8601 format `yyyy-MM-dd`)
- `quantity`: Quantity (decimal format, e.g., `1234.56`)

##### Logistics Fields

Additional logistics fields available in the order line level delivery schedule:

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

### Prices

- `lines.prices`: Current prices with either `Issued` or `Confirmed` values

{% hint style="warning" %}
The `lines.prices` field does **NOT include any open supplier or buyer request**. Either the `Issued` or `Confirmed` values are returned, depending on the line status.
{% endhint %}

- `lines.pricesIncludingRequests`: Current prices with either `Issued`, `In Progress`, or `Confirmed` values

{% hint style="warning" %}
The `lines.pricesIncludingRequests` field **includes any open supplier or buyer request**. The `Issued`, proposal or reopen request, or `Confirmed` values are returned, depending on the line and request status.
{% endhint %}

#### Price Fields

- `grossPrice`: Gross price (used with `discountPercentage`)
- `discountPercentage`: Discount percentage (used with `grossPrice`)
- `netPrice`: Net price
  - `priceInTransactionCurrency`: Price in supplier's transaction currency
    - `value`: Price value (decimal format, e.g., `1234.56`)
    - `currencyIso`: 3-letter currency code (ISO 4217)
  - `priceInBaseCurrency`: Price in your base currency
    - `value`: Price value (decimal format, e.g., `1234.56`)
    - `currencyIso`: 3-letter currency code (ISO 4217)
- `priceUnitOfMeasureIso`: 3-letter price unit (ISO 80000-1)
- `priceUnitQuantity`: Item quantity at which the price applies (typically 1 or 100)

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

### Charge Lines

Additional cost lines independent of order line prices:

- `position`: Position identifier for the charge line
- `chargeTypeCode`: Charge reason code according to [UNCL7161](https://docs.peppol.eu/poacc/upgrade-3/codelist/UNCL7161/)
- `chargeDescription`: Free text description (e.g., "Transport costs")
- `quantity`: Quantity of this charge line
- `price`: Price of this charge line
  - `priceInTransactionCurrency`: Price in supplier's transaction currency
    - `value`: Price value (decimal format, e.g., `1234.56`)
    - `currencyIso`: 3-letter currency code (ISO 4217)
  - `priceInBaseCurrency`: Price in your base currency (optional)
    - `value`: Price value (decimal format, e.g., `1234.56`)
    - `currencyIso`: 3-letter currency code (ISO 4217)
- `priceUnitOfMeasureIso`: 3-letter price unit (ISO 80000-1)

### Item Details

The `lines.mergedItemDetails` contains item details from both buyer and supplier:

- `countryOfOriginCodeIso2`: ISO 3166-1 alpha-2 country code of origin
- `combinedNomenclatureCode`: Classification code for customs and EU trade statistics
- `netWeight`: Net weight of one item
- `netWeightUnitOfMeasureIso`: Net weight unit (ISO 80000-1)
- `dangerousGoodsCodeUnece`: UN number for dangerous goods identification
- `serialNumber`: Unique identifier assigned to an item
- `batchNumber`: Identification number for a particular quantity/lot of material

{% hint style="info" %}
The buyer may send item details to inform the supplier about part information.
The supplier may check, change, and add item details if they are not correct or incomplete.
The merged details contain the original buyer information combined with supplier changes or additions.
{% endhint %}
