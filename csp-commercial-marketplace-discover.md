---
title: Discover marketplace offers - commercial marketplace
ms.topic: how-to
ms.date: 8/21/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Learn how CSP partners can use Partner Center to view or search the marketplace for SaaS offers or pricing from independent software vendors (ISVs).
author: migolova
ms.author: migolova
---

# Discover marketplace offers

**Appropriate roles:** Global admin | Admin agent

When an independent software vendor (ISV) publishes their product/solution to the Microsoft commercial marketplace, they can choose to make it available for partners in the Cloud Solution Provider (CSP) program. As a CSP partner, you can purchase and resell those solutions (otherwise known as marketplace offers) to your customers to uniquely serve their needs and distinguish your business.

> [!NOTE]
> To get the most from this article, first read [Overview of Partner Center marketplace](./csp-commercial-marketplace-overview.md).

To discover marketplace offers, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Pricing**.
2. Select **Marketplace**.
   By default, you'll see ISV products of all types and categories.
3. Filter by offer type or category. You can search by keywords, offer names, or ISV publisher names.
4. Select an offer from the list. A new page appears with a product **Overview** tab on which you can learn more about the offer. Information on this tab might include:
   - A description of the product or offer
   - More information about the ISV publisher
   - Links to documentation or marketing materials uploaded by the ISV publisher
   - Other possible ISV contacts for customer support, engineering, or a contact for the CSP program

Eligible marketplace offers are also discoverable via API. For more information and guidance, see [Get a list of offers](/partner-center/develop/create-subscription-azure-marketplace-products#get-a-list-of-offers-for-a-market).

If an offer doesn't appear as you expect in Partner Center, it might be because:

- The ISV chose not to sell the product through the CSP program. You might find these products in [the Microsoft commercial marketplace](https://appsource.microsoft.com/marketplace) or [Azure Marketplace,](https://azuremarketplace.microsoft.com/marketplace), but they won't appear in Partner Center marketplace for CSP partners to browse.
- The offer type might not be transactable through Partner Center or Azure portal (for example, Containers or some usage-based offers)
- The offer might not be available for purchase in your region
- The ISV decided to make the offer exclusive to select CSP partners. Learn more about exclusive offers in the following section.

## Exclusive offers

Some marketplace offers might be marked **Exclusive**. These offers are *visible* to all CSP partners but can be *purchased* only by partners selected by the ISV publisher. If an offer isn't marked **Exclusive**, any partner can purchase it.

If you see an offer marked **Exclusive** that you would like to sell to your customers, reach out to the ISV directly, and ask for permission to sell the offer. ISV contact information can be found on the product's **Overview** tab.

## Understand pricing for marketplace offers

To view the latest pricing details for a marketplace offer:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Pricing**.
2. Select **Price lists**.
3. Scroll down to the **Marketplace** section and select the country/region for which you would like to view pricing. **Country/region** represents the country/region your customer is in.
4. Download the **Marketplace pricing** file. This spreadsheet contains the latest pricing information for all the ISV products that are available for you to purchase. This information is updated daily, so you can check it for current prices as often as you choose.

The Marketplace price list can also be retrieved using an API. See [Get a price sheet](/partner/develop/get-a-price-sheet) for guidance.

To learn more about price lists, see [Pricing overview](./pricing-and-offers.md).

## Long-term pricing for marketplace SaaS offers

ISV partners can offer one-month, one-year, two-year, and three-year SaaS offers to CSPs.

Fixed billing plans are available with up-front, yearly, or monthly options.

The options appear in the CSP Marketplace price list as:  

- *Terms*: P1M, P1Y, P2Y, P3Y

- *Billing plans*: Monthly, Annual, Biennial, and Triennial

Partner Center APIs accept these terms and billing plans in the same format as they appear in the price list. For example, if a partner wants to purchase a two-year offer with an up-front payment, they select the term *P2Y* and the billing plan *Biennial*.

## Next steps

[Purchase marketplace offers](./csp-commercial-marketplace-purchase.md)
