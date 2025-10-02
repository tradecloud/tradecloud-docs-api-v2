# Checklist

{% hint style="danger" %}
This checklist an overview of all technical design decisions you need to make before starting to build an API integration with Tradecloud One.
{% endhint %}

This is divided in:

- Architecture Design
- ERP Design
- API Integration Design

## Checklist Architecture Design

When you are going to connect your ERP to Tradecloud One, you have to make some **integration architecture decisions**:

### Connector or API Integration?

[ ] **Should I buy a Connector or build an API integration?**

This mainly depends on your ERP system.

If your ERP is compatible with one of the Tradecloud connectors below, we advise to use one of our connectors. These connectors already contain the necessary components, message flows and data transformations to connect with Tradecloud One. 
They are battle-tested by our customers and will speed up your onboarding onto the Tradecloud One platform.

If your ERP is not compatible with one of these connectors, it is possible to build an integration with our [JSON/XML API](#checklist-api-integration-design).
This will require in-depth knowledge about your [ERP](#checklist-erp-design) and a partner or in-house software developer that has experience with web-based [API integrations](#checklist-api-integration-design).

#### Tradecloud One Connectors

Together with our partners, Tradecloud offers the following connectors.

ERP-specific connectors:

- AFAS Connector _(by [Improvit](https://www.improvit.nl/))_
- Tradecloud templates at _[Copernicus Niklas integration platform](https://www.copernicus.nl/en/products/niklas-integration-platform/)_
- Exact Globe Connector _(by [AB Software](https://www.wijzijnab.nl/))_
- Infor LN Connector _(by [Xibis](https://xibis.nl/))_
- Isah API Connector _(by [Tambien](https://tambien.nl))_
- Isah [SCI](https://help.isah.com/r511/#/home/71601/1043/isah) Connector _(by [Isah](https://isah.com))_
- Microsoft Dynamics 365 Business Central [Connectivity Studio _(by To-Increase)_](https://www.to-increase.com/business-integration/microsoft-dynamics-bc/connectivity-studio)
- Microsoft Dynamics 365 Finance & Operations [Connectivity Studio _(by To-Increase)_](https://www.to-increase.com/business-integration/connectivity-studio)
- SAP SOAP Connector - for single SAP ERP instances _(by Tradecloud)_
- Slim4 Forecast Connector _(by [Slimstock](https://www.slimstock.com))_

Generic Connectors:

- [CSV Connector](connectors/sftp/csv.md) by [Supply Drive](https://supplydrive.cloud/)
- [Edifact Connector](connectors/sftp/edifact.md) by [Supply Drive](https://supplydrive.cloud/)
- [SCSN](https://smart-connected.nl) Connector by [Supply Drive](https://supplydrive.cloud/)

### Middleware or 1-1 connection?

[ ] **Should I buy or build middleware or build a 1-1 connection?**

#### Using Message-oriented Middleware

You will need message-oriented middleware if one of the following applies:

- You have multiple business systems, like ERP, WMS and PLM systems, that have to integrate with Tradecloud One
- You plan to integrate with the outside world, eg. with webshops or logistics partners

Examples of message-oriented middleware that some of our customers use are:

- [ConnectPlaza](https://www.connectplaza.com/#1), [Mulesoft](https://www.mulesoft.com/), [Orbis](https://www.orbis-software.nl/) and [WebMethods](https://www.softwareag.com/en_corporate/platform/integration-apis/webmethods-integration.html).
- Microsoft [Azure Integration Services](https://azure.microsoft.com/en-us/products/category/integration) mostly using [API Management](https://azure.microsoft.com/en-us/products/api-management), [Logic Apps](https://learn.microsoft.com/en-us/azure/logic-apps/logic-apps-overview) and [Service Bus](https://azure.microsoft.com/en-us/products/service-bus).

Be aware you still have to build and maintain message flows & data transformations and install and configure the middleware components.

#### Using a 1-1 connection

If you have only one ERP system and are planning to connect to Tradecloud only, building a 1-1 connection without message-oriented middleware will suffice.

Some Tradecloud customers build 1-1 connections using the tools provided by the ERP system. Be aware that these tools may be limited, and may miss for example a HTTP client or server, or security or data transformation features.

### Required team members

[ ] **Which team members do I need?**

- When using a **Tradecloud One Connector**, in most cases a partner consultant will install, configure and maintain the Connector for you.
- When using **message-oriented middleware**, you will need an integration consultant with ERP knowledge to build and maintain the message flows & data transformations and install & configure the middleware components.
- When building an **API integration**, you will need developers and a tester, both with ERP knowledge, to build and maintain the message flows & data transformations and install & configure the components.

**In all cases** you will need a cloud or system engineer, to configure a firewall, configure SSL, install and configure a web server or Microsoft [Azure Integration Services](https://azure.microsoft.com/en-us/products/category/integration) components.

### Message flows

[ ] **Which message flows should I build?**

This depends on the Tradecloud One modules that are agreed upon in the contract with Tradecloud.

Within each module, there are several **message flows** possible dependent on the buyer or supplier role. The more flows are implemented, the less manual work remains. Whether a flow can be implemented depends on:

- The process flow in your business
- The capabilities of your ERP system
- The capabilities of the integration

We are happy to [support](support.md) you in making this decision, sharing our expertise of the ERP and Supply Chain landscape.

#### As a buyer

For more information about the available message flows for buyers, check out:

- The [buyer order process](order/buyer/README.md)
- The [buyer shipment process](shipment/buyer/README.md)
- The [forecast process](forecast/README.md)

#### As a supplier

For more information about the available message flows for suppliers, check out:

- The [supplier order process](order/supplier/README.md)
- The [supplier shipment process](shipment/supplier/README.md)

## Checklist ERP Design

{% hint style="info" %}
This part of the checklist is not applicable if you use one of the [Tradecloud One Connectors](#connector-or-api-integration)
{% endhint %}

Before starting the actual implementation, you need to verify the capabilities and requirements of your ERP system for an integration.

[ ] **Use a _delivery schedule_ or _single delivery_ per order line?**  

**Delivery schedule vs. single delivery:**
  
- **Delivery schedule**: Multiple scheduled deliveries per order line (default method)
  - Best for ERP systems that natively support multiple deliveries per order line (e.g., SAP)
  - Provides more flexibility for complex delivery arrangements
  - Maintains all scheduled deliveries within a single order line

- **Single delivery**: One scheduled delivery per order line
  - Best for ERP systems that only support one scheduled delivery date/quantity per order line
  - Tradecloud will automatically split delivery schedules into separate order lines in the communication with your ERP system
  - Each split line maintains a reference to the original line via `originalPosition`
  
Choose based on your ERP system's capabilities and your business requirements.

{% page-ref page="order/buyer/issue/delivery-schedule.md" %}

[ ] **Can your ERP system handle split order lines?**  

When a supplier splits an order line (e.g., it cannot deliver 10 pieces on date X, but it can deliver 6 on date X and 4 on date Y):

- **Delivery schedule**: Multiple scheduled deliveries per order line (default method)
  - Tradecloud creates new order delivery lines with empty `position` values
  - Your ERP system must:
    1. Assign new unique position identifiers to these split delivery lines
    2. Update the delivery lines in Tradecloud with these new positions

- **Single delivery**: One scheduled delivery per order line
  - Tradecloud creates new order lines with empty `position` values
  - These new lines include an `originalPosition` reference to the original line
  - Your ERP system must:
    1. Assign new unique position identifiers to these split order lines
    2. Maintain the relationship to the original line via the `originalPosition` value in your ERP
    3. Update the lines in Tradecloud with these new positions and their `originalPosition`

{% page-ref page="api/delivery-schedule.md" %}

[ ] **Receive only _changed_ or _all_ order/shipment lines?**  

When order updates are sent from Tradecloud One to your ERP, what does your ERP require?  
Does your ERP expect only new and updated lines, or does it always expect all lines of an order in an order/order response and all shipment lines in a shipment message?

### Order/response

Tradecloud sends only touched lines in an order/response message. When your ERP needs all order/response lines, you may fetch the complete order or alternatively use order polling.

### Shipment

Tradecloud sends always all lines in a shipment message. If you only need the touched shipment lines, you may filter out lines based on the 'lastUpdatedAt' field, see:  
{% page-ref page="shipment/buyer/receive/README.md#shipment-line-meta-information" %}  

## Checklist API Integration Design

{% hint style="info" %}
This part of the checklist is not applicable if you use one of the [Tradecloud One Connectors](#connector-or-api-integration)
{% endhint %}

When starting to build and integration with the Tradecloud One API, make sure to check the following:

[ ] **Use [Basic](api/standards.md#basic-http-authentication) or [JWT](api/standards.md#jwt) authentication?**  
Your integration must either use Basic Authentication or authentication based on a JWT token:
{% page-ref page="security/authentication.md" %}

[ ] **Use [JSON](api/standards.md#json) or [XML](api/standards.md#xml)?**  
By default, Tradecloud works with JSON but some API endpoints also work with XML and more will be added on request:
{% page-ref page="api/json-vs-xml.md" %}

[ ] **Use _webhooks_ or _polling_?**  
Depending on the capabilities of your integration, you may choose for using Webhooks or Polling:
{% page-ref page="api/webhook-vs-polling.md" %}

[ ] **If using webhooks, use _Basic_, _Bearer Token_ or  _OAuth_ authentication?**  
In the Tradecloud One webportal, you can configure your webhooks to use either Basic Authentication, a static Bearer token, or OAuth 2.0 Client Credentials Grant.

[ ] **Use Ip source filtering?**  
When using webhooks, you might consider to add ip source filtering to your firewall as additional security, as a webhook does not use MFA or SSO. You may find the Tradecloud egress ip addresses here:  
{% page-ref page="api/environments.md#source-ip-addresses" %}

[ ] **Are you forward compatible?**  
Your integration must follow the forward compatibility rules:  
{% page-ref page="api/compatibility.md" %}

[ ] **Do you have a test environment?**  
Tradecloud provides a test environment which you may use to develop and test against:  
{% page-ref page="api/environments.md#acceptance-test-environment" %} 

[ ] **Usage rules**  
There are [rules and limits](api/rules.md) which you may want to check. 

[ ] **Tools**  
There are [tools](api/tools/README.md) which you may want to use. Let [support](support.md) know if you need some example.

### Support

If you have any question, just ask:

{% page-ref page="support.md" %}
