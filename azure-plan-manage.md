---
title: Manage subscriptions and resources under the Azure plan
ms.topic: article
ms.date: 11/22/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Learn how partners can use different role-based access control (RBAC) options to gain operational control and management of a customer's Azure resources.
author: migolova
ms.author: migolova
---
# Manage subscriptions and resources under the Azure plan

**Appropriate roles**: Admin agent

This article explains how Cloud Solution Provider (CSP) partners can use various role-based access control (RBAC) options to get operational control and management of a customer's Azure resources.

When you transition a customer to the Azure plan, you're assigned privileged admin rights in Azure—subscription owner rights through Admin on Behalf of (AOBO) by default.

 > [!NOTE]
 > Admin rights to the Azure subscription can be removed by the customer at the subscription level, resource group level, or workload level.

Partners can get continuous operational control and management of a customer's Azure resources in CSP by using various options available through the role-based access control feature (RBAC).

- **Admin on Behalf of** - With [AOBO](https://channel9.msdn.com/Series/cspdev/Module-11-Admin-On-Behalf-Of-AOBO), any user with the Admin agent role in the partner tenant has RBAC owner access to Azure subscriptions that you create through the CSP program.

- **Azure Lighthouse**: AOBO doesn't have the flexibility to create distinct groups that work with different customers, or to enable different roles for groups or users. However, using Azure Lighthouse, you can assign different groups to different customers or roles. Because users have the appropriate level of access through Azure delegated resource management, you can reduce the number of users who have the Admin agent role (and thus have full AOBO access). That helps improve security by limiting unnecessary access to your customers' resources. It also gives you more flexibility to manage multiple customers at scale. For more information, see [Azure Lighthouse and the Cloud Solution Provider program](/azure/lighthouse/concepts/cloud-solution-provider).

- **Directory or Guest Users or [Service Principals](/azure/active-directory/develop/app-objects-and-service-principals)**: You can delegate granular access to CSP subscriptions by adding users in the customer directory or by adding guest users and assigning specific RBAC roles.

As a security practice, Microsoft recommends assigning users the minimum permissions they need to do their work. For more information, see [Azure Active Directory Privileged Identity Management resources](/azure/active-directory/privileged-identity-management/pim-configure).

## Link your PartnerID to your credentials to manage a customer's Azure resources

The following table shows the methods used to associate your PartnerID (formerly MPN ID) with various RBAC access options.

|**Category**   |**Scenario**   |**PartnerID association**|
|-----------------|:------------------------|:------------------|
|AOBO   |CSP direct partner or indirect provider creates the subscription for the customer, making the CSP direct partner or indirect provider the default owner of the subscription using AOBO. CSP direct partner or indirect provider gives indirect reseller access to the subscription using AOBO.|Automatic (no partner work required)|
|Azure Lighthouse|Partner creates a new [Managed Service offer in Marketplace](/azure/lighthouse/concepts/managed-services-offers). The offer is accepted on the CSP subscription and the partner gets access to the CSP subscription.|Automatic (no partner work required)|
|Azure Lighthouse|Partner deploys an [Azure Resource Manager (ARM) template](/azure/lighthouse/how-to/onboard-customer) in Azure subscription|Partner must associate the PartnerID with the user or service principal in the partner tenant. For more information, see [Link your PartnerID to track your impact on delegated resources](/azure/lighthouse/how-to/partner-earned-credit).|
|Directory or Guest user|Partner creates a new user or service principal in the customer directory and gives access to the CSP subscription to the user. Partner creates a new user or service principal in the customer directory. Partner adds the user to a group and gives access to the CSP subscription to the group.|Partner must associate the PartnerID with the user or service principal in the customer tenant. For more information, see [Link a PartnerID to your account that's used to manage customers](/azure/cost-management-billing/manage/link-partner-id).|

## Confirm that you have admin access

You must have admin access to manage your customer's services and to receive earned credits. For more information about earned credits, see [Partner earned credits](partner-earned-credit.md).

To determine whether you have admin access, use the following steps:

- *Review the daily usage file*: Review the unit price and effective unit price in the daily usage file and confirm whether a discount is being applied. If you're receiving the discount, you're the admin.

### Create an Azure monitor alert

You can create an activity log [Azure Monitor Alert](/azure/azure-monitor/platform/alerts-activity-log) to be notified if your RBAC access is removed from a CSP subscription.

To create an Azure monitor alert, use the following steps:

1. [Create an alert](/azure/role-based-access-control/role-assignments-alert).

   :::image type="content" source="media/azure/azurealert1.png" lightbox="media/azure/azurealert1.png" alt-text="Screenshot of an Azure portal alert.":::

2. Select the type of action that you want the alert to take.

   For example, if you specify that you want an email, you'll receive an email notifying you if any role assignment deletion occurs.

   :::image type="content" source="media/azure/azureconfigurealert2.png" lightbox="media/azure/azureconfigurealert2.png" alt-text="Screenshot in the Azure portal of configuring an alert.":::

### AOBO removal

Customers can manage access to their subscriptions by going to **Access Control** at the Azure portal. From the **Role assignments** tab, they can select **Remove access**.

If a customer removes your access, you can:

- Talk with your customer to see if admin access can be reinstated.

- Use the access provided through [role-based access control (RBAC)](/azure/role-based-access-control/overview).

- Use access provided through [Azure Lighthouse](https://azure.microsoft.com/services/azure-lighthouse/).

Role-based access differs from admin access. Roles delimit precisely what you can and can't do. Admin access is broader.

To see the roles eligible to earn partner earned credit (PEC), see [Roles and permissions for the partner earned credit](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE3QuW2).

### Cancel an Azure subscription

In the event the customer's Azure plan subscriptions have been compromised, Partners can cancel Azure subscriptions from the Partner Center. This capability is available only to Global Administrators with Admin Agent roles. To do this:

1. Select the **Customer** from the customer list
2. Navigate to the customer's **Azure subscriptions**
3. Select the **Azure plan** the subscription is under
4. On the Azure plan details page, select the Azure subscriptions to cancel
5. Submit the changes

This will cancel only the selected Azure subscriptions. Customers with access to the Azure subscription may reactivate the subscription if the Azure plan is still active. To stop this from happening, Partners should cancel all the Azure subscriptions and then the Azure plan itself.

Partners can multi-select the subscriptions but can't cancel more than 10 subscriptions at a time. Partners can cancel the Azure plan when there are no active Azure subscriptions under it. This enables partners to shut down Azure plans and subscriptions that may have been compromised, even if a bad actor has removed their RBAC permissions.

Canceled Azure subscriptions from Partner Center can only be reactivated in the Azure portal, it's important that partners are sure they're canceling the correct Azure subscriptions.

Partners can cancel Azure subscriptions through the partner center portal or by API. For API details, see [Cancel an Azure subscription](/partner-center/develop/cancel-an-azure-subscription) and to try it out, see [Azure spending - Cancel an Azure entitlement - REST API](/rest/api/partner-center/azure-spending/cancel-an-azure-entitlement#code-try-0).

More on canceling Azure subscriptions can be found in the [Azure documentation](/azure/cost-management-billing/manage/cancel-azure-subscription#what-happens-after-subscription-cancellation)

## Next steps

- [Reinstating admin privileges for Azure CSP subscriptions](reinstate-csp.md)

- [Partner earned credit - overview](partner-earned-credit.md)

- [Partner earned credit for managed services](partner-earned-credit-explanation.md)
