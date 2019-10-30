---
description: How to list your connections with other companies
---

# List your connections
Yoc can find all your connected companies using the `connected=true` parameter

## Request

{% api-method method="get" host="https://api.accp.tradecloud1.com/v2" path="/connection-search"%} 
{% api-method-summary %} Search company connections {% endapi-method-summary %}
{% api-method-spec %} 
{% api-method-request %} 
{% api-method-headers %} 
{% api-method-parameter name="Authorization" type="string" required=true %} Bearer <Authentication token> {% endapi-method-parameter %} 
{% endapi-method-headers %}
{% api-method-query-parameters %} 
{% api-method-parameter name="companyId" type="uuid" required=true %} Company Id {% endapi-method-parameter %}
{% api-method-parameter name="query" type="string" required=false %} 
Free text value. 
You may search on requesting or accepting company's name.
{% endapi-method-parameter %}
{% api-method-parameter name="connected" type="boolean" required=false %} Search for connected connections {% endapi-method-parameter %}
{% api-method-parameter name="requested" type="boolean" required=false %} Search for requested connections {% endapi-method-parameter %}
{% api-method-parameter name="offset" type="integer" required=false %} Search offset {% endapi-method-parameter %}
{% api-method-parameter name="limit" type="integer" required=false %} Search limit {% endapi-method-parameter %}
{% endapi-method-query-parameters %} 
{% endapi-method-request %}
{% endapi-method-spec %}
{% endapi-method %}

## Response

See the response body in [Swagger UI](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/connection-search/specs.yaml#/connection-search/searchConnectionsRoute)
