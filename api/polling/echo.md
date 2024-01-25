---
description: >-
  How to handle echoed changes in an open request when using polling
---

# Handle echoed changes when using polling

When your order update or order response results in an open request, asking either supplier or buyer to approve the change, there is a functional consideration that requires careful attention, if your ERP system does not make a distinction between `requested` versus `confirmed` fields such as delivery date or prices:

The fields `lines.deliverySchedule`, `lines.prices` and `lines.chargeLines` will still contain the issued or confirmed values, and not the changed values sent by your ERP system. In the next polling request, when these issued or confirmed values are processed by your ERP system, they will overwrite the changed values in your ERP system.

The fields `lines.deliveryScheduleIncludingRequest`, `lines.pricesIncludingRequest` and `lines.chargeLinesIncludingRequest` will reflect the changed values of the open request. When these values are processed by your ERP system, they will not overwrite the changed values in your ERP system.

Wether to use the `includingRequests` fields or ignore the order line update depends on the request status:

For buyers, if the [`lines.buyerLine.requests.reopenRequest.status`](../../order/buyer/receive/README.md#buyer-requests) is [`Open`](../../order/buyer/receive/README.md#request-status) then use the `includingRequests` fields.

For suppliers, if the [`lines.supplier.requests.proposal.status` or `lines.supplier.requests.reopenRequest.status`](../../order/supplier/receive/README.md#supplier-requests) is [`Open`](../../order/supplier/receive/README.md#request-status) then use the `includingRequests` fields.
