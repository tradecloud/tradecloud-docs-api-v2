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

{% api-method-response %} 
{% api-method-response-example httpCode=400 %} 
{% api-method-response-example-description %} Connection requested {% endapi-method-response-example-description %}
Test
{% endapi-method-response-example %}
{% endapi-method-response %} 
{% endapi-method-spec %}
{% endapi-method %}

See the full description in [Swagger UI](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/company/specs.yaml#/company/requestConnectionRoute)
