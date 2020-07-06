---
description: How to request the supplier to cancel an order or line
---

# Cancel an order

If a purchase order line is `Issued` , `In Progress`, `Confirmed`or `Rejected` the buyer may `cancel` the line immediately.

The buyer can cancel by setting `indicators.cancel`on either order or line level and reissue the order.

{% page-ref page="reissue.md" %}

{% hint style="warning" %}
You cannot cancel a`Cancelled` or`Completed` line
{% endhint %}

{% hint style="info" %}
Order lines having process status `Issued, In Progress, Confirmed` or `Rejected` will become `Cancelled`
{% endhint %}



