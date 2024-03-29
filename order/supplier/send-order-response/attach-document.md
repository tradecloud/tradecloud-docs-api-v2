---
description: How to attach a document to an order or line response
---

# Attach a document to an order response

You can attach documents using three methods:

1. Upload your document to the Tradecloud object-storage and attach the `objectId` to the order or line.
2. Upload your document to your company's content server and attach the `url` to the order or line.
3. Only attach document meta data, such as document code/number, revision and name.
   
## Method 1. Attach a document using the Tradecloud object-storage

### Step 1. Upload a document to the Tradecloud object-storage

Use the [Upload document](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/object-storage/specs.yaml#/object-storage/uploadDocument) endpoint to upload the document to the Tradecloud object-storage and remember the returned document `objectId`.

### Step 2. Attach the uploaded document in the order message using the `/order/order-response` API

You can attach documents using the `documents` field on either `order` or `lines` level in the body of the [Send order response](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/supplier-endpoints/sendOrderResponseBySupplierRoute) endpoint:

{% page-ref page="./" %}

This will NOT create an `OrderDocumentsAttachedBySupplier` activity and NO acknowledge task for the buyer.

{% hint style="warning" %}
The total number of documents is limited to 100 documents per order header and per order line.
{% endhint %}

### Documents body

* `code` : optional document code or number. The document code should be unique within your company and immutable.

{% hint style="info" %}
If a document with the same code is already attached to the order or line, the document will be replaced, else it will be appended.
{% endhint %}

* `revision`: optional document revision \(or version\) code or number
* `name` : optional document short \(file\) name
* `description` : optional document description or long name
* `type`: optional document business type
* `objectId`: the Tradecloud object identifier which was returned by the Tradecloud object-storage upload

## Method 2. Attach a document using your company's content server

### Step 1. Upload to your company's content server

Upload documents to your company's content server and remember the returned document `url`.

### Step 2. Provide the `url` in the order message using the `/order/order-response` API

You can provide the `url` using the `documents` field on either `order` or `lines` level in the order body of the [Send order response](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/supplier-endpoints/sendOrderResponseBySupplierRoute) endpoint.

This will NOT create an `OrderDocumentsAttachedBySupplier` activity and NO acknowledge task for the buyer.

### Documents body

* `code` : optional document code or number. The document code should be unique within your company and immutable.

{% hint style="info" %}
If a document with the same code is already attached to the order or line, the document will be replaced, else it will be appended.
{% endhint %}

* `revision`: optional document revision \(or version\) code or number
* `name` : optional document short \(file\) name
* `description` : optional document description or long name
* `type`: optional document business type
* `url`: the document location on the company's content server

## Method 3. Only provide document meta data

Only provide document meta data like code, revision, name, description and type.

You can provide the meta data using the `documents` field on either `order` or `lines` level in the order body of the [Send order response](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/supplier-endpoints/sendOrderResponseBySupplierRoute) endpoint.

This will NOT create an `OrderDocumentsAttachedBySupplier` activity and NO acknowledge task for the buyer.

### Documents body

* `code` : optional document code or number. The document code should be unique within your company and immutable.

{% hint style="info" %}
If a document with the same code is already attached to the order or line, the document will be replaced, else it will be appended.
{% endhint %}

* `revision`: optional document revision \(or version\) code or number
* `name` : optional document short \(file\) name
* `description` : optional document description or long name
* `type`: optional document business type
