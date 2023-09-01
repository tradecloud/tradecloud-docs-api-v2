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
* SAP SOAP Connector - for single SAP R/3 instances - available from Tradecloud
* [SCSN](https://smart-connected.nl) Connector - available from partner [Supply Drive](https://supplydrive.cloud/)

When choosing to build a custom API integration consider an integration/ERP partner for your ERP system.
Tradecloud sales can help you to find a partner.

## Middleware

Now you have choosen to build a custom API integration, lets look at the integration architecture: 

Do you have multiple business systems, like EPR, WMS and PLM, that have to integrate with Tradecloud?
Do you already or plan to integrate with the outside world like webshop and logistics partners?
In these cases it is recommended to use, or you are probably already using, message-oriented middleware.

Some Tradecloud customers use middleware like [ConnectPlaza](https://www.connectplaza.com/#1), [Mulesoft](https://www.mulesoft.com/), [Orbis](https://www.orbis-software.nl/) and [WebMethods](https://www.softwareag.com/en_corporate/platform/integration-apis/webmethods-integration.html).

Some Tradecloud customers build on Microsoft [Azure Integration Services](https://azure.microsoft.com/en-us/products/category/integration) mostly using [API Management](https://azure.microsoft.com/en-us/products/api-management), [Logic Apps](https://learn.microsoft.com/en-us/azure/logic-apps/logic-apps-overview) and [Service Bus](https://azure.microsoft.com/en-us/products/service-bus). 

If you have only an ERP system and are planning to only connect to Tradecloud, you may consider a 1-1 connection, without message-oriented middleware, as it will be quicker and cheaper at this moment.

## Scope

Now you have choosen to buy or build message-oriented middleware or make a 1-1 connection, lets look at the scope:

The Tradecloud modules (order/shipment/forecast) are agreed in the Tradecloud contract, but within these modules there are several message flows possible dependent on the buyer or supplier role:

### As a buyer, what is your scope?

What message flows are you going to build?

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

### As a supplier, what is your scope?

What message flows are you going to build?

* [orders](order/supplier/receive/README.md)
* [order documents](order/supplier/receive/download-document.md)
* [order responses](order/supplier/send-order-response/README.md)
* [order response documents](order/supplier/send-order-response/attach-document.md)
* [despatch advices](shipment/send-despatch-advice.md)


