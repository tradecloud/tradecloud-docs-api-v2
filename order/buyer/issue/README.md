---
description: How to issue a new purchase order as a buyer
---

# Issue a New Order

As a buyer, you can send either a **new order** or an [**updated order**](../update.md) to your supplier.

## Order Process

{% hint style="info" %}
New order lines will have order process status `Issued` and logistics status `Open`
{% endhint %}

## Sending methods

### Delivery schedule options

Choose the appropriate endpoint based on your ERP system's delivery handling capabilities:

- Use the [Send order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderByBuyerRoute) endpoint when your ERP system supports delivery schedules natively
- Use the [Send single delivery order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendSingleDeliveryByBuyerRoute) endpoint for single delivery per order line

For more details on choosing between delivery schedule options:

{% page-ref page="delivery-schedule.md" %}

{% hint style="info" %}
When sending an order, the provided supplier account number will be verified.
{% endhint %}

## Order structure

### Order header

- `companyId`: Optional Tradecloud company identifier. Only required when your integration user account has authorization for multiple companies.
- `buyerParty`: Optional legal entity that purchases the goods or services. See [Company party](#company-party).
- `buyerAccountingParty`: Optional legal entity that receives and handles the invoice. The supplier must send the invoice to this party when specified. See [Company party](#company-party).
- `supplierAccountNumber`: Supplier account number as known in your ERP system.

{% hint style="warning" %}
The `supplierAccountNumber` must be set in the Tradecloud connection in the portal, after the connection request has been accepted by the other party.
{% endhint %}

- `supplierParty`: Optional legal entity that sells the goods or services. See [Company party](#company-party).
- `purchaseOrderNumber`: Purchase order number as known in your ERP system.

{% hint style="warning" %}
The `purchaseOrderNumber` must not contain whitespace characters.
{% endhint %}

- `destination`: Delivery destination of this order as known in your ERP system
- `contact.email`: Buyer employee responsible for this order. The user with this email address should be active in Tradecloud.
- `supplierContact.email`: If known, the supplier employee responsible for this order. The user with this email address should be active in Tradecloud.

{% hint style="warning" %}
`id`, `supplierAccountNumber`, `purchaseOrderNumber`, `destination.code` and `contact.email` should be unique within your company and never change. Never renumber or reuse identifiers, numbers or codes.
{% endhint %}

### Company party

The optional buyer, buyer accounting, or supplier company party:

- `id`: Optional identifier for the party (e.g., GLN)
- `idScheme`: Optional scheme providing context to the identifier (e.g., "KvK", "GLN")
- `names`: Legal names of the party (at least one recommended)
- `addressLines`: Location address lines (at least one recommended)
- `postalCode`: Location postal code (required when `addressLines` are provided)
- `city`: Location city (required when `addressLines` are provided)
- `countryCodeIso2`: ISO 3166-1 alpha-2 country code (required when `addressLines` are provided)
- `countryName`: Optional country name

### Additional order fields

- `description`: Free format additional description
- `terms`: Order terms as agreed with your supplier
- `indicators`: Various order level indicators (see [Indicators](indicators.md))
- `properties`: Key-value based custom fields (use `\n` for new lines in values)
- `notes`: Simple custom fields (use `\n` for new lines)
- `labels`: Value-added services labels on order level
- `documents`: Attached documents (limited to 100 per order header, see [Attach Document](attach-document.md))
- `orderType`: Order type (`Purchase`, `Forecast`, or `RFQ`; default is `Purchase`)

## Order lines

The `lines` array contains one or multiple order lines (limited to 500 per order):

- `position`: Required line position identifier within the purchase order
- `originalPosition`: Optional original line position identifier within the purchase order
- `row`: Optional row label for this position (only use when your ERP distinguishes between position and row)

{% hint style="warning" %}
`lines.position` should be unique within the order and never change. Never renumber or reuse position numbers.
{% endhint %}

{% hint style="info" %}
When order lines contain an `originalPosition` reference, Tradecloud automatically merges their `scheduledDelivery` and `actualDelivery` properties into the delivery schedule and history of the line with the matching position number.
{% endhint %}

### Item information

`lines.item`: The item (article, goods) to be delivered:

- `number`: Item code/number as known in your ERP
- `revision`: Revision (version) of this item number
- `name`: Item short name
- `purchaseUnitOfMeasureIso`: Purchase unit according to ISO 80000-1 (e.g., `PCE`)
- `supplierItemNumber`: Item code/number as known at the supplier (required for wholesale suppliers)

{% hint style="warning" %}
`item.number` and `item.supplierItemNumber` are optional and may be empty (e.g., for service or RFQ orders).

Leaving both empty is not recommended for integrated suppliers, as they might reject the order line.

`item.number` should be unique within your company and never change.
{% endhint %}

### Item details

`lines.itemDetails`: Detailed part information provided by the buyer:

- `countryOfOriginCodeIso2`: ISO 3166-1 alpha-2 country code of origin
- `combinedNomenclatureCode`: Classification code for customs and EU trade statistics
- `netWeight`: Net weight of one item
- `netWeightUnitOfMeasureIso`: Net weight unit (ISO 80000-1)
- `dangerousGoodsCodeUnece`: UN number for dangerous goods identification
- `serialNumber`: Unique identifier assigned to an item
- `batchNumber`: Identification number for a particular quantity/lot of material

{% hint style="info" %}
The supplier may check, change, and add item details if needed.
The webhook `orderEvent.lines.itemDetails.mergedItemDetails` will contain the merged information.
{% endhint %}

### Delivery information

Choose one of these options:

- Use `lines.deliverySchedule` when your ERP system supports delivery schedules natively
- Use `lines.scheduledDelivery` when using single delivery per order line

For details, see [Delivery schedule](delivery-schedule.md).

### Pricing information

`lines.prices`: The requested price information:

- `grossPrice`: Gross price (use with `discountPercentage`)
- `discountPercentage`: Discount percentage (use with `grossPrice`)
- `netPrice`: Net price (recommended for simplicity)
  - `priceInTransactionCurrency`: Price in supplier's transaction currency (required)
    - `value`: Price value (decimal format)
    - `currencyIso`: 3-letter currency code (ISO 4217)
  - `priceInBaseCurrency`: Price in your base currency (optional)
    - `value`: Price value (decimal format)
    - `currencyIso`: 3-letter currency code (ISO 4217)
- `priceUnitOfMeasureIso`: Price unit (ISO 80000-1)
- `priceUnitQuantity`: Item quantity at which the price applies (typically 1 or 100)

### Charge lines

`lines.chargeLines`: Additional cost lines independent of order line prices:

- `position`: Position identifier for the charge line
- `chargeTypeCode`: Charge reason code according to [UNCL7161](https://docs.peppol.eu/poacc/upgrade-3/codelist/UNCL7161/)
- `chargeDescription`: Free text description (e.g., "Transport costs")
- `quantity`: Quantity of this charge line
- `price`: Price of this charge line
  - `priceInTransactionCurrency`: Price in supplier's transaction currency (required)
  - `priceInBaseCurrency`: Price in your base currency (optional)
- `priceUnitOfMeasureIso`: Price unit (ISO 80000-1)

{% hint style="warning" %}
Single delivery with charge lines spread over multiple order lines is not supported. Contact support if needed.
{% endhint %}

### Additional line fields

- `description`: Free format additional description
- `terms`: Line terms agreed with your supplier
  - `contractNumber`: Agreed framework contract number
  - `contractPosition`: Related position within the framework contract
- `projectNumber`: Your project number reference
- `productionNumber`: Your production number reference
- `salesOrderNumber`: Your sales order reference
- `indicators`: Line level indicators (see [Indicators](indicators.md))
- `properties`: Key-value based custom fields
- `documents`: Attached documents (limited to 100 per line, see [Attach Document](attach-document.md))
- `notes`: Simple custom fields
- `labels`: Value-added services labels on line level

## Meta data

- `erpIssueDateTime`: Date/time the order was issued in your ERP (ISO 8601 format `yyyy-MM-ddThh:mm:ss`)
- `erpIssuedBy`: User email or name from your ERP who issued this order

## Response

When the API returns HTTP status code 200, the order was successfully queued for processing. Processing typically takes less than a second, after which the order is available in the portal and forwarded to the supplier's ERP integration.
