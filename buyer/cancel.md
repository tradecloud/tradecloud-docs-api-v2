---
description: How to request the supplier to cancel an order or line
---

# Cancel an order

Cancel an order line in Tradecloud when it is cancelled at the buyer.

* `Issued`, `In Progress`, `Rejected` and `Confirmed` lines will become `Cancelled` immediately \(without request\)
* `Completed` lines cannot be cancelled
* `Cancelled` lines cannot be cancelled again

## Cancelling by resending an order using the `/order` API

You can cancel the order or line by setting `indicators.cancelled` on either order or line level and updating the order using the `/order` API resource.

{% hint style="info" %}
If you provide a `cancelled` indicator on order level, **ONLY** the lines provided in this order message will be cancelled.

If you also provide a `cancelled` indicator on line level, it has **precedence** over the order level `cancelled` indicator.
{% endhint %}

{% page-ref page="update.md" %}

## Cancelling by resending the order without the cancelled line using the `/order` API

You can cancel an order line by using the `/order` API resource, by setting the `indicators.cancelLineWhenMissing` on order level and updating the order WITHOUT including the cancelled line.

You can cancel a full order \(all the lines\) by setting the `indicators.cancelLineWhenMissing` on order level and updating the order WITHOUT any lines.

This is useful when your ERP system cannot cancel a line, but instead removes a line from the order.

{% page-ref page="update.md" %}

## Cancelling by sending the cancelled indicator using the `/order/indicators` API

You can cancel the order or line by setting `indicators.cancelled` on either order or line level and sending this indicator only, using the `/order/indicators` API resource.

{% hint style="info" %}
If you provide a `cancelled` indicator on order level, **ALL** the lines in the order will be cancelled.

If you also provide a `cancelled` indicator on line level, it has **precedence** over the order level `cancelled` indicator.
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
{% api-method-response-example-description %} 
Successfully verified and sent order indicators.
{% endapi-method-response-example-description %}
{% endapi-method-response-example %}

{% api-method-response-example httpCode=202 %}
{% api-method-response-example-description %} 
Successfully queued order indicators. The purchase order number has not yet been verified.
{% endapi-method-response-example-description %}
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %} 
Order not found.
{% endapi-method-response-example-description %}
{% endapi-method-response-example %}

{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Body example:

```text
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

{% hint style="info" %}
When sending order indicators the provided purchase order number will be verified. 

Response status codes:
- 200 OK - the purchase order number exists and the order indicators will be processed.
- 202 Accepted - the order verification has been skipped due to service unavailability and the order indicators have been queued.
- 404 Not Found - the purchase order number has not been found. 
{% endhint %}
