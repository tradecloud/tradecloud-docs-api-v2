---
description: How to receive a shipment event
---

# Receive a shipment event

Tradecloud will send a shipment event to the buyer when a shipment event has been triggered.

At this moment a shipment event will only be triggered when the supplier issues or updates a despatch advice.

## Choose the appropriate API to receive the shipment event

Currently only the shipment webhook API is supported.

See [Webhook Connector](https://tradecloud.gitbook.io/connectors/webhook-connector) for setting up and using the webhook.

Contact support if you need the polling API to receive shipment messages:

{% page-ref page="../../api/webhook-vs-polling.md" %}

## ShipmentEvent

* `eventName`: the event name, currently only `ShipmentDespatchedBySupplier`
* `shipment`: the shipment state, see below
* `meta`: the message meta information, see below

## Shipment state

* `id`: the Tradecloud shipmmet identifier
* `trackingNumber`: the tracking number of the shipment

### Shipment supplier part


### Shipment buyer part

