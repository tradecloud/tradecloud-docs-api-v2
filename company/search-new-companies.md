---
description: How to search for new companies to connect with
---

# Search for companies to connect

Search for known users at companies you want to connect with.
You may search on user's email, first name, last name and company name.

The user should have the opposite role to your user (buyer for supplier and vice versa).
Use [invite new connection](connect-to-company.md) to connect to the company you have found.

## Request

{% api-method method="get" host="https://api.accp.tradecloud1.com/v2" path="/user-search/suggest"%}
{% api-method-summary %} Suggest users {% endapi-method-summary %}
{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %} Bearer Access-Token {% endapi-method-parameter %}
{% endapi-method-headers %}
{% api-method-query-parameters %}
{% api-method-parameter name="companyId" type="uuid" required=true %} Company Id {% endapi-method-parameter %}
{% api-method-parameter name="query" type="string" required=false %}
Free text value.
For now search by user's email, first name, last name and company name is supported.
{% endapi-method-parameter %}
{% api-method-parameter name="role" type="string" required=false %} User role {% endapi-method-parameter %}
{% api-method-parameter name="offset" type="integer" required=false %} Search offset {% endapi-method-parameter %}
{% api-method-parameter name="limit" type="integer" required=false %} Search limit {% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}
{% endapi-method-spec %}
{% endapi-method %}

## Response

See the response body in [Swagger UI](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/user-search/specs.yaml#/user-search/userSuggestRoute)
