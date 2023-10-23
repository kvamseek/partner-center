---
title: Mandating multifactor authentication (MFA) for your partner tenant
ms.topic: article
ms.service: partner-dashboard
ms.subservice: partnercenter-account
description: Account settings workspace - Learn how mandating MFA for your partner tenants will help secure your access to customer resources. Includes sample scenarios.
author: vijay-vala
ms.author: vijvala
ms.date: 05/26/2023
---

# Mandating multifactor authentication (MFA) for your partner tenant

**Appropriate roles**: Admin agent | Sales agent | Helpdesk agent | Billing admin | Global admin

Better security, and ongoing security and privacy safeguards are among our top priorities, and we continue to help partners protect their customers and tenants.

To help partners protect their businesses and customers from identity theft and unauthorized access, we activated more security safeguards for partner tenants. These safeguards mandate and verify MFA. Mandating MFA helps partners to secure their access to customer resources against credentials compromise.

___

This article gives detailed examples and guidance for mandating multifactor authentication (MFA) in Partner Center.

Partners participating in the Cloud Solution Provider (CSP) program, Control Panel Vendors (CPVs), and Advisors must implement the [Partner Security Requirements](partner-security-requirements.md) to stay compliant.

Partners are required to enforce MFA for all user accounts in their partner tenant, including guest users. Users must complete MFA verification for the following areas:

- [Partner Center](#partner-center)
- [Partner Center API](#partner-center-api)
- [Partner Delegated Administration](#partner-delegated-administration)

## Partner Center

Some pages in the [Partner Center](https://partner.microsoft.com/dashboard/home) are MFA-protected, including:

- All pages under the **Customers** tab (that is, all pages with a URL that starts with
`https://partner.microsoft.com/commerce/*`)
- All pages under the **Support** > **Customer requests** tab (for example, all pages accessed with a URL that starts with `https://partner.microsoft.com/dashboard/v2/support/customers/*`)
- The **Billing** page

Other pages on Partner Center, such as the **Overview** page and **Service Health Status** check page, don't require MFA.

___

The following table shows which user types are authorized to access these MFA-protected pages (and are therefore affected by this feature).

| MFA-protected page | Admin agents | Sales agents | Helpdesk agents | Global administrator | Billing administrator |
| - | - | - | - | - | - |
| All pages under the **Customers** tab      |   x    |    x   |  x     |       |       |
| All pages under the **Support > Customer requests** tab     | x      |       |    x   |       |       |
| **Billing** page     |   x    |       |       |    x   |   x    |

If you try to access any of these pages, but you haven't completed MFA verification earlier, you'll be required to do so.

## Supported MFA options

- Partners who use Microsoft supported Azure Active Directory (Azure AD) Multi-Factor Authentication. For more information, see [Multiple ways to enable Azure AD MFA](/azure/active-directory/fundamentals/concept-fundamentals-mfa-get-started) (**MFA supported**)
- Partners who implemented any third-party MFA and part of the exception list can still access the Partner Center and APIs with exceptions but can't manage customers using DAP/GDAP (no exception allowed).
- If a partner's organization was previously granted an exception for MFA, users who manage customer tenants as part of the CSP program were required to enable Microsoft MFA requirements before March 1, 2022. Failure to comply with MFA requirements may result in the loss of customer tenant access.

The following table shows which scenarios are affected when the MFA exception is removed.

> [!IMPORTANT]
> Partners must use the Azure MFA to manage customer tenants with DAP or GDAP. No exceptions are supported.
>
> MFA exceptions are *only* allowed when using a compatible third-party MFA within the Partner Center and APIs. They are not allowed when managing a customer tenant using DAP or GDAP.

### Partner Center and APIs

For Partner Center APIs in the following table, App+User access is required.

| Scenario                                      | Azure AD Support MFA | Any third-party MFA  | No MFA     |
|-----------------------------------------------|----------------------|--------------------|------------------------------|
| Discover (price/catalog/promotion)            | MFA supported        | Exception supported    | No access  |
| Transact and manage                           | MFA supported        | Exception supported    | No access  |
| Billing and reconciliation                    | MFA supported        | Exception supported    |  No access  |
| Manage customers using delegated access/AOBO  | MFA supported        | No exception supported |  No access  |
| User and license assignment (with DAP only)   | MFA supported        | Exception supported    | No access  |
| User and license assignment (with GDAP)       | MFA supported        | No exception supported    | No access  |
| Granular Admin Relationships Request and access assignment | MFA supported | No exception supported | No access |

### Other workloads

Potential other workloads for this category include Azure AD and Microsoft Exchange.

| Scenario                                     | Azure AD Supported MFA | Any third-party MFA |
|----------------------------------------------|------------------------|-------------------|
| Discover (Price/Catalog/Promotion)           | N/A                    |  N/A                                 |
| Transact and manage                          |        N/A             |  N/A                            |
| Billing and Reconciliation                            |         N/A            |  N/A                       |
| Manage customers using delegated access/AOBO | MFA supported          | No exceptions supported             |
| User and License Assignment                  | MFA supported          | No exceptions supported             |

## Verification examples

To illustrate how verification works in the Partner Center, consider the following examples.

### Example 1: Partner has implemented Azure AD MFA

1. Consuela works for a CSP named Contoso. Contoso has implemented MFA for all their users under Contoso partner tenant using Azure AD MFA.

2. Consuela starts a new browser session and goes to the Partner Center overview page (which isn't MFA-protected). Partner Center redirects Consuela to Azure AD to sign-in.

3. Due to the existing Azure AD MFA setup by Contoso, Consuela is required to complete MFA verification. Upon successful sign-in and MFA verification, Consuela is redirected back to the Partner Center overview page.

4. Consuela tries to access one of the MFA-protected pages in Partner Center. Because Consuela has already completed MFA verification during sign-in earlier, Consuela can access the MFA-protected page without being required to go through MFA verification again.

### Example 2: Partner has implemented third-party MFA using identity federation

1. Prashob works for a CSP named Wingtip. Wingtip has implemented MFA for all their users under Wingtip partner tenant using third-party MFA, which is integrated with Azure AD via identity federation.

2. Prashob starts a new browser session and goes to the Partner Center overview page (which isn't MFA-protected). Partner Center redirects Prashob to Azure AD to sign in.

3. Because Wingtip has setup identity federation, Azure AD redirects Prashob to the federated identity provider to complete sign-in and MFA verification. Upon successful sign-in and MFA verification, Prashob is redirected back to Azure AD and then to Partner Center overview page.

4. Prashob tries to access one of the MFA-protected pages in Partner Center. Because Prashob has already completed MFA verification during sign-in earlier, he can access the MFA protected page without being required to go through MFA verification again.

5. Prashob then goes to the service management page to add users in Contoso's Azure Active Directory. Because Prashob hasn't used the Microsoft MFA to manage the customer tenant, he's blocked from managing the customer tenant.

The recommendation for Prashob in this example is to use the Azure AD Multi-Factor Authentication solution so he can manage the customer's tenant successfully.

### Example 3: Partner hasn't implemented MFA

1. A CSP partner called Fabrikam hasn't yet implemented MFA. Microsoft recommends that they implement an Azure AD-supported MFA solution.

2. John works for Fabrikam. Fabrikam hasn't implemented MFA for any user under the Fabrikam partner tenant.

3. John starts a new browser session and goes to the Partner Center overview page (which isn't MFA-protected). Partner Center redirects John to Azure AD to sign in.

4. Because Fabrikam hasn't implemented MFA, John isn't required to complete MFA verification. Upon successful sign-in, John is redirected back to the Partner Center overview page.

5. John tries to access one of the MFA-protected pages in Partner Center. Because John hasn't completed MFA verification, Partner Center redirects John to Azure AD to complete MFA verification. Because this is the first time John is required to complete MFA, John is also requested to [register for MFA](#mfa-registration-experience). Upon successful MFA registration and MFA verification, John can access the MFA-protected page.

6. On another day, before Fabrikam implements MFA for any user, John starts a new browser session and goes to the Partner Center overview page (which isn't MFA-protected). Partner Center redirects John to Azure AD to sign in without MFA prompt.

7. John tries to access one of the MFA-protected pages in Partner Center. Because John hasn't completed MFA verification, Partner Center redirects John to Azure AD to complete MFA verification. Because John has registered MFA, this time he's only asked to complete the MFA verification.

### Example 4: Partner has implemented third-party MFA with Conditional Access

1. Trent works for a CSP named Wingtip. Wingtip has implemented MFA for all their users under Wingtip partner tenant using third-party MFA in their cloud environment with conditional access.  

2. Trent starts a new browser session and goes to the Partner Center overview page (which isn't MFA-protected). Partner Center redirects Trent to Azure AD to sign in.

3. Because Wingtip has a valid third party MFA integration and are part of the exception, Azure AD redirects Trent to complete sign-in and MFA verification. Upon successful sign-in and MFA verification, Trent is redirected back to Azure AD and then to Partner Center overview page.

4. Trent tries to access one of the MFA-protected pages in Partner Center. Because Trent has already completed MFA verification during sign-in earlier, Trent can access the MFA protected page without being required to go through MFA verification again.  

5. When Trent tries to access their customer Contoso using the DAP/GDAP overview from the service management page in Partner Center, he's not allowed because he's required to use Azure AD-supported MFA. Review this article for ways to enable Azure AD MFA.

The recommended next step is for Trent to use the Azure AD Multi-Factor Authentication solution so he can manage the customer Contoso tenant successfully.

## Partner Center API

The Partner Center API supports both App-only authentication and application and user (App+User) authentication.

When App+User authentication is used, Partner Center requires MFA verification. More specifically, when a partner application sends an API request to Partner Center, it must include an access token in the authorization header of the request.

> [!NOTE]
> The [Secure Application Model framework](/partner-center/develop/enable-secure-app-model) is a scalable framework for authenticating CSP partners and CPVs through the Microsoft Azure MFA architecture when calling Partner Center APIs. You must implement this framework before enabling MFA on your tenant.

When Partner Center receives an API request with an access token obtained using App+User authentication, the Partner Center API checks for the presence of the *MFA* value in the *Authentication Method Reference (AMR)* claim. You can use a JWT decoder to validate whether an access token contains the expected authentication method reference (AMR) value or not:

``` csharp
{
  "aud": "https://api.partnercenter.microsoft.com",
  "iss": "https://sts.windows.net/df845f1a-7b35-40a2-ba78-6481de91f8ae/",
  "iat": 1549088552,
  "nbf": 1549088552,
  "exp": 1549092452,
  "acr": "1",
  "amr": [
    "pwd",
    "mfa"
  ],
  "appid": "23ec45a3-5127-4185-9eff-c8887839e6ab",
  "appidacr": "0",
  "family_name": "Adminagent",
  "given_name": "CSP",
  "ipaddr": "127.0.0.1",
  "name": "Adminagent CSP",
  "oid": "4988e250-5aee-482a-9136-6d269cb755c0",
  "scp": "user_impersonation",
  "tenant_region_scope": "NA",
  "tid": "df845f1a-7b35-40a2-ba78-6481de91f8ae",
  "unique_name": "Adminagent.csp@testtestpartner.onmicrosoft.com",
  "upn": "Adminagent.csp@testtestpartner.onmicrosoft.com",
  "ver": "1.0"
}
```

- If the value is present, Partner Center concludes that MFA verification was completed and processes the API request.
- If the value isn't present, Partner Center API rejects the request with the following response:

   ``` csharp
   HTTP/1.1 401 Unauthorized - MFA required
   Transfer-Encoding: chunked
  Request-Context: appId=cid-v1:03ce8ca8-8373-4021-8f25-d5dd45c7b12f
   WWW-Authenticate: Bearer error="invalid_token"
   Date: Thu, 14 Feb 2019 21:54:58 GMT
   ```

When App-Only authentication is used, the APIs that support App-Only authentication work continuously without requiring MFA.

## Partner Delegated Administration

Partner accounts, including Admin agents and Helpdesk agents, can use their partner delegated admin privileges (DAP) or granular delegated admin privileges (GDAP) to manage customer resources through Microsoft Online Services portals, command-line interface (CLI), and APIs (using App+User authentication). For more information, see [supported MFA options](#supported-mfa-options)

### Using service portals

When accessing Microsoft Online Services portals using Partner Delegated Admin Privileges (Admin-On-Behalf-Of) to manage customer resources, many of these portals require the partner account to authenticate interactively, with the customer Azure AD tenant set as the authentication context—the partner account is required to sign in to the customer tenant.

When Azure AD receives such authentication requests, it requires that the partner account complete MFA verification. There are two possible user experiences, depending on whether the partner account is a managed or federated identity:

- If the partner account is a **managed** identity, Azure AD directly prompts the user to complete MFA verification. If the partner account hasn't registered for MFA with Azure AD before, the user is asked to [complete MFA registration](#mfa-registration-experience) first.

- If the partner account is a **federated** identity, the experience is dependent on how the partner administrator has configured federation in Azure AD. When setting up federation in Azure AD, the partner administrator can indicate to Azure AD whether the federated identity provider supports MFA or not.
  - If so, Azure AD redirects the user to the federated identity provider to complete MFA verification.
  - If not, Azure AD directly prompts the user to complete MFA verification. If the partner account hasn't registered for MFA with Azure AD before, the user is asked to [complete MFA registration](#mfa-registration-experience) first.

The overall experience is similar to the scenario in which an end-customer tenant has implemented MFA for its administrators. For example, the customer tenant has enabled [Azure AD security defaults](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults), which requires all accounts with administrative rights to sign in to the customer tenant with MFA verification, including Admin gents and Helpdesk agents.

For testing purposes, partners can enable the [Azure AD security defaults](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) in the customer tenant and then try using Partner Delegated Administration Privileges to access the customer tenant.

> [!NOTE]
> Not all Microsoft Online Service portals require partner accounts to sign in to the customer tenant when accessing customer resources using Partner Delegated Admin Privileges. Instead, some only require the partner accounts to sign in to the partner tenant. An example is the Exchange Admin Center. Over time, we expect these portals to require partner accounts to sign in to the customer tenant when using Partner Delegated Admin Privileges.

### Using service APIs

Some Microsoft Online Services APIs (such as Azure Resource Manager, Microsoft Graph, and so on) support partners using Partner Delegated Admin Privileges to programmatically manage customer resources.

To use Partner Delegated Admin Privileges with these APIs, the partner application must include an access token in the API request Authorization header, where the access token is obtained by having a partner user account to authenticate with Azure AD, with the customer Azure AD set as the authentication context. The partner application is required to have a partner user account sign in to the customer tenant.

When Azure AD receives such as authentication request, Azure AD requires the partner user account to complete MFA verification. If the partner user account hasn't registered for MFA before, the user account is prompted to complete MFA registration first.

All partner applications that are integrated with these APIs using Partner Delegated Admin Privileges are affected by this feature. To ensure partner applications can continue to work with these APIs without interruption:

- Partners must avoid using a non-interactive user authentication method with Azure AD to obtain the access token. When using a non-interactive user authentication method such as [Password Flow](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet/wiki/Acquiring-tokens-with-username-and-password), Azure AD can't prompt the user to complete MFA verification. The partner must switch to using an interactive user authentication method such as [OpenID Connect flow](/azure/active-directory/develop/v1-protocols-openid-connect-code) instead.

- When the interactive user authentication method is used, the partner should use a partner user account that is already enabled for MFA. Alternatively, when prompted by Azure AD, partner can complete MFA registration and MFA verification during sign-in.

- This is similar to the scenario in which an end customer tenant has implemented MFA for its administrators. For example, the customer tenant has enabled [Azure AD security defaults](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults), which requires all user accounts with administrative rights to sign in to the customer tenant with MFA verification, including Admin agents and Helpdesk agents. For testing purposes, partners can enable the [Azure AD security defaults](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) in the customer tenant and then try using Partner Delegated Administration Privileges to programmatically access the customer tenant.

### MFA registration experience

During MFA verification, if the partner account hasn't registered for MFA before, Azure AD will prompt the user to complete MFA registration first:

:::image type="content" source="media/partner-security-requirements-mandating-mfa/mfa-registration-1.png" alt-text="Screenshot of the first step in MFA registration.":::

After selecting **Next**, the user will be asked to choose from a list of verification methods.

:::image type="content" source="media/partner-security-requirements-mandating-mfa/mfa-registration-2.png" alt-text="Screenshot of the second step in MFA registration.":::

After successful registration, the user must complete MFA verification using their chosen verification method.

## Common issues

Before applying for [technical exception](#how-to-submit-a-request-for-a-technical-exception) from the MFA requirement, review the list of common issues reported by other partners to understand whether your request is valid.

### Issue 1: Partner needs more time to implement MFA for their partner agents

A partner hasn't started or is still in the process of implementing MFA for their partner agents who require access to Microsoft Online Services Portals using Partner Delegated Administration Privileges to manage customer resources. The partner needs more time to complete MFA implementation. Is this a valid reason for technical exception?

**Answer**: No. A partner needs to plan to implement MFA for their users to avoid disruption.

> [!NOTE]
> Even though a partner hasn't implemented MFA for their partner agents, the partner agents can still access Microsoft Online Services portals using Partner Delegated Administration Privileges if they can complete MFA registration and MFA verification when prompted during sign-in to customer tenant. Completing MFA registration does not automatically enable the user for MFA.

### Issue 2: Partner hasn't implemented MFA for user accounts not using Delegated Admin Privileges

A partner has some users in their partner tenants who don't require access to Microsoft Online Services Portals to manage customer resources using Partner Delegated Administration Privileges. The partner is in the process of implementing MFA for these users and needs more time to complete. Is this a valid reason for technical exception?

**Answer**: No. Because these user accounts aren't using Partner Delegated Administration Privileges to manage customer resources, they won't be required to sign in to customer tenant. They won't be affected by Azure AD requiring MFA verification during sign-in to customer tenant.

### Issue 3: Partner hasn't implemented MFA for user service accounts

A partner has some user accounts in their partner tenants, which are being used by devices as service accounts. These low-privileged accounts don't require access Partner Center nor Microsoft Online Services Portals to manage customer resources using Partner Delegated Administration Privileges. Is this a valid reason for a technical exception?

**Answer**: No. Because these user accounts aren't using Partner Delegated Administration Privileges to manage customer resources, they aren't required to sign in to customer tenant. They won't be affected by Azure AD requiring MFA verification during sign-in to customer tenant.

### Issue 4: Partner can't implement MFA using Microsoft Authenticator app

A partner has "clean desk" policy, which doesn't permit employees bringing their personal mobile devices to their work area. Without access to their personal mobile devices, the employees can't install the Microsoft Authenticator app, which is the only MFA verification supported by Azure AD security defaults. Is this a valid reason for technical exception?

**Answer**: No. The partner should consider the following alternative so their employees can still complete MFA verification when accessing Partner Center:

- Partner can also sign up for Azure AD Premium or third-party MFA solutions (compatible with Azure AD) which can provide more verification methods.

### Issue 5: Partner can't implement MFA due to the use of legacy authentication protocols

A partner has some partner agents who are still using legacy authentication protocols, which aren't MFA compatible. For example, the users are still using Outlook 2010, which is based on legacy authentication protocols. Enabling MFA for these partner agents will disrupt the use of legacy authentication protocols. Is this a valid reason for technical exception?

**Answer**: No. Partners are encouraged to move away from the use of legacy authentication protocols because of potential security implications because these protocols can't be protected with MFA verification and are much more susceptible to credential compromise. If moving away from the use of legacy authentication protocols isn't an option, partners should consider signing up for Azure AD Premium, which supports the use of application passwords. Application passwords are one-time, system-generated passwords, and are stronger than human-generated passwords. By using application passwords, partners can implement MFA for their users, while falling back to application passwords for legacy authentication protocols only.

To understand the latest plan for supporting legacy authentication for Outlook, read the post about the [Basic Auth and Exchange Online](https://techcommunity.microsoft.com/t5/exchange-team-blog/basic-auth-and-exchange-online-february-2020-update/ba-p/1191282)  and follow the [Exchange team blog](https://techcommunity.microsoft.com/t5/exchange-team-blog/bg-p/Exchange) to get the upcoming news.

> [!NOTE]
> Even though the partner hasn't implemented MFA for their partner agents, the partner agents can still access Microsoft Online Services portals using Partner Delegated Administration Privileges if they can complete MFA registration and MFA verification when prompted during sign-in to customer tenant. Completing MFA registration does not automatically enable the user for MFA.

### Issue 6: Partner has implemented third-party MFA that isn't recognized by Azure AD

A partner has implemented MFA for their users using a third-party MFA solution. However, the partner is unable to correctly configure the third-party MFA solution to relay to Azure AD that MFA verification has been completed during user authentication. Is this a valid reason for technical exception?

**Answer**: This scenario might be a valid reason for a technical exception for Partner Center transact and manage. However, if your partner's organization was previously granted an exception for MFA, users who manage customer tenants as part of the CSP program must enable Microsoft MFA requirements before March 1, 2022. Failure to comply with MFA requirements might result in the removal loss of customer tenant access. Before submitting a request for a technical exception, confirm with the third-party MFA solution provider that the MFA solution can't be configured to flow the *authenticationmethodsreferences* claim (with value *multipleauthn*) to Azure AD to indicate that MFA verification has been completed during user authentication. When submitting a request for technical exception, you must provide details of the third-party MFA solution used. You must also indicate method of integration (such as through identity federation or use of Azure AD Custom Control), and provide the following information in the technical exception request as the supporting documents:

- The third-party MFA configurations
- The result of [Test the Partner Security Requirements](/powershell/partnercenter/test-partner-security-requirements) running by the third-party MFA enabled account
- The purchase order of the third-party MFA solution you're using or you plan to use

## How to submit a request for a technical exception

> [!IMPORTANT]
> As stated earlier, an MFA exception is no longer supported for managing the customer tenant using DAP or GDAP. Partners must use the Azure MFA solution for managing the customer tenant.  

Partners can apply for a technical exception to suppress MFA verification if they're encountering technical issues with Microsoft Online Services and there's no feasible solution or workaround. Before doing so, review the [Common issues](#common-issues) in the previous section.

To submit a request for technical exception:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) with Global admin or Admin agent credentials.

2. [Create a new support ticket](report-problems-with-partner-center.md):

   a. Under **Issue type**, search for **MFA - Request for exception**

      You can also select **CSP** from Category, then select **Accounts, Onboarding, Access** > **MFA - Request for exception** > **Next step**.

   b. Provide details requested to submit a service request for technical exception and select **Submit**.

Microsoft may take up to three working days to provide a response to a request for technical exception.

## Next steps

- [Partner security requirements status](partner-security-compliance.md)
