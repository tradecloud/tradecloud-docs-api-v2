# Order Events

When using the order webhook you may configure and receive below order events.

## Order is issued or updated by buyer

The buyer can issue new order lines or update existing issued lines.

If confirmed delivery schedule or prices are updated, this will become a [reopen request](#order-reopen-request-by-buyer).

| OrderEvent                  | Webhook Configuration |
| --------------------------- |-----------------------|
| `OrderIssuedByBuyer`        | New order is issued by the buyer |
| `OrderLinesIssuedByBuyer`   | Additional order lines are added by the buyer |
| `OrderLinesReissuedByBuyer` | Updated order lines are reissued by the buyer |
| `OrderLinesUpdatedByBuyer`  | Order and line fields other than prices & delivery schedules are updated by the buyer |

## Order confirmed by supplier or buyer

The supplier can either accept, reject or [propose an alternative](#order-proposal-by-supplier).

* Accepted means that the supplier confirmed the order line(s) as requested by the buyer.
* Rejected means that the supplier cannot deliver the order line(s) at all.
* Confirmed means that the supplier confirmed the order line(s) with other values as requested by the buyer and [Auto Confirm](https://docs.tradecloud1.com/api/processes/order/buyer/issue/indicators#auto-confirm) has been enabled by the buyer.

| OrderEvent                      | Webhook Configuration                     |
| ------------------------------- | ----------------------------------------- |
| `OrderLinesAcceptedBySupplier`  | Order lines are accepted by the supplier  |
| `OrderLinesRejectedBySupplier`  | Order lines are rejected by the supplier  |
| `OrderLinesConfirmedBySupplier` | Order lines are confirmed by the supplier with other values as requested by the buyer |

## Order proposal by supplier

The supplier can propose an alternative delivery schedule or prices.

The buyer either approves or rejects the proposal.

| OrderEvent                            | Webhook Configuration                                        |
| --------------------------------------| ------------------------------------------------------------ |
| `OrderChangesProposedBySupplier`      | Order changes are proposed by the supplier                   |
| `OrderChangesProposalApprovedByBuyer` | By order changes that were proposed by the supplier are approved by the buyer |
| `OrderChangesProposalRejectedByBuyer` | By order changes that were proposed by the supplier are rejected by the buyer |

## Order updated by supplier

The supplier can update existing order lines.

If delivery schedule or prices are updated this will become either a [proposal](#order-proposal-by-supplier) or [reopen request](#order-reopen-request-by-supplier).

| OrderEvent                     | Webhook Configuration                        |
| ------------------------------ | -------------------------------------------- |
| `OrderLinesUpdatedBySupplier`  | Order and line fields other than prices & delivery schedules are updated by the supplier |
| `OrderLinesItemDetailsChanged` | Order lines item details are changed by the supplier | 

## Order reopen request by buyer

The buyer can request to reopen confirmed order lines.

The supplier can either approve or reject the reopen request.

| OrderEvent                                  | Webhook Configuration                        |
| ------------------------------------------- | -------------------------------------------- |
| `OrderLinesReopenRequestedByBuyer`          | Order lines reopen is requested by the buyer     |
| `OrderLinesReopenRequestApprovedBySupplier` | Buyer reopen request is approved by the supplier |
| `OrderLinesReopenRequestRejectedBySupplier` | Buyer reopen request is rejected by the supplier |

## Order reopen request by supplier

The supplier can request to reopen confirmed order lines.

The buyer can either approve or reject the reopen request.

| OrderEvent                               | Webhook Configuration                        |
| ---------------------------------------- | -------------------------------------------- |
| `OrderLinesReopenRequestedBySupplier`    | Order lines reopen is requested by the supplier  |
| `OrderLinesReopenRequestApprovedByBuyer` | Supplier reopen request is approved by the buyer |
| `OrderLinesReopenRequestRejectedByBuyer` | Supplier reopen request is rejected by the buyer |

## Order reconfirmation request by buyer

The buyer can request to reconfirm order lines.

The supplier can either reconfirm or do a reopen request.

| OrderEvent                                 | Webhook Configuration                                |
| ------------------------------------------ | ---------------------------------------------------- |
| `OrderLinesReconfirmationRequestedByBuyer` | Order lines reconfirmation is requested by the buyer |
| `OrderLinesReconfirmedBySupplier`          | Order lines are reconfirmed by the supplier          |

## Order lines cancelled by buyer

The buyer can cancel and revert cancellation of order lines.

| OrderEvent                           | Webhook Configuration                           |
| ------------------------------------ | ----------------------------------------------- |
| `OrderLinesCancelledByBuyer`         | Order lines are cancelled by the buyer          |
| `CancelledOrderLinesRevertedByBuyer` | Cancelled order lines are reverted by the buyer |

## Order lines completed by buyer

The buyer can complete and revert completion of order lines.

| OrderEvent                           | Webhook Configuration                           |
| ------------------------------------ | ----------------------------------------------- |
| `OrderLinesCompletedByBuyer`         | Order lines are completed by the buyer          |
| `CompletedOrderLinesRevertedByBuyer` | Completed order lines are reverted by the buyer |

## Order lines logistics

Both buyer and supplier can (indirectly) update the order line logistics status and delivery schedule logistics fields `status`, `etd` and `eta`

| OrderEvent                                             | Webhook Configuration |
| ------------------------------------------------------ | --------------------- |
| `OrderLinesMarkedAsDeliveredByBuyer`                   | Order lines are marked as delivered by the buyer    |
| `OrderLinesMarkedAsDeliveredBySupplier`                | Order lines are marked as delivered by the supplier |
| `OrderLinesMarkedAsOpenByBuyer`                        | Order lines are marked as open by the buyer         |
| `OrderLinesMarkedAsOpenBySupplier`                     | Order lines are marked as open by the supplier      |
| `OrderLinesDeliveryScheduleLogisticsUpdatedByBuyer`    | Delivery schedule logistics fields are updated by the buyer    |
| `OrderLinesDeliveryScheduleLogisticsUpdatedBySupplier` | Delivery schedule logistics fields are updated by the supplier |

## Order contacts

Both buyer and supplier can reassign their order contact.

| OrderEvent                         | Webhook Configuration                                |
| ---------------------------------- | ---------------------------------------------------- |
| `OrderContactReassignedByBuyer`    | Buyer order contacts are reassigned in the portal    |
| `OrderContactReassignedBySupplier` | Supplier order contacts are reassigned in the portal |

## Maintenance

Buyer and supplier can resend order lines to their ERP system.

Order lines can be synced from the tradecloud legacy platform to the the Tradecloud One platform.

| OrderEvent              | Webhook Configuration                        |
| ----------------------- | -------------------------------------------- |
| `OrderResentByBuyer`    | The order is manually resent by the buyer    |
| `OrderResentBySupplier` | The order is manually resent by the supplier |
| `OrderSynced`           | The order is synced from the legacy platform |
