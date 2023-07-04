---
description: How to receive a shipment event
---

# Receive a shipment event

Tradecloud will send a shipment event to the buyer when a shipment event has been triggered.

At this moment a shipment event will only be triggered when the supplier issues or updates a despatch advice.

{% hint style="warning" %}
The shipment module is under development. The API and documentation may change.
{% endhint %}

## Choose the appropriate API to receive a shipment event

First choose either the webhook API or the polling API to receive shipment messages:

{% page-ref page="../../../../api/webhook-vs-polling.md" %}

## ShipmentEvent

* `eventName`: the event name, currently only `ShipmentDespatchedBySupplier`

{% hint style="warning" %}
`ShipmentDespatchedBySupplier` will be replaced by `ShipmentIssuedBySupplier`, `ShipmentApprovedByBuyer` and `ShipmentRejectedByBuyer` and other events in the future.
{% endhint %}

* `shipment`: the shipment state, see [Shipment state](#shipment-state)
* `meta`: the message meta information, see [Message meta information](#message-meta-information)

## Shipment state

The shipment data:

* `id`: the Tradecloud shipment identifier
* `identifiers`: the identifiers related to this shipment, see [Shipment identifiers](#shipment-identifiers)
* `transportMode`: the Mode of Transport name used for the delivery of goods. [Unece Code List Recommendation 19](https://unece.org/trade/uncefact/cl-recommendations) is advised for Mode of Transport names.
* `supplierShipment`: the supplier side header of the shipment, see [Supplier shipment header](#buyer-shipment-header)
* `buyerShipment`: the buyer side header part of the shipment, see [Buyer shipment header](#buyer-shipment-header)
* `loadCarriers`: a list of all the load carriers in this shipment, each load carrier containing shipment lines, see [Load carrier](#load-carrier)
* `lines`: a list of all the shipment lines, not loaded in a load carrier, see [Shipment line](#shipment-line)
* `locations`: the departure, next destination and final destination locations of a shipment, see [Shipment locations](#shipment-locations)
* `meta`: meta information about the shipment, see [Shipment meta information](#shipment-meta-information)

### Shipment identifiers

The identifiers related to this shipment:

* `billOfLadingNumber`: the bill of lading number as provided by the carrier
* `imoNumber`: the IMO [ship identification number](https://www.imo.org/en/ourwork/msas/pages/imo-identification-number-scheme.aspx) as provided by the carrier
* `carrierShipmentNumber`: the shipment number as provided by the carrier
* `trackingNumber`: the tracking number as provided by the carrier or courier

### Supplier shipment header 

The supplier side header of this shipment:

* `companyId`: the mandatory Tradecloud company identifier of the supplier
* `supplierParty`: the unique party identifier and scheme, like [GLN](https://www.gs1.org/standards/id-keys/gln), of the supplier
* `buyerAccountNumber`: the buyer account code or number as used by the supplier
* `shipmentNumber`: the related shipment number as known in the supplier's ERP system
* `invoiceNumbers`: the related invoice numbers as known in the supplier's ERP system
* `documents`: the supplier documents attached to this shipment, see [Document](#document)
* `contacts`: the supplier contacts related to this shipment, see [Contact](#contact)

### Buyer shipment header

The buyer side header of this shipment:

* `companyId`: the mandatory Tradecloud company identifier of the buyer
* `buyerParty`: the unique party identifier and scheme, like [GLN](https://www.gs1.org/standards/id-keys/gln), of the buyer
* `supplierAccountNumber`: the supplier account code or number as known at the buyer
* `documents`: the buyer documents attached to this shipment, see [Document](#document)
* `contacts`: the buyer contacts related to this shipment, see [Contact](#contact)
* `purchaseOrderTerms`: the purchase order terms as agreed between buyer and supplier, see [Purchase order terms](#purchase-order-terms)

#### Contact

A contact person related to this shipment:

* `userId`: the Tradecloud user identifier
* `email`: the contact email as known in Tradecloud
* `firstName`: the personal name of the contact person
* `lastName`: the family name of the contact person
* `position`: the business role of the contact person within the company
* `phoneNumber` the phone number of the contact person

#### Document

* `code`: the unique identifier of the document as provided by the supplier or buyer
* `revision`: the revision of the document
* `name`: the short name of the document
* `description`: the description of the document
* `type`: the type of the document. Eg. General, Invoice, Packing List, etc...
* `objectId`: the object ID as known by the Tradecloud Object Storage, if this document is stored in Tradecloud, see also:

{% page-ref page="download-document.md" %}

* `url`: the location of the document if is not stored in Tradecloud
* `meta`: meta information about the shipment document
  * `lastUpdatedAt`: ISO date and time with timezone at which the shipment document was last updated in Tradecloud. A document has been added or changed if the `document.meta.lastUpdatedAt` is equal to the `shipment.meta.lastUpdatedAt` 

#### Purchase order terms

The purchase order terms, as agreed between buyer and supplier, related to this shipment:

* `incotermsCode`: the incoterms code according to ICC [Incoterms 2020](https://iccwbo.org/business-solutions/incoterms-rules/incoterms-2020/)
* `incoterms`: the incoterms named place (delivery, terminal, port or destination)
* `paymentTermsCode`: the payment terms code as defined in the buyers ERP system
* `paymentTerms`: the payment terms text as defined in the buyers ERP system

## Load carrier

A load carrier containing shipment lines. Either use the [container fields](#container-fields) or the [generic package fields](#generic-package-fields) together with [lines](#lines).

### Container fields

When the load carrier is a container:

* `containerNumber`: the BIC ISO 6346 [Container Identification Number](https://www.bic-code.org/identification-number/)
* `containerSizeAndType`: the BIC ISO 6346 [Container Size & Type Code](https://www.bic-code.org/size-type-code/)

### Generic package fields

When the load carrier is NOT a container:

* `packageSSCC`: the package GS1 [Serial Shipping Container Code (SSCC)]( https://www.gs1.org/standards/id-keys/sscc)
* `packageType`: the package type, [Unece Code List Recommendation 21](https://unece.org/trade/uncefact/cl-recommendations) is advised

### Lines

* `lines`: a list of all the shipment lines, loaded in this load carrier, see [Shipment line](#shipment-line)

## Shipment line

A shipment line containing identifiers, item and supplier data including quantities. A line has been added to either a shipment directly or to a load carrier.

* `purchaseOrderNumber`: the mandatory related purchase order number as provided by the buyer
* `purchaseOrderLinePosition`: the mandatory line position in the purchase order as provided by the buyer
* `deliverySchedulePosition`: the related delivery schedule position in the purchase order line as provided by the buyer
* `item`: the item that is shipped, see [Shipment item](#shipment-item)
* `supplierLine`: the supplier side of the shipment line, see [Supplier shipment line](#supplier-shipment-line)
* `meta`: meta information about the shipment line, see [Shipment line meta information](#shipment-line-meta-information)

### Shipment item

The item (article, goods) that is being shipped:

* `buyerItemNumber`: the item number as provided by the buyer
* `buyerItemRevision`: the revision of the item as provided by the buyer
* `buyerItemName`: the short name of this item as provided by the buyer
* `supplierItemNumber`: the supplier item code or number as provided by the buyer or supplier
* `supplierItemRevision`: the revision (or version) as provided by the supplier
* `supplierItemName`: the short name of this item as provided by the supplier
* `purchaseUnitOfMeasureIso`: the the 3-letter purchase unit according to ISO 80000-1 which applies to this item

### Supplier shipment line

The supplier side of the shipment line:

* `despatchAdviceNumber`: the mandatory unique despatch advice number as provided by the supplier
* `despatchAdviceLinePosition` the mandatory position in the despatch advice as provided by the supplier. The position is unique within the despatch advice and immutable.
* `despatchQuantity` the mandatory despatched quantity of this purchase order line or delivery schedule position.
* `backorderQuantity`: the backorder quantity of this purchase order line or delivery schedule position.

### Shipment line meta information
* `lastUpdatedAt`: ISO date and time with timezone at which the shipment line was last updated in Tradecloud. A line has been added or changed if the `lines.meta.lastUpdatedAt` is equal to the `shipment.meta.lastUpdatedAt`

## Shipment locations

The departure and destination locations and date/times of a shipment:

* `departure`: the departure location and dates, see [Shipment departure ](#shipment-departure)
* `destinations`: one or more destination locations, arrival and departure dates, see [Shipment destination](#shipment-destination)

### Shipment departure 

A shipment departure location with ETD and ATD dates:

* `location`: the departure location, see [Shipment location](#shipment-location)

* `etdDate`: the Estimated Time of Departure of this shipment from this location
* `atdDate`: the Actual Time of Departure of this shipment from this location

### Shipment destination 

A shipment place, port or final destination with location, ETA time window, ATA, ETD and ATD dates:

* `location`: the location where the shipment should arrive next, see [Shipment location](#shipment-location)

Estimated start and end date/times indicate the scheduled time window of arrival:

* `etaStartDate`: the Estimated Time of Arrival period start date of this shipment at this destination
* `etaStartTime`: the Estimated Time of Arrival period start time of this shipment at this destination
* `etaEndDate`: the Estimated Time of Arrival period end date of this shipment at this destination
* `etaEndTime`: the Estimated Time of Arrival period end time of this shipment at this destination

* `ataDate`: the Actual Time of Arrival of this shipment at this destination
* `etdDate`: the Estimated Time of Departure of this shipment from this location
* `atdDate`: the Actual Time of Departure of this shipment from this location

## Shipment location

* `locationType`: a location type according to ICC [Incoterms 2020](https://iccwbo.org/business-solutions/incoterms-rules/incoterms-2020/):

  * `AgreedPlace` (used with EXW, FCA)
  * `PortOfLoading` (used with FAS, FOB)
  * `PortOfDestination` (used with CFR, CIF)
  * `PlaceOfDestination` (used with CPT, CIP)
  * `FinalDestination` (used with DAP, DPU, DDP)

* `id`: the required identifier for the location, in context of `idSchema`
* `idScheme`: scheme, providing context to the location identifier, like [GLN](https://www.gs1.org/standards/id-keys/gln)
* `names`: one or more location names. It is recommended to provide at least one name.
* `addressLines`: one or more location address lines
* `postalCode`: location postal code
* `city`: location city
* `countryCodeIso`: [ISO 3166-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) country code

## Shipment meta information
* `lastUpdatedAt`: ISO date and time with timezone at which the shipment was last updated in Tradecloud, useful for polling shipments.
* `supplierErpMeta` the supplier's ERP meta information about this shipment
  * `despatchAdviceErpIssueDateTime`: local date and time at which the despatch advice of this shipment was issued in the supplier's ERP system

## Message meta information

* `messageId`: the Tradecloud identifier of this message.
* `source`: includes meta information about the source of this message:

  * `traceId`: the Tradecloud trace identifier of this message. All related messages in a flow will have the same tradeId.
  * `userId`: the Tradecloud user identifier which triggered the first message in a flow
  * `companyId`: the Tradecloud company identifier which triggered the first message in a flow

* `createdDateTime`: date and time with time zone, at which this message was created
