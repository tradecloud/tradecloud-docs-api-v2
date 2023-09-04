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

Send delivery events for one or multiple existing order lines using the [Send order deliveries events](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderDeliveriesByBuyer) endpoint. This will append the deliveries to the order line's delivery history. 

{% hint style="warn" %}
Before adding a delivery to an order, the order must have been sent to Tradecloud first.
{% endhint %}

## Delivered indicator

When an order or line is received, regardless of actual quantity or date, it can can be marked as delivered by setting `indicators.delivered` on either order or line level.

### Mark as delivered by resending an order using the `/order` API

The existing order or line can be marked as delivered by setting `indicators.delivered` on either order or line level and updating the order using the [Send order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderByBuyerRoute) endpoint.

{% hint style="info" %}
If you provide a `delivered` indicator on order level, **ONLY** the lines provided in this order message will be marked as delivered.

If you also provide a `delivered` indicator on line level, it has **precedence** over the order level `delivered` indicator.
{% endhint %}

{% page-ref page="update.md" %}

### Mark as delivered by sending the delivered indicator using the `/order/indicators` API

The order or line can be marked as delivered by setting `indicators.delivered` on either order or line level and sending this indicator only, using the [Send order indicators](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderIndicatorsByBuyerRoute) endpoint.

{% hint style="info" %}
If you provide a `delivered` indicator on order level, **ALL** the lines in the order will be delivered.

If you also provide a `delivered` indicator on line level, it has **precedence** over the order level `delivered` indicator.
{% endhint %}

{% hint style="info" %}
When sending order indicators the provided purchase order number will be verified. 
{% endhint %}
