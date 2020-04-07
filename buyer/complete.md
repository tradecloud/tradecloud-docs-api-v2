---
description: How to complete an order or line
---

# Complete an order

{% hint style="warning" %}
This feature is planned. 
{% endhint %}

When an order or line is completely handled at the buyer, usually when the supplier invoice is received and approved by buyer, . 

The order or line can be marked as completed by setting `indicators.completed`on either order or line level and reissue the order:

{% page-ref page="reissue.md" %}

{% hint style="warning" %}
You cannot complete a `Cancelled` line
{% endhint %}

{% hint style="info" %}
Order lines having process status `Issued`, `In Progress` or `Confirmed` will become `Completed`
{% endhint %}



