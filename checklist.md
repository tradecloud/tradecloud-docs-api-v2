---
description: This checklist page contains important info and decisions to make before starting API client development.
---

# Checklist

{% hint style="danger" %}
This checklist contains important info and decisions to consider before start building an API integration with Tradecloud.
{% endhint %}

## Connector or API

Are you going to use a Tradecloud connector or the API?

Available Tradecloud connectors are:

* AFAS Connector - available from partner [Improvit](https://www.improvit.nl/)
* [Copernicus Niklas integration platform](https://www.copernicus.nl/en/products/niklas-integration-platform/) with Tradecloud templates
* CSV Connector - available from partner [Supply Drive](https://supplydrive.cloud/)
* Edifact Connector - available from partner [Supply Drive](https://supplydrive.cloud/)
* Exact Globe Connector - available from partner [AB Software](https://www.wijzijnab.nl/)
* Infor LN Connector - available from partner [Xibis](https://xibis.nl/)
* Isah API Connector - available from partner [Tambien](https://tambien.nl)
* Isah SCI Connector - available from partner [Isah](https://isah.com)
* Microsoft Dynamics 365 Business Central [Connectivity Studio](https://www.to-increase.com/business-integration/microsoft-dynamics-bc/connectivity-studio) - available from partner To-Increase 
* Microsoft Dynamics 365 Finance & Operations [Connectivity Studio](https://www.to-increase.com/business-integration/connectivity-studio) - available from partner To-Increase
* SAP SOAP Connector - for single SAP ERP instances - available from Tradecloud
* [SCSN](https://smart-connected.nl) Connector - available from partner [Supply Drive](https://supplydrive.cloud/)

When choosing to build a custom API integration yourself instead, consider an integration/ERP partner for your ERP system.
Tradecloud sales can help you to find a partner.

## Middleware or 1-1?

Now you have choosen to build a custom API integration, lets look at the integration architecture: 

Do you have multiple business systems, like EPR, WMS and PLM, that have to integrate with Tradecloud?
Do you already or plan to integrate with the outside world like webshops and logistics partners?
In these cases it is recommended to use message-oriented middleware.

Some Tradecloud customers buy middleware like [ConnectPlaza](https://www.connectplaza.com/#1), [Mulesoft](https://www.mulesoft.com/), [Orbis](https://www.orbis-software.nl/) and [WebMethods](https://www.softwareag.com/en_corporate/platform/integration-apis/webmethods-integration.html). Be aware you still have to build message flows & data transformations.

Some Tradecloud customers build on Microsoft [Azure Integration Services](https://azure.microsoft.com/en-us/products/category/integration) mostly using [API Management](https://azure.microsoft.com/en-us/products/api-management), [Logic Apps](https://learn.microsoft.com/en-us/azure/logic-apps/logic-apps-overview) and [Service Bus](https://azure.microsoft.com/en-us/products/service-bus). 
 
 If you have only an ERP system and are planning to only connect to Tradecloud, you may consider to build a 1-1 connection, 
 without message-oriented middleware, as it may be quicker and cheaper. 

Some Tradecloud customers build 1-1 connections on the tools or framework the ERP system provides itself. Be aware that these tools may be limited, like missing a HTTP client or server, or missing security or data transformation features.

## Flows scope?

Now you have choosen to buy or build message-oriented middleware or 1-1 connection, lets look at the scope:

The Tradecloud modules (order/shipment/forecast) are agreed in the contract with Tradecloud, but within these modules there are several message flows possible dependent on the buyer or supplier role:

### As a buyer

As a buyer, what message flows are you going to build?

* [orders](order/buyer/issue/README.md) - send orders to your suppliers
* [order updates](order/buyer/update.md) - update an order 
* [order documents](order/buyer/issue/attach-document.md) - attach documents to an order or line
* [order responses](order/buyer/receive/README.md) - receive confirmations, or proposed alternatives, from your suppliers
* [order response documents](order/buyer/receive/download-document.md) - receive attached documents from your suppliers
* [goods receipt advices](order/buyer/receive-goods.md) - notify suppliers about received goods
* [complete an order](order/buyer/complete.md) - notify suppliers about completed order lines
* [cancel an order](order/buyer/cancel.md) - notify suppliers about cancelled order lines
* [shipments](shipment/buyer/receive.md) - receive shipment planning and updates from suppliers
* [shipment documents](shipment/buyer/download-documents.md) - receive attached shipment documents
* [forecasts](forecast/issue.md) - send forecasts to your suppliers

### As a supplier

As a supplier, what message flows are you going to build?

* [orders](order/supplier/receive/README.md) - receive orders and updates from your buyers
* [order documents](order/supplier/receive/download-document.md) - receive attached documents from your buyers
* [order responses](order/supplier/send-order-response/README.md) - confirm order lines, or propose alternatives, to your buyer
* [order response documents](order/supplier/send-order-response/attach-document.md) - attach documents to your confirmations
* [despatch advices](shipment/send-despatch-advice.md) - send shipment despatch advices to your buyers

## ERP checklist

Now you know your scope, the checklist continues with ERP specific questions:

### Native or simple delivery schedule?

Does your ERP system natively support a delivery schedule? A delivery schedule consists of one or more deliveries (date & quantity) for the same item within one order line. It is no problem when your ERP system does not support a delivery schedule natively, but you have to be aware which fields to use:

{% page-ref page="order/buyer/issue/delivery-schedule.md" %}

The simple delivery schedule feature is only available for buyers at this moment.
Please let [support](support.md) know when you are interested in a simple delivery schedule at the supplier side.

### Touched or all order lines?

Does your ERP expect only new and updated or always all lines in an order, order response or shipment message?

#### Order/response message

Tradecloud sends only touched lines in an order/response message. It is no problem when your ERP needs all order/response lines, you may fetch the complete order, see:

{% page-ref page="api/webhook-vs-polling.md#using-get" %}

#### Shipment message

Tradecloud sends always all lines in a shipment message. It is no problem if you only need touched shipment lines, you may filter out lines based on the 'lastUpdatedAt' field, see:

{% page-ref page="shipment/buyer/receive/README.md#shipment-line-meta-information" %}

## API checklist

The checklist continues with more API technical questions:

### Basic or JWT authentication?

Do you want to use Basic Authentication or JSON Web Tokens? Both have pros and cons:

{% page-ref page="security/authentication.md" %}

### JSON or XML?

Do you want to use [JSON](api/standards.md#json) or [XML](api/standards.md#xml)?

Tradecloud default works with JSON but some API endpoints also work with XML and more will be added on request. 
XML documentation will be added soon. Please let [support](support.md) know when you are interested in using XML.

### Webhook or polling?

Do you want to use a webhook or polling to receive messages? Check out:

{% page-ref page="api/webhook-vs-polling.md" %}

#### Ip source filtering?

When using webhooks, you might consider to add ip source filtering to your firewall as additional security, as an integration does not use MFA or SSO. You may find the Tradecloud ip adresses here:

{% page-ref page="api/environments.md#source-ip-addresses" %}

### Are you compatible?

Your integration must be compatibility, especially following the forward compatibility rules:

{% page-ref page="api/compatibility.md" %}

### Do you have a test environment?

Tradecloud provides a test environment which you may use to develop and test against:

{% page-ref page="api/environments.md#acceptance-test-environment" %}

### Rules

There are some [rules and limits](#api/rules.md) which you may want to check.

### Tools

There are some [tools][#api/tools.md] which you may want to use. Let [support](#support.md) know if you need some example.

### Support

If you have any question just ask:

{% page-ref page="support.md" %}
