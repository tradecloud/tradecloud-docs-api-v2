---
description: 'EDIFACT, CSV and custom file formats over secure SFTP server hosted by Tradecloud'
---

# SFTP Connectors

Tradecloud provides secure file-based integration through SFTP connectors, enabling seamless data exchange using industry-standard file formats for organizations that prefer batch processing or have legacy systems.

## Available Connectors

| Connector | Format | Use Case |
|-----------|--------|----------|
| **[CSV SFTP Connector](csv.md)** | RFC 4180 CSV | Custom CSV formats for flexible data exchange |
| **[EDIFACT SFTP Connector](edifact.md)** | UN/EDIFACT D.96A | Standardized EDI messaging for supply chain |

## Connection Details

### Server Information

| Environment | Hostname | Protocol | Port |
|-------------|----------|----------|------|
| **Acceptance** | `ftp.accp.tradecloud1.com` | SFTP | 22 |
| **Production** | `ftp.tradecloud1.com` | SFTP | 22 |

### Security & Access

- **Protocol**: SFTP (SSH File Transfer Protocol) only
- **Authentication**: Username/password provided by Tradecloud support
- **Encryption**: All data transfers are encrypted in transit
- **Requirements**: SFTP client and outbound internet access

{% hint style="info" %}
FTP and FTPS protocols are **not supported** for security reasons. Only SFTP connections are accepted.
{% endhint %}

## Directory Structure

Each customer has a dedicated folder structure for organized file management:

```shell
📁 /order                    # Incoming orders
📁 /order_change             # Order modifications  
📁 /order_response           # Order confirmations
📁 /despatch_advice          # Shipment notifications
📁 /receipt_advice           # Goods receipt confirmations
📁 /archive/
  ├── order/                 # Processed order files
  ├── order_change/          # Processed order changes
  ├── order_response/        # Processed responses
  ├── despatch_advice/       # Processed shipments
  └── receipt_advice/        # Processed receipts
```

## Integration Workflows

### Uploading Files to Tradecloud

#### Customer → Tradecloud data flow

1. **Export** - Generate file from your ERP system
2. **Upload** - Transfer file to appropriate folder via SFTP
3. **Process** - Tradecloud automatically detects and imports the file
4. **Archive** - Successfully processed files are moved to archive

{% hint style="warning" %}
**File Permissions**: Use `0664` permissions when uploading files. This is required per the [SFTP specification](https://datatracker.ietf.org/doc/html/draft-ietf-secsh-filexfer-13#section-7.6) and ensures proper file processing.
{% endhint %}

### Downloading Files from Tradecloud

#### Tradecloud → Customer data flow

1. **Generate** - Tradecloud creates file based on business events
2. **Upload** - File is placed in your designated folder
3. **Download** - Your system retrieves the file via SFTP polling
4. **Process** - Import file into your ERP system
5. **Archive** - Move processed files to archive folder

## Best Practices

- **Polling Frequency**: Check for new files every 5-15 minutes
- **File Naming**: Use consistent naming conventions for easier processing
- **Error Handling**: Implement retry logic for failed transfers
- **Monitoring**: Set up alerts for processing failures or connection issues
- **Cleanup**: Regularly archive or remove old files to maintain performance

## Getting Started

1. **Contact Support** - Request FTP access credentials from [support@tradecloud1.com](mailto:support@tradecloud1.com)
2. **Choose Format** - Select CSV or EDIFACT based on your requirements
3. **Configure Client** - Set up your SFTP client with provided credentials
4. **Test Integration** - Start with acceptance environment before production
