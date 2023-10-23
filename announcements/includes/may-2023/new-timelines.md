---
ms.topic: include
author: JulCsc
ms.author: juliacawthra
ms.reviewer: mdas
ms.date: 05/23/2023
---
## New timelines: Important actions to secure the partner ecosystem

*Important capabilities and updates to improve your security posture and protect your customers' tenants are now available.*

- **Date**: May 18, 2023
- **Workspace**: Account settings
- **Impacted audience**: Direct bill partners, indirect providers, and indirect resellers transacting through the Cloud Solution Provider (CSP) program and with advisors

We'd like to share the latest dates for the upcoming granular delegated admin privileges (GDAP) milestones.

#### Transitioning delegated admin privileges (DAP) relationships to GDAP roles

Microsoft will begin transitioning DAP relationships to GDAP roles as of **May 22, 2023**. Details on the GDAP roles can be found in the [April announcement](../../2023-april.md#11).

- A notification is sent to the admin agent security group users once the GDAP relationship has been set up successfully.
  
  > [!IMPORTANT]
  > **May 23 update**: Based on partner feedback received, we have suppressed the GDAP notifications when relations are set up successfully during this Microsoft-led transition process.

- This transition excludes scenarios where a GDAP relationship exists in an expired, pending, or terminated state.
- For more information, see [GDAP Microsoft-led transition](../../../gdap-microsoft-led-transition.md).

#### Creating new customers

DAP is currently granted when a new customer tenant is created. As of **September 25, 2023**, Microsoft will no longer grant DAP for new customer creation and will instead grant GDAP with default roles when a new customer tenant is created.

The default roles vary by partner type. The following table lists the respective roles:

| Default Azure Active Directory (Azure AD) roles granted | Description | Indirect providers | Indirect resellers | Direct partners |
| ------------| ------------| ------------ | ------------| ------------|
| [Directory readers](/azure/active-directory/roles/permissions-reference#directory-readers) | Can read basic directory information; commonly used to grant directory read access to applications and guests | x | x | x |
| [Directory writers](/azure/active-directory/roles/permissions-reference#directory-writers) | Can read and write basic directory information; for granting access to applications, not intended for users  | x | x | x |
| [License administrator](/azure/active-directory/roles/permissions-reference#license-administrator) | Can manage product licenses on users and groups | x | x | x |
| [Service support administrator](/azure/active-directory/roles/permissions-reference#service-support-administrator) | Can read service health information and manage support tickets | x | x | x |
| [User administrator](/azure/active-directory/roles/permissions-reference#user-administrator) | Can manage all aspects of users and groups, including resetting passwords for limited admins | x | x | x |
| [Privileged role administrator](/azure/active-directory/roles/permissions-reference#privileged-role-administrator) | Can manage role assignments in Azure AD, and all aspects of Privileged Identity Management | x | x | x |
| [Help desk administrator](/azure/active-directory/roles/permissions-reference#helpdesk-administrator) | Can reset passwords for nonadministrators and help desk administrators | x | x | x |
| [Privileged authentication administrator](/azure/active-directory/roles/permissions-reference#privileged-role-administrator) | Can access to view, set, and reset authentication method information for any user (admin or nonadmin) | x | x | x |
| [Cloud application administrator](/azure/active-directory/roles/permissions-reference#cloud-application-administrator) | Can create and manage all aspects of app registrations and enterprise apps except App Proxy | x | | |
| [Application administrator](/azure/active-directory/roles/permissions-reference#application-administrator) | Can create and manage all aspects of app registrations and enterprise apps | x | | |
| [Global reader](/azure/active-directory/roles/permissions-reference#global-reader) | Can read everything that a global administrator can, but can't update anything | x | x | x |

#### Retirement of bulk migration tool

The tool is still available through the **end of November 2023**.

Partners should continue:

- **Requesting GDAP**: If admin access is required for a customer tenant, then the partner (with the admin agent role within the partner organization) should request, and the customer should [approve a GDAP relationship](../../../gdap-customer-approval.md) with the appropriate Azure AD roles.
- **Disabling DAP**: If admin access isn't required, the partner (with the admin agent role within the partner organization) should review the [DAP monitoring report](../../../dap-monitor-self-serve-removal.md#dap-monitoring-and-self-service-removal) and [disable DAP relationships](../../../dap-monitor-self-serve-removal.md) immediately. If admin access is needed, then the partner should complete the GDAP setup and then disable DAP. DAP can now be disabled in bulk using the [bulk migration tool](../../../gdap-bulk-migration-tool.md).

Some other security updates are as follows:

- Starting **May 31, 2023**, we're launching a **new security alerts dashboard** in Partner Center to help partners protect and detect Azure fraud. The detections are based on a set of anomalies across ARM activities, billing meter consumption, identity risk signals, crypto mining, and quota increase requests. Partners should immediately take action to adopt the new security alerts in the Partner Center portal and/or API to mitigate any monetary loss. For more information, see [Azure fraud detection and notification](../../../azure-fraud-notification.md).
- **GDAP relationship creation issue fixed**—A fix has been deployed in April to resolve the issue faced during customer creation, where a 404 error was displayed for partners with no existing reseller relationship with the customer. This took place when they navigated to **Partner Center** portal > **Customer** workspace > **Administer** > **Customer** > **New Relationship**.

#### Next steps

- Strengthen your security posture and navigate the evolving threat landscape with Microsoft cybersecurity [tools and resources](https://partner.microsoft.com/partnership/partner/security).
- Sign up for dedicated [CSP Security Q&A sessions](https://globalpbocomm.eventbuilder.com/GranularDelegatedAdminPrivilegesinCSPQASession) to have your queries answered by subject matter experts.
- Find guidance and resources in securing the partner and customer ecosystems [Partner Readiness gallery](https://partner.microsoft.com/resources/collection/granular-delegated-admin-privileges#/).
- Review the [journey map](https://partner.microsoft.com/resources/detail/securing-the-channel-journey-to-zero-trust-pdf) to navigate the transformational journey for partners to Zero Trust.
