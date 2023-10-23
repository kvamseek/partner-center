---
title: include file
ms.topic: include
author: kvamseek
ms.author: vamseekk
ms.reviewer: vamseekk
ms.date: 06/15/2023
---

## Monthly update: Important actions to secure the partner ecosystem

_Important capabilities and updates to improve your security posture and protect your customers' tenants are now available._

- **Date**: June 16, 2023
- **Workspace**: Account settings
- **Impacted audience**: Direct bill partners, indirect providers, and indirect resellers transacting through the Cloud Solution Provider (CSP) program and with advisors

#### Sign up for new security alerts today to help prevent unauthorized party abuse

The complexity, scale, and volume of threats is increasing. To help you detect and address them quickly, we’ve released [new security alerts](../../../azure-fraud-notification.md) that analyze anomalies across Azure Resource Manager (ARM) activities, deployment of workloads, billing meter consumption spikes, identity risk signals, crypto mining, and quota increase requests. Partners should immediately take action to adopt the new security alerts in Partner Center and/or API to mitigate any monetary loss.

Partners can sign in to [Partner Center](https://partner.microsoft.com/dashboard/commerce2/insights/security/alerts) to [review and resolve alerts](../../../security-alerts-dashboard.md). API partners need to make [API](../../../developer/get-fraud-events.md#rest-request-with-the-x-neweventsmodel-header) changes to get the new alerts. Learn more about the security alerts at [Azure fraud detection and notification](../../../azure-fraud-notification.md).

#### Granular delegated admin privileges (GDAP) milestones reminder

- **Transitioning delegated admin privileges (DAP) relationships to GDAP roles**: Microsoft has begun transitioning DAP relationships to GDAP roles. Details on the GDAP roles can be found in the [April announcement](../../2023-april.md#11).
  - Based on partner feedback received, we’ve suppressed the GDAP notifications when relations are set up successfully during this Microsoft-led transition process.
  - This transition excludes scenarios where a GDAP relationship exists in an expired, pending or terminated state at the time of migration.
  - GDAP roles created during this transition will be granted for a one-year duration.
  - Partners will need to ensure they carry out access assignments by providing the necessary roles to their security groups for certain conditional access policies enabled by the customer after the GDAP relationship is created during Microsoft-led migration.
  - You can find [FAQs related to this milestone here](../../../gdap-microsoft-led-transition.md).
- **Creating new customers**: DAP is currently granted when a new customer tenant is created. Starting September 25, 2023, Microsoft will no longer grant DAP for new customer creation and will instead grant GDAP with default roles when a new customer tenant is created. The default roles vary by partner type, and the respective roles can be found in the [May announcement](../../2023-may.md#creating-new-customers).
- The **bulk migration tool** will be available through the end of November 2023.

#### Continued action for partners

- **Requesting GDAP**: If admin access is required for a customer tenant, then the partner (with the admin agent role within the partner organization) should request, and the customer should approve [a GDAP relationship](../../../gdap-customer-approval.md) with the appropriate Azure Active Directory roles.
- **Disabling DAP**:  If admin access isn’t required, then partners (with the admin agent role within the partner organization) should review the [DAP monitoring report](../../../dap-monitor-self-serve-removal.md#dap-monitoring-and-self-service-removal) and [disable DAP relationships](../../../dap-monitor-self-serve-removal.md) immediately. If admin access is needed, the partner should complete the GDAP setup, and then disable DAP. DAP can now be disabled in bulk using the [bulk migration tool](../../../gdap-bulk-migration-tool.md).

#### Other security updates

- **Now generally available: Native integration of Microsoft Defender for Cloud Apps in Microsoft 365 Defender**: We’re happy to announce that the entire Microsoft Defender for Cloud Apps experience in Microsoft 365 Defender, which supports GDAP, is now available.
  - Enjoy a [short tour](https://www.microsoft.com/videoplayer/embed/RE59yVU) and review our [documentation](/microsoft-365/security/defender/microsoft-365-security-center-defender-cloud-apps). Automatic redirection is generally available to customers. While it’s currently set to off by default, we’ll start automatically redirecting customers to Microsoft 365 Defender soon. The classic Microsoft Defender for Cloud Apps will be retired towards the beginning of calendar year 2024.
  - As Microsoft 365 Defender supports GDAP, we encourage you to migrate from DAP to GDAP to start using Microsoft 365 Defender exclusively.
- **GDAP parity issues fixed**: As Microsoft continues to bridge parity gaps, we’ll update the [documentation](../../../gdap-supported-workloads.md) to reflect the same. This month, we’d like to highlight:
  - **Microsoft Admin Center (MAC)—Tenant Switcher and All Tenants** page was fixed on May 25, 2023.
  - **SharePoint**: Partners can’t [edit files and permissions](../../../gdap-supported-workloads.md#sharepoint) on files and folders within their customers' SharePoint site. This was a security risk for customers and has since been addressed.

#### Next steps

- Strengthen your security posture and navigate the evolving threat landscape with Microsoft cybersecurity [tools and resources](https://partner.microsoft.com/partnership/partner/security).
- Sign up for dedicated [CSP Security Q&A sessions](https://globalpbocomm.eventbuilder.com/GranularDelegatedAdminPrivilegesinCSPQASession) to have your queries answered by subject matter experts.
- Find guidance and resources in the securing the partner and customer ecosystems [partner readiness gallery](https://partner.microsoft.com/resources/collection/granular-delegated-admin-privileges#/).
- Review the [journey map](https://partner.microsoft.com/resources/detail/securing-the-channel-journey-to-zero-trust-pdf) to navigate the transformational journey for partners to Zero Trust.
