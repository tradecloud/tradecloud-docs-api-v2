---
description: How to announce the buyer has received goods
---

# Receive goods

There are two ways to announce the buyer has received goods:

- using the actual delivery, which is preferred over the delivered indicator, as it is more precise regarding partial deliveries.
- using the delivered indicator

## Actual delivery history

The delivery history contains the actual physical deliveries. With the actual deliveries versus the planned deliveries, Tradecloud can calculate which goods should still be delivered or are overdue.

The actual delivery history is matched against the planned delivery schedule **by date and quantity**, not by delivery line position — `deliveryHistory.position` and `deliverySchedule.position` do not have to use the same values.

There are three ways to send the delivery history to Tradecloud:

### Send the delivery history by updating an order using the `/order` endpoint

Send the actual delivery schedule by setting the `lines.deliveryHistory` field when your ERP system supports a delivery schedule natively, and update the order using the [Send order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderByBuyerRoute) endpoint.

Send the actual delivery by setting the `lines.actualDelivery` field when using the single delivery per order line feature, and update the order using the [Send single delivery order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendSingleDeliveryOrderByBuyerRoute) endpoint.

{% page-ref page="update.md" %}

### Send delivery events using the `/api-connector/order/deliveries` endpoint

Send delivery events for one or multiple existing order lines using the [Send order deliveries events](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderDeliveriesByBuyer) endpoint. This will append the deliveries to the order line's delivery history.

{% hint style="warning" %}
Before adding a delivery to an order, the order must have been sent to Tradecloud first.
{% endhint %}

{% hint style="warning" %}
The `/order/deliveries` endpoint is not supported when using the single delivery feature.
Let [support](../support.md) know when you need this endpoint for single delivery.
{% endhint %}

### Replace the delivery history using the `/api-connector/order/deliveryHistory` endpoint

Replace the delivery history for one or multiple existing order lines using the [Send order delivery history](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderDeliveryHistoryByBuyer) endpoint. Unlike `/order/deliveries`, which appends deliveries, this endpoint replaces the delivery history per order line with the deliveries in the request.

Only the lines present in the request are affected; lines not included are left untouched. To clear the delivery history of a line, send that line with an empty `deliveryHistory` array. As with the other methods, the delivery history is matched against the planned delivery schedule by date and quantity.

{% hint style="warning" %}
Before replacing the delivery history of an order, the order must have been sent to Tradecloud first.
{% endhint %}

{% hint style="warning" %}
The `/order/deliveryHistory` endpoint is not supported when using the single delivery feature.
Let [support](../support.md) know when you need this endpoint for single delivery.
{% endhint %}

## Delivered indicator

The delivered indicator marks an order or line as delivered, regardless of the actual quantity or date. It is intended for **stock items** (`lineType` `Item`) where your ERP applies **delivery tolerances** — a quantity received within tolerance is considered sufficiently delivered.

{% hint style="info" %}
**When to use the delivered indicator**

- Use it for **stock items with delivery tolerances**, where a receipt within tolerance counts as delivered. You **may** set `indicators.delivered` **on top of** the [actual delivery history](#actual-delivery-history) for this purpose — the indicator then completes the line even when the reported quantity does not fully match the planned quantity.
- Do **not** use the delivered indicator outside this tolerance use case. When you can report exact received quantities and dates, the actual delivery history alone is sufficient and preferred, as it is more precise about partial deliveries.
{% endhint %}

When an order or line is received, it can be marked as delivered by setting `indicators.delivered` on either order or line level. Unlike the actual delivery history (matched by date and quantity), the delivered indicator is applied by **order line or delivery line position**.

{% hint style="warning" %}
**Single delivery behavior:**

When the primary or any related split lines is delivered; the corresponding delivery line will become delivered.
{% endhint %}

### Mark as delivered by updating an order using the `/order` endpoint

The existing order or line can be marked as delivered by setting `indicators.delivered` on either order or line level and updating the order using the [Send order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderByBuyerRoute) endpoint:

{% page-ref page="update.md" %}

{% hint style="info" %}
If you provide a `delivered` indicator on order level, **ONLY** the lines provided in this order message will be marked as delivered.

If you also provide a `delivered` indicator on line level, it has **precedence** over the order level `delivered` indicator.
{% endhint %}

### Mark as delivered by sending the delivered indicator using the `/order/indicators` endpoint

The order or line can be marked as delivered by setting `indicators.delivered` on either order or line level and sending this indicator only, using the [Send order indicators](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderIndicatorsByBuyerRoute) endpoint.

{% hint style="warning" %}
The `/order/indicators` endpoint is not supported when using the single delivery feature.
Let [support](../support.md) know when you need this endpoint for single delivery.
{% endhint %}

{% hint style="info" %}
If you provide a `delivered` indicator on order level, **ALL** the lines in the order will be delivered.

If you also provide a `delivered` indicator on line level, it has **precedence** over the order level `delivered` indicator.
{% endhint %}
