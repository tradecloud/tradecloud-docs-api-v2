# Document Storage

Documents that are uploaded to our Object Storage ([buyer](../buyer/issue/attach-document.md#step-1-upload-a-document-to-the-tradecloud-object-storage) / [supplier](../supplier/send-order-response/attach-document.md#step-1-upload-a-document-to-the-tradecloud-object-storage)) are securely stored in our cloud.

We protect your documents and the users that receive your documents as follows:

* Documents can only be uploaded or downloaded through an [encrypted connection](encryption.md)
* Once a document is uploaded:
    * It is stored on (hardware-level) encrypted disks. 
    * it is stored spanning multiple EU data centers. 
    * It is immediately scanned for viruses, worms and trojans.   
      The scanner's database is updated every 3 hours.  
      If the document is infected, it is deleted from our storage.
* Only [authenticated](authentication.md) and [authorized](authorization.md) Tradecloud users can request a download link of a document.
* Download links are only valid for 1 minute. 
