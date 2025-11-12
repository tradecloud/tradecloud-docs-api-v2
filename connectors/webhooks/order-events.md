# Order Events

When using the order webhook, you can configure and receive the following order events.

## Order is issued or updated by buyer

The buyer can issue new order lines or update existing ones.

If confirmed delivery schedules or prices are updated, this triggers a [reopen request](#order-reopen-request-by-buyer).

| OrderEvent                  | Webhook Configuration                                                                 |
| --------------------------- | ------------------------------------------------------------------------------------- |
| `OrderIssuedByBuyer`        | New order is issued by the buyer                                                      |
| `OrderLinesIssuedByBuyer`   | Additional order lines are added by the buyer                                         |
| `OrderLinesReissuedByBuyer` | Updated order lines are reissued by the buyer                                         |
| `OrderLinesUpdatedByBuyer`  | Order and line fields other than prices & delivery schedules are updated by the buyer |

## Order confirmed by supplier or buyer

The supplier can accept, reject, or [propose an alternative](#order-proposal-by-supplier).

- **Accepted**: The supplier confirmed the order line(s) as requested by the buyer.
- **Rejected**: The supplier cannot deliver the order line(s).
- **Confirmed by buyer**: The buyer confirmed new order line(s) without requesting supplier confirmation.
- **Confirmed by supplier**: The supplier confirmed the order line(s) with different values than requested by the buyer, and the buyer has [Auto Confirm](https://docs.tradecloud1.com/api/processes/order/buyer/issue/indicators#auto-confirm) enabled.

| OrderEvent                      | Webhook Configuration                                                                       |
| ------------------------------- | ------------------------------------------------------------------------------------------- |
| `OrderLinesAcceptedBySupplier`  | Order lines are accepted by the supplier                                                    |
| `OrderLinesRejectedBySupplier`  | Order lines are rejected by the supplier                                                    |
| `OrderLinesConfirmedByBuyer`    | Order lines are unilaterally confirmed by the buyer                                         |
| `OrderLinesConfirmedBySupplier` | Order lines are confirmed by the supplier with different values than requested by the buyer |

## Order proposal by supplier

The supplier can propose alternative delivery schedules or prices.

The buyer then approves or rejects the proposal.

| OrderEvent                            | Webhook Configuration                                            |
| ------------------------------------- | ---------------------------------------------------------------- |
| `OrderChangesProposedBySupplier`      | Order changes are proposed by the supplier                       |
| `OrderChangesProposalApprovedByBuyer` | Order changes proposed by the supplier are approved by the buyer |
| `OrderChangesProposalRejectedByBuyer` | Order changes proposed by the supplier are rejected by the buyer |

## Order updated by supplier

The supplier can update existing order lines.

If delivery schedules or prices are updated, this triggers either a [proposal](#order-proposal-by-supplier) or [reopen request](#order-reopen-request-by-supplier).

| OrderEvent                     | Webhook Configuration                                                                    |
| ------------------------------ | ---------------------------------------------------------------------------------------- |
| `OrderLinesUpdatedBySupplier`  | Order and line fields other than prices & delivery schedules are updated by the supplier |
| `OrderLinesItemDetailsChanged` | Order lines item details are changed by the supplier                                     |

## Order reopen request by buyer

- The buyer can request to reopen confirmed order lines.
- The supplier can approve or reject the reopen request.
- The buyer can revert their reopen request.

| OrderEvent                                  | Webhook Configuration                            |
| ------------------------------------------- | ------------------------------------------------ |
| `OrderLinesReopenRequestedByBuyer`          | Order lines reopen is requested by the buyer     |
| `OrderLinesReopenRequestApprovedBySupplier` | Buyer reopen request is approved by the supplier |
| `OrderLinesReopenRequestRejectedBySupplier` | Buyer reopen request is rejected by the supplier |
| `OrderLinesReopenRequestRevertedByBuyer`    | Buyer reopen request is reverted by the buyer    |

## Order reopen request by supplier

The supplier can request to reopen confirmed order lines.

The buyer can approve or reject the reopen request.

| OrderEvent                               | Webhook Configuration                            |
| ---------------------------------------- | ------------------------------------------------ |
| `OrderLinesReopenRequestedBySupplier`    | Order lines reopen is requested by the supplier  |
| `OrderLinesReopenRequestApprovedByBuyer` | Supplier reopen request is approved by the buyer |
| `OrderLinesReopenRequestRejectedByBuyer` | Supplier reopen request is rejected by the buyer |

## Order reconfirmation request by buyer

The buyer can request to reconfirm order lines.

The supplier can reconfirm the order lines or submit a reopen request.

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

Both buyer and supplier can update the order line logistics status and delivery schedule logistics fields: `status`, `etd`, and `eta`.

| OrderEvent                                             | Webhook Configuration                                          |
| ------------------------------------------------------ | -------------------------------------------------------------- |
| `OrderLinesMarkedAsDeliveredByBuyer`                   | Order lines are marked as delivered by the buyer               |
| `OrderLinesMarkedAsDeliveredBySupplier`                | Order lines are marked as delivered by the supplier            |
| `OrderLinesMarkedAsOpenByBuyer`                        | Order lines are marked as open by the buyer                    |
| `OrderLinesMarkedAsOpenBySupplier`                     | Order lines are marked as open by the supplier                 |
| `OrderLinesDeliveryScheduleLogisticsUpdatedByBuyer`    | Delivery schedule logistics fields are updated by the buyer    |
| `OrderLinesDeliveryScheduleLogisticsUpdatedBySupplier` | Delivery schedule logistics fields are updated by the supplier |
| `OrderLinesShippedByBuyer`                             | Order lines are marked as shipped by the buyer                 |

## Order contacts

Both buyer and supplier can reassign their order contact.

| OrderEvent                         | Webhook Configuration                                |
| ---------------------------------- | ---------------------------------------------------- |
| `OrderContactReassignedByBuyer`    | Buyer order contacts are reassigned in the portal    |
| `OrderContactReassignedBySupplier` | Supplier order contacts are reassigned in the portal |

## Maintenance

Both buyer and supplier can manually resend order lines to their ERP system.

| OrderEvent              | Webhook Configuration                        |
| ----------------------- | -------------------------------------------- |
| `OrderResentByBuyer`    | The order is manually resent by the buyer    |
| `OrderResentBySupplier` | The order is manually resent by the supplier |
