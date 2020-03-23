---
description: Buyer API rules check list
---

# Rules

This is a \(not complete yet\) check list of buyer side API rules

## Issue new order

* [ ] `supplierAccountNumber`, `purchaseOrderNumber`, `destination.code`, `contact.email`,`contact.userName`**,**`lines.position`, `item.number`and `deliverySchedule.position` should be **unique** within your company and **never change**.
* [ ] `supplierAccountNumber` **should be set on forehand** in the Tradecloud **connection** with your supplier. You can set the account code when inviting a new connection or at any time in the connection overview in the portal.

## Reissue existing order

* [ ] Only reissue an order that **has an actual change**
* [ ] Never reissue **all** orders or **all active** orders periodically
* [ ] 


## Attach a document



## Receive goods



## Complete an order



## Reopen an order



## Cancel an order





