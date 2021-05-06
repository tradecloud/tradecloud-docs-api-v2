---
description: How to request the buyer to cancel an order or line
---

# Cancel an order

{% hint style="warning" %}
This feature is planned and API and documentation may change. 
{% endhint %}

If a purchase order line is `Issued` or `In Progress` the supplier may `reject` the line.

If a line is `Confirmed` \(both parties agreed on the delivery of goods\) then the supplier should request to cancel the line.

The supplier can request to cancel by setting `indicators.cancel`on either order or line level, when possible provide the `reason`field on line level and send an order response update.

{% page-ref page="send-order-response/" %}

{% hint style="warning" %}
This is a **request** to the buyer to cancel an order or line. 

The buyer has to **approve** the cancel request before Tradecloud accepts it.
{% endhint %}

{% hint style="warning" %}
You cannot cancel an `Issued, In Progress, Rejected, Cancelled` or`Completed` line
{% endhint %}

{% hint style="info" %}
Order lines having process status`Confirmed` will become `Cancelled`
{% endhint %}

