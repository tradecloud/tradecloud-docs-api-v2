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
 As a buyer I want to set a "No delivery expected" indicator
{% endhint %}

{% hint style="info" %}
Order lines having `noDeliveryExpected` set will NEVER become `overdue`
{% endhint %}

### Shipped by supplier

`shipped`: all goods of the order or line are completely shipped by the supplier.

{% hint style="warning" %}
This feature is planned. Ticket [TC-5667](https://tradecloud.atlassian.net/browse/TC-5667) As buyer I want to see order lines receive the logistical status ''Shipped'' when they have the status "shipped" in my ERP system.
{% endhint %}

- Order lines having logistics status `Open` will become `Shipped`
- `Delivered` lines cannot be shipped
- `Shipped` lines cannot be shipped again

{% hint style="warning" %}
Usually this is indicator is set in the `order-response` by the supplier but in some cases a buyer requires to set it.
{% endhint %}

### Delivered at buyer

`delivered`: all goods of the order or line are completely delivered at the buyer.

{% hint style="info" %}
Order lines having logistics status `Open` or `Shipped` will become `Delivered`
{% endhint %}

### Completed at buyer

`completed`: the order or line is completed at the buyer. Usually this indicator is set when the invoice is received and approved by buyer.

- `Issued`, `Rejected` and `Confirmed` lines will become `Completed`
- `In progress` and `Cancelled` lines cannot be completed
- `Completed` lines cannot be completed again
- Completing has precedence over cancelling at the same time

### Cancelled at buyer

`cancelled`: the order or line is cancelled at the buyer

{% hint style="warning" %}
This is a **request** to the supplier to cancel an order or line.

The supplier has to approve the cancel request.
{% endhint %}

- `Issued`, `In Progress`, `Rejected` and `Confirmed` lines will become `Cancelled` immediately (without request)
- `Completed` lines cannot be cancelled
- `Cancelled` lines cannot be cancelled again
