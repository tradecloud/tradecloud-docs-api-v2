---
description: How to attach a document to an order or line
---

# Attach a document to an order

You can attach documents using three methods:

1. Upload your document to the Tradecloud object-storage and attach the `objectId` to the order or line.
2. Upload your document to your company's content server and attach the `url` to the order line.
3. Only attach document meta data, such as document code/number, revision and name.
   
## Method 1. Attach a document using the Tradecloud object-storage

### Step 1. Upload a document to the Tradecloud object-storage

Use the [Upload order document](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/object-storage/specs.yaml#/object-storage/uploadDocument) to up

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

