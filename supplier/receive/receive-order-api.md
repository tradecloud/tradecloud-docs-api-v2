---
description: Choose between the webhook API or polling API to receive an order
---

# Choose a receive API

To receive an order you can use either:

* the [Webhook Connector](https://tradecloud.gitbook.io/connectors/webhook-connector) using `POST` or `PUT`
* the [Webhook Connector](https://tradecloud.gitbook.io/connectors/webhook-connector) using `GET`
* the polling pattern

## The Webhook connector

The webhook is nost suitable for companies with high volume orders; say more than 1 per minute average during office hours.

When an order is issued or has been changed at Tradecloud, we will trigger your webhook.

You can either use `POST` or `PUT` or alternatively `GET`

See [Webhook Connector](https://tradecloud.gitbook.io/connectors/webhook-connector) for setting up and using the webhook.

### Using `POST` or `PUT`

Use `POST` or `PUT` when:

* You want to receive real time orders
* You want to receive the order event content
* You only want to receive selected order events, like only issued (new) orders.
* You **only** need to receive the order lines that are **changed**, not the complete order.

{% hint style="info" %}
Pro's:

* Real time, receive the order event within seconds.
* Order event content included.
* You can filter on which order events to receive (in the company integration settings or in your integration).
* You do not have to build or configure the polling pattern.

Con's:

* You need to build or configure a webhook at your side.
* You need to publish the webhook on the internet (webserver and firewall required).
* You need to obtain and configure a public SSL certificate.

{% endhint %}

In case of an **POST or PUT webhook** the body will contain:

* `eventName:`The event name summarizes what has happened.
* `orderEvent`: The actual order event, see [Receive order](README.md)
* `orderDocumentsEvent`: \(to be documented\)

### Using `GET`

Use `GET` when:

* Same as `POST` and `PUT` above, but:

* You need to receive the **complete** order with **all** the order lines, regardless they are changed or not.

{% hint style="info" %}
Pro's:

* Real time, receive the order event trigger within seconds.
* You can filter on which order events to receive (in the company integration settings only).
* You do not have to build or configure the polling pattern.

Con's:

* You need to fetch the order.
* Basic authentication is not yet supported for the GET `/order/:orderId` API. Send a support request if you need it.
* You cannot see what order event happened
* You need to build or configure a webhook at your side.
* You need to publish the webhook on the internet (webserver and firewall required).
* You need to obtain and configure a public SSL certificate.

{% endhint %}

## The polling pattern

The polling pattern is most suitable for companies with low volume orders; say less than 1 per minute average during office hours.

{% hint style="info" %}
Pro's:

* No webhook needed: no webserver, firewall or SSL certificate needed.

Con's:

* Not real time, a polling period is typically 5 mins. which is good enough for low volume.
* You need to build or configure a periodic polling pattern at your side.
* You cannot filter on which order events to receive, you will receive any order line change.
* You cannot see what order event happened.

{% endhint %}

### Polling usage

#### Step 1. Fetch updated orders periodically

Fetch every polling period, typically 5 minutes, all orders which are new or changed since last date time.

* Use the latest `lastUpdatedAt` from previous poll request in the `lastUpdatedSince` filter.
* Sorting is set automatically to `lastUpdatedAt` order `asc` (latest `lastUpdatedAt` will be in the last order in the response body)
* Set `limit` to the maximum of `100` orders.
* Optionally use `offset` for paging, but if you receive `100` or more orders, it is easier to reduce the polling period.

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
{
  "filters": {
    "lastUpdatedSince": "YYYY-MM-DDThh:mm:ss.SSSZ"
  },
  "offset": 0,
  "limit": 100
}
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
[Search orders OpenAPI Specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-search/specs.yaml#/order-search/searchRoute)
{% endhint %}

#### Step 2. Process the orders in the search response body

See the [Search orders OpenAPI Specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-search/specs.yaml#/order-search/searchRoute) and [Receive order](README.md) for order fields descriptions.

* Use the `lastUpdatedAt` on order line level to filter on the line has been changed.
* Use the `status` field to filter on process and logistics status.

#### Step 4. Store the lastUpdatedAt for the next polling request

Store the **latest** (in the last order in the response body) `lastUpdatedAt` to be used as `lastUpdatedSince` in the next polling request.

The latest `lastUpdatedAt` should be stored **persistent**, eg. when your integration is restarted,  `lastUpdatedAt` should still be available.

If there is no order in the order body, use the same `lastUpdatedSince` in the next polling request.
