---
title: How tax policies affect payout for Azure Marketplace
description: Learn how tax policies affect payout for Azure Marketplace.
ms.topic: conceptual
ms.service: partner-dashboard
ms.subservice: partnercenter-payouts
author: deeparamani
ms.author: deramani
ms.reviewer: teruey
ms.date: 04/22/2022
---

# How tax policies affect payout for Azure Marketplace

**Appropriate roles**: Global admin | User management admin | Admin agent

## Introduction

The Microsoft commercial marketplace has global reach. Transactions occur across borders and depending on where the independent software vendor (ISV) and the customer are located, tax implications can vary. Microsoft AppSource and Azure Marketplace use the Partner Center Tax Profile Information to determine the ISV's country/region. To determine the customer's country/region, either use the customer's billing information or, if the customer is in the EU, we use two different pieces of information.

To better understand the following scenarios, refer to the [Tax details](tax-details-marketplace.md) table, which shows whether Microsoft collects and pays taxes on behalf of the publisher or if that responsibility belongs to the publisher.

> [!NOTE]
> All examples sale values and tax percentages in this topic are for illustrative purposes only, not exact figures.

## Publisher Transacts in Microsoft-managed Tax Country/Region

**Scenario A** – Transactions that take place between a publisher and a customer in a [Microsoft-managed tax country/region](tax-details-marketplace.md#microsoft-managed-countriesregions). These transactions will have applicable tax added at the time of sale and Microsoft sends that tax to the applicable country/region. No taxes are withheld from payout and payout calculations are tax exclusive.

See [Scenario D](#foreign-publisher-transacts-with-us-customer) for transactions between a non-US publisher and a US customer.

:::image type="content" source="media/tax-policies/payout-scenario-a.png" alt-text="Shows workflow for payout process scenario A.":::

## Publisher Transacts in Microsoft-managed Tax Country/Region where Marketplace Fee is Taxable Service

**Scenario B** – Transactions that take place between a US-based publisher (as defined by their Partner Center Tax Profile Information) to a customer in a Microsoft-managed tax country/region where the country/region imposes a tax on the Marketplace Fee (a taxable service). In this scenario, the tax on the store service fee is subtracted from the publisher's payout.

:::image type="content" source="media/tax-policies/payout-scenario-b.png" alt-text="Shows workflow for payout process scenario B.":::

## Publisher Transacts in Publisher-managed Tax Country/Region

**Scenario C** – Transactions that take place between a publisher and a customer in a publisher-managed tax country/region that does not impose a withholding tax on customers. Customers pay no tax at the point of sale and it is the publisher's obligation to pay all applicable taxes.

For more information on country/region-specific pricing (for example, to offset upcoming taxation) see [Plans and pricing for commercial marketplace offers](/azure/marketplace/plans-pricing#custom-prices).

:::image type="content" source="media/tax-policies/payout-scenario-c.png" alt-text="Shows workflow for payout process scenario C.":::

## Foreign Publisher Transacts with US Customer

**Scenario D** – All foreign publishers (as defined by their Partner Center Tax Profile Information) in countries/regions without a US treaty (see [Scenario E](#foreign-publisher-with-a-treaty-transacts-with-us-customer)) making a sale to a US-based customer (as defined by their customer account address). US government requires that Microsoft withhold tax on behalf of the publisher. Tax withheld from payout to publisher is calculated based on offer price.

:::image type="content" source="media/tax-policies/payout-scenario-d.png" alt-text="Shows workflow for payout process scenario D.":::

## Foreign publisher with a Treaty Transacts with US customer

**Scenario E** – All foreign publishers (as defined by their Partner Center Tax Profile Information) in countries/regions with a US treaty making a sale to a US-based customer (as defined by their customer account address). US government does not require Microsoft to withhold tax on behalf of the publisher.

:::image type="content" source="media/tax-policies/payout-scenario-e.png" alt-text="Shows workflow for payout process scenario E.":::

## Foreign publisher sells to an EU VAT-registered customer in a Microsoft-managed Country/Region (outside Ireland)

**Scenario F** – All transactions between foreign publishers and EU value-added tax (VAT)-registered customers (outside Ireland) in a Microsoft-Managed Country/Region. The customer does not pay tax on the sale.

:::image type="content" source="media/tax-policies/payout-scenario-f.png" alt-text="Shows workflow for payout process scenario F.":::

## Foreign publisher sells to an EU VAT-registered customer in a Microsoft-managed Country/Region (in Ireland)

**Scenario G** – All transactions between foreign publishers and EU VAT-registered customers (inside Ireland) in a Microsoft-Managed country/region. The customer pays Irish VAT and Microsoft pays this tax to the Irish government.

:::image type="content" source="media/tax-policies/payout-scenario-g.png" alt-text="Shows workflow for payout process scenario G.":::

## Next steps

- [Publisher FAQ](/azure/marketplace/marketplace-faq-publisher-guide)
- [Instructions to create payment and tax profiles](./set-up-your-payout-account.md?context=%2fazure%2fmarketplace%2fcontext%2fcontext#create-a-payment-profile)
