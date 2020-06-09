---
description: How to request the supplier to reopen an order line
---

# Reopen an order

{% hint style="warning" %}
This feature is under development and API and documentation may change. 
{% endhint %}

If an order line is confirmed \(both parties agreed on the delivery of goods\) then the buyer should  request to `reopen` the line. Tradecloud will create a line level reopen workflow task which the supplier can approve, reject or propose an alternative.

When you reissue an order line with the  **requested** `delivery schedule` or `prices` **NOT** **equal** to the **confirmed** `delivery schedule` and `prices`, Tradecloud will automatically create a reopen workflow task for the supplier. When possible provide the buyer line `reason`field.

You may **update an reopen request** which is in progress, by reissuing an order line again.

{% page-ref page="reissue.md" %}

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

