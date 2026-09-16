---
description: How to complete an order or line
---

# Complete an order

Complete an order line in Tradecloud when it is completely handled at the buyer,
usually when the supplier invoice is received and approved by buyer.

* `Issued`, `Rejected` and `Confirmed` lines will become `Completed`
* `In progress` and `Cancelled` lines cannot be completed
* `Completed` lines cannot be completed again
* Completing has precedence over cancelling at the same time

{% hint style="warning" %}
**Single delivery behavior:**

When all primary and related split lines are completed; the primary order line
will become completed.
{% endhint %}

## Completing by resending an order using the `/order` endpoint

The order or line can be marked as completed by setting `indicators.completed`
on either order or line level and updating the order using the [Send
order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderByBuyerRoute)
endpoint:

{% page-ref page="update.md" %}

{% hint style="info" %}
If you provide a `completed` indicator on order level, **ONLY** the lines
provided in this order message will be completed.

If you also provide a `completed` indicator on line level, it has **precedence**
over the order level `completed` indicator.
{% endhint %}

## Completing by sending the completed indicator using the `/order/indicators` endpoint

The order or line can be marked as completed by setting `indicators.completed`
on either order or line level and sending this indicator only, using the
`/order/indicators` endpoint.

Use the [Send order
indicators](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderIndicatorsByBuyerRoute)
endpoint to send the completed indicator to Tradecloud.

{% hint style="warning" %}
The `/order/indicators` endpoint is not supported when using the single delivery
feature. Let [support](../support.md) know when you need this endpoint for
single delivery.
{% endhint %}

{% hint style="info" %}
If you provide a `completed` indicator on order level, **ALL** the lines in the
order will be completed.

If you also provide a `completed` indicator on line level, it has **precedence**
over the order level `completed` indicator.
{% endhint %}

## Revert completion

Revert the completion of a `Completed` line by setting the line-level indicator
`completed=false` in a full order update, using the [Send
order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderByBuyerRoute)
or [Send single delivery
order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendSingleDeliveryOrderByBuyerRoute)
endpoint.

{% hint style="info" %}
Only an explicit `false` on line level reverts. Omitting the `completed`
indicator leaves the line unchanged and is not the same as sending `false`. A
`false` on order level does not revert, and the `/order/indicators` endpoint
does not support reverting.
{% endhint %}

The resulting status depends on whether the line was agreed with the supplier
before:

* If the line was never confirmed, it becomes `InProgress` with [in progress
  status](../status.md#line-in-progress-status) `RevertedCompletedLine`.
* If the line was confirmed and the agreed prices, delivery schedule and charge
  lines are unchanged, it returns to `Confirmed`.
* If the line was confirmed and the agreed prices, delivery schedule or charge
  lines changed, a buyer reopen request is created. The line becomes
  `InProgress` with `OpenBuyerReopenRequest` and the confirmed values stay in
  place until the supplier approves. See [Reopen an order](reopen.md).

Reverting completion does not create a task for the supplier. Webhook
subscribers receive
[`CompletedOrderLinesRevertedByBuyer`](../../../connectors/webhooks/order-events.md#order-lines-completed-by-buyer),
or
[`OrderLinesReopenRequestedByBuyer`](../../../connectors/webhooks/order-events.md#order-reopen-request-by-buyer)
on the changed-agreement path.
