---
description: Tradecloud API environments available
---

# Environments

Tradecloud has two environments available for customers:

* [Production live environment](environments.md#production-environment)
* [Acceptance test environment](environments.md#acceptance-test-environment)

## Production environment

There is one production environment a.k.a. LIVE environment. The latest features will be made available by the Tradecloud continuous delivery process.

The production environment is subject to a platform Service Level Agreement (SLA) guaranteeing 99.5% uptime, measured on an annual basis. This applies on Dutch working days, during office hours from 09:00 to 18:00 CE(S)T.

#### Documentation

You can use the endpoints below to integrate with the production environment. Use [https://api.tradecloud1.com/v2/api-connector/](https://swagger-ui.tradecloud1.com/?url=https://api.tradecloud1.com/v2/api-connector/specs.yaml) to send an order \(response\).

You can [use the Swagger UI](tools/swagger-ui.md) to explore and test the Tradecloud API:

| Service | Docs |
| :--- | :--- |
| [https://api.tradecloud1.com/v2/api-connector](https://api.tradecloud1.com/v2/api-connector) | [YAML](https://api.tradecloud1.com/v2/api-connector/specs.yaml) / [Swagger UI](https://swagger-ui.tradecloud1.com/?url=https://api.tradecloud1.com/v2/api-connector/specs.yaml) |
| [https://api.tradecloud1.com/v2/authentication](https://api.tradecloud1.com/v2/authentication) | [YAML](https://api.tradecloud1.com/v2/authentication/specs.yaml) / [Swagger UI](https://swagger-ui.tradecloud1.com/?url=https://api.tradecloud1.com/v2/authentication/specs.yaml) |
| [https://api.tradecloud1.com/v2/object-storage](https://api.tradecloud1.com/v2/object-storage) | [YAML](https://api.tradecloud1.com/v2/object-storage/specs.yaml) / [Swagger UI](https://swagger-ui.tradecloud1.com/?url=https://api.tradecloud1.com/v2/object-storage/specs.yaml) |
| [https://api.tradecloud1.com/v2/order](https://api.tradecloud1.com/v2/order) | [YAML](https://api.tradecloud1.com/v2/order/specs.yaml) / [Swagger UI](https://swagger-ui.tradecloud1.com/?url=https://api.tradecloud1.com/v2/order/specs.yaml) |
| [https://api.tradecloud1.com/v2/order-search](https://api.tradecloud1.com/v2/order-search) | [YAML](https://api.tradecloud1.com/v2/order-search/specs.yaml) / [Swagger UI](https://swagger-ui.tradecloud1.com/?url=https://api.tradecloud1.com/v2/order-search/specs.yaml) |
| [https://api.tradecloud1.com/v2/order-webhook-connector](https://api.tradecloud1.com/v2/order-webhook-connector) | [YAML](https://api.tradecloud1.com/v2/order-webhook-connector/specs.yaml) / [Swagger UI](https://swagger-ui.tradecloud1.com/?url=https://api.tradecloud1.com/v2/order-webhook-connector/specs.yaml) |
| [https://api.tradecloud1.com/v2/sci-connector](https://api.tradecloud1.com/v2/sci-connector) | [YAML](https://api.tradecloud1.com/v2/sci-connector/specs.yaml) / [Swagger UI](https://swagger-ui.tradecloud1.com/?url=https://api.tradecloud1.com/v2/sci-connector/specs.yaml) |

### Planned production maintenance

Maintenance can be planned on working days from 19:00 to 23:00 UTC \(20:00 to 00:00 CET and 21:00 to 01:00 CEST during daylight saving time\) or in weekends and will be announced at least 1 working day ahead on the [Tradecloud status page](http://status.tradecloud1.com).

Please subscribe to the status updates using the blue button on the top right of the [Tradecloud status page](http://status.tradecloud1.com).

## Acceptance-testing environment

There is one [acceptance-testing environment](https://api.accp.tradecloud1.com).

Buyers and suppliers can test new features and develop and test their Tradecloud API integration. The latest features will be made available by the Tradecloud continuous delivery process.

The acceptance-testing environment is not covered by a platform availability SLA.

#### Documentation

You can use the endpoints below to integrate with the acceptance environment. Use [https://api.accp.tradecloud1.com/v2/api-connector/](https://swagger-ui.accp.tradecloud1.com/?url=https://api.tradecloud1.com/v2/api-connector/specs.yaml) to send an order \(response\).

You can [use the Swagger UI](tools/swagger-ui.md) to explore and test the Tradecloud API:

| Service | Docs |
| :--- | :--- |
| [https://api.accp.tradecloud1.com/v2/api-connector](https://api.accp.tradecloud1.com/v2/api-connector) | [YAML](https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml) / [Swagger UI](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml) |
| [https://api.accp.tradecloud1.com/v2/authentication](https://api.accp.tradecloud1.com/v2/authentication) | [YAML](https://api.accp.tradecloud1.com/v2/authentication/specs.yaml) / [Swagger UI](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/authentication/specs.yaml) |
| [https://api.accp.tradecloud1.com/v2/object-storage](https://api.accp.tradecloud1.com/v2/object-storage) | [YAML](https://api.accp.tradecloud1.com/v2/object-storage/specs.yaml) / [Swagger UI](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/object-storage/specs.yaml) |
| [https://api.accp.tradecloud1.com/v2/order](https://api.accp.tradecloud1.com/v2/order) | [YAML](https://api.accp.tradecloud1.com/v2/order/specs.yaml) / [Swagger UI](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order/specs.yaml) |
| [https://api.accp.tradecloud1.com/v2/order-search](https://api.accp.tradecloud1.com/v2/order-search) | [YAML](https://api.accp.tradecloud1.com/v2/order-search/specs.yaml) / [Swagger UI](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-search/specs.yaml) |
| [https://api.accp.tradecloud1.com/v2/order-webhook-connector](https://api.accp.tradecloud1.com/v2/order-webhook-connector) | [YAML](https://api.accp.tradecloud1.com/v2/order-webhook-connector/specs.yaml) / [Swagger UI](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-connector/specs.yaml) |
| [https://api.accp.tradecloud1.com/v2/sci-connector](https://api.accp.tradecloud1.com/v2/sci-connector) | [YAML](https://api.accp.tradecloud1.com/v2/sci-connector/specs.yaml) / [Swagger UI](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/sci-connector/specs.yaml) |

## Source IP addresses

The Tradecloud source IP addresses usable for whitelisting in your firewall, are:

Acceptance environment:

* 35.204.36.162

Production environment:

* 35.204.224.107
* 34.90.20.233

Any changes will be announced at least 5 working days ahead on the [Tradecloud status page](http://status.tradecloud1.com).

If you use white listing you must subscribe to the status updates using the blue button on the top right of the [Tradecloud status page](http://status.tradecloud1.com).
