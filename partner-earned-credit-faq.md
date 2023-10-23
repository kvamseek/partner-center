---
title: Partner earned credit FAQ
ms.topic: article
ms.date: 7/18/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-billing
description: Find answers to frequently asked questions regarding partner earned credit (PEC).
author: sourishdeb
ms.author: sodeb
---

# Frequently asked questions for partner earned credit

Appropriate roles: Global admin | User management admin | Admin agent | Billing admin | Sales agent

Following is a list of frequently asked questions regarding partner earned credit (PEC).

## How much is PEC?

The amount partners earn for PEC will vary (see [Calculation](partner-earned-credit-explanation.md#calculation)). The rate can be found on the price list page within Partner Center.

## What Azure services are eligible for PEC?

PEC is eligible for all services related to the new Azure offer in CSP (Azure plan) except for the following:

- New Azure offer (Azure plan) reservations
- Third-party products identified as Third Party in the Tags column of the Azure plan consumption price list
- Products in the Marketplace price list
- [Azure Spot Virtual Machines](https://partner.microsoft.com/resources/collection/azure-spot-in-csp#/)
- Azure Savings Plans

## Where can I see PEC?

See [Calculation](partner-earned-credit-explanation.md#calculation).

## Where can I find PEC details?

PEC details can be queried by API, [daily recon file](partner-earned-credit-explanation.md#calculation) and [Microsoft Cost Management](partner-earned-credit-explanation.md#microsoft-cost-management-and-pec) by partners directly.

## How can I reconcile my PEC information across the two recon files?

There are two reconciliation files found in Partner Center under Billing that can be used.

- Daily rated usage reconciliation-recent activity (.csv)
- Reconciliation-recent activity (.csv)

To reconcile, the partner can compare the ProductID, SKUID, AvailabilityID fields from these two files for each SubscriptionID.

:::image type="content" source="media/advanced-specializations/partner-billing.png" alt-text="Screenshot of the Partner Center Billing tab highlighting recurring and one-time purchases." border="false":::

## For an Indirect Reseller working with an Indirect Provider, does an Indirect Provider need to add the Indirect Reseller's account as a role-based access control (RBAC) Identity and Access Management (IAM) role to the end customer's subscription in order to utilize ACM?

Yes, the CSP Indirect Provider must enable [RBAC](/azure/role-based-access-control/overview) access to the Indirect Reseller on the Azure subscription.

## What happens if a customer removes a partner's RBAC admin access?

A partner without appropriate RBAC access in CSP still retains the customer's Azure billing relationship and accountability with Microsoft. Although this doesn't affect a partner selling the previous Azure offer in CSP, for the new Azure offer in CSP, the invoiced partner isn't eligible for PEC on their Azure invoice. Partners can achieve partial admin access in CSP by obtaining access through a user account via Directory/Guest access using RBAC or through Azure Lighthouse. For more information, see [Reinstate admin privileges for a customer's Azure CSP subscriptions](reinstate-csp.md).

:::image type="content" source="media/advanced-specializations/permissions.png" lightbox= "media/advanced-specializations/permissions.png" alt-text="Screenshot of the Access control page where you can reinstate admin permissions." border="false":::

## How do I know if I'm earning PEC?

There are several ways a partner can confirm that they have the appropriate access to a customer's Azure resources.

- Review the daily usage file: If a partner is receiving the partner earned credit for Services Managed, then they have admin access. This can be determined by reviewing the unit price and effective unit price within the daily usage file and confirming if a discount is being applied.
- Create an Azure Monitor Alert: You can [create activity log alerts](/azure/azure-monitor/platform/alerts-activity-log) using Azure Monitor to receive notifications when your RBAC access is removed from CSP subscriptions. Learn more at [Partner earned credit overview](./partner-earned-credit.md).

## Why don't I see PEC on the invoice?

PEC is not explicitly called out on the invoice. There is no separate line item to view PEC. However, PEC earnings are factored into the adjusted net charges amount on the invoice. View the calculation and How is PEC paid sections to learn more about where you can view PEC details.

## Next steps

- [Price list for the new commerce experience for Azure in CSP](azure-plan-price-list.md)
- [Manage subscriptions and resources under the Azure plan](azure-plan-manage.md)
- [New commerce experience in CSP - Azure billing](azure-plan-billing.md)
- [Reinstate admin privileges for Azure CSP subscriptions](reinstate-csp.md)
- [Partner earned credit - overview](partner-earned-credit.md)
- [Roles, permissions for partner earned credit](azure-roles-perms-pec.md)
- [Understanding partner earned credit](https://partner.microsoft.com/resources/detail/understanding-partner-earned-credit-pdf)
