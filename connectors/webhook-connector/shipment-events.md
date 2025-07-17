# Shipment Events

When using the shipment webhook you may configure and receive below shipment events.

## Shipment is issued or updated by the supplier

The supplier can send a despatch advice or create or update a shipment in the portal.

| ShipmentEvent                  | Webhook Configuration |
| ------------------------------ | --------------------- |
| `ShipmentIssuedBySupplier`     | New shipment is issued by the supplier |
| `ShipmentReissuedBySupplier`   | Updated shipment is reissued by the supplier |

## Shipment is approved or rejected by the buyer

The buyer can either approve or reject a shipment created or updated by the supplier.

| ShipmentEvent                  | Webhook Configuration |
| ------------------------------ | --------------------- |
| `ShipmentApprovedByBuyer`      | Shipment is approved by the buyer |
| `ShipmentRejectedByBuyer`      | Shipment is rejected by the buyer |

## Shipment document attached

The buyer or supplier can attach a document to the shipment.

| ShipmentEvent                        | Webhook Configuration |
| ------------------------------------ | --------------------- |
| `ShipmentDocumentAttachedByBuyer`    | Document(s) are attached to te shipment by the buyer |
| `ShipmentDocumentAttachedBySupplier` | Document(s) are attached to te shipment by the supplier |

## Maintenance

The buyer can resend a shipment to their ERP.

| ShipmentEvent                        | Webhook Configuration |
| ------------------------------------ | --------------------- |
| `ShipmentResentByBuyer`              | The shipment is manual resent by the buyer |
