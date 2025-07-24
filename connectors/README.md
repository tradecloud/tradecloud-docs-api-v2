# Connectors

Tradecloud provides several connector types that complement the standard API integration, offering alternative methods for data exchange and authentication to meet diverse integration requirements.

## Overview

These connectors are **additions to the API connector**, providing specialized integration patterns:

- **Real-time push messaging** through webhook connectors
- **File-based integration** through FTP connectors  
- **Single Sign-On authentication** through Azure Active Directory

## Connector Types

### 🔗 Webhook Connector

The [webhook connectors](webhooks/README.md) work **alongside the API** to push real-time messages to your systems when orders, shipments, or documents are created or updated, eliminating the need for continuous polling.

**Key Features:**

- Real-time order and shipment event notifications
- Push-based messaging (no polling required)
- Support for both JSON and XML formats
- Filtered event delivery based on your requirements
- Works alongside API calls for complete integration

**Best for:** High-volume, real-time integrations with existing web infrastructure.

For choosing between webhook and polling approaches, see: [Webhook vs Polling](../api/webhook-vs-polling.md)

### 📁 FTP Connectors

The [FTP Connectors](ftp/README.md) provide file-based integration using secure SFTP protocols, supporting structured data formats for batch processing scenarios.

**Available FTP Connectors:**

- **CSV FTP Connector** - For comma-separated value file exchange
- **EDIFACT FTP Connector** - For UN/EDIFACT standard message format

**Key Features:**

- Secure SFTP file transfer
- Bidirectional file exchange (upload/download)
- Automatic file archiving
- Support for batch processing workflows

**Best for:** Legacy systems, batch processing, and environments requiring file-based integration.

### 🔐 Azure Active Directory Connector

The [Azure AD Connector](azure-ad/README.md) provides Single Sign-On (SSO) integration, allowing your organization's users to access Tradecloud using their existing corporate credentials.

**Key Features:**

- Single Sign-On with Azure AD credentials
- Automatic user provisioning
- Centralized access control through Azure AD policies
- Enhanced security with existing organizational policies like multi-factor authentication
- Reduced IT management overhead

**Best for:** Organizations using Microsoft Azure AD for identity management and requiring SSO capabilities.
