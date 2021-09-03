---
description: How to attach a document to an order or line
---

# Attach a document to an order

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
Upload the document to Tradecloud's object storage which will return an `objectId`
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

### Step 2. Choose an appropriate API to attach the document

{% page-ref page="attach-document-api.md" %}

## Method 2. Attach a document using your company's content server

### Step 1. Upload to your company's content server

Upload documents to your company's content server and remember the returned document `url`.

### Step 2. Choose an appropriate API to attach the document

{% page-ref page="attach-document-api.md" %}

## Method 3. Only provide document meta data

Only provide document meta data like code, revision, name, description and type.

Choose an appropriate API to attach the document

{% page-ref page="attach-document-api.md" %}

