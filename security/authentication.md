---
description: How to use JSON Web Tokens
---

# Authentication

The API supports the "Basic" HTTP authentication scheme [RFC 7617](https://tools.ietf.org/html/rfc7617) with [JSON Web Tokens](https://jwt.io/) [RFC 7519](https://tools.ietf.org/html/rfc7519)

Single Sign-On using [Oauth 2.0](https://oauth.net/2/) is on the [Tradecloud product road map](https://trello.com/b/CQomIRLJ/tradecloud-product-roadmap) and expected in 2020.

## Log in

Log in using an Basic Authorization HTTP header with a base 64 encoded email and password:

```text
// Request method and URI
GET https://api.accp.tradecloud1.com/v2/authentication/login
// Request headers:
Authorization: Basic <<Email>:<Password> base64 encoded>
```

When correctly authenticated, the response will return 200 and contain access and refresh tokens:

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

## Using the token

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

## Refreshing the token

An access token will **expire after 10 minutes and a refresh token after 24 hours**. When your access token has expired you have to use the refresh token. If your refresh token expires you have to log in again.

You can refresh your access token by placing an HTTP request to `/authentication/refresh`, using   
**only** **the Refresh-Token header.** **Do NOT use the Authorization header**.

```text
// Example request method and URI
GET https://api.accp.tradecloud1.com/v2/authentication/refresh
// Request headers:
Refresh-Token: <Refresh-Token>
```

When the refresh token is valid, the API will return 200 and containing a new access token and a new refresh token. Otherwise, the API will return 401 - "Not authenticated". The refresh token cannot be used once it is expired or a new refresh token is generated.

```text
// Response code:
200
// Response headers:
Set-Authorization: <Access-Token>
Set-Refresh-Token: <Refresh-Token>
```

## Log out

Log out will **invalidate the refresh token immediately**. The access token will expire after 10 minutes.

You can refresh your refresh token by placing an HTTP request to `/authentication/logout`, using   
**only** **the Refresh-Token header.** **Do NOT use the Authorization header**.

```text
// Example request method and URI
POST https://api.accp.tradecloud1.com/v2/authentication/logout
// Request headers:
Refresh-Token: <Refresh-Token>
// no body
```



