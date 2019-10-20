---
description: How to use order API
---

# Order

## Send order by buyer

To send new order you must be authenticated in the system and have Buyer role:

```
// Request method and URI
POST https://api.accp.tradecloud1.com/v2/order-integration
// Request headers:
Authorization: Bearer <token>
// Request body: { ... }
```
[Payload example](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-integration/specs.yaml#/order-integration/sendOrderByBuyerRoute)

You will get `200 OK` if request was successful or `500 	
Internal server error` otherwise. 

{% hint style="info" %}
[Order integration OpenAPI specification](https://api.accp.tradecloud1.com/v2/order-integration/specs.yaml) in yaml format
{% endhint %}

## Health check of order-integration service

To check service health:
```
// Request method and URI
GET https://api.accp.tradecloud1.com/v2/order-integration/health
```
You will get `200 OK` if service is healthy or `503 Service Unavailable` otherwise. 