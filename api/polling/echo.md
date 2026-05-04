---
description: >-
  How to handle echoed changes in case of an open request when using polling
---

# Handle echoed changes when using polling

## The problem

When your ERP system sends an order update or order response that results in an
**open request** (e.g. a proposal, reopen or reschedule request), the other
party must first approve or reject the change. Until that happens, the
`lines.deliverySchedule` and `lines.prices` fields keep returning the
**previous** issued or confirmed values — not the values you just sent.

On the next poll, your integration receives these old values. If your ERP system
**does not distinguish between `requested` and `confirmed` fields**, it may
overwrite the change it just submitted with the stale values from the poll
response, effectively reverting your own update.

## The solution

Skip processing a polled order line whenever it has an open request that
originated from your side. Use the
[`lines.status.processStatus`](../../order/status.md#line-process-status) or
[`lines.status.inProgressStatus`](../../order/status.md#line-in-progress-status)
fields to detect this.

### Option 1: Ignore all in-progress lines

If your integration does not process open requests at all, ignore any order line
where `lines.status.processStatus` is `InProgress`.

### Option 2: Ignore only your own open requests

If your integration does process incoming requests from the other party, only
skip the lines where **you** are the requesting party:

**Buyer integration** — ignore the response update when
`lines.status.inProgressStatus` is one of:

- `OpenBuyerReopenRequest`
- `OpenBuyerReconfirmationRequest`

**Supplier integration** — ignore the order update when
`lines.status.inProgressStatus` is one of:

- `OpenSupplierProposal`
- `OpenSupplierReopenRequest`
- `OpenSupplierShipmentRescheduleRequest`

See [Line in Progress status](../../order/status.md#line-in-progress-status) for
the complete list of in-progress status values.
