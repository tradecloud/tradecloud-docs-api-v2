---
description: How to request the supplier to cancel an order or line
---

# Cancelling an order or line

Cancel an order line in Tradecloud when it is cancelled at the buyer.

- `Issued`, `In Progress`, `Rejected` and `Confirmed` lines will become `Cancelled` immediately (without request)
- `Completed` lines cannot be cancelled
- `Cancelled` lines cannot be cancelled again

## Cancelling by resending an order

The order or line can be cancelled by setting `indicators.cancelled` on either order or line level and updating the order.

{% hint style="info" %}
If you provide a `cancelled` indicator on order level, **ONLY** the lines provided in this order message will be cancelled.

If you also provide a `cancelled` indicator on line level, it has **precedence** over the order level `cancelled` indicator.
{% endhint %}

{% page-ref page="update.md" %}

## Cancelling by sending the cancelled indicator

The order or can be cancelled by setting `indicators.cancelled` on either order or line level and sending this indicator only.

{% hint style="info" %}
If you provide a `cancelled` indicator on order level, **ALL** the lines in the order will be cancelled.

If you also provide a compl`cancelled`eted indicator on line level, it has **precedence**  over the order level `cancelled` indicator.
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
```
{
  "order": {
    "purchaseOrderNumber": "PO123456789",
    "indicators": {
      "cancelled": true
    }
  },
  "lines": [
    {
      "position": "0001",
      "indicators": {
        "cancelled": true
      }
    }
  ]
}
```

{% hint style="info" %}
[Send order indicators OpenAPI Specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderIndicatorsByBuyerRoute)
{% endhint %}
