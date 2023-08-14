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

## Sending messages

Rules for any Tradecloud API request:

### Send messages sequential

Send the next message when the previous one has been responded with HTTP Status Code 200 OK or 202 Accepted.

Do **not** send more than **10 requests per second**.

Tradecloud may respond with [HTTP Status Code 429](https://tools.ietf.org/html/rfc6585#section-4) `Too Many Requests`

### Queue and retry messages with an exponential backoff.

The Tradecloud [environments](environments.md) do not have an availability SLO of 100%. If Tradecloud is temporarily unavailable, it is the API client's responsibility to queue the message and automatically retry with exponential backoff till Tradecloud is available again. An alternative is to warn the ERP user, who is trying to send the message to Tradecloud, so the user can manually retry later.

If Tradecloud responds with either: 

- a HTTP Status Code 5xx Server Error or
- [HTTP Status Code 429](https://tools.ietf.org/html/rfc6585#section-4) `Too Many Requests` or 
- the requests does time out (currently 5 secs. at Tradecloud API side)
  
Then the client must automatically retry, using an exponential backoff strategy, or use a manual retry strategy. 
The [Exponential Backoff Calculator](http://backoffcalculator.com/?interval=5&rate=2&attempts=5) is handy to verify the retry plan.

### Only send new or changed orders or order responses

Only send an **order** or **order response** that either **is new** or **has an actual change**

### Never resend all orders or responses periodically

Never *re*send **all** or **all active** orders, responses, dispatch advices or forecasts periodically.

Resending periodically will result in processing delays and excessive network, server and storage resource usage.

### The order or order response should only contain new or changed lines

The order or response should preferable only contain **order lines** that are **new or changed**. But you can also send all lines anyway.

Sending all lines may result in processing delays and unnecessary network, server and storage resource usage.

### Arrays are limited to 100 objects

The TOTAL number of objects is limited to 100 objects per collection by default.

Examples are:

- 100 documents in total per order 
- 100 documents in total per order line
- 100 delivery lines per delivery schedule
- 100 delivery lines per delivery history

Exceptions are:

- 500 lines in total per order 
- 500 lines in total per shipment
- 500 lines in total per supplier forecast

## Orders and lines

### Do not change destination or item

As buyer your integration **should not change the order destination or line item** when updating an order.  
If you wish to change the order destination, or a line item, either:

* Discuss this with your supplier through the chat function in the Portal. If your supplier agrees, update the order\(line\) accordingly through your integration.
* Cancel the order\(line\) and create a new order\(line\) with the alternative destination or item.

### Support delivery schedule

Your integration **must support a line delivery schedule with multiple schedule lines** when sending or receiving an order, response or event.  
If your ERP does not support a delivery schedule in an order line, this will conflict with split lines that may be sent back by your supplier. You can either:

* Map the delivery schedule lines that come in on ERP order lines in your integration.
* Aggregate Tradecloud's delivery schedule lines that are sent by your supplier as they come in, but never send an update regarding the delivery schedule after the order was created.
* Reject any supplier proposal or reopen request with split delivery lines.

Your integration **must support the other party may add or remove a delivery schedule line**.
