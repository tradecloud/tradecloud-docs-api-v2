---
description: How to request the buyer to reopen an order or line
---

# Reopen an order

{% hint style="warning" %}
This feature is under development and API and documentation may change.
{% endhint %}

If an order line is confirmed \(both parties agreed on the delivery of goods\) then the supplier should request to `reopen` the line. Tradecloud will create a line level reopen workflow task which the buyer can approve or reject.

When the supplier sends an order response update with **responded** `delivery schedule` and `prices` **NOT** **equal** to the **confirmed** `delivery schedule` and `prices`, Tradecloud will automatically create line level reopen workflow task for the supplier. When possible provide the supplier line `reason`field.

You may **update an reopen request** which is in progress, by sending an order response update again.

{% page-ref page="send-order-response/" %}

{% hint style="warning" %}
This is a **request** to the buyer to reopen an already confirmed order line.

The buyer has to **approve** the reopen request before Tradecloud accepts it.
{% endhint %}

{% hint style="warning" %}
You cannot reopen a `Completed` or `Cancelled` line
{% endhint %}

{% hint style="info" %}
An order line having process status `Confirmed` will become `InProgress`
{% endhint %}

