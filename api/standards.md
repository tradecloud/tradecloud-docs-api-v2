---
description: Overview of standards used by the Tradecloud API
---

# Standards

{% hint style="danger" %}
Your integration **must support** these standards.
{% endhint %}

## Basic HTTP authentication

The [Basic HTTP authentication](https://en.wikipedia.org/wiki/Basic_access_authentication) scheme, which transmits credentials as user-id/password pairs, encoded using Base64.

Published as [RFC 7617](https://tools.ietf.org/html/rfc7617)

## HTTP 1.1 and 2.0

The [Hypertext Transfer Protocol](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) is a stateless application-level protocol for distributed, collaborative, hypertext information systems.

HTTP 1.1. is published as [RFC 7230](https://tools.ietf.org/html/rfc7230) and RFC 7231 to 7237.

HTTP 2.0 is published as [RFC 7540](https://tools.ietf.org/html/rfc7540)

## ISO Date/Time

Date/time values use [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) date format `YYYY-MM-DD` or local date/time format `YYYY-MM-DDThh:mm:ss`

Published as [ISO 8601-1:2019](https://www.iso.org/standard/70907.htm)

## JSON

JavaScript Object Notation is a lightweight, text-based, language-independent data interchange format.

Published as [RFC 8259](https://tools.ietf.org/html/rfc8259) and [ECMA-404](https://www.ecma-international.org/publications/standards/Ecma-404.htm) [\(PDF\)](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-404.pdf)

{% hint style="warning" %}
The JSON syntax does not assign any significance to the **ordering** of name/value pairs.

Therefor **XML** based transformations **expecting ordering** will break.
{% endhint %}

## JWT

[JSON Web Tokens](https://jwt.io/) are an open, industry standard [RFC 7519](https://tools.ietf.org/html/rfc7519) method for representing claims securely between two parties.

## Media Types

Tradecloud supports a sub set of the [RFC 6838 Media Type Specifications](https://tools.ietf.org/html/rfc6838).

{% page-ref page="/security/media-types.md" %}

## OpenAPI

The [OpenAPI Version 2.0 Specification \(OAS 2.0\)](https://swagger.io/specification/v2/) creates a RESTful interface for easily developing and consuming an API by effectively mapping all the resources and operations associated with it.

## REST

[Representational state transfer \(REST\)](https://en.wikipedia.org/wiki/Representational_state_transfer%20) is not a standard but a software architectural style that defines a set of constraints to be used for creating Web services. The Tradecloud API additionally uses a command and query style.

## TLS v1.2

[Transport Layer Security](https://en.wikipedia.org/wiki/Transport_Layer_Security) is a cryptographic protocol designed to provide communications security over a computer network. 

{% hint style="warning" %}
The Tradecloud API only supports [TLS v1.2](https://en.wikipedia.org/wiki/Transport_Layer_Security#TLS_1.2) published as [RFC 5246](https://tools.ietf.org/html/rfc5246).
{% endhint %}

## URI

A Uniform Resource Identifier \(URI\) is a compact sequence of characters that identifies an abstract or physical resource. 

Published as [RFC 3986](https://tools.ietf.org/html/rfc3986) with [errata](https://www.rfc-editor.org/errata_search.php?rfc=3986).

{% hint style="warning" %}
[URLs](https://www.w3schools.com/tags/ref_urlencode.ASP) can only be sent over the Internet using the [ASCII character-set](https://www.w3schools.com/charsets/ref_html_ascii.asp). 

Since URLs often contain characters outside the ASCII set, the URL has to be converted into a valid ASCII format. URL encoding replaces unsafe ASCII characters with a "%" followed by two hexadecimal digits. URLs cannot contain spaces. URL encoding normally replaces a space with a plus \(+\) sign or with %20.
{% endhint %}

## UTF-8

ISO/IEC 10646-1 defines a large character set called the Universal Character Set \(UCS\) which encompasses most of the world's writing systems. The originally proposed encodings of the UCS, however, were not compatible with many current applications and protocols, and this has led to the development of UTF-8

Published as [RFC 9259](https://tools.ietf.org/html/rfc8259#section-8.1)
