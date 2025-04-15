# 1. Getting an Integration Account

In order to get an Integration account and a test supplier:

1. Send an email to [Tradecloud Support](../support.md) including:
   * 2 email addresses:
     * **An integration email address**: This should be a non-personal email address on a company domain like `tradecloud@company.com`. The email address must have an mailbox to receive an invite email.
     * **A buyer email address**: This can be a personal email address on a company domain like `firstname.lastname@company.com`. This email will be used to log into the Web Portal.
   * Your company name
   * For a test supplier:
     * The company name of a supplier
     * The account or relation number that the supplier has in your ERP.
     
     In order to develop the integration, you only need to provide this information for one arbitrary supplier in your ERP.
2. Once you have received an integration account, you can test its username and password against `https://api.accp.tradecloud1.com/v2/authentication/login` (See [Swagger API Specs](https://swagger-ui.accp.tradecloud1.com/?url=https://api.accp.tradecloud1.com/v2/authentication/specs.yaml#/authentication/login))


