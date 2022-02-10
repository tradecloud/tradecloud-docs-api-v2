---
description: 'How to get a user''s name, roles, profile and settings.'
---

# Get a user

Get your user's name, roles, profile and settings:

## Request

{% api-method method="get" host="https://api.accp.tradecloud1.com/v2" path="/user/:id" %}
{% api-method-summary %}
Find user by id
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="uuid" required=true %}
User id \(UUID\) to find.
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

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Response

See the response body in [Swagger UI](https://swagger-ui.s.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/user/specs.yaml#/user/findUserByIdRoute)

