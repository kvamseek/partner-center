---
author: JulCsc
ms.author: juliacawthra
ms.reviewer: mdas
ms.date: 04/19/2023
---

## Security reminder: Important actions for partners to secure the partner ecosystem

*Important capabilities and updates to improve your security posture and protect your customers' tenants are now available.*

- **Date**: April 19, 2023
- **Workspace**: Account settings
- **Impacted audience**: Direct bill partners, indirect providers, and indirect resellers transacting through the Cloud Solution Provider (CSP) program and with advisors

Partners should continue securing their access with the following steps:

1. **Requesting granular delegated admin privileges (GDAP)**: If admin access is required for a customer tenant, then the partner (with the admin agent role within the partner organization) should request, and customer should [approve a GDAP relationship](../../../gdap-customer-approval.md) with the appropriate Azure Active Directory (AD) roles.
1. **Disabling delegated admin privileges (DAP)**: If admin access isn’t required, then the partner (with the admin agent role within the partner organization) should review the [DAP monitoring report](../../../dap-monitor-self-serve-removal.md#dap-monitoring-and-self-service-removal) and [disable DAP relationships](../../../dap-monitor-self-serve-removal.md) immediately. If admin access is needed, then the partner should complete the GDAP setup and then disable DAP.

Microsoft will begin transitioning DAP relationships to GDAP roles starting May 22, 2023. Default roles will be automatically assigned to corresponding predefined CSP security groups, which could fall under either admin agents or help desk agents.

#### Admin agents security group

- [Directory readers](/azure/active-directory/roles/permissions-reference#directory-readers): Can read basic directory information; commonly used to grant directory read access to applications and guests
- [Directory writers](/azure/active-directory/roles/permissions-reference#directory-writers): Can read and write basic directory information; for granting access to applications, not intended for users
- [License administrator](/azure/active-directory/roles/permissions-reference#license-administrator): Can manage product licenses on users and groups
- [User administrator](/azure/active-directory/roles/permissions-reference#user-administrator): Can manage all aspects of users and groups, including resetting passwords for limited admins
- [Privileged role administrator](/azure/active-directory/roles/permissions-reference#privileged-role-administrator): Can manage role assignments in Azure AD and all aspects of Privileged Identity Management (PIM)
- [Privileged authentication administrator](/azure/active-directory/roles/permissions-reference#privileged-authentication-administrator): Can access view, set, and reset authentication method information for any user (admin or nonadmin)
- [Service support administrator](/azure/active-directory/roles/permissions-reference#service-support-administrator): Can read service health information and manage support tickets
- [Help desk administrator](/azure/active-directory/roles/permissions-reference#helpdesk-administrator): Can reset passwords for nonadministrators and help desk administrators

#### Help desk agents security group

1. [Service support administrator](/azure/active-directory/roles/permissions-reference#service-support-administrator): Can read service health information and manage support tickets
2. [Help desk administrator](/azure/active-directory/roles/permissions-reference#helpdesk-administrator): Can reset passwords for nonadministrators and help desk administrators

#### Latest updates

- **Parity features now available in the Exchange Admin Center (EAC)**: EAC has made the following available with GDAP, with [updated learning documentation](../../../gdap-supported-workloads.md#exchange-admin-center):
  - Groups management
  - Rules
  - Link to go to Microsoft 365 Admin Center
  - Support Central widget
  - Give Feedback widget
- **New customer FAQs now available**: To help partners address questions around DAP and GDAP with their customers, we’ve created a set of [FAQs](../../../gdap-migration-faq.md).

#### Reminders

- **Bulk migration tool**: This tool has been enhanced to allow partners to remove DAP relationships in bulk. It also allows you to carry out bulk editing, deletion of access assignments, and deletion of GDAP relationships. For more information, see [GDAP bulk migration tool](../../../gdap-bulk-migration-tool.md).
- **Now fixed: Customer details section on the account page with no DAP**: Partners transitioning from DAP to GDAP were seeing issues in the **Customer details** section on the **Accounts page**. On March 20, 2023, a fix was deployed. More details are available [in this FAQ](../../../gdap-faq.md#why-is-the-company-details-section-in-the-account-page-under-customers-no-longer-displaying-details-when-dap-is-removed).
- **Advisors can now establish GDAP relationships successfully**: On April 10, 2023, we deployed a fix that resolved the "Something went wrong on our end. Please try again later" error, allowing an advisor admin relationship to be approved by customer.

#### Next steps

- Strengthen your security posture and navigate the evolving threat landscape with Microsoft cybersecurity [tools and resources](https://partner.microsoft.com/partnership/partner/security).
- Sign up for dedicated [CSP Security Q&A sessions](https://globalpbocomm.eventbuilder.com/GranularDelegatedAdminPrivilegesinCSPQASession) to have your queries answered by subject matter experts.
- Find guidance and resources in securing the partner and customer ecosystems in the [Partner Readiness gallery](https://partner.microsoft.com/resources/collection/granular-delegated-admin-privileges#/).
