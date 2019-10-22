---
description: How to list your connections with other companies
---

# List your connections
Yoc can find all connected companies using `connected=true` parameter

## Request

{% api-method method="get" host="" path="https://api.accp.tradecloud1.com/v2/connection-search" %} {% api-method-summary %} Search company connections {% endapi-method-summary %}

{% api-method-parameter name="companyId" type="string" required=true %} Company Id {% endapi-method-parameter %}
{% api-method-parameter name="query" type="string" required=false %} Query string {% endapi-method-parameter %}
{% api-method-parameter name="connected" type="boolean" required=false %} Search for connected connections {% endapi-method-parameter %}
{% api-method-parameter name="requested" type="boolean" required=false %} Search for requested connections {% endapi-method-parameter %}
{% api-method-parameter name="offset" type="integer" required=false %} Search offset {% endapi-method-parameter %}
{% api-method-parameter name="limit" type="integer" required=false %} Search limit {% endapi-method-parameter %}

## Response

See the response body in [Swagger UI](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/connection-search/specs.yaml#/connection-search/searchConnectionsRoute)
