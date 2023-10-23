---
title: Set an Azure spending budget for customers
ms.topic: how-to
ms.date: 6/22/2023
description: Learn how to set or remove monthly Azure spending budgets for your customers, and also to view Azure spending data and set budget-related notifications.
ms.service: partner-dashboard
ms.subservice: partnercenter-billing
author: sodeb
ms.author: sodeb
---

# Set, check, or remove monthly Azure spending budgets for customers in Partner Center

**Appropriate roles**: Admin agent

You can set a [monthly Azure spending budget](#set-azure-spending-budget) for your customers in Partner Center. This budget helps your customers track how much they spend on Azure and lets you compare their spending to the monthly budget. Also, your customers will be able to plan better how much they'll spend on Azure and avoid getting too high bills.

> [!NOTE]
> This feature is unavailable in sandbox or Test in Production (TIP) accounts.

Once you’ve set a budget for your customer’s Azure spending, you can also look at how they use Azure. These options may help you find services that aren’t set up correctly or strange patterns that could be signs of fraud. Then, you can work with your customers to find the cause and keep costs in check. You can also change the customer’s budget to a higher amount if needed.

## Azure spending data

Azure spending data is an *estimate*, and *actual billing amounts* may vary. The amount *doesn’t include* taxes, credits, or other fees.

The spending data is *refreshed daily*. Your customers can keep using Azure services and resources (and getting charged for them) if you don’t change their account settings in the Azure portal.

## Set Azure spending budget

You can set a monthly Azure spending budget for customers with **legacy Microsoft Azure subscriptions** in the Partner Center:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Billing**.

2. Select **Azure spending**.

3. On the **Azure spending** page, under **Customers with Microsoft Azure subscriptions**, select the customers for whom you want to set a budget.

4. Enter a value for **Monthly budget**.

5. Choose **Apply** to save your changes.

You can set a budget for an individual customer in their subscription settings.

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Select the customer's **Company name**.

3. On the customer’s **Subscriptions** page, under **Usage-based subscription**, choose **Change budget**.

4. Enter a value for the budget.

5. Choose **Apply** to save your changes.

You can remove a monthly Azure spending budget for your customers in Partner Center.

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Billing**.

2. Select **Azure spending**.

3. On the **Azure spending** page, under **Customers with Microsoft Azure subscriptions**, select the customer whose budget you want to remove.

4. Choose **Remove budget**.

You can track your customers’ current Azure spending and monthly budgets at any time.

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Billing**.

2. Select **Azure spending**.

3. On the **Azure spending** page, under **Customers with Microsoft Azure subscriptions**, you can see an overview of customers’ monthly budgets, current spending estimates and percentage of budget used.

:::image type="content" source="media/azure-plan-billing/azure-spending.png"  alt-text="Screenshot of the Azure spending page in Partner Center." lightbox="media/azure-plan-billing/azure-spending.png":::

## How to access the new Azure Spending (NCE) UI

To gain access to the new user interface in the New Commerce Experience (NCE):

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Billing**.
1. Select **Azure spending (NCE)** from the task menu on the left side.
1. On the resulting page, you’ll be able to view, set, edit, or remove budgets for your customers with Azure plan subscriptions.

> [!NOTE] 
> The new page shows only customers with Azure plan subscriptions who have an active reseller relationship with the partner. If the relationship ends after setting the budget, the customer will no longer appear on this page.

## Set Azure spending budget using the new (NCE) UI.

To set a monthly Azure spending budget for your customers in the Partner Center:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Billing**.
1. Select **Azure spending (NCE)** from the task menu on the left side.
1. In the **Customers** section, choose **Manage budget**.
1. In the side panel, search for the customer names for whom you want to set a budget.
1. Enter the budget amount for each customer.
1. Select **Submit**.

:::image type="content" source="media/azure-plan-billing/azure-spending-n-c-e.png"  alt-text="Screenshot shows the new NCE version of the Azure spend page, with a list of customers set up with Azure spending budgets in Partner Center." lightbox="media/azure-plan-billing/azure-spending-n-c-e.png":::

To update the monthly budget for a customer:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Billing**.
1. Select **Azure spending (NCE)** from the task menu on the left side.
1. In the **Customers** section, choose **Manage budget**.
1. In the side panel, search for the customer names for whom you want to update a budget.
1. Update the budget amount for each customer.
1. Select **Submit**.

To remove the monthly budget for your customers:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Billing**.
1. Select **Azure spending (NCE)** from the task menu on the left side.
1. In the **Customers** section, choose **Manage budget**.
1. In the side panel, search for the customer names for whom you want to remove a budget.
1. Clear the budget field for the customer.
1. Select **Submit**.

To monitor your customers’ Azure expenses and monthly budgets:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Billing**.
1. Select **Azure spending (NCE)** from the task menu on the left side.
1. In the **Customers** section, review the customers’ monthly budgets, current estimates and percentage of budget used so far.

> [!IMPORTANT] 
> The estimated amounts are typically 24 hours behind the current usage. It can occasionally be longer, depending on certain limitations.

:::image type="content" source="media/azure-plan-billing/azure-spending-budget.png"  alt-text="Screenshot shows a list of customers set up with Azure spending budgets in Partner Center." lightbox="media/azure-plan-billing/azure-spending.png":::

## Notifications for budget limits

Keep control of your Azure bill by setting up email alerts that let you know when your customers’ monthly spending is approaching their budget limit. With this feature, you’ll be notified **every 7 days** when customers **spend 80% or more** of their monthly budget. This way, you can keep track of their spending and take steps to make sure they don’t go over budget. To configure email notifications:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select the **Notifications** (bell) icon.

2. Select **My preferences**.

3. Configure a preferred email address if you haven’t.

4. Configure the preferred language for the notification.

5. Select all of the boxes in the **Billing** workspace under **Notification preferences** section.

> [!NOTE]
> **No notification** will be sent once the budget **exceeds 100%.**

## Itemized costs by service

You can view itemized costs (and estimated usage) by service for usage-based subscriptions:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Select the customer’s **Company name**.

3. On the customer’s **Subscriptions** page, under **Usage-based subscriptions**, select the name of the **Subscription**.

4. On the subscription’s page, you can review the **Itemized costs** by service, and the **Estimated usage** for the current month.

## Next steps

- [New commerce experience in CSP - Azure billing](azure-plan-billing.md)
