---
title: Use the secure application model framework
description: Learn how to use the secure application model framework for authenticating CSP and CPV partners.
ms.date: 01/26/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: Vamseek
ms.author: vijvala
---

# Secure application model framework

Microsoft is introducing a secure, scalable framework for authenticating cloud solution provider (CSP) partners and Control Panel Vendors (CPV) through the Microsoft Azure multi-factor authentication (MFA) architecture. CSP partners and Control Panel Vendors can rely on the new model to elevate security for Partner Center API integration calls. This helps all parties including Microsoft, CSP partners and Control Panel Vendors to protect their infrastructure and customer data from security risks.

[!INCLUDE [Important - Azure AD Graph is deprecated](./includes/azure-ad-graph-notice.md)]

## Scope

This article applies to the following partners:

- Control Panel Vendors (CPVs) are independent software vendors who develop apps for use by CSP partners to integrate with Partner Center APIs. A CPV isn't a CSP partner with direct access to the partner dashboard or APIs. They're the companies that develop applications (usually web apps) that enable CSPs to sell their products through a unified marketplace.
- CSP indirect providers and CSP direct partners who are using app ID + user authentication and directly integrate with Partner Center APIs.

> [!NOTE]
> To qualify as a CPV, you must onboard to Partner Center as a CPV first. If you are an existing CSP partner who is also a CPV, this prerequisite applies to you, as well.

## Secure application development

In the process of placing orders for Microsoft products on behalf of CSPs, marketplace applications from CPVs interact with Microsoft APIs to place orders and provision resources for customers.

Some of these APIs include:

- Partner Center APIs implementing commerce operations like placing orders and managing subscription lifecycles.
- Microsoft Graph APIs that implement identity management for CSP tenants and CSP customer's tenants.
- Azure Resource Manager (ARM) APIs implementing Azure deployment functionality.

CSP partners are empowered with delegated privileges to act on behalf of their customers when calling Microsoft APIs. Delegated privileges allow CSP partners to complete purchase, deployment, and support scenarios for their customers.

Marketplace applications are designed to help CSP partners list their solutions for customers. To achieve this, marketplace applications need to impersonate CSP partner privileges to call Microsoft APIs.

Since CSP partner privileges are high and provide access to all of the partner's customers, it's important to understand how these applications must be designed to withstand security exploitation vectors. Security attacks on these sensitive applications can lead to the compromise of customer data. Therefore, permission grants and partner privilege impersonation must be designed to follow the principle of least privilege. The following principles and best practices ensure that marketplace applications are sustainable and can withstand compromises.

### Security principles for credentials impersonation

- Marketplace applications must not store any credentials from CSP partners.
- CSP partner user passwords shouldn't be shared.
- CSP partner tenant web app keys must not be shared with Control Panel Vendors.
- A marketplace application must present the application identity along with partner information as opposed to using only partner credentials when making calls impersonating a CSP partner identity.
- Access to a marketplace application must be based on the principle of least privilege and clearly articulated in permissions.
- Authorization for a marketplace application must be pivoted to multiple credentials.
- Application credentials and partner credentials must be provided together to gain access.

  > [!IMPORTANT]
  > It is important that there is no single point of compromise.

- Access must be restricted to a specific audience or API.
- Access must identify the purpose of the impersonation.
- Access permissions for a marketplace application must be time bound. CSP partners must be able to renew or revoke access to the marketplace application.
- Quick control or remediation processes must be in place to handle compromises of marketplace application credentials.
- All user accounts should use two-factor authentication (2FA).
- The application model should be friendly to extra security provisions, like conditional access to a better security model.

> [!NOTE]
> CSP indirect providers and CSP direct partners who are using app ID + user authentication and directly integrate with Partner Center APIs are required to follow the above principles to secure their own marketplace applications.

## Application identity and concepts

### Multi-tenant applications

A multi-tenant application is generally a software as a service (SaaS) application. You can configure your application to accept sign-ins from any Azure Active Directory (Azure AD) tenants by configuring the application type as **multi-tenant** on the [Azure dashboard](https://portal.azure.com). Users in any Azure AD tenant will be able to sign in to your application after consenting to use their account with your application.

To learn more about creating a multi-tenant application, see [Sign in any Azure Active Directory user using the multi-tenant application pattern](/azure/active-directory/develop/howto-convert-app-to-be-multi-tenant).

## Consent framework

For a user to sign in to an application in Azure AD, the application must be represented in the user's tenant, which allows the organization to do things like apply unique policies when users from their tenant sign-in to the application. For a single tenant application, this registration is simple: it's the one that happens when you register the application in the Azure dashboard.

For a multi-tenant application, the initial registration for the application lives in the Azure AD tenant used by the developer. When a user from a different tenant signs in to the application for the first time, Azure AD asks them to consent to the permissions requested by the application. If they consent, then a representation of the application called a service principal is created in the user's tenant, and the sign in process can continue. A delegation is also created in the directory that records the user's consent to the application.

> [!NOTE]
> CSP indirect providers and CSP direct partners who are using app ID + user authentication and directly integrate with Partner Center APIs will have to give consent to their marketplace application using the same consent framework.

The consent experience is affected by the permissions requested by the application. Azure AD supports two kinds of permissions, app-only and delegated.

- **App-only permission** is granted directly to the identity of the application. For example, you can grant an application permission to read the list of users in a tenant, regardless of who is signed in to the application.
- **Delegated permission** grants an application the ability to act as a signed in user for a subset of the things the user can do. For example, you can grant an application the delegated permission to read the signed in user's calendar.

Some permissions are consented to by a regular user, while others require a tenant administrator's consent. For more information on Azure Active Directory consent framework, see [Understanding Azure AD application consent experiences](/azure/active-directory/develop/application-consent-experience).

- [Scopes, permissions, and consent in the Azure Active Directory v2.0 endpoint](/azure/active-directory/develop/v2-permissions-and-consent)
- [Understanding user and admin consent](/azure/active-directory/develop/active-directory-devhowto-multi-tenant-overview#understanding-user-and-admin-consent)

## Multi-tenant application open authorization (OAuth) token flow

In a multi-tenant application open authorization (OAuth) flow, the application is represented as a multi-tenant application in the CPV or CSP partner's tenant.

To access Microsoft APIs (Partner Center APIs, Graph APIs, and so on), CSP partners must log in to the application and consent to allow the application to call APIs on their behalf.

> [!NOTE]
> CSP indirect providers and CSP direct partners who are using app ID and user authentication and directly integrate with Partner Center APIs will have to give consent to their marketplace application to use the same consent framework.

The application gains access to the partner's resources, like Graph and Partner Center APIs, through consent and OAuth grants.

## Create a multi-tenant application

A multi-tenant application must adhere to the following requirements:

- It must be a web app with an application ID and secret key.
- It must have implicit authentication mode turned off.

In addition, we recommend adhering to these best practices:

- Use a certificate for the secret key.
- Enable conditional access to apply IP range restrictions. This may require more functionality to be enabled on the Azure AD tenant.
- Apply access token lifetime policies for the application.

When acquiring a token, the app ID and secret key must be presented. The secret key can be a certificate.

The application can be configured to call multiple APIs including Azure Resource Manager APIs. The following are the minimum set of permissions required for Partner Center APIs:

- Azure Active Directory delegated permissions: **Access the directory as signed in user**
- Partner Center APIs delegated permissions: **Access**

## Application captures partner consent

A multi-tenant application must acquire consent from partners and use the consent and grant to make further calls to Partner Center APIs. Consent is acquired through an OAuth authentication code flow.

To acquire consent, CPVs or CSP partners must build an onboarding website that can accept an authentication code grant from Azure active directory.

For more information, see [Authorize access to Azure Active](/azure/active-directory/develop/v1-protocols-oauth-code) and [Directory web applications using the OAuth 2.0 code grant flow](/azure/active-directory/develop/v1-protocols-oauth-code).

Here are the steps for a multi-tenant application to capture CSP partner consent along with a reusable token for making calls to Partner Center APIs.

Use the following steps to acquire partner consent.

1. Build a partner onboarding web application that can host a consent link for the partner to click through to accept consent for the multi-tenant application.
2. The CSP partner clicks on the consent link. For example, `https://login.microsoftonline.com/common/oauth2/authorize?&client_id=<marketplaceappid>&response_ty`
3. The Azure AD login page explains the permissions that will be granted to the application on behalf of the user. The CSP partner can decide to use either Admin Agent or Sales Agent credentials to sign in and approve the consent. The application is given permissions based on the user role used to sign in.
4. Once consent is granted, Azure Active Directory creates a service principal of the CPV's multi-tenant application into the CSP partner's tenant.
   The application is given OAuth grants to act on behalf of the user. These grants allow the multi-tenant application to call Partner Center APIs on behalf of the partner.
   At this point, the Azure AD login page redirects to the partner onboarding web application. The web application receives an authorization code from Azure AD. The partner onboarding web application must use the authorization code along with the application ID and secret key to call the Azure AD [Tokens API](/azure/active-directory/develop/access-tokens) to obtain a refresh token.
5. Securely store the refresh token. The refresh token is part of the partner credentials used to obtain access to Partner Center APIs on behalf of the partner. Once the refresh token is acquired, encrypt it and store it in a secret key store, such as the [Azure key vault](https://azure.microsoft.com/services/key-vault/).

## Token request call flow

A CPVs or CSP partner's application must acquire an access token before making calls to Partner Center APIs. These APIs are represented at resource URL `https://api.partnercenter.microsoft.com`.

A CPV application should identify which partner account it must impersonate to call Partner Center APIs based on either product or federated sign-in. The application retrieves the encrypted refresh token for that partner tenant from the secret key store. The refresh token must be decrypted before use.

For CSP partners where there's only one tenant who gives consent, the partner account refers to the CSP partner's tenant.

The refresh token is a multi-audience token. That means the refresh token can be used to obtain a token for multiple audiences based on the consent that is granted. For example, if partner consent is given for Partner Center APIs and Microsoft Graph APIs, the refresh token can be used to request an access token for both APIs. The access token has the "on behalf of" grant and allows a marketplace application to impersonate the partner who consented while calling these APIs.

An access token can be acquired for a single audience at a time. If an application needs to access multiple APIs, it must request multiple access tokens for the targeted audience. To request an access token, the application needs to call the Azure AD [Tokens API](/dotnet/api/microsoft.identitymodel.tokens?view=azure-dotnet&preserve-view=true). Alternatively, it could also use the Azure AD SDK's [AuthenticationContext.AcquireTokenAsync](/dotnet/api/microsoft.identity.web.itokenacquisition.getaccesstokenforappasync?view=msal-model-dotnet-latest&preserve-view=true) and pass in following information:

- Resource URL, which is the endpoint URL for the application to be called. For example, the resource URL for the Microsoft Partner Center API is `https://api.partnercenter.microsoft.com`.
- Application credentials consisting of the web app's application ID and secret key.
- The refresh token

The resulting access token allows the application to make calls to APIs that are mentioned in the resource. The application can't request an access token for APIs that weren't granted permission as part of the consent request. The UserPrincipalName (UPN) attribute value is the Azure AD username for the user accounts.

## More considerations

### Conditional access

When it comes to managing your cloud resources, a key aspect of cloud security is identity and access. In a mobile-first, cloud-first world, users can access your organization's resources using various devices and apps from anywhere. Simply focusing on who can access a resource is no longer enough. To master the balance between security and productivity, you also need to consider how a resource is accessed. By using Azure AD conditional access, you can address this requirement. With conditional access, you can implement automated access control decisions for accessing your cloud apps that are based on conditions.

For more information, see [What is conditional access in Azure Active Directory?](/azure/active-directory/conditional-access/overview)

### IP range-based restrictions

You can restrict tokens to be issued to specific range of IP addresses only. This feature helps restrict the surface area of attack to a specific network only.

### Multi-factor authentication

Enforcing multi-factor authentication helps restrict credential compromise situations by enforcing credentials verification to two or more forms. This feature allows Azure AD to validate the identity of the caller via secure secondary channels, such as mobile or email, before issuing tokens.

For more information, see [How it works: Azure Multi](/azure/active-directory/authentication/concept-mfa-howitworks).

## Next steps

- [How to configure a new multi-tenant application](/azure/active-directory/application-dev-setup-multi-tenant-app)[-](/en-us/azure/active-directory/application-dev-setup-multi-tenant-app)
- [Authorize access to Azure Active Directory web applications using the OAuth 2.0 code grant flow](/azure/active-directory/develop/v1-protocols-oauth-code)
- [How application consent works](/azure/active-directory/application-dev-consent-framework)
- [Partner Center REST API reference](/partner-center/develop/partner-center-rest-api-reference)
