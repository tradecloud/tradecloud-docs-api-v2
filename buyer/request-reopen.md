---
description: How to request the supplier to reopen an order or line
---

# Request to reopen an order

{% hint style="warning" %}
This feature is planned. 
{% endhint %}

If an order or line is confirmed \(both parties agreed on the delivery of goods\) then the buyer should  request to `reopen` the order / line. Tradecloud will create a reopen workflow task which the supplier can approve, reject or propose an alternative.

{% hint style="warning" %}
This is a **request** to the supplier to reopen an already agreed order or line. 

The supplier has to **approve** the reopen request before Tradecloud accepts it.
{% endhint %}

{% hint style="warning" %}
You cannot reopen a `Completed` or `Cancelled` order or line
{% endhint %}

{% hint style="info" %}
Order lines having process status `Confirmed` will become `InProgress`
{% endhint %}

## Automatic reopen request

When you reissue an order and change `delivery schedule` or `prices`, Tradecloud will automatically create a supplier reopen workflow task. In this case you do not have to set `indicators.reopened`

{% page-ref page="reissue.md" %}

## Forced reopen request

If you want the change other values, like the delivery address, you can force a reopen request by setting `indicators.reopened`on either order or line level and reissue the order.

See also:

{% page-ref page="indicators.md" %}



