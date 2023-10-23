---
title: Give customers permissions to buy their own products and services
description: Learn how CSP program partners can let customers buy their own services, like Azure reservations, for a subscription purchased for them in Partner Center.
ms.topic: how-to
ms.date: 10/13/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
author: jischulz
ms.author: jischulz
---

# Give customers permissions to buy their own products and services

**Appropriate roles**: Admin agent | Sales agent

This article shows how a partner in the Cloud Solution Provider (CSP) program can give a customer permission to buy some of their own services or resources.

Partners in the CSP program often use Partner Center and its commercial marketplace to buy solutions and services for their customers. Direct bill and indirect provider partners can then allow some customers to provision these services themselves directly from the Azure portal.

Here's an example. Let's say you buy an Azure plan subscription for a customer in Partner Center. You then decide to add other resources or services to that subscription on the customer's behalf. In this case, you might add Azure reservations to the customer's subscription (such as, adding reserved, virtual machine instances). You might then allow the customer to further provision the Azure reservation resources themselves in the Azure portal.

Now, with the **Customer permissions** feature, you give customers more self-service options with Azure resources. By turning on permissions for the customer, you allow customers to buy their own resources (such as, buying their own Azure reservations).

## Overview of customer permissions in Partner Center

Use the Customer **Account** page to turn on (or turn off) customer permissions. Currently, this feature supports:

- **Azure reservations:** Turning on this permission allows the customer to purchase their own Azure reservations for a specific Azure subscription you've purchased for them.
- **Azure savings plans:** Turning on this permission allows the customer to purchase their own Azure savings plan for a specific Azure subscription you've purchased for them.

Before you turn on customer permissions, note these important points:

- By default, customer permissions are automatically disabled (turned off) in Partner Center.

- Before you can turn on (or turn off) permissions for a customer, you must be assigned the role of Admin Agent in Partner Center.

  Partners assigned the role of Sales Agent or Help Desk Agent have read-only access and can't turn customer permissions on or off.

- You can turn on (enable) permissions for any customer you choose.

- You can turn on (or turn off) customer permissions using either the Partner Center or [Partner Center APIs](/partner-center/develop/manage-customers).

- After you turn on (enable) permissions for a specific customer, you'll be responsible to pay for any subsequent purchases made by that customer. If customers want to exchange, cancel or renew a purchase they've made (or they want to change the initial scope of a reservation), they will not be able to do so themselves. They need to ask you, as the partner, to help them exchange, cancel, and renew purchases, or make later changes to a reservation's scope.

- After you turn on permissions for a specific customer, you will **not be** notified of any later purchases made by the customer.

- Reservations purchases made by the customer will appear in Partner Center along with any purchases made by you. You can find these purchases on the customer's **Order history** page, their **Reservations** page, or in the [**Activity Log**](activity-logs.md).

- Azure savings plan purchases will appear in the Azure portal under **Savings plans**. Azure savings plans do no appear in the Partner Center or in the Partner Center APIs. 

> [!NOTE]
> For information about prices the customer will pay and how to help customers manage their purchases, see [Help customers manage reservations they purchase](give-customers-permission.md#help-customers-manage-reservations-they-purchase).

## Give customers permission to buy their own Azure reservations

Azure reservations are a great way to buy Azure services at a discounted rate. To learn more about the benefits of Azure reservations, see [What are Azure Reservations?](/azure/cost-management-billing/reservations/save-compute-costs-reservations)

Now you have the choice to buy Azure reservations on behalf of your customers, as you may have already been doing. Or, you can give customers permission to buy their own Azure reservations.

> [!NOTE]
> After you give customers permission to buy their own Azure reservations, help them manage any reservations they purchase. For more information, see [Help customers manage reservations they purchase](give-customers-permission.md#help-customers-manage-reservations-they-purchase).

## Give customers permission to buy their own Azure savings plans

Azure savings plans are a great way to buy Azure services at a discounted rate. You have the choice to buy Azure savings plans on behalf of your customers, as you may have already been doing. Or, you can give customers permission to buy their own Azure savings plans. Purchasing Azure savings plans happens only in the Azure portal.

To learn more about the benefits of Azure savings plans, see [What are Azure savings plans for compute?](https://go.microsoft.com/fwlink/?linkid=2211952&clcid=0x409)

### To enable customers to buy their own Azure reservations or Azure savings plans

1. Verify the customer has an existing Azure plan or Azure Global subscription you purchased on their behalf.

2. Verify the customer has been assigned the **Owner** role for this subscription.

3. Enable customer permissions (turn this feature **On**) to purchase their own Azure reservations or Azure savings plans.

Each step appears below.

### Verify the customer has an existing Azure subscription

Before you give customers permission to buy their own Azure reservations or Azure savings plans, you must verify the customer has an existing Azure plan or Azure Global subscription. If the customer shows no current Azure subscription in Partner Center, you must buy a subscription for them before you turn on their customer permissions.

- To see if a customer already has an Azure subscription, go to the Partner Center [customer list](https://partner.microsoft.com/commerce/customers/list) and select the specific customer from the list. Then select **Subscriptions** and look for any usage-based subscriptions for either Azure plan or Azure Global.

- If a customer doesn't have an existing Azure subscription, you can buy a subscription for them. See [Purchase the Azure plan](purchase-azure-plan.md).

### Verify the customer has been assigned the correct role in Azure

After you verify the customer has an existing Azure subscription, you also need to verify the key users associated with your customer have been assigned the correct **Owner** role for that Azure subscription. This is the role-based access (RBAC) the customer needs to buy Azure reservations for an Azure subscription you purchased.

Some partners may have already assigned the **Owner** role to customers wanting to actively manage and provision their own Azure resources. If you have already assigned **Owner** status to a customer to manage prior subscriptions you've purchased for them, you can skip this step.

> [!IMPORTANT]
> If a customer has not been assigned the **Owner** role, they will receive an error in the Azure portal preventing them from buying Azure reservations or Azure savings plans.

To verify the customer has been assigned the **Owner** role for an Azure subscription:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Select the customer, then select **Subscriptions** for that customer, and locate the specific Azure subscription.

3. Select **Manage**.

   This will open the [Azure portal](https://portal.azure.com/).

4. To assign the Owner role to a specific user, follow these steps to [assign a user as an administrator](/azure/cost-management-billing/manage/add-change-subscription-administrator#to-assign-a-user-as-an-administrator).

### Turn on or turn off customer permissions to purchase their own Azure reservations or Azure savings plans

After you verify the customer has an existing Azure subscription and users are assigned the **Owner** role for that subscription, you're ready to turn on (enable) customer permissions. You can also use these steps to turn off (disable) customer permissions. You can enable or disable customer permissions using either the Partner Center or [Partner Center APIs](/partner-center/develop/manage-customers).

To turn on or off customer permissions in Partner Center:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Select the customer, then select **Account**.

   The customer **Account** page appears.

3. Locate the **Customer permissions** area at the bottom of the page.

   :::image type="content" source="media/give-customers-permission-reservations.png" alt-text="Customer permissions on Account page." border="true":::

4. Under **Azure reservations** or **Azure savings plan**, locate the **Allow customer to purchase** option.

5. To turn on customer permissions, move the switch next to this option to the **On** position. To turn off customer permissions, move the switch to the **Off** position.

    > [!NOTE]
    > To learn what else happens when you turn on a customer's permissions to purchase their own Azure reservations or Azure savings plans, see [Overview of customer permissions in Partner Center](give-customers-permission.md#overview-of-customer-permissions-in-partner-center).
    >
    > When you turn on (or turn off) customer permissions, the Activity log records each action. (This log is accessible when you select the Gear icon from the top of the Partner Center). When you turn customer permissions on or off, the action will appear as either **Create Customer Purchase Permissions** or **Delete Customer Purchase Permissions** in the Activity log.

### Enable Microsoft Cost Management for customers

Partners can enable Microsoft Cost Management for customer tenant Azure subscriptions. Providing access allows customers to view their costs for Azure consumed services at pay-as-you-go retail rates. Costs are shown in the customer's billing currency for their consumed usage at Azure RBAC subscription and resource groups scopes. For more information about how partners can grant access to customers, see [Enable cost management for customer tenant subscriptions](/azure/cost-management-billing/costs/get-started-partners#enable-cost-management-for-customer-tenant-subscriptions).

> [!NOTE]
> Although partners can enable reservation and savings plan purchases, these purchases aren't shown in cost data.

## Help customers manage reservations they purchase

Once you give customers permission to purchase their own Azure reservations, you can help them better manage any resources they purchase. Customers can manage many aspects of Azure reservations themselves directly from the [Azure portal](https://portal.azure.com/). They'll need your help managing a few other aspects of Azure reservations they purchase within your CSP subscription.

Help customers understand more about managing these aspects of Azure reservations:

- Prices customers will pay for Azure reservations 
- How customers can optimize use of Azure reservations
- What happens when customers purchase reservations with a shared scope?
- What happens if customers want to change, cancel, and renew a reservation, or change its scope?

**Prices customers will pay for their reservations.** Your customer will be purchasing Azure reservations based on a subscription you previously bought for them in your CSP partner billing account. The customer's price for any Azure reservations they purchase based on this subscription is also set by you. This price may be different from the Web Direct price the customer sees in the Azure portal.

**How customers can optimize their use of a reservation.** Some customers might benefit from learning more about how to optimize their use of a reservation or how to assign a reservation's initial scope during their purchase. For more information, ask customers to read [Manage reservations for Azure resources](/azure/cost-management-billing/reservations/manage-reserved-vm-instance).

**What happens when a customer purchases a reservation with a shared scope?** When customers purchase a reservation based on a prior CSP subscription and assign a shared scope to that reservation, any discounts the customer has been given by you'll apply to matching usage for all subscriptions that you've purchased for that customer.

**What should customers do if they want to exchange, cancel, or renew a purchase they have made, or change the initial scope of a reservation?** Customers need to ask their partner to help them change a reservation's initial scope. They also need a partner's help to exchange, cancel, or renew a reservation. They can't perform these tasks themselves with reservations based on subscriptions purchased for them by a CSP partner.

## Help customers manage savings plans they purchase

Once you give customers permission to purchase their own Azure savings plans, you can help them better manage any resources they purchase. Customers can manage many aspects of Azure savings plans themselves directly from the [Azure portal](https://portal.azure.com/). They'll need your help managing a few other aspects of Azure savings plans they purchase within your CSP subscription.

Help customers understand more about managing these aspects of Azure savings plan:

- [Overview of Azure savings plans](https://go.microsoft.com/fwlink/?linkid=2211952)
- [What are Azure savings plans for compute?](https://go.microsoft.com/fwlink/?linkid=2211734)
- [Azure saving plan cancellation policies](https://go.microsoft.com/fwlink/?linkid=2212017)
- [How saving plan discount is applied](https://go.microsoft.com/fwlink/?linkid=2211954)
- [Manage Azure savings plans](https://go.microsoft.com/fwlink/?linkid=2211843)
- [Get pricing and rates for Azure meters](https://go.microsoft.com/fwlink/?linkid=2211735)

## Next steps

- [Buy Azure reservations on behalf of your customers](azure-reservations-buying.md)
- [Partner Center - Sell Microsoft reservations](azure-reservations.md)
- [Manage Azure reservations on behalf of your customers](azure-reservations-manage.md)
- [What are Azure savings plans for compute?](https://go.microsoft.com/fwlink/?linkid=2211734)
