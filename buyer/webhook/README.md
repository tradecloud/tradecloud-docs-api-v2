---
description: How to receive an order response sent by the supplier
---

# Receive an order response

A supplier will confirm an order line by either accepting or rejecting it, or propose an alternative delivery schedule or prices. By accepting, rejecting or proposing the supplier sends a order response to the buyer.

## Receive an order response from Tradecloud

To receive an order response you will need to use the [webhook connector](https://tradecloud.gitbook.io/connectors/webhook-connector).  
When an order response is new or has been changed at Tradecloud, we will trigger your webhook.

You can either choose to receive the order id and GET the order yourself or to receive the order event.   
In either case you will use the GET order JSON body:

{% hint style="info" %}
[API v2 GET order specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order/specs.yaml#/order/getOrderByIdRoute)
{% endhint %}

### Order body JSON objects <a id="order-body-json-objects"></a>

#### Order

* `id`: the Tradecloud order identifier

#### buyerOrder

This part is an echo of your order fields as explained in [Issue a new order](../issue/#order-body-json-objects)

#### supplierOrder

* `companyId`: the supplier's Tradecloud company identifier. 
* `buyerAccountNumber`: your account number as known in the supplier's ERP system
* `description`: a free format additional description of this order by the supplier
* `contact`: the supplier employee responsible for this order. 
* `properties`: are key-value based custom fields, added by the supplier
* `notes`: are simple custom fields, added by the supplier
* `documents`: contain meta data and link of attached documents by the supplier.  See [Download a document attached to an order response](download-document.md) 
* `indicators`: `deliveryOverdue` is true when all order lines are overdue
* `status`: 
* `version`: order Tradecloud version number
* `eventDates`: some key event date/times

#### lines

* `id`: the Tradecloud line identifier

#### buyerLine

This part is an echo of your line fields as explained in [Issue a new order](../issue/#lines)

**supplierLine**

* aaa

















