---
description: How to connect to another company
---

# Invite new connection

Use [Search for companies to connect](search-new-companies.md) to search for known users at companies you want to connect with. When you found a user and company to connect with, you can request a connection to the other company and user. The other user will receive an invitation email to connect with you and your company.

## Request

{% api-method method="post" host="https://api.accp.tradecloud1.com/v2" path="/company/:companyId/connection/:otherCompanyId/request" %}
{% api-method-summary %}
Request company connection
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="companyId" type="uuid" required=true %}
Request connection for company id
{% endapi-method-parameter %}

{% api-method-parameter name="otherCompanyId" type="uuid" required=true %}
Request connection to company id
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Bearer Access-Token
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="otherUserId" type="uuid" required=true %}
Request connection to user id
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Connection requested
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

See the full description in [Swagger UI](https://swagger-ui.s.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/company/specs.yaml#/company/requestConnectionRoute)

