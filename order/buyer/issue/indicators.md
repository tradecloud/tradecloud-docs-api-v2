---
description: How to use order and line indicators as a buyer
---

# Buyer indicators overview

## Order & line indicators

You can set indicators on both order and line levels.
Line indicators have precedence over \(overrule\) order indicators.

{% hint style="warning" %}
When working with the single delivery per order line feature, these indicators behave slightly different, check the [single delivery order line behavior](#single-delivery-order-line-behavior).
{% endhint %}

### Confirmed by buyer

`confirmed`: all goods of this order or line are confirmed by the supplier, according to the buyer.

{% hint style="info" %}
The order or line must have process status `Issued` and will become `Confirmed`.
This indicator is only intended for onboarding or migration of order lines which are already confirmed.
{% endhint %}

### Reconfirmation request by buyer

`requestReconfirmation`: the supplier is requested to reconfirm the order line. The supplier either reconfirms the order line with requested values or alternatively does a reopen request with different values.

{% hint style="info" %}
The order or line must have process status `Confirmed` and will become `InProgress`.
The `inProgressStatus` will become `OpenBuyerReconfirmationRequest`
{% endhint %}

### Shipped by supplier

`shipped`: all goods of this order or line are completely shipped by the supplier, according to the buyer.

{% hint style="info" %}
The order or line having logistics status `Open`, `Produced`, `ReadyToShip`  will become `Shipped`.
{% endhint %}

### Delivered at buyer

`delivered`: all goods of the order or line are completely delivered at the buyer.

{% hint style="info" %}
The order or line having logistics status `Open`, `Produced`, `ReadyToShip` or `Shipped` will become `Delivered`.
{% endhint %}

### Completed at buyer

`completed`: the order or line is completed at the buyer. Usually this indicator is set when the invoice is received and approved by buyer.

- `Issued`, `In progress`, `Rejected` and `Confirmed` lines will become `Completed`.
- `Cancelled` lines cannot be completed.
- `Completed` lines cannot be completed again.
- Completing has precedence over cancelling at the same time.

### Cancelled by buyer

`cancelled`: the order or line is cancelled by the buyer.

- `Issued`, `In Progress`, `Rejected` and `Confirmed` lines will become `Cancelled` immediately.
- `Completed` lines cannot be cancelled.
- `Cancelled` lines cannot be cancelled again.

## Order only indicators

### Auto confirm

`autoConfirm`: If this flag is set to true then the order lines will be automatically confirmed in case of a supplier proposal or reopen request.

### Cancel line when missing

`cancelLineWhenMissing`: If this flag set to true and existing order lines positions are not present among incoming lines then they will be cancelled.

- `Issued`, `In Progress`, `Rejected` and `Confirmed` lines will become `Cancelled` immediately.
- `Completed` lines cannot be cancelled.
- `Cancelled` lines cannot be cancelled again.

## Order line only indicators

### No delivery expected

`noDeliveryExpected`: no goods of are expected to be delivered to the buyer.

{% page-ref page="no-delivery-expected.md" %}

### Propose when accepted

`proposeWhenAccepted`: If this flag is set to true then this line becomes automatically a supplier proposal in case the supplier the accepts a line.

{% page-ref page="propose-when-accepted.md" %}

## Single delivery order line behavior

{% hint style="info" %}
**How indicators work with single delivery per order line:**

When using the single delivery per order line feature, Tradecloud manages related lines through the `originalPosition` reference. This affects how indicators behave:
{% endhint %}

### Indicator behaviors

| Indicator | Behavior with single delivery |
|-----------|-------------------------------|
| `confirmed` | The primary order line and all related split lines will only become confirmed when all are confirmed |
| `requestReconfirmation` | Only needs to be set on the primary order line; Tradecloud will apply it to all related split lines |
| `shipped` | Can be set on individual lines; the primary order line will become shipped when all related split lines are shipped |
| `delivered` | Can be set on individual lines; the primary order line will become delivered when all related split lines are delivered |
| `completed`| Should only be set on the primary order line; Tradecloud will automatically complete all related split lines |
| `cancelled`| Should only be set on the primary order line; Tradecloud will automatically cancel all related split lines |
| `proposeWhenAccepted` | Should only be set on the primary order line; Tradecloud will apply the proposal to all related split lines when accepted |

This approach ensures consistent status tracking across all related order lines while minimizing the need to set indicators on each individual split line.
