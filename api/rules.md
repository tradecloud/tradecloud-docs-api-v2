---
description: API rules check list
---

# Rules

{% hint style="danger" %}
Your integration **must follow** these rules.

Tradecloud will **review** your integration in the acceptance test environment **before going live.**
{% endhint %}

## Support the Tradecloud standards

Your integration **must support** the Tradecloud standards.

{% page-ref page="standards.md" %}

## Support forward compatibility

Your integration **must support** **forward** compatibility.

{% page-ref page="compatibility.md" %}

## Identifiers must be unique and immutable

Your identifiers like below must be **unique** and may **never change or be reassigned**.

Identifier examples are:

* `supplierAccountNumber`
* `buyerAccountNumber`
* `purchaseOrderNumber`
* `destination.code`
* `position`
* `item.number`
* `deliverySchedule.position`
* `salesOrderNumber`
* `salesOrderPosition`
* `contact.email`
* `contact.userName`

## Connections must be configured

The **account number should be set on forehand** in the **Tradecloud** **connection** with your supplier or buyer. You can set the account code when inviting a new connection or at any time in the connection overview in the portal.

## Sending orders or order responses

### Only resend changed orders or order responses

Only resend an order or order response that **has an actual change**

### **Never send all orders periodically**

Never resend **all** orders or **all active** orders periodically.

## Attach a document



## Receive goods



## Complete an order



## Reopen an order



## Cancel an order





