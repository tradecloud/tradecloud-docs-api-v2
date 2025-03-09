# Getting started

This page describes all the prerequisites for that should be covered before [sending your first](sending-my-first-order.md) order to Tradecloud.

### 1. Design and checklist

Make sure you have familiarized yourself with [this checklist](../checklist.md). For a minimal PoC, it is important that you made design decisions related to:

* [Delivery Schedules vs Single Deliveries](../api/delivery-schedule.md)
* [Basic Authentication or JWT](../security/authentication). This example will assume you chose Basic Authentication, as this is suitable for most integrations.
* [JSON vs XML](../api/json-vs-xml.md). This example will assume you use JSON. Minimal XML examples can be [provided upon request](../support.md).

After you have set up a PoC, it is advised to go through the full [Checklist](../checklist.md) again and cover the remaining points.

### 2. Getting an integration account

Contact [Tradecloud Support](../support.md) to request an Integration account and some test suppliers.
To gain access to the Tradecloud Acceptance environment, we will need:

* 2 email addresses:
  * **An integration email address**: This should be a non-personal email address, of which the mailbox is accessible to the integrator.
  * **A buyer email address**: This can be a personal or non-personal email address, which will be used to log into the Web Portal.
* Your company name
* Company names of two suppliers you want to use for testing, including their supplier number in your ERP. We will initially add test accounts to these supplier companies, so your supplier will not be involved in testing the integration yet.

Once you have received an integration account, you can test its username and password against `https://api.tradecloud1.com/v2/authentication/login` (See [Swagger API Specs](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/authentication/specs.yaml#/authentication/login))


