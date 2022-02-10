---
description: How to list your company's users
---

# List your company's users

Search for users of your company.

## Request

{% api-method method="get" host="https://api.accp.tradecloud1.com/v2" path="/user-search/search" %}
{% api-method-summary %}
Search users
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

{% api-method-query-parameters %}
{% api-method-parameter name="companyId" type="uuid" required=true %}
Company Id
{% endapi-method-parameter %}

{% api-method-parameter name="query" type="string" required=false %}
Free text value. For now search by user's email, first name and last name is supported.
{% endapi-method-parameter %}

{% api-method-parameter name="role" type="string" required=false %}
User role
{% endapi-method-parameter %}

{% api-method-parameter name="offset" type="integer" required=false %}
Search offset
{% endapi-method-parameter %}

{% api-method-parameter name="limit" type="integer" required=false %}
Search limit
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Users found
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Response

See the response body in [Swagger UI](https://swagger-ui.s.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/user-search/specs.yaml#/user-search/userSearchRoute)

