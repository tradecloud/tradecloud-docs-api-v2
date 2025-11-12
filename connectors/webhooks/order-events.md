# Order Events

When using the order webhook, you can configure and receive the following order events.

## Order is issued or updated by buyer

The buyer can issue, reissue before confirmation or update order lines.

- **Issued**: The buyer issued a new order or issued additional lines within an existing order
- **Reissued** The buyer updated issued lines
- **Updated**: The buyer updated confirmed lines. If confirmed delivery schedules or prices are updated, this triggers a [reopen request](#order-reopen-request-by-buyer).

| OrderEvent                  | Webhook Configuration                                                                 |
| --------------------------- | ------------------------------------------------------------------------------------- |
| `OrderIssuedByBuyer`        | New order is issued by the buyer                                                      |
| `OrderLinesIssuedByBuyer`   | Additional order lines are added by the buyer                                         |
| `OrderLinesReissuedByBuyer` | Updated order lines are reissued by the buyer                                         |
| `OrderLinesUpdatedByBuyer`  | Order and line fields other than prices & delivery schedules are updated by the buyer |

## Order confirmed by supplier or buyer

The supplier can accept, reject, or [propose an alternative](#order-proposal-by-supplier).

- **Accepted**: The supplier confirmed the order line(s) as requested by the buyer.
- **Rejected**: The supplier rejected the requested order line(s).
- **Confirmed by buyer**: The buyer confirmed new order line(s) without requesting supplier confirmation.
- **Confirmed by supplier**: The supplier confirmed the order line(s) with different values than requested by the buyer, and the buyer has [Auto Confirm](https://docs.tradecloud1.com/api/processes/order/buyer/issue/indicators#auto-confirm) enabled.

| OrderEvent                      | Webhook Configuration                                                                       |
| ------------------------------- | ------------------------------------------------------------------------------------------- |
| `OrderLinesAcceptedBySupplier`  | Order lines are accepted by the supplier                                                    |
| `OrderLinesRejectedBySupplier`  | Order lines are rejected by the supplier                                                    |
| `OrderLinesConfirmedByBuyer`    | Order lines are unilaterally confirmed by the buyer                                         |
| `OrderLinesConfirmedBySupplier` | Order lines are confirmed by the supplier with different values than requested by the buyer |

## Order proposal by supplier

The supplier can propose an alternative delivery schedule or prices. The buyer then approves or rejects the proposal.

- **Propose**: The supplier proposed an alternative delivery schedule or prices.
- **Approve or reject**: The buyer approved or rejected the proposal.

| OrderEvent                            | Webhook Configuration                                            |
| ------------------------------------- | ---------------------------------------------------------------- |
| `OrderChangesProposedBySupplier`      | Order changes are proposed by the supplier                       |
| `OrderChangesProposalApprovedByBuyer` | Order changes proposed by the supplier are approved by the buyer |
| `OrderChangesProposalRejectedByBuyer` | Order changes proposed by the supplier are rejected by the buyer |

## Order updated by supplier

The supplier can update existing order lines. If delivery schedule or prices are updated, this triggers either a [proposal](#order-proposal-by-supplier) or [reopen request](#order-reopen-request-by-supplier).

- **Updated**: The supplier updated fields other than prices & delivery schedules.
- **Changed**: The supplier updated item details as requested by the buyer.

| OrderEvent                     | Webhook Configuration                                                                    |
| ------------------------------ | ---------------------------------------------------------------------------------------- |
| `OrderLinesUpdatedBySupplier`  | Order and line fields other than prices & delivery schedules are updated by the supplier |
| `OrderLinesItemDetailsChanged` | Order lines item details are changed by the supplier                                     |

## Order reopen request by buyer

The buyer can request an alternative delivery schedule or prices after confirmation. The supplier then approves or rejects the request.

- **Requested**: The buyer requested to reopen confirmed order lines.
- **Reverted**: The buyer reverted their reopen request.
- **Approved or rejected**: The supplier approved or rejected the reopen request.

| OrderEvent                                  | Webhook Configuration                            |
| ------------------------------------------- | ------------------------------------------------ |
| `OrderLinesReopenRequestedByBuyer`          | Order lines reopen is requested by the buyer     |
| `OrderLinesReopenRequestRevertedByBuyer`    | Buyer reopen request is reverted by the buyer    |
| `OrderLinesReopenRequestApprovedBySupplier` | Buyer reopen request is approved by the supplier |
| `OrderLinesReopenRequestRejectedBySupplier` | Buyer reopen request is rejected by the supplier |

## Order reopen request by supplier

The supplier can request an alternative delivery schedule or prices after confirmation. The buyer then approves or rejects the request.

- **Requested**: The supplier requested to reopen confirmed order lines.
- **Approved or rejected**: The buyer approved or rejected the reopen request.

| OrderEvent                               | Webhook Configuration                            |
| ---------------------------------------- | ------------------------------------------------ |
| `OrderLinesReopenRequestedBySupplier`    | Order lines reopen is requested by the supplier  |
| `OrderLinesReopenRequestApprovedByBuyer` | Supplier reopen request is approved by the buyer |
| `OrderLinesReopenRequestRejectedByBuyer` | Supplier reopen request is rejected by the buyer |

## Order reconfirmation request by buyer

The buyer can request to reconfirm order lines. The supplier can reconfirm the order lines or submit a [reopen request](#order-reopen-request-by-supplier)

- **Requested**: The buyer requested to reconfirm order lines.
- **Reconfirmed**: The supplier reconfirmed the order lines

| OrderEvent                                 | Webhook Configuration                                |
| ------------------------------------------ | ---------------------------------------------------- |
| `OrderLinesReconfirmationRequestedByBuyer` | Order lines reconfirmation is requested by the buyer |
| `OrderLinesReconfirmedBySupplier`          | Order lines are reconfirmed by the supplier          |

## Order lines cancelled by buyer

The buyer can cancel order lines and revert the cancellation of order lines

- **Cancelled**: The buyer can cancel order lines.
- **Reverted**: The buyer can revert cancellation of order lines.

| OrderEvent                           | Webhook Configuration                           |
| ------------------------------------ | ----------------------------------------------- |
| `OrderLinesCancelledByBuyer`         | Order lines are cancelled by the buyer          |
| `CancelledOrderLinesRevertedByBuyer` | Cancelled order lines are reverted by the buyer |

## Order lines completed by buyer

The buyer can complete order lines and revert the completion of order lines.

- **Completed**: The buyer can complete order lines.
- **Reverted**: The buyer can revert completion of order lines.

| OrderEvent                           | Webhook Configuration                           |
| ------------------------------------ | ----------------------------------------------- |
| `OrderLinesCompletedByBuyer`         | Order lines are completed by the buyer          |
| `CompletedOrderLinesRevertedByBuyer` | Completed order lines are reverted by the buyer |

## Order lines logistics

Both buyer and supplier can update the logistics process.

- **Open**: The buyer or supplier marked order lines as open again, being previously shipped or delivered.
- **Shipped**: The buyer marked order lines as shipped by the supplier
- **Delivered**: The buyer or supplier marked order lines as delivered at the buyer.
- **Updated**: The buyer or supplier updated the delivery line logistics fields.

| OrderEvent                                             | Webhook Configuration                                          |
| ------------------------------------------------------ | -------------------------------------------------------------- |
| `OrderLinesMarkedAsOpenByBuyer`                        | Order lines are marked as open by the buyer                    |
| `OrderLinesMarkedAsOpenBySupplier`                     | Order lines are marked as open by the supplier                 |
| `OrderLinesShippedByBuyer`                             | Order lines are marked as shipped by the buyer                 |
| `OrderLinesMarkedAsDeliveredByBuyer`                   | Order lines are marked as delivered by the buyer               |
| `OrderLinesMarkedAsDeliveredBySupplier`                | Order lines are marked as delivered by the supplier            |
| `OrderLinesDeliveryScheduleLogisticsUpdatedByBuyer`    | Delivery schedule logistics fields are updated by the buyer    |
| `OrderLinesDeliveryScheduleLogisticsUpdatedBySupplier` | Delivery schedule logistics fields are updated by the supplier |

## Order contacts

- **Reassigned**: The buyer or supplier reassigned their order contact.

| OrderEvent                         | Webhook Configuration                                |
| ---------------------------------- | ---------------------------------------------------- |
| `OrderContactReassignedByBuyer`    | Buyer order contacts are reassigned in the portal    |
| `OrderContactReassignedBySupplier` | Supplier order contacts are reassigned in the portal |

## Maintenance

- **Resent**: Buyer or supplier manually resent the order to their ERP system.

| OrderEvent              | Webhook Configuration                        |
| ----------------------- | -------------------------------------------- |
| `OrderResentByBuyer`    | The order is manually resent by the buyer    |
| `OrderResentBySupplier` | The order is manually resent by the supplier |
