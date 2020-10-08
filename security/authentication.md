---
description: How to use JSON Web Tokens
---

# Authentication

The API supports the "Basic" HTTP authentication scheme [RFC 7617](https://tools.ietf.org/html/rfc7617) with or without [JSON Web Tokens](https://jwt.io/) [RFC 7519](https://tools.ietf.org/html/rfc7519)

## Basic Authentication without a token

Use the Basic HTTP Authentication scheme to authenticate against the Tradecloud API Connector.

{% hint style="info" %}
Using Basic Authentication without tokens:

Pro: this is a simple authentication method, supported by all integrations

Con's: 

* The response time is long, average 1 second, up to 3 seconds.
* It is only supported by connectors, not by other services like the object-storage.
{% endhint %}

{% hint style="warning" %}
**Use Basic Authentication without tokens only when you send one order or response occasionally,** **less then 1 per minute.**

**And you do not need other services, like the object-storage, user and company services**

**Or when your integration system does not support** [**JSON Web Tokens**](https://jwt.io/) ****[**RFC 7519**](https://tools.ietf.org/html/rfc7519)\*\*\*\*
{% endhint %}

### Authenticate

Authenticate using an Basic Authorization HTTP header with a base 64 encoded email and password:

```text
// Example request method and URI
POST https://api.accp.tradecloud1.com/v2/api-connector/order
// Request headers:
Authorization: Basic <<Email>:<Password> base64 encoded>
```

When correctly authenticated, the response will return [HTTP status code 200](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes#2xx_success) `OK`

When NOT correctly authenticated, the response will return [HTTP status code 401](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes#4xx_client_errors) `Unauthorized` 

## Basic Authentication with a token

Use the Basic HTTP Authentication scheme to authenticate against the authentication service.

Use the returned token to the authorize against the Tradecloud API Connector and other services.

{% hint style="info" %}
Using Basic Authentication with a token:

Pro's: 

* the response time is short \(except for the initial authentication\), average 200ms
* It is supported by all connectors and services, including the object-storage

Con: this is a complex authentication and authorization method
{% endhint %}

{% hint style="warning" %}
**Use tokens when you send batches of orders or responses**, **more then 1 per minute**

**Or when you need additional services, like the object-storage, user and company services**
{% endhint %}

### Authenticate

Log in using an Basic Authorization HTTP header with a base 64 encoded email and password:

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

When correctly authorized, the response will return [HTTP status code 200](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes#2xx_success) `OK`  

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

When the refresh token is valid, the API will return HTTP status code 200 `OK` and containing a new access token and a new refresh token. Otherwise, the API will return HTTP status code  401 `Unauthorized` 

```text
// Response code:
200
// Response headers:
Set-Authorization: <Access-Token>
Set-Refresh-Token: <Refresh-Token>
```

The refresh token cannot be used once it is expired or a new refresh token is generated.

### Log out

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



