# Azure Active Directory Connector

The Azure Active Directory Connector enables seamless Single Sign-On (SSO) integration between your organization's Azure AD and Tradecloud, allowing your users to access Tradecloud using their existing corporate credentials.

## Key Benefits

- **Single Sign-On Experience** - Users can access Tradecloud with their existing Azure AD credentials
- **Automatic User Provisioning** - New users are automatically created in your Tradecloud company
- **Centralized Access Control** - Use Azure AD conditional access policies to control who can access Tradecloud
- **Enhanced Security** - Leverage your organization's existing security policies and multi-factor authentication
- **Reduced IT Overhead** - No need to manage separate Tradecloud user accounts

## How It Works

1. **User Authentication** - Users sign in through Azure AD using their corporate credentials
2. **Access Control** - Azure AD conditional access policies determine which users can access Tradecloud
3. **User Provisioning** - Permitted users are automatically synchronized and created in your Tradecloud company
4. **Seamless Access** - Users are redirected to Tradecloud with an authenticated session

## Prerequisites

Before setting up the Azure AD Connector, ensure you have:

- Administrative access to your organization's Azure Active Directory
- Appropriate permissions to register applications in Azure AD
- Access to configure conditional access policies (if required)
- Contact with Tradecloud support for final configuration

{% hint style="info" %}
The Azure AD Connector is an add-on feature. Contact [sales@tradecloud1.com](mailto:sales@tradecloud1.com) for pricing and availability information.
{% endhint %}

## Setup Process

### For Customers

The setup process involves configuring your Azure AD environment to work with Tradecloud. This includes registering Tradecloud as an application, configuring permissions, and setting up token claims.

{% page-ref page="ad-setup.md" %}

### For Tradecloud Support

Tradecloud engineers will configure the backend systems to accept and process Azure AD authentication tokens from your organization.

{% page-ref page="tc-setup.md" %}

## Security Considerations

- Only users permitted by your Azure AD conditional access policies will be synchronized to Tradecloud
- User access can be revoked immediately by removing permissions in Azure AD
- All authentication flows use industry-standard OAuth 2.0 and OpenID Connect protocols
- No sensitive user data is stored outside of your Azure AD environment

## Support

For technical assistance with the Azure AD Connector setup:

- Contact Tradecloud support through [support@tradecloud1.com](mailto:support@tradecloud1.com)
- For sales inquiries, email [sales@tradecloud1.com](mailto:sales@tradecloud1.com)
