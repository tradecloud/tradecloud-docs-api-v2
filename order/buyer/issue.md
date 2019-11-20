---
description: How to isue and reissue an order as a buyer
---

# Issue and reissue order

As buyer you can send either a new or updated purchase order to Tradecloud.

## Send an order to Tradecloud

As a buyer you can send a new purchase order to Tradecloud.

When the api method returns HTTP status code 200, the order was succesfully queued to be processed by Tradecloud. Processing takes normally less then a second, after which to order is forwarded to the supplier and visible in the portal.

{% hint style="info" %}
After processing the order lines will have order process status `Issued`
{% endhint %}

### Send order API method

{% api-method method="post" host="https://api.accp.tradecloud1.com/v2" path="/order"%}
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

See the order JSON body in [Swagger UI](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-integration/specs.yaml#/order-integration/sendOrderByBuyerRoute)

### JSON objects

#### Order

- `companyId`: your Tradecloud company id
- `supplierAccountNumber`: targetted supplier account number as known in your ERP system
- `purchaseOrderNumber`: the puchase order number as in your ERP system
- `destination`: the order delivery destination code and address
- `terms`: the order terms as already agreed with your supplier
- `indicators`: the order is `complete`, completely `delivered` or there is `noDeliveryExpected` anymore
- `contact`: the employee responsible for this order. You can either send his/her email or userName as in you ERP system
- `lines`: provide at least one or multiple purchase order lines.

{% hint style="info" %}
The supplierAccountNumber should be set on forehand in the Tradecloud connection with your supplier. Else we do not know where to send this order.
{% endhint %}

#### Lines

- `position`: the line position within the purchase order number

#### Item

- `item.number`: the item number as in your ERP
- `item.name`: the item short name
- `item.purchaseUnitOfMeasureIso`: the 3-letter purchase unit according to ISO 80000, typical example is `pcs`
- `item.supplierItemNumber`: the item number as known at the supplier. Advised in case of wholesale suppliers.

#### Requested prices

- `line.prices`: the requested price(s). Provide either `netPrice`, used by most buyers or alternatively `grossPrice` together with `discountPercentage`. Price has a decimal `1234.56` format with any number of digits.
- `priceInLocalCurrency`: at least provide a price in the local currency of the supplier, like `CNY` in China.
- `priceInBaseCurrency`: if available provide a price in your base currency, like `EUR` in the EU.
- `currencyIso`: the 3-letter currency codes according to ISO 4217:2015, like `EUR`, `USD` and `CNY`
- `priceUnitOfMeasureIso`: the 3-letter price unit according to ISO 80000. The purchase unit and price unit may be different.
- `priceUnitQuantity`: the item quantity at which the price applies. Typically this is 1 (unit price) or 100 (the price applies to 100 items)

#### Requested planned delivery shedule

- `line.deliverySchedule`: the requested planned delivery schedule. Provide at least one or multiple delivery schedule lines.
- `deliverySchedule.position`: the position in the delivery schedule. Not to be confused with the `line.postion`
- `deliverySchedule.date`: the requested delivery date of this delivery schedule position. Date has ISO 8601 date `yyyy-MM-dd` format
- `deliverySchedule.quantity`: the requested quantity of this delivery schedule position. Quantity has a decimal `1234.56` format with any number of digits.

#### Historical actual delivery schedule

- `line.deliveryHistory`: the historic actual delivery schedule. This will be used to calculate a line is overdue. Fields similar as in `line.deliverySchedule`

#### Order meta data

- `erpIssueDateTime`: Date and time the order was orginally issued. DateTime has any ISO 8601 date/time (UTC or with time zone) format, examples `yyyy-MM-ddThh:mm:ssZ` or `yyyy-MM-ddThh:mm:ss+01:00`. When using a time zone it changes during daylight saving.
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

The request is the same as above. Tradecloud will update the order based on the `purchaseOrderNumber` and will update or add lines based on the `position`.

The update is event oriented, eg. you only have to send the lines affected (updated, added or some indicator set). But you can also send all lines.

#### Order meta data

- `erpLastChangeDateTime`: Date and time the order was updated. DateTime has any ISO 8601 date/time format.
- `erpLastChangedBy`: the user name as known in your ERP system which updated this order