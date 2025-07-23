---
description: >-
  Tradecloud triggers a webhook to notify the buyer or supplier the order or
  shipment is new or has been updated.
---

# Webhook Connector

## Using the webhook

### Tradecloud sends a webhook trigger to your webhook service

When an order or shipment is new or has been changed at Tradecloud, we will trigger your webhook realtime.
Tradecloud will send a `POST` request to your webhook API, which will contain the **order**, **order documents** or **shipment event** in the JSON or tXML body. 

#### Documents

If you are receiving **order documents events**, the POST request body contains a document `objectId`. You must [download the document](https://docs.tradecloud1.com/api/processes/order/buyer/receive/download-document) as the document content is not embedded in the event itself.

## Next: setting up the webhook

{% page-ref page="setting-up-the-webhook.md" %}
