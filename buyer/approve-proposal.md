---
description: How to approve an order change proposal by a supplier
---

# Approve order changes proposed by supplier

As buyer you can approve a order line proposal:

{% api-method method="post" host="https://api.accp.tradecloud1.com/v2" path="/order/{id}/line/{position}/proposal/approve" %}
{% api-method-summary %}
Approve proposed order line change
{% endapi-method-summary %}

{% api-method-description %}
Approve one order line proposal by using Tradecloud order id, position and order version.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=false %}
The Tradecloud order id  
\(not to be confused with the purchase order number\)
{% endapi-method-parameter %}

{% api-method-parameter name="position" type="string" required=true %}
The line position within the order
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=false %}
Bearer Access-Token
{% endapi-method-parameter %}

{% api-method-parameter name="Content-Type" type="string" required=false %}
application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="version" type="string" required=false %}
Tradecloud order version  
\(used for optimistic locking\)
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
  "ok": true
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
[Approve proposal OpenAPI specs](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/order/specs.yaml#/order/approveProposedLineChangesRoute)
{% endhint %}

{% hint style="warning" %}
It is not possible to use the order integration API, by \(re\)issueing an order, to approve order lines. If you need this, send a request to support.
{% endhint %}

