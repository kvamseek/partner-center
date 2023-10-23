---
title: Obtain a customer's admin privileges
ms.topic: how-to
ms.date: 09/20/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Obtain the permissions you need to manage a customer's service or subscription on their behalf. Learn how permissions are granted, revoked, and managed.
author: kvamseek
ms.author: vamseekk
---

# Get delegated administration privileges from a customer

**Appropriate roles**: Admin agent | Sales agent

To manage a customer's service or subscription on their behalf, the customer must grant you administrator permissions for that service. To get administrator permissions from a customer, invite a customer to establish a reseller relationship with you. After the customer approves your request, you can sign in to the service's admin portal and manage the service on their behalf.

## <a name="invitesteps"></a> Invite a customer to establish a reseller relationship with you

To invite a customer to establish a reseller relationship with you, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Select **Request a reseller relationship**.

3. Clear the **Include delegated administration privileges for Azure Active Directory and Office 365** checkbox if you don't want [delegated administration permissions](dap-faq.md).

4. Review the draft **Email text**.

   You can select **Open in email** to open the draft in your default email application, or **Copy to clipboard** for editing or to paste the draft into an email message.

> [!IMPORTANT]
> You can edit the draft email request, but **be sure to keep the included link** because it is personalized to link the customer directly to your account.

5. Select **Done**.

6. Email the request to your customer.

> [!NOTE]
> The person who accepts your request to establish a reseller relationship must be a Global admin of your customer's tenant.

   When your customer selects the link in your email message, the Microsoft Admin Center page opens, where they can accept your request.

## Provision and manage the service for the customer

After the customer accepts your request, they'll appear on your **Customers** page in Partner Center. You can provision and manage the service for the customer from there.

To manage the customer's account, services, users, and licenses, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Select **Administer**, then expand the customer's record by selecting the down arrow near their name.

3. Select the admin portal for the service that you want to manage.

> [!IMPORTANT]
> Customers can reassign or remove administrator permissions in a service's admin portal. You should be aware (and inform your customers) that when a customer removes your administrator permissions, you can't open a service request at Microsoft on their behalf until you reestablish your relationship.

### Azure subscriptions and resource management

Each Azure subscription has its own set of resource management roles. Before a Cloud Solution Provider (CSP) partner can manage a customer's Azure subscription, that partner must be assigned  one or more roles under the Azure subscription. Specifically:

1. When a customer accepts a reseller invitation and grants delegated administration privilege to a partner, the partner doesn't automatically get access to existing Azure subscriptions under the customer tenant.

2. When the CSP partner provisions a new Azure subscription for the customer, the Admin Agents group under the CSP partner tenant is automatically assigned the Owner role under the subscription. Based on this role assignment, members of group can access and manage resources under the subscription.

3. When a customer removes delegated administration privileges from a partner using the Office 365 Portal, the partner can still manage the customer's Azure subscription, as long as the partner is still assigned to one or more roles under the subscription. To stop the partner from managing the Azure subscription, the customer must remove the role assignment.

## Customers can find which partners have delegated admin privileges

To find out which partners have admin privileges to their tenant from within the Office 365 admin portal, customers can use the following steps:

1. Sign in to the Office 365 admin portal as a Global admin.

2. Selects **Settings** > **Partner relationships**.

3. On the **Partner relationships** page, view the list of the partners with whom they work and those partners that have been granted delegated administration privileges to their tenant.

## Customers can manage a partner's delegated admin privileges

Customers can manage rights and permissions to their Office 365 accounts on the **Partner relationships** page in the Office 365 admin center. On this page, customers can:

1. See which partners they have a relationship with and which partners have delegated admin privileges

2. Remove a partner's delegated administration privileges from the tenant

Your customer may decide to remove your delegated admin privileges from their tenant but retain the relationship with you for subscription and license renewal purposes.

To remove delegated administration privileges from a partner, customers can use the following steps:

1. Sign in to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2074649).

2. Select the row of the partner to remove.

3. Select **Remove roles**.

4. When prompted to confirm, select **Yes**.

> [!IMPORTANT]
> Customers cannot find the partners who are assigned an Azure AD role using Azure AD Portal/PowerShell/Graph. Instead, they should use the Partner relationships page in the Office 365 Admin Portal to find out whether a delegated administration privilege has been assigned to a partner.

## Delegated admin privileges in Azure AD

There are two security groups in the partner's Azure AD tenant that are used for delegated administration: **Admin Agents** and **Helpdesk Agents**.

When a customer grants a delegated administration privilege to a partner:

1. The *Admin Agent* group is assigned to the *Global administrator* role in the customer's Azure AD tenant.

2. The *Helpdesk Agent* group is assigned to the *Helpdesk administrator* role in the customer's Azure AD tenant.

Based on the directory roles assigned, members of both groups can sign in to the customer's Azure AD tenant and Office 365 services using their partner credentials and administer on behalf of the customer.

If your customer removes delegated admin privileges, the Azure AD role assignments are removed, and you won't be able to manage the customer's Azure AD tenant.

## Windows Autopilot

From Partner Center, CSP partners can manage Autopilot profiles for their customers without delegated admin privileges under these circumstances:

1. If a customer removes delegated administration privileges but retains a reseller relationship with you, you can continue to manage Autopilot profiles for them.

2. You can manage customer devices that you or another partner have added.

3. You *can't* manage devices your customer has added through the Microsoft Store for Business, Microsoft Store for Education, or Microsoft Intune Portal.

For more information about Autopilot, see [Simplify device setup with Windows Autopilot](autopilot.md).

> [!IMPORTANT]
> The current Autopilot management experience in Partner Center might continue to change. At the time this article was published, the following changes are being considered:

1. A partner must be granted delegated administration privilege by the customer before the partner can add/update/remove profiles and applying/removing profile from any devices in the customer tenant.

2. A partner must be granted delegated administration privilege by the customer before the partner can remove devices added by other partners or by the customer in the customer tenant. Otherwise, the partner can remove only devices added previously by the same partner.
