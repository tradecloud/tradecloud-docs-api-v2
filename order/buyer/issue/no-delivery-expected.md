---
description: How to announce a line has no goods delivery expected
---

# No delivery expected

{% hint style="warning" %}
This feature is planned. Ticket [TC-5564](https://tradecloud.atlassian.net/browse/TC-5564)
 As a buyer I want to set a "No delivery expected" indicator.
{% endhint %}

When a line has no goods to be delivered, for example a service, fee or text line, the line can be marked by setting `indicators.noDeliveryExpected`.

You can set `No delivery expected` by using the `/order` API resource, by setting the `indicators.noDeliveryExpected` on line level.

{% hint style="info" %}
Lines having the `noDeliveryExpected` indicator set will never become `Overdue`.
{% endhint %}
