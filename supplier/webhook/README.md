---
description: How to receive a purchase order sent by the buyer.
---

# Receive an order

Tradecloud will send a new purchase order to the supplier when the buyer issues a purchase order.   
Tradecloud will send an updated purchase order when the buyer reissues a purchase order,  a supplier change proposal is approved by the buyer or when a buyer reopen request is approved by the supplier.

## Receive an order from Tradecloud <a id="receive-an-order-response-from-tradecloud"></a>

To receive an order you will need to use the [webhook connector](https://tradecloud.gitbook.io/connectors/webhook-connector). When an order response is new or has been changed at Tradecloud, we will trigger your webhook.

You can either choose to receive the order id and GET the order yourself or alternatively to receive the order event which contains the affected lines.

{% hint style="warning" %}
When you **GET the order yourself** you will get **ALL** the order lines.

When you use **the order event** it will **ONLY** contain the lines **affected** by the order event.
{% endhint %}

In case of a **GET webhook**, using the **order id** you can fetch the actual order from Tradecloud:

{% hint style="info" %}
[GET webhook eindpoint OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-client/specs.yaml#/order-webhook%20endpoints/webhookGet)  
[API v2 GET order OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order/specs.yaml#/order/getOrderByIdRoute)
{% endhint %}

In case of **POST** or **PUT** **webhook** you can use the **order event** inside the request JSON body:

{% hint style="info" %}
[POST/PUT webhook endpoint OpenAPI specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-client/specs.yaml#/order-webhook%20endpoints/webhookPost)
{% endhint %}

### Body JSON objects <a id="order-body-json-objects"></a>

#### Event

In case of an **POST or PUT webhook** the body will contain:

* `eventName:`The event name summarizes what happened, one of:
  * `OrderIssuedByBuyer`: New order has been issued by buyer.
  * `OrderReissuedByBuyer`: Updated order has been issued by buyer.
  * `OrderChangesProposalApprovedByBuyer`: Buyer has approved proposed order lines.
  * `OrderChangesProposalRejectedByBuyer`: Buyer has rejected proposed order lines.
  * `OrderDocumentsAttachedByBuyer`: Buyer [attached documents](download-document.md) to order or lines.
  * `OrderSynced`: Order has been synced from the legacy platform.
* `orderEvent`: The actual order event, see **Order** below.

#### Order

* `id`: the Tradecloud order identifier
* `buyerOrder`: the buyer part of the order, see below
* `supplierOrder`: the supplier part of the order
* `indicators.deliveryOverdue` is true when all order lines are overdue
* `status.processStatus`: is the aggregate of all lines process status, see below
* `status.logisticsStatus`: is the aggregate of all lines logistics status, see below
* `version`: the  Tradecloud order version number
* `eventDates`: some key order event date/times

#### Buyer order part <a id="supplier-order-part"></a>

`buyerOrder` contains the buyer order fields:

* `companyId`: the supplier's Tradecloud company identifier. 
* `supplierAccountNumber`: your account number as known in the buyer's ERP system
* `description`: a free format additional description of this order added by the buyer
* `contact`: the buyer employee responsible for this order. 
* `properties`: are key-value based custom fields, added by the buyer.
* `notes`: are simple custom fields, added by the buyer.
* `documents`: contain meta data and link of attached documents by the buyer.  

#### Supplier order part <a id="buyer-order-part"></a>

`supplierOrder` is mostly an echo of your order fields as explained in[ Send order response](../send-order-response/)​.

* `buyerAccountNumber`: the buyer account number as known in your ERP system.



