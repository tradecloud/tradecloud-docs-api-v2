---
description: How to update your company's profile and settings.
---

# Update company profile and settings

Name and roles cannot be updated.

Update your profile and settings:

## Request

{% api-method method="put" host="" path="https://api.accp.tradecloud1.com/v2/company/:id" %} {% api-method-summary %} Update company by id (UUID) {% endapi-method-summary %}

### Body

In the request body you may update:

* profile fields
* integration settings, either webhook or ftp
* copy unchanged fields from [Get company profile and settings](get.md)

See the request body in [Swagger UI](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/company/specs.yaml#/company/updateCompanyRoute)

## Response

Only a HTTP status code will be returned
