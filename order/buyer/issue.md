---
description: How to issue a new order as a buyer
---

# Issue a new order

As buyer you can send either a new or [updated](reissue.md) purchase order to Tradecloud.

## Send a new order to Tradecloud

As a buyer you can send a new purchase order to Tradecloud.

{% hint style="info" %}
After processing the order lines will have order process status `Issued`
{% endhint %}

### Send order API method

{% api-method method="post" host="https://api.accp.tradecloud1.com/v2" path="/order-integration/order"%}
{% api-method-summary %}Send order by buyer{% endapi-method-summary %}
{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %} Bearer Access-Token {% endapi-method-parameter %}
{% api-method-parameter name="Content-Type" type="string" required=true %} application/json {% endapi-method-parameter %}
{% endapi-method-headers %}
{% api-method-body-parameters %}
{% api-method-parameter name="body" type="object" required=true %} Order JSON body {% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}
{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %} Successfully queued order (no body will be returned) {% endapi-method-response-example-description %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

 [Send order OpenAPI Specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-integration/specs.yaml#/order-integration/sendOrderByBuyerRoute)

### Order body JSON objects

#### Order

- `companyId`: your Tradecloud company identifier. You can find your company id in the URL when selecting "My company" in the portal dropdown menu. For example in `https://portal.accp.tradecloud1.com/company/06893bba-e131-4268-87c9-7fae64e16ee9` the last part `06893bba-e131-4268-87c9-7fae64e16ee9` is the company id.
- `supplierAccountNumber`: the supplier account number as known in your ERP system
- `purchaseOrderNumber`: the purchase order number as known in your ERP system
- `destination`: the delivery destination of this order as known in your ERP system
- `contact`: the employee responsible for this order. You can either send his/her email or userName as known in your ERP system
  
{% hint style="danger" %}
`supplierAccountNumber`, `purchaseOrderNumber`, `destination.code`, `contact.email` and `contact.userName` should be unique within your company and never change. Never renumber or re-use numbers or code's.
{% endhint %}

{% hint style="danger" %}
The `supplierAccountNumber` should be set on forehand in the Tradecloud connection with your supplier. You can set the account code when inviting a new connection or at any time in the connection overview in the portal.
{% endhint %}

#### Secondary order fields

- `description`: a free format additional description of this order
- `terms`: the order terms as agreed with your supplier
- `indicators`: see [Indicators](indicators.md)
- `properties`: are key-value based custom fields. You can user as many as needed, but too many will clutter the portal. Use `\n` for a new line in the value.
- `notes`: are simple custom fields. You can user as many as needed, but too many will clutter the portal. Use `\n` for a new line.
- `documents`: contain meta data and link of attached documents. See [Attach a document to an order](attach-document.md)

#### Lines

- `lines`: a purchase order contains one or multiple lines
- `line`: a purchase order line which contains at least the position, item and delivery schedule. It is structured as a JSON element in the `lines` JSON array. 
- `position`: the line position within the purchase order

{% hint style="danger" %}
`lines.position` should be unique within the order and never change.
Never renumber or re-use `position` numbers.
{% endhint %}

#### Item

- `lines.item`: the item (or article, goods) to be delivered
- `lines.item.number`: the item code or number as known in your ERP
- `lines.item.revision`: the revision (or version) of this item number
- `lines.item.name`: the item short name
- `lines.item.purchaseUnitOfMeasureIso`: the 3-letter purchase unit according to ISO 80000-1, a typical example is `PCE`
- `lines.item.supplierItemNumber`: the item code or number as known at the supplier. Advised in case of wholesale suppliers.

{% hint style="danger" %}
`item.number` should be unique within your company and never change.
Never renumber or re-use `item.number`s.
{% endhint %}

#### Requested planned delivery schedule

- `line.deliverySchedule`: the requested planned delivery schedule. Provide at least one or multiple delivery schedule lines.
- `deliverySchedule.position`: the position in the delivery schedule. Not to be confused with the `line.position`
- `deliverySchedule.date`: the requested delivery date of this delivery schedule position. Date has ISO 8601 date `yyyy-MM-dd` format. See also [Standards](../../api/standards.md).
- `deliverySchedule.quantity`: the requested quantity of this delivery schedule position. Quantity has a decimal `1234.56` format with any number of digits.

{% hint style="danger" %}
`deliverySchedule.position` should be unique within the delivery schedule and never change.
Never renumber or re-use `deliverySchedule.position`s.
{% endhint %}

#### Requested prices

- `lines.prices`: the requested price. Advised is to provide only `netPrice` for its simplicity, used by most buyers, or alternatively `grossPrice` together with `discountPercentage`. 
- `priceInLocalCurrency`: at least provide a price in the local currency of the supplier, like `CNY` in China.
- `priceInBaseCurrency`: if available provide a price in your base currency, like `EUR` in the EU.
- `value`: the price value has a decimal `1234.56` format with any number of digits.
- `currencyIso`: the 3-letter currency code according to ISO 4217, like `EUR`, `USD` and `CNY`
- `priceUnitOfMeasureIso`: the 3-letter price unit according to ISO 80000-1. The purchase unit and price unit may be different.
- `priceUnitQuantity`: the item quantity at which the price applies. Typically this is 1 (unit price) or 100 (the price applies to 100 items)

#### Secondary line fields

- `description`: a free format additional description of this line
- `terms`: the line terms as agreed with your supplier
- `terms.contractNumber`: the agreed framework contract number
- `terms.contractPosition`: the related position within the framework contract
- `projectNumber`: Your project number reference
- `productionNumber`:  Your production number reference
- `salesOrderNumber`:  Your sales order reference (not be confused with the supplier sales order number)
- `indicators`: see [Indicators](indicators.md)
- `properties`: are key-value based custom fields. You can use as many as needed, but too many will clutter the portal.  Use `\n` for a new line in the value.
- `notes`: are simple custom fields.You can use as many as needed, but too many will clutter the portal. Use `\n` for a new line.
- `documents`: contain meta data and link of attached documents. See [Attach a document to a line](attach-document.md)

#### New order meta data

- `erpIssueDateTime`: Date and time the order was originally issued in your ERP system. `DateTime` has ISO 8601 local date/time format `yyyy-MM-ddThh:mm:ss`. See also [Standards](../../api/standards.md).
- `erpIssuedBy`: the user email or user name as known in your ERP system who issued this order

## Response

Only a HTTP status code will be returned

When the `/order-integration/order` API method returns HTTP status code 200, the order was successfully queued to be processed by Tradecloud. Processing takes usually less then a second, after which the order is available in the portal and is forwarded to the supplier ERP integration.
