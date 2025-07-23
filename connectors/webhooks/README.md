---
description: >-
  Real-time webhook notifications for orders, shipments, and documents. 
  Tradecloud triggers your webhook when events occur, eliminating the need for polling.
---

# Webhook Connector

The Webhook Connector enables real-time push notifications from Tradecloud to your systems. When orders, shipments, or documents are created or updated, Tradecloud automatically triggers your webhook endpoint with the relevant event data.

## How It Works

Tradecloud sends HTTP `POST` requests to your webhook endpoint containing:

- **Order Events** - New orders, updates, status changes
- **Shipment Events** - Despatch advice, delivery updates  
- **Document Events** - Attached files and documentation

### Event Formats

Choose between two data formats for your webhook:

- **JSON** - Standard REST API format for modern integrations
- **tXML** - Structured XML format for legacy systems

### Document Handling

Document events contain a `objectId` reference rather than embedded content. Use the [document download API](https://docs.tradecloud1.com/api/processes/order/buyer/receive/download-document) to retrieve the actual file content when processing document events.

## Benefits

- **Real-time delivery** - Events arrive within seconds of occurrence
- **Filtered events** - Receive only the events relevant to your business process
- **Reliable delivery** - Automatic retry with exponential backoff for failed requests
- **Secure transmission** - HTTPS-only with authentication support

## Implementation Requirements

Your webhook endpoint must support:

- **HTTPS with valid SSL certificate** (TLS 1.2 or 1.3)
- **POST method** with JSON or tXML request body parsing
- **Authentication** (Basic Auth, Bearer Token, or OAuth 2.0)
- **HTTP status codes** for proper response handling

## Quick Start

1. **[Set up your webhook endpoint](webhook-setup.md)** - Technical implementation requirements
2. **[Configure in Tradecloud portal](portal-setup.md)** - Enable events and authentication
3. **Test integration** - Validate event processing in acceptance environment
