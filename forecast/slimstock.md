---
description: How to issue a forecast as a buyer using Slimstock
---

# Issue a new Slimstock forecast 

## Forecast process

As buyer you can send a new forecast from Slimstock to Tradecloud.

{% hint style="info" %}
A forecast cannot be updated. Issued forecasts will always be appended to the existing set of forecasts.
{% endhint %}

## Endpoint

Use the [Send Slimstock forecast](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendSlimstockForecastByBuyerRoute) endpoint to send a Slimstock forecast to Tradecloud.

{% hint style="info" %}
When sending a forecast the provided supplier account number will be verified. 
{% endhint %}

## Header

* `companyId`: the optional Tradecloud company identifier. You only have to provide a companyId when your integration user account has authorization for multiple companies.
* `supplierAccountNumber`: the supplier account number as known in your ERP system.

{% hint style="warning" %}
The `supplierAccountNumber` must be set in the Tradecloud connection in the portal, after the connection request has been accepted.
{% endhint %}

* `forecastNumber`: the mandatory forecast identifier in Slimstock. The number must be the same for each supplier forecast from the same generated forecast.

{% hint style="warning" %}
The `forecastNumber` must not contain whitespace characters.
{% endhint %}

## Lines

`lines`: a forecast contains one or multiple lines. A forecast line contains item information and up to 36 months of demand forecasts for this item.

* `buyerItemNumber`: the mandatory item code or number as known in Slimstock and your ERP.
* `buyerItemRevision`: the revision \(or version\) of this item number.
* `buyerItemName`: the mandatory item short name.
* `supplierItemNumber`: the item code or number as known at the supplier. Required in case of wholesale suppliers.
* `purchaseUnitOfMeasureIso`: the purchase unit according to ISO 80000-1, a typical example is `PCE`.
* `startDate`: the date at which the forecasts periods start. Only the month and year of this date are used (day of month is ignored).
* `M0`: The forecasted demand for the 0th month, being the month of `startDate`. Quantity has a decimal `1234.56` format with any number of digits.
* `M1` - `M35`: The forecasted demands for the consecutive months. Quantity has a decimal `1234.56` format with any number of digits.

{% hint style="warning" %}
`buyerItemNumber` should be unique within your company and never change. Never renumber or re-use `buyerItemNumber`s.
{% endhint %}

## issueDateTime

* `issueDateTime`: Date and time the forecast was originally issued in your forecast or ERP system. `DateTime` has ISO 8601 local date/time format `yyyy-MM-ddThh:mm:ss`. See also [Standards](../../api/standards.md).
