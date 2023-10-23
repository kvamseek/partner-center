---
title: Partner earned credit for managed services
ms.topic: article
ms.date: 04/13/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-billing
description: Learn how Microsoft partner earned credit (PEC) for managed services is calculated and paid, and how to ensure that you're eligible.
author: sourishdeb
ms.author: sodeb
---

# How partner earned credit is calculated and paid

**Appropriate roles**: Global admin | User management admin | Admin agent | Billing admin | Sales agent

Partner earned credit (PEC) for managed services recognizes and rewards partners who own IT operational control and management of some or all of a customers' Azure environment.

By default, as a Cloud Solution Provider (CSP) partner, you're granted the necessary access rights to your customer's subscription. Those access rights enable you to perform operational management and control of the resources on the subscription. Other ways in which customers can provision access for transacting partners are described in the following section.

The monthly invoice amount is the net partner earned credit. You can see PEC details in your monthly recon file.

For other ways in which a customer can provision access for the transacting partner, see the following articles:

- [Manage subscriptions and resources under the Azure plan](azure-plan-manage.md)
- [Reinstate admin privileges for Azure CSP subscriptions](reinstate-csp.md)

## Eligibility

To receive partner earned credit (PEC):

- You must have an active Microsoft AI Cloud Partner Program agreement and a valid role-based [access control](azure-roles-perms-pec.md) [(RBAC)](/azure/role-based-access-control/overview) role.

- You must have access permissions, which can be set in three ways:

  - **Admin on behalf of (AOBO)** is the default. When a partner provisions an Azure Plan subscription for a customer, AOBO is set in the form of a *foreign principal* who inherits owner permissions on the Azure subscription. The AOBO permissions mean that a certain group in the CSP Partner Center tenant—*Admin agents*—inherit those permissions.

    For more information about AOBO, see [Delegated admin privileges in Azure AD](./customers-revoke-admin-privileges.md#delegated-admin-privileges-in-azure-ad).

  - **Azure Lighthouse** is an option suitable for partners who are interested in enabling sophisticated cross-tenant management experiences for Azure solutions. Like AOBO, Azure Lighthouse allows groups of users in the (Partner) management tenant to inherit delegated permissions in the customer's Azure subscription. The difference is that Azure Lighthouse enables more granular definition of groups and permission levels than AOBO.

    For more information about Azure Lighthouse, see [Cross-tenant management experiences](/azure/lighthouse/concepts/cross-tenant-management-experience).
  - **Individual user accounts and service principals:** Sometimes working with individual user accounts that have permissions on Azure Subscriptions might be best. These user accounts can be guest user accounts (from any tenant) or user accounts created in the customer tenant or service principals.

    For more information, see [Link your PartnerID to track your impact on delegated resources](/azure/lighthouse/how-to/partner-earned-credit).

- In the case of indirect providers and their indirect resellers, an indirect provider is eligible for PEC if either the indirect provider or the indirect reseller or both have AOBO privileges or an eligible RBAC role.

   For more information about individual user accounts and service principals, see [Reinstate admin privileges for Azure CSP subscriptions](reinstate-csp.md).

- PEC is earned on Azure resource level, resource group or subscription. If a partner has valid access at either the subscription or resource group level, each resource that rolls up to the higher entity earns PEC.

**PEC isn't applicable to:**

- Azure plan reservations
- Products identified as *Third Party* in the **Tags** column of the Azure plan consumption price list
- Products in the Marketplace price list
- [Azure Spot Virtual Machines](/azure/virtual-machines/spot-vms)
- Azure Savings Plans

If you have issues with PEC, see [Troubleshooting partner earned credit](partner-earned-credit-troubleshoot.md).

In addition to the requirements above, PEC is only applicable to services listed in the Azure plan consumption pricing. You can view and export this pricing from the [Azure plan pricing](https://partner.microsoft.com/commerce/sales) page.

For more detailed information, see [Troubleshooting partner earned credit](./partner-earned-credit-troubleshoot.md).

For more information on PEC, see the [Microsoft Cost Management](/azure/cost-management-billing/costs/get-started-partners) page.

For more information on eligibility, see [Roles and permissions required to earn partner earned credit](azure-roles-perms-pec.md).

## Calculation

- Partner earned credit is calculated daily. You're paid for each day that you have PEC-eligible access on each subscription.
- Although PEC details don't appear on your monthly invoice, PEC earnings are factored into the adjusted net charges line in the invoice.
- You can find more PEC details in the [daily usage file](daily-rated-usage-recon-files.md) and in the monthly invoice recon file. All values are in USD, as shown in column **AI**, **PricingCurrency**:

:::image type="content" source="media/advanced-specializations/recon-file.png" alt-text="Screenshot of a Partner Center reconciliation file identifying columns." border="false":::

The following table describes the PEC elements found in the monthly invoice recon file.

| Column | Description |
| --- | --- |
| C | *CustomerName* |
| P | *UnitPrice* |
| AD | *EffectiveUnitPrice* is the price after PEC is applied and the requirements have been met. When PEC is applied, you'll see that the *EffectiveUnitPrice* in column AD is a percentage less than the *UnitPrice* in column P. |
| V | *PriceAdjustmentDescription* This column is blank if no requirements for PEC are met or have the PEC percent that will be applied to *UnitPrice*. However, you may be eligible for additional credits. If so, they'll be listed in this column. Example: *100% Tier 1 Discount*. |

To monitor PEC access, use the following steps:

- **Daily rated usage file** shows where PEC is applied (or *not* applied) on a daily basis.

- **[Azure monitor alerts](azure-plan-manage.md)** monitor changes to persistent privileged access.

The daily rated usage file:

:::image type="content" source="media/advanced-specializations/partner-daily.png" alt-text="Screenshot of a Partner Center daily rated usage file highlighting the effective unit price." border="false":::

## Partner earned credit API

A PEC API is available as part of the Azure API toolset. For information on PowerShell and CLI APIs, see [Link an Azure account to a PartnerID](/azure/cost-management-billing/manage/link-partner-id).

## Microsoft Cost Management and PEC

Microsoft Cost Management (ACM) using Cost Analysis enables you, as a partner, to view the costs that have received the benefit of PEC. For a detailed presentation on ACM, see the [May 2021 CSP Spotlight call](https://commercial_licensing.eventbuilder.com/2021MayCSPSpotlight).

## Use ACM to view your partner earned credit

1. In the [Azure portal](https://portal.azure.com/), sign in to your partner tenant and select **Cost Management + Billing**.

1. Select **Cost management**.

1. Select **Cost analysis**.

   The **Cost analysis** view displays the costs for your billing account for all the services purchased and consumed at the prices that you pay Microsoft.
   :::image type="content" source="media/advanced-specializations/partner-cost.png" alt-text="Screenshot of a cost management cost analysis page." border="false":::

1. In the pivot chart drop-down list, select *PartnerEarnedCreditApplied*.

   - If this value is **True**, the associated cost has the benefit of the partner earned credit.

   - If this value is **False**, the associated cost hasn't met the required eligibility for the credit, or the service purchased isn't eligible for partner earned credit.

> [!NOTE]
> Typically, usage for services takes 8-24 hours to appear in *Cost Management*, and the PEC credits appear within 48 hours of time of access in Microsoft Cost Management.

You can also group by and filter by the **PartnerEarnedCreditApplied** property by using the **Group by** and **Add** filter features. These filters allow you to drill into costs that have PEC and the costs that have no PEC applied.

## How is PEC paid?

PEC earnings are factored into the *adjusted net charges* line in the invoice. The **Total** of the invoice shown below illustrates this. For adjustment details, see the monthly invoice reconciliation file and Azure daily rated usage file.

:::image type="content" source="media/advanced-specializations/invoice.png" alt-text="Screenshot of a Partner Center invoice stating that adjustment details appear on recon and Azure daily usage files." border="false":::

## Next steps

- [Price list for the new commerce experience for Azure in CSP](azure-plan-price-list.md)
- [Manage subscriptions and resources under the Azure plan](azure-plan-manage.md)
- [New commerce experience in CSP - Azure billing](azure-plan-billing.md)
- [Reinstate admin privileges for Azure CSP subscriptions](reinstate-csp.md)
