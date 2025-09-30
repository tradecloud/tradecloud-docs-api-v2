---
description: 'Custom CSV file integration using RFC 4180 format over secure FTP'
---

# CSV SFTP Connector

The CSV SFTP Connector enables flexible data exchange using custom CSV (Comma-Separated Values) formats, ideal for organizations with specific data structure requirements or legacy systems that work best with tabular data.

## Overview

Perfect for businesses that need:

- **Custom data formats** tailored to existing ERP systems
- **Spreadsheet-compatible** files for manual processing
- **Flexible field mapping** to match internal data structures
- **Simple integration** with minimal technical overhead

## Technical Specifications

| Specification | Details |
|---------------|---------|
| **Data Format** | [RFC 4180](https://tools.ietf.org/html/rfc4180) Compliant CSV |
| **Character Encoding** | UTF-8 |
| **Field Delimiter** | Comma (`,`) |
| **Text Qualifier** | Double quote (`"`) |
| **Line Terminator** | CRLF (`\r\n`) |

## Supported Message Types

The CSV connector supports all core business documents:

- **Orders** - Purchase orders and order updates
- **Order Responses** - Supplier confirmations and modifications  
- **Despatch Advice** - Shipment notifications with tracking details
- **Receipt Advice** - Goods receipt confirmations from buyers

## Custom Implementation

Each CSV implementation is **custom-designed** to match your specific:

- Field requirements and naming conventions
- Data validation rules and formats
- Business logic and workflow needs
- Integration with existing systems

## Connection Details

- **Transport Protocol**: [SFTP](https://datatracker.ietf.org/doc/html/draft-ietf-secsh-filexfer-13) (SSH File Transfer Protocol)
- **Server Location**: Tradecloud-hosted secure SFTP server
- **Client Requirements**: SFTP client software and outbound internet access
- **Security**: Encryption for all file transfers

## Availability

The CSV FTP Connector is available through our partner **Supplydrive**, who provides:

- Custom CSV format design and mapping
- Implementation and testing support  
- Ongoing maintenance and support
- Integration expertise and best practices

## Getting Started

1. **Assess Requirements** - Identify your CSV format needs and data structure
2. **Contact Partner** - Reach out to Supplydrive for custom implementation
3. **Design Format** - Collaborate on CSV field mapping and validation rules
4. **Test Integration** - Validate data flow in acceptance environment
5. **Go Live** - Deploy to production with monitoring and support
