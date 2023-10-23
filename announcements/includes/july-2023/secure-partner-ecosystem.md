---
ms.topic: include 
author: JulCsc 
ms.author: juliacawthra
ms.reviewer: mdas
ms.date: 07/17/2023 
---
## Monthly update: Important actions partners need to take to secure the partner ecosystem

*Important capabilities and updates to improve your security posture and protect your customers' tenants are now available.*

- **Date:** July 17, 2023
- **Workspace:** Account settings
- **Impacted audience:** Direct bill partners, indirect providers, and indirect resellers transacting through the Cloud Solution Provider (CSP) program and with advisors

#### Granular delegated admin privileges (GDAP) milestones reminder

- **Transitioning delegated admin privileges (DAP) relationships to GDAP roles**—Microsoft has begun transitioning DAP relationships to GDAP roles.
  - Based on partner feedback, we’ve added the **global reader** role to the [Microsoft-led transition roles list](../../../gdap-microsoft-led-transition.md#what-azure-ad-roles-does-microsoft-assign-when-a-gdap-relationship-is-created-using-the-microsoft-led-transition-tool). Partners will now get nine roles as part of the Microsoft-led transition. The global reader role is added to the Admin Agent security group. Take note that for GDAP relationships created by Microsoft in May, the global reader role has already been added.
  - GDAP roles created during this transition will be granted for a one-year duration.
  - DAP removals during the Microsoft-led transition:
    - For GDAPs created by partners using either a partner-led tool—Partner Center UI or API—DAP relationships will be removed by the end of July 2023.
    - For GDAPs created as part of the Microsoft-led transition, DAP relationships will be removed 30 days after GDAP is created.
    - For DAPs transitioned to GDAPs by Microsoft in May, DAP relationships will be removed by end of July 2023.
    - When DAP creation is stopped for new customers in September 2023, Microsoft will remove any remaining DAPs.
  - Refer to the [FAQ related to this milestone](../../../gdap-faq.md#how-can-i-continue-to-administer-services-for-my-customers-if-dap-for-inactive-customers-is-removed).
- **Creating new customers**—DAP is currently granted when a new customer tenant is created. Starting September 25, 2023, Microsoft will no longer grant DAP for new customer creation and will instead grant default GDAP with specific roles. The default roles vary by partner type; you can [find the latest default roles in this FAQ](../../../gdap-faq.md#what-azure-active-directory-roles-would-be-granted-for-default-gdap-as-part-of-create-customer).
- The **bulk migration tool** will be available through the end of November 2023.

#### Actions that partners should continue

- **Requesting GDAP**—If admin access is required for a customer tenant, the person with the admin agent role within the partner organization should request, and the customer should [approve a GDAP relationship](../../../gdap-customer-approval.md) with the appropriate Azure Active Directory (Azure AD) roles.
- **Disabling DAP**—If admin access isn’t required, the person with the admin agent role within the partner organization should review the [DAP monitoring report](../../../dap-monitor-self-serve-removal.md) and [disable DAP relationships](../../../dap-monitor-self-serve-removal.md) immediately. If admin access is needed, the partner should complete the GDAP setup, and then disable DAP. DAP can be disabled in bulk using the [bulk migration tool](../../../gdap-bulk-migration-tool.md).

#### Other security updates

- Partners can now request a **quota increase** using the self-serve tools. We’ve enabled a self-serve capability for Cloud Solution Provider (CSP) partners to request a quota increase on their customers’ Azure subscriptions. Partners can request quota using the [Azure portal](/azure/quotas/quickstart-increase-quota-portal) or [Quota - Update - REST API](/rest/api/reserved-vm-instances/quota/update). For security reasons, quota requests are only allowed by CSP partners and not by customers. Partners need to request using the admin on behalf of (AOBO) permissions to enable their customers to make quota requests.
- The following **DAP-to-GDAP parity features** are now available:
  - Exchange Admin Center has made the following available with GDAP, with [updated Microsoft Learn documentation](../../../gdap-supported-workloads.md#exchange-admin-center):
    - Organization—Sharing
    - Public folders—Mailbox
  - The guest inviter role has been fixed and now works with other workloads.
  - Partners can now search for users in the Azure AD portal.
  - Partner Center: The **View all resources on Azure portal** link is available under **Subscriptions**.
- We recommend partners who are using the partner-led tool or creating new GDAPs select the **privileged authentication administrator** Azure AD role so they can reset the password and authentication method for a user (admin or non-admin). This will be provided to GDAPs created during the Microsoft-led transition, as well as default GDAPs granted during new customer creation starting in September 2023. You can [find more information in this FAQ](../../../gdap-faq.md#what-roles-are-required-by-a-partner-to-reset-an-admin-password-and-mfa-device-if-a-customer-admin-is-locked-out-of-their-account-and-cant-accept-a-gdap-relationship-request-from-a-partner).
- Starting September 25, 2023, **DAP will no longer be available with reseller relationships**. The updated **Request Reseller Relationship** link will continue to be available in Partner Center UI and the API contract “/v1/customers/relationship requests” property URL will continue to return the invitation URL to be sent to the admin of the customer tenant.
- **Creating support tickets**—For a quicker turnaround for DAP-to-GDAP parity issues, partners should create tickets via the customer portal or through Partner Center for Partner Center-related issues.
- **New customer FAQ available**—We’ve created an FAQ to [help partners address questions around DAP and GDAP with their customers](../../../gdap-migration-faq.md).
- **Updated technical training for partners** is now available. It consists of a one-hour live webinar, followed by a modular on-demand training program that partners can take at their own pace. You can register for the [live webinars](https://info.microsoft.com/US-NoGEP-CATALOG-FY24-07Jul-03-Security-through-the-lens-of-Zero-Trust-SREVM18140_Catalog-Display-Page.html) and then take the [on-demand training](https://learn.get365ready.com/user_catalog_class/show/1119138) (the access code will be shared during the live webinar) which includes the following articles:
  - Securing identities in the cloud and implementing Office 365 security
  - Securing workloads in the cloud with Microsoft Defender for Cloud
  - Securing cloud workloads with Azure Network security and XDR
  - Managing your security posture in the cloud and defending against threats on endpoints

### Next steps

- Strengthen your security posture and navigate the evolving threat landscape with Microsoft cybersecurity [tools and resources](https://partner.microsoft.com/partnership/partner/security).
- Sign up for dedicated [CSP Security Q&A sessions](https://globalpbocomm.eventbuilder.com/GranularDelegatedAdminPrivilegesinCSPQASession) to have your queries answered by subject matter experts.
- Find guidance and resources in securing the partner and customer ecosystems [partner readiness gallery](https://partner.microsoft.com/resources/collection/granular-delegated-admin-privileges#/).
- Review the [journey map](https://partner.microsoft.com/resources/detail/securing-the-channel-journey-to-zero-trust-pdf) to navigate the transformational journey for partners to Zero Trust.
