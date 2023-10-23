---
title: Workloads supported by granular delegated admin privileges (GDAP)
ms.topic: article
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Description of workloads supported by GDAP.
author: kvamseek
ms.author: vamseekk
ms.date: 8/27/2023
---

# Workloads supported by granular delegated admin privileges (GDAP)

**Appropriate roles**: All users interested in Partner Center

This article lists tasks for workloads supported by granular delegated admin privileges (GDAP).

The following workloads are supported:

- [Workloads supported by granular delegated admin privileges (GDAP)](#workloads-supported-by-granular-delegated-admin-privileges-gdap)
  - [Azure AD](#azure-ad)
  - [Exchange admin center](#exchange-admin-center)
  - [Microsoft 365 admin center](#microsoft-365-admin-center)
  - [Microsoft Purview](#microsoft-purview)
  - [Microsoft 365 Lighthouse](#microsoft-365-lighthouse)
  - [Windows 365](#windows-365)
  - [Teams admin center](#teams-admin-center)
  - [Microsoft 365 Defender](#microsoft-365-defender)
    - [Supported MDE features in Microsoft 365 Defender portal per SKU](#supported-mde-features-in-microsoft-365-defender-portal-per-sku)
  - [Power BI](#power-bi)
  - [SharePoint](#sharepoint)
  - [Dynamics 365 and Power Platform](#dynamics-365-and-power-platform)
  - [Dynamics 365 Business Central](#dynamics-365-business-central)
  - [Dynamics Lifecycle Services](#dynamics-lifecycle-services)
  - [Intune (Endpoint Manager)](#intune-endpoint-manager)
  - [Azure portal](#azure-portal)
  - [Alternative Azure GDAP guidance (without using Admin Agent)](#alternative-azure-gdap-guidance-without-using-admin-agent)
  - [Visual Studio](#visual-studio)
  - [Why don't I see some DAP AOBO links in GDAP Service management page?](#why-dont-i-see-some-dap-aobo-links-in-gdap-service-management-page)
  - [Next steps](#next-steps)

## Azure AD

All Azure AD tasks are supported except the following capabilities:

| Area | Capabilities | Issue
|:--------------|:-----------|:-----------
| Group management | Creation of Microsoft 365 group, Administration of dynamic membership rules | Not supported
| Devices | Administration of settings for Enterprise State Roaming |
| Applications | Consenting to an enterprise application inline with sign-in, Administration of enterprise application ‘User settings' |
| External identities | Administration of external identity features |
| Monitoring | Log analytics, Diagnostic settings, Workbooks, and the ‘Monitoring' tab on Microsoft Azure Active Directory (Azure AD) overview page |
| Overview page | My feed - roles for signed-in user | May display incorrect role information; doesn't affect actual permissions
| User settings | ‘User features' management page | Not accessible to certain roles
___

## Exchange admin center

For the Exchange admin center, the following tasks are supported by GDAP.

| Resource type | Resource subtype | Currently supported | Issue
|:--------------|:-----------|:------------------|:--------
| Recipient management | Mailboxes | Create Shared Mailbox, Update Mailbox, Convert to Shared/User Mailbox, Delete Shared Mailbox, Manage Mail-flow Settings, Manage Mailbox Policies, Manage Mailbox Delegation, Manage Email Addresses, Manage Automatic Replies, Manage More Actions, Edit Contact Information, Groups Management | Open another user's mailbox
| | Resources | Create/Add a Resource [Equipment/Room], Delete a Resource, Manage Hide from GAL setting, Manage Booking delegates settings, Manage Resource delegates settings |
| | Contacts | Create/Add a Contact [Mail User/Mail Contact], Delete a Contact, Edit Organization Settings |
| Mail-flow | Message Trace | Start a Message Trace, Check default/custom/autosaved/downloadable queries, Rules | Alert, Alert Policies
| | Remote Domains | Add a Remote Domain, Delete a Remote Domain, Edit Message Reporting, Reply Types | |
| | Accepted Domains | Manage Accepted Domains | |
| | Connectors     | Add a Connector, Manage Restrictions, Sent email identity, Delete Connector
| Roles | Admin Roles | Add Role Group, Delete Role Groups that aren't in-built Role Groups, Edit Role Groups that aren't in-built Role Groups, Copy Role Group |
| Migration | Migration | Add Migration Batch, Try Google Workspace Migration, Approve Migration Batch, View Details of the Migration Batch, Delete Migration Batch
| Microsoft 365 admin center link | | Link to go to Microsoft 365 Admin Center |
| Miscellaneous | | Give Feedback Widget, Support Central Widget
| Dashboard | Reports | |

**Supported RBAC roles** include the following:

- Exchange Administrator
- Global Administrator
- Helpdesk Administrator
- Global Reader
- Security Administrator
- Exchange Recipient Administrator
___

## Microsoft 365 admin center

> [!IMPORTANT]
> Some key features of the Microsoft 365 admin center can be impacted by service incidents and ongoing development work. You can view active Microsoft 365 admin center issues at [Microsoft Admin portal](https://admin.microsoft.com/adminportal?#/servicehealth/).

We're excited to announce the release of the Microsoft 365 admin center support for GDAP. With this preview release, you'll have the ability to sign in to the admin center with all of the [Azure AD roles supported by enterprise customers](/azure/active-directory/roles/permissions-reference) except **Directory Readers**.

This release has limited capabilities and will allow you to use the following areas of the Microsoft 365 admin center:

- **Users** (including assigning licenses)
- **Billing** > **Your Products**
- **Health** > **Service Health**
- **Support Central** > **Creating support ticket**

Known Issues:
- User with Privileged Authentication Administrator role cannot delete a Global Admin user in customer tenant. Workaround: Use delete in Azure Active Directory (AAD).
- Cannot export site usage product reports in Microsoft 365 admin center.
___

## Microsoft Purview

For Microsoft Purview, the following tasks are supported by GDAP.

| Solution | Currently supported | Issue  
|:----------|:----------|:--------
| Audit   | [Microsoft 365 auditing solutions](/microsoft-365/compliance/auditing-solutions-overview?view=o365-worldwide&preserve-view=true) <br> - Set up basic/advanced audit <br> - Search audit log <br> - Using PowerShell to search audit log <br> - Export/configure/view audit log <br> - Turn auditing on and off <br> - Manage audit log retention policies <br> - Investigate common issues/compromised accounts <br> - Export/configure/view audit log |
| Compliance Manager | [Compliance Manager](/microsoft-365/compliance/compliance-manager?view=o365-worldwide&preserve-view=true) <br> - Build and manage assessments <br> - Create/extend/modify assessment templates <br> - Assign and complete improvement actions <br> - Set user permissions |
| MIP | [Microsoft Purview Information Protection](/microsoft-365/compliance/information-protection?view=o365-worldwide&preserve-view=true) <br> [Learn about data classification](/microsoft-365/compliance/data-classification-overview?view=o365-worldwide&preserve-view=true) <br> [Learn about data loss prevention](/microsoft-365/compliance/dlp-learn-about-dlp?view=o365-worldwide&preserve-view=true) <br> **Data Classification**: <br> - Create and manage sensitive information types <br> - Create and manage Exact Data Match <br> - Monitor what's being done with labeled content using Activity Explorer <br> **Information Protection**: <br> - Create and publish sensitivity labels and label policies <br> - Define labels to be applied to files and emails <br> - Define labels to be applied to sites and groups <br> - Define labels to be applied to schematized data assets <br> - Automatically apply a label to content using client-side auto-labeling and server-side auto-labeling and schematized data assets <br> - Restrict access to labeled content using encryption <br> - Configure privacy and external user access and external sharing and conditional access for labels applied to sites and groups <br> - Set label policy to include default, mandatory, downgrade controls and apply them to files and emails, groups and sites and Power BI content <br> **DLP**: <br> - Create, test, and tune a DLP policy <br> - Perform alerts and incident management <br> - View DLP rule match events in activity explorer <br> - Configure Endpoint DLP settings | - View labeled content in Content Explorer <br> - Create and manage Trainable Classifiers <br> - Groups and Sites label support |
| Microsoft Purview Data Lifecycle Management | [Learn about Microsoft Purview Data Lifecycle Management in Microsoft 365](/microsoft-365/compliance/information-governance?view=o365-worldwide&preserve-view=true) <br> - Create and manage static and adaptive retention policies <br> - Create retention labels <br> - Create retention label policies <br> - Create and manage adaptive scopes | - Archiving <br> - Import PST files |
| Microsoft Purview Records Management | [Microsoft Purview Records Management](/microsoft-365/compliance/records-management?view=o365-worldwide&preserve-view=true) <br> - Label content as a record <br> - Label content as a regulatory record <br> - Create and manage static and adaptive retention label policies <br> - Create and manage adaptive scopes <br> - Migrate retention labels and manage your retention requirements with file plan <br> - Configure retention and deletion settings with retention labels <br> - Retain content when an event occurs with event-based retention | - Disposition management |

To learn about supported Azure AD roles in Microsoft 365 compliance portal, see [Permissions in the Microsoft Purview](/microsoft-365/compliance/microsoft-365-compliance-center-permissions?view=o365-worldwide&preserve-view=true)

___

## Microsoft 365 Lighthouse

[Microsoft 365 Lighthouse](/microsoft-365/lighthouse/m365-lighthouse-overview?view=o365-worldwide&preserve-view=true) is an admin portal that helps Managed Service Providers (MSPs) secure and manage devices, data, and users at scale for small and medium-sized business customers.

GDAP roles grant the same customer access in Lighthouse as when those GDAP roles are used to access customers' admin portals individually. Lighthouse provides a multitenant view across users, devices, and data based on users' level of delegated permissions. For an overview of all Lighthouse multitenant management functionality, see the [Lighthouse documentation](/microsoft-365/lighthouse/m365-lighthouse-overview?view=o365-worldwide&preserve-view=true).

Now MSPs can use Lighthouse to set up GDAP for any customer tenant. Lighthouse provides role recommendations based on different MSP job functions for an MSP, and Lighthouse GDAP templates enable partners to easily save and reapply settings that enable least-privileged customer access. For more information, and to view a demo, see the [Lighthouse GDAP setup wizard](/microsoft-365/lighthouse/m365-lighthouse-setup-gdap?view=o365-worldwide&preserve-view=true).

For Microsoft 365 Lighthouse, the following tasks are supported by GDAP. For more information on permissions required to access Microsoft 365 Lighthouse, see [Overview of permissions in Microsoft 365 Lighthouse](/microsoft-365/lighthouse/m365-lighthouse-overview-of-permissions?view=o365-worldwide&preserve-view=true).

| Resource | Currently supported |
|:---------|:---------------|
| Home   |   Included   |
| Tenants | Included |
| Users   | Included |
| Devices | Included |
| Threat management | Included |
| Baselines | Included |
| Windows 365 | Included |
| Service health | Included |
| Audit logs | Included |
| Onboarding | Customers must have either a GDAP and indirect reseller relationship, or a DAP relationship to be onboarded. |

**Supported Azure role-based access control (Azure RBAC) roles** include the following:

- Authentication Administrator
- Compliance Administrator
- Conditional Access Administrator
- Cloud Device Administrator
- Global Administrator
- Global Reader
- Helpdesk Administrator
- Intune Administrator
- Password Administrator
- Privileged Authentication Administrator
- Security Administrator
- Security Operator
- Security Reader
- Service Support Administrator
- User Administrator

___

## Windows 365

For Windows 365, the following tasks are supported by GDAP.

| Resource | Currently supported |
|:---------|:-----------|
| Cloud PC | List Cloud PCs, Get Cloud PC, Reprovision Cloud PC, End grace period, Reprovision Cloud PC remote action, Bulk reprovision Cloud PCs remote action, Resize Cloud PCs remote action, Get Cloud PC remote action results |
| Cloud PC device image | List device images, Get device image, Create device image, Delete device image, Get source image, Reupload device image |
| Cloud PC on-premises network connection | List on-premises connection, Get on-premises connection, Create on-premises connection, Update on-premises connection, Delete on-premises connection, Run health checks, Update AD domain password |
| Cloud PC provisioning policy | List provisioning policies, Get provisioning policy, Create provisioning policy, Update provisioning policy, Delete provisioning policy, Assign provisioning policy |
| Cloud PC audit event | List audit events, Get audit event, Get audit activity types |
| Cloud PC user setting | List user settings, Get user setting, Create user setting, Update user setting, Delete user setting, Assign |
| Cloud PC supported region | List supported regions |
| Cloud PC service plans | List service plans |

**Supported Azure RBAC roles** include the following:

- Global Administrator
- Intune Administrator
- Security Administrator
- Security Operator
- Security Reader
- Global Reader
- (In verification) Windows 365 Administrator

**Unsupported resources for preview:**

- N/A

___

## Teams admin center

For the Teams admin center, the following tasks are supported by GDAP.

| Resource | Currently supported |
|:---------|:-----------|
| Users | Assign policies, Voice settings, Outbound calling, Group call pickup settings, Call delegation settings, Phone numbers, Conferencing settings |
| Teams | Teams policies, Update policies |
| Devices | IP phones, Teams Rooms, Collaboration bars, Teams displays, Teams panels |
| Locations | Reporting labels, Emergency addresses, Network topology, Networks and locations |
| Meetings | Conference bridges, Meeting policies, Meeting settings, Live events policies, Live events settings |
| Messaging policies | Messaging policies |
| Voice | Emergency policies, Dial plans, Voice routing plans, Call queues, Auto attendants, Call park policies, Calling policies, Caller ID policies, Phone numbers, Direct routing |
| Analytics and reports | Usage reports |
| Org-wide settings | External access, Guest access, Teams settings, Teams upgrade, Holidays, Resource accounts |
| Planning | Network planner |
| Teams PowerShell module | All PowerShell cmdlets from the Teams PowerShell module (available from the Teams PowerShell module - 3.2.0 Preview version) |

**Supported RBAC roles** include the following:

- Teams Administrator
- Global Administrator
- Teams Communications Administrator
- Teams Communications Support Engineer
- Teams Communications Support Specialist
- Teams Device Administrator
- Global Reader

**Unsupported resources for GDAP access** include the following:

- Manage Teams
- Team templates
- Teams Apps
- Policy packages
- Teams advisor
- Call Quality Dashboard

___

## Microsoft 365 Defender

Microsoft 365 Defender is a unified pre- and post-breach enterprise defense suite. It natively coordinates detection, prevention, investigation, and response across endpoints, identities, email, and applications to provide integrated protection against sophisticated attacks.

The Microsoft 365 Defender portal is also the home of other products in the Microsoft 365 security stack, such as Microsoft Defender for Endpoint and Microsoft Defender for Office 365.

Documentation of all capabilities and security products is available in the Microsoft 365 Defender portal:

- [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender?view=o365-worldwide&preserve-view=true)

**Microsoft Defender for Endpoint:**

- [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/?view=o365-worldwide&preserve-view=true)
- [Microsoft Defender for Endpoint P1 capabilities](/microsoft-365/security/defender-endpoint/defender-endpoint-plan-1?view=o365-worldwide&preserve-view=true)
- [Microsoft Defender for Business](/microsoft-365/security/defender-business/?view=o365-worldwide&preserve-view=true)

**Microsoft Defender for Office 365:**

- [Exchange Online Protection (EOP)](/microsoft-365/security/office-365-security/exchange-online-protection-overview?view=o365-worldwide&preserve-view=true)
- [Microsoft Defender for Office 365 Plan 1](/microsoft-365/security/office-365-security/defender-for-office-365?view=o365-worldwide#microsoft-defender-for-office-365-plan-1-and-plan-2&preserve-view=true)
- [Microsoft Defender for Office 365 Plan 2](/microsoft-365/security/office-365-security/defender-for-office-365?view=o365-worldwide#microsoft-defender-for-office-365-plan-1-and-plan-2&preserve-view=true)

**App governance:**

- [App governance in Microsoft 365](/defender-cloud-apps/app-governance-manage-app-governance)

The following are capabilities that are available for tenants accessing the Microsoft 365 Defender portal using a GDAP token.

| Resource type | Currently supported |
|:--------------|:-----------|
| Microsoft 365 Defender features | All Microsoft 365 Defender features (as listed in the documentation above): Incidents, Advanced hunting, Action Center, Threat Analytics, Connection of the following security workloads into Microsoft 365 Defender: Microsoft Defender for Endpoint, Microsoft Defender for Identity, Microsoft Defender for Cloud Apps |
| Microsoft Defender for Endpoint features | All Microsoft Defender for Endpoint features listed in the documentation above, see details per P1 / SMB SKU in the [table](#supported-mde-features-in-microsoft-365-defender-portal-per-sku) below. |
| Microsoft Defender for Office 365 | All Microsoft Defender for Office 365 features listed in the documentation above. See details per each license in this table: [Office 365 Security including Microsoft Defender for Office 365 and Exchange Online Protection](/microsoft-365/security/office-365-security/overview?view=o365-worldwide&preserve-view=true)|
| App Governance | Authentication works for GDAP token (App+User token), Authorization policies work according to the user roles as before |

**Supported Azure AD roles in Microsoft 365 Defender portal:**

[Documentation of supported roles in Microsoft 365 Defender portal](/microsoft-365/security/defender/m365d-permissions?view=o365-worldwide&preserve-view=true)

> [!NOTE]
> Not all roles are applicable to all security products. For information about what roles are supported in a specific product, refer to the product documentation.

___

### Supported MDE features in Microsoft 365 Defender portal per SKU

| Endpoint capabilities per SKU | Microsoft Defender for Business | Microsoft Defender for Endpoint Plan 1 | Microsoft Defender for Endpoint Plan 2 |
| - | - | - | - |
| Centralized management | X | X | X |
| Simplified client configuration | X | | |
| Threat and vulnerability management | X | | X |
| Attack surface reduction | X | X | X |
| Next-gen protection | X | X | X |
| Endpoint detection and response | X | | X |
| Automated investigation and response | X | | X |
| Threat hunting and six-month data retention | | | X |
| Threat analytics | X | | X |
| Cross-platform support for Windows, MacOS, iOS, and Android | X | X | X |
| Microsoft threat experts | | | X |
| Partner APIs | X | X | X |
| Microsoft 365 Lighthouse for viewing security incidents across customers | X | | |

___

## Power BI

For the Power BI workload, the following tasks are supported by GDAP.

| Resource type | Currently supported
|:--------------|:-----------
| Administrator tasks | - All menu items under "[Admin portal](/power-bi/admin/service-admin-portal)" except "Azure connections" </br>

**Supported Azure AD Roles in scope:**

- Fabric Administrator
- Global Administrator

**Power BI properties out of scope:**

- Not all non-administrator tasks are guaranteed to work
- "Azure connections" under Admin portal

___

## SharePoint

For SharePoint, the following tasks are supported by GDAP.

| Resource type | Currently supported |
|:--------------|:-----------|
| Homepage | Cards render but data may not render |
|Sites Management – Active Sites | Create sites: Team site, Communication site, Assign/change site owner, Assign sensitivity label to site (if configured in Azure AD) during site creation, Change sensitivity label of site, Assign privacy settings to site (if not predefined with a sensitivity label), Add/Remove members to a site, Edit site external sharing settings, Edit site name, Edit site URL, View site activity, Edit storage limit, Delete a site, Change built-in views of sites, Export site list to CSV file, Save custom views of sites, Associate site with a Hub, Register site as a Hub |
| Sites Management – Active Sites | Create other sites: Document Center, Enterprise Wiki, Publishing Portal, Content Center |
|Sites Management – Deleted Sites | Restore site, Permanently delete site (except for Microsoft 365 group-connected team sites) |
| Policies – Sharing | Set External Sharing policies for SharePoint and OneDrive for Business, Change "More external sharing settings", Set policies for File and Folder links, Change "Other settings" for sharing |
| Access control | Set/change unmanaged device policy, Set/change idle sessions timeline policies, Set/change network location policy (separate from Azure AD IP policy, Set/change modern authentication policy, Set/change OneDrive access |
| Settings | SharePoint - Home site, SharePoint - Notifications, SharePoint - Pages, SharePoint - Site creation, SharePoint - Site storage limits, OneDrive - Notifications, OneDrive - Retention, OneDrive - Storage limit, OneDrive - Sync |
| PowerShell | To connect a customer tenant as a GDAP admin, use a tenanted authorization endpoint (with the customer's tenant ID) in the `AuthenticanUrl` parameter instead of the default common endpoint.<br>For example, `Connect-SPOService -Url https://contoso-admin.sharepoing.com -AuthenticationUrl https://login.microsoftonline.com/<tenantID>/oauth2/authorize`.

**Roles in scope** include the following:

- SharePoint Administrator
- Global Administrator
- Global Reader

**SharePoint Admin Center properties out of scope** include the following:

- All Classic Admin features/functionality/templates are out of scope and not guaranteed to work correctly
- Note: For any SharePoint Admin Center supported GDAP roles, partners cannot edit files and permissions on files and folders in the customer SharePoint site. This was a security risk to customers and has been addressed.

___

## Dynamics 365 and Power Platform

For Power platform and Dynamics 365 customer engagement applications (Sales, Service), the following tasks are supported by GDAP.

| Resource type | Currently supported |
|:--------------|:-----------|
| Administrator tasks | - All menu items in Power Platform admin center </br>

**Supported Azure AD Roles in scope** include the following:

- Power platform administrator
- Global administrator
- Helpdesk Administrator (for Help + Support)
- Service Support Administrator (for Help + Support)

**Properties out of scope**:

- None

___

## Dynamics 365 Business Central

For Dynamics 365 Business Central, the following tasks are supported by GDAP.

| Resource type | Currently supported |
|:--------------|:--------------------|
| Administrator tasks | All tasks`*` |

`*` Some tasks require permissions assigned to the administrator user within the Dynamics 365 Business Central environment. Refer to the available documentation.

**Supported Azure AD Roles in scope** include the following:

- Dynamics 365 administrator
- Global administrator
- Help Desk administrator

**Properties out of scope**:

- None

___

## Dynamics Lifecycle Services

For Dynamics Lifecycle Services, the following tasks are supported by GDAP.

| Resource type | Currently supported |
|:--------------|:--------------------|
| Administrator tasks | All tasks |

**Supported Azure AD Roles in scope** include the following:

- Dynamics 365 administrator
- Global administrator

**Properties out of scope**:

- None

___

## Intune (Endpoint Manager)

Supported Azure AD Roles in scope:

- Intune Administrator
- Global Administrator
- Global Reader
- Reports Reader
- Security reader
- Compliance Administrator
- Security Administrator

To check access level for the above roles, see the [Intune RBAC documentation](/mem/intune/fundamentals/role-based-access-control).

Support for Intune doesn't include use of GDAP when enrolling servers for Microsoft Tunnel, or for configuring or installing any of the connectors for Intune. Examples of Intune connectors include but aren't limited to the *Intune Connector for Active Directory*, *Mobile threat defense connector*, and the *Microsoft Defender for Endpoint connector*.
___

## Azure portal

:::image type="content" source="./media/gdap/gdap-azure-portal.png" alt-text="Diagram showing the relationship between partner and customer using GDAP.":::

Azure AD roles in scope:

- Any Azure AD role such as [Directory Readers](/azure/active-directory/roles/permissions-reference#directory-readers) (least privileged role) for accessing Azure subscription as owner

GDAP role guidance:

- Partner and customer must have **Reseller** relationship
- Partner must create security group *(e.g Azure Managers)* for managing Azure **and nest it under Admin Agents** for per customer access partitioning as recommended best practice.
- When partner purchases Azure plan for the customer, Azure subscription is provisioned and Admin Agents group is assigned [Azure RBAC](/azure/role-based-access-control/overview) as [owner](/azure/role-based-access-control/built-in-roles#owner) on Azure subscription
- Since Azure Managers security group is member of Admin Agents group, users that are members of Azure Managers become the Azure subscription RBAC owner
- To access Azure subscription as owner for customer, any Azure AD role such as [Directory Readers](/azure/active-directory/roles/permissions-reference#directory-readers) (least privileged role) must be assigned to Azure Managers security group

___

## Alternative Azure GDAP guidance (without using Admin Agent)

**Prerequisites:**

- Partner and customer have a **Reseller** relationship.
- Partner has created a security group for managing Azure **and nested it under the HelpDeskAgents** group per customer access partitioning as is a recommended best practice.
- Partner has purchased an Azure plan for the customer, the Azure subscription is provisioned and the partner assigned the Admin Agents group [Azure RBAC](/azure/role-based-access-control/overview) as [owner](/azure/role-based-access-control/built-in-roles#owner) on the Azure subscription but no RBAC role assignment has been made for **Helpdesk Agents**.

**Partner admin steps:**

The partner admin on the subscription runs the following scripts using PowerShell to create Helpdesk FPO on the Azure subscription.

- Connect to the partner tenant to get the `object ID` of the HelpDeskAgents group.

   ```powershell
   Connect-AzAccount -Tenant "Partner tenant"
   # Get Object ID of HelpDeskAgents group
   Get-AzADGroup -DisplayName HelpDeskAgents
   ```

- Ensure that your customer has:
  - The role of **owner** or **user access administrator**
  - Permissions to create role assignments at the subscription level

**Customer steps:**

To complete the process, your customer must perform the following steps, using either PowerShell or Azure CLI.

1. If using PowerShell, the customer needs to update the `Az.Resources` module.

   ```powershell
   Update-Module Az.Resources
   ```

2. Connect to the tenant in which the CSP subscription exists.

   ```powershell
   Connect-AzAccount -TenantID "<Customer tenant>"
   ```

   ```azurecli
   az login --tenant <Customer tenant>
   ```

3. Connect to the subscription.

   > [!NOTE]
   > This is **only** applicable if the user has role assignment permissions over multiple subscriptions in the tenant.

   ```powershell
   Set-AzContext -SubscriptionID <"CSP Subscription ID">
   ```

   ```azurecli
   az account set --subscription <CSP Subscription ID>
   ```

4. Create the role assignment.

   ```powershell
   New-AzRoleAssignment -ObjectID "<Object ID of the HelpDeskAgents group from step above>" -RoleDefinitionName "Owner" -Scope "/subscriptions/'<CSP subscription ID>'"
   ```

   ```azurecli
   az role assignment create --role "Owner" --assignee-object-id <Object ID of the HelpDeskAgents group from step above> --scope "/subscriptions/<CSP Subscription Id>"
   ```

___

## Visual Studio

:::image type="content" source="./media/gdap/gdap-visual-studio.png" alt-text="Diagram showing the relationship between the Visual Studio managers group and the customer through GDAP.":::

Azure AD Roles in scope:

- Any Azure AD role such as [Directory Readers](/azure/active-directory/roles/permissions-reference#directory-readers) (least privileged role) for accessing Azure subscription as owner

GDAP role guidance to partners:

- Prerequisites:
  - Partner and customer must have a **Reseller** relationship
  - Partner must purchase **Azure subscription** for the customer
- Partner must create security group (for example, *Visual studio managers*) for purchasing and managing Visual Studio subscriptions and nest it under Admin Agents for per customer access partitioning as recommended best practice.
- GDAP role for purchasing and managing Visual studio is **same** as Azure GDAP.
- *Visual studio managers* Security Group must be assigned any Azure AD role such as [Directory Readers](/azure/active-directory/roles/permissions-reference#directory-readers) (least privileged role) for accessing Azure subscription as owner
- Users part of *Visual studio managers* Security Group will be able to **purchase** **Visual studio subscription on Marketplace** <https://marketplace.visualstudio.com> (due to nested member of Admin Agents users will have access to Azure subscription)
- Users who are part of the Visual Studio managers security group can **change quantity** of Visual Studio subscriptions

:::image type="content" source="./media/gdap/gdap-visual-studio-subscriptions.png" alt-text="Screenshot showing available Visual Studio subscriptions.":::

- Users who are part of the Visual Studio managers security group can **cancel** Visual Studio subscription (by changing quantity to zero)
- Users who are part of the Visual Studio managers security group can **add subscriber** to manage [Visual Studio subscriptions](https://manage.visualstudio.com) (for example, browse customer directory and add Visual Studio role assignment as subscriber)

Visual Studio properties out of scope:

- None

___

## Why don't I see some DAP AOBO links in GDAP Service management page?

| DAP AOBO links | Reason why it's missing in GDAP Service Management page |
|:---------------|:---------------------------------------------------------
| Microsoft 365 Planner </br> <https://portal.office.com/> | This is a duplicate of the [Microsoft 365](https://portal.office.com/) AOBO link that already exists. |
| Sway </br> <https://portal.office.com/> | This is a duplicate of the [Microsoft 365](https://portal.office.com/) AOBO link that already exists. |
| Windows 10 </br> <https://portal.office.com/> | This is a duplicate of the [Microsoft 365](https://portal.office.com/) AOBO link that already exists. |
| Cloud App Security </br> <https://portal.cloudappsecurity.com/> | [Microsoft Defender for Cloud Apps](https://portal.cloudappsecurity.com/) will be retired. This portal will merge into [Microsoft 365 Defender](https://security.microsoft.com), which supports GDAP. |
| Azure IoT Central </br> <https://apps.azureiotcentral.com/> | Currently not supported. Out of scope for GDAP. |
| Windows Defender Advanced Threat Protection </br> <https://securitycenter.windows.com> | Windows Defender Advanced Threat Protection will be retired. Partners are advised to move to [Microsoft 365 Defender](https://security.microsoft.com), which supports GDAP. |

## Next steps

- [Assign Azure AD roles](gdap-assign-azure-ad-roles.md)
- [Least-privileged roles by task](gdap-least-privileged-roles-by-task.md)
- [GDAP FAQ](gdap-faq.md)
