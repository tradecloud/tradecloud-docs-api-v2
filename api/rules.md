---
description: API rules check list
---

# Rules

{% hint style="danger" %}
Your integration **must follow** these rules.

Tradecloud will **review** your integration in the acceptance test environment **before going live.**
{% endhint %}

## Support the Tradecloud standards

Your integration **must support** the Tradecloud [standards](standards.md).

{% hint style="warning" %}
Pitfall: JSON syntax does not assign any significance to the **ordering** of name/value pairs.
{% endhint %}

## Support forward compatibility

Your integration **must support** [forward compatibility](compatibility.md#forward-compatibility).

## Identifiers must be unique and immutable

Your identifiers like below **must be** **unique** and may **never change or be reassigned**.

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

### Send orders or responses sequential

Send the next order or response when the previous one has been responded with HTTP Status Code 200

Do **not** send more than **10 requests per second**.

Tradecloud may respond with [HTTP Status Code 429](https://tools.ietf.org/html/rfc6585#section-4) `Too Many Requests`

### Only resend changed orders or order responses

Only resend an order or order response that **has an actual change**

### **Never send all orders periodically**

Never resend **all** orders or **all active** orders periodically.

## Orders and lines

As buyer your integration **should not change destination or item** when reissuing an order line.

Your integration **must** **support a line delivery schedule with multiple schedule lines** when sending or receiving an order, response or event.

Your integration **must support** **the other party may** **add or remove a delivery schedule line**.

## Attach a document



## Receive goods



## Complete an order



## Reopen an order



## Cancel an order





