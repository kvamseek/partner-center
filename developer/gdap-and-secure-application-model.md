---
title: Migrate your CPV/CSP applications to use granular delegated admin privileges
ms.topic: article
ms.service: partner-dashboard
ms.subservice: partnercenter-api
description: Use granular delegated admin privileges (GDAP) to securely provide consent for your Control Panel Vendor (CPV) and Cloud Solution Provider (CSP) applications, either per user tenant or by using an on-behalf-of (OBO) admin account.
author: kvamseek
ms.author: vamseekk
ms.date: 7/31/2023
---

# Migrate your CPV/CSP applications to use granular delegated admin privileges

**Appropriate roles**: Global admin | User management admin

[!INCLUDE [Important - Azure AD Graph is deprecated](./includes/azure-ad-graph-notice.md)]

This article shows how to update your Control Panel Vendor (CPV) and Cloud Solution Provider (CSP) applications to use granular delegated admin privileges (GDAP). The GDAP model helps enforce security best practices in the [secure application model](./enable-secure-app-model.md) and the [Microsoft identity platform application model](/azure/active-directory/develop/application-model), including providing minimum rights and a time-bound framework.


## Comparison of GDAP with DAP

The GDAP model replaces the delegated admin privileges (DAP) model, and it isn't backward compatible. The DAP model is being deprecated.

With the DAP admin agent model, you can grant your partner-managed app a set of configured permissions for all your customers in your tenant without review. This process is called [preconsent](/graph/auth-cloudsolutionprovider?tabs=azuread#pre-consent-your-app-for-all-your-customers). This process exposes the customer tenant in a way that's difficult for a partner to govern. It potentially escalates nonprivileged users and tasks to a privileged context.

The risk for using preconsent is further amplified because partners can't review or audit the consents. Although the **Azure AD Enterprise Application** page shows other consents, it doesn't show applications that preconsents have consented to. This legacy behavior doesn't align with the minimum-rights concept in the Microsoft identity platform.

In the GDAP model, either the customer or an admin with an on-behalf-of (OBO) relationship to the customer consents to allow the partner-managed applications to use their tenant. This behavior provides traceability for the customer and aligns to the Microsoft identity platform application model and the secure application model framework.

GDAP doesn't require you to create a specific relationship or security group for your application service principal.

For more information, see [Use the secure application model framework](./secure-app-model-framework.md#secure-application-development).

## Application permissions and user Azure AD roles

You can assign applications permissions in Azure Active Directory (Azure AD) on the **API permissions** tab.

With GDAP, you can no longer add Azure AD roles to an application by using relationships or through inclusion in a security group. Users have roles that are assigned directly through the Azure portal or indirectly through group assignment. Users can't have application permissions.

## Application consent

Application consent is the process of a resource owner granting authorization for a client application to access protected resources, under specific permissions, on behalf of the resource owner.

The following table lists the application service models that work with application consent.

| Application model | App consent | OBO |
|-------------------|-------------|--------------------|
|Multitenant application only (DAP only, not supported in GDAP) | Yes | No |
|Multitenant application + user | Yes | No |
|Multitenant application + user + OBO | Yes | Requires a GDAP relationship |

### Explicit multitenant application-only consent

Explicit application-only consent to a customer tenant isn't supported for third-party application developers who use GDAP. Such application-only consent isn't compatible with the time-limited minimum-rights contract that GDAP manages.

### Explicit multitenant application + user consent

Partner Center provides an API that allows a CPV or CSP to provide consent to their application through automation in the customer's tenant. Explicit app + user consent is required for every customer tenant.

The app + user pattern respects the time-limited minimum-rights contract that GDAP manages. For more information, see:

- [REST API for automating explicit CPV/CSP application + user consent in a customer tenant](./control-panel-vendor-apis.md)
- [PowerShell cmdlet for calling the API](/powershell/module/partnercenter/new-partnercustomerapplicationconsent?view=partnercenterps-3.0&preserve-view=true)

This API requires the calling partner user to be a member of a security group that has a GDAP relationship with the target customer/tenant. The GDAP relationship and associated security group must include *at least one* of these confirmed roles:

- Global Administrator
- Application Administrator (replaced Privileged Role Administrator)
- Cloud Application Administrator

> [!NOTE]
> Use of Privileged Role Administrator is no longer recommended.

The partner user must also be a member of the AdminAgents security group, which is required for calling the Partner Center APIs.

### Use of an admin account to provide consent on behalf of users in the secure application model

Partners can automatically provide consent to an application by setting up an OBO admin account, setting permissions, generating a temporary token, and associating the account with the user.

1. Create a new user account or choose an existing user account to be used as the CPV/CSP OBO account (for example, `AdminOnBehalfOf@contoso.onmicrosoft.com`).
1. Create a security group to be associated with your customer's GDAP relationship (for example, **AdminOnBehalfOfSG**).
1. Add your OBO user (`AdminOnBehalfOf@contoso.onmicrosoft.com`) to the customer's GDAP security group (**AdminOnBehalfOfSG).**
1. Define the following GDAP relationship parameters. You'll use these later.
   - Duration in days.
   - Requested Azure AD roles needed for the OBO.
   - When you want to automate the application consent as described in the preceding section. The GDAP relationship should include at least one of the following: Cloud Application Administrator, Application Administrator, Global Administrator to do the consent operation by using the API.
1. The CPV or CSP either creates a new multitenant application registration or uses an existing registration in the partner tenant.

   Record the application ID (for example, **A5000000-F000-4000-8000-300000000000**).
1. Generate and renew the OBO refresh token by using the multitenant application + **AdminOnBehalfOf** user identity generated in step 1.

   The following examples show how to create the respective token by using one-time interactive sign-in. Ensure that the sign-in uses multifactor authentication (MFA), because the refresh token must be created through MFA to work for OBO scenarios.

   - [Enable the secure app model](./enable-secure-app-model.md#samples)
   - [C# example](https://github.com/microsoft/Partner-Center-DotNet-Samples/tree/master/secure-app-model)
   - [.NET example](https://github.com/microsoft/Partner-Center-DotNet-Samples/tree/master/secure-app-model)

   Store your OBO user's refresh token in a secure location that can be accessed from your multitenant application. Azure Key Vault can be one option but isn't required. For more information, see the [Azure Key Vault overview](/azure/key-vault/general/overview) and the [Key Vault API documentation](/rest/api/keyvault/).

   Ensure that the stored refresh token is renewed at least every 90 days to avoid expiration. You can do this within your automation code or by developing a standalone app or script that renews the token. Whenever a new access token is created from the stored refresh token, a new refresh token with a 90-day lifetime is generated.

   Whenever you need to authenticate to the customer tenant for operations, get the most recent refresh token from your secure store and use it to generate an access token (and new refresh token) for authentication.

1. For each customer who will use your multitenant application and for whom you want to run activities through delegated administration, take the following steps:
   1. Create a GDAP relationship by using the information defined in step 4.
   1. Submit the GDAP relationship for approval.
   1. After the GDAP relationship is active, assign the security group defined in step 2 with the appropriate Azure AD roles defined in step 4.
   1. Make sure that an admin has granted consent for your application in the customer's tenant. For the automatic consent approach, you can do this after GDAP is established. For manual consent, a customer's admin can do this before GDAP is set up.

> [!NOTE]
> You can use the refresh token generated in step 6 for authentication against each customer. You don't need to take step 6 for each customer separately. When you're doing operations in a customer tenant, you take the initially generated token and exchange it for a token that's generated against the customer tenant. This is possible because of the GDAP relationship/roles and the application consent.

To set up multiple customers at scale, we recommend the following process:

- For new customers where no delegation privilege exists, include one of the prerequisite consenting roles in your initial GDAP relationship request (for example, Cloud Application Administrator).
  
  Alternatively, if you prefer short-term delegation of privileges, evaluate if you can use a second GDAP relationship request with a short duration (like one day) by using a permission that allows the consent delegation (like Cloud Application Administrator). This approach allows removing the more privileged role after you verify consent function. You can manually remove this second GDAP request at any time.
- For customer cases where a delegation privilege exists and the partner has DAP, perform the automated consent in bulk (for example, by using the PowerShell script `new-PartnerCustomerApplicationConsent`).

When you're migrating from DAP to GDAP by using the partner-led bulk migration tool, set up the respective roles that allow for the partner to consent for migrated customers. For customers who have only partial GDAP role delegations, the partner requests the Cloud Application Administrator role (or a similar role from the list of role prerequisites) for the customer to manually approve.

## Consent API

This section discusses the API CPV/CSP application + user consent in customer tenant in greater detail.

### Identify enterprise applications and scopes (also known as permissions)

For each application for which you plan to give consent, map the application APIs and permissions to the JSON payload. You can find your application details in the Azure portal by selecting **Azure AAD: App Registrations "your app"** and then selecting the **API Permissions** tab.

Follow the steps in [Verify first-party Microsoft applications in sign-in reports](/troubleshoot/azure/active-directory/verify-first-party-apps-sign-in) in Azure AD to filter on Microsoft apps. Locate the enterprise application APIs referenced by your application and get their specific application IDs. These application IDs will be assigned to `enterpriseApplicationId` in the following JSON example.

The following IDs come from example application permissions:

|Application name | Application ID == **enterpriseApplicationId** |
|-----------------|----------------------------|
|Azure Active Directory|00000002-0000-0000-c000-000000000000|
|Microsoft Graph|00000003-0000-0000-c000-000000000000|

Include in the scope property the required permissions for each API. The scope property can contain all permissions (comma delimited) or a subset of permissions configured on the application for which you want to provide consent.

Example JSON payload:

```json
{
    "applicationId": "57667d41-992a-49b0-99d8-ddf68328373f",
    "applicationGrants": [
        {
            "enterpriseApplicationId":"00000002-0000-0000-c000-000000000000",
            "scope":"Directory.ReadWrite.All"
        },
        {
            "enterpriseApplicationId":"00000003-0000-0000-c000-000000000000",
            "scope":"Directory.ReadWrite.All"
        }
    ]
}
```

> [!NOTE]
> Before you call the API, ensure that the created authentication token uses the same application ID for which you want to give consent in the customer's tenant. You can use a popular website such as [jwt.ms](https://jwt.ms/) to decode your bearer token and ensure that your application IDs match. In the bearer token, `"appID":"57667d41-992a-49b0-99d8-ddf68328373f"` should match the `applicationID` value in the JSON payload.

### Get friendly names for permissions and scopes

The following information is useful if you want to discover the friendly names for application API permissions as displayed in the [Azure portal](https://portal.azure.com/) **Azure AD application registration** section for a specific application.

#### Get a list of your applications

Run ```graph api get application```.

Get a list of application IDs and display names. The `id` value is the application object ID.

```https://graph.microsoft.com/v1.0/applications?$select=id,displayName```

Get an application's `requiredResourceAccess` value, which contains your application API and permissions as viewed in the Azure portal. Replace `{applicationObjectId}` with the application ID from the previous step.

```https://graph.microsoft.com/v1.0/applications/{applicationObjectId}?$select=requiredResourceAccess](https://graph.microsoft.com/v1.0/applications/{applicationObjectId}?$select=requiredResourceAccess)```

Example response:

```rest
"requiredResourceAccess": [
    {
        "resourceAppId": "00000003-0000-0000-c000-000000000000",
        "resourceAccess": [
            {
                "id": "885f682f-a990-4bad-a642-36736a74b0c7",
                "type": "Scope"
            },
            {
                "id": "e1fe6dd8-ba31-4d61-89e7-88639da4683d",
                "type": "Scope"
            },
            {
                "id": "06da0dbc-49e2-44d2-8312-53f166ab848a",
                "type": "Scope"
            },
            {
                "id": "c5366453-9fb0-48a5-a156-24f0c49a4b84",
                "type": "Scope"
            }
        ]
    }
]
```

#### Get a service principal

Run [Graph api get servicePrincipal](/graph/api/serviceprincipal-get).

Get a specific service principal's `oauth2PermissionScopes` value. Replace `{resourceAppId}` with the value returned in the `requiredResourceAccess` array. (There might be more than one.)

```https://graph.microsoft.com/v1.0/servicePrincipals?$filter=appid eq '{resourceAppId}'&$select=oauth2PermissionScopes ```

Find the scope definitions by ID in the response and the friendly name stored in the `value` property.

Example edited response (reduced for clarity):

```
{
    "adminConsentDisplayName": "Manage Delegated Admin relationships with customers",
    "id": "885f682f-a990-4bad-a642-36736a74b0c7",
    "isEnabled": true,
     "type": "Admin",
    "value": "DelegatedAdminRelationship.ReadWrite.All"
},
{
    "adminConsentDisplayName": "Sign in and read user profile",
    "id": "e1fe6dd8-ba31-4d61-89e7-88639da4683d",
    "isEnabled": true,
    "type": "User",
    "value": "User.Read"
},
{
    "adminConsentDisplayName": "Read directory data",
    "id": "06da0dbc-49e2-44d2-8312-53f166ab848a",
    "isEnabled": true,
    "type": "Admin",
    "value": "Directory.Read.All"
},
{
    "adminConsentDisplayName": "Read and write directory data",
    "id": "c5366453-9fb0-48a5-a156-24f0c49a4b84",
    "isEnabled": true,
    "type": "Admin",
    "value": "Directory.ReadWrite.All"
},
```

## Missing security principals in a customer tenant

The application consent API requires that the application APIs (service principals) exist in the customer's tenant. You might see an error message like the following example when you're consenting. It signals that the application doesn't exist in the customer's tenant.

> "The app is trying to access a service 'c5393580-f805-4401-95e8-94b7a6ef2fc2' (Office 365 Management APIs) that your organization 'contosoxyz.onmicrosoft.com' lacks a service principal for. Contact your IT Admin to review the configuration of your service subscriptions or consent to the application in order to create the required service principal."

The example error says that the Office 365 Management API isn't installed in the customer's tenant. For prerequisites to ensure that the service principal is installed, see [Get started with Office 365 Management APIs](/office/office-365-management-api/get-started-with-office-365-management-apis).

To check that a service principal exists in the customer's tenant, you can call the Graph API for `servicePrincipals` in that tenant.

For the application that needs consent in the customer's tenant, you can query the application's `requiredResourceAccess` array. In that array, for each `resourceAppId` instance, you can call the API in the target tenant. Replace _{resourceIDvalue}_ with the `resourceAppId` value.

```https://graph.microsoft.com/v1.0/servicePrincipals?$filter=appid eq '{resourceID value}'&$select=id,appId,appDisplayName```

For example:

```https://graph.microsoft.com/v1.0/servicePrincipals?$filter=appid eq 'c5393580-f805-4401-95e8-94b7a6ef2fc2'&$select=id,appId,appDisplayName```

This is the result if the service principal is found:

```
    "value": [
        {
            "id": "6cf71994-a896-4e8a-a7a4-6d64276bf370",
            "appId": "c5393580-f805-4401-95e8-94b7a6ef2fc2",
            "appDisplayName": "Office 365 Management APIs"
        }
    ]
```

This is the result if the service principal is not found:

```
    "value": []
```

Your result will determine your path forward: omitting the service principal, determining why a service principal is missing for a customer, or other actions that are specific to your business.

## Manually requesting app consent

If you have the Global Administrator role in a customer's tenant, you can consent to the app yourself. In cases where the customer doesn't want to approve the Global Administrator role, you can ask them to enter the URI in a browser and manually consent themselves. After the consent is completed, your app should be able to run with the GDAP-enabled customer.

To get consent for your app in the customer's tenant, construct a URI as follows. Replace `{customertenant}` with the customer's tenant. Replace `{appid}` with the app for which you want to provide consent.

```https://login.microsoftonline.com/{customertenant}.onmicrosoft.com/adminconsent?client_id={appid}```

Enter the newly constructed URI in a web browser and follow the sign-in and consent prompts.

## Resources

The following resource links are a suggested reading order:

- **GDAP application consent**
  - [Partner Center authentication: partner consent](./partner-center-authentication.md#partner-consent)
  - [CPV/CSP API for an application: customer consent](./control-panel-vendor-apis.md)
- **Secure application model**
  - [Enable the secure application model framework](./enable-secure-app-model.md)
  - [Use the secure application model framework](./secure-app-model-framework.md)
  - [Create a secure partner application for a CSP and a CPV](./secure-sample-application.md)
  - [Partner Center samples: Secure app model](https://github.com/microsoft/Partner-Center-DotNet-Samples/tree/master/secure-app-model)
- **Microsoft identity platform**
  - [Build apps that sign in Azure AD users](/azure/active-directory/develop/howto-convert-app-to-be-multi-tenant)
  - [Azure AD built-in roles: Microsoft identity platform and OAuth2.0 on-behalf-of flow](/azure/active-directory/roles/permissions-reference)
  - [Scopes, permissions, and consent](/azure/active-directory/develop/v2-oauth2-on-behalf-of-flow)
  - [Access tokens](/azure/active-directory/develop/access-tokens)
  - [Consent framework](/azure/active-directory/develop/consent-framework)
  - [Glossary of terms in the Microsoft identity platform (consent)](/azure/active-directory/develop/developer-glossary#consent)
