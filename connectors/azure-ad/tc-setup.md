---
description: >-
  This page describes the configurations needed on Tradecloud side to enable
  Azure AD Single Sign-On integration for your users
---

# Azure AD Connector - Tradecloud Configuration

{% hint style="info" %}
This configuration is performed by Tradecloud support team. Please provide the required information below when requesting setup.
{% endhint %}

## Overview

After configuring Azure AD (as described in [Azure AD Setup](ad-setup.md)), Tradecloud needs to be configured to recognize and authenticate users from your Azure AD tenant. This involves setting up both frontend and backend configurations.

## Prerequisites

Before requesting Tradecloud configuration, ensure you have:

- ✅ Completed the [Azure AD Setup](ad-setup.md) steps
- ✅ Your Azure AD **Tenant ID** (available in Azure Portal > Azure Active Directory > Properties)
- ✅ Your Azure AD **Client ID** (from the registered application)
- ✅ Your **Tradecloud Company ID** (provided by Tradecloud support)
- ✅ List of **email domains** that should use Azure AD authentication

## Configuration Information Required

Please provide the following information to Tradecloud support for configuration:

| Information       | Description                                            | Example                                          |
| ----------------- | ------------------------------------------------------ | ------------------------------------------------ |
| **Tenant ID**     | Your Azure AD tenant identifier                        | `12345678-1234-1234-1234-123456789abc`           |
| **Client ID**     | Application (client) ID from Azure AD app registration | `87654321-4321-4321-4321-cba987654321`           |
| **Company ID**    | Your Tradecloud company identifier (UUID)              | `abcd1234-5678-9012-3456-789012345678`           |
| **Email Domains** | Domains that should use Azure AD authentication        | `yourcompany.com`, `yourcompany.onmicrosoft.com` |
| **Environment**   | Tradecloud environment (production/acceptance)         | `production`                                     |

## How the Configuration Works

### 1. Frontend Configuration

The frontend configuration maps email domains to Azure AD connections and handles the authentication flow.

**Configuration File**: `src/app/auth/routes/login/state/sso.connections.ts`

```typescript
// Azure AD connection mappings
export const azureAppMappings: AzureConnectionMappings = {
  yourcompany_prod: {
    clientId: "87654321-4321-4321-4321-cba987654321",
    tenantId: "12345678-1234-1234-1234-123456789abc",
  },
  yourcompany_accp: {
    clientId: "87654321-4321-4321-4321-cba987654321",
    tenantId: "12345678-1234-1234-1234-123456789abc",
  },
};

// Global domain mappings - which connection to use for each domain
const globalDomainMappings: SsoConnectionMap = {
  "yourcompany.com": "yourcompany_prod",
  "yourcompany.onmicrosoft.com": "yourcompany_prod",
};

// User-specific overrides (optional)
const connectionsByEmail: { [email: string]: AzureConnection } = {
  "testuser@yourcompany.onmicrosoft.com": "yourcompany_accp",
};
```

**Key Components:**

- **azureAppMappings**: Maps connection names to Azure AD credentials
- **globalDomainMappings**: Maps email domains to connection names
- **connectionsByEmail**: User-specific overrides for testing or special cases

### 2. Backend Configuration

The backend services (authentication and user microservices) need to validate JWT tokens and map users to the correct Tradecloud company.

**Configuration Files**:

- `authentication/src/main/resources/application.conf`
- `user/src/main/resources/application.conf`

```hocon
sso {
   domainMapping = [
     {
        domain = "yourcompany.com"
        companyId = "abcd1234-5678-9012-3456-789012345678"
        tenantId = "12345678-1234-1234-1234-123456789abc"
     },
     {
        domain = "yourcompany.onmicrosoft.com"
        companyId = "abcd1234-5678-9012-3456-789012345678"
        tenantId = "12345678-1234-1234-1234-123456789abc"
     }
   ]
}
```

**Configuration Properties:**

- **domain**: Email domain that should use this configuration
- **companyId**: Tradecloud company ID (UUID) where users will be created
- **tenantId**: Azure AD tenant ID for JWT token validation

## Testing the Configuration

After configuration is complete, test the integration:

1. **Navigate** to your Tradecloud environment login page
2. **Enter** an email address from your configured domain
3. **Verify** you're redirected to Azure AD for authentication
4. **Complete** the Azure AD login process
5. **Confirm** you're redirected back to Tradecloud with access

## Troubleshooting

### Common Issues

| Issue                           | Possible Cause            | Solution                                  |
| ------------------------------- | ------------------------- | ----------------------------------------- |
| User not redirected to Azure AD | Domain not configured     | Verify domain mapping in frontend config  |
| Authentication fails            | Invalid tenant/client ID  | Double-check Azure AD credentials         |
| User created in wrong company   | Incorrect company mapping | Verify backend domain mapping             |
| Token validation errors         | Tenant ID mismatch        | Ensure backend tenant ID matches Azure AD |
