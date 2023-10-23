---
title: Cloud Solution Provider security best practices
ms.topic: article
ms.date: 10/13/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Learn CSP security best practices.
author: vijay-vala
ms.author: vijvala
---

# CSP security best practices

All partners in the Cloud Solution Provider (CSP) program accessing [Partner Center](https://partner.microsoft.com/dashboard/home) and [Partner Center APIs](./developer/index.yml) should follow the security guidance in this article to protect themselves and customers.

For customer security, see [Customer security best practices](customer-security-best-practices.md).

[!INCLUDE [Important - Azure AD Graph is deprecated](./developer/includes/azure-ad-graph-notice.md)]

## Highly recommended steps in your tenants

- [Add a security contact](security-contact.md) for security-related issue notifications in the Partner Center tenant.
- Check your [identity secure score](/azure/active-directory/fundamentals/identity-secure-score) in Microsoft Azure Active Directory (Azure AD) and take the appropriate actions to raise your score.
- Review and implement the guidance documented in [Managing nonpayment, fraud, or misuse](non-payment-fraud-misuse.md).
- Familiarize yourself with the NOBELIUM threat actor and related materials:
  - [NOBELIUM targeting delegated administrative privileges to facilitate broader attacks](https://www.microsoft.com/security/blog/2021/10/25/nobelium-targeting-delegated-administrative-privileges-to-facilitate-broader-attacks/)
  - [NOBELIUM response training](https://partner.microsoft.com/training/assets/detail/introduction-to-nobelium-response-training-mp4)
  - [Securing the channel: Journey to zero trust](https://partner.microsoft.com/training/assets/collection/nobelium-response-security-training#/)
  
## Identity best practices

### Require multifactor authentication

- Ensure that **all users** in your Partner Center tenants and your customer tenants are registered for and require multifactor authentication (MFA).  There are various ways to configure MFA.  Choose the method that applies to the tenant you're configuring:
  - My Partner Center/Customer's tenant has Azure AD Premium Plan 1
    - Use [Conditional Access](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) to enforce MFA.
  - My Partner Center/Customer's tenant has Azure AD Premium Plan 2
    - Use [Conditional Access](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) to enforce MFA.
    - [Implement risk-based policies](/azure/active-directory/authentication/tutorial-risk-based-sspr-mfa) using Azure AD Identity Protection.
    - For your Partner Center tenant, you might qualify for Microsoft 365 E3 or E5, depending on your Internal Use Rights (IUR) benefits.  These SKUs include Azure AD Premium Plan 1 or 2, respectively.
    - For your customer's tenant, we recommend enabling [security defaults](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults).
      - If your customer is using apps that require legacy authentication, those apps won't function after you enable security defaults.  If the app can't be replaced, removed, or updated to use modern authentication, you can enforce MFA through [per-user MFA](/azure/active-directory/authentication/howto-mfa-userstates).
      - You can monitor and enforce your customer's use of security defaults using the following Graph API call:
        - [identitySecurityDefaultsEnforcementPolicy resource type - Microsoft Graph v1.0 | Microsoft Learn](/graph/api/resources/identitysecuritydefaultsenforcementpolicy)
- Ensure that the MFA method used is phishing-resistant. You can do so by using [passwordless authentication](/azure/active-directory/authentication/howto-authentication-passwordless-deployment) or [number matching](/azure/active-directory/authentication/how-to-mfa-number-match).
- If a customer refuses to use MFA, don't provide them any administrator role access to Azure AD or write permissions to Azure Subscriptions.

### App access

- Adopt the Secure Application Model framework. All partners integrating with Partner Center APIs must adopt the [Secure Application Model framework](/partner-center/develop/enable-secure-app-model) for any app and user auth model applications.
- Disable [user consent](/microsoft-365/admin/misc/user-consent) in Partner Center Azure AD tenants or use the [admin consent workflow](/azure/active-directory/manage-apps/configure-admin-consent-workflow).
  
### Least privilege / No standing access

- Users who have Azure AD administrative roles such as Global admin or Security admin shouldn't regularly use those accounts for email and collaboration.  Create a separate user account with no Azure AD administrative roles for collaboration tasks.
- Review the Admin agent group and remove people who don't need access.
- Regularly review administrative role access in Azure AD, and limit access to as few accounts as possible. For more information, see [Azure AD built-in roles](/azure/active-directory/roles/permissions-reference).
- Users who have left the company or changed roles within the company should be removed from Partner Center access.
- If you have Azure AD Premium Plan 2, use [Privileged Identity Management (PIM)](/azure/active-directory/privileged-identity-management/pim-configure) to enforce just-in-time (JIT) access. Use dual custody to review and approve access for Azure AD administrator roles and Partner Center roles.
- For securing privileged roles, see [Securing privileged access overview](/security/compass/overview).
- Regularly review access to customer environments.
  - [Remove inactive Delegated Administration Privileges (DAP)](dap-monitor-self-serve-removal.md).
  - [Move active DAP relationships to Granular Delegated Admin Privileges (GDAP)](gdap-bulk-migration-tool.md).
  - Ensure that GDAP relationships are utilizing roles with the [least privileges needed](gdap-least-privileged-roles-by-task.md).

### Identity isolation

- Avoid hosting your Partner Center instance in the same Azure AD tenant that hosts your internal IT services, such as email and collaboration tools.
- Use separate, dedicated user accounts for Partner Center privileged users who have customer access.
- Avoid creating user accounts in customer Azure AD tenants intended to be used by partners to administer the customer tenant and related apps and services.

## Devices best practices

- Only allow Partner Center and customer tenant access from registered, healthy workstations that have managed security baselines and are monitored for security risks.
- For Partner Center users with privileged access to customer environments, consider requiring dedicated workstations (virtual or physical) for those users to access customer environments.  For more information, see [Securing privileged access](/security/compass/overview).

## Monitoring best practices

### Partner Center APIs

- All Control Panel vendors should [Enable the secure application model](/partner-center/develop/enable-secure-app-model) and turn on logging for every user activity.
- Control Panel vendors should enable auditing of every partner agent logging into the application and all actions taken.

### Sign-in monitoring and auditing

- Partners with an Azure Active Directory P2 license automatically qualify to keep audit and sign-in log data up to 30 days.
  
  Confirm that:
  - Audit logging is in place where delegated administrator accounts are used.
  - Logs are capturing the maximum level of details provided by the service.
  - Logs are retained for an acceptable period (up to 30 days) that allows for detection of anomalous activity.
  
  Detailed audit logging might require purchasing more services. For more information, see [How long does Azure AD store reporting data?](/azure/active-directory/reports-monitoring/reference-reports-data-retention)
- Regularly review and verify password recovery email addresses and phone numbers within Azure AD for all users with the Global admin roles, and update if necessary.
- Implement audit logging best practices and perform routine review of activity performed by delegated administrator accounts.
  - [What are Azure Active Directory reports?](/azure/active-directory/reports-monitoring/overview-reports)
  - [Analyze activity logs using Azure Monitor logs](/azure/active-directory/reports-monitoring/howto-analyze-activity-logs-log-analytics)
  - [Azure AD audit activity reference](/azure/active-directory/reports-monitoring/reference-audit-activities)
- Partners should review the risky users report within their environment and address the accounts that have been detected with risk according to published guidance.
  - [Remediate risks and unblock users](/azure/active-directory/identity-protection/howto-identity-protection-remediate-unblock)
  - [User experiences with Azure AD Identity Protection](/azure/active-directory/identity-protection/concept-identity-protection-user-experience)
  
## Related materials

- For Microsoft security best practices, see [Microsoft Security Best Practices](/security/compass/compass).
- For best practices for managing service principals, see [Securing service principals in Azure Active Directory](/azure/active-directory/fundamentals/service-accounts-principal).
- [Partner security requirements](partner-security-requirements.md)
- [Guiding principles of Zero Trust](/security/zero-trust/)
- [Customer security best practices](customer-security-best-practices.md)
