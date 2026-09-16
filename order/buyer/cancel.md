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

When using the single delivery per order line feature, cancellation works
differently depending on whether you're cancelling all order lines or an
individual line:

- When all primary and related split lines are cancelled; the primary order line will become cancelled.
- When an individual order line is cancelled; Tradecloud will remove the individual line from the orginal line's delivery schedule.
{% endhint %}

## Cancelling by resending an order using the `/order` endpoint

You can cancel the order or line by setting `indicators.cancelled` on either
order or line level and updating the order using the [Send
order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderByBuyerRoute)
endpoint:

{% page-ref page="update.md" %}

{% hint style="info" %}
If you provide a `cancelled` indicator on order level, **ONLY** the lines
provided in this order message will be cancelled.

If you also provide a `cancelled` indicator on line level, it has **precedence**
over the order level `cancelled` indicator.
{% endhint %}

## Cancelling by resending the order without the cancelled line using the `/order` endpoint

When your ERP system cannot cancel a line, but instead removes a line from the
order, you can still cancel an order line by setting the
`indicators.cancelLineWhenMissing` on order level and updating the order WITHOUT
including the cancelled line using the [Send
order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderByBuyerRoute)
endpoint:

{% page-ref page="update.md" %}

{% hint style="info" %}
You can cancel a full order \(all the lines\) by setting the
`indicators.cancelLineWhenMissing` on order level and updating the order WITHOUT
any lines.
{% endhint %}

## Cancelling by sending the cancelled indicator using the `/order/indicators` endpoint

You can cancel the order or line by setting `indicators.cancelled` on either
order or line level, using the [Send order
indicators](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderIndicatorsByBuyerRoute)
endpoint to send the cancelled indicator to Tradecloud.

{% hint style="warning" %}
The `/order/indicators` endpoint is not supported when using the single delivery
feature. Let [support](../support.md) know when you need this endpoint for
single delivery.
{% endhint %}

{% hint style="info" %}
If you provide a `cancelled` indicator on order level, **ALL** the lines in the
order will be cancelled.

If you also provide a `cancelled` indicator on line level, it has **precedence**
over the order level `cancelled` indicator.
{% endhint %}

## Revert cancellation

Revert the cancellation of a `Cancelled` line by setting the line-level
indicator `cancelled=false` in a full order update, using the [Send
order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderByBuyerRoute)
or [Send single delivery
order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendSingleDeliveryOrderByBuyerRoute)
endpoint.

{% hint style="info" %}
Only an explicit `false` on line level reverts. Omitting the `cancelled`
indicator leaves the line unchanged and is not the same as sending `false`. A
`false` on order level does not revert, and the `/order/indicators` endpoint
does not support reverting.
{% endhint %}

Unlike reverting a completion, reverting a cancellation always asks the supplier
to act before the line is agreed again. The resulting status depends on whether
the line was agreed with the supplier before:

- If the line was never confirmed, it returns to `Issued` and the supplier is
  asked to confirm it.
- If the line was confirmed and the agreed prices, delivery schedule and charge
  lines are unchanged, the supplier is asked to reconfirm them. The line becomes
  `InProgress` with [in progress
  status](../status.md#line-in-progress-status) `OpenBuyerReconfirmationRequest`.
- If the line was confirmed and the agreed prices, delivery schedule or charge
  lines changed, a buyer reopen request is created. The line becomes
  `InProgress` with `OpenBuyerReopenRequest` and the confirmed values stay in
  place until the supplier approves. See [Reopen an order](reopen.md).

{% hint style="warning" %}
**Single delivery behavior:**

When using the single delivery per order line feature, reverting does not
restore a line that was removed from the parent's delivery schedule when it was
cancelled.
{% endhint %}

Webhook subscribers receive
[`CancelledOrderLinesRevertedByBuyer`](../../../connectors/webhooks/order-events.md#order-lines-cancelled-by-buyer),
or
[`OrderLinesReopenRequestedByBuyer`](../../../connectors/webhooks/order-events.md#order-reopen-request-by-buyer)
on the changed-agreement path.
