---
description: >-
  Choose between the webhook or polling APIs to receive an order, order response or shipment message
---

# Webhook versus polling

To receive an order, order response or shipment message you can use either:

* The [Webhooks](../connectors/webhooks/README.md).
* The polling pattern.

## The Webhook Connector

When an order or shipment has been changed at Tradecloud, we will trigger your webhook real-time.

The webhook is most suitable for companies with real-time, high-volume orders and having a web server or integration platform, firewall and SSL certificate available.

We will send a `POST` request to your webhook containing the order or shipment content. See the [Webhooks](../connectors/webhooks/README.md) documentation for more information.

### `POST` Request Content

By using the [Order Webhook](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-connector/specs.yaml#/order-webhook%20endpoints/webhookPost) endpoint for orders, you can receive order event messages. The order webhook `POST` request body sent by Tradecloud contains:

* `eventName`: The event name summarizes what has happened.
* `orderEvent`: The order event, when using a delivery schedule.
* `singleDeliveryOrderEvent`: The order event, when using only one single delivery per order line.
* `orderDocumentsEvent`: The order documents event, when using documents.

By using the [Shipment Webhook](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/shipment-webhook-connector/specs.yaml#/shipment-webhook%20endpoints/webhookPost) endpoint for shipments, you can receive the shipment contents. The shipment webhook `POST` request body sent by Tradecloud contains:

* `eventName`: The event name summarizes what has happened.
* `shipment`: The actual shipment.

Choose webhooks when:

* Receive real-time order or shipment events.
* Receive the full event payload.
* Filter on specific event types only.
* Receive **only** the lines that are **changed**, not the entire order.
* Optionally use XML instead of JSON.

{% hint style="info" %}
Pros:

* Real-time, receive the order or shipment event within a second.
* Order or shipment event content included.
* Can filter on which order or shipment events to receive, in the order & shipment webhook settings in your company settings or filter events yourself in your integration.
* Can choose to use XML instead of JSON.
* No need to build or configure the polling pattern.

Cons:

* Need to build or configure a webhook at your side.
* Need to publish the webhook on the Internet \(web server and firewall required\).
* Need to obtain and configure a public SSL certificate.
{% endhint %}

### Webhook Response

Your webhook is required to return a response with a valid [HTTP Status code](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status) after processing the incoming request.
Based on the HTTP Status code of this response, Tradecloud's Webhook Connector will react as follows:

**`2xx` - Success response**  
Tradecloud considers the event to be successfully processed by your webhook.  
Commonly used success responses are:

* `200` - OK: Your webhook has successfully processed the response.
* `202` - Accepted: Your webhook has verified that the incoming request can be processed and has queued it for processing.

**`4xx` - Client error response**  
Tradecloud considers the event as not successfully processed, but the request will not be retried, as resending the same request is expected to result in the same error.

Commonly used client error responses are:

* `400` - Bad Request: Your webhook found a **functional** error during the processing of the incoming request.
* `401` - Unauthorized: The supplied authentication (eg. credentials) are not valid.
* `403` - Forbidden: Tradecloud is not authorized to perform this action.
* `404` - Not Found: The requested resource, such as the related order, could not be found.

**`5xx` - Server error response**  
Tradecloud considers the event not successfully processed due to an error in the webhook.

Tradecloud will not retry `500` Internal Server Errors, as this code is often used in case of a **functional** error, and resending the same request is expected to result in the same error. Tradecloud will indefinitely retry the request with exponential back-off for other server error codes (>500).

Commonly used server error responses are:

* `500` - Internal Server Error: An error occurred in the webhook.
* `502` - Bad Gateway: The upstream ERP system is not available.
* `503` - Service Unavailable: The webhook is currently not available.
* `504` - Gateway Timeout: There was a timeout when connecting to the upstream ERP system.

## The polling pattern

The polling pattern is an alternative to the webhook pattern and can be used to receive an order or shipment by polling the Tradecloud API.

Periodically, typically each 5 minutes, check if there are new or updated orders or shipments by using the last updated date time stamp of the last fetched order or shipment.

The polling pattern is most suitable for companies with low-volume orders, and not willing to invest in a web server, firewall and SSL certificate.

{% hint style="info" %}
Pros:

* No webhook needed: no web server, firewall or SSL certificate needed.
* Can use the single delivery per order line feature.

Cons:

* Not real-time, a polling period is typically 5 mins.
* Need to build or configure a periodic polling pattern at your side.
* Cannot filter on which order or shipment events to act on, will receive any order or shipment change, including echoed changes from your ERP system.
* Cannot see what order or shipment event happened, multiple events may have happened.
* Cannot choose XML, but must use JSON.
{% endhint %}

For polling usage see:

{% page-ref page="polling/README.md" %}

For handling echoed changes from your ERP system see:

{% page-ref page="polling/echo.md" %}
