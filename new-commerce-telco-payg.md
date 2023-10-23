---
title: New commerce telco pay-as-you-go
ms.topic: article
ms.date: 06/30/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Learn about new commerce experiences for purchasing offers that enable pay-as-you-go overage.
author: migolova
ms.author: migolova
---

# New commerce overage for telco pay-as-you-go

**Appropriate roles**: Admin agent | Sales agent | Global admin

In traditional license-based scenarios, there wasn't a way to enable service usage beyond monthly limits. Customers needing more than 120 minutes needed to purchase communication credits, or *comm credits*, themselves directly from Microsoft. These communication credits weren't offered in Partner Center. Partners can now enable overage capabilities for those services that allow it.

> [!NOTE]
> The new commerce experiences for license-based services include many new capabilities and are available to all Cloud Solution Provider (CSPs). For more information, see [new commerce experiences overview](new-commerce-license-based.md).

## Using new commerce telco pay-as-you-go

To use overage services, identify which are in the price list tags column as *IncludeOverage*.

Partners can identify which product SKUs include overage capabilities by doing the following:

- Viewing the [Partner Center catalog product SKUs](https://partner.microsoft.com/dashboard/pricing/pricelist)
- Filtering the new commerce price list by **includesOverage** in the tags column

You can purchase the offers and the system configures an overage subscription that only collects costs when customers exceed the allocated monthly calling minutes that come with the offer purchased.

Overage can be enabled by accessing **Manage Overage** in the **Manage Subscriptions** page. Manage Overage enables you to activate and assign which Azure subscription the overage charges will flow to. At any time, you can turn off overage by setting the consumption subscription to *None*.

> [!NOTE]
> **Manage Overage** requires having the ability to create an Azure plan. By default, partners cannot provision Azure plans using their sandbox accounts. Partners who need to do so with their sandbox account must apply for access. More information can be found in the [Azure plan sandbox documentation](/partner-center/develop/test-and-debug#azure-plan).

**Manage Overage** is only accessible if the partner has subscriptions that enable overage. When monthly overage charges accrue, they are shown in the partner's reconciliation file.

Partners can track overage usage by visiting the Microsoft Cost Management capabilities in the Azure portal.

## Pricing and margins

Telco pay-as-you-go is billed based on monthly usage when the customer uses the number of calling minutes for the plan they have. Partners can discover and download the pricing for these charges at the [Microsoft Teams Phone and Calling site](https://www.microsoft.com/microsoft-teams/voice-calling). Partners can go to the **See rates for where you want to call** option on the page to download and view the rates for various calling plans.

The pricing and calling plan overage charges aren't reduced for Cloud Solution Provider (CSP) audiences. There are no CSP discounts or margins for overage charges.

## Important details about overage

- Purchasing a license-based product SKU that includes overage capabilities will only purchase the license-based product. Partners will need to take another step to turn on overage by going to the subscription management page and clicking **Manage overage**.
- Only Admin Agents for the transacting partner can enable overage.
- Enabling overage will create a no-cost Azure plan and an associated default Azure subscription, **Subscription 1**, specifically for overage consumption. If the Azure plan already exists, enabling overage will create the new subscription under the existing Azure plan. Partners can always view or reassign overage to other subscriptions in **Manage overage**. Customers that aren't yet on an Azure plan will need to transition to an Azure plan before they can enable overage.
- Telco pay-as-you-go charges will **not receive partner earned credit (PEC)**. You should expect to be charged and billed the amounts in the [Microsoft Teams Phone and Calling site](https://www.microsoft.com/microsoft-teams/voice-calling).

Overage settings are per service per customer. Only one overage subscription can be assigned at a time. If a partner purchases E5 with calling plans for a new customer, that partner will have overage assigned to their consumption subscription. If a second partner purchases another copy of E5 with calling plans, the system will respect the first partner's purchase and assignment. Partners can always **Manage overage** from the subscriptions page to disable or turn it off by assigning overage to **None**.

If overage settings need to be changed from one partner to another, the three parties involved must first agree. After they agree, the existing partner can set overage to **None** to enable the other partner to set overage to their subscription.

## Telco pay-as-you-go APIs

- [SKU properties](/partner-center/develop/product-resources#sku) include a *consumptionType* property to help the PartnerIDentify whether a SKU enables overage
- [Get overage](/partner-center/develop/get-subscription-overage) to understand if any overage is currently set up for your customer
- [Update overage](/partner-center/develop/update-subscription-overage) to update customer's overage to an Azure subscription or to set it to *None*

## Next steps

- [New commerce license based overview](new-commerce-license-based.md)
