---
description: How to request the supplier to reopen an order line
---

# Reopen an order

If an order line is **confirmed** (buyer and supplier agreed on delivery
schedule, prices and related fields), the buyer can **reopen** it to propose
different values. Tradecloud creates a line-level reopen workflow task that the
supplier can **approve**, **reject** or **answer with a proposal**.

## When a reopen request is created

When you **reissue** an order line and the **requested** `delivery schedule` and
`prices` are **not equal** to the **confirmed** `delivery schedule` and
`prices`, Tradecloud automatically creates a reopen workflow task for the
supplier.

When possible, provide the buyer line `reason` field.

## Update a reopen request that is in progress

You may **change an open reopen request** by updating the order line again (same
as creating a reopen: new requested values that still differ from confirmed).

{% page-ref page="update.md" %}

## Revert a reopen request

You can **withdraw** an open reopen request **without** waiting for the
supplier to approve or reject it.

Send an order update where the **requested** `delivery schedule` and `prices`
are **equal** to the **confirmed** `delivery schedule` and `prices` — i.e. you
align your request with what was already agreed before the reopen.

In that case there is nothing left to negotiate: Tradecloud **reverts** the
reopen workflow instead of keeping the line in negotiation. The line can return
to process status `Confirmed` and the line-level
[`inProgressStatus`](../status.md#line-in-progress-status) is cleared.

This is **not** the same as the supplier rejecting the reopen; you are
explicitly matching the last confirmed agreement.

Webhook subscribers receive
[`OrderLinesReopenRequestRevertedByBuyer`](../../../connectors/webhooks/order-events.md#order-reopen-request-by-buyer).

{% hint style="warning" %}
This is a **request** to the supplier to reopen an already confirmed order line.

The supplier has to **approve** the reopen request before Tradecloud accepts a
**change** that still differs from the confirmed values.
{% endhint %}

{% hint style="warning" %}
There is no direct reopen for a `Completed` or `Cancelled` line. First
[revert completion](complete.md#revert-completion) or
[revert cancellation](cancel.md#revert-cancellation) with a full order update.
{% endhint %}

### Reopen after reverting a Completed or Cancelled line

When you revert a previously **confirmed** Completed or Cancelled line and the
update also **changes** agreed prices, delivery schedule or charge lines,
Tradecloud creates a buyer reopen request instead of applying the new agreement
immediately:

- process status becomes `InProgress` with
  [`inProgressStatus`](../status.md#line-in-progress-status)
  `OpenBuyerReopenRequest`
- the existing confirmed agreement stays unchanged until the supplier
  **approves** the reopen request
- the changed values are stored in the open buyer reopen request

If the reverting update leaves agreed prices, delivery schedule and charge lines
unchanged, the line returns to `Confirmed` and no reopen request is created.

{% hint style="info" %}
An order line with process status `Confirmed` becomes `InProgress` when a reopen
request is open. See [Line process status](../status.md#line-process-status).
{% endhint %}
