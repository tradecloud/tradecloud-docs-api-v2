---
description: How to update your company's profile and settings.
---

# Update your company

You can update your company profile and settings as described below. Note that your company name or roles cannot be updated.

## Request

{% api-method method="put" host="https://api.accp.tradecloud1.com/v2" path="/company/:id" %}
{% api-method-summary %}
Update company by id
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="uuid" required=true %}
Company id to update.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Bearer Access-Token
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Body

In the request body you may update:

* profile fields
* integration settings, either webhook or ftp
* as the PUT method will overwrite the complete company profile and settings object, copy remaining fields from [Get company profile and settings](get.md)

See the request body in [Swagger UI](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/company/specs.yaml#/company/updateCompanyRoute)

## Response

Only a HTTP status code will be returned

