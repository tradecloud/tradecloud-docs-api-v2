---
description: How to use order and line indicators as a buyer
---

# Buyer indicators overview

## Order & line indicators

You can set indicators on both order and line levels.
Line indicators have precedence over \(overrule\) order indicators.

### Confirmed by buyer

`confirmed`: all goods of this order or line are confirmed by the supplier, according to the buyer.

{% hint style="info" %}
The order or line must have process status `issued` and will become `confirmed`. 
This indicator is only intended for onboarding or migration of order lines which are already confirmed.
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
