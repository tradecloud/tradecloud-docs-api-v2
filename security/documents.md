# Document storage

Documents that are uploaded to our Object Storage \([buyer](../order/buyer/issue/attach-document.md#step-1-upload-a-document-to-the-tradecloud-object-storage) / [supplier](../order/supplier/send-order-response/attach-document.md#step-1-upload-a-document-to-the-tradecloud-object-storage)\) are securely stored in our cloud.

We protect your documents and the users that receive your documents as follows:

* Documents can only be uploaded or downloaded through an [encrypted connection](encryption.md)
* The following file extensions are blocked by our API:   
    `.ade`, `.adp`, `.apk`, `.appx`, `.appxbundle`, `.bat`, `.cab`, `.chm`, `.cmd`, `.com`, `.cpl`, `.diagcab`, `.diagcfg`, `.diagpack`, `.dll`, `.dmg`, `.ex`, `.ex_`, `.exe`, `.hta`, `.img`, `.ins`, `.iso`, `.isp`, `.jar`, `.jnlp`, `.js`, `.jse`, `.lib`, `.lnk`, `.mde`, `.msc`, `.msi`, `.msix`, `.msixbundle`, `.msp`, `.mst`, `.nsh`, `.pif`, `.ps1`, `.scr`, `.sct`, `.shb`, `.sys`, `.vb`, `.vbe`, `.vbs`, `.vhd`, `.vxd`, `.wsc`, `.wsf`, `.wsh`, `.xll`
* Once a document is uploaded:
  * It is stored on \(hardware-level\) encrypted disks. 
  * it is stored spanning multiple EU data centers. 
  * It is immediately scanned for viruses, worms and trojans.   

    The scanner's database is updated every 3 hours.  

    If the document is infected, it is deleted from our storage.
* Only [authenticated](authentication.md) and [authorized](authorization.md) Tradecloud users can request a download link of a document.
* Download links are only valid for 1 minute. 

