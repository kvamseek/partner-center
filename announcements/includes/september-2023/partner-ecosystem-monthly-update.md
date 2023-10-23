---
title: include file
ms.topic: include
author: JulCsc
ms.author: mdas
ms.date: 09/19/2023
---

## Monthly update: Important actions partners need to take to secure the partner ecosystem

*Important capabilities and updates to improve your security posture and protect your customers' tenants are now available.*

- **Date**: September 19, 2023
- **Workspace**: General
- **Impacted audience**: Direct bill partners, indirect providers, and indirect resellers transacting through the Cloud Solution Provider (CSP) program and with advisors.

#### Milestones reminder

- **Transitioning delegated admin privileges (DAP) relationships to granular delegated admin privileges (GDAP) roles**—Microsoft has completed the creation of GDAP relationships as part of Microsoft-led DAP to GDAP transition and has begun DAP removal:

  - Review the [frequently asked questions](../../../gdap-faq.md#gdap-frequently-asked-questions) related to this milestone.
  - Validate the newly created GDAP relationship and create a new GDAP relationship with the necessary Azure Active Directory (AAD) roles in case you require extra AAD roles to manage customers.

- **Creating new customers**—Default GDAP will be available in Sandbox starting September 25 and in production starting October 9. [More details are available](../../../gdap-faq.md#what-are-the-timelines-for-stop-dap-and-grant-default-gdap-with-creation-of-a-new-customer). Partners must explicitly grant granular permissions to security groups in the [Default GDAP](../../../gdap-assign-azure-ad-roles.md).

- On October 9, 2023, **DAP will no longer be available with reseller relationships**. The updated *Request Reseller Relationship* link remains available in Partner Center UI and the API contract “/v1/customers/relationship requests” property URL still returns the invitation URL sent to the admin of the customer tenant.

- The [**bulk migration**](../../../gdap-bulk-migration-tool.md) tool is available through the end of November 2023. You can continue to create and apply [GDAP templates in Microsoft 365 Lighthouse](https://techcommunity.microsoft.com/t5/small-and-medium-business-blog/set-up-granular-delegated-admin-privileges-in-microsoft-365/ba-p/3809422) beyond this date, and a consent link is generated to provide to customers.

Partners should continue:

- **Requesting GDAP** if admin access is required for a customer tenant.
- **Disabling DAP** if DAP relationships are no longer required. The person with the admin agent role within the partner organization should review the [DAP monitoring report](../../../dap-monitor-self-serve-removal.md#dap-monitoring-and-self-service-removal) and [disable DAP relationships](../../../dap-monitor-self-serve-removal.md) immediately.

#### Available now

- **Microsoft 365 Lighthouse** enables GDAP setup for any customer tenant with built-in role recommendations tailored for Managed Service Providers. Partners can create GDAP templates to save settings they’ve configured and reapply them as needed. [Review the guidance and details](https://techcommunity.microsoft.com/t5/small-and-medium-business-blog/set-up-granular-delegated-admin-privileges-in-microsoft-365/ba-p/3809422).

- Familiarize yourself with the new GDAP UI in Admin Relationships and Role assignments to Security Groups within Partner Center.

- Reminder that AAD is now called [Microsoft Entra ID](/azure/active-directory/fundamentals/new-name).

- Endpoint Manager has been renamed to Microsoft Intune under Administer Services in Service Management page.

#### Coming soon

- **GDAP auto extend feature**—Starting October 30, 2023, partners will be able to auto extend new or existing GDAPs by 6 months.

- **Migrating from AAD to Microsoft Graph API**—AAD Graph will be **retired soon**. There won't be further investment in AAD Graph, and AAD Application Programming Interfaces (APIs) have no service level agreement or maintenance commitment beyond security-related fixes. Investments in new features and functionalities are only made in Microsoft Graph. All partners must take steps to migrate existing apps/APIs on AAD Graph to Microsoft Graph. APIs: Review [Partner Center authentication](../../../developer/partner-center-authentication.md) for more information.

#### Next steps

1. Strengthen your security posture and navigate the evolving threat landscape with Microsoft cybersecurity [tools and resources](https://partner.microsoft.com/partnership/partner/security).
2. Sign up for dedicated [CSP Security Q&A sessions](https://globalpbocomm.eventbuilder.com/GranularDelegatedAdminPrivilegesinCSPQASession) to have your queries answered by subject matter experts.
3. Find guidance and resources in securing the partner and customer ecosystems [partner readiness gallery](https://partner.microsoft.com/resources/collection/granular-delegated-admin-privileges#/).
4. Review the [journey map](https://partner.microsoft.com/resources/detail/securing-the-channel-journey-to-zero-trust-pdf) to navigate the transformational journey for partners to Zero Trust.
