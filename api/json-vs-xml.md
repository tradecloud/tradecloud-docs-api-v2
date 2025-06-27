---
description: >-
  Choose between JSON and XML formats in the Tradecloud API. Learn about format support, when to use each, and how to implement both JSON and tXML formats.
---

# JSON versus XML

The Tradecloud API supports both JSON and XML formats to support different integration requirements. This guide explains how to choose the appropriate format for your implementation.

## Overview

The Tradecloud API provides two data formats:

- **JSON**: The default format for all API endpoints
- **tXML**: A proprietary XML format available for specific endpoints

Both formats contain identical data structures and functionality - tXML is a one-to-one mapping of the JSON format.

## When to use each format

### Use JSON when

- Building new modern integrations
- Implementing REST API clients

### Use tXML when

- Integrating with ERP systems that require XML
- Working with enterprise middleware that requires XML

## JSON Format

JSON is the **default and recommended format** for all Tradecloud API endpoints.

### Implementation

All API endpoints support JSON by default. Simply use `Content-Type: application/json` in your HTTP headers.

For detailed JSON structure and examples, see the [JSON body format documentation](requests.md#json-body).

## tXML Format

tXML (Tradecloud XML) is a proprietary XML format that provides the same functionality as JSON but in XML structure.

### Supported Endpoints

The following API endpoints support tXML format:

#### Buyer Endpoints

- [Send order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderByBuyerRoute)
- [Send single delivery order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendSingleDeliveryOrderByBuyerRoute)

#### Supplier Endpoints

- [Send order response](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/supplier-endpoints/sendOrderResponseBySupplierRoute)

#### Webhook Endpoints

- [Order Webhook](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order-webhook-connector/specs.yaml#/order-webhook%20endpoints/webhookPost)

### Implementation

To use tXML format, set the `Content-Type` header to `application/xml` in your HTTP requests.

For detailed tXML structure and examples, see the [XML body format documentation](requests.md#xml-body).

#### Viewing tXML Examples

You can view tXML examples in the Swagger UI documentation:

1. Open the endpoint in Swagger UI
2. In the "Parameter content type" dropdown, select "application/xml"
3. The "Example Value" section will show the tXML structure

## Getting Additional tXML Support

If you need tXML support for additional API endpoints not currently listed, please contact [Tradecloud support](../support.md) with your specific requirements.

## Next Steps

- Review the [API request formats](requests.md) for detailed implementation examples
- Explore the [Swagger UI documentation](tools/swagger-ui.md) for interactive API testing
- Check the [Postman collection](tools/postman.md) for ready-to-use API examples
