---
description: How to request the supplier to cancel an order or line
---

# Request to cancel an order

{% hint style="warning" %}
This feature is planned. Ticket [TC-4479](https://tradecloud.atlassian.net/browse/TC-4479) As a buyer I want to cancel an order line using a cancel request workflow.
{% endhint %}

If an order or line is confirmed \(both parties agreed on the delivery of goods\) then the buyer should  request to cancel the order / line.

You can request to cancel by setting `indicators.cancelled`on either order or line level adn reissue the order:

{% page-ref page="reissue.md" %}

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



