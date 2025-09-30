---
description: How to send a purchase order response to your buyer.
---

# Send order response

As a supplier, you can send a purchase order response to your buyer.

{% hint style="warning" %}
Each order response **must** contain **one or more order lines**.

The order response should only contain **order lines** that are **new or changed**.
{% endhint %}

## Order process

After sending an order response, the order line process status may change based on the current status:

### Status: Issued

The order line will become:

- `Confirmed` if:
  - The `accepted` indicator is set, OR
  - Responded delivery schedule and prices match the requested values
- `Rejected` if the `rejected` indicator is set
- `InProgress` if responded values differ from requested values (creates a proposal task for the buyer)

### Status: InProgress

The order line will become:

- `Confirmed` if:
  - The `accepted` indicator is set, OR
  - Responded delivery schedule and prices match the requested values
- `Rejected` if the `rejected` indicator is set
- Stays `InProgress` if responded values still differ from requested values

### Status: Confirmed

The order line will:

- Become `InProgress` if responded values differ from confirmed values (creates a reopen request task for the buyer)
- Stay `Confirmed` if responded values match the confirmed values

### Status: Completed or Cancelled

The process status will **not** change.

## Endpoint

Use the [Send order response](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/supplier-endpoints/sendOrderResponseBySupplierRoute) endpoint to send an order response to Tradecloud.

HTTP status code **200** or **202** means the order response was successfully verified or queued. 

Processing typically takes less than a second, after which:

- The provided buyer account number and purchase order number have been verified.
- The order response appears in the portal.
- The response is forwarded to the buyer's ERP integration.

## Order fields

### Required fields

- `buyerAccountNumber`: your buyer's account number as known in your ERP system
  - Must be set in in the Tradecloud portal after the connection is accepted
  - Must be unique within your company
- `purchaseOrderNumber`: the purchase order number sent by the buyer
- `lines`: Each order response must contain one or more lines:

### Optional fields

- `companyId`: Tradecloud company identifier (only needed if your integration user has multiple company authorizations)
- `contact.email`: email of the supplier employee responsible for this order
  - The user must be active in Tradecloud
- `description`: additional description of this order
- `indicators.accepted`: accept responded order lines as-is (its delivery schedule and prices will be ignored)
- `indicators.rejected`: reject responded order lines (its delivery schedule and prices will be ignored)
- `properties`: key-value custom fields (use `\n` for new lines)
- `notes`: simple text notes (use `\n` for new lines)

## Line fields

- `purchaseOrderLinePosition`: **required** - must match the position sent by the buyer

### Responded delivery schedule

At least one delivery schedule line is required:

- `position`: optional position in the delivery schedule
  - Echo the `position` from the buyer, OR leave empty
  - For new split delivery lines: omit the position (buyer will assign it)
  - If empty: preserve the original order and append new lines at the end
- `date`: delivery date in ISO 8601 format (`yyyy-MM-dd`)
  - Can be left empty if unknown
  - Provide a `reason` if different from the requested date
- `quantity`: delivery quantity in decimal format (e.g., `1234.56`)
  - Can be left empty if unknown
  - Provide a `reason` if different from the requested quantity

### Responded prices

**Recommended:** Use `netPrice` for simplicity, or use `grossPrice` + `discountPercentage`.

- `netPrice` OR `grossPrice` + `discountPercentage`:
  - `priceInTransactionCurrency`: **required**
    - `value`: decimal format (e.g., `1234.56`)
    - `currencyIso`: 3-letter ISO 4217 code (e.g., `EUR`, `USD`, `CNY`)
  - `priceInBaseCurrency`: optional
    - `value`: decimal format (e.g., `1234.56`)
    - `currencyIso`: 3-letter ISO 4217 code
- `priceUnitOfMeasureIso`: price unit (ISO 80000-1) - copied from buyer if empty
- `priceUnitQuantity`: quantity at which price applies (typically `1` or `100`) - copied from buyer if empty

### Responded charge lines

Additional costs independent of order line prices (e.g., transport, packing, inspection):

- `position`: identifier for the charge line
  - Echo the `position` from the buyer, OR
  - Omit for new charge lines (buyer will assign it)
- `chargeTypeCode`: **required** - charge reason code ([UNCL7161](https://docs.peppol.eu/poacc/upgrade-3/codelist/UNCL7161/))
- `chargeDescription`: **required** - text description (e.g., "Transport costs")
- `quantity`: **required** - quantity for this charge
- `price`: **required**
  - `priceInTransactionCurrency`: **required**
    - `value`: decimal format (e.g., `1234.56`)
    - `currencyIso`: 3-letter ISO 4217 code (e.g., `EUR`, `USD`, `CNY`)
  - `priceInBaseCurrency`: optional
    - `value`: decimal format
    - `currencyIso`: 3-letter ISO 4217 code
- `priceUnitOfMeasureIso`: price unit (ISO 80000-1)

### Other line fields

- `description`: additional description of this line
- `indicators.accepted`: accept the line as-is (delivery schedule, prices, and header indicators ignored)
- `indicators.rejected`: reject the line (delivery schedule, prices, and header indicators ignored)
- `reason`: explanation when:
  - The line is rejected
  - Responded values differ from requested or confirmed values
  - Sending a [reopen request](../reopen.md)
- `properties`: key-value custom fields (use `\n` for new lines)
- `notes`: simple text notes (use `\n` for new lines)

### Item

{% hint style="info" %}
It is not possible to propose an alternative item.  
If you need this feature, send a request to support.
{% endhint %}

### Item Details

You can check, change, or add item details if the buyer's information is incorrect or incomplete:

- `countryOfOriginCodeIso2`: ISO 3166-1 alpha-2 country code of origin
- `combinedNomenclatureCode`: goods classification code for customs and trade statistics
- `netWeight`: net weight of one item
- `netWeightUnitOfMeasureIso`: net weight unit (ISO 80000-1)
- `dangerousGoodsCodeUnece`: UN number for dangerous goods (4-digit)
- `serialNumber`: unique sequential identifier for the item
- `batchNumber`: identification number for a quantity/lot from a manufacturer

## Order response metadata

- `erpResponseDateTime`: date/time the order was responded in your ERP (ISO 8601 format: `yyyy-MM-ddThh:mm:ss`)
- `erpRespondedBy`: email or username of the person who responded to this order in your ERP
