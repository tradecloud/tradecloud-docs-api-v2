---
description: How to use order and line indicators as a buyer
---

# Indicators

When sending a purchase order to Tradecloud you can optionally set indicators on both order and line levels.

## Order indicators

Order indicators have precedence over (overrule) line indicators.

- `order.indicators.shipped`: all goods of every line are completely shipped by the supplier. Usual this is indicator is set by the supplier in the `order-response` but in some cases a buyer requires to set it.
- `order.indicators.delivered`: all goods of every line are completely delivered at the buyer.
- `order.indicators.noDeliveryExpected`: there are no more deliveries expected at the buyer, even if not all goods have been delivered.

## Line indicators

- `lines.indicators.shipped