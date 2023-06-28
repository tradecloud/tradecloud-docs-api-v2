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

When an order or shipment has been changed at Tradecloud, we will trigger your webhook, which optionally contains the order or shipment event.

The webhook is most suitable for companies with real time, high volume orders and having a web server or integration platform, firewall and SSL certificate available.

You can either use `POST` or alternatively `GET`.

See [Webhook Connector](https://tradecloud.gitbook.io/connectors/webhook-connector) for setting up and using the webhook.

### Using `POST`

When using `POST` the **order** webhook request body contains:

* `eventName`: The [eventName](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-client/specs.yaml#/order-webhook%20endpoints/webhookPost) \(click "Model"\) summarizes what has happened.
* `orderEvent`: The actual order event, see [OrderEvent](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-client/specs.yaml#/order-webhook%20endpoints/webhookPost) \(click "Model" and "OrderEvent"\)
* `orderDocumentsEvent`: Or the actual order documents event, see [OrderDocumentEvent](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-client/specs.yaml#/order-webhook%20endpoints/webhookPost) \(click "Model" and "OrderDocumentsEvent"\).

When using `POST` the **shipment** webhook request body contains:

* `eventName`: The [eventName](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/shipment-webhook-connector/specs.yaml#/shipment-webhook%20endpoints/webhookPost) \(click "Model") summarizes what has happened.
* `shipmentEvent`: The actual shipment, see [Shipment](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/shipment-webhook-connector/specs.yaml#/shipment-webhook%20endpoints/webhookPost) \(click "Model" and "Shipment"\).

Use `POST` when:

* You want to receive real time order or shipment events.
* You want to receive the order event or shipment event content.
* You only want to receive order or shipment events of a specific type.
* You **only** need to receive the order lines that are **changed**, not all the lines of the order.

{% hint style="info" %}
Pro's:

* Real time, receive the order or shipment event within a second.
* Order or shipment event content included.
* You can filter on which order or shipment events to receive, in the order & shipment webhook settings in your company profile or filter events yourself in your integration.
* You do not have to build or configure the polling pattern.

Con's:

* You need to build or configure a webhook at your side.
* You need to publish the webhook on the internet \(webserver and firewall required\).
* You need to obtain and configure a public SSL certificate.
{% endhint %}

### Using `GET`

When using `GET` the webhook request URL will contain the Tradecloud `orderId`, which you must use to fetch the order.

Use `GET` when:

* Same as `POST` above, but:
* You need to receive the **complete** order with **all** the order lines, regardless they are changed or not.

{% hint style="info" %}
Pro's:

* Real time, receive the order or shipment within a second.
* You can filter on which order or shipment events to receive, in the order & shipment webhook settings in your company profile.
* You do not have to build or configure the polling pattern.

Con's:

* You need to fetch the order or shipment.
* You cannot see what order or shipment event happened.
* You need to build or configure a webhook at your side.
* You need to publish the webhook on the internet \(web server and firewall required\).
* You need to obtain and configure a public SSL certificate.
{% endhint %}

## The polling pattern

Check if there are new or updated orders or shipments every polling period, typically 5 minutes, by using the last updated date time stamp of the last fetched order or shipment.

The polling pattern is most suitable for companies with low volume orders, and not willing to invest in a web server, firewall and SSL certificate.

{% hint style="info" %}
Pro's:

* No webhook needed: no web server, firewall or SSL certificate needed.

Con's:

* Not real time, a polling period is typically 5 mins.
* You need to build or configure a periodic polling pattern at your side.
* You cannot filter on which order or shipment events to act on, you will receive any order or shipment change.
* You cannot see what order or shipment event happened, multiple events may have happened.
{% endhint %}

### Polling usage

#### Step 1. Fetch updated orders or shipments periodically

Fetch every polling period, typically 5 minutes, all orders or shipments which are new or changed since last date time.

* Use the latest `lastUpdatedAt` from previous poll request in the `lastUpdatedSince` filter.
* Sorting is set automatically to `lastUpdatedAt` order `asc` \(the latest `lastUpdatedAt` will be in the last order or shipment in the response body\)
* Set `limit` to the maximum of `100` orders or shipments.
* Optionally use `offset` for paging, but if you receive more than `100` orders or shipments, it is easier to reduce the polling period, so you receive less orders or shipments per request.

{% hint style="info" %}
[Search orders OpenAPI Specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-search/specs.yaml#/order-search/searchRoute)
{% endhint %}

{% hint style="info" %}
[Search shipments OpenAPI Specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/shipment/specs.yaml#/shipment/searchShipmentsRoute)
{% endhint %}

#### Step 2. Process the orders in the search response body

See the [Search orders OpenAPI Specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-search/specs.yaml#/order-search/searchRoute).

* Use the `lastUpdatedAt` on order line level to filter the lines that have been changed.
* Use the `status` field to filter on order process and logistics status.

See the [Search shipments OpenAPI Specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/shipment/specs.yaml#/shipment/searchShipmentsRoute).

#### Step 3. Store the `lastUpdatedAt` for the next polling request

Store the **latest** \(in the last order or shipment in the response body\) `lastUpdatedAt` to be used as `lastUpdatedSince` in the next polling request.

* `lastUpdatedAt` has type `String` with format `YYYY-MM-DDThh:mm:ss.SSSZ`, but to keep it simple just store it as a `String`.
* The latest `lastUpdatedAt` should be stored **persistent**. When your integration is restarted or crashes, `lastUpdatedAt` should still be available.
* If there is no order in the order or shipment response body, use the same `lastUpdatedSince` in the next polling request.
* The very first time, use a date in the past, from the point you want to receive existing order responses.
