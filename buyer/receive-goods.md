---
description: How to announce the buyer has received goods
---

# Receive goods

There are two ways to announce the buyer has received goods. Using the actual delivery schedule is preferred over the delivered indicator, as it is more precise regarding partial deliveries.

## Actual delivery schedule

This schedule contains the actual physical deliveries. With the actual deliveries versus the planned deliveries Tradecloud can calculate which goods should still be delivered or are even overdue.

The actual delivery schedule can be send by setting `lines.deliveryHistory` and update the order:

{% page-ref page="update.md" %}

## Delivered indicator

{% hint style="warning" %}
This feature is planned and API and documentation may change. 
{% endhint %}

When an order or line is received, regardless of actual quantity or date, it can can be marked as delivered by setting `indicators.delivered`on either order or line level and update the order:

{% page-ref page="update.md" %}



