---
description: How to receive a shipment event
---

# Receive a shipment event

Tradecloud sends shipment events to buyers when a shipment event is triggered.

{% hint style="warning" %}
The shipment module is under development. The API and documentation may change.
{% endhint %}

### Choose your API method

You must choose between two methods to receive shipment events:

- **Webhook API (Push)**: Tradecloud pushes shipment events to your system.
- **Polling API (Pull)**: Your system periodically checks for shipment updates.

For details on choosing between these methods:

{% page-ref page="../../../../api/webhook-vs-polling.md" %}

## Implementation options

### Using the webhook API

Use the [POST shipment webhook](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/shipment-webhook-connector/specs.yaml#/shipment-webhook%20endpoints/webhookPost) endpoint.

The webhook body contains:

- `eventName`: The shipment event name, currently:
  - `ShipmentIssuedBySupplier`
  - `ShipmentReissuedBySupplier`
  - `ShipmentApprovedByBuyer`
  - `ShipmentRejectedByBuyer`
  - `ShipmentHeaderUpdatedBySupplier`
  - `ShipmentDocumentAttachedByBuyer`
  - `ShipmentDocumentAttachedBySupplier`
  - `ShipmentResentByBuyer`
- `shipment`: The actual shipment state
- `meta`: The message meta information, see [Message meta information](#message-meta-information)

### Using the polling API

Use the [POST poll shipments](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/shipment/specs.yaml#/shipment/pollShipmentsRoute) endpoint.

The polling response body contains:

- `data`: The actual shipment states
- `total`: The total number of matching shipments, independent of paging
- `lastUpdatedAt`: Store the `lastUpdatedAt` value to use as `lastUpdatedAfter` in subsequent requests

## Shipment state

The shipment data includes:

- `id`: The Tradecloud shipment identifier
- `identifiers`: The identifiers related to this shipment, see [Shipment identifiers](#shipment-identifiers)
- `transportMode`: The mode of transport name used for the delivery of goods. [UNECE Code List Recommendation 19](https://unece.org/trade/uncefact/cl-recommendations) is recommended for mode of transport names
- `supplierShipment`: The supplier side header of the shipment, see [Supplier shipment header](#supplier-shipment-header)
- `buyerShipment`: The buyer side header of the shipment, see [Buyer shipment header](#buyer-shipment-header)
- `loadCarriers`: A list of all load carriers in this shipment, each containing shipment lines, see [Load carrier](#load-carrier)
- `lines`: A list of all shipment lines not loaded in a load carrier, see [Shipment line](#shipment-line)
- `locations`: The departure and destination locations with arrival and departure date/times, see [Shipment locations](#shipment-locations)
- `status`: The shipment status
  - `processStatus`: The shipment process status, currently `Issued`, `Approved`, or `Rejected`, and may be extended with other values in the future
  - `processStatusReason`: The optional reason for the current process status, for example why the shipment was rejected
- `meta`: Meta information about the shipment, see [Shipment meta information](#shipment-meta-information)

### Shipment identifiers

The identifiers related to this shipment:

- `billOfLadingNumber`: The bill of lading number as provided by the carrier
- `imoNumber`: The IMO [ship identification number](https://www.imo.org/en/ourwork/msas/pages/imo-identification-number-scheme.aspx) as provided by the carrier
- `carrierShipmentNumber`: The shipment number as provided by the carrier
- `trackingNumber`: The tracking number as provided by the carrier or courier

### Supplier shipment header

The supplier side header of this shipment:

- `companyId`: The mandatory Tradecloud company identifier of the supplier
- `supplierParty`: The unique party identifier and scheme, like [GLN](https://www.gs1.org/standards/id-keys/gln), of the supplier
- `buyerAccountNumber`: The buyer account code or number as used by the supplier
- `shipmentNumber`: The related shipment number as known in the supplier's ERP system
- `invoiceNumbers`: The related invoice numbers as known in the supplier's ERP system
- `documents`: The supplier documents attached to this shipment, see [Document](#document)
- `contacts`: The supplier contacts related to this shipment, see [Contact](#contact)

### Buyer shipment header

The buyer side header of this shipment:

- `companyId`: The mandatory Tradecloud company identifier of the buyer
- `buyerParty`: The unique party identifier and scheme, like [GLN](https://www.gs1.org/standards/id-keys/gln), of the buyer
- `supplierAccountNumber`: The supplier account code or number as known by the buyer
- `documents`: The buyer documents attached to this shipment, see [Document](#document)
- `contacts`: The buyer contacts related to this shipment, see [Contact](#contact)
- `purchaseOrderTerms`: The purchase order terms as agreed between buyer and supplier, see [Purchase order terms](#purchase-order-terms)

#### Contact

A contact person related to this shipment:

- `userId`: The Tradecloud user identifier
- `email`: The contact email as known in Tradecloud
- `firstName`: The given name of the contact person
- `lastName`: The family name of the contact person
- `position`: The business role of the contact person within the company
- `phoneNumber`: The phone number of the contact person

#### Document

- `code`: The unique identifier of the document as provided by the supplier or buyer
- `revision`: The revision of the document
- `name`: The short name of the document
- `description`: The description of the document
- `type`: The type of the document (e.g., General, Invoice, Packing List, etc.)
- `objectId`: The object ID as known by the Tradecloud Object Storage, if this document is stored in Tradecloud, see also:

{% page-ref page="download-document.md" %}

- `url`: The location of the document if it is not stored in Tradecloud
- `meta`: Meta information about the shipment document
  - `lastUpdatedAt`: ISO date and time with timezone when the shipment document was last updated in Tradecloud. A document has been added or changed if the `document.meta.lastUpdatedAt` equals the `shipment.meta.lastUpdatedAt`

#### Purchase order terms

The purchase order terms, as agreed between buyer and supplier, related to this shipment:

- `incotermsCode`: The Incoterms code according to ICC [Incoterms 2020](https://iccwbo.org/business-solutions/incoterms-rules/incoterms-2020/)
- `incoterms`: The Incoterms named place (delivery, terminal, port, or destination)
- `paymentTermsCode`: The payment terms code as defined in the buyer's ERP system
- `paymentTerms`: The payment terms text as defined in the buyer's ERP system

## Load carrier

A load carrier containing shipment lines. Use either the [container fields](#container-fields) or the [generic package fields](#generic-package-fields) together with [lines](#lines).

### Container fields

When the load carrier is a container:

- `containerNumber`: The BIC ISO 6346 [Container Identification Number](https://www.bic-code.org/identification-number/)
- `containerSizeAndType`: The BIC ISO 6346 [Container Size & Type Code](https://www.bic-code.org/size-type-code/)

### Generic package fields

When the load carrier is NOT a container:

- `packageSSCC`: The package GS1 [Serial Shipping Container Code (SSCC)](https://www.gs1.org/standards/id-keys/sscc)
- `packageType`: The package type. [UNECE Code List Recommendation 21](https://unece.org/trade/uncefact/cl-recommendations) is recommended

### Lines

- `lines`: A list of all shipment lines loaded in this load carrier, see [Shipment line](#shipment-line)

## Shipment line

A shipment line containing identifiers, item, and supplier data including quantities. A line is added to either a shipment directly or to a load carrier.

- `purchaseOrderNumber`: The mandatory related purchase order number as provided by the buyer
- `purchaseOrderLinePosition`: The mandatory line position in the purchase order as provided by the buyer
- `deliverySchedulePosition`: The related delivery schedule position in the purchase order line as provided by the buyer
- `item`: The item that is shipped, see [Shipment item](#shipment-item)
- `supplierLine`: The supplier side of the shipment line, see [Supplier shipment line](#supplier-shipment-line)
- `meta`: Meta information about the shipment line, see [Shipment line meta information](#shipment-line-meta-information)

### Shipment item

The item (article, goods) being shipped:

- `buyerItemNumber`: The item number as provided by the buyer
- `buyerItemRevision`: The revision of the item as provided by the buyer
- `buyerItemName`: The short name of this item as provided by the buyer
- `supplierItemNumber`: The supplier item code or number as provided by the buyer or supplier
- `supplierItemRevision`: The revision (or version) as provided by the supplier
- `supplierItemName`: The short name of this item as provided by the supplier
- `purchaseUnitOfMeasureIso`: The 3-letter purchase unit according to ISO 80000-1 which applies to this item

### Supplier shipment line

The supplier side of the shipment line:

- `despatchAdviceNumber`: The mandatory unique despatch advice number as provided by the supplier
- `despatchAdviceLinePosition`: The mandatory position in the despatch advice as provided by the supplier. The position is unique within the despatch advice and immutable
- `despatchQuantity`: The mandatory despatch quantity of this purchase order line or delivery schedule position
- `backorderQuantity`: The backorder quantity of this purchase order line or delivery schedule position

### Shipment line meta information

- `lastUpdatedAt`: ISO date and time with timezone when the shipment line was last updated in Tradecloud. A line has been added or changed if the `lines.meta.lastUpdatedAt` equals the `shipment.meta.lastUpdatedAt`

## Shipment locations

The departure and destination locations together with arrival and departure date/times of a shipment:

- `departure`: The departure location and dates, see [Shipment departure](#shipment-departure)
- `destinations`: One or more destination locations with arrival and departure date/times, see [Shipment destination](#shipment-destination)

### Shipment departure

A shipment departure location with ETD and ATD dates:

- `location`: The departure location, see [Shipment location](#shipment-location)
- `etdDate`: The Estimated Time of Departure of this shipment from this location
- `atdDate`: The Actual Time of Departure of this shipment from this location

### Shipment destination

A shipment place, port, or final destination with location, ETA time window, ATA, ETD, and ATD dates:

- `location`: The location where the shipment should arrive next, see [Shipment location](#shipment-location)

Estimated start and end date/times indicate the scheduled time window of arrival:

- `etaStartDate`: The Estimated Time of Arrival period start date of this shipment at this destination
- `etaStartTime`: The Estimated Time of Arrival period start time of this shipment at this destination
- `etaEndDate`: The Estimated Time of Arrival period end date of this shipment at this destination
- `etaEndTime`: The Estimated Time of Arrival period end time of this shipment at this destination

- `ataDate`: The Actual Time of Arrival of this shipment at this destination
- `etdDate`: The Estimated Time of Departure of this shipment from this location
- `atdDate`: The Actual Time of Departure of this shipment from this location

## Shipment location

- `locationType`: A location type according to ICC [Incoterms 2020](https://iccwbo.org/business-solutions/incoterms-rules/incoterms-2020/):

  - `AgreedPlace` (used with EXW, FCA)
  - `PortOfLoading` (used with FAS, FOB)
  - `PortOfDestination` (used with CFR, CIF)
  - `PlaceOfDestination` (used with CPT, CIP)
  - `FinalDestination` (used with DAP, DPU, DDP)

- `id`: The required identifier for the location, in context of `idSchema`
- `idScheme`: Scheme providing context to the location identifier, like [GLN](https://www.gs1.org/standards/id-keys/gln)
- `names`: One or more location names. It is recommended to provide at least one name
- `addressLines`: One or more location address lines
- `postalCode`: Location postal code
- `city`: Location city
- `countryCodeIso`: [ISO 3166-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) country code

## Shipment meta information

- `lastUpdatedAt`: ISO date and time with timezone when the shipment was last updated in Tradecloud, useful for polling shipments
- `supplierErpMeta`: The supplier's ERP meta information about this shipment
  - `despatchAdviceErpIssueDateTime`: Local date and time when the despatch advice of this shipment was issued in the supplier's ERP system

## Message meta information

- `messageId`: The Tradecloud identifier of this message
- `source`: Includes meta information about the source of this message:

  - `traceId`: The Tradecloud trace identifier of this message. All related messages in a flow will have the same traceId
  - `userId`: The Tradecloud user identifier which triggered the first message in a flow
  - `companyId`: The Tradecloud company identifier which triggered the first message in a flow

- `createdDateTime`: Date and time with time zone when this message was created
