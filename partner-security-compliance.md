---
title: Security requirements status report
ms.date: 9/16/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-account
description: Learn how to check your security requirements compliance with the security requirements status report and Partner Center MFA report
author: vijay-vala
ms.author: vijvala
ms.topic: conceptual
---

# Security requirements status report

**Appropriate roles**: CPV admin | Global admin

This article explains the *Security requirements status* report in Partner Center.

The Security requirements status report:

- Provides metrics on multifactor authentication (MFA) compliance. (MFA compliance is a [partner security requirement](partner-security-requirements.md) for users in your partner tenant.)
- Displays Partner Center activities on partner tenants.

*Security requirements status* is updated daily and reflects sign-in data from the previous seven days.

## Access the Security requirements status report

To access the Security requirements status report, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Settings** (gear) icon.
2. Select the **Account settings** workspace, then **Security requirements status**.

> [!NOTE]
> The *Security requirements status* report is supported only in Partner Center. It's not available in the Microsoft Cloud for US Government or Microsoft Cloud Germany.
>
> We strongly recommend that all partners transacting through a sovereign cloud (US Government and Germany) adopt these new security requirements, but doing so isn't required.
>
> Microsoft will provide more details regarding the enforcement of these security requirements for sovereign clouds in the future.

## Security status metrics

The following sections explain the metrics in the *Security requirements status report* in more detail.

### MFA configuration on a partner tenant

The metric **Percentage of enabled user accounts with MFA enforced using options listed here:** shows the percentage of enabled user accounts on your partner tenant that have MFA enforced. You can use one of these [MFA options](/azure/active-directory/fundamentals/concept-fundamentals-mfa-get-started) to achieve compliance. This data is captured and reported on a daily basis. For example:

- Contoso is a CSP partner with 110 user accounts in the tenant. 10 of those user accounts are disabled.
- Of the remaining 100 user accounts, 90 have MFA enforced using the provided [MFA options](/azure/active-directory/fundamentals/concept-fundamentals-mfa-get-started).

Therefore, the metric displays **90%**.

### Partner Center requests with MFA

Each time your employees sign in to work on Partner Center or use APIs and then get or send data through Partner Center, their security status is challenged and tracked. Also included in security-status tracking are your applications and any control panel vendor applications. This data is shown in metrics under **Percentage of requests to Partner Center with MFA**, and reflects the previous seven days.

#### Dashboard MFA verification

The metric **Through Partner Center** is related to activities within the Partner Center. It measures the percentage of operations made by users who have completed MFA verification. For example:

- Contoso is a CSP partner with two Admin agents, Jane and John.
- On the first day, Jane logged in to Partner Center without MFA verification and performed three operations.
- On the second day, John logged in to Partner Center without MFA verification and performed five operations.
- On the third day, Jane logged in to Partner Center with MFA verification and performed two operations.
- No operations were performed by either agent on the remaining four days.
- Out of the 10 operations performed in the seven-day window, two were performed by a user with MFA verification. Therefore, the metric displays **20%**.

Use the file **Portal requests without MFA** to understand which user logged in to Partner Center without having MFA verification and the time of last visit during the reporting window.

#### App+User MFA verification

The metric **Through API or SDK** is related to App+User authentication through Partner Center API requests. It measures the percentage of API requests made using an access token with MFA claim. For example:

- Fabrikam is a CSP partner and has a CSP application that uses a mix of App+User authentication and app-only authentication methods.
- On the first day, the application made three API requests, which were backed by an access token obtained through App+User authentication method without MFA verification.
- On the second day, the application made five API requests, which were backed by an access token obtained using App-only authentication.
- On the third day, the application made two API requests, which were backed by an access token obtained using App+User authentication method with MFA verification.
- There were no operations made by either agent on the remaining four days.
- The five API requests on the second day, which were backed by an access token obtained through App-only authentication, are omitted from the metric because it doesn't make use of user credentials. Out of the remaining five operations, two of them were backed by an access token obtained with MFA verification. Therefore, the metric shows **40%**.

If you want to understand which App+user activities results in the non 100% on this metric, use the files:

- **API requests summary** to understand the overall MFA status by application.
- **All API requests** to understand the detail of each API requests made by users of your tenant. The result is limited to a maximum of the 10,000 most recent requests to help ensure a good downloading experience.

## Actions to take when MFA status is less than 100%

Some partners who have implemented MFA might see report metrics below 100%. To understand why, here are some factors to consider.

> [!NOTE]
> You will need to work with someone from your organization who is familiar with identity management and MFA implementation for your partner tenant.

### Implemented MFA for your partner tenant

You must implement MFA for your partner tenant to reach compliance. For information about how to implement MFA, see [Security requirements for using Partner Center or Partner Center APIs](partner-security-requirements.md).

> [!NOTE]
> MFA metrics are calculated daily and take into account operations performed in the previous seven days. If you only recently completed MFA implementation for your partner tenant, the metrics might not show 100% yet.

### Verify MFA on all user accounts

Understand whether your current MFA implementation covers all user accounts or only some. Some MFA solutions are policy-based and support user exclusion, while others might require you to explicitly enable MFA on a per-user basis.

Verify that you haven't excluded any user from your current MFA implementation. Any user account that is excluded and logs in to Partner Center to perform any CSP-, CPV-, or Advisor-related activity can cause the metrics to be below 100%.

### Review your MFA conditions

Understand whether your current implementation only enforces MFA under specific conditions. Some MFA solutions provide the flexibility to enforce MFA only when certain conditions are met. For example, when a user is accessing from an unknown device or unknown location, that can trigger MFA enforcement. A user who is enabled for MFA but isn't required to complete MFA verification when accessing Partner Center can cause the metrics to be below 100%.

> [!NOTE]
> For partners who have implemented MFA using Azure Active Directory (Azure AD) security defaults, it's important to note that for non-admin user accounts, MFA is enforced based on risk. Users are prompted for MFA only during risky sign-in attempts (for example, if a user is signing in from a different location). In addition, users have up to 14 days to register for MFA. Users who have not completed MFA registration aren't challenged for MFA verification during the 14-day period. Therefore, it is expected that the metrics will be below 100% for partners who have implemented MFA using Azure AD security defaults.

### Review third-party MFA configurations

If you're using a third-party MFA solution, identify how you're integrating it with Azure AD. In general, there are two methods:

- **Identity federation** - When Azure AD receives an authentication request, Azure AD redirects the user to the federated identity provider for authentication. Upon successful authentication, the federated identity provider redirects the user back to Azure AD along with a SAML token. For Azure AD to recognize that the user has completed MFA verification when authenticating to the federated identity provider, the SAML token must include the *authenticationmethodsreferences* claim (with value *multipleauthn*). Check whether the federated identity provider supports issuing such a claim. If so, check whether the federated identity provider has been configured to do so. If the claim is missing, Azure AD (and therefore, Partner Center) won't know that the user has completed MFA verification. The missing the claim can cause the metric to be below 100%.

- **Custom Control** - Azure AD Custom Control can't be used to identify whether a user has completed MFA verification through a third-party MFA solution. As a result, any user who has completed MFA verification through a custom control will always appear to Azure AD (and in turn, to Partner Center) as not having completed MFA verification. Where possible, it's recommended that you switch to using Identity Federation as opposed to Custom Control when integrating with Azure AD.

### Identify which users have signed in to Partner Center without MFA

It might be helpful to identify which users are logging in to Partner Center without MFA verification and verify them against your current MFA implementation. You can use the [Azure AD sign-in report](/azure/active-directory/reports-monitoring/concept-sign-ins) to find out whether a user has completed MFA verification or not. The Azure AD sign-in report is only available to partners who have subscribed to Azure AD Premium or any Microsoft 365 SKU, which includes Azure AD Premium (for example, EMS).

## Next steps

- [Partner Center security guidance group community](https://www.microsoftpartnercommunity.com/t5/Partner-Center-Security-Guidance/ct-p/partner-center-security-guidance)
- [Partner Center security requirements](partner-security-requirements.md)
- [Partner Center security requirements FAQ](partner-security-requirements-faq.yml)
