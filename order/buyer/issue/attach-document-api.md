---
description: Choose an appropriate API to attach a document to an order or line
---

# Choose attach document API

You can attach documents using two methods:

1. Embedded in the order, using the `/order` API
2. Attach to an existing order, using the `/order/documents` API

## 1. Embedded in the order message using the `/order` API

You can attach documents body using the `documents` field on either `order` or `lines` level in the order body of the `/order` API.

This will NOT create an `OrderDocumentsAttachedByBuyer`activity and NO acknowledge task for the supplier.

{% hint style="warning" %}
The total number of documents is limited to 100 documents per order header and per order line.
{% endhint %}

{% page-ref page="./" %}

{% hint style="info" %}
[Send order OpenAPI Specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderByBuyerRoute)
{% endhint %}

### Documents body

* `code` : optional document code or number. The document code should be unique within your company and immutable.
* `revision`: optional document revision \(or version\) code or number
* `name` : optional document short \(file\) name
* `description` : optional document description or long name
* `type`: optional document business type
* `objectId`: optional Tradecloud object identifier which was returned by the Tradecloud object-storage upload
* `url`: optional document location if it is not stored in the Tradecloud object-storage.


## 2. Attach to an existing order using the `/order/documents` API

You can attach documents to existing orders using the `documents` field on either `order` or `lines` level in the body of the [Attach order documents](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/attachOrderDocumentsByBuyerRoute) endpoint.

This will create  `OrderDocumentsAttachedByBuyer` and, if enabled, an acknowledge task for the supplier.

{% hint style="warning" %}
The total number of documents is limited to 100 documents per order header and per order line.
{% endhint %}

{% hint style="warning" %}
Before attaching a document to an order, the order must have been sent to Tradecloud first.
{% endhint %}

{% hint style="info" %}
When attaching documents the provided purchase order number will be verified. 
{% endhint %}

### Order documents body

#### Order

* `companyId`: the optional Tradecloud company identifier. You only have to provide a companyId when your integration user account has multiple company permissions.
* `supplierAccountNumber`: the supplier account number as known in your ERP system
* `purchaseOrderNumber`: the purchase order number as known in your ERP system
* `documents`: the documents to be attached to this order

#### Lines

* `lines`: the purchase order lines having a new document attached
* `position`: the line position within the purchase order
* `documents`: the documents to be attached to this line

#### Documents

* `code` : optional document code or number. The document code should be unique within your company and immutable. 

{% hint style="info" %}
If a document for an order(line) has the same code as an existing document at that order(line), the original will be overwritten. Otherwise, the newly attached document will be appended.
{% endhint %}

* `revision`: optional document revision \(or version\) code or number
* `name` : optional document short \(file\) name
* `description` : optional document description or long name
* `type`: optional document business type
* `objectId`: optional Tradecloud object identifier which was returned by the Tradecloud object-storage upload
* `url`: optional document location if it is not stored in the Tradecloud object-storage.
