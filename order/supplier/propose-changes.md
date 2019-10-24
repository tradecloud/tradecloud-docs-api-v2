---
description: How to propose changes to an order or line sent by a buyer
---

# Propose order changes

As a supplier you can propose changes of order line:

## Request

{% api-method method="post" host="https://api.accp.tradecloud1.com/v2" path="/order/{id}/line/{position}/_propose"%} 
{% api-method-summary %} Propose order line changes {% endapi-method-summary %}
{% api-method-spec %} 
{% api-method-request %} 
{% api-method-headers %} 
{% api-method-parameter name="Authorization" type="string" required=true %} Authentication token {% endapi-method-parameter %} 
{% endapi-method-headers %}
{% api-method-path-parameters %} 
{% api-method-parameter name="id" type="uuid" required=true %} Order id {% endapi-method-parameter %}
{% api-method-parameter name="position" type="string" required=true %} Order line position {% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% api-method-body-parameters %} 
{% api-method-parameter name="body" type="object" required=true %} Propose order line changes body {% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}
{% api-method-response %} 
{% api-method-response-example httpCode=200 %} 
{% api-method-response-example-description %} Acknowledge {% endapi-method-response-example-description %}
{
   "ok" : true
}
{% endapi-method-response-example %}
{% endapi-method-response %} 
{% endapi-method-spec %}
{% endapi-method %}

### Body

See the request body and full api description in [Swagger UI](https://swagger-ui.test.tradecloud1.com/?url=https://master.test.tradecloud1.com/v2/order/specs.yaml#/order/proposeChangesOrderLineRoute)
