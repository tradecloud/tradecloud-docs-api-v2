---
description: How to complete an order or line
---

# Complete an order

{% hint style="warning" %}
This feature is planned.
{% endhint %}

When an order or line is completely handled at the buyer, usually when the supplier invoice is received and approved by buyer.

## Completing by resending an order

The order or line can be marked as completed by setting `indicators.completed`on either order or line level and updating the order.

{% hint style="info" %}
If you provide a completed indicator on order level, ONLY the lines provided in this order message will be completed.
{% endhint %}

{% page-ref page="update.md" %}

## Completing by sending the complete indicator

The order or can be marked as competed  by setting `indicators.completed`on either order or line level and sending the indicator only.

{% hint style="info" %}
If you provide a completed indicator on order level, ALL the lines in the order will be completed, regardless the lines provided in this order indicators message.
{% endhint %}

{% api-method method="post" host="https://api.accp.tradecloud1.com/v2" path="/api-connector/order/indicators" %}
{% api-method-summary %}
Send order by buyer
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Bearer Access-Token
{% endapi-method-parameter %}

{% api-method-parameter name="Content-Type" type="string" required=true %}
application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="body" type="object" required=true %}
{
  "order": {
    "purchaseOrderNumber": "PO123456789",
    "indicators": {
      "completed": true
    }
  },
  "lines": [
    {
      "position": "0001",
      "indicators": {
        "completed": true
      }
    }
  ]
}
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
[Send order OpenAPI Specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderIndicatorsByBuyerRoute)
{% endhint %}

{% hint style="warning" %}
You cannot complete a `Cancelled` line
{% endhint %}

{% hint style="info" %}
Order lines having process status `Issued`, `In Progress` or `Confirmed` will become `Completed`
{% endhint %}
