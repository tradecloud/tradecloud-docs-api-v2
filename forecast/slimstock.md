---
description: How to issue a forecast as a buyer using Slimstock
---

# Issue a new Slimstock forecast 

As buyer you can send a new forecast from Slimstock to your supplier.

{% hint style="info" %}
A forecast cannot be updated. Issued forecasts will always be appended to the existing set of forecasts.
{% endhint %}

{% hint style="warning" %}
The forecast module is under development. The API and documentation may change.
{% endhint %}

{% api-method method="post" host="https://api.accp.tradecloud1.com/v2" path="/api-connector/forecast/slimstock" %}
{% api-method-summary %}
Send forecast by buyer
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
Forecast JSON body
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}

{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %} 
Successfully verified and sent forecast.
{% endapi-method-response-example-description %}
{% endapi-method-response-example %}

{% api-method-response-example httpCode=202 %}
{% api-method-response-example-description %} 
Successfully queued forecast. The supplier account code has not yet been verified.
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
[Send forecast OpenAPI Specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendSlimstockForecastByBuyerRoute)
{% endhint %}

{% hint style="info" %}
When sending a forecast the provided supplier account number will be verified. 

Response status codes:
- 200 OK - the supplier account number exists and the forecast will be processed.
- 202 Accepted - the supplier verification has been skipped due to service unavailability and the forecast has been queued.
- 404 Not Found - the supplier account number has not been found. 
{% endhint %}

## Header

* `companyId`: the optional Tradecloud company identifier. You only have to provide a companyId when your integration user account has authorization for multiple companies.
* `supplierAccountNumber`: the supplier account number as known in your ERP system.

{% hint style="warning" %}
The `supplierAccountNumber` must be set in the Tradecloud connection in the portal, after the connection request has been accepted by the other party.
{% endhint %}

* `forecastNumber`: the mandatory forecast identifier in Slimstock. The number must be the same for each supplier forecast from the same generated forecast.

{% hint style="warning" %}
The `forecastNumber` must not contain whitespace characters.
{% endhint %}

## Lines

`lines`: a forecast contains one or multiple lines. A forecast line contains item, period and demand in this period.Lines are grouped into a schedule based on the same `buyerItemNumber`. When multiple lines with the same `buyerItemNumber` are provided, the item data of an arbitrary line will be used.

### Item

`lines.item`: the forecasted item \(or article, goods\).
* `buyerItemNumber`: the mandatory item code or number as known in Slimstock and your ERP.
* `buyerItemRevision`: the revision \(or version\) of this item number.
* `buyerItemName`: the mandatory item short name.
* `supplierItemNumber`: the item code or number as known at the supplier. Required in case of wholesale suppliers.
* `purchaseUnitOfMeasureIso`: the purchase unit according to ISO 80000-1, a typical example is `PCE`.

{% hint style="warning" %}
`buyerItemNumber` should be unique within your company and never change. Never renumber or re-use `buyerItemNumber`s.
{% endhint %}

* `period`: the Slimstock relative forecast period. M0 is current month, M1 is next month etc.
* `quantity`: the forecasted demand of this item, in this period, for this supplier. Quantity has a decimal `1234.56` format with any number of digits.

## issueDateTime

* `issueDateTime`: Date and time the forecast was originally issued in your forecast or ERP system. `DateTime` has ISO 8601 local date/time format `yyyy-MM-ddThh:mm:ss`. See also [Standards](../../api/standards.md).
