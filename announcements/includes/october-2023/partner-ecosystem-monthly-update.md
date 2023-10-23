---
title: include file
ms.topic: include
author: JulCsc
ms.author: mdas
ms.date: 10/18/2023
---

## Monthly update: Important actions partners need to take to secure the partner ecosystem

*Important capabilities and updates to improve your security posture and protect your customers' tenants are now available.*

- **Date**: October 18, 2023
- **Workspace**: General
- **Impacted audience**: Direct bill partners, indirect providers, and indirect resellers transacting through the Cloud Solution Provider (CSP) program and with advisors.

From training opportunities to digital marketing campaigns - [here's how we're helping partners improve security capabilities](https://blogs.partner.microsoft.com/partner/keeping-customers-secure-is-a-year-round-opportunity/) as well as land new customers!

#### Milestones reminder

- **Transitioning delegated admin privileges (DAP) relationships to granular delegated admin privileges (GDAP) roles**: Microsoft has completed the creation of GDAP relationships as part of Microsoft-led DAP to GDAP transition and has begun DAP removal.

  - Learn more about the [Microsoft-led transition from DAP to GDAP](../../../gdap-microsoft-led-transition.md) related to this milestone.

  - Validate the newly created GDAP relationship and create a new GDAP relationship with the necessary Microsoft Entra roles in case you require additional roles to manage customers.

- **Creating new customers**: [Default GDAP](../../../gdap-faq.md#what-are-the-timelines-for-stop-dap-and-grant-default-gdap-with-creation-of-a-new-customer) is now available. Partners must explicitly [grant granular permissions to security groups](../../../gdap-assign-azure-ad-roles.md) in the Default GDAP.

  - **DAP is no longer available with reseller relationships.** The updated Request Reseller Relationship link will continue to be available in Partner Center UI and the API contract "/v1/customers/relationship requests" property URL will continue to return the invitation URL to be sent to the admin of the customer tenant.

  - The [**bulk migration tool**](../../../gdap-bulk-migration-tool.md) is available through the end of **November 2023**. You can continue to create and apply [GDAP templates in Microsoft 365 Lighthouse](https://techcommunity.microsoft.com/t5/small-and-medium-business-blog/set-up-granular-delegated-admin-privileges-in-microsoft-365/ba-p/3809422) beyond this date, and a consent link will be generated to provide to customers.

**Partners should continue**:

- **Requesting GDAP** if admin access is required for a customer tenant.

- **Disabling DAP** if DAP relationships are no longer required. The person with the admin agent role within the partner organization should review the [DAP monitoring report](../../../dap-monitor-self-serve-removal.md#dap-monitoring-and-self-service-removal) and [disable DAP relationships](../../../dap-monitor-self-serve-removal.md) immediately.

- To ensure that [their app is consented to in customer tenant](../../../gdap-faq.md#what-action-must-a-partner-perform-moving-from-dap-to-gdap-regarding-consent).

#### Available now

DAP to GDAP **parity feature** update:

- Partners can now [add or edit custom Domain Name System records](/microsoft-365/admin/setup/add-domain#add-or-edit-custom-dns-records) in Microsoft Admin Center.

#### Coming soon

- **GDAP auto extend feature**: Starting October 30, 2023, partners will be able to auto extend new or existing GDAPs by 6 months.

#### Next steps

- Strengthen your security posture and navigate the evolving threat landscape with Microsoft cybersecurity [tools and resources](https://partner.microsoft.com/partnership/partner/security).

- Sign up for dedicated [CSP Security Q&A sessions](https://globalpbocomm.eventbuilder.com/GranularDelegatedAdminPrivilegesinCSPQASession) to have your queries answered by subject matter experts.

- Find guidance and resources in securing the partner and customer ecosystems [partner readiness gallery](https://partner.microsoft.com/resources/collection/granular-delegated-admin-privileges#/).

- Review the [journey map](https://partner.microsoft.com/resources/detail/securing-the-channel-journey-to-zero-trust-pdf) to navigate the transformational journey for partners to Zero Trust.
