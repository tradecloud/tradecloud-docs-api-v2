---
description: How to announce the supplier has shipped goods
---

# Ship goods

{% hint style="warning" %}
This feature is planned and API and documentation may change. 
{% endhint %}

When an order or line is completely shipped by the supplier, it can be marked as shipped by setting `indicators.shipped` on either order or line level.

- Order lines having logistics status `Open` will become `Shipped`
- `Delivered` lines cannot be shipped
- `Shipped` lines cannot be shipped again

{% hint style="warning" %}
Usually this is indicator is set in the `order-response` by the supplier but in some cases a buyer requires to set it.
{% endhint %}

## Mark as shipped by resending an order

The order or line can be marked as shipped by setting `indicators.shipped` on either order or line level and updating the order.

{% hint style="info" %}
If you provide a `shipped` indicator on order level, **ONLY** the lines provided in this order message will be shipped.

If you also provide a `shipped` indicator on line level, it has **precedence** over the order level `shipped` indicator.
{% endhint %}

{% page-ref page="update.md" %}

## Mark as shipped by sending the shipped indicator

The order or line can be marked as completed by setting `indicators.shipped` on either order or line level and sending this indicator only.

{% hint style="info" %}
If you provide a `shipped` indicator on order level, **ALL** the lines in the order will be shipped.

If you also provide a `shipped` indicator on line level, it has **precedence** over the order level `shipped` indicator.
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
      "shipped": true
    }
  },
  "lines": [
    {
      "position": "0001",
      "indicators": {
        "shipped": true
      }
    }
  ]
}
```

{% hint style="info" %}
[Send order indicators OpenAPI Specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderIndicatorsByBuyerRoute)
{% endhint %}
