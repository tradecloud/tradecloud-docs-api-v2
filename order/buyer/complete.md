---
description: How to complete an order or line
---

# Complete an order

Complete an order line in Tradecloud when it is completely handled at the buyer, usually when the supplier invoice is received and approved by buyer.

* `Issued`, `Rejected` and `Confirmed` lines will become `Completed`
* `In progress` and `Cancelled` lines cannot be completed
* `Completed` lines cannot be completed again
* Completing has precedence over cancelling at the same time

{% hint style="warning" %}
**Single delivery order line completion behavior:**

When using the single delivery per order line feature:

1. The `completed` indicator should only be set on the **primary order line** (the first line with a specific item number)
2. Tradecloud will automatically complete all related split lines that reference the primary line via their `originalPosition` field.

This ensures consistent completion across all related order lines without requiring individual completion of each split line.
{% endhint %}

## Completing by resending an order using the `/order` API

The order or line can be marked as completed by setting `indicators.completed` on either order or line level and updating the order using the [Send order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderByBuyerRoute) endpoint:

{% page-ref page="update.md" %}

{% hint style="info" %}
If you provide a `completed` indicator on order level, **ONLY** the lines provided in this order message will be completed.

If you also provide a `completed` indicator on line level, it has **precedence** over the order level `completed` indicator.
{% endhint %}

## Completing by sending the completed indicator using the `/order/indicators` API

The order or line can be marked as completed by setting `indicators.completed` on either order or line level and sending this indicator only, using the `/order/indicators` API resource.

Use the [Send order indicators](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderIndicatorsByBuyerRoute) endpoint to send the completed indicator to Tradecloud.

{% hint style="info" %}
When sending order indicators the provided purchase order number will be verified. 
{% endhint %}
