---
title: include file
ms.topic: include
author: JulCsc
ms.author: mdas
ms.date: 08/15/2023
---

## Monthly update: Reminder of actions partners need to take with GDAP to secure the partner ecosystem

_Important capabilities and updates to improve your security posture and protect your customers' tenants are now available._

- **Date**: August 15, 2023
- **Workspace**: Account settings
- **Impacted audience**: Direct bill partners, indirect providers, and indirect resellers transacting through the Cloud Solution Provider (CSP) program and with advisors

#### Granular Delegated Admin Privileges (GDAP) milestones reminder

- **Transitioning Delegated Admin Privileges (DAP) relationships to GDAP roles**: Microsoft has begun transitioning DAP relationships to GDAP roles.

  Partners get nine [roles](../../../gdap-microsoft-led-transition.md#what-azure-ad-roles-does-microsoft-assign-when-a-gdap-relationship-is-created-using-the-microsoft-led-transition-tool) as part of the Microsoft-led transition. The roles are granted for a **1-year duration**.

  Read the [frequently asked questions](../../../gdap-faq.md) related to this milestone.

- **Creating new customers**: As of **September 25, 2023**, Microsoft will no longer grant DAP for new customer creation. Instead, Microsoft will grant default GDAP with [specific roles](../../../gdap-faq.md#what-azure-active-directory-roles-would-be-granted-for-default-gdap-as-part-of-create-customer).

- **The bulk migration tool** is available through the end of **November 2023**.

Partners should continue:

- **Requesting GDAP** if admin access is required for a customer tenant.

- **Disabling DAP** if admin access isn't required. The person with the admin agent role within the partner organization should review the [DAP monitoring report](../../../dap-monitor-self-serve-removal.md#dap-monitoring-and-self-service-removal) and [disable DAP relationships](../../../dap-monitor-self-serve-removal.md) immediately.

#### Available now

- DAP to GDAP **parity features** update: Exchange Admin Center has made the following features available with GDAP, with [updated documentation](../../../gdap-supported-workloads.md#exchange-admin-center):

  - Exchange transport rules
  - Public folders
  - Quarantine emails

- **Device management** now requires GDAP relationships. To ensure a seamless experience, Microsoft recommends the **Directory Reader** as the least privileged role for this action. Review how to [upload devices to a new batch](../../../developer/upload-a-list-of-devices-to-create-a-new-batch-for-the-specified-customer.md), [update devices with a policy](../../../developer/update-a-list-of-devices-with-a-policy.md), and [upload devices to an existing batch](../../../developer/upload-a-list-of-devices-for-the-specified-customer.md) for more details.

#### Coming soon

- **GDAP auto extend feature**. In **October 2023**, Microsoft will launch the capability to extend existing GDAP relationships by 6 months. More details will be shared in September.

- **Migrating from AAD to Microsoft Graph API**. Azure AD Graph will be retired shortly. There will be no further investment in Azure AD Graph. Azure AD Graph application programming interfaces have no service-level agreement or maintenance commitment beyond security-related fixes. Investments in new features and functionalities will only be made in Microsoft Graph. All Partners must take action to move to MS Graph. To learn more, see our [latest announcement](https://techcommunity.microsoft.com/t5/microsoft-entra-azure-ad-blog/important-azure-ad-graph-retirement-and-powershell-module/ba-p/3848270).

- **Exchange Online automation change**. The Legacy Exchange Online Public Client ID (_app ID a0c73c16-a7e3-4564-9a95-2bdf47383716_) will be **retired shortly**. Any code that incorporates either the legacy public client or the Partner Center PowerShell module will no longer function. Going forward partners and customers should use Exchange PowerShell to manage Exchange activities. To learn more, see [the Exchange Online PowerShell module](/powershell/exchange/exchange-online-powershell-v2).

#### Next steps

- Strengthen your security posture and navigate the evolving threat landscape with Microsoft cybersecurity [tools and resources.](https://partner.microsoft.com/partnership/partner/security)
    
- Sign up for dedicated [CSP Security Q&A sessions](https://globalpbocomm.eventbuilder.com/GranularDelegatedAdminPrivilegesinCSPQASession) to have your questions answered by subject matter experts.
    
- Find guidance and resources in securing the partner and customer ecosystems in  [partner readiness gallery](https://partner.microsoft.com/resources/collection/granular-delegated-admin-privileges#/).
    
- Review the [journey map](https://partner.microsoft.com/resources/detail/securing-the-channel-journey-to-zero-trust-pdf) to navigate the transformational journey for partners to Zero Trust.
