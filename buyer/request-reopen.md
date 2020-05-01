---
description: How to request the supplier to reopen an order line
---

# Request to reopen an order



{% hint style="warning" %}
This feature is under development and API and documentation may change. 
{% endhint %}

If an order line is confirmed \(both parties agreed on the delivery of goods\) then the buyer should  request to `reopen` the line. Tradecloud will create a line level reopen workflow task which the supplier can approve, reject or propose an alternative.

{% hint style="warning" %}
This is a **request** to the supplier to reopen an already confirmed order line. 

The supplier has to **approve** the reopen request before Tradecloud accepts it.
{% endhint %}

{% hint style="warning" %}
You cannot reopen a `Completed` or `Cancelled` line
{% endhint %}

{% hint style="info" %}
An order line having process status `Confirmed` will become `InProgress`
{% endhint %}

## Automatic reopen request

When you reissue a line and change line `item`, `delivery schedule` or `prices`, Tradecloud will automatically create line level reopen workflow task for the supplier. In this case you do not have to set `indicators.reopened`

{% page-ref page="reissue.md" %}

## Forced reopen request

If you want the change other line values you can force a reopen request by setting `indicators.reopenRequest`on line level and reissue the order.

{% page-ref page="reissue.md" %}

