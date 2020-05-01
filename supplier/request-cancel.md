---
description: How to request the buyer to cancel an order or line
---

# Request to cancel an order

{% hint style="warning" %}
This feature is planned and API and documentation may change. 
{% endhint %}

If an order or line is confirmed \(both parties agreed on the delivery of goods\) then the supplier should  request to cancel the order / line.

The supplier can request to cancel by setting `indicators.cancelRequest`on either order or line level and send an order response update:

{% page-ref page="send-order-response/" %}

{% hint style="warning" %}
This is a **request** to the buyer to cancel an order or line. 

The buyer has to **approve** the cancel request before Tradecloud accepts it.
{% endhint %}

{% hint style="warning" %}
You cannot cancel a `Completed` line
{% endhint %}

{% hint style="info" %}
Order lines having process status `Issued`, `In Progress` or `Confirmed` will become `Cancelled`
{% endhint %}

