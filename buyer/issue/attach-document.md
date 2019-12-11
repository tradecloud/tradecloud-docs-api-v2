---
description: How to attach a document to an order or line
---

# Attach a document to an order

You can attach documents in three ways:

1. Upload your document to the Tradecloud object-storage and link it by objectId to the order or line
2. Upload your document to your company's content server and link it by url to the order line
3. Only provide document meta data, such as document code/number, revision and name

## 1. Attach a document using the Tradecloud object-storage

{% hint style="warning" %}
This feature is planned. Ticket [TC-5060](https://tradecloud.atlassian.net/browse/TC-5060) As a user I want to attach documents to an order \(line\) and be able to download
{% endhint %}

### Step 1. Upload a document to the Tradecloud object-storage

Upload the document to the Tradecloud object-storage and remember the returned objectId.

{% api-method method="post" host="https://api.accp.tradecloud1.com/v2" path="/object-storage/upload" %}
{% api-method-summary %}
Upload a new object and associated metadata
{% endapi-method-summary %}

{% api-method-description %}

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
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

[Upload object OpenAPI Specification](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/object-storage/specs.yaml#/object-storage/upload)

### Step 2. Link the uploaded document objectId to the order or line

Link the uploaded document objectId with the order or line and send the order

```javascript
  "documents": [
      {
        "code": "123456789",
        "revision": "2",
        "name": "Tradecloud API Manual",
        "objectId": "40fef20d-8769-4a0b-aa2d-90a0b00750b4"
      }
    ],
```

Send the order with the `document` using [\(Re\)issue an order](./)

## 2. Attach a document using your company's content server

### Step 1. Upload to your company's content server

Upload to your company's content server and remember the returned document url.

### Step 2. Link the uploaded document url to the order or line

Add a `document` to the `order` or `lines` JSON object, example:

```javascript
  "documents": [
      {
        "name": "Tradecloud API Manual",
        "url": "https://your-content-server.company.com/123456789/2"
      }
    ],
```

Send the order with the `document` using [\(Re\)issue an order](./)

## 3. Only provide document meta data

Add a `document` to the `order` or `lines` JSON object, example:

```javascript
  "documents": [
      {
        "code": "123456789",
        "revision": "2",
        "name": "Tradecloud API Manual"
      }
    ],
```

Send the order with the `document` using [\(Re\)issue an order](./)

