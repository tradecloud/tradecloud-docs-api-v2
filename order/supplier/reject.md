---
description: How to reject an order or line sent by a buyer
---

# Reject order

As a supplier you can reject specific line of order:

## Request

{% api-method method="post" host="https://api.accp.tradecloud1.com/v2" path="/order/:id/line/:position/_reject"%} 
{% api-method-summary %} Reject order line {% endapi-method-summary %}
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
{% api-method-parameter name="reason" type="string" required=true %} Rejection reason {% endapi-method-parameter %}
{% api-method-parameter name="version" type="integer" required=true %} Order version {% endapi-method-parameter %}
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

See the full description in [Swagger UI](https://swagger-ui.test.tradecloud1.com/?url=https://master.test.tradecloud1.com/v2/order/specs.yaml#/order/rejectOrderLineRoute)
