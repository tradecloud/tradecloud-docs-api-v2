---
description: >-
  Choose between JSON and XML in the `api-connector` and `order-webhook-connector`
---

# JSON versus XML

The Tradecloud API supports default a proprietary JSON format, but for some API endpoints a proprietary XML format is supported.

## JSON

The Tradecloud API supports default a proprietary Tradecloud [JSON format](requests.md#json-body), called `TSON`.

All `api-connector`, `order-search`, `shipment-search`, `order-webhook-connector` and `shipment-webhook-connector` API endpoints support `TSON`.

## XML

The Tradecloud API supports a proprietary Tradecloud [XML format](requests.md#xml-body), called `tXML`, which is a 1-on-1 translation of the `TSON` format:

Only the [Send order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderByBuyerRoute) and [Send simple order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendSimpleOrderByBuyerRoute) endpoints support `tXML` at this moment.

You can see an XML example by selecting "application/xml" in the "Parameter content type" dropdown, under the "Example Value" in above API specifications.

We are currently adding `tXML` support to the [POST Order Webhook](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-client/specs.yaml#/order-webhook%20endpoints/webhookPost) endpoint.

 Let [support](../support.md) know if you need `tXML` support for additional API endpoints.
