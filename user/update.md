---
description: How to update your user's profile and settings.
---

# Update an user

You can update user profile and settings. Note that user companyId and roles cannot be updated.

## Request

{% api-method method="put" host="https://api.accp.tradecloud1.com/v2" path="/user/:id" %}
{% api-method-summary %}
Update user
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="uuid" required=true %}
User id
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Bearer Access-Token
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="body" type="object" required=true %}
Update user body
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
User updated \(HTTP status code and user id will be returned\)
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Body

See the request body in [Swagger UI](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/company/specs.yaml#/company/updateCompanyRoute)

## Response

Only a HTTP status code will be returned

