---
title: Discover marketplace margins
ms.topic: how-to
ms.date: 07/31/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: As a CSP partner, learn how to use Partner Center to discover margins configured by independent software vendors (ISVs).
author: migolova
ms.author: migolova
---

# Marketplace margins (ISV to Partner private offers)

**Appropriate roles:** Global admin | Billing admin | Admin agent | Sales agent | Helpdesk agent

A private offer enables an ISV publisher to provide a margin on their published solution to incentivize you to sell that solution to their customers.

As a CSP partner, you might have an existing relationship with some independent software vendors (ISVs) who want to extend a private offer to you.

If you discover a solution that you'd like to resell to your customers that was published by an ISV who you don't have an existing relationship with, you can reach out to the ISV to ask whether they're willing to extend a private offer margin to you.

The ISV publisher's contact information can be found by selecting the desired solution from the Partner Center **Marketplace** page in the **Pricing** workspace.

## Understand private offer margins

When an ISV publisher creates a private offer, they can configure it as:

- A percentage discount applied to the original price of a solution
 \- or \-
- A custom price that overrides the original price of the solution

An ISV publisher might choose to extend a private offer on purchases made for all your customers or for a subset of your customers.

When an ISV publisher creates a private offer, they must configure start and end dates on the margin they extend to you for their solution. Start and end dates are listed on the **Margins** page in the **Pricing** workspace. Margins only apply to purchases made within that time frame.

- If you renew a subscription to a product within the private offer start and end dates, the margin is applied to the renewal.
- If you renew a subscription after the margin end date, the margin isn't applied to the renewal.

Some products are priced per-user. If you increase the number of seats/users for those offers during the private offer time frame:

- The discount for the license-based portion of the charges is retained until the end of the subscription.
- The margin applied to consumption isn't retained after the margin end date.

Reach out to the ISV publisher if you would like them to extend the margin period.

## View private offer margins in Partner Center

To discover margins extended to you by ISV publishers, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Pricing**.
2. Select **Margins**.
  
   **If the ISV:**

   - Extended a private offer margin to you, you'll see it listed there.
   - Specified the customers for whom the margin is applicable, you'll see the customer information in the **Customer name** and **Customer ID** columns.
   - Configured the margin to be available to all your customers, then you'll see **All customers** listed in those columns.
   - Configured the private offer as a percentage discount, you'll see it listed in the **Margin** column.
   - Configured the private offer as a custom price, you'll see a **Custom pricing** link in the **Margin** column. Selecting **Custom pricing** opens a panel that shows more detail.

3. You can also select **Download CSV** at the top of the page to download the margins data in a comma delimited format.

Margins data can also be retrieved using an API. For more information, see [Get margins](/partner-center/develop/get-margins) and [Download margins](/partner-center/develop/download-margins).

## Understand pricing for products with margins

The **Margins** page doesn't have information about the original pricing of the offers listed. To view the original pricing, go to [Partner Center Price lists](https://partner.microsoft.com/dashboard/pricing/pricelist) and scroll down to the **Marketplace** section.

The **Marketplace** price list is shared across all CSP partners and has retail pricing. You can apply the percentage discount listed on the **Margins** page to the retail price of a product that you want to purchase to understand the final price of the item before purchasing it.

## Purchase products with private offer margins

Any margin extended to you by an ISV publisher is automatically applied when you purchase the product for your customer through Partner Center or deploy the product from the Microsoft Azure portal. No other steps are necessary to receive the discount.

You can't opt out of a margin after an ISV extends it to you.

## Understand billing for products with private offer margins

To understand the billed amount after you've purchased a product with a private offer margin, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Billing**.
2. In the **Billing history** section, select the **Recurring and one-time purchases** pivot.
3. Select the Reconciliation file link to download the file.

Use the following information in the reconciliation file to understand whether a private offer margin was applied to the transaction:

- **UnitPrice** shows the original price set by the ISV.
- **EffectiveUnitPrice** shows the price after a margin is applied.
- **PriceAdjustmentDescription** displays *Private offer margin applied* if a margin was applied on that purchase.

To learn more, see [Billing for marketplace offers](./csp-commercial-marketplace-billing.md) .

## Private offer margins and indirect resellers

Margins are made available only to partners billed by Microsoft. These include transacting partners such as indirect providers and direct-bill partners.

An ISV can't extend a margin to an indirect reseller, but they can provide a margin to an indirect provider. The indirect provider may then decide to pass the discount along to their indirect reseller (though they aren't required to do so).

## Next steps

- [Overview of marketplace offers](./csp-commercial-marketplace-overview.md)
- [Purchase marketplace offers](./csp-commercial-marketplace-purchase.md)
- [Billing for marketplace offers](./csp-commercial-marketplace-billing.md)
