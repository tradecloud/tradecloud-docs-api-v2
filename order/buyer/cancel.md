---
description: How to request the supplier to cancel an order or line
---

# Cancel an order

Cancel an order line in Tradecloud when it is cancelled at the buyer.

- `Issued`, `In Progress`, `Rejected` and `Confirmed` lines will become `Cancelled` immediately
- `Completed` lines cannot be cancelled
- `Cancelled` lines cannot be cancelled again

{% hint style="warning" %}
**Single delivery behavior:**

When using the single delivery per order line feature, cancellation works differently depending on whether you're cancelling all order lines or an individual line:

- When all primary and related split lines are cancelled; the primary order line will become cancelled. 
- When an individual order line is cancelled; Tradecloud will remove the individual line from the orginal line's delivery schedule.
{% endhint %}

## Cancelling by resending an order using the `/order` endpoint

You can cancel the order or line by setting `indicators.cancelled` on either order or line level and updating the order using the [Send order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderByBuyerRoute) endpoint:

{% page-ref page="update.md" %}

{% hint style="info" %}
If you provide a `cancelled` indicator on order level, **ONLY** the lines provided in this order message will be cancelled.

If you also provide a `cancelled` indicator on line level, it has **precedence** over the order level `cancelled` indicator.
{% endhint %}

## Cancelling by resending the order without the cancelled line using the `/order` endpoint

When your ERP system cannot cancel a line, but instead removes a line from the order, you can still cancel an order line by setting the `indicators.cancelLineWhenMissing` on order level and updating the order WITHOUT including the cancelled line using the [Send order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderByBuyerRoute) endpoint:

{% page-ref page="update.md" %}

{% hint style="info" %}
You can cancel a full order \(all the lines\) by setting the `indicators.cancelLineWhenMissing` on order level and updating the order WITHOUT any lines.
{% endhint %}

## Cancelling by sending the cancelled indicator using the `/order/indicators` endpoint

You can cancel the order or line by setting `indicators.cancelled` on either order or line level, using the [Send order indicators](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderIndicatorsByBuyerRoute) endpoint to send the cancelled indicator to Tradecloud.

{% hint style="warning" %}
The `/order/indicators` endpoint is not supported when using the single delivery feature.
Let [support](../support.md) know when you need this endpoint for single delivery.
{% endhint %}

{% hint style="info" %}
If you provide a `cancelled` indicator on order level, **ALL** the lines in the order will be cancelled.

If you also provide a `cancelled` indicator on line level, it has **precedence** over the order level `cancelled` indicator.
{% endhint %}

## Revert cancellation

You can revert a `Cancelled` order line by sending a **full order update** with
an explicit **line-level** `indicators.cancelled=false`.

Applicable endpoints:

- [Send order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderByBuyerRoute)
- [Send single delivery order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendSingleDeliveryOrderByBuyerRoute)

{% hint style="warning" %}
Order-header-level `cancelled=false` does **not** revert lines. The
`/order/indicators` endpoint does **not** support reverting.
{% endhint %}

Resulting [process status](../status.md#line-process-status):

| Situation | Result |
| --- | --- |
| No confirmed line | `InProgress` with [`inProgressStatus`](../status.md#line-in-progress-status) `RevertedCancelledLine` |
| Confirmed line, unchanged agreed prices, delivery schedule and charge lines | `Confirmed` |
| Confirmed line, changed agreed prices, delivery schedule or charge lines | `InProgress` with `OpenBuyerReopenRequest`; the confirmed agreement stays unchanged until the supplier approves — see [Reopen an order](reopen.md) |

Logistics status is recalculated from the delivery schedule (typically `Open` when no
deliveries remain). `cancelledAt` is cleared; `confirmedAt` is unchanged when a confirmed
agreement existed.

Webhook subscribers receive
[`CancelledOrderLinesRevertedByBuyer`](../../../connectors/webhooks/order-events.md#order-lines-cancelled-by-buyer).
