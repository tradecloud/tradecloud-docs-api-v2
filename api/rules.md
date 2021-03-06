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

### Identifiers must be unique and immutable

Your identifiers

* **must be unique**
* **must never change**
* **must never be reassigned**

### Identifiers must not contain whitespace characters

Your identifiers **must not contain whitespace characters.**

## Connections must be configured

The **account number should be set on forehand** in the **Tradecloud connection** with your supplier or buyer. You can set the account code when inviting a new connection or at any time in the connection overview in the portal.

## Sending orders or order responses

### Send orders or responses sequential

Send the next order or response when the previous one has been responded with HTTP Status Code 200

Do **not** send more than **10 requests per second**.

Tradecloud may respond with [HTTP Status Code 429](https://tools.ietf.org/html/rfc6585#section-4) `Too Many Requests`

### Only send new or changed orders or order responses

Only send an **order** or **order response** that either **is new** or **has an actual change**

### The order or order response should only contain new or changed lines

The order or order response should only contain **order lines** that are **new or changed**. Sending an unchanged order line could trigger an unexpected line status change in Tradecloud.

### Never send all orders or responses periodically

Never resend **all** or **all active** orders or responses periodically.

## Orders and lines

As buyer your integration **should not change the order destination or line item** when updating an order.  
If you wish to change the order destination, or a line item, either:

* Discuss this with your supplier through the chat function in the Portal. If your supplier agrees, update the order\(line\) accordingly through your integration.
* Cancel the order\(line\) and create a new order\(line\) with the alternative destination or item.

Your integration **must support a line delivery schedule with multiple schedule lines** when sending or receiving an order, response or event.  
If your ERP does not support a delivery schedule in an order line, this will conflict with split lines that may be sent back by your supplier. You can either:

* Map the delivery schedule lines that come in on ERP order lines in your integration.
* Aggregate Tradecloud's delivery schedule lines that are sent by your supplier as they come in, but never send an update regarding the delivery schedule after the order was created.
* Reject any supplier proposal or reopen request with split delivery lines.

Your integration **must support the other party may add or remove a delivery schedule line**.

## Upload a document or image

Your integration should only upload doucments and images with **supported Media Types and File Extensions**:

{% page-ref page="../security/media-types.md" %}

## Attach a document

## Receive goods

## Complete an order

## Reopen an order

## Cancel an order

