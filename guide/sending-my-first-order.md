# 2. Sending my first order

Sending an order with only minimal data to Tradecloud is quite simple.
But first, we need to choose a format for the requested deliveries:

1. [Delivery schedule](sending-delivery-schedule/sending-my-first-order.md) — multiple scheduled deliveries per order line
2. [Single delivery](sending-single-delivery/sending-my-first-order.md) — one scheduled delivery per order line

ERP system compatibility is an important consideration when choosing between delivery methods:

- **Multiple deliveries support**: Some ERP systems (like SAP) natively support multiple deliveries per order line, making them fully compatible with Tradecloud's _delivery schedule_ approach.
- **Single delivery limitation**: Other ERP systems can only handle one delivery per order line. If your ERP system has this limitation, the _single delivery_ method is recommended for seamless integration.
