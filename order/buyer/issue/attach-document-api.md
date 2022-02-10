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

{% page-ref page="./" %}

{% hint style="info" %}
[Send order OpenAPI Specification](https://swagger-ui.s.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderByBuyerRoute)
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

You can attach documents to existing orders using the `documents` field on either `order` or `lines` level in the body of the `/order/documents` API.

This will create  `OrderDocumentsAttachedByBuyer` and, if enabled, an acknowledge task for the supplier.

{% hint style="warn" %}
Before attaching a document to an order, the order must have been sent to Tradecloud first.
{% endhint %}

{% api-method method="post" host="https://api.accp.tradecloud1.com/v2" path="/order/documents" %}
{% api-method-summary %}

{% endapi-method-summary %}

{% api-method-description %}
Attach the uploaded document `objectId` to the order or line.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=false %}
Bearer Access-Token
{% endapi-method-parameter %}

{% api-method-parameter name="Content-Type" type="string" required=true %}
application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="body" type="string" required=true %}
See OpenAPI specs
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}

{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %} 
Successfully verified and attached order documents.
{% endapi-method-response-example-description %}
{% endapi-method-response-example %}

{% api-method-response-example httpCode=202 %}
{% api-method-response-example-description %} 
Successfully queued the order documents attachment. The purchase order number has not yet been verified.
{% endapi-method-response-example-description %}
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %} 
Order not found.
{% endapi-method-response-example-description %}
{% endapi-method-response-example %}

{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
[Attach order documents by buyer OpenAPI specs](https://swagger-ui.s.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/attachOrderDocumentsByBuyerRoute)
{% endhint %}

{% hint style="info" %}
When attaching documents the provided purchase order number will be verified. 

Response status codes:
- 200 OK - the purchase order number exists and the documents will be attached.
- 202 Accepted - the order verification has been skipped due to service unavailability and the document attachment has been queued.
- 404 Not Found - the purchase order number has not been found. 
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
