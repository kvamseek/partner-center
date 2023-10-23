---
title: Enable secure application model
description: Secure your Partner Center and control panel apps.
ms.date: 12/09/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: Vamseek
ms.author: vijvala
---

# Enabling the Secure Application Model framework

Microsoft is introducing a secure, scalable framework for authenticating cloud solution provider (CSP) partners and control panel vendors (CPV) through the Microsoft Azure Active Directory Multi-Factor Authentication (MFA) architecture.

You can use the new model to elevate security for Partner Center API integration calls. This helps all parties (including Microsoft, CSP partners, and CPVs) to protect their infrastructure and customer data from security risks.

The CSP program allows customers to buy Microsoft products and services through the partners. As per the agreement with Microsoft, partners are required to manage the environment for the customers they sell to and provide support. Customers who buy through this channel must place a high amount of trust in the partner they're buying from because the partner business has high-privilege admin access to the customer tenant.  

## Scope

This article relates to both CSPs and CPVs.

### CPVs

- A CPV is an independent software vendor that develops apps for use by CSP partners to integrate with Partner Center APIs.
- A CPV isn't a CSP partner with direct access to Partner Center or APIs.

### CSPs

- CSP indirect providers and CSP direct partners who are using app ID + user authentication and directly integrate with Partner Center APIs.

## Security requirements

For details on security requirements, see [Partner Security Requirements](../partner-security-requirements.md).

## Secure Application Model

Marketplace applications need to impersonate CSP partner privileges to call Microsoft APIs. Security attacks on these sensitive applications can lead to the compromise of customer data.

For an overview and details of the new authentication framework, see the [Secure Application Model framework](./secure-app-model-framework.md), which covers principles and best practices to make marketplace applications sustainable and robust from security compromises.

## Samples

The following overview documents and sample code describe how partners can implement the Secure Application Model framework:

- [Create a secure CSP or CPV app](./secure-sample-application.md)
- [.NET Samples](https://github.com/microsoft/Partner-Center-DotNet-Samples/tree/master/secure-app-model)
- [Java Samples](https://github.com/microsoft/Partner-Center-Java-Samples/tree/master/secure-app-model)

    [!INCLUDE [Partner Center Java SDK support details](./includes/java-sdk-support.md)]

- [REST instructions and samples](#rest)
- [PowerShell instructions and samples](#powershell)

## REST

To to make REST calls with the Secure Application Model framework with sample code, follow these steps:

1. [Create a web app](#create-a-web-app)

- [Enabling the Secure Application Model framework](#enabling-the-secure-application-model-framework)
  - [Scope](#scope)
- [Enabling the Secure Application Model framework](#enabling-the-secure-application-model-framework)
  - [Scope](#scope)
    - [CPVs](#cpvs)
    - [CSPs](#csps)
  - [Security requirements](#security-requirements)
  - [Secure Application Model](#secure-application-model)
  - [Samples](#samples)
  - [REST](#rest)
    - [Create a web app](#create-a-web-app)
    - [Get authorization code](#get-authorization-code)
      - [Authorization code call trace](#authorization-code-call-trace)
    - [Get refresh token](#get-refresh-token)
      - [Sample refresh call](#sample-refresh-call)
    - [Get access token](#get-access-token)
    - [Make Partner Center API calls](#make-partner-center-api-calls)
      - [Example Partner Center API call](#example-partner-center-api-call)
  - [PowerShell](#powershell)

### Create a web app

1. Sign in to the [Azure portal](https://portal.azure.com).

2. Create an Azure Active Directory (Azure AD) app.

3. Give delegated application permissions to the following resources, *depending on your application's requirements*. If necessary, you can add more delegated permissions for application resources.

   1. **Microsoft Partner Center** (some tenants show **SampleBECApp**)

   2. **Azure Management APIs** (if you're planning to call Azure APIs)

   3. **Windows Azure Active Directory**

4. Make sure that the home URL of your app is set to an endpoint where a live web app is running. This app needs to accept the [authorization code](#get-authorization-code) from the Azure AD login call. For example, in the example code in [the following section](#get-authorization-code), the web app is running at `https://localhost:44395/`.

5. Note the following information from your web app's settings in Azure AD:

   - Application ID
   - Application secret

> [!NOTE]
> It is recommended to [use a certificate as your application secret](/azure/active-directory/develop/active-directory-certificate-credentials). However, you can also create an application key in the Azure portal. The sample code in [the following section](#get-authorization-code) uses an application key.

### Get authorization code

You must get an authorization code for your web app to accept from the Azure AD login call:

1. Log in to [Azure AD](https://login.microsoftonline.com/common/oauth2/authorize?client_id=Application-Id&response_mode=form_post&response_type=code%20id_token&scope=openid%20profile&nonce=1).

    Be sure to log in with the user account from which you make Partner Center API calls (such as an admin agent or sales agent account).

2. Replace **Application-Id** with your Azure AD app ID (GUID).

3. When prompted, log in with your user account with MFA configured.

4. When prompted, enter more MFA information (phone number or email address) to verify your login.

5. After you're logged in, the browser will redirect the call to your web app endpoint with your authorization code. For example, the following sample code redirects to `https://localhost:44395/`.

#### Authorization code call trace

```http
POST https://localhost:44395/ HTTP/1.1
Origin: https://login.microsoftonline.com
Upgrade-Insecure-Requests: 1
Content-Type: application/x-www-form-urlencoded
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8
Referrer: https://login.microsoftonline.com/kmsi
Accept-Encoding: gzip, deflate, br
Accept-Language: en-US,en;q=0.9
Cookie: OpenIdConnect.nonce.hOMjjrivcxzuI4YqAw4uYC%2F%2BILFk4%2FCx3kHTHP3lBvA%3D=dHVyRXdlbk9WVUZFdlFONVdiY01nNEpUc0JRR0RiYWFLTHhQYlRGNl9VeXJqNjdLTGV3cFpIWFg1YmpnWVdQUURtN0dvMkdHS2kzTm02NGdQS09veVNEbTZJMDk1TVVNYkczYmstQmlKUzFQaTBFMEdhNVJGVHlES2d3WGlCSlVlN1c2UE9sd2kzckNrVGN2RFNULWdHY2JET3RDQUxSaXRfLXZQdG00RnlUM0E1TUo1YWNKOWxvQXRwSkhRYklQbmZUV3d3eHVfNEpMUUthMFlQUFgzS01RS2NvMXYtbnV4UVJOYkl4TTN0cw%3D%3D

code=AuthorizationCodeValue&id_token=IdTokenValue&<rest of properties for state>
```

### Get refresh token

You must then use your authorization code to get a refresh token:

1. Make a POST call to the Azure AD login endpoint `https://login.microsoftonline.com/CSPTenantID/oauth2/token` with the authorization code. For an example, see the following [sample call](#sample-refresh-call).

2. Note the refresh token that is returned.

3. Store the refresh token in Azure Key Vault. For more information, see the [Key Vault API documentation](/rest/api/keyvault/).

> [!IMPORTANT]
> The refresh token must be [stored as a secret](/rest/api/keyvault/secrets/set-secret/set-secret) in Key Vault.

#### Sample refresh call

Placeholder request:

```http
POST https://login.microsoftonline.com/CSPTenantID/oauth2/token HTTP/1.1
Content-Type: application/x-www-form-urlencoded
Host: login.microsoftonline.com
Content-Length: 966
Expect: 100-continue
```

Request body:

```http
resource=https%3a%2f%2fapi.partnercenter.microsoft.com&client_id=Application-Id&client_secret=Application-Secret&grant_type=authorization_code&code=AuthorizationCodeValue
```

Placeholder response:

```http
HTTP/1.1 200 OK
Cache-Control: no-cache, no-store
Content-Type: application/json; charset=utf-8
```

Response body:

```http
{"token_type":"Bearer","scope":"user_impersonation","expires_in":"3599","ext_expires_in":"3599","expires_on":"1547579127","not_before":"1547575227","resource":"https://api.partnercenter.microsoft.com","access_token":"Access
```

### Get access token

You must obtain an access token before you can make calls to the Partner Center APIs. You must use a refresh token to obtain an access token because access tokens generally have a limited lifetime (for example, less than an hour).

Placeholder request:

```http
POST https://login.microsoftonline.com/CSPTenantID/oauth2/token HTTP/1.1
Content-Type: application/x-www-form-urlencoded
Host: login.microsoftonline.com
Content-Length: 1212
Expect: 100-continue
```

Request body:

```http
resource=https%3a%2f%2fapi.partnercenter.microsoft.com&client_id=Application-Id &client_secret= Application-Secret&grant_type=refresh_token&refresh_token=RefreshTokenVlaue&scope=openid
```

Placeholder response:

```http
HTTP/1.1 200 OK
Cache-Control: no-cache, no-store
Content-Type: application/json; charset=utf-8
```

Response body:

```http
{"token_type":"Bearer","scope":"user_impersonation","expires_in":"3600","ext_expires_in":"3600","expires_on":"1547581389","not_before":"1547577489","resource":"https://api.partnercenter.microsoft.com","access_token":"AccessTokenValue","id_token":"IDTokenValue"}
```

### Make Partner Center API calls

You must use your access token to call the Partner Center APIs. See the following example call.

#### Example Partner Center API call

```http
GET https://api.partnercenter.microsoft.com/v1/customers/CustomerTenantId/users HTTP/1.1
Authorization: Bearer AccessTokenValue
Accept: application/json
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## PowerShell

[!INCLUDE [Partner Center PowerShell module support details](./includes/powershell-module-support.md)]

You can use the [Partner Center PowerShell module](https://www.powershellgallery.com/packages/PartnerCenter) to reduce the required infrastructure to exchange an authorization code for an access token. This method is optional for making [Partner Center REST calls](#rest).

For more information on this process, see [Secure App Model](/powershell/partnercenter/secure-app-model) PowerShell documentation.

1. Install the Azure AD and Partner Center PowerShell modules.

    ```powershell
    Install-Module AzureAD
    ```

    ```powershell
    Install-Module PartnerCenter
    ```

2. Use the **[New-PartnerAccessToken](/powershell/module/partnercenter/new-partneraccesstoken)** command to perform the consent process and capture the required refresh token.

    ```powershell
    $credential = Get-Credential

    $token = New-PartnerAccessToken -ApplicationId 'xxxx-xxxx-xxxx-xxxx' -Scopes 'https://api.partnercenter.microsoft.com/user_impersonation' -ServicePrincipal -Credential $credential -Tenant 'yyyy-yyyy-yyyy-yyyy' -UseAuthorizationCode
    ```

    > [!NOTE]
    > The **ServicePrincipal** parameter is used with the **New-PartnerAccessToken** command because an Azure AD app with a type of **Web/API** is being used. This type of app requires that a client identifier and secret be included in the access token request. When the **Get-Credential** command is invoked, you will be prompted to enter a username and password. Enter the application identifier as the username. Enter the application secret as the password. When the **New-PartnerAccessToken** command is invoked, you will be prompted to enter credentials again. Enter the credentials for the service account that you are using. This service account should be a partner account with appropriate permissions.

3. Copy the refresh token value.

    ```powershell
    $token.RefreshToken | clip
    ```

You should store the refresh token value in a secure repository, such as Azure Key Vault. For more information on how to use the secure application module with PowerShell, see the [multi-factor authentication](/powershell/partnercenter/multi-factor-auth) article.
