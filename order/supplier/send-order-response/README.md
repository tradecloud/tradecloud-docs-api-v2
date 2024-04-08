---
description: How to send a purchase order response to your buyer.
---

# Send order response

As a supplier you can send either a **new or updated** purchase order response to your buyer.

{% hint style="warning" %}
The order response should only contain **order lines** that are **new or changed**. Sending an unchanged order line could trigger an unexpected line status change in Tradecloud.
{% endhint %}

## Order process

After sending an order response to Tradecloud the order lines **process status may change**:

When the order line has process status `Issued`:

* When`indicators.accepted` is set the process status will become`Confirmed`
* When`indicators.rejected` is set the process status will become`Rejected`
* When the by supplier **responded** `delivery schedule` and `prices` are **equal** to the by buyer **requested** `delivery schedule` and `prices` the process status will become `Confirmed`
* When the **responded** `delivery schedule` and `prices` are **NOT** equal to the **requested** `delivery schedule` and `prices` the process status will become `InProgress` and a **proposal** task for the buyer will be created.

When the order line has process status `InProgress`:

* When`indicators.accepted` is set the process status will become`Confirmed`
* When`indicators.rejected` is set the process status will become`Rejected`
* When the by supplier **responded** `delivery schedule` and `prices` are **equal** to the by buyer

  **requested** `delivery schedule` and `prices` the process status will become `Confirmed`

* When the **responded** `delivery schedule` and `prices` are **NOT** equal to the **requested** `delivery schedule` and `prices` the process status will stay `InProgress`.

When the order line has process status `Confirmed`:

* When the by supplier **responded** `delivery schedule` and `prices` are **NOT** equal to the **confirmed** `delivery schedule` and `prices` the process status will become `InProgress` and a **reopen request** task for the buyer will be created.
* When the **responded** `delivery schedule` and `prices` are **equal** to the **confirmed** `delivery schedule` and `prices` the process status will stay `Confirmed`

{% hint style="warning" %}
This [reopen request](../reopen.md) feature is under development and API and documentation may change.
{% endhint %}

When the order line already has process status `Rejected`the process status will **NOT** change.

When the order line already has process status `Completed` the process status will **NOT** change.

When the order line already has process status `Cancelled` the process status will **NOT** change.

## Endpoint

Use the [Send order response](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/supplier-endpoints/sendOrderResponseBySupplierRoute) endpoint to send an order response to Tradecloud.

{% hint style="info" %}
When sending an order response the provided buyer account number and purchase order number will be verified. 
{% endhint %}

## Order

* `companyId`: the optional Tradecloud company identifier. You only have to provide a companyId when your integration user account has multiple company authorization.
* `buyerAccountNumber`: the buyer account number as known in your ERP system.

{% hint style="warning" %}
The `buyerAccountNumber` should be set in the Tradecloud connection in the portal, after the connection request has been accepted by the other party.
{% endhint %}

* `purchaseOrderNumber`: the purchase order number as sent by the buyer.
* `contact.email`: the supplier employee responsible for this order. The user with this email address should be active in Tradecloud.

{% hint style="warning" %}
`buyerAccountNumber` and `contact.email` should be unique within your company and never change. Never renumber or re-use numbers or code's.
{% endhint %}

### Other order fields

* `description`: a free format additional description of this order.
* `indicators.accepted`: explicitly **accept** the order as is, the responded lines `delivery schedule` and `prices` will be ignored.
* `indicators.rejected`: explicitly **reject** the order, the responded lines`delivery schedule` and `prices`will be ignored.
* Additional `indicators`:

{% page-ref page="../cancel.md" %}

* `properties`: are key-value based custom fields. You can use as many as needed, but too many will clutter the portal. Use `\n` for a new line in the value.
* `notes`: are simple custom fields. You can use as many as needed, but too many will clutter the portal. Use `\n` for a new line.

## Lines

* `lines`: a purchase order response contains one or multiple lines. A purchase order line contains at least the position and delivery schedule. It is structured as a JSON element in the `lines` JSON array. 
  * `purchaseOrderLinePosition`: the line position within the purchase order.

{% hint style="warning" %}
The supplier must echo the `purchaseOrderLinePosition` as sent by the buyer.
{% endhint %}

### Item

{% hint style="info" %}
It is not possible to propose an alternative item.  
If you need this feature, send a request to support.
{% endhint %}

### Item Details

* `lines.itemDetails`: detailed part information changed by the supplier.

{% hint style="info" %}
The buyer may send item details to inform the supplier about part information.  
The supplier may check, change and add item details if they are not correct or incomplete.
{% endhint %}

* `countryOfOriginCodeIso2`: The ISO 3166-1 alpha-2 country code of manufacture, production, or growth where an article or product comes from.
* `combinedNomenclatureCode`: A tool for classifying goods, set up to meet the requirements both of the Common Customs Tariff and of the EU's external trade statistics.
* `netWeight`: Net weight of one item.
* `netWeightUnitOfMeasureIso`: Net weight unit according to ISO 80000-1.
* `dangerousGoodsCodeUnece`: UN numbers or UN IDs are four-digit numbers that identify dangerous goods, hazardous substances and articles in the framework of international transport.
* `serialNumber`: is an unique identifier assigned incrementally or sequentially to an item, to uniquely identify it.
* `batchNumber`: is an identification number assigned to a particular quantity or lot of material from a single manufacturer

### Responded planned delivery schedule

* `lines.deliverySchedule`: the responded planned delivery schedule. Provide at least one or multiple delivery schedule lines.
  * `position`: the optional position in the delivery schedule. Not to be confused with the `line.position`.
  * `date`: the responded delivery date of this delivery schedule position.  If the delivery date is yet unknown, leave this date empty.  If the date is not equal to the requested date, when possible provide a `reason` , see below. Date has ISO 8601 date `yyyy-MM-dd` format. See also [Standards](../../api/standards.md).
  * `quantity`: the responded quantity of this delivery schedule position.  If the quantity that can be delivered is yet unknown, leave this quantity empty.  If the quantity is not equal to the requested date, when possible provide a `reason` , see below. Quantity has a decimal `1234.56` format with any number of digits.

{% hint style="warning" %}
The supplier must echo the `deliverySchedule.position` as sent by the buyer.
When sending a new delivery line do NOT provide a `position`. The buyer will assign a `position`.
{% endhint %}

### Responded prices

* `lines.prices`: the responded price. Advised is to provide only `netPrice` for its simplicity, or alternatively `grossPrice` together with `discountPercentage`. 
    * `grossPrice`: the gross price. Used together with `discountPercentage`.
    * `discountPercentage`: the discount percentage. Used together with `grossPrice`.
    * `netPrice`: the net price.
      * `priceInTransactionCurrency`: at least provide a price in the transaction currency, like `CNY` in China.
        * `value`: the price value has a decimal `1234.56` format with any number of digits.
        * `currencyIso`: the 3-letter currency code according to ISO 4217, like `EUR`, `USD` and `CNY`.
      * `priceInBaseCurrency`: optionally provide a price in your base currency, like `EUR` in the EU.
        * `value`: the price value has a decimal `1234.56` format with any number of digits.
        * `currencyIso`: the 3-letter currency code according to ISO 4217, like `EUR`.
    * `priceUnitOfMeasureIso`: the price unit according to ISO 80000-1. The purchase unit and price unit may be different.
    * `priceUnitQuantity`: the item quantity at which the price applies. Typically this is 1 \(unit price\) or 100 \(the price applies to 100 items\)

### Responded charge lines

* `lines.chargeLines`: the requested additional cost lines of an order line, independent of the order line prices, like transport, packing, administration, inspection and certification costs.
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

{% hint style="warning" %}
The supplier must echo the `chargeLines.position` as sent by the buyer. 
When sending a new charge line do NOT provide a `position`. The buyer will assign a `position`.
{% endhint %}

#### Other line fields

* `description`: a free format additional description of this line
* `indicators.accepted`: explicitly **accept** the order line as is, the responded `delivery schedule` and `prices` will be ignored.
* `indicators.rejected`: explicitly **reject** the order line, the responded`delivery schedule` and `prices`will be ignored. When possible provide the `reason` , see below.
* Additional `indicators`:

{% page-ref page="../cancel.md" %}

* `properties`: are key-value based custom fields. You can use as many as needed, but too many will clutter the portal.  Use `\n` for a new line in the value.
* `notes`: are simple custom fields.You can use as many as needed, but too many will clutter the portal. Use `\n` for a new line.
* `reason`: optional reason in case:
  * the order line is **rejected**
  * the **responded** `delivery schedule` and `prices` are **NOT** **equal** to the **requested** or **confirmed**`delivery schedule` and `prices`
  * a [**reopen** request](../reopen.md)
  * a [**cancel** request](../cancel.md)

## Order response meta data

* `erpResponseDateTime`: Date and time the order was responded from your ERP system.  `DateTime` has ISO 8601 local date/time format `yyyy-MM-ddThh:mm:ss`. See also [Standards](../../api/standards.md).
* `erpRespondedBy`: the user email or user name as known in your ERP system who responded this order

## Response

When the `/api-connector/order-response` API method returns HTTP status code 200, the order response was successfully queued for processing by Tradecloud. Processing takes usually less then a second, after which the order response is available in the portal and is forwarded to the buyer ERP integration.
