---
description: How to complete an order or line
---

# Complete an order

{% hint style="warning" %}
This feature is planned.  Ticket [TC-5186](https://tradecloud.atlassian.net/browse/TC-5186) As a buyer I want to complete orders and lines
{% endhint %}

When an order or line is completely handled at the buyer, usually when the supplier invoice is received and approved by buyer, . 

The order or line can be marked as completed by [reissue an order](reissue.md) and setting `indicators.completed`on either order or line level.

{% hint style="warning" %}
You cannot complete a `Cancelled` line
{% endhint %}

{% hint style="info" %}
Order lines having process status `Issued`, `In Progress` or `Confirmed` will become `Completed`
{% endhint %}

{% page-ref page="indicators.md" %}



