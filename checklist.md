---
description: This checklist page contains important info and decisions to make before starting API client development.
---

# Checklist

{% hint style="danger" %}
This checklist contains important info and decisions to consider before start building an API integration with Tradecloud.
{% endhint %}

## Connector or API

Are you going to use a Tradecloud connector or the API?

Available Tradecloud connectors:

* AFAS Connector - available from partner [Improvit](https://www.improvit.nl/)
* [Copernicus Niklas](https://www.copernicus.nl/en/products/niklas-integration-platform/) with Tradecloud templates
* CSV Connector - available from partner [Supply Drive](https://supplydrive.cloud/)
* Edifact Connector - available from partner [Supply Drive](https://supplydrive.cloud/)
* Exact Globe Connector - for Exact Globe ERP Systems by parter [AB Software](https://www.wijzijnab.nl/)
* Infor LN Connector - available from partner [Xibis](https://xibis.nl/)
* Isah API Connector - available from partner [Tambien](https://tambien.nl)
* Isah SCI Connector - for Isah ERP systems by partner [Isah](https://isah.com)
* Microsoft Dynamics 365 Business Central [Connectivity Studio](https://www.to-increase.com/business-integration/microsoft-dynamics-bc/connectivity-studio) - available from partner To-Increase 
* Microsoft Dynamics 365 Finance & Operations [Connectivity Studio](https://www.to-increase.com/business-integration/connectivity-studio) - available from partner To-Increase
* SAP SOAP Connector - for single SAP ERP instances - available from Tradecloud
* [SCSN](https://smart-connected.nl) Connector - available from partner [Supply Drive](https://supplydrive.cloud/)

When choosing to build a custom API integration instead, consider an integration/ERP partner for your ERP system.
Tradecloud sales can help you to find a partner.

## Middleware

Now you have choosen to build a custom API integration, lets look at the integration architecture: 

Do you have multiple business systems, like EPR, WMS and PLM, that have to integrate with Tradecloud?
Do you already or plan to integrate with the outside world like webshops and logistics partners?
In these cases it is recommended to use, or you are probably already using, message-oriented middleware.

Some Tradecloud customers buy middleware like [ConnectPlaza](https://www.connectplaza.com/#1), [Mulesoft](https://www.mulesoft.com/), [Orbis](https://www.orbis-software.nl/) and [WebMethods](https://www.softwareag.com/en_corporate/platform/integration-apis/webmethods-integration.html). Be aware you still have to build message flows & data transformations.

Some Tradecloud customers build on Microsoft [Azure Integration Services](https://azure.microsoft.com/en-us/products/category/integration) mostly using [API Management](https://azure.microsoft.com/en-us/products/api-management), [Logic Apps](https://learn.microsoft.com/en-us/azure/logic-apps/logic-apps-overview) and [Service Bus](https://azure.microsoft.com/en-us/products/service-bus). 
 
 If you have only an ERP system and are planning to only connect to Tradecloud, you may consider to build a 1-1 connection, 
 without message-oriented middleware, as it may be quicker and cheaper. 

Some Tradecloud customers build 1-1 connections on the tools or framework the ERP system provides itself. Be aware that these tools may be limited, like missing a HTTP client or server, or missing security or data transformation features.

## Scope

Now you have choosen to buy or build message-oriented middleware or make a 1-1 connection, lets look at the scope:

The Tradecloud modules (order/shipment/forecast) are agreed in the Tradecloud contract, but within these modules there are several message flows possible dependent on the buyer or supplier role:

### As a buyer

As a buyer, what message flows are you going to build?

* [orders](order/buyer/issue/README.md)
* [order updates](order/buyer/update.md)
* [order documents](order/buyer/issue/attach-document.md)
* [order responses](order/buyer/receive/README.md)
* [order response documents](order/buyer/receive/download-document.md)
* [goods receipt advices](order/buyer/receive-goods.md)
* [complete an order](order/buyer/complete.md)
* [cancel an order](order/buyer/cancel.md)
* [shipments](shipment/buyer/receive.md)
* [shipment documents](shipment/buyer/download-documents.md)
* [forecasts](forecast/issue.md)

### As a supplier

As a supplier, what message flows are you going to build?

* [orders](order/supplier/receive/README.md)
* [order documents](order/supplier/receive/download-document.md)
* [order responses](order/supplier/send-order-response/README.md)
* [order response documents](order/supplier/send-order-response/attach-document.md)
* [despatch advices](shipment/send-despatch-advice.md)

## Native or simple delivery schedule

Now you know your scope, which probably includes orders and order responses, the next question is:

Does your ERP system natelivy support a delivery schedule within an order line?
A delivery schedule consists of one or more deliveries (date & quantity) for the same item within one order line.

It is no problem when your ERP system does not support a delivery schedule natively, but you have to be aware which fields to use:

{% page-ref page="order/buyer/issue/delivery-schedule.md" %}

The simple delivery schedule feature is only available for buyers at this moment.

## All or touched order lines

Does your ERP expect only new and updated or always all lines in an order, order response or shipment message?

### Order/response message

Tradecloud sends only touched lines in an order/response message.

If you need all order/response lines, you may fetch the complete order, see:

{% page-ref page="api/webhook-vs-polling.md#using-get" %}

### Shipment message

Tradecloud sends always all lines in a shipment message.

If you only need only touched shipment lines, you may filter out lines based on the 'lastUpdatedAt' field, see:

{% page-ref page="shipment/buyer/receive/README.md#shipment-line-meta-information }
