---
description: How to announce the supplier has shipped goods
---

# Ship goods

{% hint style="warning" %}
This feature is planned and API and documentation may change. 
{% endhint %}

When an order or line is completely shipped by the supplier, it can be marked as shipped by setting `indicators.shipped`on either order or line level and reissue the order:

{% page-ref page="reissue.md" %}

{% hint style="info" %}
Order lines having logistics status `Open` will become `Shipped`

You cannot ship a `Delivered` line.
{% endhint %}

{% hint style="warning" %}
Usually this is indicator is set in the `order-response` by the supplier but in some cases a buyer requires to set it.
{% endhint %}



