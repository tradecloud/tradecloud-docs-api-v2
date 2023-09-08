---
description: >-
  Choose between JSON and XML in the `api-connector` and `order-webhook-connector`
---

# JSON versus XML

The Tradecloud API supports default a proprietary JSON format, but for some API endpoints a proprietary XML format is supported.

## JSON

The Tradecloud API supports default a proprietary Tradecloud JSON format, called `TSON`.

See also: [JSON body](requests.md#json-body).

All `api-connector`, `order-search`, `shipment-search`, `order-webhook-connector` and `shipment-webhook-connector` API endpoints support `TSON`.


## XML

The Tradecloud API supports a proprietary Tradecloud XML format, called `tXML`, which is a 1-on-1 translation of the `TSON` format:

See also: [XML body](requests.md#xml-body)

Only the `api-connector` [Send order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderByBuyerRoute) and [Send simple order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendSimpleOrderByBuyerRoute) endpoints support `tXML` at this moment.

We are currently addting `tXML` to the `order-webhook-connector` POST endpoint.

 Let [support](support.md) know if you need `tXML` support for additional API enpoints.
