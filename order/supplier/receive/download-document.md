---
description: How to download a document from an order or line
---

# Download a document attached to an order

You can download documents using two methods:

1. If the webhook order or line `document` contains an `objectId`: Download the buyer's document from the Tradecloud object-storage using the `objectId` and `downloadUrl`
2. If the webhook order or line `document` contains an `url`: Download the document from the buyer's content server.

If both `objectId` and `url` are missing in the `document`, no file is available for download.

## Method 1. Download the document from the Tradecloud object-storage <a id="method-1-download-the-document-from-the-tradecloud-object-storage"></a>

### Step 1. Retrieve the `objectId` from the document <a id="step-1-retrieve-the-objectid-from-the-document"></a>

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

### Step. 2. Retrieve the `downloadUrl` from the object storage <a id="step-2-retrieve-the-downloadurl-from-the-object-storage"></a>

{% api-method method="get" host="https://api.accp.tradecloud1.com/v2" path="/object-storage/document/{objectId}/metadata" %}
{% api-method-summary %}
Get document metadata
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="objectId" type="string" required=false %}
document objectId
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=false %}
Bearer Access-Token
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
  "id": "67aa8ece-5d41-496f-a94c-483e360b833b",
  "filename": "test.pdf",
  "contentType": "application/octet-stream",
  "downloadUrl": "https://tradecloud-accp-documents.s3.eu-central-1.amazonaws.com/67aa8ece-5d41-496f-a94c-483e360b833b?response-content-disposition=attachment%3B%20filename%3Dtest.pdf&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Date=20200406T203728Z&X-Amz-SignedHeaders=host&X-Amz-Expires=59&X-Amz-Credential=AKIAUXFSTTRHS7FN2JKY%2F20200406%2Feu-central-1%2Fs3%2Faws4_request&X-Amz-Signature=8bda9e2b4d810e0d7650e363373874c4f2e52aa53f1e46d82c5bf3eaf907832d"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
[GET document metadata OpenAPI specification](https://swagger-ui.s.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/object-storage/specs.yaml#/object-storage/getDocumentMetadata)
{% endhint %}

### Step 3. Download the document using the `downloadUrl` <a id="step-3-download-the-document-using-the-downloadurl"></a>

Just GET the `downloadUrl`

{% hint style="warning" %}
This Amazon AWS S3 presigned url will expire within 1 minute.
{% endhint %}

## Method 2. Download the document from the supplier content server <a id="method-2-download-the-document-from-the-supplier-content-server"></a>

### Step 1. Retrieve the `url` from the document <a id="step-1-retrieve-the-url-from-the-document"></a>

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

### Step 2. Download the document using the `url` <a id="step-2-download-the-document-using-the-url"></a>

Just GET the `url`

