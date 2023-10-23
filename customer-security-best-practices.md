---
title: Customer security best practices
ms.topic: article
ms.date: 03/21/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Learn customer security best practices.
author: vijay-vala
ms.author: vijvala
---

# Customer security best practices

**Appropriate roles**: Global Admin | Admin Agent | Helpdesk Agent

All customers of Cloud Solution Provider (CSP) partners should follow the security guidance in this article.

For security best practices for Cloud Solution Providers, see [CSP security best practices](csp-security-best-practices.md).

___

- Ensure **multifactor authentication (MFA) is enabled and registered on every account**. Use either Microsoft Azure Active Directory (Azure AD) [security defaults](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) or [Conditional Access](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) to enforce MFA.  MFA is the best baseline security hygiene method to protect against threats.
  - Consider using passwordless sign-in with the [Microsoft Authenticator app](/azure/active-directory/authentication/howto-authentication-passwordless-phone).
- Frequently review subscriptions and resources or services that might have been provisioned unexpectedly.
  - Review the [Azure Monitor activity log](/azure/azure-monitor/essentials/activity-log?tabs=powershell) for Azure subscription-related activity.
- Utilize [cost anomaly alerts](/azure/cost-management-billing/understand/analyze-unexpected-charges#create-an-anomaly-alert) to detect unexpected high consumption in your Azure subscription.
- Users who have Azure AD administrative roles such as Global Administrator or Security Administrator should not be regularly used for email and collaboration.  Create a separate user account with no Azure AD administrative roles for collaboration tasks.
- Regularly review and verify password recovery email addresses and phone numbers within Azure AD for all users with the Global Admin roles and update if necessary.
- **Review, audit, and minimize access privileges and delegated permissions.** It's important to consider and implement a least-privilege approach. Microsoft recommends prioritizing a thorough [review and audit of partner relationships](/microsoft-365/commerce/manage-partners?view=o365-worldwide&preserve-view=true) to minimize any unnecessary permissions between your organization and upstream providers. Microsoft recommends immediately removing access for any partner relationships that look unfamiliar or haven't yet been audited.
- **Review, harden, and monitor all tenant administrator accounts:** All organizations should thoroughly review all tenant admin users, including users associated with [Administer On Behalf Of (AOBO)](./azure-plan-manage.md) in Azure subscriptions, and verify the authenticity of the users and activity. We strongly encourage the use of phishing-resistant MFA for all tenant administrators, review of devices registered for use with MFA, and minimizing the use of standing high-privilege access. Continue to reinspect all active tenant admin users accounts, and check audit logs regularly to verify that high-privilege user access isn't granted or delegated to admin users who don't require those privileges to do their jobs.
- **Review service provider permissions access from B2B and local accounts:** In addition to using delegated administrative privilege capabilities, some cloud service providers use business-to-business (B2B) accounts or local administrator accounts in customer tenants. We recommend that you identify whether your cloud service providers use these accounts, and if so, ensure that those accounts are well governed and have least-privilege access in your tenant. Microsoft recommends against the use of "shared" administrator accounts. Review the [detailed guidance](/azure/active-directory/external-identities/auditing-and-reporting) on how to review permissions for B2B accounts.
- **Review and audit Azure AD sign-ins and configuration changes:** Authentications of this nature are audited and available to customers through the [Azure AD sign in logs](/azure/active-directory/reports-monitoring/concept-sign-ins), [Azure AD audit logs](/azure/active-directory/reports-monitoring/concept-audit-logs), and the [Microsoft Purview compliance portal](/exchange/security-and-compliance/exchange-auditing-reports/search-role-group-changes) (formerly in the Exchange Admin Center). We recently added the capability to see sign-ins by partners who have delegated admin permissions. You can see a filtered view of those sign-ins by going to the sign-in logs in the [Azure AD admin portal](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/SignIns) and adding the filter **Cross-tenant access type: Service provider** on the **User-sign ins (non-interactive)** tab.

:::image type="content" source="media/customer-security-best-practices/azure-ad-admin-portal-filter.png" alt-text="Screenshot of Azure AD admin portal, adding a filter Cross-tenant access type:Service provider on the User-sign ins.":::

- **Review Existing Log Availability and Retention Strategies:** Investigating activities conducted by malicious actors places a large emphasis on having adequate log-retention procedures for cloud-based resources, including Microsoft 365. Various subscription levels have individualized log availability and retention policies, which are important to understand before forming an incident response procedure.

We encourage all organizations to become familiar with the logs made available within your subscription and to evaluate them routinely for adequacy and anomalies. For organizations relying on a third-party organization, work with them to understand their logging strategy for all administrative actions and establish a process should logs need to be made available during an incident.

## See also

[CSP security best practices](csp-security-best-practices.md)

