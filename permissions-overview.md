---
title: Assign roles and permissions to users
ms.topic: article
ms.date: 11/22/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-account
description: Learn about roles, permissions, and workspace access in Partner Center. Learn which roles are best for your company's users who manage commercial transactions, referrals, incentives, or Microsoft AI Cloud Partner Program memberships - Account settings workspace.
author: sharath-satish-msft
ms.author: shsatish
---

# Assign roles, permissions, and workspace access to users

**Appropriate roles**: Account admin | Global admin | User management admin

You determine the access your users have to Partner Center by the roles you assign to them. Each program has roles specific to the business it relates to. For example, if your business is a Cloud Solution Provider (CSP) business, your users need roles specific to the CSP program, not just standard Microsoft Azure Active Directory (Azure AD) tenant management roles such as global admin.

## Azure AD tenant roles and non-Azure AD roles

- *[Azure AD tenant roles](#manage-csp-commercial-transactions-in-partner-center-azure-ad-and-csp-roles)* include global admin, user admin, and CSP roles.
- *Non-Azure-AD roles* are roles that don't manage the tenant. They include business profile admin, referral admin, incentive admin, incentive user, and Microsoft AI Cloud Partner Program (formerly the Microsoft Partner Network) partner admin.

## User roles, permissions, and workspace access

Nine tables in this article list Partner Center user roles, the permissions granted by those roles, and the workspaces those roles have access to.

The tables are:

- [Assign roles, permissions, and workspace access to users](#assign-roles-permissions-and-workspace-access-to-users)
  - [Azure AD tenant roles and non-Azure AD roles](#azure-ad-tenant-roles-and-non-azure-ad-roles)
  - [User roles, permissions, and workspace access](#user-roles-permissions-and-workspace-access)
  - [Manage CSP commercial transactions in Partner Center (Azure AD and CSP roles)](#manage-csp-commercial-transactions-in-partner-center-azure-ad-and-csp-roles)
  - [Manage Microsoft AI Cloud Partner Program membership and your company](#manage-microsoft-ai-cloud-partner-program-membership-and-your-company)
  - [Manage referrals](#manage-referrals)
    - [Scope of referral roles](#scope-of-referral-roles)
  - [Manage incentives](#manage-incentives)
  - [View Partner Center Insights data](#view-partner-center-insights-data)
    - [Control Panel Vendor](#control-panel-vendor)
    - [Guest user](#guest-user)
    - [Help + support](#help--support)
  - [Next steps](#next-steps)

This article doesn't describe all roles, such as [roles in the Microsoft marketplace](/azure/marketplace/user-roles) and [roles with privileges for various GDAP capabilities](gdap-least-privileged-roles-by-task.md).

> [!NOTE]
> The Owner role is assigned to the user who enrolled in the program. An existing owner with AAD account can assign owner permissions to other AAD users. If the current Owner doesn't have an AAD account, then [create a support ticket](report-problems-with-partner-center.md) to change the owner.

> [!NOTE]
> Role assignments or changes done in Azure portal can take up to one hour to appear in Partner Center.

> [!NOTE]
> Editing user permissions is not supported in national clouds, including Microsoft Cloud for US Government and Microsoft Azure and Microsoft 365 operated by 21Vianet in China.

## Manage CSP commercial transactions in Partner Center (Azure AD and CSP roles)

This table lists the Azure AD and CSP roles you can assign to users. It also shows the workspaces and other access granted with those user roles.

| Workspace     | Level of access                         | User Role       | Learn more                                                    |
|-------------------|-----------------------------------------------------------------|------------------------|------------------------------------------------------------------------------------------------------------------|
| Customers     | Customer management                       | Admin agent      | [Connect with your customers](connect-with-your-customers.md)                                           |
| Customers     | View all partner profiles                    | User management admin |                                                          |
| Customers     | Request a relationship with a customer             | Sales agent **\***      |                                                          |
| Customers     | View the customer agreement                   | Sales agent **\***     |                                                          |
| Pricing      | View agreements, price lists, and offers            | Global admin      |                                                          |
| Pricing      | View pricing and offers                     | Admin agent      |                                                          |
| Pricing      | View pricing and offers                     | Sales agent **\***      |                                                          |
| Account settings | Can access all Microsoft account/services with full privileges | Global admin      | [Manage your Partner Center account](partner-center-account-setup.md)                                        |
| Account settings | View, create, and manage all partner users             | Global admin      |  [Create user accounts and assign roles.](create-user-accounts-and-set-permissions.md) <br> Only a Global admin can [reset a password](reset-a-user-password.md) for a global admin.                   |
| Account settings | Add device list to the Partner Center              | Admin agent      |                                                          |
| Account settings | Create and apply profiles to devices              | Admin agent      |                                                          |
| Account settings | Subscription management                     | Admin agent      |                                                          |
| Account settings | Cancel Azure subscription                     | Global admin      |                                                          |
| Account settings | Request delegated administrator privileges           | Admin agent      |                                                          |
| Account settings | Administer on behalf of a customer               | Admin agent      |                                                          |
| Account settings | Register a value-added reseller                 | Admin agent      |                                                          |
| Account settings | Add device list to the Partner Center              | Sales agent **\***      |                                                          |
| Account settings | Subscription management                     | Sales agent **\***      |                                                          |
| Account settings | Enroll a value-added reseller                  | Sales agent **\***      |                                                          |
| Account settings | View my learning profile                         | Default user      |[Link or unlink a Microsoft Certification profile ID (MCID) to a PartnerID](ms-learn-associate.md)|
| Account settings | View my profile                         | Default user      |[Reset your password](reset-my-pasword.md) |
| Billing      | View, create, and manage billing, invoices, and recon files   | Global admin      |                                                          |
| Billing      | Billing                             | Admin agent      |                                                          |
| Billing      |View, create, and manage billing, invoices, and recon files  | Billing admin     | [Read your bill](./billing.md)                                                  |
| Billing      | View pricing                          | Billing admin     |                                                          |
| Billing      | Manage subscriptions and billing issues on behalf of customers | Helpdesk agent     |                                                          |
| Billing      | Customer management                       | Sales agent **\***      | [Provide billing support for your customers and help answer their billing questions](provide-billing-support.md)                |
| Referrals     | Manage customer leads                      | Sales agent **\***      |                                                          |

> [!NOTE]
> \* The *Sales agent* role is visible in Partner Center user management only for tier 1 and tier 2 indirect providers.

*[Return to top](#user-roles-permissions-and-workspace-access)*

## Manage Microsoft AI Cloud Partner Program membership and your company

This table lists the roles you can assign to users so they can view and manage memberships, competencies, programs, and benefits in the Microsoft AI Cloud Partner Program. It also shows the workspace access granted with those user roles.

| Workspace     | Level of access                         | User Role       | Learn more                                              |
|-------------------|-----------------------------------------------------------------|------------------------|-------------------------------------------------------------------------------------------------------|
| Membership    | View, create, and manage partner service requests       | MPN Partner Admin   |                                                    |
| Membership    | View user details and their skills data            | MPN Partner Admin   | [Skills report in Partner Center](./mpn-benefits-map-competency-learning-option-enroll.md)                  |
| Membership    | View Solutions partner designations                      | MPN Partner Admin   | [Introduction to Solutions partner designations](introduction-to-pcs.md)|
| Membership    | View and purchase Microsoft AI Cloud Partner Program offers                 | MPN Partner Admin   | [Buy or renew a Microsoft Action Pack subscription or silver and gold competencies](mpn-get-action-pack.md)           |
| Membership    | View Microsoft AI Cloud Partner Program offers order history and invoices          | MPN Partner Admin   |                                                     |
| Membership    | View partner contribution indicator data           | MPN Partner Admin   |                                                     |
| Membership    | Can work in the Voucher Validation tool            | MPN Partner Admin   |                                                     |
| Benefits     | View and manage benefits                   | MPN Partner Admin   |                                                     |
| Benefits     | View, create, and manage users                | User management admin | [Manage your Microsoft AI Cloud Partner Program membership benefits and offers in Partner Center](manage-your-partner-network-benefits.md)        |
| Account settings | Add locations                          | Account admin     | [Manage locations](manage-locations.md)                                           |
| Account settings | Manage profiles related to the accounts you're the admin for   | Account admin     |                                                     |
| Account settings | Assign roles for users in tenant to non-Azure-AD roles    | Account admin     |                                                     |
| Account settings | View legal, company, business, and Microsoft AI Cloud Partner Program profiles        | MPN Partner Admin   |  [Verify your company profile](update-your-partner-profile.md)                    |
| Account settings | View other user roles within company, but can't assign roles | MPN Partner Admin   |                                                     |
| Account settings | Enroll locations into programs                | Account admin     |
| Account settings | Export learning users                | MPN Partner admin     |                                                     |
| Insights     | View customer data analytics                 | MPN Partner Admin   |                                                     |

*[Return to top](#user-roles-permissions-and-workspace-access)*

## Manage referrals

This table lists roles you can assign to users so they can create, manage, edit, assign, register, or view in the *Referrals* workspace. (See [Scope of referral roles](#scope-of-referral-roles) in the next table for the scope of deals that Referrals users can make.)

| Workspace | Level of access                                                          | User Role        | Learn more          |
|------------|-----------------------------------------------------------------------------------------------------------------------------------|-------------------------|-------------------------------|
| Referrals | Create and manage everything under Referrals tab in Partner Center                                | Referrals admin     | [Manage Co-sell opportunities](manage-co-sell-opportunities.md) |
| Referrals | Can view and edit all the co-sell opportunities and leads                                     | Referrals admin     |                 |
| Referrals | Can assign team members for a deal                                                | Referrals admin     |                 |
| Referrals | Can view and edit business profiles                                                | Referrals admin     |                 |
| Referrals | Can view and register deals for opportunities that are marked as won and eligible for deal registration              | Referrals admin     |                 |
| Referrals | Create and manage co-sell opportunities only if they're a part of the team                            | Referrals user     | [Manage Co-sell opportunities](manage-co-sell-opportunities.md) |
| Referrals | Can create co-sell opportunities for the locations where they're assigned the role.                       | Referrals user     |                 |
| Referrals | Can view and register deals for opportunities that are marked as won and eligible for deal registration if they're team member. | Referrals user     |                 |
| Referrals | Create and manage business profiles                                                | Business profile admin | [Manage business profiles](create-a-marketing-profile.md)   |
| Referrals | Can publish and edit Solutions                                                     | Co-Sell Solution admin | [Configure Co-Sell solution](co-sell-configure.md) |

If the user is an admin for referrals, they have full access to that workspace. If the user only needs access to a specific location, then the user role needs to be manually added to that location. This ensures the user doesn't have access to the whole account but rather only to a location.

*[Return to top](#user-roles-permissions-and-workspace-access)*

### Scope of referral roles

This table shows the scope of deals that users with *[Referrals](#manage-referrals)* privileges can make.

| Workspace | Scope         | What you can do                                                       |
|------------|------------------------|-----------------------------------------------------------------------------------------------------------------------------|
| Referrals | Entire company     | Both admins and users have access to create deals for any location in their company.                     |
| Referrals |            | Referral admin has access to view and edit all the deals.                                  |
| Referrals |            | Referral users have access to view and edit all the deals only if they're a part of the team.                |
| Referrals | One or more locations | Both admins and users have access to create deals for the assigned location in their company.                |
| Referrals |            | Referral admin has access to view and edit all the deals belonging to the assigned locations.                |
| Referrals |            | Referrals users have access to view and edit all the deals belonging to the assigned locations if they're part of the team.|

*[Return to top](#user-roles-permissions-and-workspace-access)*

## Manage incentives

This table lists roles you can assign to users so they can initiate, manage, edit, dispute, or view in the *Incentives* workspace.

| Workspace  | Level of access                     | User Role     | Learn more                          |
|-------------|---------------------------------------------------------|-------------------|--------------------------------------------------------------|
| Incentives | Initiates and manages incentives           | Incentives admin | [Use these resources to help you get started with incentives](incentives-get-started-intro.md) |
| Incentives | Can view and edit all aspects of incentives programs | Incentives admin |                                |
| Incentives | Can view and edit bank and tax details        | Incentives admin |                                |
| Incentives | View rebate and co-op earnings            | Incentives admin |                                |
| Incentives | Dispute incentives payments              | Incentives admin |                                |
| Incentives | Can view incentives programs             | Incentives user  |                                |
| Incentives | Can view and initiate incentives claims        | Incentives user  |                                |
| Incentives | View rebate and co-op earnings            | Incentives user  |                                |

If the user is an admin for incentives, they have full access to that workspace. If the user only needs access to a specific location, then the user role needs to be manually added to that location. This ensures the user doesn't have access to the whole account, but rather only to a location.

*[Return to top](#user-roles-permissions-and-workspace-access)*

## View Partner Center Insights data

This table lists roles you can assign to users so they can access, view, and create data about your customers and their purchases in the *Insights* workspace.

| Workspace | Level of access                                                                          | User Role        | Learn more                            |
|------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------|------------------------------------------------------------------|
| Insights  |View customer data analytics                                                                   | MPN Partner Admin    |                                  |
| Insights  | Access to all reporting datasets, create partner support tickets, view partner support tickets you create                             | Executive report viewer | [Overview dashboard reports available in Partner Center Insights](insights-overview-report.md)|
| Insights  | Access to data reports with exception of revenue and customer and employee personal data, create partner support tickets, view partner support tickets you create | Report viewer      |                                  |

*[Return to top](#user-roles-permissions-and-workspace-access)*

### Control Panel Vendor

This table shows the roles with access to Control Panel Vendor (CPV) capabilities.

A [Control Panel Vendor](enroll-as-cpv.md) (CPV) is an independent software vendor that develops applications for use by CSP) partners to enable them to integrate their systems with Partner Center APIs. A Control Panel vendor isn't a CSP Partner with direct access to the Partner Center or Partner Center APIs.

| Workspace     | Level of access                            | User Role   | Learn more                                            |
|-------------------|------------------------------------------------------------------------|----------------|--------------------------------------------------------------------------------------------------|
| Account settings | View and manage your CPV profile        | Global admin  | [Enroll as a Control Panel Vendor to help integrate CSP partner systems with Partner Center APIs](enroll-as-cpv.md) |
| Account settings | View and manage any of your users who need access to CPV capabilities |  Global admin |                                                  |

*[Return to top](#user-roles-permissions-and-workspace-access)*

### Guest user

A user can be added as a guest on the Azure AD tenant. Their access to Partner Center capabilities depends on the role they're assigned by the admin on the Azure AD tenant.

| Guest user  | User Roles      |
|----------------------|:------------------------|
|           | MPN Partner Admin    |
|           | Business profile admin |
|           | Referrals admin     |

> [!NOTE]
> To access, view, or manage an account, a guest user need to be assigned an admin role. For a Microsoft AI Cloud Partner Program account, a guest user must have the Global admin or MPN Partner Admin role. (Otherwise, they will see the message, *"Access denied. Please contact your company's global admin and ask them to grant you the appropriate access permissions."*)

*[Return to top](#user-roles-permissions-and-workspace-access)*

### Help + support

This table lists roles you can assign to users, and the level of help and support that they can create, view, access, or provide.

| Workspace     | Level of access                                     | User Role                                                                                                 | Learn more                                           |
|-------------------|-----------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|
| Help + support  | Create support tickets for Partner Center.<br> View partner support tickets that you create. | Global admin, Account admin, Helpdesk agent, MPN Partner Admin, Incentives admin, Incentives user, Admin agent, User management admin, Billing admin, Referrals admin, Referrals user, Business profile admin, Sales agent (The *Sales agent* role is visible in Partner Center user management only for tier 1 and tier 2 indirect providers.)   |                                                |
| Customers  | Service health and service requests for customers                   | Admin agent                                                                                                |                                                |
| Customers  | Search for and view a customer                            | Helpdesk agent                                                                                              |  |
| Customers  | Edit customer details                                 | Helpdesk agent                                                                                              |                                                |
| Customers  | Help resolve customer issues with billing or subscription management         | Helpdesk agent                                                                                              |                                                |
| Customers  | Request support on behalf of customers                        | Helpdesk agent                                                                                              |                                                |

*[Return to top](#user-roles-permissions-and-workspace-access)*

## Next steps

Read the following articles for more information about roles and permissions.

- [Assign user roles and permissions for Microsoft marketplace](/azure/marketplace/user-roles)
- [Set roles or custom permissions for account users for Windows and Xbox](/windows/uwp/publish/set-custom-permissions-for-account-users)
- [Create user accounts and assign roles and permissions](create-user-accounts-and-set-permissions.md)
- [Verify your account information when you enroll in a new Partner Center program](verification-responses.md)
