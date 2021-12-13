---
description: How to receive a shipment event
---

# Receive a shipment event

Tradecloud will send a shipment event to the buyer when a shipment event has been triggered.

At this moment a shipment event will only be triggered when the supplier issues or updates a despatch advice.

## Choose the appropriate API to receive the shipment event

Currently only the shipment webhook API is supported.

See [Webhook Connector](https://tradecloud.gitbook.io/connectors/webhook-connector) for setting up and using the webhook.

Contact support if you need the polling API to receive shipment messages:

{% page-ref page="../../api/webhook-vs-polling.md" %}

{% hint style="warning" %}
This shipment module is under development. The API and documentation may change.
{% endhint %}

## ShipmentEvent

* `eventName`: the event name, currently only `ShipmentDespatchedBySupplier`
* `shipment`: the shipment state, see [Shipment state](#shipment-state)
* `meta`: the message meta information, see [Message meta information](#message-meta-information)

## Shipment state

* `id`: the Tradecloud shipment identifier
* `trackingNumber`: the tracking number of the shipment as provided by the carrier or courier
* `supplierShipment`: the supplier side header of the shipment, see [Supplier shipment header](#buyer-shipment-header)
* `buyerShipment`: the buyer side header part of the shipment, see [Buyer shipment header](#buyer-shipment-header)
* `lines`: a list of all the shipment lines, see [Shipment line](#shipment-line)
* `locations`: the departure, next destination and final destination locations of a shipment, see [Shipment locations](#shipment-locations)
* `meta`: meta information about the shipment, see [Shipment meta information](#shipment-meta-information)

### Supplier shipment header 

* `companyId`: the Tradecloud company identifier of the supplier
* `buyerAccountNumber`: the buyer account code or number as used by the supplier
* `shipmentNumber`: the related shipment number as known in the supplier's ERP system

### Buyer shipment header

* `companyId`: the Tradecloud company identifier of the buyer
* `supplierAccountNumber`: the supplier account code or number as known at the buyer

## Shipment line

* `purchaseOrderNumber`: the related purchase order number as provided by the buyer
* `purchaseOrderLinePosition`: the line position in the purchase order as provided by the buyer
* `item`: the item that is shipped, see [Shipment item](#shipment-item)
* `supplierLine`: the supplier side of the shipment line, details see below
* `meta`: meta information about the shipment line, see [Shipment line meta information](#shipment-line-meta-information)

### Shipment item

* `buyerItemNumber`: the item number as provided by the buyer
* `buyerItemRevision`: the revision of the item as provided by the buyer
* `buyerItemName`: the short name of this item as provided by the buyer
* `supplierItemNumber`: the supplier item code or number as provided by the buyer or supplier
* `supplierItemRevision`: the revision (or version) as provided by the supplier
* `supplierItemName`: the short name of this item as provided by the supplier
* `purchaseUnitOfMeasureIso`: the the 3-letter purchase unit according to ISO 80000-1 which applies to this item

### Supplier shipment line

* `despatchAdviceNumber`: the unique despatch advice number as provided by the supplier
* `despatchAdviceLinePosition` the position in the despatch advice as provided by the supplier. The position is unique within the despatch advice and immutable.
* `despatchQuantity` the despatched quantity of this purchase order line or delivery schedule position.
* `backorderQuantity`: the backorder quantity of this purchase order line or delivery schedule position.

### Shipment line meta information
* `lastUpdatedAt`: local date and time at which the shipment line was last updated in Tradecloud. A line has been changed if the line.lastUpdatedAt is equal to the shipment.lastUpdatedAt
* `supplierErpMeta` the supplier's ERP meta information about this shipment line
  * `despatchAdviceErpIssueDateTime`: local date and time at which the despatch advice of this shipment line was issued in the supplier's ERP system

## Shipment locations

* `departure`: the departure location and date of a shipment, see [Shipment departure ](#shipment-departure)
* `destination`: the next destination location and scheduled arrival date/time, see [Shipment next destination](#shipment-next-destination)
* `finalDestination`: the final destination location and scheduled arrival date/time, see [Shipment final destination](#shipment-final-destination)

### Shipment departure 

* `location`: the departure location, see [Shipment location](#shipment-location)
* `actualDate`: the actual departure local date

### Shipment next destination 

* `location`: the location where the shipment should arrive next, see [Shipment location](#shipment-location)

Scheduled start and end date/times indicate the scheduled time window of arrival:

* `scheduledStartDate`: start local date of the arrival time window
* `scheduledStartTime`: start local time of the arrival time window
* `scheduledEndDate`: end local date of the arrival time window
* `scheduledEndTime`: end local time of the arrival time window

### Shipment final destination

* `location`: the location where the shipment should arrive finally, see [Shipment location](#shipment-location)

Scheduled start and end date/times indicate the scheduled time window of arrival:

* `scheduledStartDate`: start local date of the arrival time window. 
* `scheduledStartTime`: start local time of the arrival time window.
* `scheduledEndDate`: end local date of the arrival time window.
* `scheduledEndTime`: end local time of the arrival time window.

## Shipment location

* `locationType`: a location type according to Incoterms 2020:

  * `AgreedPlace` (used with EXW, FCA)
  * `PortOfLoading` (used with FAS, FOB)
  * `PortOfDestination` (used with CFR, CIF)
  * `PlaceOfDestination` (used with CPT, CIP)
  * `FinalDestination` (used with DAP, DPU, DDP)

* `id`: the required identifier for the location, in context of `idSchema`
* `idScheme`: scheme, providing context to the location identifier. For example GLN
* `names`: one or more location names. It is recommended to provide at least one name.
* `addressLines`: one or more location address lines
* `postalCode`: location postal code
* `city`: location city
* `countryCodeIso`: country code

## Shipment meta information
* `lastUpdatedAt`: local date and time at which the shipment was last updated in Tradecloud
* `supplierErpMeta` the supplier's ERP meta information about this shipment
  * `despatchAdviceErpIssueDateTime`: local date and time at which the despatch advice of this shipment was issued in the supplier's ERP system

## Message meta information

* `messageId`: the Tradecloud identifier of this message.
* `source`: includes meta information about the source of this message:

  * `traceId`: the Tradecloud trace identifier of this message. All related messages in a flow will have the same tradeId.
  * `userId`: the Tradecloud user identifier which triggered the first message in a flow
  * `companyId`: the Tradecloud company identifier which triggered the first message in a flow

* `createdDateTime`: date and time, in UTC time zone, at which this message was created
