---
description: How to use JSON Web Tokens
---

# Authentication

## Getting a token

Log in using an Basic Authorization  HTTP header with a base 64 encoded email and password:

```
// Request method and URI
GET https://api.accp.tradecloud1.com/v2/authentication/_login
// Request headers:
Authorization: Basic <<Email>:<Password> base64 encoded>
```

When correctly authenticated, the response will return 200 and contain a token and a refresh token:

```
// Response code:
200 
// Response headers:
Set-Authorization: <Token>
Set-Refresh-Token: <Refresh-Token>
```

{% hint style="info" %}
[Authentication OpenAPI specification](https://api.accp.tradecloud1.com/v2/authentication/specs.yaml) in yaml format
{% endhint %}

##  Using a token

Use a Bearer Authorization HTTP header with the Token in each request:

```text
// Example request method and URI
GET https://api.accp.tradecloud1.com/v2/user?email=<Email>
// Request headers:
Authorization: Bearer <Token>
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

Access token will expire after 1 hour, refresh token after 24 hours.
If access token expires you have either to log in again or use the refresh token.
If refresh token expires you have to log in again.

To refresh token:
Make http call to `/refresh` endpoint using Refresh-Token header:
```text
// Example request method and URI
GET https://api.accp.tradecloud1.com/v2/authentication/_refresh
// Request headers:
Refresh-Token: <Refresh-Token>
```

When refresh token is valid, the response will return 200 and contain new token pairs, otherwise you will get 401 "Not authenticated".
The old ones are discarded and cannot be used any more.

```
// Response code:
200 
// Response headers:
Set-Authorization: <Token>
Set-Refresh-Token: <Refresh-Token>
```
Also there are some special cases:
1) If you call `/refresh` providing valid token in Authorization header you will get 200 OK without new access/refresh tokens, regardless you provide Refresh-Token
2) If you call `/refresh` providing corrupted token in Authorization header, you will always get 401 even if Refresh-Token is valid.  





