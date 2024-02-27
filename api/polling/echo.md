---
description: >-
  How to handle echoed changes in an open request when using polling
---

# Handle echoed changes when using polling

When your order update or order response results in an **open request**, asking the other party to approve the change, there is a functional consideration that requires careful attention, if your ERP system **does not make a distinction between `requested` versus `confirmed` fields** such as delivery date, quantity or prices:

In this case the fields `lines.deliverySchedule`, `lines.prices` and `lines.chargeLines` will still contain the issued or confirmed values, and not the changed values just sent by your ERP system. In the next polling request, when these issued or confirmed values are processed by your ERP system, they will revert the changed values in your ERP system. These fields have to be ignored when:

* In general, when [`lines.status.ProcessStatus`](../../order/buyer/receive/README.md#line-process-status) is `InProgress`.
* Or more fine grained, if you are a buyer and the [`lines.status.inProgressStatus`](../../order/buyer/receive/README.md#line-in-progress-status) is `OpenBuyerReopenRequest`.
* Or if you are a supplier and the [`lines.status.inProgressStatus`](../../order/supplier/receive/README.md#line-in-progress-status) is either `OpenSupplierProposal` or `OpenSupplierReopenRequest`.
