---
title: Move customers from current Azure offers to Azure plan
ms.topic: how-to
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Learn how CSP partners can use Partner Center to move customers from existing CSP Azure offers to Azure services under the Azure plan.
author: brentserbus
ms.author: brserbus
ms.date: 1/11/2023

---

# Transition customers to Azure plan from existing CSP Azure offers

**Applies to**: Partner Center

**Appropriate roles**: Admin agent | Billing admin | Global admin | Helpdesk agent | Sales agent | User management admin

This article explains how you can use Partner Center to move customers from existing CSP Azure offers to Azure services under the Azure plan.

- Indirect providers and direct-bill partners can transition to the new commerce experience available in the Microsoft Cloud Service Provider Program (CSP) for Azure.

- Indirect resellers must work through their indirect providers.

Customers will have a streamlined way to buy cloud services, whether purchasing from partners, from Microsoft sellers, or directly on the web.

This transition capability is only for customers transitioning to the new commerce experience for Azure and who have signed the Microsoft Customer Agreement. It isn't for other offers in CSP such as Microsoft 365 or Dynamics 365.

## Transition existing CSP offers to an Azure plan

You can transition a customer from their existing CSP Azure offers to Azure services under the Azure plan in the new commerce experience in the CSP program from within Partner Center.

### Prerequisites

- The partner and customer must have an established reseller relationship through Partner Center.
- The customer must have signed the Microsoft Customer Agreement.

**The transition workflow automates the following prerequisites**:

- Purchase of Azure plans
- One plan per customer in Direct CSP scenarios
- One plan per reseller

   For an example, a partner has purchased two Microsoft Azure offers and has included two distinct POR in the purchase. In this case, the transition the workflow  automatically purchases two Azure plans (one per reseller) and maps the respective Azure subscriptions under the Azure plans.

To transition existing CSP offers to an Azure plan, use the following steps:

1. In Partner Center, select the Azure plan for your customer.

2. Select **Transition billing to Azure plan**.

   :::image type="content" source="media/azure-plan-transition/usage-based-subs-report.png" lightbox="media/azure-plan-transition/usage-based-subs-report.png" alt-text="Screenshot showing usage-based subscriptions report information with a selectable option called: Transition Azure subscription billing to Azure plan.":::

3. Select **Continue**.

   :::image type="content" source="media/azure-plan-transition/transition-to-azure-plan-dialog.png" lightbox="media/azure-plan-transition/transition-to-azure-plan-dialog.png" alt-text="Screenshot of a dialog box in Partner Center titled Transition to Azure plan with implications to read about the transition and two options to select, Continue or Cancel.":::

   Your customer is transitioned to the Azure plan.

   After your purchase of Azure plans, the system maps the Azure subscriptions to the Azure plans.

   Progress can be viewed in the Azure portal and in Partner center.
  
   **Note:** After a partner transitions to Azure plan, when they call the Get Subscriptions API, they get only the Azure plan as part of the subscriptions response, not the individual Azure subscriptions under the Azure plan.

4. Return to your customer's Partner Center **Subscriptions** page to update their budget limit using their local currency.

   :::image type="content" source="media/azure-plan-transition/budget-limit.png" lightbox="media/azure-plan-transition/budget-limit.png" alt-text= "Screenshot of the Subscriptions page with budget limits set in local currency for a billing period.":::

   > [!NOTE]
   > The budget you set in Partner Center doesn't carry over to the Azure portal. You should also set the budget and alert in the Azure portal.

   When you move to the Azure plan, you can no longer purchase Azure subscriptions for this customer. You create the subscriptions under the Azure plan in the Azure portal.

   > [!NOTE]
   > All Azure subscriptions purchased through RBAC under the Azure plan are priced and billed in local currency. Foreign exchange rates aren't used.

### Track your transition details

Follow the transition progress in the Azure portal and in Partner Center.

:::image type="content" source="media/azure-plan-transition/transition-details.png" lightbox="media/azure-plan-transition/transition-details.png" alt-text="Screenshot of a table of transition details per subscription, including subscription ID, transition date, and transition status.":::

### Effects on billing

Transitioning a customer from an existing Cloud Service Provider (CSP) Azure offer has following effects on billing:

- You're billed on your existing CSP invoice for all usage up to the point of exiting the original CSP Azure subscription.

- If you had admin access rights to the CSP subscription, you'll continue to have access when that subscription is migrated.

To learn about transitioning direct Enterprise Agreements to CSP and Server and Cloud enrollments to Azure services, see [Get billing ownership of Azure subscriptions for Microsoft Partner Agreement](/azure/billing/mpa-request-ownership)

### Audit log

To reconcile billing, use the following steps:

- View your history of "Microsoft Azure" (0145P) subscriptions on the **Subscriptions** page.

"Microsoft Azure" (0145P) subscription has two parts:

- Azure subscription (entitlement)
- Commerce subscription

When the transition is complete:

- The Azure subscription is moved under the new Azure plan
- The commerce subscription is suspended so that no further usage is reported.

> [!NOTE]
> When a Microsoft Azure (0145P) subscription is purchased in CSP, both the commerce subscription and the Azure subscription (entitlement) have the same value. Only in the case of billing ownership changes or transfers do the values differ.

### Transition issues

If an issue occurs during transition, you're updated in the transition workflow. There won't be disturbances to Azure usage.

## Next steps

- [Manage subscriptions and resources under the Azure plan](azure-plan-manage.md)

- [Partner earned credit - overview](partner-earned-credit.md)
