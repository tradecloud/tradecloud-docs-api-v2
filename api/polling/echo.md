---
description: >-
  How to handle echoed changes in case of an open request when using polling
---

# Handle echoed changes when using polling

An order update or order response can result in an **open request**, where the other party is asked to approve changes. 

In this case, there is a functional consideration that requires careful attention, if your ERP system **does not make a distinction between `requested` versus `confirmed` fields**:

In this case the fields `lines.deliverySchedule`, `lines.prices` and `lines.chargeLines` will still contain the issued or confirmed values, and not the changed values just sent by your ERP system. In the next polling request, when these old values are processed by your ERP system, they may revert the changed values in your ERP system.

This can be solved by ignoring the order or response update in your polling integration when there is an open request:

* When you do not process open requests at all: ignore the order/response update when [`lines.status.ProcessStatus`](../../order/buyer/receive/README.md#line-process-status) is `InProgress`.
* When you are a buyer and and you process supplier requests: ignore the response update when [`lines.status.inProgressStatus`](../../order/buyer/receive/README.md#line-in-progress-status) is `OpenBuyerReopenRequest`.
* When you are a supplier and and you process buyer requests: ignore the order update when [`lines.status.inProgressStatus`](../../order/supplier/receive/README.md#line-in-progress-status) is either `OpenSupplierProposal` or `OpenSupplierReopenRequest`.
