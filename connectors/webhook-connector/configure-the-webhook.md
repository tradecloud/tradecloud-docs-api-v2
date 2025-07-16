# Configure your webhooks in the Tradecloud One portal

## Select one or more webhooks

A company admin can configure one or more webhooks in your company settings on the [Tradecloud One platform](http://portal.tradecloud1.com):

![Webhook Settings](../.gitbook/assets/webhook-settings.png)

- Select **My company** in the menu below your avatar.
- The **Settings** tab in the Company menu should be selected.
- Configure one or more **Webhook Integration**s below.

## Orders Webhook Integration

Enable the Order Webhook Integration if you want to receive a webhook trigger when an order has been issued or changed:

![Order Events](../.gitbook/assets/webhook-order-events.png)

A default set of order events will be enabled. The actual set you want to select wil be dependent on the capabilities of your integration and ERP system and your order process requirements. You can find a list of events here:

{% page-ref page="order-events.md" %}

### Order Delivery Schedule

![Order Delivery Schedule](../.gitbook/assets/webhook-order-delivery-schedule.png)

You can configure the way the delivery schedule is included in the body of a webhook POST request. You can choose between:

- Multiple delivery lines per order line. This will result in an `orderEvent` in the POST request body.
- Only one delivery line per order line. This will result in a `singleDeliveryOrderEvent` in the POST request body.

See [the API manual](https://docs.tradecloud1.com/api/introduction/api/delivery-schedule) to read about the delivery schedule versus the single delivery per order line.

## Order Documents Webhook Integration

Enable the Order Documents Webhook Integration if you want to receive a webhook trigger when an order document has been attached:

![Order Documents Events](../.gitbook/assets/webhook-order-documents-events.png)

You may choose whether you want to receive events for documents added by the buyer of an order, the suppplier, or both. You can find a list of events here:

{% page-ref page="order-documents-events.md" %}

## Shipments Webhook Integration

Enable the Shipment Webhook Integration if you want to receive a webhook trigger when a shipment has been issued or changed:

![Shipment Events](../.gitbook/assets/webhook-shipment-events.png)

A default set of shipments events will be enabled. The actual set you want to select wil be dependent on the capabilities of your integration and ERP system and your shipment process requirements. You can find a list of events here:

{% page-ref page="shipment-events.md" %}

## Method and URL

Configure the webhook method and endpoint URL:

![Webhook method and URL](../.gitbook/assets/webhook-url.png)

- Select **POST** as HTTP method.
- Enter your webhook endpoint URL:
  - The URL must start with **https://**

{% hint style="info" %}
Only `POST` is supported as HTTP method.
{% endhint %}

## Credentials

Finally, configure the credentials. Choose either Basic authentication, Bearer token or OAuth.

### Basic authentication

Tradecloud supports [Basic authentication](https://swagger.io/docs/specification/authentication/basic-authentication), where the client sends a HTTPS request with the `Authorization` header that contains the word `Basic` followed by a space and a base64-encoded string username:password.

Published as [RFC 7617 "The 'Basic' HTTP Authentication Scheme"](https://datatracker.ietf.org/doc/html/rfc7617)

![Webhook basic authentication](../.gitbook/assets/webhook-basic-auth.png)

Fill in username and password, as provided by your webhook configuration, and save the settings.

### Bearer token

Tradecloud supports [Bearer authentication](https://swagger.io/docs/specification/authentication/bearer-authentication/), where the client sends a HTTPS request with the `Authorization` header that contains word `Bearer` followed by a space and the static token.

Published as [RFC 6750 "The OAuth 2.0 Authorization Framework: Bearer Token Usage"](https://datatracker.ietf.org/doc/html/rfc6750)

![Webhook bearer token](../.gitbook/assets/webhook-bearer-token.png)

Fill in the token, as provided by your webhook configuration, and save the settings.

### OAuth

Tradecloud supports the Oauth 2.0 Client Credentials Grant, where the client sends a HTTPS form request with:

- `grant_type` with value `client_credentials`
- `client_id`, `client_secret` and `scope`

Published as the [RFC 6749 "Oauth 2.0 Client Credentials Grant"](https://datatracker.ietf.org/doc/html/rfc6749#section-4.4)

![Webhook Oauth](../.gitbook/assets/webhook-oauth.png)

Fill in the fields:

- `authentication URL`: the OAuth 2.0 token endpoint including your `Directory (tenant) ID`, for example `https://login.microsoftonline.com/<Tenant ID>/oauth2/v2.0/token`
- `client ID`: the `Application (client) ID` of your webhook client app as configured in Ms Azure AD
- `client Secret`: the `Client Secret Value` of your webhook client app as configured in Ms Azure AD
- `scope`: the scope granted to the webhook client app, for example containing the webhook endpoint `https://<webhook endpoint>/.default`.

## Testing

You can test webhook triggers using [webhook.site](https://webhook.site)

Use a bogus username and password when testing against webhook site.
