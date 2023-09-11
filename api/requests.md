---
description: How to make API requests
---

# Requests

## Making an API request

An API request consist of:

* [HTTP method](requests.md#HTTP-method): `GET`, `POST`, `PUT` or `DELETE`
* [HTTP headers](requests.md#HTTP-headers): authorization and content type
* [URL](requests.md#URL): HTTPS, environment, service, method and parameters
* [JSON body](requests.md#json-body) which contains the payload

## HTTP method

The API supports

* `GET` to get a specific JSON object, like a purchase order, or to download a document \(one JSON object or document is returned\) or to query objects \(a JSON collection is returned\)
* `POST` to create a new JSON object or upload a document
* `PUT` to update an existing JSON object
* `DELETE` to delete an existing JSON object or document

## HTTP headers

### Authorization

Use the `Authorization` header for basic authentication and token authorization, see [Authentication](../security/authentication.md)

### Content-Type

Use the `Content-Type: application/json` header in case of `POST` or `PUT` with a JSON body.

Use the `Content-Type: application/xml` header in case of `PUT` with an XML body.

## URL

The API uses the [REST](https://en.wikipedia.org/wiki/Representational_state_transfer) software architectural style that defines a set of constraints to be used for creating Web services. The API additionally uses a command and query style.

An URL is build up like this: `https://environment/service/method/parameters?parameters`

### HTTPS scheme

The API only supports HTTPS, see [Encryption](../security/encryption.md).

### Environments

Tradecloud has [three environments](environments.md):

* [test environments](https://api.test.tradecloud1.com) have a short dynamic life cycle and have NO availability SLA
* the [acceptance test environment](https://api.accp.tradecloud1.com) has an availability SLA of 95% 10/5
* the [production environment](https://api.tradecloud1.com/) has an availability SLA of 99.5% 24/7

{% page-ref page="environments.md" %}

### Services

Each environment has a set of services which you can find on each environment page, like the [acceptance test environment](https://api.accp.tradecloud1.com) and [production environment](https://api.tradecloud1.com/)

On the environment page for each service the API endpoint you can find the [OpenAPI 2.0 Specification](https://swagger.io/specification/v2/) [YAML](https://yaml.org/spec/1.2/spec.html) file, the OpenAPI UI rendering, the health and label \(version\) is published.

Common used services are:

* `authentication` for authentication, to get a token
* `api-connector` for buyer and supplier ERP integration
* `object-storage` to upload and download documents
* `order` for order/line commands
* `order-search` for order queries
* `order-line-search` for order-line queries
* `sci-connector` for buyer ERP integration using SCSN

### Methods

In each [OpenAPI 2.0 Specification](https://swagger.io/specification/v2/) you can find the methods supported by the service. For example the [`api-connector`](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml) service:

`POST /api-connector/order` [sends an order by the buyer](../buyer/issue/)

`POST /api-connector/order-response` sends an order response by the supplier

### Parameters

Most service methods have either path parameters, query parameters and/or a [JSON body](requests.md#JSON-body) or [XML body](requests.md#XML-body)

#### Path parameters

A request can have a path parameter such as an `{id}` in `object-storage` service `download` method:

[`GET /object-storage/download/{id}`](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/object-storage/specs.yaml#/object-storage/download)

#### Query parameters

A GET request can have a query parameter such as a `query` in `company-search`:

[`GET /company-search?query=name`](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/company-search/specs.yaml#/company-search/CompanySearchRoute)

### JSON body
The Tradecloud API supports a proprietary [JSON](standards.md#json) format, called `TSON`:

A POST request has a JSON body \(payload\), such as a purchase order sent to the `api-connector` service `order` method:

[`POST /api-connector/order`](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderByBuyerRoute)

```javascript
{
  "order": {
    "companyId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "supplierAccountNumber": "12345",
    "purchaseOrderNumber": "PO123456789",
    "destination": {
        ...
```

JSON is a standard published as [RFC 8259](https://tools.ietf.org/html/rfc8259) and [ECMA-404](https://www.ecma-international.org/publications/standards/Ecma-404.htm) [\(PDF\)](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-404.pdf)

* JSON text [MUST be encoded using UTF-8](https://tools.ietf.org/html/rfc8259#section-8.1)
* JSON strings: [some characters, like the quote, MUST be escaped](https://tools.ietf.org/html/rfc8259#section-7)
* JSON strings: for date/time values [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) date format `YYYY-MM-DD` or local date/time format `YYYY-MM-DDThh:mm:ss` is used

### XML body

Tradecloud supports [XML](standards.md#xml):

- Following the [tXML standard](json-vs-xml.md) for some `api-connector` and `order-webhook-connector` API endpoints.
- Following the [SCSN Standard](https://smartconnected.semantic-treehouse.nl/#/Standards) for the `sci-connector` API endpoint.

#### tXML

The Tradecloud API supports a proprietary XML format, called `tXML`, which is a 1-on-1 translation of the proprietary `TSON` format:

A POST request has a `tXML` body \(payload\), such as a purchase order sent to the `api-connector` service `order` method:

[`POST /api-connector/order`](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderByBuyerRoute)

```xml
<?xml version="1.0" encoding="UTF-8"?>
<SendOrderByBuyer>
    <companyId>00f03b98-2511-489f-9695-13791b3f66b6</companyId>
    <supplierAccountNumber>12345</supplierAccountNumber>
    <purchaseOrderNumber>PO123456789</purchaseOrderNumber>
    <destination>
       ...
```

* XML text [MUST be encoded using UTF-8](https://tools.ietf.org/html/rfc8259#section-8.1)

#### Isah SCI API

A `sci-connector` POST request has a [SCSN](https://smartconnected.semantic-treehouse.nl/#/Projects) body \(payload\), such as a purchase order sent to the `sci-connector` service `order` method:

[`PUT /sci-connector/order`](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/sci-connector/specs.yaml#/sci-connector/sendOrderByBuyerRoute)

```markup
<?xml version="1.0" encoding="UTF-8"?>
<Order>
    <ID>123</ID>
    <IssueDate>2018-10-06</IssueDate>
    <Note>[Free-form text]</Note>
    <BuyerCustomerParty>
        ...
```

* XML text [MUST be encoded using UTF-8](https://tools.ietf.org/html/rfc8259#section-8.1)
