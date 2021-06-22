---
description: How to use order and line indicators as a buyer
---

# Buyer indicators overview

## Indicators

You can set indicators on both order and line levels.
Line indicators have precedence over \(overrule\) order indicators.

### No delivery expected

`noDeliveryExpected`: no goods of are expected to be delivered to the buyer.

{% hint style="warning" %}
This feature is planned. Ticket [TC-5564](https://tradecloud.atlassian.net/browse/TC-5564)
 As a buyer I want to set a "No delivery expected" indicator.
{% endhint %}

{% hint style="info" %}
Order lines having `noDeliveryExpected` set will NEVER become `overdue`.
{% endhint %}

### ReadyToShip indicated by buyer

`ReadyToShip`: this indicator is not implemented on order or line level, please use value `ReadyToShip` in the `deliverySchedule.status`.

### Shipped by supplier

`Shipped`: this indicator is not implemented on order or line level, please use value `Shipped` in the `deliverySchedule.status`.

### Delivered at buyer

`delivered`: all goods of the order or line are completely delivered at the buyer.

{% hint style="info" %}
Order lines having logistics status `Open`, `Produced`, `ReadyToShip` or `Shipped` will become `Delivered`.
{% endhint %}

### Completed at buyer

`completed`: the order or line is completed at the buyer. Usually this indicator is set when the invoice is received and approved by buyer.

- `Issued`, `Rejected` and `Confirmed` lines will become `Completed`.
- `In progress` and `Cancelled` lines cannot be completed.
- `Completed` lines cannot be completed again.
- Completing has precedence over cancelling at the same time.

### Cancelled at buyer

`cancelled`: the order or line is cancelled at the buyer.

- `Issued`, `In Progress`, `Rejected` and `Confirmed` lines will become `Cancelled` immediately.
- `Completed` lines cannot be cancelled.
- `Cancelled` lines cannot be cancelled again.

### Cancel line when missing

`cancelLineWhenMissing`: when set on order level, and a line is missing in the order update, the line is assumed cancelled at the buyer.

- `Issued`, `In Progress`, `Rejected` and `Confirmed` lines will become `Cancelled` immediately.
- `Completed` lines cannot be cancelled.
- `Cancelled` lines cannot be cancelled again.
