---
title: Save with Azure savings plans
description: As a Cloud Solution Provider, you can use the Azure portal to acquire and manage Azure savings plans for customers.
ms.topic: article
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
author: migolova
ms.author: migolova
ms.date: 06/15/2023
---

# As a Cloud Solution Provider, you can acquire Azure savings plans through Partner Center

**Appropriate roles**: Admin agent | Global admin | Helpdesk agent | User management admin

As of June 2023, partners can purchase an Azure savings plan (ASP) through Partner Center. Previously, Azure savings plan was only supported for purchase through the Azure portal. Partners can now purchase Azure savings plan through Partner Center portal, APIs, or they can continue to use the Azure portal.

To purchase Azure savings plan using the Partner Center APIs, see [Purchase Azure savings plans](developer/azure-purchase-savings-plan.md).

> [!NOTE]
> Currently, sales agents will not be able to purchase Azure savings plan.

## What are Azure savings plans?

Partners in the CSP program can offer their customers Microsoft Azure savings plans to gain significant savings. Azure savings plans save you money when you have consistent usage of Azure compute resources. An Azure savings plan helps you save money by allowing you to commit to a fixed hourly spend on compute services for one-year or three-year terms. A savings plan can significantly reduce your resource costs by up to 65% from pay-as-you-go prices. Discount rates per meter vary by commitment term (one-year or three-year), not commitment amount.

Azure savings plan discounts are applied to the estimated retail prices (ERPs). Savings from a savings plan are applied instead of the partner-earned credit. These discount types aren't additive, if a partner has a savings plan the savings plan discounts will apply. Partners that don't have a savings plan but meet the requirements for partner earned credit, continue to get the partner-earned credits.

## Pricing for Azure savings plans

You can find pricing using the following resources:

- [Azure pricing calculator](https://azure.microsoft.com/pricing/calculator/)
- [Azure pricing page](https://azure.microsoft.com/pricing/)
- [Azure retail prices REST API](/rest/api/cost-management/retail-prices/azure-retail-prices)

## Discover and purchase an Azure savings plan in Partner Center

To purchase an Azure savings plan for a customer in Partner Center, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.
1. Choose a customer and then select **Subscriptions**.
1. Select **New Subscription** and then the **Azure** tab.
1. From the **Type** dropdown, select **Azure savings plans**.
1. Select **Add to cart** for your desired product SKU.
1. Once you're ready to continue the checkout flow, select **Review** from the right-side column.
1. After reviewing, select **Buy** to complete the purchase.

> [!NOTE]
> To be able to discover Azure savings plan and add the Product SKUs to your cart, the customer must already have an Azure Plan.

### Review your Azure savings plan purchase  

When reviewing your cart for checkout, several attributes of the Azure saving plan can be edited, including billing frequency, scope, Azure plan, and hourly commitment in USD. Azure saving plans are available with a one-year or three-year term; the term length is fixed per product SKU and can't be changed on the **Review** page. One-time and monthly billing frequencies are available for each term.

The following scope options are available for Azure saving plans purchased in Partner Center:

- **Single scope** - Applies the savings plan benefit to the eligible resources in the selected subscription. If **Single** is selected as the scope, you're prompted to then select a specific Azure subscription.
- **Shared scope** - Applies the savings plan benefit to eligible resources within subscriptions that are in the billing context. If a subscription was moved to a different billing context, the benefit longer applies to this subscription and continues to apply to other subscriptions in the billing context.

While applying savings plan benefits to your usage, Azure processes savings plans in the following order:

1. Savings plans with a single resource group scope; this scope can be selected for purchases made in Azure portal.
1. Savings plans with a single subscription scope.
1. Savings plans scoped to a management group; this scope can be selected for purchases made in the Azure portal.
1. Savings plans with a shared scope (multiple subscriptions), described previously.

An Azure plan is required for purchase of an Azure savings plan. During **Review**, you're prompted to select an Azure plan to nest your savings plan under. For indirect partners, the associated reseller is inherited from the selected Azure plan.

The **Hourly commitment** field can also be edited. The input value represents the monetary amount available through the Azure savings plan each hour.

### Secondary deal review and Azure savings plan

With Microsoft's commitment to anticorruption, orders might be flagged and require additional information from partners. When a deal is selected for review, it doesn't necessarily mean that there are any inherent issues with the deal but rather, a combination of multiple risk attributes requires Microsoft to take a deeper look at the deal specifics.

If an order containing an Azure savings plan is flagged for review and requires a purchase order (PO) upload, the partner must submit and receive approval within 90 days of the order being made. Any purchase orders that aren't submitted or can't be reviewed due to delayed submission within 90 days will be rejected, and a new order must be placed.

Order status can be checked via the **Order history** page in Partner Center. Via APIs, partners can [get a list of pending PO uploads](developer/pending-po-upload.md) and [submit PO records](developer/attaching-purchase-order-and-completing-po-details.md). You can find the steps for uploading the document in the [Secondary deal review training deck](https://partner.microsoft.com/resources/detail/secondary-review-overview-pdf).

For more information on the secondary review process, what to upload for the end customer purchase commitment, or the information required in this form, see the training at the [Secondary Review Desk collection](https://partner.microsoft.com/resources/collection/secondary-review-desk-collection#/).

### Enable customers to buy Azure savings plan through Azure portal

A partner may enable a customer to self-serve in the Azure portal but will need to give the customer permission to buy Azure savings plan on the specific Azure subscription the partner has purchased for the customer. Permissions are off by default. For more information on how to enable customer permissions, see [Give customers permissions to buy their own products and services](give-customers-permission.md).

Even if the customer buys the savings plan themselves, if they use the Azure subscription that a CSP has purchased, the billing happens through the CSP.

## View and manage Azure savings plan

Partners can view Azure savings plans purchased in Partner Center. Like reservation instances, partners can continue to use the [Azure portal](https://portal.azure.com/) for postpurchase management actions. For more information on managing Azure savings plan, see [Manage Azure savings plans - Microsoft Cost Management](/azure/cost-management-billing/savings-plan/manage-savings-plan). The ability to transfer Azure savings plans from one partner to another isn't currently supported in Partner Center.

To view Azure savings plans purchased in Partner Center, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.
1. Choose a customer and then select **Subscriptions**.
1. Select the **Azure** tab.
1. From the **Category** dropdown, select **Azure savings plans**.
1. Select an Azure savings plan name to view more subscription details.
1. Under **Action**, select **Manage** to navigate to Azure portal for postpurchase management actions.  

## Invoice and reconciliation for Azure savings plan

Partners can visit [Reconciling and billing of savings plan in CSP](azure-savings.md) to understand how the savings are reflected in their monthly billing reconciliation files.

## Incentives for Azure savings plan

At the time of launch, partners who qualify for Azure Partner incentives receive an incentive based on consumption. This is similar to what's currently offered for reserved instance.

> [!NOTE]
> This is the offer at the time of launch and might be subject to change.

## Sandbox for Azure savings plan

Transacting in Sandbox is available for Azure savings plans. For customers who already have an Azure plan, Azure savings plans are discoverable in the **Browse** view of the catalog.

## Azure savings plan resources

- [Azure savings plan for compute collection](https://partner.microsoft.com/resources/collection/azure-savings-plan-for-compute#/)
- [Overview of Azure savings plans](https://go.microsoft.com/fwlink/?linkid=2211952)
- [Reconciling and billing of savings plan in CSP](azure-savings.md)
- [What are Azure savings plans for compute?](https://go.microsoft.com/fwlink/?linkid=2211734)
- [Azure saving plan cancellation policies](https://go.microsoft.com/fwlink/?linkid=2212017)
- [How saving plan discounts are applied](https://go.microsoft.com/fwlink/?linkid=2211954)
- [Manage Azure savings plans](https://go.microsoft.com/fwlink/?linkid=2211843)
- [Get pricing and rates for Azure meters](https://go.microsoft.com/fwlink/?linkid=2211735)
