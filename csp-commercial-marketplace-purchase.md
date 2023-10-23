---
title: Purchase commercial marketplace offers
ms.topic: how-to
ms.date: 07/31/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: As a CSP partner, learn how to use the Partner Center marketplace to make customer purchases of SaaS offers from independent software vendors (ISVs).
author: migolova
ms.author: migolova
---

# Purchase marketplace offers

**Appropriate roles:** Global admin | Admin agent

**Audience**: CSP partners

As a partner in the Cloud Solution Provider (CSP) program, you can purchase solutions published by independent software vendors (otherwise known as marketplace offers) and resell them to your customers. Offering ISV solutions to your customers and bundling them with Microsoft products enables you to create unique solutions that serve your customers' individual business needs and helps you differentiate your business.

There are two types of offers:

- **License-based** (or entitlement-based) subscriptions, which include Software-as-a-Service (SaaS) applications
- **Usage-based** (or consumption-based) subscriptions, which include offers based on virtual machines, containers or Azure applications.

## How to purchase license-based offers

To purchase a license-based subscription in Partner Center, follow these steps:

1. Sign in to the [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.
2. Select the customer you want to purchase the product for from the customer list.
3. From the customer's **Subscriptions** page, select **Add new**.
4. Select the **Marketplace** tab. The resulting list contains all eligible marketplace SaaS offers.
5. Select the products/subscriptions you want to purchase for your customer.

   Some offers may not always be available. Possible reasons include:

   - The customer already has a subscription to that product and is only allowed one.
   - The customer's subscription might have been suspended. (In this case, you can reactivate the subscription rather than purchase a new one.)
   - The product/subscription may not be available in the customer's billing country or region.
   - The ISV publisher may have chosen not to make the offer available through the CSP program.
   - The ISV publisher may have made the offer exclusive to only certain CSP partners to purchase.
   - The product may not be purchasable through the Partner Center but is available for purchase through the marketplace in the Azure portal.

6. For each product/subscription you want to add, enter the number of licenses (if necessary) and select **Add to cart**.

   Some products may prompt you to select an Azure plan. If your customer doesn't have an existing Azure plan, you can follow these instructions to purchase one: [Purchase an Azure plan](./purchase-azure-plan.md).

7. When you're finished adding subscriptions, select **Review** to review your order.
8. When you're ready to purchase, select **Buy**.

You can also use [Partner Center APIs](/partner-center/develop/create-subscription-azure-marketplace-products) to purchase license-based subscriptions for your customers.

## How to purchase usage-based offers

In contrast to license-based subscriptions, usage-based subscriptions can't be purchased through Partner Center, and must be purchased through the Azure portal. Follow these steps to purchase consumption-based products:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.
2. Select the customer you want to purchase a product for from the customer list.
3. On the **Subscriptions** page under the **Azure** tab, select **Azure plans and subscriptions**, and then select **View all resources on Azure portal**. Sign in with your CSP account. Doing so takes you to your customer's resources in the [Azure Management portal](https://portal.azure.com/#blade/HubsExtension/BrowseAll).
4. In the **All resources** view in the Azure Management portal, select **Create** from the left-hand menu.
5. Select **See more in Marketplace** at the top of the products list.
6. Filter by **Publisher type: Partners** to view only products published by ISVs.
7. Select the product you want to purchase for your customer and follow the prompts to complete the transaction.

Usage-based products aren't available for purchase through Partner Center APIs at this time.

## Next steps

[Manage commercial marketplace offers](./csp-commercial-marketplace-manage.md)
