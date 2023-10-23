---
title: Purchase the Azure plan for customers and access the latest Azure services
ms.topic: how-to
ms.date: 09/09/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Using the Azure plan, learn how to buy single or multiple Azure subscriptions, Azure reservations, to configure resources, and to view or add subscriptions.
author: iragulati1
ms.author: iragulati
---
# Purchase the Azure plan for customers and access the latest Azure services

**Applies to**: Partner Center

**Appropriate roles**: Global admin | User management admin | Sales agent

When you purchase an Azure plan for your customers under the Microsoft Customer Agreement, you have access to the full catalog of the latest Azure services at pay-as-you-go rates. Cloud Solution Provider (CSP) partners will now be able to access any Azure service when it becomes generally available. A partner can have multiple Azure subscriptions under an Azure plan.

## Country/region availability

The new commerce experience in CSP for Azure is currently scheduled to be available in 137 countries. See the full list of those [countries/regions](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE3QN0x).

## How to purchase Azure plan

How you purchase the Azure plan is similar to purchasing any other subscription. The key difference is that before you actually place your order you need to confirm that your customer has signed the Microsoft Customer Agreement.

1. Select **Segment Commercial**, then type "Microsoft Azure".

2. Under **Azure plan**, select **Add to cart**.

   :::image type="content" source="media/azure/Azurepurchase1.png" alt-text="Purchase.":::

The partner must confirm the customer has reviewed and accepted the Microsoft Customer Agreement terms. For more information on how the partner can do so, read the [Confirm customer acceptance of the Microsoft Customer Agreement](./confirm-customer-agreement.md). Other resources are available in the [resource gallery](https://partner.microsoft.com/resources/collection/Microsoft-Customer-Agreement-in-the-CSP-program#/).

Next, confirm digitally or invite the customer to sign the Microsoft Customer Agreement directly with Microsoft.

### To invite the customer to sign the agreement directly

1. On the customer's **Account** page, select **Update** next to **Microsoft Customer Agreement**.

2. Fill out the information about the individual at the customer's company who accepted the Microsoft Customer Agreement.

3. Select **Save and continue**.

As part of the new commerce experience for Azure in CSP, we've introduced a [new Azure offer](./azure-plan-lp.md). For important dates related to the previous Azure offer (MS-AZR-0145p), refer to the [offer document](https://go.microsoft.com/fwlink/p/?linkid=2164140).

If you enrolled **before** July 21, 2021:

- You'll be able to add the previous Azure offer to cart to your cart for customers who have purchased it in the past.
- If you enrolled before July 21 *and* have customers that enrolled after July 21, you won't be able to add the previous Azure offer to your cart.

If you  enrolled **on or after** July 21, 2021

- You won't be able to add the previous Azure offer to your cart.

The following error will be encountered if you try to add the previous Azure offer but aren't eligible due to above business policy.

:::image type="content" source="media/add-products.png" alt-text="Screenshot showing the Add products screen.":::

To find the new Azure plan with Partner Center APIs, see [Create an Azure plan](/partner-center/develop/create-azure-plan#get-the-catalog-item-for-azure-plan).

## Review and buy

Return to the **Add a product** page where you can see that the Azure plan has been added. Select **Review** to review your purchase and then select **Buy**.

> [!NOTE]
> Once you purchase the Azure plan for a customer, you can no longer purchase Microsoft Azure (0145p) for that customer. You'll need to create future subscriptions through the Azure plan.

> [!NOTE]
> You cannot set a friendly name when purchasing an azure plan. Friendly name can be set on the subscription only after it has been purchased, by updating the subscription via the Partner Center or the update subscription API.

## Purchase Azure reservations under the Azure plan

You can also buy Microsoft Azure reservations under Azure plan on behalf of your customers in Partner Center. (Or, if you prefer, you can [give permission for your customers to buy their own Azure reservations](give-customers-permission.md) from a prior subscription you purchased for them.)

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Select the customer who wants to purchase Azure reservations, and then select the down arrow to expand the customer's row.

3. Select **Add products** and then select **Azure**.

   - Choose the customer's market segment from the **Segment** list.
   - Choose **Reservations** from the **Product type** list.
   - Choose the type of reservation the customer wants from the **Reservations type** list.

Azure reservations must be associated with an active Azure plan. Choose the Azure plan you want to add Azure reservations to from the Customer subscription list.

> [!IMPORTANT]
> If the customer doesn't already have an active Azure plan, select Azure to add one now. For further instructions read [Purchase Azure reservations](azure-reservations-buying.md#purchase-azure-reservations).

> [!NOTE]
> A reservation's scope can only be set to **Shared**, currently in Partner Center. To select single subscription scope or update from shared to single subscription scope go to **Microsoft Azure Management portal** using following instructions.

:::image type="content" source="media/azure/addprods1.png" alt-text="Shared scope reservations setting.":::

To manage the customer's reservation in the Azure portal:

1. From **Customers** select the customer you want to manage.

2. Using the down arrow, expand the customer's row and select **Microsoft Azure Management portal**.

## View Azure subscriptions under the Azure plan

From the **Subscriptions** page, in the usage-based section, expand **Azure plan** to see associated Azure subscriptions under the Azure plan.

:::image type="content" source="media/azure/addprods2.png" lightbox="media/azure/addprods2.png" alt-text="View list of Azure subscriptions.":::

## Add subscriptions and configure resources

You create subscriptions and configure resources for your customers through the Azure portal. Learn how at [Create Azure subscriptions](/azure/cost-management-billing/manage/create-subscription#create-a-subscription-as-a-partner-for-a-customer).

You're also able to separate your customer's environment by workload or project. You can also manage subscriptions through [Azure Lighthouse](https://azure.microsoft.com/services/azure-lighthouse/) and the [Azure portal](https://portal.azure.com).

To manage your customer's resources and subscriptions, you need **Admin on Behalf Of** (AOBO) privileges. For information on managing your access, read [Manage subscriptions and resources under the Azure plan](azure-plan-manage.md)

## Next steps

- [Customer transitions to Azure plan](azure-plan-transition.md)

- [Partner earned credit - overview](partner-earned-credit.md)
