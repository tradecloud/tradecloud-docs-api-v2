---
description: >-
  Choose between JSON and XML in the `api-connector` and `order-webhook-connector`
---

# JSON versus XML

The Tradecloud API by default supports a proprietary JSON format, but for some API endpoints a proprietary XML format is supported.

## JSON

The Tradecloud API by default supports a proprietary Tradecloud [JSON format](requests.md#json-body). This is the default for all endpoints.

## XML

The Tradecloud API supports a proprietary Tradecloud [XML format](requests.md#xml-body), called `tXML`, which is a 1-on-1 translation of the proprietary JSON format:

* [Send order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderByBuyerRoute) and
* [Send single delivery order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendSingleDeliveryOrderByBuyerRoute) endpoints support `tXML`.

You can see an XML example by selecting "application/xml" in the "Parameter content type" dropdown, under the "Example Value" in above API specifications:

![Select order API XML content type](../.gitbook/assets/select-order-api-xml-content-type.png)

Also the [POST Order Webhook](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-connector/specs.yaml#/order-webhook%20endpoints/webhookPost) endpoint supports `tXML`.

You can see an XML example by selecting "application/xml" in the "Parameter content type" dropdown, under the "Example Value" in above API specification:

![Select order webhook XML content type](../.gitbook/assets/select-order-webhook-xml-content-type.png)

Let [support](../support.md) know if you need `tXML` support for additional API endpoints.
