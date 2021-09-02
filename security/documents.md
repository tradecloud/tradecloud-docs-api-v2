# Document Storage

Documents that are uploaded to Tradecloud's Object Storage ([buyer](../buyer/issue/attach-document.md#step-1-upload-a-document-to-the-tradecloud-object-storage) / [supplier](../supplier/send-order-response/attach-document.md#step-1-upload-a-document-to-the-tradecloud-object-storage)) are securely stored in our cloud.  
We protect your documents and the people that receive your documents as follows:

* Documents can only be uploaded or downloaded through an [encrypted connection](encryption.md)
* Once a document is uploaded to our Object Storage, it is immediately scanned for viruses, worms and trojans. The scanner's database is updated every 3 hours.
* Only Tradecloud users can request a download link of a document. If a Tradecloud user requests a download link, we first verify that the user is [authorized](authorization.md) to access this document, based on the provided JWT Access Token.
* Download links are only valid for 1 minute. 
