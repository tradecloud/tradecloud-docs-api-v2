---
description: Order and line status reference
---

# Order and line status

This page consolidates all order-level, line-level, and related status values used in Tradecloud orders.

## Order status

The order status is the aggregation of all the lines statuses.

### Order process status

The order process status is one of:

* `Issued`: the order is (re)issued by the buyer.
* `InProgress`: the order is under negotiation between buyer and supplier
* `Confirmed`: the order is completely agreed between buyer and supplier
* `Rejected`: the order is completely rejected by supplier
* `Completed`: the order is completed at the buyer
* `Cancelled`: the order is cancelled by the buyer

### Order logistics status

The order logistics status is one of:

* `Open`: no or partial quantity Produced, ReadyToShip, Shipped or Delivered
* `Produced`: the order full quantity is produced by the supplier
* `ReadyToShip`: the order full quantity is ready to be shipped by the supplier
* `Shipped`: the order full quantity is shipped by the supplier
* `Delivered`: the order full quantity is delivered at the buyer
* `Cancelled`: the order is cancelled by the buyer

## Line status

### Line process status

The line process status is one of:

* `Issued`: the line is (re)issued by the buyer
* `InProgress`: the line is under negotiation between buyer and supplier
* `Confirmed`: the line is agreed between buyer and supplier
* `Rejected`: the line is rejected by supplier
* `Completed`: the line is completed at the buyer
* `Cancelled`: the line is cancelled by the buyer

### Line in Progress status

The line in progress status is a more fine-grained status when an order line `processStatus` is `InProgress` and is one of:

#### Supplier proposal

* `OpenSupplierProposal`: There is an open proposal from the supplier.
* `RejectedSupplierProposal`: The proposal from the supplier was rejected and no other requests are open.

#### Supplier rejection

* `ReissuedRejectedLine`: The rejected order line was reissued by the buyer.

#### Reopen requests

* `OpenBuyerReopenRequest`: There is an open reopen request (confirm different schedule/prices) from the buyer.
* `OpenSupplierReopenRequest`: There is an open reopen request (confirm different schedule/prices) from the supplier.

#### Reconfirmation request

* `OpenBuyerReconfirmationRequest`: There is an open reconfirmation request (reconfirm the same schedule & prices) from the buyer.

#### Reschedule request

* `OpenSupplierShipmentRescheduleRequest`: There is an open reschedule request (confirm different schedule) due to a shipment.
* `ApprovedDeliverySchedule`: The delivery schedule has been approved after a reschedule request.
* `RejectedDeliverySchedule`: The delivery schedule has been rejected after a reschedule request.

#### Completed or cancelled line reversion

* `RevertedCompletedLine`: The completion of this line was reverted.
* `RevertedCancelledLine`: The cancellation of this line was reverted.

### Line logistics status

The line logistics status is one of:

* `Open`: no or partial quantity Produced, ReadyToShip, Shipped or Delivered
* `Produced`: the line quantity is produced by the supplier
* `ReadyToShip`: the line quantity is ready to be shipped by the supplier
* `Shipped`: the line quantity shipped by the supplier
* `Delivered`: the line quantity delivered at the buyer
* `Cancelled`: the line is cancelled by the buyer

## Scheduled delivery logistics status

The delivery line logistics status applies to individual scheduled deliveries within an order line's delivery schedule. The status is one of:

* `Open`: no or partial quantity Produced, ReadyToShip, Shipped or Delivered
* `Produced`: the delivery line quantity is produced by the supplier
* `ReadyToShip`: the delivery line quantity is ready to be shipped by the supplier
* `Shipped`: the delivery line quantity is shipped by the supplier
* `Delivered`: the delivery line quantity is delivered at the buyer

## Request status

The request status applies to all requests (supplier or buyer). The status is one of:

* `Open`: Requested by one party. To be approved or rejected by the other party.
* `Approved`: The request is approved by the other party.
* `Rejected`: The request is rejected by the other party.
* `Closed`: The request is closed because it is not relevant anymore.
