---
description: How to invite a new user
---

# Invite a new user

You can invite a new user to your company. An invitation email will be sent to this user.

## Request

{% api-method method="post" host="https://api.accp.tradecloud1.com/v2" path="/user" %}
{% api-method-summary %}
Create user
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Bearer Access-Token
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="body" type="object" required=true %}
Create user body
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
User created \(HTTP status code and user id will be returned\)
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Body

See the request body in [Swagger UI](https://swagger-ui.s.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/user/specs.yaml#/user/createUserRoute)

