---
description: >-
  How to use the polling pattern.
---

# Polling usage

The polling API is an alternative for the webhook API. The pro's and cons are explained in:

{% page-ref page="api/webhook-vs-polling.md" %}

This page explains the polling pattern usage, which consists of 3 steps:

1. Every polling period, fetch order or shipments which are changed after last time.
2. Process the fetched new or updated orders or shipments.
3. Persist the `lastUpdatedAt` for the next polling request

## Step 1. Fetch updated orders or shipments periodically

Fetch every polling period, typically 5 minutes, all orders or shipments which are new or changed after last time.

* Use the latest `lastUpdatedAt` from previous poll request in the `lastUpdatedAfter` filter.
* Sorting is set automatically to `lastUpdatedAt` order `asc` \(the latest `lastUpdatedAt` will be in the last order or shipment in the response body\)
* Set `limit` to the maximum of `100` orders or shipments.
* Optionally use `offset` for paging, but if you receive more than `100` orders or shipments, it is easier to reduce the polling period, so you receive less orders or shipments per request.

Use the [Search orders](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-search/specs.yaml#/order-search/searchRoute) endpoint for polling orders.

Use the [Search shipments](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/shipment/specs.yaml#/shipment/searchShipmentsRoute) endpoint for polling shipments.

## Step 2. Process the orders or shipments in the search response body

Process the fetched new or updated orders or shipments.

{% hint style="warning" %}
You may receive any order or shipment change, including echoed changes from your ERP system. How to handle your own open request is explained in [Polling requests](requests.md):
{% endhint %}

See the [Search orders](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-search/specs.yaml#/order-search/searchRoute) endpoint:

* Use the `lines.lastUpdatedAt` field to filter the order lines that have been changed.
* Use the `status` field to filter on order process and logistics status.

See the [Search shipments](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/shipment/specs.yaml#/shipment/searchShipmentsRoute) endpoint:

* Use the `lines.meta.lastUpdatedAt` to filter the shipment lines that have been changed.
* Use the `status` field to filter on shipment process and logistics status.

## Step 3. Persist the `lastUpdatedAt` for the next polling request

Persist the **latest** \(in the last order or shipment in the response body\) `lastUpdatedAt` to be used as `lastUpdatedAfter` in the next polling request.

* `lastUpdatedAt` has type `String` with format `YYYY-MM-DDThh:mm:ss.SSSZ`, but to keep it simple just store it as a `String`.
* The latest `lastUpdatedAt` should be stored **persistent**. When your integration is restarted or crashes, `lastUpdatedAt` should still be available.
* If there is no order in the order or shipment response body, use the same `lastUpdatedAfter` in the next polling request.
* The very first time, use a date in the past, from the point you want to receive existing order responses.
