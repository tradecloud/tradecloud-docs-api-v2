---
description: How to send a purchase order response to your buyer.
---

# Send order response

As a supplier you can send either a new or updated purchase order response to your buyer.

## Send an order response to Tradecloud <a id="send-a-new-order-to-tradecloud"></a>

After sending an order response to Tradecloud the order lines **process status may change**:

When the order line has status `Issued`: 

* When`indicators.accepted` is set the process status will become`Confirmed`
* When`indicators.rejected` is set the process status will become`Rejected`
* When the by supplier **responded** `delivery schedule` and `prices` are **equal** to the by buyer **requested** `delivery schedule` and `prices` the process status will become `Confirmed`
* When the **responded** `delivery schedule` and `prices` are **NOT** equal to the **requested** `delivery schedule` and `prices` the process status will become `InProgress` and a **proposal** for the buyer will be created.

When the order line has status `InProgress`:

* When`indicators.accepted` is set the process status will become`Confirmed`
* When`indicators.rejected` is set the process status will become`Rejected`
* When the by supplier **responded** `delivery schedule` and `prices` are **equal** to the by buyer

   **requested** `delivery schedule` and `prices` the process status will become `Confirmed`

* When the **responded** `delivery schedule` and `prices` are **NOT** equal to the **requested** `delivery schedule` and `prices` the process status will stay `InProgress`.

When the order line has status `Confirmed`:

* When the by supplier **responded** `delivery schedule` and `prices` are **NOT** equal to the **confirmed** `delivery schedule` and `prices` the process status will become `InProgress` and a **reopen request** to the buyer will be created.
* When the **responded** `delivery schedule` and `prices` are **equal** to the **confirmed** `delivery schedule` and `prices` the process status will stay `Confirmed`

When the order line already has process status `Completed` the process status will **NOT** change.

When the order line already has process status `Cancelled` the process status will **NOT** change.

And the **logistics status may change**:

* When`indicators.shipped` is set the order line will have logistics status `Shipped`
* When the order line already has logistics status  `Delivered` the status will NOT change.

{% api-method method="post" host="https://api.accp.tradecloud1.com/v2" path="/order-integration/order-response" %}
{% api-method-summary %}
Send order response by supplier
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Bearer Access-Token
{% endapi-method-parameter %}

{% api-method-parameter name="Content-Type" type="string" required=true %}
application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="body" type="object" required=true %}
Order response JSON body, see below.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
S[end order response OpenAPI Specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-integration/specs.yaml#/supplier-endpoints/sendOrderResponseBySupplierRoute)
{% endhint %}

## Order

* `companyId`: your Tradecloud company identifier. You can find your company id in the URL when selecting "My company" in the portal dropdown menu. For example in `https://portal.accp.tradecloud1.com/company/06893bba-e131-4268-87c9-7fae64e16ee9` the last part `06893bba-e131-4268-87c9-7fae64e16ee9` is the company id.
* `buyerAccountNumber`: the buyer account number as known in your ERP system.
* `purchaseOrderNumber`: the purchase order number as sent by the buyer.
* `contact`: the supplier employee responsible for this order. You can either send his/her email or userName as known in your ERP system.

{% hint style="warning" %}
`buyerAccountNumber`, `contact.email` and `contact.userName` should be unique within your company and never change. Never renumber or re-use numbers or code's.
{% endhint %}

{% hint style="warning" %}
The `buyerAccountNumber` should be set on forehand in the Tradecloud connection with your supplier. You can set the account code when inviting a new connection or in the connection overview in the portal.
{% endhint %}

#### Other order fields

* `description`: a free format additional description of this order.
* `indicators.accepted`: explicitly **accept** the order as is, the responded lines `delivery schedule` and `prices` will be ignored.
* `indicators.rejected`: explicitly **reject** the order, the responded lines`delivery schedule` and `prices`will be ignored.
* Additional `indicators`:

{% page-ref page="../ship-goods.md" %}

{% page-ref page="../reopen-request.md" %}

{% page-ref page="../cancel-request.md" %}

* `properties`: are key-value based custom fields. You can use as many as needed, but too many will clutter the portal. Use `\n` for a new line in the value.
* `notes`: are simple custom fields. You can use as many as needed, but too many will clutter the portal. Use `\n` for a new line.
* `documents`: contain meta data and link of attached documents, see:

{% page-ref page="attach-document.md" %}

## Lines

* `lines`: a purchase order response contains one or multiple lines
* `line`: a purchase order line which contains at least the position and delivery schedule. It is structured as a JSON element in the `lines` JSON array. 
* `purchaseOrderLinePosition`: the line position within the purchase order as sent by the buyer.

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

* `line.deliverySchedule`: the responded planned delivery schedule. Provide at least one or multiple delivery schedule lines.
* `deliverySchedule.position`: the optional position in the delivery schedule. Not to be confused with the `line.position`
* `deliverySchedule.date`: the responded delivery date of this delivery schedule position.  If the delivery date is yet unknown, leave this date empty.  If the date is not equal to the requested date, when possible provide a `reason` , see below. Date has ISO 8601 date `yyyy-MM-dd` format. See also [Standards](../../api/standards.md).
* `deliverySchedule.quantity`: the responded quantity of this delivery schedule position.  If the quantity that can be delivered is yet unknown, leave this quantity empty.  If the quantity is not equal to the requested date, when possible provide a `reason` , see below. Quantity has a decimal `1234.56` format with any number of digits.

{% hint style="warning" %}
`deliverySchedule.position` should be unique within the delivery schedule and never change. Never renumber or re-use `deliverySchedule.position`s.
{% endhint %}

### Responded prices

* `lines.prices`: the responded price. Advised is to provide only `netPrice` for its simplicity, or alternatively `grossPrice` together with `discountPercentage`. 
* `priceInTransactionCurrency`: at least provide a price in the transaction currency, like `CNY` in China.
* `priceInBaseCurrency`: optionally provide a price in your base currency, like `EUR` in the EU.
* `value`: the price value has a decimal `1234.56` format with any number of digits.
* `currencyIso`: the 3-letter currency code according to ISO 4217, like `EUR`, `USD` and `CNY`
* `priceUnitOfMeasureIso`: the price unit according to ISO 80000-1. The purchase unit and price unit may be different.
* `priceUnitQuantity`: the item quantity at which the price applies. Typically this is 1 \(unit price\) or 100 \(the price applies to 100 items\)

#### Other line fields

* `description`: a free format additional description of this line
* `indicators.accepted`: explicitly **accept** the order line as is, the responded `delivery schedule` and `prices` will be ignored.
* `indicators.rejected`: explicitly **reject** the order line, the responded`delivery schedule` and `prices`will be ignored. When possible provide the `reason` , see below.
* Additional `indicators`:

{% page-ref page="../ship-goods.md" %}

{% page-ref page="../reopen-request.md" %}

{% page-ref page="../cancel-request.md" %}

* `properties`: are key-value based custom fields. You can use as many as needed, but too many will clutter the portal.  Use `\n` for a new line in the value.
* `notes`: are simple custom fields.You can use as many as needed, but too many will clutter the portal. Use `\n` for a new line.
* `reason`: optional reason in case 
  * the order line is **rejected**
  * the **responded** `delivery schedule` and `prices` are **NOT** **equal** to the **requested** or **confirmed**`delivery schedule` and `prices`
  * a [**reopen** request](../reopen-request.md)
  * a [**cancel** request](../cancel-request.md)

## Order response meta data

* `erpResponseDateTime`: Date and time the order was responded from your ERP system.  `DateTime` has ISO 8601 local date/time format `yyyy-MM-ddThh:mm:ss`. See also [Standards](../../api/standards.md).
* `erpRespondedBy`: the user email or user name as known in your ERP system who responded this order

## Response

When the `/order-integration/order-response` API method returns HTTP status code 200, the order response was successfully queued for processing by Tradecloud. Processing takes usually less then a second, after which the order response is available in the portal and is forwarded to the buyer ERP integration.

