---
description: How to announce the buyer has received goods
---

# Receive goods

There are two ways to announce the buyer has received goods:
- using the actual delivery, which is preferred over the delivered indicator, as it is more precise regarding partial deliveries.
- using the delivered indicator

## Actual delivery history

The delivery history contains the actual physical deliveries. With the actual deliveries versus the planned deliveries, Tradecloud can calculate which goods should still be delivered or are overdue.

There are two ways to send the delivery history to Tradecloud:

- by sending the delivery history using the `lines.deliveryHistory` field and updating the order using the `/order` API.
- by sending one or more delivery events using the `/api-connector/order/deliveries` API.

### Send the delivery history by resending an order using the `/order` API

Send the actual delivery schedule by setting the `lines.deliveryHistory` and updating the order using the `/order` API resource:

{% page-ref page="update.md" %}

### Send delivery events using the `/api-connector/order/deliveries` API

Send delivery events for one or multiple existing order lines using the `/api-connector/order/deliveries` API. This will append the deliveries to the order line's delivery history. 

{% hint style="warn" %}
Before adding a delivery to an order, the order must have been sent to Tradecloud first.
{% endhint %}

{% api-method method="post" host="https://api.accp.tradecloud1.com/v2" path="/api-connector/order/deliveries" %}
{% api-method-summary %}
Send order delivery events by buyer
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
Successfully verified and sent delivery events.
{% endapi-method-response-example-description %}
{% endapi-method-response-example %}

{% api-method-response-example httpCode=202 %}
{% api-method-response-example-description %} 
Successfully queued delivery events. The purchase order number has not yet been verified.
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

	
```
{
  "order": {
    "purchaseOrderNumber": "PO12345"
  },
  "lines": [
    {
      "position": "0001",
      "deliveries": [
        {
          "date": "2021-02-31",
          "quantity": 41.5
        }
      ]
    }
  ]
}
```

## Delivered indicator

When an order or line is received, regardless of actual quantity or date, it can can be marked as delivered by setting `indicators.delivered` on either order or line level.

### Mark as delivered by resending an order using the `/order` API

The existing order or line can be marked as delivered by setting `indicators.delivered` on either order or line level and updating the order using the `/order` API resource.

{% hint style="info" %}
If you provide a `delivered` indicator on order level, **ONLY** the lines provided in this order message will be marked as delivered.

If you also provide a `delivered` indicator on line level, it has **precedence** over the order level `delivered` indicator.
{% endhint %}

{% page-ref page="update.md" %}

### Mark as delivered by sending the delivered indicator using the `/order/indicators` API

The order or line can be marked as delivered by setting `indicators.delivered` on either order or line level and sending this indicator only, using the `/order/indicators` API resource.

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

{% hint style="info" %}
When sending order indicators the provided purchase order number will be verified. 

Response status codes:
- 200 OK - the purchase order number exists and the order indicators will be processed.
- 202 Accepted - the order verification has been skipped due to service unavailability and the order indicators have been queued.
- 404 Not Found - the purchase order number has not been found. 
{% endhint %}
