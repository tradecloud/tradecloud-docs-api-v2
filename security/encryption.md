---
description: Tradecloud API encryption
---

# Connection Encryption

Tradecloud API uses encryption to secure your connection to the API on two levels:

## Transport Layer Security

The Tradecloud API only supports [Hypertext Transfer Protocol Secure \(HTTPS\)](https://en.wikipedia.org/wiki/HTTPS) and does not support plain HTTP.

The Tradecloud SSL certificate only supports the [Transport Layer Security \(TLS\) v1.2](https://en.wikipedia.org/wiki/Transport_Layer_Security#TLS_1.2) protocol and does not support SSL 2 or 3, TLS v1 or v1.1 protocols.

Check the quality of the Tradecloud certificate using [SSL Labs](https://www.ssllabs.com/ssltest/analyze.html?d=api.accp.tradecloud1.com&latest).

## Encrypted and hashed tokens

The Tradecloud API uses hashed [JSON Web Tokens](https://jwt.io/) therefore the token can only be compromised.

