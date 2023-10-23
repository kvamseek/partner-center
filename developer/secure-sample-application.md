---
title: Secure partner application for CSP and CPV
description: Create a secure Partner Center application.
ms.date: 01/26/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.custom: has-azure-ad-ps-ref
ms.topic: article
author: Vamseek
ms.author: vijvala
---

# Create a secure partner application

You can implement the Secure Application Model framework by creating an application for either Cloud Solution Providers (CSPs) or Control Panel Vendors (CPVs).

[Implement secure application model](enable-secure-app-model.md)

[Steps to enable secure application model](enable-secure-app-model.md#samples)

[!INCLUDE [Important - Azure AD Graph is deprecated](./includes/azure-ad-graph-notice.md)]

## Create a Partner Center service principal

First, create a Microsoft Partner Center service principal in the CSP partner's tenant, where the multi-tenant application is going to be created.

For CSP partner tenants, this service principal should already exist. If not, create using the following steps.

In an administrator PowerShell window, run the following commands.

1. Install the AzureAD module.
   `Install-Module "AzureAD"`
2. Run Connect-AzureAD, this prompts for a user name and password. Enter the tenant admin credentials.
   `Connect-AzureAD`
3. Create a Microsoft Partner Center service principal.
   `New-AzureADServicePrincipal -DisplayName "Microsoft Partner Center" -AppId fa3d9a0c-3fb0-42cc-9193-47c7ecd2edbd`

## Create a multi-tenant application in the CSP partner's tenant

Use the following steps to make sure that the following application properties are set for the newly created multi-tenant application.

1. Sign in into [portal.azure.com](https://portal.azure.com )
2. Select Azure Active Directory and App registrations to create new registrations with multi-tenant.

:::image type="content" source="media/csp-register-app.png" alt-text="Screenshot showing Register an app modal." lightbox="media/csp-register-app.png":::

3. Select a user-facing display name for your application.
4. Select Supported account type: Accounts in any organizational directory (Any Azure AD directory - Multitenant).
5. Select a **platform** type "**Web**."
6. The **Redirect** URL must be your application redirect URL, which will show the consent success message to the partner and collect a refresh token. Make sure that the redirect URL of your app is set to an endpoint where a live web app is running. This app needs to accept the [authorization code](enable-secure-app-model.md#get-authorization-code) from the Azure AD sign-in call.
7. Go to **Manage** > **Certificates & secrets** > **+New client secret** in the Client secrets tab.

> [!NOTE]
> You'll need the following information from your web app's settings in Azure AD:
>
> - Application ID
> - Application secret

:::image type="content" source="media/csp-certificates-secrets.png" alt-text="Screenshot showing Certificates and secrets." lightbox="media/csp-certificates-secrets.png":::

## Apply permissions

Make sure the following permissions are set for the multi-tenant application.

In the **API permission** section:
- There shouldn't be any direct **Application Permissions** to the multi-tenant application.
- Follow the below path for adding Delegated permissions for Microsoft Graph:
     - **API Permissions** > **Add a permission** > **Microsoft APIs** > **Microsoft Graph** > **Delegated Permissions**
        - `DelegatedAdminRelationship.ReadWrite.All
User.Read.All`

   :::image type="content" source="media/csp-request-api-permissions.png" alt-text="Screenshot showing partner app request API permissions." lightbox="media/csp-request-api-permissions.png":::

   - Follow the below path for adding Delegated permissions for *Microsoft Partner Center - Grant Access Partner Center* permissions under **Delegated Permissions**:
     - **API Permissions** > **Add a permission** > **APIs my organization uses** > **Microsoft Partner Center** > **Delegated Permissions** > **User Impersonation**

   :::image type="content" source="media/csp-permissions.png" alt-text="Screenshot showing partner app A P I permissions." lightbox="media/csp-permissions.png":::

## Provide consent link

Present the partner with the consent link and have them sign in with their service account to approve the application to act on behalf of the service account on the partner tenant.

The CSP partner user **must be** a Global Admin and an Admin Agent to consent the multi-tenant application.

### Multi tenant application

The multi tenant `ApplicationID` needs to be replaced with your Application ID. 

Navigate to **App Registrations** and select the Application (Client) ID and replace below.

:::image type="content" source="media/csp-azure-ad-client.png" alt-text="Screenshot showing Partner Azure A D client." lightbox="media/csp-azure-ad-client.png":::

### Get authorization code

You must get an authorization code for your web app from the Azure AD sign-in call:

1. Sign in to [Azure AD](https://login.microsoftonline.com/common/oauth2/authorize?client_id=Application-Id&response_mode=form_post&response_type=code%20id_token&scope=openid%20profile&nonce=1).
2. Replace **Application-Id** with your Azure AD app ID (GUID).
3. When prompted, sign in with your user account with MFA configured.
4. When prompted, enter other MFA information (phone number or email address) to verify your sign-in.
5. After you're logged in, the browser will redirect the call to your web app endpoint with your authorization code. For example, the following sample code redirects to `https://localhost:44395/`.

```json
GET https://login.microsoftonline.com/common/oauth2/authorize?&client_id=<CSPApplicationId>&response_type=code&redirect_url=https://<CSPApplicationUrl_which_collects_refreshtoken>
```

or

```json
GET https://login.microsoftonline.com/common/oauth2/authorize?&client_id=<CSPApplicationId>&response_type=code
```

For China, use the following link:

```json
GET https://login.chinacloudapi.cn/common/oauth2/authorize ?&client_id= <CSPApplicationId>&response_type=code&redirect_url= https://<CSPApplicationUrl_which_collects_refreshtoken>
```

or

```json
GET https://login.chinacloudapi.cn/common/oauth2/authorize?&client_id= <CSPApplicationId>&response_type=code
```

Authorization code call trace: `https://localhost:44395/?code=<authorization_code>&<rest of properties for state>`

### Get refresh token

You must then use your authorization code to get a refresh token:

1. Make a POST call to the Azure AD sign-in endpoint `https://login.microsoftonline.com/CSPTenantID/oauth2/token` with the authorization code. For an example, see the following [sample call](enable-secure-app-model.md#sample-refresh-call).
2. Note the refresh token that is returned.
3. Store the refresh token in the Azure Key Vault. For more information, see the [Key Vault API documentation](/rest/api/keyvault/).

> [!NOTE]
> The resources mentioned in the below sample POST call are for GDAP-Graph APIs.
>
> Resources for other PC APIs are as follows:
>
> Partner Center APIs (`https://api.partnercenter.microsoft.com`)
>
> [GDAP APIs](https://graph.microsoft.com)
>
> Partner API (`https://api.partner.microsoft.com`)

#### Sample call

```json
POST  'https://login.microsoftonline.com/<partnerTenantId>/oauth2/token' \
--header 'content-type: application/x-www-form-urlencoded' \
--form 'grant_type="authorization_code"' \
--form 'client_id=<application_id or client_id>' \
--form 'resource="https://graph.microsoft.com"' \
--form 'code="<authorization_code>"'   
Response Body:

{
    "token_type": "Bearer",
    "scope": "DelegatedAdminRelationship.ReadWrite.All User.Read.All",
    "expires_in": "4549",
    "ext_expires_in": "4549",
    "expires_on": "1652886571",
    "not_before": "1652881721",
    "resource": "https://graph.microsoft.com",
    "access_token": "Access_token",
    "refresh_token": "Refresh_token",    
    "id_token": "Id_token"
}
```

## Set up key vault

First, create a new web application in the CSP partner's tenant. If the CPV application is used for calling the Partner Center APIs, CPV should create a new web application in the CPV partner's tenant.

If you're using Azure Key Vault:

1. Create the Azure Key Vault with the appropriate `<key-vault-name>` and it results in a DNS name like: `https://<key-vault-name>.vault.azure.net`
2. Add a refresh token to the key vault.

## Provide access to the key vault

In the access policies of the key vault, add the **KeyVaultAccessApp** with permissions to only manage the **Get** and **Set** aspects of a **Secret**.

:::image type="content" source="media/csp-sample-app-permissions-options.png" alt-text="Screenshot showing CSP partner app required permissions." lightbox="media/csp-sample-app-permissions-options.png":::

## Configure the prototype

The prototype has two applications:

- **Partner Consent**: Represents a web application designed to accept consent from a CSP partner and show a success message.
  - This application sets up consent and captures the refresh token of the consented user.
  - The consented user's refresh token is used for generating the access token for the CSP partner tenant.
- **CSP application** or **CPV application**: Represents a primary application, which calls Partner Center APIs and graph.
  - APIs to perform commerce and user actions on behalf of the partner.

This application retrieves the access token for a specific audience (Partner Center APIs or Graph) before calling respective APIs. It uses the refresh token that is stored securely in the key vault.

## Partner consent application (CSP)

### CSP web configuration

For the CSP partner application, the `web.config` file has the following sections called out. Update these values with corresponding application IDs and secrets. For your primary application, use "certificate" as the web application secret instead of plain secrets because it provides an extra layer of security.

```html
<!-- AppID that represents CSP application -->
<add key="ida:CSPApplicationId" value="CSPApplicationIdValue" />
<!--
Please use certificate as your client secret and deploy the certificate to your environment.
The following application secret is for sample application only. please do not use secret directly from the config file.
-->
<add key="ida:CSPApplicationSecret" value="CSPApplicationSecretValue" />
<!-- AppID that is given access for keyvault to store the refresh tokens --> <add key="ida:KeyVaultClientId" value="KeyVaultClientIdValue" />
<!--
Please use certificate as your client secret and deploy the certificate to your environment.
The following application secret is for sample application only. please do not use secret directly from the config file.
-->
<add key="ida:KeyVaultClientSecret" value="KeyVaultClientSecretValue" />
<!-- AAD instance: Global is .com, for different national clouds it changes German cloud: .de, China cloud: login.chinacloudapi.cn -->
<add key="ida:AADInstance" value="https://login.microsoftonline.com/" />
```

### CSP application configuration

For the CSP partner application, the `app.config` file has the following sections called out. Update the values with the corresponding application IDs and secrets. For your primary application, use "certificate" as the web application secret instead of plain secrets because it provides an extra layer of security.

```html
<!-- AppID that represents CSP application -->
<add key="ida:CPVApplicationId" value="CPVApplicationIdValue" />
<!--
Please use certificate as your client secret and deploy the certificate to your environment. The following application secret is for sample application only. please do not use secret directly from the config file.
-->
<add key="ida:CPVApplicationSecret" value="CPVApplicationSecretValue" />
<!-- AppID that is given access for keyvault to store the refresh tokens -->
<add key="ida:KeyVaultClientId" value="KeyVaultClientIdValue" />
<!--
Please use certificate as your client secret and deploy the certificate to your environment. The following application secret is for sample application only. please do not use secret directly from the config file.
-->
<add key="ida:KeyVaultClientSecret" value="KeyVaultClientSecretValue" />
<!-- AAD instance: Global is .com, for different national clouds it changes German cloud: .de,
China cloud: login.chinacloudapi.cn -->
<add key="ida:AADInstance" value="https://login.microsoftonline.com/" />
```

## Partner consent application (CPV)

CSPs using the CPV application can call the [ApplicationConsent API](./control-panel-vendor-apis.md) to create the service principal on the customer tenant to access the Microsoft Graph to manage the customer tenants. For more information, see [Partner Center authentication](partner-center-authentication.md#control-panel-provider-authentication).

### CPV web configuration

For the CSP partner application, the `web.config` file has the following sections called out. Update these values with corresponding application IDs and secrets. For your primary application, use "certificate" as the web application secret instead of plain secrets because it provides an extra layer of security.

```html
<!-- AppID that represents Control panel vendor application -->
<add key="ida:CPVApplicationId" value="CPVApplicationIdValue" />
<!--
Please use certificate as your client secret and deploy the certificate to your environment. The following application secret is for sample application only. please do not use secret directly from the config file.
-->
<add key="ida:CPVApplicationSecret" value="CPVApplicationSecretValue" />
<!-- AppID that is given access for keyvault to store the refresh tokens -->
<add key="ida:KeyVaultClientId" value="KeyVaultClientIdValue" />
<!--
Please use certificate as your client secret and deploy the certificate to your environment. The following application secret is for sample application only. please do not use secret directly from the config file.
-->
<add key="ida:KeyVaultClientSecret" value="KeyVaultClientSecretValue" />
<!-- AAD instance: Global is .com, for different national clouds it changes German cloud: .de, China cloud: login.chinacloudapi.cn -->
<add key="ida:AADInstance" value="https://login.microsoftonline.com/" />
```

### CPV application configuration

For the CPV partner application, the `app.config` file has the following sections called out. Update the values with the corresponding application IDs and secrets. For your primary application, use "certificate" as the web application secret instead of plain secrets because it provides an extra layer of security.

```html
<!-- AppID that represents Control panel vendor application -->
<add key="ida:CPVApplicationId" value="CPVApplicationIdValue" />
<!--
Please use certificate as your client secret and deploy the certificate to your environment. The following application secret is for sample application only. please do not use secret directly from the config file.
-->
<add key="ida:CPVApplicationSecret" value="CPVApplicationSecretValue" />
<!-- AppID that is given access for keyvault to store the refresh tokens -->
<add key="ida:KeyVaultClientId" value="KeyVaultClientIdValue" />
<!--
Please use certificate as your client secret and deploy the certificate to your environment. The following application secret is for sample application only. please do not use secret directly from the config file.
-->
<add key="ida:KeyVaultClientSecret" value="KeyVaultClientSecretValue" />
<!-- AAD instance: Global is .com, for different national clouds it changes German cloud: .de, China cloud: login.chinacloudapi.cn -->
<add key="ida:AADInstance" value="https://login.microsoftonline.com/" />
```
