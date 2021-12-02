---
description: How to issue a new purchase order as a buyer
---

# Issue a new order

As buyer you can send either a **new or** [**updated**](../update.md) purchase order to your supplier.

{% hint style="warning" %}
The order should only contain **order lines** that are **new or changed**. Sending an unchanged order line could trigger an unexpected line status change in Tradecloud.
{% endhint %}

## Order process

As a buyer you can send a new purchase order to Tradecloud.

{% hint style="info" %}
The new order lines will have order process status `Issued`and logistics status `Open`
{% endhint %}

{% api-method method="post" host="https://api.accp.tradecloud1.com/v2" path="/api-connector/order" %}
{% api-method-summary %}
Send order by buyer
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
Order JSON body
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}

{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %} 
Successfully verified and sent order.
{% endapi-method-response-example-description %}
{% endapi-method-response-example %}

{% api-method-response-example httpCode=202 %}
{% api-method-response-example-description %} 
Successfully queued order. The supplier account code has not yet been verified.
{% endapi-method-response-example-description %}
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %} 
Supplier not found.
{% endapi-method-response-example-description %}
{% endapi-method-response-example %}

{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
[Send order OpenAPI Specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderByBuyerRoute)
{% endhint %}

{% hint style="info" %}
When sending an order the provided supplier account number will be verified. 

Response status codes:
- 200 OK - the supplier account number exists and the order will be processed.
- 202 Accepted - the supplier verification has been skipped due to service unavailability and the order has been queued.
- 404 Not Found - the supplier account number has not been found. 
{% endhint %}

## Order

* `companyId`: the optional Tradecloud company identifier. You only have to provide a companyId when your integration user account has multiple company authorization.
* `supplierAccountNumber`: the supplier account number as known in your ERP system

{% hint style="warning" %}
The `supplierAccountNumber` should be set in the Tradecloud connection in the portal, after the connection request has been accepted by the other party.
{% endhint %}

* `purchaseOrderNumber`: the purchase order number as known in your ERP system.

{% hint style="warning" %}
The `purchaseOrderNumber` must not contain whitespace characters
{% endhint %}

* `destination`: the delivery destination of this order as known in your ERP system
* `contact.email`: the buyer employee responsible for this order. The user with this email address should be active in Tradecloud.
* `supplierContact.email`: if known, the supplier employee responsible for this order. The user with this email address should be active in Tradecloud.

{% hint style="warning" %}
`supplierAccountNumber`, `purchaseOrderNumber`, `destination.code` and `contact.email` should be unique within your company and never change. Never renumber or re-use numbers or code's.
{% endhint %}

### Other order fields

* `description`: a free format additional description of this order
* `terms`: the order terms as agreed with your supplier
* `indicators`:

When all order lines have no goods to be delivered, for example service, fee or text lines:

{% page-ref page="no-delivery-expected.md" %}

* `properties`: are key-value based custom fields. You can user as many as needed, but too many will clutter the portal. Use `\n` for a new line in the value.
* `notes`: are simple custom fields. You can user as many as needed, but too many will clutter the portal. Use `\n` for a new line.
* `labels`: value-added services labels on order level. Please note the practicable number of labels is dependent on the supplier.
* `documents`: contain meta data and link of attached documents, see:
* `orderType`: the order type, one of `Purchase` or `Forecast`. Default `Purchase`.

{% page-ref page="attach-document.md" %}

## Lines

* `lines`: a purchase order contains one or multiple lines
* `line`: a purchase order line which contains at least the position, item and delivery schedule. It is structured as a JSON element in the `lines` JSON array. 
* `position`: the required line position identifier within the purchase order
* `row`: the optional row label for this position. Only use a row when there is a distinction between position and row in your ERP system. Do NOT use row as identifier.

{% hint style="warning" %}
`lines.position` should be unique within the order and never change. Never renumber or re-use `position` numbers.
{% endhint %}

### Item

* `lines.item`: the item \(or article, goods\) to be delivered
* `lines.item.number`: the item code or number as known in your ERP
* `lines.item.revision`: the revision \(or version\) of this item number
* `lines.item.name`: the item short name
* `lines.item.purchaseUnitOfMeasureIso`: the purchase unit according to ISO 80000-1, a typical example is `PCE`
* `lines.item.supplierItemNumber`: the item code or number as known at the supplier. Advised in case of wholesale suppliers.

{% hint style="warning" %}
`item.number` should be unique within your company and never change. Never renumber or re-use `item.number`s.
{% endhint %}

### Item details

* `lines.itemDetails`: detailed part information initially provided by buyer.

{% hint style="info" %}
The buyer may send item details to inform the supplier about part information.  
The supplier may check, change and add item details if they are not correct or incomplete.  
The webhook `orderEvent.lines.itemDetails.mergedItemDetails` will contain the merged original item details added by the buyer merged with the changed or added item details by the supplier.
{% endhint %}

* `countryOfOriginCodeIso2`: The ISO 3166-1 alpha-2 country code of manufacture, production, or growth where an article or product comes from.
* `combinedNomenclatureCode`: A tool for classifying goods, set up to meet the requirements both of the Common Customs Tariff and of the EU's external trade statistics.
* `netWeight`: Net weight of one item.
* `netWeightUnitOfMeasureIso`: Net weight unit according to ISO 80000-1.
* `dangerousGoodsCodeUnece`: UN numbers or UN IDs are four-digit numbers that identify dangerous goods, hazardous substances and articles in the framework of international transport.
* `serialNumber`: is an unique identifier assigned incrementally or sequentially to an item, to uniquely identify it.
* `batchNumber`: is an identification number assigned to a particular quantity or lot of material from a single manufacturer

### Requested planned delivery schedule

* `line.deliverySchedule`: the requested planned delivery schedule. Provide at least one or multiple delivery schedule lines.
* `deliverySchedule.position`: the optional position in the delivery schedule. Not to be confused with the `line.position`.
* `deliverySchedule.date`: the requested delivery date of this delivery schedule position. Date has ISO 8601 date `yyyy-MM-dd` format. See also [Standards](../../api/standards.md).
* `deliverySchedule.quantity`: the requested quantity of this delivery schedule position. Quantity has a decimal `1234.56` format with any number of digits.
* `deliverySchedule.status`: The logistics status of this delivery line according to the buyer. The `deliverySchedule.position` MUST be set when providing `status`.

{% hint style="warning" %}
`deliverySchedule.position` should be unique within the delivery schedule and never change. Never renumber or re-use a `deliverySchedule.position`.

The buyer must provide a `deliverySchedule.position` when providing the `status` field and to be able to receive additional logistics fields.
{% endhint %}

{% hint style="info" %}
The delivery line logistics status is one of:

* `ReadyToShip`: full quantity ready to be shipped by the supplier
* `Shipped`: full quantity shipped by the supplier

This logistics status is planned and API and documentation may change:

* `Delivered`: full quantity delivered at the buyer
{% endhint %}

### Requested prices

* `lines.prices`: the requested price. Advised is to provide only `netPrice` for its simplicity, used by most buyers, or alternatively `grossPrice` together with `discountPercentage`. 
* `priceInTransactionCurrency`: at least provide a price in the transaction currency of the supplier, like `CNY` in China.
* `priceInBaseCurrency`: provide a price in your base currency, like `EUR` in the EU.
* `value`: the price value has a decimal `1234.56` format with any number of digits.
* `currencyIso`: the 3-letter currency code according to ISO 4217, like `EUR`, `USD` and `CNY`
* `priceUnitOfMeasureIso`: the price unit according to ISO 80000-1. The purchase unit and price unit may be different.
* `priceUnitQuantity`: the item quantity at which the price applies. Typically this is 1 \(unit price\) or 100 \(the price applies to 100 items\)

### Other line fields

* `description`: a free format additional description of this line
* `terms`: the line terms as agreed with your supplier
* `terms.contractNumber`: the agreed framework contract number
* `terms.contractPosition`: the related position within the framework contract
* `projectNumber`: Your project number reference
* `productionNumber`:  Your production number reference
* `salesOrderNumber`:  Your sales order reference \(not be confused with the supplier sales order number\)
* `indicators`:

When a line has no goods to be delivered, for example a service, fee or text line:

{% page-ref page="no-delivery-expected.md" %}

When your order process requires the buyer to always approve every line:

{% page-ref page="propose-when-accepted.md" %}

* `properties`: are key-value based custom fields. You can use as many as needed, but too many will clutter the portal.  Use `\n` for a new line in the value.
* `documents`: contain attached documents, see:

{% page-ref page="attach-document.md" %}

* `notes`: are simple custom fields.You can use as many as needed, but too many will clutter the portal. Use `\n` for a new line.
* `labels`: value-added services labels on line level. Please note the practicable number of labels is dependent on the supplier.

## New order meta data

* `erpIssueDateTime`: Date and time the order was originally issued in your ERP system. `DateTime` has ISO 8601 local date/time format `yyyy-MM-ddThh:mm:ss`. See also [Standards](../../api/standards.md).
* `erpIssuedBy`: the user email or user name as known in your ERP system who issued this order

## Response

When the `/api-connector/order` API method returns HTTP status code 200, the order was successfully queued for processing by Tradecloud. Processing takes usually less then a second, after which the order is available in the portal and is forwarded to the supplier ERP integration.

