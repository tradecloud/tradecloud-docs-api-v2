---
description: >-
  Choose between the webhook API or polling API to receive an order, order response or shipment message
---

# Webhook versus polling

To receive an order, order response or shipment message you can use either:

* The [Webhook Connector](https://tradecloud.gitbook.io/connectors/webhook-connector) using `POST`.
* The [Webhook Connector](https://tradecloud.gitbook.io/connectors/webhook-connector) using `GET`.
* The polling pattern.

## The Webhook Connector

When an order or shipment has been changed at Tradecloud, we will trigger your webhook.

The webhook is most suitable for companies with real time, high volume orders and having a web server or integration platform, firewall and SSL certificate available.

You can either use `POST` to receive order or shipment content or alternatively `GET` to only receive an `orderId` or `shipmentId`.

See [Webhook Connector](https://tradecloud.gitbook.io/connectors/webhook-connector) for setting up and using the webhook.

### Using `POST`

To receive order event messages use the [POST Order Webhook](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-connector/specs.yaml#/order-webhook%20endpoints/webhookPost) endpoint.

When using `POST` the order webhook request body contains:

* `eventName`: The event name summarizes what has happened.
* `orderEvent`: The order event, when using a delivery schedule.
* `singleDeliveryOrderEvent`: The order event, when using only one single delivery per order line.
* `orderDocumentsEvent`: The order documents event, when using documents.

To receive shipment event messages use the [POST Shipment Webhook](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/shipment-webhook-connector/specs.yaml#/shipment-webhook%20endpoints/webhookPost) endpoint.

When using `POST` the shipment webhook request body contains:

* `eventName`: The event name summarizes what has happened.
* `shipment`: The actual shipment.

Use `POST` when:

* You want to receive real time order or shipment events.
* You want to receive the order event or shipment event content.
* You only want to receive order or shipment events of a specific type.
* You **only** need to receive the order lines that are **changed**, not all the lines of the order.
* You want to use only one single delivery per order line.
* You want to use XML instead of JSON.

{% hint style="info" %}
Pro's:

* Real time, receive the order or shipment event within a second.
* Order or shipment event content included.
* You can filter on which order or shipment events to receive, in the order & shipment webhook settings in your company settings or filter events yourself in your integration.
* You can use the single delivery per order line feature.
* You can choose to use XML instead of JSON.
* You do not have to build or configure the polling pattern.

Con's:

* You need to build or configure a webhook at your side.
* You need to publish the webhook on the internet \(webserver and firewall required\).
* You need to obtain and configure a public SSL certificate.
{% endhint %}

### Using `GET`

The `GET` endpoint is an alternative to the `POST` endpoint and can be used to receive the `orderId` or `shipmentId` of the order or shipment that has been changed.

To receive the `orderId` use the [GET Order Webhook](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-connector/specs.yaml#/order-webhook%20endpoints/webhookGet) endpoint.

When using `GET` the webhook request URL will contain the Tradecloud `orderId`, which you must use to fetch the order.

To receive the `shipmentId` use the [GET Shipment Webhook](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/shipment-webhook-connector/specs.yaml#/shipment-webhook%20endpoints/webhookGet) endpoint.

When using `GET` the webhook request URL will contain the Tradecloud `shipmentId`, which you must use to fetch the shipment.

Use `GET` when:

* Same as `POST` above, but:
* You need to receive the **complete** order with **all** the order lines, regardless they are changed or not.
* You can handle the delivery schedule yourself.

{% hint style="info" %}
Pro's:

* Real time, receive the order or shipment within a second.
* You can filter on which order or shipment events to receive, in the order & shipment webhook settings in your company profile.
* You do not have to build or configure the polling pattern.

Con's:

* You need to fetch the order or shipment.
* You cannot see what order or shipment event happened.
* You cannot use the single delivery per order line feature.
* You cannot choose XML, but must use JSON.
* You need to build or configure a webhook at your side.
* You need to publish the webhook on the internet \(web server and firewall required\).
* You need to obtain and configure a public SSL certificate.
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
Tradecloud considers the event as not successfully processed, but resending the same request is expected to result in the same error.
The request will not be retried, the DevOps team will be alerted to investigate the issue.  
Commonly used client error responses are:

* `400` - Bad Request: Your webhook found a **functional** error during the processing of the incoming request.
* `401` - Unauthorized: The supplied authentication (eg. credentials) are not valid.
* `403` - Forbidden: Tradecloud is not authorized to perform this action.
* `404` - Not Found: The requested resource, such as the related order, could not be found.

**`5xx` - Server error response**  
Tradecloud considers the event not successfully processed due to an error in the webhook. Tradecloud will indefinitely retry the request with exponential back-off. The DevOps team is alerted to monitor the issue.  
Commonly used server error responses are:

* `500` - Internal Server Error: A technical error occurred in the webhook.
* `502` - Bad Gateway: The upstream ERP system is not available.
* `503` - Service Unavailable: The webhook is currently not available.
* `504` - Gateway Timeout: There was a timeout when connecting to the upstream ERP system.

## The polling pattern

The polling pattern is an alternative to the webhook pattern and can be used to receive an order or shipment by polling the Tradecloud API.

Periodically, typically each 5 minutes, check if there are new or updated orders or shipments by using the last updated date time stamp of the last fetched order or shipment.

The polling pattern is most suitable for companies with low volume orders, and not willing to invest in a web server, firewall and SSL certificate.

{% hint style="info" %}
Pro's:

* No webhook needed: no web server, firewall or SSL certificate needed.

Con's:

* Not real time, a polling period is typically 5 mins.
* You need to build or configure a periodic polling pattern at your side.
* You cannot filter on which order or shipment events to act on, you will receive any order or shipment change, including echoed changes from your ERP system.
* You cannot see what order or shipment event happened, multiple events may have happened.
* You cannot use the single delivery per order line feature.
* You cannot choose XML, but must use JSON.
{% endhint %}

For polling usage see:

{% page-ref page="polling/README.md" %}

For handling echoed changes from your ERP system see:

{% page-ref page="polling/echo.md" %}
