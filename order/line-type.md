---
description: >-
  Order line classification: Item, Service, and Charge lines (lineType) and optional chargeReasonCode.
---

# Order line type

Every purchase order line can be classified with an optional **`lineType`**.
That tells Tradecloud and your supplier whether the line is a physical item, a
service, or a standalone charge (for example freight or handling on its own
line), instead of treating everything implicitly as merchandise.

## Values of `lineType`

- **`Item`** — The line represents goods or a physical article. This is the
  **default** if you omit `lineType`.
- **`Service`** — The line represents a service (labour, subscription,
  fee-for-service, and similar) rather than a stock item.
- **`Charge`** — The line is **only** an allowance or charge (freight,
  packaging, administration, and similar) as its own order line, usually with a
  price on that line.

Omitting `lineType` is **backward compatible** when **sending** an order: those
lines behave like **`Item`**, so existing integrations need no change.

## When suppliers receive an order

On webhook and poll payloads, each **`buyerLine`** includes **`lineType`**:
`Item`, `Service`, or `Charge`. If the buyer did not send `lineType` on issue,
you still receive **`Item`**. **`chargeReasonCode`** is present when the buyer
provided one.

## `chargeReasonCode` on the line

For **`Charge`** lines you can send an optional **`chargeReasonCode`** on the
same order line (not inside nested objects). Values follow
[UNCL7161](https://docs.peppol.eu/poacc/upgrade-3/codelist/UNCL7161/) (UN/CEFACT
charge and allowance reason codes). Example: `FC` (freight).

You may also use `chargeReasonCode` in other combinations as your process
requires; the OpenAPI spec describes allowed shapes.

{% hint style="warning" %}
Tradecloud does not necessarily require `chargeReasonCode` whenever `lineType`
is `Charge`; enforce any business rules in your own ERP if needed.
{% endhint %}

## Relation to nested `chargeLines`

Older integrations could attach extra costs with a nested **`chargeLines`**
array on a line. That model is **deprecated** for new work: model a separate
order line with `lineType` **`Charge`**, line-level pricing, and optionally
`chargeReasonCode`. Legacy documentation for `chargeLines` remains for those
integrations.

## Portal behaviour for charge lines

In the Tradecloud portal, **suppliers cannot split** a buyer line that is a
charge line. Negotiation (accept, reject, propose) otherwise follows the same
line-level flow as other lines.

## Where this appears in the docs

- **Buyer — send an order**: [Line type and charge reason code](buyer/issue/README.md#line-type-and-charge-reason-code)
- **Supplier — inbound order payload**: buyer lines in [Receive an order](supplier/receive/README.md#buyer-line)
