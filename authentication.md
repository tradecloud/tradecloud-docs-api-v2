---
description: How to use JSON Web Tokens
---

# Authentication

## Getting a token

Log in using an Basic Authorization  HTTP header with a base 64 encoded email and password:

```text
// Request method and URI
GET https://api.accp.tradecloud1.com/v2/authentication/_login
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

Use a Bearer Authorization HTTP header with the Access Token in each request:

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
// Reponse body:
{
    "id": "<uuid>",
    "email": "<Email>",
    "firstName": "First name",
    "lastName": "Last name",
    ...
}
```

## Refreshing a token

An access token will expire after 1 hour, a refresh token after 24 hours.
When your access token expires you have either to log in again or use the refresh token.
If your refresh token expires you have to log in again.

You can refresh your access token by placing an HTTP request to `/authentication/_refresh`, using the Refresh-Token header:

```text
// Example request method and URI
GET https://api.accp.tradecloud1.com/v2/authentication/_refresh
// Request headers:
Refresh-Token: <Refresh-Token>
```

When the refresh token is valid, the API will return 200 and contain a new token pair, containing a new access token and a new refresh token. 
Otherwise, the API will return 401 - "Not authenticated".
Refresh token cannot be used once it is expired or a new refresh token is generated.

```text
// Response code:
200
// Response headers:
Set-Authorization: <Access-Token>
Set-Refresh-Token: <Refresh-Token>
```

In addition, consider the following:
1) If you place a request to  `/_refresh` providing a valid access token in the Authorization header, the API will return 200 - OK, without a new token pair. This is regardless of whether you provided a valid refresh token or not.
2) If you place a request to `/_refresh` providing a corrupted access token in the Authorization header, the API will always return 401 - Not authenticated. This is regardless of whether you provided a valid refresh token or not.
