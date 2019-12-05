---
description: How to use order and line indicators as a buyer
---

# Indicators

When sending a purchase order to Tradecloud you can optionally set indicators on both order and line levels.

{% hint style="info" %}
Line indicators have precedence over (overrule) order indicators.
{% endhint %}

## Order indicators

- `order.indicators.noDeliveryExpected`: no goods of any line are expected to be delivered to the buyer.

{% hint style="info" %}
Order lines having `noDeliveryExpected` set will NEVER become `overdue`
{% endhint %}

- `order.indicators.shipped`: all goods of every line are completely shipped by the supplier. Usually this is indicator is set in the `order-response` by the supplier but in some cases a buyer requires to set it.

{% hint style="info" %}
Order lines having logistics status `Open` will become `Shipped`
{% endhint %}
  
- `order.indicators.delivered`: all goods of every line are completely delivered at the buyer.

{% hint style="info" %}
Order lines having logistics status `Open` or `Shipped` will become `Delivered`
{% endhint %}

- `order.indicators.completed`: all lines are completed at the buyer. Usually this indicator is set when the invoice is received and approved by buyer.

{% hint style="info" %}
Order lines having process status `Issued`, `In Progress` or `Confirmed` will become `Completed`
{% endhint %}

- `order.indicators.cancelled`: all lines are cancelled by the buyer. 

{% hint style="info" %}
Order lines having process status `Issued`, `In Progress` or `Confirmed` will become `Cancelled`
{% endhint %}

## Line indicators

- `order.indicators.noDeliveryExpected`: no goods of any line are expected to be delivered to the buyer.

{% hint style="info" %}
An order line having `noDeliveryExpected` set will NEVER become `overdue`
{% endhint %}

- `order.indicators.shipped`: all goods of every line are completely shipped by the supplier. Usual this is indicator is set in the `order-response` by the supplier but in some cases a buyer requires to set it.

{% hint style="info" %}
An order line having logistics status `Open` will become `Shipped`
{% endhint %}

- `order.indicators.delivered`: all goods of every line are completely delivered at the buyer.

{% hint style="info" %}
An Order line having logistics status `Open` or `Shipped` will become `Delivered`
{% endhint %}

- `order.indicators.completed`: all lines are completed at the buyer. Usual this indicator is set when the invoice is received and approved by buyer.

{% hint style="info" %}
An order line having process status `Issued`, `In Progress` or `Confirmed` will become `Completed`
{% endhint %}

- `order.indicators.cancelled`: all lines are cancelled by the buyer. 

{% hint style="info" %}
An order line having process status `Issued`, `In Progress` or `Confirmed` will become `Cancelled`
{% endhint %}
