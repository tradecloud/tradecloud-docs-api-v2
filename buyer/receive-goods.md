---
description: How to announce the buyer has received goods
---

# Receive goods

There are two ways to announce the buyer has received goods. Using the actual delivery schedule is preferred over the delivered indicator, as it is more precise regarding partial deliveries.

## Actual delivery schedule

This schedule contains the actual physical deliveries. With the actual deliveries versus the planned deliveries Tradecloud can calculate which goods should still be delivered or are overdue.

The actual delivery schedule can be send by setting the `lines.deliveryHistory` and updating the order:

{% page-ref page="update.md" %}

## Delivered indicator

When an order or line is received, regardless of actual quantity or date, it can can be marked as delivered by setting `indicators.delivered` on either order or line level.

### Mark as delivered by resending an order

The order or line can be marked as delivered by setting `indicators.delivered` on either order or line level and updating the order.

{% hint style="info" %}
If you provide a `delivered` indicator on order level, **ONLY** the lines provided in this order message will be marked as delivered.

If you also provide a `delivered` indicator on line level, it has **precedence** over the order level `delivered` indicator.
{% endhint %}

{% page-ref page="update.md" %}

### Mark as delivered by sending the delivered indicator

The order or line can be marked as delivered by setting `indicators.delivered` on either order or line level and sending this indicator only.

{% hint style="info" %}
If you provide a `delivered` indicator on order level, **ALL** the lines in the order will be delivered.

If you also provide a `delivered` indicator on line level, it has **precedence** over the order level `delivered` indicator.
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
      "delivered": true
    }
  },
  "lines": [
    {
      "position": "0001",
      "indicators": {
        "delivered": true
      }
    }
  ]
}
```

{% hint style="info" %}
[Send order indicators OpenAPI Specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderIndicatorsByBuyerRoute)
{% endhint %}
