---
title: GDAP role guidance 
ms.topic: article
ms.date: 2/01/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Guidance about which least-privileged roles can be used for GDAP.
author: kvamseek
ms.author: vamseekk
---

# GDAP role guidance

**Appropriate roles**: Admin agent

This article gives guidance about which least-privileged Microsoft Azure Active Directory (Azure AD) built-in role can be used for each granular delegated admin privileges (GDAP) capability. For example, to submit support requests on behalf of a customer requires the [Service support administrator](/azure/active-directory/roles/permissions-reference#service-support-administrator) role, which is the least-privileged Azure AD built-in role on your customer's tenant.

## Creating support requests

Indirect resellers can't create support requests for Azure. Instead, they must work with their indirect providers.

| To create a support request for: | Direct-bill partners and indirect providers must have the following least privileged role:
|--|--|
| **Microsoft 365 in the Microsoft 365 admin center** | GDAP role assignment to a role that has _Microsoft.office365.supportTickets/allEntities/allTasks_ permissions, such as [Service support administrator](/azure/active-directory/roles/permissions-reference#service-support-administrator) |
| **Dynamics 365 in Power Platform Admin Center** | GDAP role assignment to a role that has _Microsoft.office365.supportTickets/allEntities/allTasks_ permissions, such as [Service support administrator](/azure/active-directory/roles/permissions-reference#service-support-administrator) |
| **Azure subscription resource in the Azure portal** | **Prerequisite**: To create requests on behalf of customers using a customer's Azure subscription, partners must have a reseller relationship with the customer as explained in [CSP regional authorization](regional-authorization-overview.md). For more information, see [Steps to setup Azure GDAP](gdap-supported-workloads.md#azure-portal). </br></br> Any GDAP assignment to an Azure AD role, such as [Directory readers](/azure/active-directory/roles/permissions-reference#directory-readers), <br><br> **- AND -** <br> <br> Azure role-based access control (RBAC) role assignment to a role with _Microsoft.Support/supportTickets/write_ permissions, such as [Support request contributor](/azure/role-based-access-control/built-in-roles#support-request-contributor) |
| **Azure AD in the Azure portal** | **Alternative 1: If a customer doesn't have Azure AD P1 or P2** </br></br> **Prerequisite**: To create requests on behalf of customers using a customer's Azure subscription, partners must have a reseller relationship with the customer per [CSP regional authorization](regional-authorization-overview.md). For more information, see [Steps to setup Azure GDAP](gdap-supported-workloads.md#azure-portal). </br></br>Any GDAP assignment to an  Azure AD role, such as [Directory readers](/azure/active-directory/roles/permissions-reference#directory-readers), <br><br> **- AND -** <br> <br> Azure RBAC role assignment to a role with _Microsoft.Support/supportTickets/write_ permissions, such as [Support request contributor](/azure/role-based-access-control/built-in-roles#support-request-contributor) </br> </br> **Alternative 2: If customer has Azure AD P1 or P2** Any GDAP assignment to an  Azure AD role that has: _microsoft.azure.supportTickets/allEntities/allTasks_ permissions, such as [Service support administrator](/azure/active-directory/roles/permissions-reference#service-support-administrator) |

## GDAP roles by partner types

### Indirect providers

The following roles are recommended for indirect providers to transact and manage:

- New customer tenant creation
- Reseller relationship setup
- Purchase
- Subscription management
- Upgrades
- Conversions
- Customer user creation and license assignment
- Customer service requests (requests creation on behalf of customer)

| **Role**                                | **Description**                          |
|----------------------------------------|------------------------------------------|
| **Reader roles**:                           |                                          |
| [Directory readers](/azure/active-directory/roles/permissions-reference#directory-readers) | Can read basic directory information. Commonly used to grant directory read access to applications and guests |
| [Directory writers](/azure/active-directory/roles/permissions-reference#directory-writers) | Can read and write basic directory information. For granting access to applications, not intended for users. |
| [Global reader](/azure/active-directory/roles/permissions-reference#global-reader)         | Can read everything that a Global administrator can, but can't update anything   |
| **User management and license management**:    |          |
| [User administrator](/azure/active-directory/roles/permissions-reference#user-administrator)      | Can manage all aspects of users and groups, including resetting passwords for limited admins                  |
| [License administrator](/azure/active-directory/roles/permissions-reference#license-administrator)                                 | Can manage product licenses on users and groups                                                               |
| [Service support administrator](/azure/active-directory/roles/permissions-reference#service-support-administrator)                       | Can read service health information and manage support requests                                                |
| **Help Desk**:                         |                     |
| [Help Desk administrator](/azure/active-directory/roles/permissions-reference#helpdesk-administrator)                                 | Can reset passwords for non-administrators and Help Desk administrators                                        |

### Direct-bill partners, indirect resellers, and advisors

The following roles are recommended for indirect resellers, advisors, and direct-bill partners who also play the role of MSPs. They're all categorized as specialized managed service providers (MSPs) who completely manage customer's environment as outsourced IT department. This section is categorized roles required by tasks and functions.

#### Typical tasks of a tier-1 technician in managed services

| **Role**      | **Task**      | **Function**    |
|---------------|---------------|-----------------|
| Service support administrator   | Submit support requests on behalf of the customer.     | Help Desk creates and manages support requests.     |
| Security reader   | View security-related policies across Microsoft 365 services.   | Help Desk collects discovery on customer tenant to troubleshoot or update security and compliance portal policies, such as data loss prevention policies. |
| Intune administrator    | Can manage all aspects of the Intune product.     | Help Desk handles customer device enrollment and troubleshooting.                                                                                         |
| SharePoint administrator    | Can manage all aspects of the SharePoint service.        | Help Desk manages SharePoint site permissions.                                                                                                            |
| Teams communications support specialist | Can manage the Microsoft Teams service.         | Help Desk troubleshoots call quality issues.                                                                                                              |
| Help Desk administrator                  | Can reset passwords for non-administrators and these admins: Directory Readers Guest Inviter Help Desk administrator Message Center Reader Password administrator Reports Reader.       | Help Desk resets passwords.               |
| Desktop analytics administrator         | Can access and manage desktop management tools and services.     | Help Desk can manage the desktop analytics service by viewing asset inventory and reading standard properties of authorization policies.                  |
| Authentication administrator            | Has access to view, set, and reset authentication method information for any non-admin user.   | Help Desk can access to view, set, and reset authentication method information for any non-admin user (for example, MFA and conditional access).                      |
| Exchange administrator                  | Users with this role have global permissions within Microsoft Exchange Online when the service is present. Also has the ability to create and manage all Microsoft 365 groups, manage support requests, and monitor service health; can send OBO and manage inboxes.       | Help Desk manages shared mailboxes, helps solve mailbox quota issues, and creates and manages transport rules.    |
| License administrator                   | Can assign, remove, and update license assignments.   | During troubleshooting, Help Desk assesses and remediates if there's a licensing issue with the support request.                                       |
| User administrator                      | Can manage all aspects of users and groups, including resetting passwords for limited admins; can block user sign-in.     | Help Desk manages all aspects of users and groups, including resetting passwords for limited admins and blocking a former customer employee's access to Microsoft 365 services.                                                      |
| Groups administrator                    | Members of this role can create/manage groups, create/manage groups settings like naming and expiration policies, and view groups activity and audit reports.     | Help Desk adds owners to groups and adds members to groups.   |
| Directory reader                        | Users in this role can read basic directory information.  | Help Desk can read basic directory information as part of troubleshooting.                                                                                |
| Message center reader                   | Can read messages and updates for their organization in Office 365 Message Center only.     | Help Desk reads Message Center to troubleshoot support issues.    |
| Printer administration                  | Users with this role can register printers and manage all aspects of all printer configurations in the Microsoft Universal Print solution, including the Universal Print Connector settings. They can consent to all delegated print permission requests. Printer administrators also have access to print reports. | Help Desk would manage printer configurations and troubleshoot printer issues.      |
| Guest inviter                           | Users in this role can manage Azure Active Directory B2B guest user invitations.           | Help Desk can invite guest users independent of the _Members can invite guests_ setting.    |

## Least-privileged role by task

The following table displays tasks within each GDAP capability, along with the least-privileged role required to perform each task.

| GDAP capability | Task | Least-privileged role
|:-----|:-----|:---------------------
| [Support](/azure/active-directory/roles/delegate-by-task#support) |Submit support ticket | [Service support administrator](/azure/active-directory/roles/permissions-reference#service-support-administrator)
| [Users](/azure/active-directory/roles/delegate-by-task#users) |Add user to directory role | [Privileged role administrator](/azure/active-directory/roles/permissions-reference#privileged-role-administrator)
| |Add user to group | [User administrator](/azure/active-directory/roles/permissions-reference#user-administrator)
| |Assign license | [License administrator](/azure/active-directory/roles/permissions-reference#license-administrator)
| |Create guest user | [Guest inviter](/azure/active-directory/roles/permissions-reference#guest-inviter)
| |Reset guest user invitation | [User administrator](/azure/active-directory/roles/permissions-reference#user-administrator)
| |Create user |[User administrator](/azure/active-directory/roles/permissions-reference#user-administrator)
| |Delete user |[User administrator](/azure/active-directory/roles/permissions-reference#user-administrator)
| |Invalidate refresh tokens of limited admin |[User administrator](/azure/active-directory/roles/permissions-reference#user-administrator)
| |Invalidate refresh tokens of nonadmin |[Password administrator](/azure/active-directory/roles/permissions-reference#password-administrator)
| |Invalidate refresh tokens of privileged admin |[Privileged authentication administrator](/azure/active-directory/roles/permissions-reference#privileged-authentication-administrator)
| |Read basic configuration |[Default user role](/azure/active-directory/fundamentals/users-default-permissions)
| |Reset password for limited admin |[User administrator](/azure/active-directory/roles/permissions-reference#user-administrator)
| |Reset password for nonadmin |[Password administrator](/azure/active-directory/roles/permissions-reference#password-administrator)
| |Reset password for privileged admin |[Privileged authentication administrator](/azure/active-directory/roles/permissions-reference#privileged-authentication-administrator)
| |Revoke license |[License administrator](/azure/active-directory/roles/permissions-reference#license-administrator)
| |Update all properties except user principal name | [User administrator](/azure/active-directory/roles/permissions-reference#user-administrator)
| |Update user principal name for limited admin | [User administrator](/azure/active-directory/roles/permissions-reference#user-administrator)
| |Update user principal name for privileged admin | [Global administrator](/azure/active-directory/roles/permissions-reference#global-administrator)
| |Update user settings |  [Global administrator](/azure/active-directory/roles/permissions-reference#global-administrator)
| |Update authentication methods | [Authentication administrator](/azure/active-directory/roles/permissions-reference#authentication-administrator)
| [Groups](/azure/active-directory/roles/delegate-by-task#groups) | Assign license| [User administrator](/azure/active-directory/roles/permissions-reference#user-administrator)
| | Create group | [Groups administrator](/azure/active-directory/roles/permissions-reference#groups-administrator)
| | Create, update, or delete access review of a group or app | [User administrator](/azure/active-directory/roles/permissions-reference#user-administrator)
| | Manage group expiration | [User administrator](/azure/active-directory/roles/permissions-reference#user-administrator)
| | Manage group settings | [Groups administrator](/azure/active-directory/roles/permissions-reference#groups-administrator)
| | Read all configuration (except hidden membership) | [Directory readers](/azure/active-directory/roles/permissions-reference#directory-readers)
| | Read hidden membership | Group member
| | Read membership of groups with hidden membership | [Help Desk administrator](/azure/active-directory/roles/permissions-reference#helpdesk-administrator)
| | Revoke license | [License administrator](/azure/active-directory/roles/permissions-reference#license-administrator)
| | Update group membership | [Group owner](/azure/active-directory/fundamentals/users-default-permissions#object-ownership)
| | Update group owners | [Group owner](/azure/active-directory/fundamentals/users-default-permissions#object-ownership)
| | Update group properties | [Group owner](/azure/active-directory/fundamentals/users-default-permissions#object-ownership)
| | Delete group | [Groups administrator](/azure/active-directory/roles/permissions-reference#groups-administrator)
| [Licenses](/azure/active-directory/roles/delegate-by-task#licenses) |Assign license |[License administrator](/azure/active-directory/roles/permissions-reference#license-administrator)
| |Read all configuration |[Directory readers](/azure/active-directory/roles/permissions-reference#directory-readers)
| |Revoke license |[License administrator](/azure/active-directory/roles/permissions-reference#license-administrator)

## Roles by complexity

| Role                                                                                                                                | Simple | Medium | Complex |
|-----------------------------------------------------------------------------------------------------------------------------------------|------------|------------|-------------|
| [Application administrator](/azure/active-directory/roles/permissions-reference#application-administrator)                               |            |            | x           |
| [Application developer](/azure/active-directory/roles/permissions-reference#application-developer)                                       |            |            | x           |
| [Attack payload author](/azure/active-directory/roles/permissions-reference#attack-payload-author)                                        |            |            | x           |
| [Attack Simulation administrator](/azure/active-directory/roles/permissions-reference#attack-simulation-administrator)                        |            |            | x           |
| [Authentication administrator](/azure/active-directory/roles/permissions-reference#authentication-administrator)                           |            |            | x           |
| [Azure AD joined device Local administrator](/azure/active-directory/roles/permissions-reference#azure-ad-joined-device-local-administrator)       |            |            | x           |
| [Azure DevOps administrator](/azure/active-directory/roles/permissions-reference#azure-devops-administrator)                                |            |            | x           |
| [Azure information protection administrator](/azure/active-directory/roles/permissions-reference#azure-information-protection-administrator) |            |            | x           |
| [Billing administrator](/azure/active-directory/roles/permissions-reference#billing-administrator)                                             |            |            | x           |
| [Cloud Application administrator](/azure/active-directory/roles/permissions-reference#cloud-application-administrator)                          |            | x          | x           |
| [Cloud device administrator](/azure/active-directory/roles/permissions-reference#cloud-device-administrator)                                |            |            | x           |
| [Compliance administrator](/azure/active-directory/roles/permissions-reference#compliance-administrator)                                     |            |            | x           |
| [Conditional access administrator](/azure/active-directory/roles/permissions-reference#conditional-access-administrator)                        |            |            | x           |
| [Desktop analytics administrator](/azure/active-directory/roles/permissions-reference#desktop-analytics-administrator)                      |            |            | x           |
| [Directory readers](/azure/active-directory/roles/permissions-reference#directory-readers)                                                   | x          | x          | x           |
| [Directory synchronization accounts](/azure/active-directory/roles/permissions-reference#directory-synchronization-accounts)                    |            |            | x           |
| [Domain name administrator](/azure/active-directory/roles/permissions-reference#domain-name-administrator)                                  |            |            | x           |
| [Dynamics 365 administrator](/azure/active-directory/roles/permissions-reference#dynamics-365-administrator)                                |            | x          | x           |
| [Exchange administrator](/azure/active-directory/roles/permissions-reference#exchange-administrator)                                           |            | x          | x           |
| [Exchange recipient administrator](/azure/active-directory/roles/permissions-reference#exchange-recipient-administrator)                      |            |            | x           |
| [External identity provider administrator](/azure/active-directory/roles/permissions-reference#external-identity-provider-administrator)       |            |            | x           |
| [Global reader](/azure/active-directory/roles/permissions-reference#global-reader)                                                             | x          | x          | x           |
| [Groups administrator](/azure/active-directory/roles/permissions-reference#groups-administrator)                                               |            |            | x           |
| [Guest inviter](/azure/active-directory/roles/permissions-reference#guest-inviter)                                                       |            |            | x           |
| [Helpdesk administrator](/azure/active-directory/roles/permissions-reference#helpdesk-administrator)                                         | x          | x          | x           |
| [Hybrid identify administrator](/azure/active-directory/roles/permissions-reference#hybrid-identity-administrator)                            |            |            | x           |
| [Insights administrator](/azure/active-directory/roles/permissions-reference#insights-administrator)                                         |            |            | x           |
| [Intune administrator](/azure/active-directory/roles/permissions-reference#intune-administrator)                                               |            | x          | x           |
| [License administrator](/azure/active-directory/roles/permissions-reference#license-administrator)                                         |       x     | x          | x           |
| [Message Center privacy Reader](/azure/active-directory/roles/permissions-reference#message-center-privacy-reader)                           |            |            | x           |
| [Message Center reader](/azure/active-directory/roles/permissions-reference#message-center-reader)                                            |            |            | x           |
| [Network administrator](/azure/active-directory/roles/permissions-reference#network-administrator)                                         |            |            | x           |
| [Office apps administrator](/azure/active-directory/roles/permissions-reference#office-apps-administrator)                                |            |            | x           |
| [Password administrator](/azure/active-directory/roles/permissions-reference#password-administrator)                                       |            |            | x           |
| [Power BI administrator](/azure/active-directory/roles/permissions-reference#power-bi-administrator)                                            |            | x          | x           |
| [Power Platform administrator](/azure/active-directory/roles/permissions-reference#power-platform-administrator)                                |            | x          | x           |
| [Printer administrator](/azure/active-directory/roles/permissions-reference#printer-administrator)                                       |            |            | x           |
| [Printer Technician](/azure/active-directory/roles/permissions-reference#printer-technician)                                                 |            |            | x           |
| [Privileged authentication administrator](/azure/active-directory/roles/permissions-reference#privileged-authentication-administrator)      |            |            | x           |
| [Privileged role administrator](/azure/active-directory/roles/permissions-reference#privileged-role-administrator)                          |            |            | x           |
| [Reports reader](/azure/active-directory/roles/permissions-reference#reports-reader)                                                         |            | x          | x           |
| [Search administrator](/azure/active-directory/roles/permissions-reference#search-administrator)                                               |            |            | x           |
| [Search editor](/azure/active-directory/roles/permissions-reference#search-editor)                                                             |            |            | x           |
| [Security administrator](/azure/active-directory/roles/permissions-reference#security-administrator)                                       |            | x          | x           |
| [Security reader](/azure/active-directory/roles/permissions-reference#security-reader)                                                         |            | x          | x           |
| [Service support administrator](/azure/active-directory/roles/permissions-reference#service-support-administrator)                            | x          | x          | x           |
| [SharePoint administrator](/azure/active-directory/roles/permissions-reference#sharepoint-administrator)                                 |            | x          | x           |
| [Skype for Business administrator](/azure/active-directory/roles/permissions-reference#skype-for-business-administrator)                     |            |            | x           |
| [Teams administrator](/azure/active-directory/roles/permissions-reference#teams-administrator)                                             |            | x          | x           |
| [Teams communications administrator](/azure/active-directory/roles/permissions-reference#teams-communications-administrator)                  |            |            | x           |
| [Teams communications support engineer](/azure/active-directory/roles/permissions-reference#teams-communications-support-engineer)             |            |            | x           |
| [Teams communications support specialist](/azure/active-directory/roles/permissions-reference#teams-communications-support-specialist)       |            |            | x           |
| [Teams devices administrator](/azure/active-directory/roles/permissions-reference#teams-devices-administrator)                                  |            |            | x           |
| [User administrator](/azure/active-directory/roles/permissions-reference#user-administrator)                                                 |    x        | x          | x           |
| [Windows 365 administrator](/azure/active-directory/roles/permissions-reference#windows-365-administrator)                                    |            | x          | x           |

## Next steps

- [How to terminate a relationship&mdash;for partners](gdap-partner-terminate.md)
- [How to terminate a relationship&mdash;for customers](gdap-customer-terminate.md)
- [Expiring notifications](gdap-expiring-notifications.md)
- [Activity logs](gdap-activity-logs.md)


