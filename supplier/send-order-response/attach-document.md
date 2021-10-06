---
description: How to attach a document to an order or line response
---

{% hint style="warning" %}
This feature is not available yet. Please contact support@tradecloud1.com if you need this feature.
{% endhint %}

# Attach a document to an order response

You can attach documents using three methods:

1. Upload your document to the Tradecloud object-storage and attach the `objectId` to the order or line
2. Upload your document to your company's content server and attach the `url` to the order line
3. Only attach document meta data, such as document code/number, revision and name

## Method 1. Attach a document using the Tradecloud object-storage

{% hint style="warning" %}
Your integration should only upload documents and images with [supported Media Types and File Extensions]()
{% endhint %}

### Step 1. Upload a document to the Tradecloud object-storage

{% api-method method="post" host="https://api.accp.tradecloud1.com/v2" path="/object-storage/document" %}
{% api-method-summary %}
Upload a new document
{% endapi-method-summary %}

{% api-method-description %}
Upload the document to Tradecloud's object storage which returns an `objectId`
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Bearer Access-Token
{% endapi-method-parameter %}

{% api-method-parameter name="Content-Type" type="string" required=true %}
application/???
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="body" type="object" required=true %}
Document body
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Document upload successful, returning the object id
{% endapi-method-response-example-description %}

```text
{
  "id": "40fef20d-8769-4a0b-aa2d-90a0b00750b4"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=413 %}
{% api-method-response-example-description %}
Document upload failed, the document size exceeds 100 MB
{% endapi-method-response-example-description %}

```text

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
[Upload document OpenAPI specs](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/object-storage/specs.yaml#/object-storage/uploadDocument)
{% endhint %}

### Step 2. Attach the uploaded document `objectId` to the order or line

{% api-method method="post" host="https://api.accp.tradecloud1.com/v2" path="/order-response/documents" %}
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
Successfully verified and attached order response documents.
{% endapi-method-response-example-description %}
{% endapi-method-response-example %}

{% api-method-response-example httpCode=202 %}
{% api-method-response-example-description %} 
Successfully queued order response documents. The buyer account number and purchase order number has not yet been verified.
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
TO DO: Attach order documents by supplier OpenAPI specs
{% endhint %}

{% hint style="info" %}
When ataching documents the provided buyer account number and purchase order number will be verified. 

Response status codes:
- 200 OK - the buyer account number and purchase order number exist and the documents will be attached.
- 202 Accepted - the order verification has been skipped due to service unavailability and the document attachment has been queued.
- 404 Not Found - either the buyer account number or the purchase order number has not been found. 
{% endhint %}

## Order response documents body

### Order

* `companyId`: the optional Tradecloud company identifier. You only have to provide a companyId when your integration user account has multiple company permissions.
* `buyerAccountNumber`: the buyer account number as known in your ERP system
* `purchaseOrderNumber`: the purchase order number as sent by the buyer
* `documents`: the documents to be attached to this order

### Lines

* `lines`: the purchase order lines having a new document attached
* `position`: the purchase order line position within the purchase order
* `documents`: the documents to be attached to this line

### Documents

* `code` : optional document code or number. The document code should be unique within your company and immutable.
* `revision`: optional document revision \(or version\) code or number
* `name` : optional document short \(file\) name
* `description` : optional document description or long name
* `type`: optional document business type
* `objectId`: optional Tradecloud object identifier which was returned by the Tradecloud object-storage upload
* `url`: optional document location if it is not stored in the Tradecloud object-storage.

## Response

When the `/api-connector/order-response/documents` API method returns HTTP status code 200, the order documents were successfully queued for processing by Tradecloud. Processing takes usually less then a second, after which the order response documents are available in the portal and are forwarded to the buyer ERP integration.

## Method 2. Attach a document using your company's content server

### Step 1. Upload to your company's content server

Upload documents to your company's content server and remember the returned document `url`.

### Step 2. Attach uploaded document `url` to the order or line

Use Step 2. in method 1, but use `url` instead of `objectId`

## Method 3. Only provide document meta data

Only provide document meta data like code, revision, name, description and type.

Use Step 2. in method 1, but do not provide an `url` or `objectId`

