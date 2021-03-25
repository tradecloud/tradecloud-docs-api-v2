---
description: How to use JSON Web Tokens
---

# Authentication

The API supports 2 means of authentication:

* Using "Basic" HTTP authentication scheme \([RFC 7617](https://tools.ietf.org/html/rfc7617)\) upon every HTTP request.
* Using "Basic" HTTP authentication scheme \([RFC 7617](https://tools.ietf.org/html/rfc7617)\) to obtain a [JSON Web Token](https://jwt.io/) \([RFC 7519](https://tools.ietf.org/html/rfc7519)\). The JWT is used for authentication for all following requests.

## Basic Authentication upon every request

You can use the Basic HTTP Authentication scheme to authenticate against the Tradecloud API Connector upon every request.

{% hint style="info" %}
Pro: this is a simple authentication method, supported by all integrations

Con's:

* The response time is long, average 1 second, up to 3 seconds.
* It is only supported by connectors, not by other services like the object-storage.
{% endhint %}

{% hint style="warning" %}
**Use Basic Authentication upon every request only when**:

* You send one order or response occasionally; less then 1 per minute.
* You do not need to integrate with other services, like the object-storage, user and company services
* Or when your integration system does not support [**JSON Web Tokens**](https://jwt.io/) \([RFC 7519](https://tools.ietf.org/html/rfc7519)\)
{% endhint %}

### How to Authenticate

You can authenticate using a Basic Authorization HTTP header with a base 64 encoded email and password:

```text
// Example request method and URI
POST https://api.accp.tradecloud1.com/v2/api-connector/order
// Request headers:
Authorization: Basic <<Email>:<Password> base64 encoded>
```

When correctly authenticated, your request will be processed and if all is well, the response will have [HTTP status code 200](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes#2xx_success) `OK`

When NOT correctly authenticated, the response will return [HTTP status code 401](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes#4xx_client_errors) `Unauthorized`

In case of some server issue, including the upstream authentication service being unreachable,  
the response will return [HTTP status code 500](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes#5xx_server_errors) `Internal Server Error`

## Basic Authentication with JSON Web Tokens

1. Use the Basic HTTP Authentication scheme to **authenticate** against the authentication service.
2. Use the returned JWT to **authorize** against the Tradecloud API Connector and other services for all subsequent requests.

{% hint style="info" %}
Pro's:

* Faster response time \(except for the initial authentication\), average 200ms
* It is supported by all connectors and services, including the object-storage

Con: this is a more complex authentication and authorization method
{% endhint %}

{% hint style="warning" %}
**Use JSON Web Tokens when:**

* You send batches of orders or responses; more then 1 per minute
* When you need additional services, like the object-storage, user and company services
{% endhint %}

### Authenticate

You can log in using a Basic Authorization HTTP header with a base 64 encoded email and password:

```text
// Request method and URI
GET https://api.accp.tradecloud1.com/v2/authentication/login
// Request headers:
Authorization: Basic <<Email>:<Password> base64 encoded>
```

When correctly authenticated, the response will return [HTTP status code 200](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes#2xx_success) `OK`  
and contain **access** and **refresh** tokens:

```text
// Response code:
200
// Response headers:
Set-Authorization: <Access-Token>
Set-Refresh-Token: <Refresh-Token>
```

When NOT correctly authenticated, the response will return [HTTP status code 401](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes#4xx_client_errors) `Unauthorized`

{% hint style="info" %}
[Authentication OpenAPI specification](https://api.accp.tradecloud1.com/v2/authentication/specs.yaml) in yaml format
{% endhint %}

### Authorize

Use a Bearer Authorization HTTP header with the access token in each request:

```text
// Example request method and URI
POST https://api.accp.tradecloud1.com/v2/api-connector/order
// Request headers:
Authorization: Bearer <Access-Token>
```

When correctly authenticated, your request will be processed and if all is well, the response will have [HTTP status code 200](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes#2xx_success) `OK`

### Refreshing the token

An access token will **expire after 10 minutes and a refresh token after 24 hours**. When your access token has expired you have to use the refresh token. If your refresh token expires you have to log in again.

You can refresh your access token by placing an HTTP request to `/authentication/refresh`, using  
**only** **the Refresh-Token header.** **Do NOT use the Authorization header**.

```text
// Example request method and URI
GET https://api.accp.tradecloud1.com/v2/authentication/refresh
// Request headers:
Refresh-Token: <Refresh-Token>
```

When the refresh token is valid, the API will return HTTP status code 200 `OK` and containing a new access token and a new refresh token. Otherwise, the API will return HTTP status code 401 `Unauthorized`

```text
// Response code:
200
// Response headers:
Set-Authorization: <Access-Token>
Set-Refresh-Token: <Refresh-Token>
```

The refresh token cannot be used once it is expired or a new refresh token is generated.

## Log out

Log out will **invalidate the refresh token immediately**. The access token will expire after 10 minutes.

You can invalidate your refresh token by placing an HTTP request to `/authentication/logout`, using  
**only** **the Refresh-Token header.** **Do NOT use the Authorization header**.

```text
// Example request method and URI
POST https://api.accp.tradecloud1.com/v2/authentication/logout
// Request headers:
Refresh-Token: <Refresh-Token>
// no body
```

