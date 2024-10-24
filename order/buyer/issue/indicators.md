---
description: How to use order and line indicators as a buyer
---

# Buyer indicators overview

## Order & line indicators

You can set indicators on both order and line levels.
Line indicators have precedence over \(overrule\) order indicators.

{% hint style="warning" %}
When working with the single delivery per order line feature, these indicators behave slighty different, check the [single delivery feature](#single-delivery).
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

## Single delivery

When working with the single delivery per order line feature, lines with the same item, prices and terms are grouped into one parent order line with a delivery schedule. In this case, these indicators behave slighty different:

### Confirmed by buyer

The parent order line will only become confirmed, when all grouped lines are confirmed.

### Reconfirmation request by buyer

Only the parent order line has to be reconfirmed.

### Shipped by supplier

This line will become shipped, and the parent order line will become shipped when all grouped lines are marked as shipped.

### Delivered at buyer

This line will become delivered, and the parent order line will become delivered when all grouped lines are marked as delivered.

### Completed at buyer

Only the parent order line will become completed when all grouped lines are marked as completed.

### Cancelled by buyer

This line will be removed from the delivery schedule, and the parent order line will become cancelled when all lines are marked as cancelled.

### Propose when accepted

Only the parent order line will become a proposal.
