---
description: How to download a document from an order or line
---

# Download a document attached to an order

You can download documents using two methods:

1. If the webhook order or line `document` contains an `objectId`: Download the buyer's document from the Tradecloud object-storage using the `objectId` and `downloadUrl`
2. If the webhook order or line `document` contains an `url`: Download the document from the buyer's content server.

If both `objectId` and `url` are missing in the `document`, no file is available for download.

## Method 1. Download the document from the Tradecloud object-storage

### Step 1. Retrieve the `objectId` from the document

Please check the `documents` fields in order and lines in: 

```text
"documents": [
  {
    "code": "123456789",
    "revision": "B",
    "name": "Tradecloud API Manual",
    "objectId": "67aa8ece-5d41-496f-a94c-483e360b833b",
    "type": "General",
    "description": "General document"
  }
],
```

In this example the `objectId` is:

```text
67aa8ece-5d41-496f-a94c-483e360b833b
```

### Step. 2. Retrieve the `downloadUrl` from the object storage

Apply the `objectId` in the [GET document metadata](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/object-storage/specs.yaml#/object-storage/getDocumentMetadata) endpoint to retrieve the `downloadUrl` from the object storage.

### Step 3. Download the document using the `downloadUrl`

Just GET the `downloadUrl`

{% hint style="warning" %}
This Amazon AWS S3 presigned url will expire within 1 minute.
{% endhint %}

## Method 2. Download the document from the supplier content server

### Step 1. Retrieve the `url` from the document

Please check the `documents` fields in order and lines in: 

```text
"documents": [
  {
    "code": "123456789",
    "revision": "B",
    "name": "Tradecloud API Manual",
    "url": "http://buyer.com/content/manual.pdf",
    "type": "General",
    "description": "General document"
  }
],
```

In this example the `url` is:

```text
http://buyer.com/content/manual.pdf
```

### Step 2. Download the document using the `url`

Just GET the `url`

