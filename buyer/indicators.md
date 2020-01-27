---
description: How to use order and line indicators as a buyer
---

# Buyer indicators overview

## Indicators

When sending a purchase order to Tradecloud you can optionally set indicators on both order and line levels.

{% hint style="info" %}
Line indicators have precedence over \(overrule\) order indicators.
{% endhint %}

### No delivery expected

`noDeliveryExpected`: no goods of are expected to be delivered to the buyer.

{% hint style="warning" %}
This feature is planned. Ticket [TC-5564](https://tradecloud.atlassian.net/browse/TC-5564) As a buyer I want to set a "No delivery expected" indicator
{% endhint %}

{% hint style="info" %}
Order lines having `noDeliveryExpected` set will NEVER become `overdue`
{% endhint %}

### Shipped by supplier

`shipped`: all goods of the order or line are completely shipped by the supplier. 

{% hint style="warning" %}
This feature is planned. [TC-5121](https://tradecloud.atlassian.net/browse/TC-5121) As buyer I want to see order lines receive the logistical status ''Shipped/Delivered'' when they have the status "shipped/Delivered" in my ERP system.
{% endhint %}

{% hint style="warning" %}
Usually this is indicator is set in the `order-response` by the supplier but in some cases a buyer requires to set it.
{% endhint %}

{% hint style="info" %}
Order lines having logistics status `Open` will become `Shipped`

You cannot ship a delivered line.
{% endhint %}

### Delivered at buyer

{% hint style="warning" %}
This feature is planned. [TC-5121 ](https://tradecloud.atlassian.net/browse/TC-5121)As buyer I want to see order lines receive the logistical status ''Shipped/Delivered'' when they have the status "shipped/Delivered" in my ERP system.
{% endhint %}

`delivered`: all goods of the order or line are completely delivered at the buyer.

{% hint style="info" %}
Order lines having logistics status `Open` or `Shipped` will become `Delivered`
{% endhint %}

### Completed at buyer

{% hint style="warning" %}
This feature is planned.  Ticket [TC-5186](https://tradecloud.atlassian.net/browse/TC-5186) As a buyer I want to complete orders and lines
{% endhint %}

`completed`: the order or line is completed at the buyer. Usually this indicator is set when the invoice is received and approved by buyer.

{% hint style="warning" %}
You cannot complete a `Cancelled` line
{% endhint %}

{% hint style="info" %}
Order lines having process status `Issued`, `In Progress` or `Confirmed` will become `Completed`
{% endhint %}

### Reopened at buyer

{% hint style="warning" %}
This feature is planned. Ticket TC-4480 As a buyer I want to reopen an order line using a reopen request workflow
{% endhint %}

`reopened`: the order or line is reopened at the buyer

{% hint style="warning" %}
This is a **request** to the supplier to reopen an already agreed order or line. 

The supplier has to approve the reopen request.
{% endhint %}

{% hint style="warning" %}
You cannot reopen a `Completed` or `Cancelled` order or line
{% endhint %}

{% hint style="info" %}
Order lines having process status `Confirmed` will become `InProgress`
{% endhint %}

### Cancelled at buyer

{% hint style="warning" %}
This feature is planned. Ticket [TC-4479](https://tradecloud.atlassian.net/browse/TC-4479) As a buyer I want to cancel an order line using a cancel request workflow.
{% endhint %}

`cancelled`: the order or line is cancelled at the buyer

{% hint style="warning" %}
This is a **request** to the supplier to cancel an order or line. 

The supplier has to approve the cancel request.
{% endhint %}

{% hint style="warning" %}
You cannot cancel a `Completed` line
{% endhint %}

{% hint style="info" %}
Order lines having process status `Issued`, `In Progress` or `Confirmed` will become `Cancelled`
{% endhint %}

