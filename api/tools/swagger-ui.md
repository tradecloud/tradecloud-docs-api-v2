---
description: Using Swagger UI for API client development
---

# Swagger UI

You can use the [Swagger UI](https://swagger.io/tools/swagger-ui/) to explore and test the Tradecloud API.

Please refer to the API Environments page for an overview of the available Swagger UI documentation.

{% content-ref url="../environments.md" %}
[environments.md](../environments.md)
{% endcontent-ref %}

## Send an order using the Swagger UI

1.  Click the **Authorize** button on the top right

    <img src="../../.gitbook/assets/swaggerui/step1.png" alt="" data-size="original">
2.  Fill in your Basic authorization credentials of the integration user that was provided to you. Click **Authorize** and then **Close**.

    <img src="../../.gitbook/assets/swaggerui/step2.png" alt="" data-size="original">
3.  Click the endpoint you want to use and click on **Try it out**.

    <img src="../../.gitbook/assets/swaggerui/step3.png" alt="" data-size="original">
4.  Adjust the request body according to the data you want to send to Tradecloud.

    <img src="../../.gitbook/assets/swaggerui/step4.png" alt="" data-size="original">
5.  Click the **Execute** button.

    The **Responses** section in the Swagger UI should display the API response and the effects of your request should now be visible in the Tradecloud Portal.
