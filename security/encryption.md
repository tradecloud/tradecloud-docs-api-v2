---
description: Tradecloud API encryption
---

# Encryption

Tradecloud API uses encryption on two levels:

## Transport Layer Security

The Tradecloud API only support [Hypertext Transfer Protocol Secure (HTTPS)](https://en.wikipedia.org/wiki/HTTPS) and does not support plain HTTP.

The quality of the Tradecloud Certificates can be checked using [SSL Labs](https://www.ssllabs.com/ssltest/analyze.html?d=api.accp.tradecloud1.com&latest)

## Encrypted and hashed tokens

The Tradecloud API uses encrypted and hashed [JSON Web Tokens](https://jwt.io/) therefor the token cannot be read or updated.
