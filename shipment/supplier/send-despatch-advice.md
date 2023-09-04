---
description: How to send a new or updated despatch advice to Tradecloud
---

# Send a despatch advice

As supplier you can send either a **new or updated** despatch advice to your buyer.

{% hint style="info" %}
When a purchase order number is provided, but the item is not or partly provided, the item in the despatch advice will be enriched if Tradecloud can find the purchase order.
{% endhint %}

## Endpoint 

{% hint style="warning" %}
The shipment module is under development. The API and documentation may change.
{% endhint %}

Use the [Send despatch advice](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/supplier-endpoints/sendDespatchAdviceBySupplierRoute) to send a despatch advice to Tradecloud.

{% hint style="info" %}
When sending a despatch advice the provided buyer account number will be verified.
{% endhint %}

# Despatch advice

* `header`: the despatch advice header, see [Despatch advice header](#despatch-advice-header)
* `lines`: the despatch advice lines, see [Despatch advice line](#despatch-advice-line). The total number of lines is limited to 500 lines per shipment.
* `erpIssueDateTime`: local date and time at which the despatch advice of this shipment was issued in the supplier's ERP system

## Despatch advice header

* `supplierCompanyId`: the optional Tradecloud company identifier of the supplier. You only have to provide a companyId when your integration user account has authorization for multiple companies. 
* `buyerAccountNumber`: the buyer account code or number as known in the supplier's ERP system
* `despatchAdviceNumber`: the unique despatch advice number as provided by the supplier
* `shipment`: the shipment related to this despatch advice:

## Despatch advice shipment

* `shipmentNumber`: the related shipment number as known in the supplier's ERP system.

{% hint style="warning" %}
The `shipmentNumber` must not contain whitespace characters.
{% endhint %}

* `shipmentCompanyName`: the shipment company name, like the carrier or courier name.
* `trackingNumber`: the tracking number of the shipment as provided by the carrier or courier
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

## Despatch advice line

* `despatchAdviceLinePosition` the position in the despatch advice as provided by the supplier. The position is unique within the despatch advice and immutable.
* `purchaseOrderNumber`: the related purchase order number as provided by the buyer
* `purchaseOrderLinePosition`: the line position in the purchase order as provided by the buyer
* `item`: the item that is shipped, see [Shipment item](#shipment-item)
* `despatchQuantity` the despatched quantity of this purchase order line or delivery schedule position.
* `backorderQuantity`: the backorder quantity of this purchase order line or delivery schedule position.

### Despatch advice item

* `buyerItemNumber`: the required item code or number as provided by the buyer
* `buyerItemRevision`: the revision of the item as provided by the buyer
* `buyerItemName`: the short name of this item as provided by the buyer
* `supplierItemNumber`: the supplier item code or number as known in the supplier's ERP system
* `supplierItemRevision`: the revision (or version) as known in the supplier's ERP system
* `supplierItemName`: the short name of this item as known in the supplier's ERP system
* `purchaseUnitOfMeasureIso`: the the 3-letter purchase unit according to ISO 80000-1 which applies to this item
