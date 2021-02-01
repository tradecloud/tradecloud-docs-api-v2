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

## Identifiers

Identifier examples are:

- `supplierAccountNumber`
- `buyerAccountNumber`
- `purchaseOrderNumber`
- `destination.code`
- `position`
- `item.number`
- `deliverySchedule.position`
- `salesOrderNumber`
- `salesOrderPosition`
- `contact.email`
- `contact.userName`

### Identifiers must be unique and immutable

Your identifiers

- **must be unique**
- **must never change**
- **must never be reassigned**

### Identifiers must not contain whitespace characters

Your identifiers **must not contain whitespace characters.**

## Connections must be configured

The **account number should be set on forehand** in the **Tradecloud** **connection** with your supplier or buyer. You can set the account code when inviting a new connection or at any time in the connection overview in the portal.

## Sending orders or order responses

### Send orders or responses sequential

Send the next order or response when the previous one has been responded with HTTP Status Code 200

Do **not** send more than **10 requests per second**.

Tradecloud may respond with [HTTP Status Code 429](https://tools.ietf.org/html/rfc6585#section-4) `Too Many Requests`

### Only send new or changed orders or order responses

Only send an **order** or **order response** that either **is new** or **has an actual change**

### The order or order response should only contain new or changed lines

The order or order response should only contain **order lines** that are **new or changed**.
Sending an unchanged order line could trigger an unexpected line status change in Tradecloud.

### Never send all orders or responses periodically

Never resend **all** or **all active** orders or responses periodically.

## Orders and lines

As buyer your integration **should not change destination or item** when updating an order line.

Your integration **must** **support a line delivery schedule with multiple schedule lines** when sending or receiving an order, response or event.

Your integration **must support** **the other party may** **add or remove a delivery schedule line**.

## Attach a document

## Receive goods

## Complete an order

## Reopen an order

## Cancel an order
