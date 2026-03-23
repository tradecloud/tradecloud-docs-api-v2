---
description: How to request the buyer to reopen an order or line
---

# Reopen an order

If an order line is **confirmed** (buyer and supplier agreed on delivery schedule, prices and related fields), the supplier can **reopen** it to propose different values. Tradecloud creates a line-level reopen workflow task that the buyer can **approve** or **reject**.

## When a reopen request is created

When you send an order response update and the **responded** `delivery schedule`, `prices` and/or `charge lines` are **not equal** to the **confirmed** `delivery schedule`, `prices` and `charge lines`, Tradecloud automatically creates a reopen workflow task for the **buyer**.

When possible, provide the supplier line `reason` field.

## Update a reopen request that is in progress

You may **change an open reopen request** by sending another order response update (new responded values that still differ from confirmed).

{% page-ref page="send-order-response/" %}

## Revert a reopen request

You can **withdraw** an open reopen request **without** waiting for the buyer to approve or reject it.

Send an order response where the **responded** `delivery schedule`, `prices` and `charge lines` are **equal** to the **confirmed** `delivery schedule`, `prices` and `charge lines` — i.e. you align your response with what was already agreed before the reopen.

In that case there is nothing left to negotiate: Tradecloud **reverts** the reopen workflow instead of keeping the line in negotiation. The line can return to process status `Confirmed` and the line-level [`inProgressStatus`](../status.md#line-in-progress-status) is cleared.

This is **not** the same as the buyer rejecting the reopen; you are explicitly matching the last confirmed agreement.

Webhook subscribers receive [`OrderLinesReopenRequestRevertedBySupplier`](../../../connectors/webhooks/order-events.md#order-reopen-request-by-supplier).

{% hint style="warning" %}
This is a **request** to the buyer to reopen an already confirmed order line.

The buyer has to **approve** the reopen request before Tradecloud accepts a **change** that still differs from the confirmed values.
{% endhint %}

{% hint style="warning" %}
You cannot reopen a `Completed` or `Cancelled` line.
{% endhint %}

{% hint style="info" %}
An order line with process status `Confirmed` becomes `InProgress` when a reopen request is open. See [Line process status](../status.md#line-process-status).
{% endhint %}
