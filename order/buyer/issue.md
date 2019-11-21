---
description: How to issue and reissue an order as a buyer
---

# Issue and reissue order

As buyer you can send either a new or updated purchase order to Tradecloud.

## Send a new order to Tradecloud

As a buyer you can send a new purchase order to Tradecloud.

When the `/order-integration/order` API method returns HTTP status code 200, the order was successfully queued to be processed by Tradecloud. Processing takes usually less then a second, after which to order is available in the portal and is forwarded to the supplier ERP integration.

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

- `companyId`: your Tradecloud company id
- `supplierAccountNumber`: the supplier account number as known in your ERP system
- `purchaseOrderNumber`: the purchase order number as in your ERP system
- `destination`: the order delivery destination code and address as in your ERP system
- `contact`: the employee responsible for this order. You can either send his/her email or userName as known in you ERP system
  
{% hint style="danger" %}
`supplierAccountNumber`, `purchaseOrderNumber`, `destination.code`, `contact.email` and `contact.userName` should be unique within your company and never change. Never renumber or re-use numbers or code's.
{% endhint %}

{% hint style="danger" %}
The `supplierAccountNumber` should be set on forehand in the Tradecloud connection with your supplier. You can set the account code when inviting a new connection or at any time in the connection overview in the portal.
{% endhint %}

#### Secondary order fields

- `terms`: the order terms as agreed with your supplier
- `properties`: are key-value based custom fields. You can user as many as needed, but too many will clutter the portal. Use `\n` for line breaks in the value.
- `notes`: are simple custom fields. You can user as many as needed, but too many will clutter the portal. Use `\n` for line breaks.
- `documents`: contain meta data and link of attached documents. See [Attach a document to an order](order/buyer/attach-document.md)

#### Lines

- `lines`: provide at least one or multiple purchase order lines.
- `position`: the line position within the purchase order

{% hint style="danger" %}
`lines.position` should be unique within the order and never change.
Never renumber or re-use `position` numbers.
{% endhint %}

#### Item

- `lines.item.number`: the item number as in your ERP
- `lines.item.name`: the item short name
- `lines.item.purchaseUnitOfMeasureIso`: the 3-letter purchase unit according to ISO 80000, typical example is `pcs`
- `lines.item.supplierItemNumber`: the item number as known at the supplier. Advised in case of wholesale suppliers.

{% hint style="danger" %}
`item.number` should be unique within your company and never change.
Never renumber or re-use `item.number`s.
{% endhint %}

#### Requested prices

- `lines.prices`: the requested price(s). Provide either `netPrice`, used by most buyers or alternatively `grossPrice` together with `discountPercentage`. Price has a decimal `1234.56` format with any number of digits.
- `priceInLocalCurrency`: at least provide a price in the local currency of the supplier, like `CNY` in China.
- `priceInBaseCurrency`: if available provide a price in your base currency, like `EUR` in the EU.
- `currencyIso`: the 3-letter currency codes according to ISO 4217, like `EUR`, `USD` and `CNY`
- `priceUnitOfMeasureIso`: the 3-letter price unit according to ISO 80000. The purchase unit and price unit may be different.
- `priceUnitQuantity`: the item quantity at which the price applies. Typically this is 1 (unit price) or 100 (the price applies to 100 items)

#### Requested planned delivery schedule

- `line.deliverySchedule`: the requested planned delivery schedule. Provide at least one or multiple delivery schedule lines.
- `deliverySchedule.position`: the position in the delivery schedule. Not to be confused with the `line.position`
- `deliverySchedule.date`: the requested delivery date of this delivery schedule position. Date has ISO 8601 date `yyyy-MM-dd` format
- `deliverySchedule.quantity`: the requested quantity of this delivery schedule position. Quantity has a decimal `1234.56` format with any number of digits.

{% hint style="danger" %}
`deliverySchedule.position` should be unique within the schedule line and never change.
Never renumber or re-use `deliverySchedule.position`s.
{% endhint %}

#### Secondary line fields

- `terms`: the line terms as agreed with your supplier
- `terms.contractNumber`: the agreed framework contract number
- `terms.contractPosition`: the related position within the framework contract
- `projectNumber`: Your project number reference
- `productionNumber`:  Your production number reference
- `salesOrderNumber`:  Your sales order reference (not be confused with the supplier sales order number)
- `properties`: are key-value based custom fields. You can use as many as needed, but too many will clutter the portal.  Use `\n` for line breaks in the value.
- `notes`: are simple custom fields.You can use as many as needed, but too many will clutter the portal. Use `\n` for line breaks.
- `documents`: contain meta data and link of attached documents. See [Attach a document to a line](order/buyer/attach-document.md)

#### New order meta data

- `erpIssueDateTime`: Date and time the order was originally issued in your ERP system. `DateTime` has ISO 8601 local date/time format `yyyy-MM-ddThh:mm:ss`
- `erpIssuedBy`: the user name as known in your ERP system who issued this order

## Send an updated order to Tradecloud

As a buyer you can send an updated purchase order to Tradecloud.

{% hint style="danger" %}
Most supplier ERP integrations do not have the capability to automatically process an updated order. It will processed manually by the supplier and the order will have a longer human response time.
{% endhint %}

{% hint style="info" %}
If an order line has order process status `Issued` or `In Progress` it will be `Reissued` and keep the same status.
If the line has status `Rejected` (by supplier) it will be `Reissued` and become `In Progress`.
If the line has status `Confirmed` it will be `Reopened` and become `In Progress`.
In case of any other status like `Completed` or `Cancelled` the order update will be ignored.
{% endhint %}

### Send updated order API method

The `/order-integration/order` API method is the same as above with additional JSON objects as mentioned below. Tradecloud will update the order based on the `purchaseOrderNumber` and will update or add lines based on the `lines.position` and will update or add delivery schedule and history based on `deliverySchedule.position` and `deliveryHistory.position`.

{% hint style="tip" %}
The update is event oriented, eg. you only have to send the lines affected (updated, added or some command or  indicator set). But you can also send all lines.
{% endhint %}

### Additional order body JSON objects

#### Historical actual delivery schedule

- `lines.deliveryHistory`: the historic actual delivery schedule. This will be used to calculate the line `Overdue` indicator. The fields are similar as in `lines.deliverySchedule`

#### Updated order meta data

- `erpLastChangeDateTime`: Date and time the order was updated in your ERP system. `DateTime` has ISO 8601 local date/time format `yyyy-MM-ddThh:mm:ss`
- `erpLastChangedBy`: the user name as known in your ERP system who updated this order
