# Option A: Sending a Delivery Schedule per order line

This page explains how to request deliveries for order lines by means of a Delivery Schedule. A Delivery Schedule can contain 1 or multiple requested deliveries for a single order line.

### Sending the order

1. Set the URL to `https://api.accp.tradecloud1.com/v2/api-connector/order`
2. Set the HTTP Method to `POST`
3. Provide a **Basic Authentication** header, which contains the [username and password](../setup-integration-account.md) of the integration account.
4. Provide the JSON below as the request body. Make sure you replace `{{supplierAccountNumber}}` with the supplier account number you have [configured](#configure-the-supplier-account-number) for a test supplier.


{% tabs %}
{% tab title="JSON" %}

Set the request body MIME-type to `application/json`.

```json
{
  "order": {
    "supplierAccountNumber": "{{supplierAccountNumber}}",
    "purchaseOrderNumber": "PO123456789",
    "destination": {
      "names": [
        "My Company Warehouse",
        "Dock 12"
      ],
      "countryCodeIso2": "NL"
    }
  },
  "lines": [
    {
      "position": "0001",
      "item": {
        "name": "Round tube 60x45",
        "purchaseUnitOfMeasureIso": "PCE"
      },
      "prices": {
        "netPrice": {
          "priceInTransactionCurrency": {
            "value": 1234.56,
            "currencyIso": "EUR"
          }
        },
        "priceUnitOfMeasureIso": "PCE",
        "priceUnitQuantity": 100
      },
      "deliverySchedule": [
        {
          "date": "2026-01-31",
          "quantity": 5
        },
        {
          "date": "2026-02-07",
          "quantity": 10
        }
      ]
    }
  ]
}
```

{% endtab %}
{% tab title="XML" %}

Set the request MIME-type to `application/xml`

```xml
<?xml version="1.0" encoding="UTF-8"?>
<SendOrderByBuyer>
	<order>
		<supplierAccountNumber>{{supplierAccountNumber}}</supplierAccountNumber>
		<purchaseOrderNumber>PO123456789</purchaseOrderNumber>
		<destination>
			<name>My Company Warehouse</name>
			<name>Dock 12</name>
			<countryCodeIso2>NL</countryCodeIso2>
		</destination>
	</order>
	<line>
		<position>0001</position>
		<item>
			<name>Round tube 60x45</name>
			<purchaseUnitOfMeasureIso>PCE</purchaseUnitOfMeasureIso>
		</item>
		<deliveryScheduleLine>
			<date>2026-01-31</date>
			<quantity>5</quantity>
		</deliveryScheduleLine>
        <deliveryScheduleLine>
            <date>2026-02-07</date>
            <quantity>10</quantity>
        </deliveryScheduleLine>
		<prices>
			<netPrice>
				<priceInTransactionCurrency>
					<value>1234.56</value>
					<currencyIso>EUR</currencyIso>
				</priceInTransactionCurrency>
			</netPrice>
			<priceUnitOfMeasureIso>PCE</priceUnitOfMeasureIso>
			<priceUnitQuantity>100</priceUnitQuantity>
		</prices>
	</line>
</SendOrderByBuyer>
```
{% endtab %}
{% endtabs %}


**That's all!**  
You can now log into the [Web Portal](https://portal.accp.tradecloud1.com) and go to the Order overview page. When you click the order line, you can now see the requested Delivery Schedule.

