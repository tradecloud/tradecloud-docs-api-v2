---
description: How to request the supplier to reopen an order or line
---

# Request to reopen an order

{% hint style="warning" %}
This feature is planned. Ticket [TC-4480](https://tradecloud.atlassian.net/browse/TC-4480) As a buyer I want to reopen an order line using a reopen request workflow
{% endhint %}

If an order or line is confirmed \(both parties agreed on the delivery of goods\) then the buyer should  request to change the order / line, called `reopen` in the confirmed case.

You can request to reopen by [reissue an order](reissue.md) and setting `indicators.reopened`on either order or line level. This means the line is `reopened` at the buyer side.

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

{% page-ref page="indicators.md" %}



