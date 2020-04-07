---
description: How to announce the supplier has shipped goods
---

# Ship goods

{% hint style="warning" %}
This feature is planned. Ticket [TC-5667](https://tradecloud.atlassian.net/browse/TC-5667) As buyer I want to see order lines receive the logistical status ''Shipped'' when they have the status "shipped" in my ERP system.
{% endhint %}

When an order or line is completely shipped by the supplier, it can can be marked as shipped by [reissue an order](reissue.md) and setting `indicators.shipped`on either order or line level.

{% hint style="warning" %}
Usually this is indicator is set in the `order-response` by the supplier but in some cases a buyer requires to set it.
{% endhint %}

{% hint style="info" %}
Order lines having logistics status `Open` will become `Shipped`

You cannot ship a delivered line.
{% endhint %}

{% page-ref page="indicators.md" %}



