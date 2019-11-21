---
description: How to issue and reissue an order as a buyer
---

# Issue and reissue order

As buyer you can send either a new or updated purchase order to Tradecloud.

## Send a new order to Tradecloud

As a buyer you can send a new purchase order to Tradecloud.

When the API method returns HTTP status code 200, the order was successfully queued to be processed by Tradecloud. Processing takes usually less then a second, after which to order is available in the portal and is forwarded to the supplier ERP integration.

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

Relevant fields for new orders

#### Order

- `companyId`: your Tradecloud company id
- `supplierAccountNumber`: the supplier account number as known in your ERP system
- `purchaseOrderNumber`: the purchase order number as in your ERP system
- `destination`: the order delivery destination code and address as in your ERP system
- `terms`: the order terms as agreed with your supplier
- `contact`: the employee responsible for this order. You can either send his/her email or userName as known in you ERP system
- `lines`: provide at least one or multiple purchase order lines.

{% hint style="warn" %}
`supplierAccountNumber`s, `purchaseOrderNumber`s and `destination.code`s should be unique within your company and never change. Never renumber or re-use numbers or code's.
{% endhint %}

{% hint style="info" %}
The `supplierAccountNumber` should be set on forehand in the Tradecloud connection with your supplier. You can set the account code when inviting a new connection or in the connection overview in the portal.
{% endhint %}

#### Lines

- `position`: the line position within the purchase order number

{% hint style="warn" %}
`lines.position` should be unique within the order and never change.
Never renumber or re-use `position` numbers.
{% endhint %}

#### Item

- `lines.item.number`: the item number as in your ERP
- `lines.item.name`: the item short name
- `lines.item.purchaseUnitOfMeasureIso`: the 3-letter purchase unit according to ISO 80000, typical example is `pcs`
- `lines.item.supplierItemNumber`: the item number as known at the supplier. Advised in case of wholesale suppliers.

{% hint style="warn" %}
`item.number` should be unique within your company and never change.
Never renumber or re-use `item.number`s.
{% endhint %}

#### Requested prices

- `lines.prices`: the requested price(s). Provide either `netPrice`, used by most buyers or alternatively `grossPrice` together with `discountPercentage`. Price has a decimal `1234.56` format with any number of digits.
- `priceInLocalCurrency`: at least provide a price in the local currency of the supplier, like `CNY` in China.
- `priceInBaseCurrency`: if available provide a price in your base currency, like `EUR` in the EU.
- `currencyIso`: the 3-letter currency codes according to ISO 4217:2015, like `EUR`, `USD` and `CNY`
- `priceUnitOfMeasureIso`: the 3-letter price unit according to ISO 80000. The purchase unit and price unit may be different.
- `priceUnitQuantity`: the item quantity at which the price applies. Typically this is 1 (unit price) or 100 (the price applies to 100 items)

#### Requested planned delivery schedule

- `line.deliverySchedule`: the requested planned delivery schedule. Provide at least one or multiple delivery schedule lines.
- `deliverySchedule.position`: the position in the delivery schedule. Not to be confused with the `line.position`
- `deliverySchedule.date`: the requested delivery date of this delivery schedule position. Date has ISO 8601 date `yyyy-MM-dd` format
- `deliverySchedule.quantity`: the requested quantity of this delivery schedule position. Quantity has a decimal `1234.56` format with any number of digits.

{% hint style="warn" %}
`deliverySchedule.position` should be unique within the line and never change.
Never renumber or re-use `deliverySchedule.position`s.
{% endhint %}

#### New order meta data

- `erpIssueDateTime`: Date and time the order was originally issued in your ERP system. DateTime has any ISO 8601 date/time (UTC or with time zone) format, examples `yyyy-MM-ddThh:mm:ssZ` or `yyyy-MM-ddThh:mm:ss+01:00`. When using a time zone it changes during daylight saving.
- `erpIssuedBy`: the user name as known in your ERP system which issued this order

## Send an updated order to Tradecloud

As a buyer you can send an updated purchase order to Tradecloud.

{% hint style="info" %}
If an order line has order process status `Issued` or `In Progress` it will be `Reissued` and keep the same status.

If the line has status `Rejected` (by supplier) it will be `Reissued` and become `In Progress`.
If the line has status `Confirmed` it will be `Reopened` and become `In Progress`.

In case of any other status like `Completed` or `Cancelled` the order update will be ignored.
{% endhint %}

### Send updated order API method

The request is the same as above. Tradecloud will update the order based on the `purchaseOrderNumber` and will update or add lines based on the `lines.position` and will update or add delivery schedule and history based on `deliverySchedule.position` and `deliveryHistory.position`.

{% hint style="info" %}
The update is event oriented, eg. you only have to send the lines affected (updated, added or some command or  indicator set). But you can also send all lines.
{% endhint %}

#### Historical actual delivery schedule

- `line.deliveryHistory`: the historic actual delivery schedule. This will be used to calculate if a line is overdue. Fields similar as in `line.deliverySchedule`

#### Updated order meta data

- `erpLastChangeDateTime`: Date and time the order was updated in your ERP system. DateTime has any ISO 8601 date/time format.
- `erpLastChangedBy`: the user name as known in your ERP system which updated this order
