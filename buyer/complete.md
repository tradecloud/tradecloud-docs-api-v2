---
description: How to complete an order or line
---

# Complete an order

Complete an order line in Tradecloud when it is completely handled at the buyer, usually when the supplier invoice is received and approved by buyer.

* `Issued`, `Rejected` and `Confirmed` lines will become `Completed`
* `In progress` and `Cancelled` lines cannot be completed
* `Completed` lines cannot be completed again
* Completing has precedence over cancelling at the same time

## Completing by resending an order using the `/order` API

The order or line can be marked as completed by setting `indicators.completed` on either order or line level and updating the order using the `/order` API resource.

{% hint style="info" %}
If you provide a `completed` indicator on order level, **ONLY** the lines provided in this order message will be completed.

If you also provide a `completed` indicator on line level, it has **precedence** over the order level `completed` indicator.
{% endhint %}

{% page-ref page="update.md" %}

## Completing by sending the completed indicator using the `/order/indicators` API

The order or line can be marked as completed by setting `indicators.completed` on either order or line level and sending this indicator only, using the `/order/indicators` API resource.

{% hint style="info" %}
If you provide a `completed` indicator on order level, **ALL** the lines in the order will be completed.

If you also provide a `completed` indicator on line level, it has **precedence** over the order level `completed` indicator.
{% endhint %}

{% api-method method="post" host="https://api.accp.tradecloud1.com/v2" path="/api-connector/order/indicators" %}
{% api-method-summary %}
Send order indicators by buyer
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

{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Body example:

```text
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
```

{% hint style="info" %}
[Send order indicators OpenAPI Specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderIndicatorsByBuyerRoute)
{% endhint %}

