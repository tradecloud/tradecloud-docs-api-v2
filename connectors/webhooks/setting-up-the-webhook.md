---
description: Setting up the webhook at the customer side
---

# Setting up the webhook

To receive a webhook trigger you will need:

- A simple web service reachable from the internet, which listens to some URL.
- The web service must support **SSL** only and you will need a SSL certificate.
- The web service must be configured to use **TLS v1.2** or **v1.3**.
- Self-signed certificates are NOT supported.
- The web service must support either  **basic authentication**, **static bearer token** or **OAuth 2.0 Client Credentials Grant**.
- The webservice must support the **POST** HTTP method and be able to parse the request body in **JSON** or **tXML**

{% hint style="info" %}
You can test the security level of your certificate at [SSL Labs](https://www.ssllabs.com/ssltest/)
{% endhint %}

## Setting up the order webhook

Your webhook must implement the [order webhook OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-connector/specs.yaml#/order-webhook%20endpoints/webhookPost):

- Use the `orderEvent` field when working with a delivery schedule with multiple deliveries per order line.
- Use the `singleDeliveryOrderEvent` field when with working with a single delivery per order line.
- Use the `orderDocumentsEvent` field when receiving order documents.

See [the API manual](https://docs.tradecloud1.com/api/introduction/api/delivery-schedule) to read about the delivery schedule versus the single delivery per order line.

{% hint style="warning" %}
An `orderEvent` or `singleDeliveryOrderEvent` will **only** contain the order lines **affected** by the event.
{% endhint %}

When using the `orderDocumentsEvent` field, you must [download the document](https://docs.tradecloud1.com/api/processes/order/buyer/receive/download-document) as the document content is not embedded in the event itself.

## Setting up the shipment webhook

Your webhook must implement the [shipment webhook OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/shipment-webhook-connector/specs.yaml#/shipment-webhook%20endpoints/webhookPost): 

{% hint style="warning" %}
THe shipment even will contain **all** the lines and documents.
You can filter new/changed lines and documents based on the `lastUpdatedAt` fields.
{% endhint %}

When using a `documents` field, you must [download the document](https://docs.tradecloud1.com/api/processes/shipment/buyer/receive/download-document) as the document content is not embedded in the event itself.

## Next: configure the webhook

{% page-ref page="configure-the-webhook.md" %}
