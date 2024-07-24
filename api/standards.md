---
description: Overview of standards used by the Tradecloud API and webhooks
---

# Standards

{% hint style="danger" %}
Your integration **must support** these standards.
{% endhint %}

## Basic authentication

[Basic authentication](https://swagger.io/docs/specification/authentication/basic-authentication/) is a simple HTTP authentication scheme built into the HTTP protocol. The client sends HTTPS requests with the Authorization header that contains the word `Basic` followed by a space and a base64-encoded string username:password

Published as [RFC 7617 "The 'Basic' HTTP Authentication Scheme"](https://datatracker.ietf.org/doc/html/rfc7617)

Basic authentication is supported by both the API v2.0 and webhooks.

## Bearer authentication

[Bearer authentication](https://swagger.io/docs/specification/authentication/bearer-authentication/) is an HTTP authentication scheme that involves security tokens called bearer tokens. The client send HTTPS requests with the `Authorization` header that contains the word `Bearer` followed by a space and the token.

Published as [RFC 6750 "The OAuth 2.0 Authorization Framework: Bearer Token Usage"](https://datatracker.ietf.org/doc/html/rfc6750)

The bearer token is supported as part of [JWT](#jwt) by the API v2.0.

The bearer token is supported as part of [OAuth](#oauth) and as static token by the webhooks.

## HTTP 1.1 and 2.0

The [Hypertext Transfer Protocol](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) is a stateless application-level protocol for distributed, collaborative, hypertext information systems.

HTTP 1.1. is published as [RFC 7230](https://datatracker.ietf.org/doc/html/rfc7230) and RFC 7231 to 7237.

HTTP 2.0 is published as [RFC 7540](https://datatracker.ietf.org/doc/html/rfc7540)

## ISO Date/Time

Date/time values use [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) date format `YYYY-MM-DD` or local date/time format `YYYY-MM-DDThh:mm:ss`

Published as [ISO 8601-1:2019](https://www.iso.org/standard/70907.htm)

## JSON

Tradecloud supports JSON and [XML](#xml). JavaScript Object Notation (JSON) is a lightweight, text-based, language-independent data interchange format.

Published as [RFC 8259](https://datatracker.ietf.org/doc/html/rfc8259) and [ECMA-404](https://www.ecma-international.org/publications/standards/Ecma-404.htm) [\(PDF\)](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-404.pdf)

{% hint style="warning" %}
The JSON syntax does not assign any significance to the **ordering** of name/value pairs.

Therefor **XML** based transformations **expecting ordering** will break.
{% endhint %}

{% hint style="warning" %}
The Tradecloud [compatibility rules](compatibility.md) apply to the JSON usage.
{% endhint %}

## JWT

[JSON Web Tokens](https://jwt.io/) are an open, industry standard [RFC 7519](https://datatracker.ietf.org/doc/html/rfc7519) method for representing claims securely between two parties.

JWT is supported by the API v2 only (and not by the webhooks).

## Media Types

Tradecloud supports a sub set of the [RFC 6838 Media Type Specifications](https://datatracker.ietf.org/doc/html/rfc6838).

## OAuth

[OAuth 2.0](https://swagger.io/docs/specification/authentication/oauth2/) is an authorization protocol that gives an API client limited access to user data on a web server. OAuth relies on authentication scenarios called flows, which allow the resource owner (user) to share the protected content from the resource server without sharing their credentials. For that purpose, an OAuth 2.0 server issues access tokens that the client applications can use to access protected resources on behalf of the resource owner.

Published as [RFC 6749 "The OAuth 2.0 Authorization Framework"](https://datatracker.ietf.org/doc/html/rfc6749)

The [Oauth 2.0 Client Credentials Grant](https://datatracker.ietf.org/doc/html/rfc6749#section-4.4) is supported by the order webhooks only (and not by the API v2 or shipment webhook at this moment).

## OpenAPI

The [OpenAPI Version 2.0 Specification \(OAS 2.0\)](https://swagger.io/specification/v2/) creates a RESTful interface for easily developing and consuming an API by effectively mapping all the resources and operations associated with it.

## REST

[Representational state transfer \(REST\)](https://en.wikipedia.org/wiki/Representational_state_transfer%20) is not a standard but a software architectural style that defines a set of constraints to be used for creating Web services. The Tradecloud API additionally uses a command and query style.

## TLS v1.2 and v1.3

[Transport Layer Security](https://en.wikipedia.org/wiki/Transport_Layer_Security) is a cryptographic protocol designed to provide communications security over a computer network.

{% hint style="warning" %}
The Tradecloud API only supports [TLS v1.2](https://en.wikipedia.org/wiki/Transport_Layer_Security#TLS_1.2) published as [RFC 5246](https://datatracker.ietf.org/doc/html/rfc5246) and [TLS v1.3](https://en.wikipedia.org/wiki/Transport_Layer_Security#TLS_1.3) published as [RFC 8446](https://datatracker.ietf.org/doc/html/rfc8446)
{% endhint %}

## URI

A Uniform Resource Identifier \(URI\) is a compact sequence of characters that identifies an abstract or physical resource.

Published as [RFC 3986](https://datatracker.ietf.org/doc/html/rfc3986) with [errata](https://www.rfc-editor.org/errata_search.php?rfc=3986).

{% hint style="warning" %}
[URLs](https://www.w3schools.com/tags/ref_urlencode.ASP) can only be sent over the Internet using the [ASCII character-set](https://www.w3schools.com/charsets/ref_html_ascii.asp).

Since URLs often contain characters outside the ASCII set, the URL has to be converted into a valid ASCII format. URL encoding replaces unsafe ASCII characters with a "%" followed by two hexadecimal digits. URLs cannot contain spaces. URL encoding normally replaces a space with a plus \(+\) sign or with %20.
{% endhint %}

## UTF-8

ISO/IEC 10646-1 defines a large character set called the Universal Character Set \(UCS\) which encompasses most of the world's writing systems. The originally proposed encodings of the UCS, however, were not compatible with many current applications and protocols, and this has led to the development of UTF-8

Published as [RFC 9259](https://datatracker.ietf.org/doc/html/rfc8259#section-8.1)

## XML

Tradecloud supports XML and [JSON](#json). The [Extensible Markup Language](https://en.wikipedia.org/wiki/XML) its main purpose is serialization, i.e. transmitting arbitrary data.

Published as [Extensible Markup Language (XML) 1.0 (Fifth Edition)](https://www.w3.org/TR/REC-xml/)

{% hint style="warning" %}
Tradecloud does not assign any significance to the **ordering** of XML tags.

Therefor **XML** based transformations **expecting ordering** will break.
{% endhint %}

{% hint style="warning" %}
The Tradecloud [compatibility rules](compatibility.md) apply to the XML usage.
{% endhint %}
