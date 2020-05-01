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

Use the `Content-Type: application/json` header in case of `POST` or `PUT` with a JSON body

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
* `order-integration` for buyer and supplier ERP integration
* `object-storage` to upload and download documents
* `order` for order/line commands
* `order-search` for order queries
* `order-line-search` for order-line queries

### Methods

In each [OpenAPI 2.0 Specification](https://swagger.io/specification/v2/) you can find the methods supported by the service. For example the [`order-integration`](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-integration/specs.yaml#/order-integration/sendOrderByBuyerRoute) service:

`POST /order-integration/order` [sends an order by the buyer](../buyer/issue/)

`POST /order-integration/order-response` sends an order response by the supplier

### Parameters

Most service methods have either path parameters, query parameters and/or a [JSON body](requests.md#JSON-body)

#### Path parameters

A request can have a path parameter such as an `{id}` in `object-storage` service `download` method:

[`GET /object-storage/download/{id}`](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/object-storage/specs.yaml#/object-storage/download)

#### Query parameters

A GET request can have a query parameter such as a `query` in `company-search`:

[`GET /company-search?query=name`](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/company-search/specs.yaml#/company-search/CompanySearchRoute)

### JSON body

A POST request has a [JSON](requests.md#json) body \(payload\) such as a purchase order in `order-integration` service `order` method:

[`POST /order-integration/order`](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-integration/specs.yaml#/order-integration/sendOrderByBuyerRoute)

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

