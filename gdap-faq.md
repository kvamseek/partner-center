---
title: GDAP frequently asked questions
ms.topic: article
<<<<<<< HEAD
ms.date: 08/10/2023
=======
ms.date: 10/12/2023
>>>>>>> e8cb93c44b47f75c2045bd14c50b58c3d8e1cc8e
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Granular delegated administrative privileges (GDAP) frequently asked questions
author: kvamseek
ms.author: vamseekk
---

# GDAP frequently asked questions

**Appropriate roles**: All users interested in Partner Center

Granular delegated admin permissions (GDAP) give partners access to their customers' workloads in a way that is more granular and time-bound, which can help to address customer security concerns.

With GDAP, partners can provide more services to customers who may be uncomfortable with the high levels of partner access.

GDAP also helps with customers who have regulatory requirements to provide only least-privileged access to partners.

## Setting up GDAP

###### Who can request a GDAP relationship?

Someone with the *Admin agent* role at a partner organization can [create a GDAP relationship request](gdap-obtain-admin-permissions-to-manage-customer.md).

###### Does a GDAP relationship request expire if the customer doesn't take any action?

Yes. GDAP relationship requests expire after 90 days.

###### How long does a GDAP relationship last?

Partners define the duration of a GDAP relationship. The default duration is two years. (The maximum duration is two years.) However, a partner can update the duration and reduce it to as little as one day.

###### Can I make a GDAP relationship with a customer permanent?

No. Permanent GDAP relationships with customers aren't possible for security reasons. The maximum duration of a GDAP relationship is two years.

###### Can a GDAP relationship with a customer autorenew?

No. A GDAP relationship can't autorenew for security reasons.

###### What do I do when the GDAP relationship with a customer expires? Is there an automatic renewal process?

If the GDAP relationship with your customer expires, [request a GDAP relationship](./gdap-obtain-admin-permissions-to-manage-customer.md) again. There's no automatic renewal process.

You can use [GDAP relationship analytics](./gdap-relationship-analytics.md) to track GDAP relationship expiration dates and prepare for their renewal.

###### How can a customer extend or renew a GDAP relationship?

To extend or renew a GDAP relationship, the customer should ask their partner to [send a GDAP relationship request](./gdap-obtain-admin-permissions-to-manage-customer.md).

###### If a GDAP relationship expires, are the customer's existing subscriptions affected?

No. There's no change to a customer's existing subscriptions when a GDAP relationship expires.

###### How can I continue to administer services for my customers if DAP for inactive customers is removed?

While DAP and GDAP coexist, you can continue to administer services for your customers by establishing a GDAP relationship or by recreating a DAP relationship with them through Partner Center. We recommend establishing a *GDAP* relationship to ensure you have the most secure and least privileged access to your customer's tenant.

When DAP is retired, you'll be required to have a GDAP relationship with any customers for whom you want to administer services.

###### How can a customer reset their password and MFA device if they're locked out of their account and can't accept a GDAP relationship request from a partner?

Refer to [Troubleshoot Azure Active Directory Multi-Factor Authentication issues](/troubleshoot/azure/active-directory/troubleshoot-azure-mfa-issue) and [Can't use Azure AD Multi-Factor Authentication to sign in to cloud services after you lose your phone or the phone number changes](/troubleshoot/azure/active-directory/cannot-use-mfa-signin-lose-phone) for guidance.

###### What roles are required by a partner to reset an admin password and MFA device if a customer admin is locked out of their account and can't accept a GDAP relationship request from a partner?

Partner must request [Privileged authentication administrator](/azure/active-directory/roles/permissions-reference#privileged-authentication-administrator) Azure AD role when creating first GDAP, to be able to reset password and authentication method for a user (admin or nonadmin).
Privileged Authentication Administrator role is part of the roles being set up by MLT (Microsoft Led Tool) and is planned to be available with Default GDAP during Create Customer flow (planned for September).

Partner could have the customer admin try [Reset password](/microsoft-365/admin/add-users/reset-passwords#reset-my-admin-password).
As a precaution, partner must set up SSPR (Self-service password reset) for their customers. Refer to [Let people reset their own passwords](/microsoft-365/admin/add-users/let-users-reset-passwords#steps-let-people-reset-their-own-passwords)

###### Who receives a GDAP relationship termination notification email?

Within a *partner* organization, people with the *Admin agent* role receive a termination notification.

Within a *customer* organization, people with the *Global admin* role receive a termination notification.

###### Can I see when a customer removes GDAP in the activity logs?

Yes. Partners can see when a customer removes GDAP in the Partner Center activity logs.

###### Do I need to create a GDAP relationship with all of my customers?

No. GDAP is an optional capability for partners who want to manage their customer's services in a more granular and time-bound way. You can choose which customers you want to create a GDAP relationship with.

###### If I have multiple customers, do I need to have multiple security groups for those customers?

The answer depends on how you want to manage your customers.

- If you want your partner users to be able to manage all customers, you can put all of your partner users into one security group and that one group can manage all of your customers.

- If you prefer to have various partner users managing various customers, assign those partner users to separate security groups for customer isolation.

###### Can indirect resellers create GDAP relationship requests at Partner Center?

Yes. Indirect resellers (and indirect providers and direct-bill partners) can create GDAP relationship requests at Partner Center.

###### Why can't a partner user with GDAP access a workload as AOBO (Admin On Behalf Of)?

As part of GDAP setup, it's important to ensure that security group(s) created in partner tenant with partner users is selected and desired Azure Active Directory roles are assigned to the security group. Refer [Assign Azure Active Directory roles](gdap-assign-azure-ad-roles.md).

<a name="exclude-csps"></a>
###### What is the recommended next step if the conditional access policy set by the customer blocks all external access including CSP's access (AOBO) to the customer's tenant?

Customers can now exclude CSPs from conditional access policy so that partners can run no consent GDAP bulk migration tool to transition to GDAP without getting blocked.

**Include users**

This list of users typically includes all of the users an organization is targeting in a Conditional Access policy.

The following options are available to include when creating a Conditional Access policy:

- Select users and groups
  - Guest or external users (preview)
    - This selection provides several choices that can be used to target Conditional Access policies to specific guest or external user types and specific tenants containing those types of users. There are several different types of guest or external users that can be selected, and multiple selections can be made:
      - Service provider users, for example a Cloud Solution Provider (CSP)
    - One or more tenants can be specified for the selected user type(s), or you can specify all tenants.

**External partner access**

Conditional Access policies that target external users may interfere with service provider access, for example granular delegated admin privileges. For more information, see [Introduction to granular delegated admin privileges (GDAP)](gdap-introduction.md). For policies that are intended to target service provider tenants, use the **Service provider user** external user type available in the **Guest or external users** selection options.

:::image type="content" source="media/gdap/conditional-access-policy-1.png" alt-text="Screenshot of CA policy UX targeting guest and external user types from specific Azure AD organizations.":::

**Exclude users**

When organizations both include and exclude a user or group, the user or group is excluded from the policy, as an exclude action overrides an include in policy.

The following options are available to exclude when creating a Conditional Access policy:

- Guest or external users
  - This selection provides several choices that can be used to target Conditional Access policies to specific guest or external user types and specific tenants containing those types of users. There are [several different types of guest or external users that can be selected](/azure/active-directory/external-identities/authentication-conditional-access#conditional-access-for-external-users), and multiple selections can be made:
    - Service provider users, for example a Cloud Solution Provider (CSP)
  - One or more tenants can be specified for the selected user type(s), or you can specify all tenants.

:::image type="content" source="media/gdap/conditional-access-policy-2.png" alt-text="Screenshot of CA policy.":::

For more information, see:

- [Graph API Experience: Beta API with the new external user type information](/graph/api/resources/conditionalaccessguestsorexternalusers)
- [Conditional access policy](/azure/active-directory/conditional-access/concept-conditional-access-users-groups)
- [Conditional access external users](/azure/active-directory/external-identities/authentication-conditional-access#assigning-conditional-access-policies-to-external-user-types-preview)

##### Do I need a GDAP relationship to create support tickets although I have Premier Support for Partners?

Yes, regardless of the support plan you have, the least privileged role for partner users to be able to create support tickets for their customer is Service support administrator. 

## GDAP API

###### Are APIs available to create a GDAP relationship with customers?

For information about APIs and GDAP, see the [Partner Center developer documentation](/partner-center/develop)

###### Can I use the beta GDAP APIs for production?  

Yes. It's recommended that partners use the [beta GDAP APIs](/graph/api/resources/delegatedadminrelationships-api-overview?view=graph-rest-beta&preserve-view=true) for production and later switch to APIs v.1 when they become available.

Although there's a warning, "Use of these APIs in production applications isn't supported," that generic guidance is for any beta API under Graph and isn't applicable to the beta GDAP Graph APIs.

###### Can I create multiple GDAP relationships with different customers at once?

Yes. GDAP relationships can be created using APIs, enabling partners to scale this process. Creating multiple GDAP relationships isn't available at Partner Center, however. For information about APIs and GDAP, see the [Partner Center developer documentation](/partner-center/develop).

###### Can I bulk migrate customers from DAP to GDAP?

Yes. You can bulk migrate customers from DAP to GDAP using APIs. Using multiple APIs, you can automate the process of creating GDAP relationships with your customers. For information about APIs and GDAP, see the [Partner Center developer documentation](/partner-center/develop).

###### Can multiple security groups be assigned in a GDAP relationship using one API call?

The API works for one security group at a time, but you can map multiple security groups to multiple roles at Partner Center.

## Roles

###### Which GDAP roles are needed to access an Azure subscription?

- To manage Azure with per-customer access partitioning (which is the recommended best practice), create a security group (such as *Azure Managers*) and **nest it under Admin agents**.

- To access an Azure subscription as an owner for a customer, you can assign any [Azure Active Directory (Azure AD) built-in role](/azure/active-directory/roles/permissions-reference) (such as *[Directory readers](/azure/active-directory/roles/permissions-reference#directory-readers)*, the least privileged role) to the *Azure Managers* security group.

   For steps to set up Azure GDAP, see [Workloads supported by granular delegated admin privileges (GDAP)](gdap-supported-workloads.md).

###### Is there guidance about the least-privileged roles I can assign to users for specific tasks?

Yes. For information about how to restrict a user's administrator permissions by assigning least privileged roles in Azure Active Directory (Azure AD), see [Least privileged roles by task in Azure Active Directory](/azure/active-directory/roles/delegate-by-task).

###### What is the least privileged role I can assign to a customer's tenant and still be able to create support tickets for the customer?

We recommend assigning the *Service support administrator* role. To learn more, see [Least privileged roles by task in Azure Active Directory](/azure/active-directory/roles/delegate-by-task).

###### Can I open support tickets for a customer in a GDAP relationship from which all Azure AD roles have been excluded?

No. The least privileged role for partner users to be able to create support tickets for their customer is the *Service support administrator*. Therefore, to be able to create support tickets for the customer, a partner user must be in a security group and assigned to that customer with that role.

###### Where can I find information about all the roles and workloads included in GDAP?

For information about all the roles, see [Azure AD built-in roles](/azure/active-directory/roles/permissions-reference).

For information about workloads, see [Workloads supported by granular delegated admin privileges (GDAP)](gdap-supported-workloads.md).

###### What GDAP role gives access to the Microsoft 365 Admin Center?

Many roles are used for Microsoft 365 Admin Center. For more information, see [Commonly used Microsoft 365 admin center roles](/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide&preserve-view=true#commonly-used-microsoft-365-admin-center-roles).

###### Can I create custom security groups for GDAP?

Yes. Create a security group, assign approved roles, and then assign partner tenant users to that security group.

###### Which GDAP roles give read-only access to the customer's subscriptions and so don't allow the user to manage them?

Read-only access to customer's subscriptions is provided by the *Global reader*, *Directory reader* and *Partner tier 2 support* roles.

###### What role should I assign to my partner agents (currently Admin agents) if I would like them to manage the customer tenant but not modify the customer's subscriptions?

We recommend removing the partner agents from the *Admin agent* role and adding them to a GDAP security group only. That way, they can administer services (service management and log service requests, for example), but they can't purchase and manage subscriptions (change quantity, cancel, schedule changes, and so on).

###### What happens if a customer grants GDAP roles to partner and then removes roles or severs the GDAP relationship?

The security groups assigned to the relationship lose access to that customer. The same thing happens if a customer terminates a DAP relationship.

###### Can a partner continue to transact for a customer after removing all GDAP relationship with the customer?

Yes, removing the GDAP relationships with a customer doesn't terminate the partners' reseller relationship with the customer. Partners can still purchase products for the customer and manage Azure budget and other related activities.

###### Can some roles in my GDAP relationship with my customer have a longer time to expiration than others?

No. All roles in a GDAP relationship have the same time to expiration: the duration that was chosen when the relationship was created.

###### Do I need GDAP to fulfill orders for new and existing customers in Partner Center?

No. You don't need GDAP to fulfill orders for new and existing customers. You can continue to use the same process to fulfill customer orders in Partner Center.

###### Do I have to assign one partner agent role to all customers, or can I assign a partner agent role to one customer only?

GDAP relationships are per-customer. You can have multiple relationships per customer. Each GDAP relationship can have different roles and use different Azure AD Groups within your CSP Tenant.

In Partner Center, role assignment works at customer-to-GDAP relationship level. If you want to multicustomer role assignment, you can automate using APIs.

###### Can a partner user have GDAP roles and a Guest account?

Guest accounts don't work with GDAP and DAP. Customers must remove any Guest accounts to get GDAP and DAP to work.

###### Do I need DAP/GDAP for Azure subscription provisioning?

No, you don't need DAP or GDAP to purchase Azure Plans and provision Azure subscriptions for a customer. The process to create an Azure Subscription for a customer is documented at [Create a subscription for a partner's customer - Azure Cost Management + Billing](/azure/cost-management-billing/manage/create-customer-subscription). By default, the **Admin Agents** group in the Partner's tenant becomes the owner of the Azure Subscriptions provisioned for the customer. Sign in to the Azure portal using your Partner Center ID.

To provision access to the customer, you need a GDAP relationship. The GDAP relationship must include at minimum the Azure AD role of **Directory Readers**. To provision access in Azure, use the access control (IAM) page. For AOBO, sign in to Partner Center, and use the **Service Management** page to provision access to the customer.

GDAP currently only supports [Azure AD built-in roles](/azure/active-directory/roles/permissions-reference). Custom Azure AD roles aren't supported.

###### Which Azure AD roles are supported by GDAP?

## DAP and GDAP

###### Is GDAP replacing DAP?

Yes. During the transition period, DAP and GDAP will coexist, with GDAP permissions taking precedence over DAP permissions for *Microsoft 365*, *Dynamics 365*, and *Azure* workloads.

###### Can I continue to use DAP, or do I have to transition all my customers to GDAP?

DAP and GDAP coexist during the transition period. However, GDAP will eventually replace DAP to ensure that we provide a more secure solution for our partners and customers. It's advised that you transition your customers to GDAP as soon as possible to ensure continuity.

###### While DAP and GDAP coexist, will there be any changes to the way a DAP relationship is created?

There are no changes to the existing DAP relationship flow while DAP and GDAP coexist.

###### What Azure Active Directory roles would be granted for default GDAP as part of Create customer?

DAP is currently granted when a new customer tenant is created. Starting September 25, 2023, Microsoft will no longer grant DAP for new customer creation and will instead grant Default GDAP with specific roles. The default roles vary by partner type, as shown in the following table:


| Azure AD Roles Granted For Default GDAP       | Direct Bill Partners | Indirect Providers | Indirect Resellers | Domain Partners | Control Panel Vendors (CPVs) | Advisor | Opted out of Default GDAP (No DAP) |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------ | ---------------------- | ---------------------- | ------------------- | -------------------------------- | ----------- | -------------------------------------- |
| 1. [Directory Readers](/azure/active-directory/roles/permissions-reference#directory-readers). Can read basic directory information. Commonly used to grant directory read access to applications and guests. | x                        | x                      | x                      | x                   | x                                |            |                                        |
| 2. [Directory writers](/azure/active-directory/roles/permissions-reference#directory-writers). Can read and write basic directory information. For granting access to applications, not intended for users. | x                        | x                      | x                      | x                   | x                                |            |                                        |
| 3. [License Administrator](/azure/active-directory/roles/permissions-reference#license-administrator). Can manage product licenses on users and groups. | x                        | x                      | x                      | x                   | x                                |            |                                        |
| 4. [Service Support Administrator](/azure/active-directory/roles/permissions-reference#service-support-administrator). Can read service health information and manage support tickets. | x                        | x                      | x                      | x                   | x                                |            |                                        |
| 5. [User Administrator](/azure/active-directory/roles/permissions-reference#user-administrator). Can manage all aspects of users and groups, including resetting passwords for limited admins.   | x                        | x                      | x                      | x                   | x                                |            |                                        |
| 6. [Privileged Role Administrator](/azure/active-directory/roles/permissions-reference#privileged-role-administrator). Can manage role assignments in Azure AD, and all aspects of Privileged Identity Management.                             | x                        | x                      | x                      | x                   | x                                |            |                                        |
| 7. [Helpdesk Administrator](/azure/active-directory/roles/permissions-reference#helpdesk-administrator). Can reset passwords for non-administrators and Help Desk administrators.        | x                        | x                      | x                      | x                   | x                                |            |                                        |
| 8. [Privileged Authentication Administrator](/azure/active-directory/roles/permissions-reference#privileged-authentication-administrator). Can access to view, set and reset authentication method information for any user (admin or nonadmin). | x                        | x                      | x                      | x                   | x                                |            |                                        |
| 9. [Cloud Application Administrator](/azure/active-directory/roles/permissions-reference#cloud-application-administrator). Can create and manage all aspects of app registrations and enterprise apps except App Proxy.        | x                        | x                      |                        | x                   | x                                |             |                                        |
<<<<<<< HEAD
| 10. [Application Administrator](/azure/active-directory/roles/permissions-reference#application-administrator). Can create and manage all aspects of app registrations and enterprise apps. | x                        | x                      |                        | x                   | x                                |             |                                        |
=======
| 10. [Application Administrator](/azure/active-directory/roles/permissions-reference#application-administrator).  Can create and manage all aspects of app registrations and enterprise apps. | x                        | x                      |                        | x                   | x                                |             |                                        |
>>>>>>> e8cb93c44b47f75c2045bd14c50b58c3d8e1cc8e
| 11. [Global Reader](/azure/active-directory/roles/permissions-reference#global-reader). Can read everything that a Global administrator can, but can't update anything.     | x                        | x                      | x                      | x                   | x                                |             |                                        |
| 12.   [External Identity Provider Administrator](/azure/active-directory/roles/permissions-reference#external-identity-provider-administrator). Can manage federation between Azure AD organizations and external identity providers. |                          |                        |                        | x                   |                                  |             |                                        |
| 13.   [Domain Name Administrator](/azure/active-directory/roles/permissions-reference#domain-name-administrator). Can manage domain names in cloud and on-premises.   |                          |                        |                        | x                   |                                  |             |                                        |

###### How will GDAP work with Privileged Identity Management in Azure AD?

Partners can implement [Privileged Identity Management (PIM)](/azure/active-directory/privileged-identity-management/pim-configure) on a GDAP security group in the partner's tenant to elevate the access of a few high-privilege users, just in time (JIT) to grant them high-privilege roles like Password admins with automatic removal of access.

To enable this implementation, the subscription to Microsoft Entra ID P2 is required by PIM is available for free. Microsoft partners can [sign in to get the details](https://partner.microsoft.com/resources/detail/cybersecurity-with-azure-ad-pdf).

Until **January 2023**, it was required that every **Privileged Access Group** (former name for the **PIM for Groups** feature) had to be in a **role-assignable** group. This restriction has now been **removed**. Given this, it's now possible to enable **more** **than** **500** **groups** per
tenant **in PIM**, but only up to 500 groups can be role-assignable.

Summary:

- Partners can use both role-assignable **and non-role-assignable** groups in PIM. This effectively **removes the limit on 500 groups**/tenant in PIM.

- With the latest updates, there will be two ways to onboard **group** to PIM (UX-wise): from the **PIM** menu or from the **Groups** menu. Regardless of the way you choose, the net result is the same.

  - Ability to onboard role-assignable/non-role-assignable groups through PIM menu is already available.

  - Ability to onboard role-assignable/non-role-assignable groups through Groups menu is already available.

- For more information, see [Privileged Identity Management (PIM) for Groups (preview) - Azure Active Directory](/azure/active-directory/privileged-identity-management/concept-pim-for-groups).


###### How do DAP and GDAP coexist if a customer buys Microsoft Azure and Microsoft 365 or Dynamics 365?

GDAP is generally available with support for all Microsoft commercial cloud services (*Microsoft 365*, *Dynamics 365*, *Microsoft Azure*, and *Microsoft Power Platform* workloads). For more information about how DAP and GDAP can coexist and how GDAP takes precedence, see [How will GDAP take precedence over DAP](#how-do-gdap-permissions-take-precedence-over-dap-permissions-while-dap-and-gdap-coexist).

###### I have a large customer base (10,000 customer accounts, for example). How do I transition from DAP to GDAP?

This action can be carried out by APIs.

###### Will my partner earned credit (PEC) earnings be affected when I transition from DAP to GDAP? Will there be any effect on Partner Admin Link (PAL)?

No. Your PEC earnings won't be affected when you transition to GDAP. There are no changes to PAL with the transition, ensuring that you continue to earn PEC.

###### Is PEC affected when DAP/GDAP is removed?

- If a partner's customer has DAP only and DAP is removed, PEC isn't lost.
- If a partner's customer has DAP, and they move to GDAP for Office and Azure simultaneously, and DAP is removed, PEC isn't lost.
- If the partner's customer has DAP, and they move to GDAP for Office but keep Azure as-is (they don't move to GDAP) and DAP is removed, PEC won't be lost, but Azure subscription access will be lost.
- If an RBAC role is removed, PEC is lost, but removing GDAP won't remove RBAC.

###### How do GDAP permissions take precedence over DAP permissions while DAP and GDAP coexist?

When the user is part of both the GDAP security group and the DAP Admin agents group *and* the customer has both DAP and GDAP relationships, GDAP access takes precedence at the partner, customer, and workload level.

For example, if a partner user signs in for a given workload and there's DAP for the Global admin role and GDAP for the Global reader role, the partner user only gets Global reader permissions.

If there are three customers with GDAP roles assignments to only GDAP security group (not Admin agents):

:::image type="content" source="./media/gdap/gdap-faq-partner-tenant.png" alt-text="Diagram showing the relationship between different users as members of *Admin agent* and GDAP security groups.":::

| Customer     | Relationship with partner
|--------------|--------------------------------
| Customer 1   | DAP (no GDAP)
| Customer 2   | DAP + GDAP both
| Customer 3   | GDAP (no DAP)

The following table describes when a user signs in to a different customer tenant.

| Example user    | Example customer tenant  | Behavior  | Comments         |
|-------------|---------------------------------|---------------|---------------------------------------------|
| User 1      | Customer 1                      | DAP           | This example is DAP as-is.       |
| User 1      | Customer 2                      | DAP           | There's no GDAP role assignment to the *Admin agents* group, which results in DAP behavior.     |
| User 1      | Customer 3                      | No access     | There's no DAP relationship, so the *Admin agents* group doesn't have access to customer 3. |
| User 2      | Customer 1                      | DAP           |   This example is DAP as-is       |
| User 2  | Customer 2                  | GDAP      | GDAP takes precedence over DAP because there's a GDAP role assigned to user 2 through the GDAP security group even if the user is part of the *Admin agent* group.  |
| User 2      | Customer 3                      | GDAP          | This example is a GDAP-only customer.       |
| User 3      | Customer 1                      | No access     | There's no GDAP role assignment to customer 1.        |
| User 3      | Customer 2                      | GDAP          | User 3 isn't part of the *Admin agent* group, which results in GDAP-only behavior.      |
| User 3      | Customer 3                      | GDAP          | GDAP-only behavior    |

###### Will disabling DAP or transitioning to GDAP affect my legacy competency benefits or Solutions Partner designations I've attained?

DAP and GDAP aren't eligible association types for Solutions Partner designations and disabling or transitioning from DAP to GDAP won't impact your attainment of Solutions Partner designations. Your renewal of legacy competency benefits or Solutions Partner benefits will also not be impacted.

Go to [Partner Center Solutions Partner designations](https://partner.microsoft.com/dashboard/mpn/program/solutionspartner/solutionareas/overview) to view what other partner association types are eligible for Solutions Partner designations.

###### How does GDAP work with Azure Lighthouse? Do GDAP and Azure Lighthouse affect each other?

With respect to the relationship between Azure Lighthouse and DAP/GDAP, think of them as decoupled parallel paths to Azure resources, so severing one shouldn't affect the other.

- In the Azure Lighthouse scenario, users from the partner tenant never sign-in to the customer tenant and don't have any Azure AD permissions in the customer tenant. Their Azure RBAC role assignments are also kept in the partner tenant.

- In the GDAP scenario, users from the partner tenant sign-in to the customer tenant, and the Azure RBAC role assignment to the Admin agents group is also in the customer tenant. You can block the GDAP path (users can no longer sign in) while the Azure Lighthouse path is unaffected. Conversely, you can sever the Lighthouse relationship (projection) without affecting GDAP. For more information, see the [Azure Lighthouse](/azure/lighthouse/concepts/cloud-solution-provider) documentation.

###### How does GDAP work with Microsoft 365 Lighthouse?

Managed Service Providers (MSPs) enrolled in the Cloud Solution Provider (CSP) program as *indirect resellers* or *direct bill* partners can now use Microsoft 365 Lighthouse to set up GDAP for any customer tenant. Because there are a few ways that partners are managing their transition to GDAP already, this wizard lets Lighthouse partners adopt role recommendations specific to their business needs. It also lets them adopt security measures like just-in-time (JIT) access. MSPs can also create GDAP templates through Lighthouse to easily save and reapply settings that enable least-privileged customer access. For more information, and to view a demo, see the [Lighthouse GDAP setup wizard](/microsoft-365/lighthouse/m365-lighthouse-setup-gdap?view=o365-worldwide&preserve-view=true).

MSPs can set up GDAP for any customer tenant in Lighthouse. To access customer's workload data in Lighthouse, a GDAP or DAP relationship is required. If GDAP and DAP coexist in a customer tenant, GDAP permissions take precedence for MSP technicians in GDAP-enabled security groups. For more information on requirements for Microsoft 365 Lighthouse, see [Requirements for Microsoft 365 Lighthouse](/microsoft-365/lighthouse/m365-lighthouse-requirements?view=o365-worldwide&preserve-view=true).

###### What is the best way to move to GDAP and remove DAP without losing access to Azure subscriptions if I have customers with Azure?

The correct sequence to follow for this scenario is:

1. Create a GDAP relationship for **both Microsoft 365 and Azure**.
2. Assign Azure AD roles to security groups for **both Microsoft 365 and Azure**.
3. Configure GDAP to take precedence over DAP.
4. Remove DAP.

> [!IMPORTANT]
> If you don't follow these steps, existing Admin agents managing Azure may lose access to Azure subscriptions for the customer.

The following sequence could result in *losing access* to Azure subscriptions:

1. Remove DAP.

   You won't necessarily lose access to an Azure subscription by removing DAP. But at this time you can't browse the customer's directory to do any Azure RBAC role assignments (such as assigning a new customer user as subscription RBAC contributor).
1. Create a GDAP relationship for **both Microsoft 365 and Azure together.**

   You may lose access to the Azure subscription at this step as soon as GDAP is set up.
1. Assign Azure AD roles to security groups for **both Microsoft 365 and Azure**

   You'll regain access to Azure subscriptions after Azure GDAP setup is complete.

###### I have customers with Azure subscriptions without DAP. If I move them to GDAP for Microsoft 365, will I lose access to the Azure subscriptions?

If you have Azure subscriptions *without DAP* that you manage as owner, by adding GDAP for Microsoft 365 to that customer, you may lose access to the Azure subscriptions. To avoid that, move the customer to Azure GDAP *at the same time* that you move the customer to Microsoft 365 GDAP.

> [!IMPORTANT]
> If these steps aren't followed, existing Admin agents managing Azure may lose access to Azure subscriptions for the customer.

###### Can a single relationship link be used with multiple customers?

No. Relationships, once accepted, aren't reusable.

###### If I have a reseller relationship with customers without DAP and who have no GDAP relationship, can I access their Azure subscription?

If you have an existing reseller relationship with the customer, you'll still need to establish a GDAP relationship in order to can manage their Azure subscriptions. 

1. Create a security group (for example, Azure Managers) in Azure AD.
1. Create a GDAP relationship with the **directory reader** role. 
1. Make the security group a member of the **Admin Agent** group.

Once this is done, you'll be able to manage your customer's Azure subscription via AOBO. The subscription can't be managed via CLI/Powershell.

###### Can I create an Azure plan for customers without DAP and who have no GDAP relationship?

Yes, you can create an Azure plan even if there's no DAP or GDAP with an existing reseller relationship; however, in order to manage that subscription, you'll need DAP or GDAP.

###### Why is the Company details section in the Account page under Customers no longer displaying details when DAP is removed?

As partners transition from DAP to GDAP, they must ensure the following are in place to see Company details:

- An active GDAP relationship
- Any of the following Azure AD roles are assigned: Global Administrator, Directory Readers, Global Reader. Refer to [grant granular permissions to security groups](/partner-center/gdap-assign-azure-ad-roles).

###### Why is my username replaced with "user_somenumber" in portal.azure.com when a GDAP relationship exists?

When a CSP logs into their customer's Azure portal (portal.azure.come) using their CSP credentials and a GDAP relationship exists, the CSP notices that their username is "user_" followed by some number. It doesn't display their actual username as in DAP. This is by design.

:::image type="content" source="./media/gdap/username.png" alt-text="Screenshot of username showing replacement. ":::

###### What are the timelines for Stop DAP and grant Default GDAP with creation of a new customer?

| Tenant type | Availability date         | Partner Center API behavior (POST /v1/customers)<br>enableGDAPByDefault: true | Partner Center API behavior (POST /v1/customers)<br>enableGDAPByDefault: false | Partner Center API behavior (POST /v1/customers)<br>No change to request or payload | Partner Center UI behavior        |
| ----------- | ------------------------- | ----------------------------------------------------------------------------- | ------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------- | --------------------------------- |
| **Sandbox**   | September 25, 2023 (API Only) | DAP = No. Default GDAP = Yes                                                  | DAP = No. Default GDAP = No                                                    | DAP = Yes. Default GDAP = No                                                        | Default GDAP = Yes                |
| **Production**  | October 10, 2023 (API + UI)    | DAP = No. Default GDAP = Yes                                                  | DAP = No. Default GDAP = No                                                    | DAP = Yes. Default GDAP = No                                                        | Opt-in/out available: Default GDAP |
| **Production**  | November 1, 2023              | DAP = No. Default GDAP = Yes                                                  | DAP = No. Default GDAP = No                                                    | DAP = No. Default GDAP = Yes                                                        | Opt-in/out available: Default GDAP |

Partners must explicitly [grant granular permissions to security groups](/partner-center/gdap-assign-azure-ad-roles) in the Default GDAP.<br>
Starting October 9, 2023, DAP will no longer be available with reseller relationships. The updated Request Reseller Relationship link will continue to be available in Partner Center UI and the API contract “/v1/customers/relationship requests” property URL will continue to return the invitation URL to be sent to the admin of the customer tenant.

###### Should a partner grant granular permissions to security groups in the Default GDAP?
Yes, partners must explicitly [grant granular permissions to security groups](/partner-center/gdap-assign-azure-ad-roles) in the Default GDAP to manage customer.

###### What actions can a partner with Reseller relationship but no DAP and no GDAP perform in Partner Center?
Partners with reseller relationship only without DAP or GDAP can create customers, place & manage orders, download software keys, manage Azure RI. Cannot view customer company details, cannot view users or assign licenses to users, cannot log tickets on behalf of customers, cannot access & administer product specific admin centers (like Teams admin center, etc.).

###### What action must a partner perform moving from DAP to GDAP regarding consent?
For a partner or CPV to access and manage a customer tenant, their app's service principal must be consented in customer tenant. When DAP is active, they must add the app's service principal to the Admin Agents SG in the partner tenant. With GDAP, partner must ensure their app is consented in customer tenant. If the app uses delegated permissions (App + User) and an active GDAP exists with any of the three roles (Cloud Application Administrator, Application Administrator, Global Administrator) [consent API](/partner-center/developer/control-panel-vendor-apis) can be leveraged. If the app uses application only permissions, it must be manually consented either by the partner or customer having any of the three roles (Cloud Application Administrator, Application Administrator, Global Administrator), using [tenant-wide admin consent URL](/azure/active-directory/manage-apps/grant-admin-consent?pivots=portal#construct-the-url-for-granting-tenant-wide-admin-consent).

## Offers

###### Is management of Azure subscriptions included in this release of GDAP?

Yes. The current release of GDAP supports all products: *Microsoft 365*, *Dynamics 365*, *Microsoft Power Platform*, and *Microsoft Azure*.
