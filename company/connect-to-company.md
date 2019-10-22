---
description: How to connect to another company
---

# Connect to another company

You can request connection to another company:

## Request

{% api-method method="post" host="https://api.accp.tradecloud1.com/v2" path="/company/:companyId/connection/:otherCompanyId/_request"%} 
{% api-method-summary %} Request company connection {% endapi-method-summary %}
{% api-method-spec %} 
{% api-method-request %} 
{% api-method-headers %} 
{% api-method-parameter name="Authorization" type="string" required=true %} Authentication token {% endapi-method-parameter %} 
{% endapi-method-headers %}
{% api-method-path-parameters %} 
{% api-method-parameter name="companyId" type="uuid" required=true %} Request connection for company id {% endapi-method-parameter %}
{% api-method-parameter name="otherCompanyId" type="uuid" required=true %} Request connection to company id {% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% api-method-body-parameters %} 
{% api-method-parameter name="otherUserId" type="uuid" required=true %} Request connection to user id {% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}
{% endapi-method-spec %}
{% endapi-method %}

## Response

Only a HTTP status code will be returned
