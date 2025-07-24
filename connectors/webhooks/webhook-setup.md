---
description: Technical requirements and implementation guide for webhook endpoints
---

# Webhook Endpoint Setup

This guide covers the technical requirements for implementing your webhook endpoint to receive real-time events from Tradecloud.

## Technical Requirements

### Infrastructure Requirements

Your webhook endpoint must meet these mandatory requirements:

| Requirement | Details |
|-------------|---------|
| **Protocol** | HTTPS only (HTTP not supported) |
| **TLS Version** | TLS 1.2 or 1.3 minimum |
| **SSL Certificate** | Valid certificate from recognized CA (no self-signed) |
| **HTTP Method** | POST method support |
| **Content Types** | JSON and/or tXML parsing capability |
| **Internet Access** | Publicly accessible from Tradecloud servers |

{% hint style="info" %}
**Certificate Validation**: Test your SSL configuration at [SSL Labs](https://www.ssllabs.com/ssltest/) to ensure compatibility.
{% endhint %}

### Authentication Support

Your webhook must implement **one** of these authentication methods:

#### Basic Authentication

- **Standard**: [RFC 7617](https://datatracker.ietf.org/doc/html/rfc7617)
- **Header**: `Authorization: Basic <base64(username:password)>`
- **Use Case**: Simple integrations with static credentials

#### Bearer Token

- **Standard**: [RFC 6750](https://datatracker.ietf.org/doc/html/rfc6750)  
- **Header**: `Authorization: Bearer <token>`
- **Use Case**: API key-based authentication

#### OAuth 2.0 Client Credentials

- **Standard**: [RFC 6749](https://datatracker.ietf.org/doc/html/rfc6749#section-4.4)
- **Grant Type**: `client_credentials`
- **Use Case**: Enterprise integrations with token refresh

## Webhook Implementation

### Order Events

Implement the [Order Webhook API](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-connector/specs.yaml#/order-webhook%20endpoints/webhookPost) to receive order-related events.

**Event Types Available:**

- `orderEvent` - Multi-delivery order lines (delivery schedule mode)
- `singleDeliveryOrderEvent` - Single delivery per order line  
- `orderDocumentsEvent` - Document attachments and updates

{% hint style="warning" %}
**Important**: Order events contain **only the affected order lines**, not the complete order. Process incrementally based on the event data.
{% endhint %}

### Shipment Events

Implement the [Shipment Webhook API](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/shipment-webhook-connector/specs.yaml#/shipment-webhook%20endpoints/webhookPost) to receive shipment notifications.

**Event Characteristics:**

- Contains **all shipment lines and documents**  
- Filter changes using `lastUpdatedAt` timestamps
- Process documents via download API when needed

{% hint style="warning" %}
**Performance Tip**: Use `lastUpdatedAt` fields to identify new or changed items rather than processing the entire shipment.
{% endhint %}

### Document Processing

When receiving document events:

1. **Extract Document ID** - Get `objectId` from the event
2. **Download Content** - Use appropriate download API:
   - [Order documents](https://docs.tradecloud1.com/api/processes/order/buyer/receive/download-document)
   - [Shipment documents](https://docs.tradecloud1.com/api/processes/shipment/buyer/receive/download-document)
3. **Process File** - Handle the downloaded content in your system

## Response Handling

Your webhook must return appropriate HTTP status codes:

| Status Code | Meaning | Tradecloud Action |
|-------------|---------|-------------------|
| **2xx**  | Success | Event marked as delivered |
| **4xx**  | Client Error | No retry |
| **500**  | Server Error | No retry |
| **>500** | Server Error | Retry with exponential backoff |

### Recommended Response Codes

- `200 OK` - Event processed successfully
- `202 Accepted` - Event queued for processing  
- `400 Bad Request` - Invalid event data
- `401 Unauthorized` - Authentication failed
- `500 Internal Server Error` - Event processing error
- `502 Bad Gateway` - upstream ERP system temporary unavailability
- `503 Service Unavailable` - Temporary unavailability

## Testing Your Webhook

### Development Testing

Use [webhook.site](https://webhook.site) for initial testing and payload inspection.

## Next Steps

Once your webhook endpoint is implemented:

**[Configure webhook settings](portal-setup.md)** in the Tradecloud portal to enable event delivery.
