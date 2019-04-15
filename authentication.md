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
[Autentication OpenAPI specification](https://api.accp.tradecloud1.com/v2/authentication/specs.yaml) in yaml format
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

The token will expire after one week. You will to have log in again after expiration.  
The authentication refresh token API is not implemented yet \(ticket [TC-4734](https://tradecloud.atlassian.net/browse/TC-4734)\).



