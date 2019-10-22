---
description: How to search for new companies to connect with
---

# Search for companies to connect

You can search for new companies providing role that is opposite to your user (buyer for supplier and vice versa) 

## Request

{% api-method method="get" host="https://api.accp.tradecloud1.com/v2/user-search/_suggest" %} 
{% api-method-summary %} Suggest users {% endapi-method-summary %}
{% api-method-spec %} 
{% api-method-request %} 
{% api-method-query-parameters %} 
{% api-method-parameter name="companyId" type="string" required=true %} Company Id {% endapi-method-parameter %}
{% api-method-parameter name="query" type="string" required=false %} Query string {% endapi-method-parameter %}
{% api-method-parameter name="role" type="string" required=false %} User role {% endapi-method-parameter %}
{% api-method-parameter name="offset" type="integer" required=false %} Search offset {% endapi-method-parameter %}
{% api-method-parameter name="limit" type="integer" required=false %} Search limit {% endapi-method-parameter %}
{% endapi-method-query-parameters %} 
{% endapi-method-request %}
{% endapi-method-spec %}
{% endapi-method %}

## Response

See the response body in [Swagger UI](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/user-search/specs.yaml#/user-search/userSuggestRoute)
