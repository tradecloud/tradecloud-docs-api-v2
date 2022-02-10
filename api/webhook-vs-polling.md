---
description: >-
  Choose between the webhook API or polling API to receive an order or order
  response
---

# Webhook versus polling

To receive an order or order response you can use either:

* The [Webhook Connector](https://tradecloud.gitbook.io/connectors/webhook-connector) using `POST` or `PUT`.
* The [Webhook Connector](https://tradecloud.gitbook.io/connectors/webhook-connector) using `GET`.
* The polling pattern.

## The Webhook Connector

When an order has been changed at Tradecloud, we will trigger your webhook, which optionally contains the order event.

The webhook is most suitable for companies with real time, high volume orders and having a web server or integration platform, firewall and SSL certificate available.

You can either use `POST` or `PUT` or alternatively `GET`.

See [Webhook Connector](https://tradecloud.gitbook.io/connectors/webhook-connector) for setting up and using the webhook.

### Using `POST` or `PUT`

When using `POST` or `PUT` the webhook request body will contain:

* `eventName:`The [eventName](https://swagger-ui.s.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-client/specs.yaml#/order-webhook%20endpoints/webhookPost) \(click "Model"\) summarizes what has happened.
* `orderEvent`: The actual order event, see [OrderEvent](https://swagger-ui.s.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-client/specs.yaml#/order-webhook%20endpoints/webhookPost) \(click "Model" and "OrderEvent"\) and [Receive order response](./).
* `orderDocumentsEvent`: Or the actual order documents event, see see [OrderDocumentEvent](https://swagger-ui.s.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-client/specs.yaml#/order-webhook%20endpoints/webhookPost) \(click "Model" and "OrderDocumentsEvent"\).

Use `POST` or `PUT` when:

* You want to receive real time order events.
* You want to receive the order event content.
* You only want to receive selected order events.
* You **only** need to receive the order lines that are **changed**, not all the lines of the order.

{% hint style="info" %}
Pro's:

* Real time, receive the order event within a second.
* Order event content included.
* You can filter on which order events to receive \(in the company integration settings or filter in your integration\).
* You do not have to build or configure the polling pattern.

Con's:

* You need to build or configure a webhook at your side.
* You need to publish the webhook on the internet \(webserver and firewall required\).
* You need to obtain and configure a public SSL certificate.
{% endhint %}

### Using `GET`

When using `GET` the webhook request URL will contain the Tradecloud `orderId`, which you must use to fetch the order.

Use `GET` when:

* Same as `POST` and `PUT` above, but:
* You need to receive the **complete** order with **all** the order lines, regardless they are changed or not.

{% hint style="info" %}
Pro's:

* Semi real time, receive the order within seconds.
* You can filter on which order events to receive \(in the company integration settings only\).
* You do not have to build or configure the polling pattern.

Con's:

* You need to fetch the order.
* Basic authentication is not yet supported for the GET `/order/:orderId` API. Send a support request if you need it.
* You cannot see what order event happened.
* You need to build or configure a webhook at your side.
* You need to publish the webhook on the internet \(web server and firewall required\).
* You need to obtain and configure a public SSL certificate.
{% endhint %}

## The polling pattern

Check if there are new or updated orders every polling period, typically 5 minutes, by using the last updated date time stamp of the last fetched order.

The polling pattern is most suitable for companies with low volume order responses and not willing to invest in a web server, firewall and SSL certificate.

{% hint style="info" %}
Pro's:

* No webhook needed: no web server, firewall or SSL certificate needed.

Con's:

* Not real time, a polling period is typically 5 mins.
* You need to build or configure a periodic polling pattern at your side.
* You cannot filter on which order events to receive, you will receive any order line change.
* You cannot see what order event happened.
{% endhint %}

### Polling usage

#### Step 1. Fetch updated orders periodically

Fetch every polling period, typically 5 minutes, all orders which are new or changed since last date time.

* Use the latest `lastUpdatedAt` from previous poll request in the `lastUpdatedSince` filter.
* Sorting is set automatically to `lastUpdatedAt` order `asc` \(latest `lastUpdatedAt` will be in the last order in the response body\)
* Set `limit` to the maximum of `100` orders.
* Optionally use `offset` for paging, but if you receive more than `100` orders, it is easier to reduce the polling period, so you receive less orders per request.

{% api-method method="post" host="https://api.accp.tradecloud1.com/v2" path="/order-search/search" %}
{% api-method-summary %}
Search orders
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Basic Authentication or Bearer Access-Token
{% endapi-method-parameter %}

{% api-method-parameter name="Content-Type" type="string" required=true %}
application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="body" type="object" required=true %}
{ "filters": { "lastUpdatedSince": "YYYY-MM-DDThh:mm:ss.SSSZ" }, "offset": 0, "limit": 100 }
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
[Search orders OpenAPI Specification](https://swagger-ui.s.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-search/specs.yaml#/order-search/searchRoute)
{% endhint %}

#### Step 2. Process the orders in the search response body

See the [Search orders OpenAPI Specification](https://swagger-ui.s.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-search/specs.yaml#/order-search/searchRoute) and [Receive order response](./) for order fields descriptions.

* Use the `lastUpdatedAt` on order line level to filter on the line has been changed.
* Use the `status` field to filter on process and logistics status.

#### Step 4. Store the `lastUpdatedAt` for the next polling request

Store the **latest** \(in the last order in the response body\) `lastUpdatedAt` to be used as `lastUpdatedSince` in the next polling request.

* `lastUpdatedAt` has type `String` with format `YYYY-MM-DDThh:mm:ss.SSSZ`, but to keep it simple just store it as a `String`.
* The latest `lastUpdatedAt` should be stored **persistent**. When your integration is restarted or crashes, `lastUpdatedAt` should still be available.
* If there is no order in the order response body, use the same `lastUpdatedSince` in the next polling request.
* The very first time, use a date in the past, from the point you want to receive existing order responses.

