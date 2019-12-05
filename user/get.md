---
description: How to get a user's name, roles, profile and settings.
---

# Get user profile and settings

Get your user's name, roles, profile and settings:

## Request

{% api-method method="get" host="https://api.accp.tradecloud1.com/v2" path="/user/:id"%}
{% api-method-summary %} Find user by id {% endapi-method-summary %}
{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %} Bearer Access-Token {% endapi-method-parameter %}
{% endapi-method-headers %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="uuid" required=true %} User id (UUID) to find. {% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}
{% endapi-method-spec %}
{% endapi-method %}

## Response

See the response body in [Swagger UI](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/user/specs.yaml#/user/findUserByIdRoute)
