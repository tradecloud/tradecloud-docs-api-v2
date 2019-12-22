---
description: How to request the supplier to cancel an order or line
---

# Request to cancel an order

{% hint style="warning" %}
This feature is planned. Ticket [TC-4479](https://tradecloud.atlassian.net/browse/TC-4479) As a buyer I want to cancel an order line using a cancel request workflow.
{% endhint %}

If an order or line is confirmed \(both parties agreed on the delivery of goods\) then the buyer should  request to change the order / line, called `reopen` in the confirmed case.

You can request to reopen by [reissue an order](reissue.md) and setting `indicators.cancelled`on either order or line level. This means the line is `cancelled` at the buyer side.

{% hint style="warning" %}
This is a **request** to the supplier to cancel an order or line. 

The supplier has to **approve** the cancel request before Tradecloud accepts it.
{% endhint %}

{% hint style="warning" %}
You cannot cancel a `Completed` line
{% endhint %}

{% hint style="info" %}
Order lines having process status `Issued`, `In Progress` or `Confirmed` will become `Cancelled`
{% endhint %}

{% page-ref page="indicators.md" %}



