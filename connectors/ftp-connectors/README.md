---
description: 'Edifact, IDoc and CSV files over FTP server at Tradecloud side'
---

# FTP Connectors

Tradecloud provides several FTP based connectors:

* [CVS FTP Connector](csv-ftp-connector.md)
* [Edifact FTP Connector](edifact-ftp-connector.md)

## FTP Configuration

### Host

| Environment | Host |
| :--- | :--- |
| Acceptance test | ftp.accp.tradecloud1.com |
| Production | ftp.tradecloud1.com |

### Protocol

| Protocol | Description | Supported | Port |
| :--- | :--- | :--- | :--- |
| SFTP | SSH File Transfer Protocol  | Yes | 22 |
| FTPS | Explicit FTP over TLS | No | |
| FTP  | w/o encryption | No | |

### Username / password

The customer FTP username and password will be set by Tradecloud support.

## FTP Folders

There is one FTP folder structure per customer:
```
/order
/order_change
/order_response 
/despatch_advice
/receipt_advice
/archive/order
        /order_change
        /order_response 
        /despatch_advice
        /receipt_advice
```

## FTP Flows

### Uploading a file to Tradecloud

{% hint style="warning" %}
Both parties must use `0664` permission when uploading files.
Setting the correct permissions is the responsibility of the client as outlined in the [standard](https://datatracker.ietf.org/doc/html/draft-ietf-secsh-filexfer-13#section-7.6).
{% endhint %}

![](../.gitbook/assets/ftp-upload-flow-by-customer.png)

| Party | Step | Description |
| :--- | :--- | :--- |
| Tradecloud | Periodic polling | Periodically poll the folder for a new file |
| Customer | 1. Export file | Customer  exports a new file |
| Customer | 2. Upload file | Customer uploads a new file |
| Tradecloud | 3. Download file | Tradecloud downloads a new file |
| Tradecloud | 4. Import file | Tradecloud imports the file |
| Tradecloud | 5. Archive file | When successfully imported, move the file to the archive folder |

### Downloading a file from Tradecloud

![](../.gitbook/assets/ftp-download-flow-by-customer.png)

| Party | Step | Description |
| :--- | :--- | :--- |
| Customer | Periodic polling | Periodically poll the folder for a new file |
| Tradecloud | 1. Export file | Tradecloud exports a new file |
| Tradecloud | 2. Upload file | Tradecloud uploads a new file |
| Customer | 3. Download file | Customer downloads a new file |
| Customer | 4. Process file | Customers ERP system imports the file |
| Customer | 5. Archive file | When successfully imported, move the file to the archive folder |
