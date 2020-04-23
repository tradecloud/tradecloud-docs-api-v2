---
description: How to use JSON Web Tokens
---

# Authentication

The API supports the "Basic" HTTP authentication scheme [RFC 7617](https://tools.ietf.org/html/rfc7617) with [JSON Web Tokens](https://jwt.io/) [RFC 7519](https://tools.ietf.org/html/rfc7519)

Single Sign-On using [Oauth 2.0](https://oauth.net/2/) is on the [Tradecloud product road map](https://trello.com/b/CQomIRLJ/tradecloud-product-roadmap) and expected in 2020.

## Getting a token

Log in using an Basic Authorization HTTP header with a base 64 encoded email and password:

```text
// Request method and URI
GET https://api.accp.tradecloud1.com/v2/authentication/login
// Request headers:
Authorization: Basic <<Email>:<Password> base64 encoded>
```

When correctly authenticated, the response will return 200 and contain a token and a refresh token:

```text
// Response code:
200
// Response headers:
Set-Authorization: <Access-Token>
Set-Refresh-Token: <Refresh-Token>
```

{% hint style="info" %}
[Authentication OpenAPI specification](https://api.accp.tradecloud1.com/v2/authentication/specs.yaml) in yaml format
{% endhint %}

## Using a token

Use a Bearer Authorization HTTP header with the access token in each request:

```text
// Example request method and URI
GET https://api.accp.tradecloud1.com/v2/user?email=<Email>
// Request headers:
Authorization: Bearer <Access-Token>
```

When correctly authenticated, the response will return 200 and in this example some user info.

```text
// Response code:
200
// Response body:
{
    "id": "<uuid>",
    "email": "<Email>",
    "firstName": "First name",
    "lastName": "Last name",
    ...
}
```

## Refreshing a token

An access token will expire after 10 minutes and a refresh token after 24 hours. When your access token expires you have either to log in again or use the refresh token. If your refresh token expires you have to log in again.

You can refresh your access token by placing an HTTP request to `/authentication/refresh`, using the Refresh-Token header:

```text
// Example request method and URI
GET https://api.accp.tradecloud1.com/v2/authentication/refresh
// Request headers:
Refresh-Token: <Refresh-Token>
```

When the refresh token is valid, the API will return 200 and containing a new access token and a new refresh token. Otherwise, the API will return 401 - "Not authenticated". Refresh token cannot be used once it is expired or a new refresh token is generated.

```text
// Response code:
200
// Response headers:
Set-Authorization: <Access-Token>
Set-Refresh-Token: <Refresh-Token>
```

In addition, consider the following:

* If you place a request to `/refresh` providing a valid access token in the Authorization header, the API will return 200 - OK, without a new token pair. This is regardless of whether you provided a valid refresh token or not. 
* If you place a request to `/refresh` providing a corrupted access token in the Authorization header, the API will always return 401 - Not authenticated. This is regardless of whether you provided a valid refresh token or not.

