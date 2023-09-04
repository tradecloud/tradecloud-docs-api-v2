---
description: How to issue a forecast as a buyer
---

# Issue a new forecast

As buyer you can send a new forecast to your supplier.

{% hint style="info" %}
A forecast cannot be updated. Issued forecasts will always be appended to the existing set of forecasts.
{% endhint %}

{% hint style="info" %}
Use the [Send Slimstock forecast](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendForecastByBuyerRoute) endpoint to send a forecast to Tradecloud.
{% endhint %}

{% hint style="info" %}
When sending a forecast the provided supplier account number will be verified. 
{% endhint %}

## Header

* `companyId`: the optional Tradecloud company identifier. You only have to provide a companyId when your integration user account has authorization for multiple companies.
* `supplierAccountNumber`: the supplier account number as known in your ERP system.

{% hint style="warning" %}
The `supplierAccountNumber` must be set in the Tradecloud connection in the portal, after the connection request has been accepted.
{% endhint %}

* `forecastNumber`: the mandatory forecast identifier, like code or number as known in your forecast or ERP system. The number must be the same for all items for all suppliers in the same generated forecast.

{% hint style="warning" %}
The `forecastNumber` must not contain whitespace characters.
{% endhint %}

## Lines

`lines`: a forecast contains one or multiple lines. A forecast line consists of an item and forecast schedule. It is structured as a JSON element in the `lines` JSON array. 

### Item

`lines.item`: the forecasted item \(or article, goods\).

* `buyerItemNumber`: the mandatory item code or number as known in your ERP system.
* `buyerItemRevision`: the revision \(or version\) of this item number.
* `buyerItemName`: the mandatory item short name.
* `supplierItemNumber`: the item code or number as known at the supplier. Required in case of wholesale suppliers.
* `purchaseUnitOfMeasureIso`: the purchase unit according to ISO 80000-1, a typical example is `PCE`.

{% hint style="warning" %}
`buyerItemNumber` should be unique within your company and never change. Never renumber or re-use `buyerItemNumber`s.
{% endhint %}

`lines.schedule`: the forecast schedule lines for this item, each consisting of a forecast period and forecasted demand during this period. It is structured as a JSON element in the `schedule` JSON array. 

* `startDate`: the first day of this forecast period. Date has ISO 8601 date `yyyy-MM-dd` format. See also [Standards](../../api/standards.md).
* `endDate`: the last day of this forecast period.
* `quantity`: the forecasted demand of this item, in this period, for this supplier. Quantity has a decimal `1234.56` format with any number of digits.

## issueDateTime

* `issueDateTime`: Date and time the forecast was originally issued in your forecast or ERP system. `DateTime` has ISO 8601 local date/time format `yyyy-MM-ddThh:mm:ss`. See also [Standards](../../api/standards.md).
