# Checklist

{% hint style="danger" %}
This checklist an overview of all technical design decisions you need to make before starting to build an API integration with Tradecloud One.
{% endhint %}

This is divided in:

- Architecture Design
- ERP Design
- API Integration Design

## Checklist Architecture Design

When you are going to connect your ERP to Tradecloud One, you have to make some **integration architecture decisions**

### Connector or API Integration?

- [ ] Should I buy a Connector or build an API integration?

**Tradecloud One Connectors**  

Tradecloud One Connectors already contain the necessary components, message flows and data transformations to connect with Tradecloud One.  
Together with our partners, Tradcloud offers the following connector:

* AFAS Connector _(by [Improvit](https://www.improvit.nl/))_
* Tradecloud templates at _[Copernicus Niklas integration platform](https://www.copernicus.nl/en/products/niklas-integration-platform/)_
* CSV Connector _(by [Supply Drive](https://supplydrive.cloud/))_
* Edifact Connector _(by [Supply Drive](https://supplydrive.cloud/))_
* Exact Globe Connector _(by [AB Software](https://www.wijzijnab.nl/))_
* Infor LN Connector _(by [Xibis](https://xibis.nl/))_
* Isah API Connector _(by [Tambien](https://tambien.nl))_
* Isah [SCI](https://help.isah.com/r511/#/home/71601/1043/isah) Connector _(by [Isah](https://isah.com))_
* Microsoft Dynamics 365 Business Central [Connectivity Studio _(by To-Increase)_](https://www.to-increase.com/business-integration/microsoft-dynamics-bc/connectivity-studio) 
* Microsoft Dynamics 365 Finance & Operations [Connectivity Studio _(by To-Increase)_](https://www.to-increase.com/business-integration/connectivity-studio)
* SAP SOAP Connector - for single SAP ERP instances
* [SCSN](https://smart-connected.nl) Connector _(by [Supply Drive](https://supplydrive.cloud/))_

### Middleware or 1-1 connection?

- [ ] Should I buy or build middleware or build a 1-1 connection?

When building an API integration, lets look at the integration architecture: 

Do you have multiple business systems, like ERP, WMS and PLM systems, that have to integrate with Tradecloud?
Do you already or plan to integrate with the outside world, like webshops and logistics partners?
In these cases it is recommended to use message-oriented middleware.

Some Tradecloud customers buy middleware like [ConnectPlaza](https://www.connectplaza.com/#1), [Mulesoft](https://www.mulesoft.com/), [Orbis](https://www.orbis-software.nl/) and [WebMethods](https://www.softwareag.com/en_corporate/platform/integration-apis/webmethods-integration.html). Be aware you still have to build and maintain message flows & data transformations and install and configure the middleware components.

Some Tradecloud customers build on Microsoft [Azure Integration Services](https://azure.microsoft.com/en-us/products/category/integration) mostly using [API Management](https://azure.microsoft.com/en-us/products/api-management), [Logic Apps](https://learn.microsoft.com/en-us/azure/logic-apps/logic-apps-overview) and [Service Bus](https://azure.microsoft.com/en-us/products/service-bus). 
 
 If you have only one ERP system and are planning to connect to Tradecloud only, you may consider to build a 1-1 connection, without message-oriented middleware.

Some Tradecloud customers build 1-1 connections using the tools provided by the ERP system. Be aware that these tools may be limited, and may miss for example a HTTP client or server, or security or data transformation features.

### Which team members do I need?

- [ ] Based on these choices, which team members do I need?

When using a Tradecloud Connector, in most cases a partner consultant will install, configure and maintain the Connector for you.

In the case of message-oriented middleware, you will need an integration consultant to build and maintain the message flows & data transformations and install & configure the middleware components.

When building an API integration, you will need developers and a tester to build and maintain the message flows & data transformations and install & configure the components.

In all cases you will need a cloud or system engineer, to configure a firewall, configure SSL, install and configure a web server or Microsoft [Azure Integration Services](https://azure.microsoft.com/en-us/products/category/integration) components.

### Which **message flows** should I build?

- [ ] Which message flows should I build?

When building an API integration, lets look at the scope: The Tradecloud modules (order/shipment/forecast) are agreed in the contract with Tradecloud, but within these modules there are several **message flows** possible dependent on the buyer or supplier role:

#### As a buyer

As a buyer, what message flows are you going to build?

* [orders](order/buyer/issue/README.md) - send orders to your suppliers
* [order updates](order/buyer/update.md) - update an order 
* [order documents](order/buyer/issue/attach-document.md) - attach documents to an order or line
* [order responses](order/buyer/receive/README.md) - receive confirmations, or proposed alternatives, from your suppliers
* [order response documents](order/buyer/receive/download-document.md) - receive attached documents from your suppliers
* [goods receipt advices](order/buyer/receive-goods.md) - notify suppliers about received goods
* [complete an order](order/buyer/complete.md) - notify suppliers about completed order lines
* [cancel an order](order/buyer/cancel.md) - notify suppliers about cancelled order lines
* [shipments](shipment/buyer/receive/README.md) - receive shipment planning and updates from suppliers
* [shipment documents](shipment/buyer/receive/download-document.md) - receive attached shipment documents
* [forecasts](forecast/issue.md) - send forecasts to your suppliers

#### As a supplier

As a supplier, what message flows are you going to build?

* [orders](order/supplier/receive/README.md) - receive orders and updates from your buyers
* [order documents](order/supplier/receive/download-document.md) - receive attached documents from your buyers
* [order responses](order/supplier/send-order-response/README.md) - confirm order lines, or propose alternatives, to your buyer
* [order response documents](order/supplier/send-order-response/attach-document.md) - attach documents to your confirmations
* [despatch advices](shipment/supplier/send-despatch-advice.md) - send shipment despatch advices to your buyers

## ERP checklist

The checklist continues with ERP specific questions:

### Use a **native** or **simple** delivery schedule?

Does your ERP system **natively support a delivery schedule?** A delivery schedule consists of one or more deliveries, having a position, date & quantity, for the same item within one order line. It is no problem when your ERP system does not support a delivery schedule natively, but you have to be aware which alternative fields to use:

{% page-ref page="order/buyer/issue/delivery-schedule.md" %}

The simple delivery schedule feature is only available for buyers at this moment.
Please let [support](support.md) know when you are interested in a simple delivery schedule at the supplier side.

### Can you **split** a delivery schedule?

Does you ERP system support delivery or order lines split by a supplier? A supplier may split a line into multiple lines. A split line will have no position assigned by Tradecloud. The ERP system must assign a position to the split line and update the order line to Tradecloud, check out:

{% page-ref page="order/buyer/receive/delivery-schedule.md" %}

### **Touched** or **all** order lines?

Does your ERP expect only new and updated or always all lines in an order, order response or shipment message?

#### Order/response message

Tradecloud sends only touched lines in an order/response message. It is no problem when your ERP needs all order/response lines, you may fetch the complete order, see:

{% page-ref page="api/webhook-vs-polling.md#using-get" %}

#### Shipment message

Tradecloud sends always all lines in a shipment message. It is no problem if you only need touched shipment lines, you may filter out lines based on the 'lastUpdatedAt' field, see:

{% page-ref page="shipment/buyer/receive/README.md#shipment-line-meta-information" %}

## API checklist

The checklist continues with technical API questions:

### **Basic** or **JWT** authentication?

Do you want to use Basic Authentication or JSON Web Tokens for your API client? Both have pros and cons:

{% page-ref page="security/authentication.md" %}

### **JSON** or **XML**?

Do you want to use [JSON](api/standards.md#json) or [XML](api/standards.md#xml)?

Tradecloud default works with JSON but some API endpoints also work with XML and more will be added on request. 
XML documentation will be added soon. Please let [support](support.md) know when you are interested in using XML.

### **Webhooks** or **polling**?

Do you want to use webhooks or polling to receive messages? Check out:

{% page-ref page="api/webhook-vs-polling.md" %}

#### Webhook **Basic** or **Bearer Token** authentication?

When using webhooks, do you want to use Basic Authentication or Bearer Tokens for your webhooks?

#### Ip source filtering?

When using webhooks, you might consider to add ip source filtering to your firewall as additional security, as a webhook does not use MFA or SSO. You may find the Tradecloud egress ip addresses here:

{% page-ref page="api/environments.md#source-ip-addresses" %}

### Are you **forward compatible**?

Your integration must follow the forward compatibility rules:

{% page-ref page="api/compatibility.md" %}

### Do you have a **test environment**?

Tradecloud provides a test environment which you may use to develop and test against:

{% page-ref page="api/environments.md#acceptance-test-environment" %}

### Rules

There are [rules and limits](api/rules.md) which you may want to check.

### Tools

There are [tools](api/tools/README.md) which you may want to use. Let [support](support.md) know if you need some example.

### Support

If you have any question just ask:

{% page-ref page="support.md" %}
