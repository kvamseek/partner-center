---
title: Azure credit offer balance
ms.topic: article
ms.date: 7/27/2022
description: Learn where to find the Azure credit offer balance.
ms.service: partner-dashboard
ms.subservice: partnercenter-billing
author: khakiali
ms.author: alikhaki
---

# Azure credit offer balance

**Appropriate roles**: Admin agent | Billing admin | Global admin

This article shows you where to find your customers’ Azure credit offer balance.

## Find the Azure credit offer balance

Follow these steps to see the Azure credit offer (ACO) balance for your customers:

1. Within Microsoft Partner Center, navigate to the **Billing** workspace.

   :::image type="content" source="media/billing-workspace.png" alt-text="Screenshot of the Partner Center Billing Workspace.":::

2. Select the **Billing history** left navigation tab --> "**Recurring and one-time purchases USD**" tab. You can view the Azure Credit Balance by clicking on the "**View your Azure credit balance**" link. This will download a CSV file with the ACO balances for all customers.

   :::image type="content" source="media/azure-credit-balance.png" alt-text="Screenshot of the Azure credit balance.":::

The.csv file has information about ACO balances for eligible customers, such as:

|Attribute| Description|
|----------|-------------|
|PartnerID|Partner’s tenant ID
|CustomerID|Customer’s tenant ID
|InvoiceMonth|Invoice month or billing period
|CreditName| Credit’s name: “ACO”
|CreditAmount|Total amount of credit that has been used since the credit was given
|Status|Credit Credit status (active/expired)
|BalanceAmount|Credit balance at the end of the billing period
|CurrencyCode|Currency of credit
|AgreementID|ACO agreement ID
|EffectiveDate|Credit start date
|ExpiryDate| Credit end date

> [!TIP]
>
> - To find the amount given as credit in a specific month, subtract the previous month’s credit amount from the current month’s credit amount. For example, if your credit limit is $1,000 and you used $500 of credit last month and $200 of credit this month, your total credit used so far is $700. The `CreditAmount` attribute of the Credit Balance report will show up as $700. Therefore, the credit given this month is $200 ($700 - $500).
> - The “Azure Credit” text in the `CreditReasonCode` attribute of the invoice reconciliation data indicates the transaction that used ACO to offset the charges.
> 

> [!NOTE]
> The Credit Balance report may show changes to the credit amount used during the current billing month, but you shouldn’t compare it to the open-period estimates because the final credit adjustment only happens at the end of the billing month.
>
>  

> [!IMPORTANT]
> Azure Credit Offer (ACO) and Partner Earned Credit (PEC) can’t be applied together for the same resource usage. ACO is utilized first, and once it’s fully used up, PEC is applied for any remaining usage.
>
> 
## Next steps

- [Understand your bill and reconciliation file](read-your-bill.md)
- [Common billing scenarios for CSP program partners](common-billing-scenarios.md)
- [Change billing frequency](common-billing-scenarios.md)
- [Customer order history](csp-offers.md)
- [Pricing and offers](pricing-and-offers.md)
