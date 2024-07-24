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

### Send the delivery history by updating an order using the `/order` API

Send the actual delivery schedule by setting the `lines.deliveryHistory` field when your ERP system supports a delivery schedule natively, and update the order using the [Send order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderByBuyerRoute) endpoint.

Send the actual delivery by setting the `lines.actualDelivery` field when using the single delivery per order line feature, and update the order using the [Send single delivery order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendSingleDeliveryOrderByBuyerRoute) endpoint.

{% page-ref page="update.md" %}

### Send delivery events using the `/api-connector/order/deliveries` API

Send delivery events for one or multiple existing order lines using the [Send order deliveries events](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderDeliveriesByBuyer) endpoint. This will append the deliveries to the order line's delivery history. 

{% hint style="warning" %}
Before adding a delivery to an order, the order must have been sent to Tradecloud first.
{% endhint %}

{% hint style="warning" %}
When using the single delivery per order line feature, the deliveries endpoint only supports the first order line of each item number. The deliveries of the first line will be applied to all order lines having the same item, prices and terms.
{% endhint %}

## Delivered indicator

When an order or line is received, regardless of actual quantity or date, it can can be marked as delivered by setting `indicators.delivered` on either order or line level.

{% hint style="warning" %}
When using the single delivery per order line feature, the `delivered` indicator is only supported for the first order line of each item number. The other lines with the same item, prices and terms will also be marked as delivered together with the first line.
{% endhint %}

### Mark as delivered by updating an order using the `/order` API

The existing order or line can be marked as delivered by setting `indicators.delivered` on either order or line level and updating the order using the [Send order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderByBuyerRoute) endpoint:

{% page-ref page="update.md" %}

{% hint style="info" %}
If you provide a `delivered` indicator on order level, **ONLY** the lines provided in this order message will be marked as delivered.

If you also provide a `delivered` indicator on line level, it has **precedence** over the order level `delivered` indicator.
{% endhint %}

### Mark as delivered by sending the delivered indicator using the `/order/indicators` API

The order or line can be marked as delivered by setting `indicators.delivered` on either order or line level and sending this indicator only, using the [Send order indicators](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderIndicatorsByBuyerRoute) endpoint.

{% hint style="info" %}
If you provide a `delivered` indicator on order level, **ALL** the lines in the order will be delivered.

If you also provide a `delivered` indicator on line level, it has **precedence** over the order level `delivered` indicator.
{% endhint %}

{% hint style="info" %}
When sending order indicators the provided purchase order number will be verified. 
{% endhint %}
