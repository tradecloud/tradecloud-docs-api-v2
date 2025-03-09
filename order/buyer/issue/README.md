---
description: How to issue a new purchase order as a buyer
---

# Issue a new order

As a buyer, you can send either a **new order** or an [**updated order**](../update.md) to your supplier.

## Order process

{% hint style="info" %}
New order lines will have order process status `Issued` and logistics status `Open`
{% endhint %}

## Sending methods

### Delivery schedule options

Choose the appropriate endpoint based on your ERP system's delivery handling capabilities:

- Use the [Send order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendOrderByBuyerRoute) endpoint when your ERP system supports delivery schedules natively
- Use the [Send single delivery order](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/api-connector/specs.yaml#/buyer-endpoints/sendSingleDeliveryByBuyerRoute) endpoint for single delivery per order line

For more details on choosing between delivery schedule options:

{% page-ref page="delivery-schedule.md" %}

{% hint style="info" %}
When sending an order the provided supplier account number will be verified.
{% endhint %}

## Order

* `companyId`: the optional Tradecloud company identifier. You only have to provide a companyId when your integration user account has authorization for multiple companies.
* `buyerParty`: the optional legal entity that purchases the goods or services. See [Company party](#company-party).
* `buyerAccountingParty`: the optional legal entity that receives and handles the invoice. The supplier must send the invoice to the buyer accounting party when specified. See [Company party](#company-party).
* `supplierAccountNumber`: the supplier account number as known in your ERP system.

{% hint style="warning" %}
The `supplierAccountNumber` must be set in the Tradecloud connection in the portal, after the connection request has been accepted by the other party.
{% endhint %}

* `supplierParty`: the optional legal entity that sells the goods or services. See [Company party](#company-party).
* `purchaseOrderNumber`: the purchase order number as known in your ERP system.

{% hint style="warning" %}
The `purchaseOrderNumber` must not contain whitespace characters.
{% endhint %}

* `destination`: the delivery destination of this order as known in your ERP system
* `contact.email`: the buyer employee responsible for this order. The user with this email address should be active in Tradecloud.
* `supplierContact.email`: if known, the supplier employee responsible for this order. The user with this email address should be active in Tradecloud.

{% hint style="warning" %}
`id`, `supplierAccountNumber`, `purchaseOrderNumber`, `destination.code` and `contact.email` should be unique within your company and never change. Never renumber or re-use identifiers, numbers or code's.
{% endhint %}

### Company party

The optional buyer, buyer accounting or supplier company party:

* `id`: the optional identifier for the party, for example a GLN.
* `idScheme`: the optional scheme, providing context to the identifier. Eg. `"KvK"`, `"GLN"`, etc.
* `names`: the legal names of the party. It is recommended to provide at least one name.
* `addressLines`: the location address lines of the party. It is recommended to provide at least one address line.
* `postalCode`: the location postal code of the party. Provide when `addressLines` are provided.
* `city`: the location city of the party. Provide when `addressLines` are provided.
* `countryCodeIso2` the ISO 3166-1 alpha-2 country code of the party. Provide when `addressLines` are provided.
* `countryName` the optional country name of the party.

### Other order fields

* `description`: a free format additional description of this order
* `terms`: the order terms as agreed with your supplier
* `indicators`: various order level indicators, see:

{% page-ref page="indicators.md" %}

* `properties`: are key-value based custom fields. You can user as many as needed, but too many will clutter the portal. Use `\n` for a new line in the value.
* `notes`: are simple custom fields. You can user as many as needed, but too many will clutter the portal. Use `\n` for a new line.
* `labels`: value-added services labels on order level. Please note the practicable number of labels is dependent on the supplier.
* `documents`: contain meta data and link of attached documents. The total number of documents is limited to 100 documents per order header. See:

{% page-ref page="attach-document.md" %}

* `orderType`: the order type, one of `Purchase`, `Forecast` or `RFQ`. Default `Purchase`.

## Lines

`lines`: a purchase order contains one or multiple lines. The total number of lines is limited to 500 lines per order. It is structured as a JSON element in the `lines` JSON array.

* `position`: the required line position identifier within the purchase order
* `row`: the optional row label for this position. Only use a row when there is a distinction between position and row in your ERP system. Do NOT use row as identifier.

{% hint style="warning" %}
`lines.position` should be unique within the order and never change. Never renumber or re-use `position` numbers.
{% endhint %}

### Item

`lines.item`: the item \(or article, goods\) to be delivered

* `number`: the item code or number as known in your ERP
* `revision`: the revision \(or version\) of this item number
* `name`: the item short name
* `purchaseUnitOfMeasureIso`: the purchase unit according to ISO 80000-1, a typical example is `PCE`
* `supplierItemNumber`: the item code or number as known at the supplier. Required in case of wholesale suppliers.

{% hint style="warning" %}
`item.number` and `item.supplierItemNumber` are optional and may be left empty, for example in case of service or RFQ orders.

Leaving the `item.number` and `item.supplierItemNumber` both empty is not recommended for integrated suppliers, as the supplier might reject the order line.

`item.number` should be unique within the buyer's company and never change. Never renumber or re-use `item.number`s for a different item.
{% endhint %}

### Item details

`lines.itemDetails`: detailed part information initially provided by buyer.

{% hint style="info" %}
The buyer may send item details to inform the supplier about part information.  
The supplier may check, change and add item details if they are not correct or incomplete.  
The webhook `orderEvent.lines.itemDetails.mergedItemDetails` will contain the merged original item details added by the buyer merged with the changed or added item details by the supplier.
{% endhint %}

* `countryOfOriginCodeIso2`: The ISO 3166-1 alpha-2 country code of manufacture, production, or growth where an article or product comes from.
* `combinedNomenclatureCode`: A tool for classifying goods, set up to meet the requirements both of the Common Customs Tariff and of the EU's external trade statistics.
* `netWeight`: Net weight of one item.
* `netWeightUnitOfMeasureIso`: Net weight unit according to ISO 80000-1.
* `dangerousGoodsCodeUnece`: UN numbers or UN IDs are four-digit numbers that identify dangerous goods, hazardous substances and articles in the framework of international transport.
* `serialNumber`: is an unique identifier assigned incrementally or sequentially to an item, to uniquely identify it.
* `batchNumber`: is an identification number assigned to a particular quantity or lot of material from a single manufacturer

### Requested planned delivery schedule

Use the `lines.deliverySchedule` field when your ERP system supports a delivery schedule natively.

Or use the `lines.scheduledDelivery` field when using single delivery per order line.

Please see this page to choose between the delivery schedule or single delivery per order line:

{% page-ref page="delivery-schedule.md" %}

### Requested prices

`lines.prices`: the requested price. Advised is to provide only `netPrice` for its simplicity, used by most buyers, or alternatively `grossPrice` together with `discountPercentage`.

* `grossPrice`: the gross price. Use together with `discountPercentage`.
* `discountPercentage`: the discount percentage. Use together with `grossPrice`.
* `netPrice`: the net price.
  * `priceInTransactionCurrency`: at least provide a price in the transaction currency of the supplier, like `CNY` in China.
    * `value`: the price value has a decimal `1234.56` format with any number of digits.
    * `currencyIso`: the 3-letter currency code according to ISO 4217, like `EUR`, `USD` and `CNY`.
  * `priceInBaseCurrency`: provide a price in your base currency, like `EUR` in the EU.
    * `value`: the price value has a decimal `1234.56` format with any number of digits.
    * `currencyIso`: the 3-letter currency code according to ISO 4217, like `EUR`.
* `priceUnitOfMeasureIso`: the price unit according to ISO 80000-1. The purchase unit and price unit may be different.
* `priceUnitQuantity`: the item quantity at which the price applies. Typically this is 1 \(unit price\) or 100 \(the price applies to 100 items\)

### Requested charge lines

`lines.chargeLines`: the requested additional cost lines of an order line, independent of the order line prices, like transport, packing, administration, inspection and certification costs.

* `position`: the position used to identify a charge line.
* `chargeTypeCode`: the mandatory charge reason code according to [UNCL7161](https://docs.peppol.eu/poacc/upgrade-3/codelist/UNCL7161/)
* `chargeDescription`: a mandatory free text description, like "Transport costs".
* `quantity`: the mandatory quantity of this charge line.
* `price`: the mandatory price of this charge line.
  * `priceInTransactionCurrency`: the mandatory price in the transaction currency of the supplier, like `CNY` in China.
    * `value`: the price value has a decimal `1234.56` format with any number of digits.
    * `currencyIso`: the 3-letter currency code according to ISO 4217, like `EUR`, `USD` and `CNY`.
  * `priceInBaseCurrency`: the optional price in your base currency, like `EUR` in the EU.
    * `value`: the price value has a decimal `1234.56` format with any number of digits.
    * `currencyIso`: the 3-letter currency code according to ISO 4217, like `EUR`.
* `priceUnitOfMeasureIso`: the 3-letter price unit according to ISO 80000-1 which applies to the charge line price.

{% hint style="warning" %}
The single delivery variant, where charge lines are spread over multiple order lines having the same item, prices and terms, and each only one charge line, is not supported. Send a support request if you need it.
{% endhint %}

### Other line fields

* `description`: a free format additional description of this line
* `terms`: the line terms as agreed with your supplier
  * `contractNumber`: the agreed framework contract number
  * `contractPosition`: the related position within the framework contract
* `projectNumber`: Your project number reference
* `productionNumber`:  Your production number reference
* `salesOrderNumber`:  Your sales order reference \(not be confused with the supplier sales order number\)
* `indicators`: various line level indicators, see:

{% page-ref page="indicators.md" %}

When a line has no goods to be delivered, for example a service, fee or text line:

{% page-ref page="no-delivery-expected.md" %}

When your order process requires the buyer to always approve every line:

{% page-ref page="propose-when-accepted.md" %}

* `properties`: are key-value based custom fields. You can use as many as needed, but too many will clutter the portal.  Use `\n` for a new line in the value.
* `documents`: contain attached documents. The total number of documents is limited to 100 documents per order line. See:

{% page-ref page="attach-document.md" %}

* `notes`: are simple custom fields.You can use as many as needed, but too many will clutter the portal. Use `\n` for a new line.
* `labels`: value-added services labels on line level. Please note the practicable number of labels is dependent on the supplier.

## New order meta data

* `erpIssueDateTime`: Date and time the order was originally issued in your ERP system. `DateTime` has ISO 8601 local date/time format `yyyy-MM-ddThh:mm:ss`. See also [Standards](../../api/standards.md).
* `erpIssuedBy`: the user email or user name as known in your ERP system who issued this order

## Response

When the `/api-connector/order` API method returns HTTP status code 200, the order was successfully queued for processing by Tradecloud. Processing takes usually less then a second, after which the order is available in the portal and is forwarded to the supplier ERP integration.
