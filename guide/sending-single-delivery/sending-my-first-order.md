# Option B: Sending a Single Delivery per order line

This page explains how to send your first order with a Single Delivery per order line.

### Sending the order

1. Set the URL to `https://api.accp.tradecloud1.com/v2/api-connector/order/single-delivery`
2. Set the HTTP Method to `POST`
3. Provide a **Basic Authentication** header, which contains the [username and password](../setup-integration-account.md) of the integration account.
4. Provide the JSON below as the request body. Make sure you replace `{{supplierAccountNumber}}` with the supplier account number you [provided](../setup-integration-account.md) for a test supplier.

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
      "scheduledDelivery": {
        "date": "2026-01-31",
        "quantity": 5
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
      }
    },
    {
      "position": "0002",
      "item": {
        "name": "Round tube 60x45",
        "purchaseUnitOfMeasureIso": "PCE"
      },
      "scheduledDelivery": {
        "date": "2026-02-07",
        "quantity": 10
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
      }
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
        <scheduledDelivery>
            <date>2026-01-31</date>
            <quantity>5</quantity>
        </scheduledDelivery>
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
    <line>
        <position>0002</position>
        <item>
            <name>Round tube 60x45</name>
            <purchaseUnitOfMeasureIso>PCE</purchaseUnitOfMeasureIso>
        </item>
        <scheduledDelivery>
            <date>2026-02-07</date>
            <quantity>10</quantity>
        </scheduledDelivery>
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
You can now log into the [Web Portal](https://portal.accp.tradecloud1.com) and go to the Order overview page. When you click the order, you will see a single order line with the 2 scheduled deliveries.

