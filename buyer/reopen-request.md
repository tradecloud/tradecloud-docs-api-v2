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

When you reissue an order line with  **requested** `delivery schedule` and `prices` **NOT** **equal** to the **confirmed** `delivery schedule` and `prices`, Tradecloud will automatically create a line level reopen workflow task for the supplier. 

In this case you do not have to set buyer line  `indicators.reopened`

When possible provide the buyer line `reason`field.

{% page-ref page="reissue.md" %}

## Forced reopen request

If you want the change other line values you can force a reopen request by setting the buyer line `indicators.reopenRequest` and reissue the order.

{% page-ref page="reissue.md" %}

