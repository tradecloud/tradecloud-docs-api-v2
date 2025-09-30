---
description: 'UN/EDIFACT D.96A standard messaging over secure FTP for supply chain integration'
---

# EDIFACT SFTP Connector

The EDIFACT SFTP Connector provides standardized Electronic Data Interchange (EDI) messaging using the internationally recognized UN/EDIFACT D.96A format, ensuring seamless interoperability with trading partners worldwide.

## Overview

Ideal for organizations that require:

- **Industry-standard EDI** messaging for supply chain automation
- **Global interoperability** with international trading partners
- **Structured data exchange** with built-in validation
- **Regulatory compliance** for industries requiring EDI standards

## Technical Specifications

| Specification | Details |
|---------------|---------|
| **EDI Standard** | [UN/EDIFACT D.96A](https://unece.org/DAM/trade/untdid/d96a/d96a.zip) |
| **Character Set** | UNOC (ISO 8859-1) |
| **Transport Protocol** | [SFTP](https://datatracker.ietf.org/doc/html/draft-ietf-secsh-filexfer-13) |
| **File Format** | Plain text with EDI segments |

## Supported Message Types

The EDIFACT connector supports essential supply chain documents:

| Message Type | EDI Code | Purpose |
|--------------|----------|---------|
| **Purchase Orders** | `ORDERS` | New purchase orders and requirements |
| **Order Changes** | `ORDCHG` | Modifications to existing orders |
| **Order Responses** | `ORDRSP` | Supplier confirmations and acknowledgments |
| **Despatch Advice** | `DESADV` | Shipment notifications and ASNs |
| **Receipt Advice** | `RECADV` | Goods receipt confirmations |

## Standards Compliance

All messages comply with UN/EDIFACT D.96A specifications:

- **Message structure** follows standard segment definitions
- **Data elements** use standard codes and formats  
- **Validation rules** ensure data integrity and compliance
- **Documentation** available in [official UN/EDIFACT D.96A package](https://unece.org/DAM/trade/untdid/d96a/d96a.zip)

## Connection Details

- **Transport Protocol**: SFTP (SSH File Transfer Protocol) for secure transmission
- **Server Location**: Tradecloud-hosted secure SFTP environment
- **Client Requirements**: EDI-capable system and SFTP client
- **Security**: End-to-end encryption with authentication

## Availability

The EDIFACT FTP Connector is available through our partner **Supplydrive**, providing:

- **Implementation expertise** for UN/EDIFACT D.96A standard
- **Message mapping and validation** services
- **Testing** support
- **Ongoing maintenance** and technical support

## Getting Started

1. **Evaluate Readiness** - Assess your EDI requirements and system capabilities
2. **Partner Consultation** - Contact Supplydrive for implementation planning
3. **Message Design** - Configure EDIFACT message types and trading partner setup
4. **Testing Phase** - Validate message exchange in acceptance environment  
5. **Production Deployment** - Go live with monitoring and ongoing support
