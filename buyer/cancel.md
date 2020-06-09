---
description: How to request the supplier to cancel an order or line
---

# Cancel an order

{% hint style="warning" %}
This feature is planned and API and documentation may change. 
{% endhint %}

If a purchase order line is `Issued` the buyer may `cancel` the line immediately.

If a line is `In Progress` \(parties are negotiating\) or `Confirmed` \(both parties agreed on the delivery of goods\) then the buyer should request to cancel the line.

The buyer can request to cancel by setting `indicators.cancel`on either order or line level, when possible provide the `reason`field on line level  and reissue the order.

{% page-ref page="reissue.md" %}

{% hint style="warning" %}
When the line is `In progress` or `Confirmed` it is a **request** to the supplier to cancel a line. 

The supplier has to **approve** the cancel request before Tradecloud accepts it.
{% endhint %}

{% hint style="warning" %}
You cannot cancel a `Rejected, Cancelled` or`Completed` line
{% endhint %}

{% hint style="info" %}
Order lines having process status `Issued,` `In Progress` or `Confirmed` will become `Cancelled`
{% endhint %}



