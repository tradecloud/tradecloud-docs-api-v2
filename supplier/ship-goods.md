---
description: How to annouce the supplier has shipped goods
---

# Ship goods

{% hint style="warning" %}
This feature is planned and API and documentation may change. 
{% endhint %}

When an order or line is completely shipped by the supplier, it can can be marked as shipped by setting `indicators.shipped`on either order or line level and sending an order response update:

{% page-ref page="send-order-response/" %}

{% hint style="info" %}
Order lines having logistics status `Open` will become `Shipped`

You cannot ship a `Delivered` line.
{% endhint %}

