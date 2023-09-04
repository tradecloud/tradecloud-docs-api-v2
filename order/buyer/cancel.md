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

Use the [Send order indicators](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderIndicatorsByBuyerRoute) endpoint to send the cancelled indicator to Tradecloud.

{% hint style="info" %}
When sending order indicators the provided purchase order number will be verified. 
{% endhint %}
