---
title: Partner offers in the CSP program
ms.topic: article
ms.date: 06/30/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: As a CSP program partner, learn about the growing catalog of Microsoft cloud services and offers you can sell to customers.
author: migolova
ms.author: migolova
---

# Overview of partner offers in the CSP program

**Appropriate roles**: Admin agent | Global admin | Sales agent

As a partner in the Cloud Solution Provider (CSP) program, you have a growing catalog of offers available to you. You can sell the full range of [Microsoft cloud services](https://partner.microsoft.com/cloud-solution-provider/products-and-services) and various other offers that change frequently.

To see the CSP offers for the current month:

- Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select the **Pricing** workspace.

Not yet enrolled in the Cloud Solution Provider program? Go to [Cloud Solution Provider](https://partner.microsoft.com/cloud-solution-provider) for information about how to enroll.

## What you can sell through CSP

You can sell the following types of products and services to your CSP customers:

- [Azure reservations](#azure-reservations)
- [Software](#software)
- [Online services](#online-services)
- [Software as a Service (SaaS) and other Azure Marketplace products](#software-as-a-service-saas-and-other-azure-marketplace-products)

### Azure reservations

   Customers can reserve space in advance on Azure virtual machines for a one-year or a three-year term.

   For more information, see [Sell Microsoft Azure Reserved VM Instances](azure-reservations.md).

### Software

   Customers can buy software subscriptions (to Windows Server and SQL Server, for a one-year or a three-year term, to run on Azure reserved VM instances).

   For more information, see [Sell software subscriptions through CSP](csp-software-subscriptions.md).

### Online services

*Online services* are purchased as *subscriptions*.

To make it easier for you to order multiple types of products in one place, we've integrated the "add subscription" task into the "add products" task.

For more information, see [Customer subscriptions](customer-subscriptions.md).

New commerce experience offers differ from the *traditional* online service subscriptions in several ways. For more information about these new commerce experiences, see [new commerce experiences overview](new-commerce-license-based.md).

### Software as a Service (SaaS) and other Azure Marketplace products

You can sell subscriptions to SaaS products from independent software vendors (ISVs).

To see only SaaS offers in **Online services**, use the filters to set **Publisher** to **Partner**. Doing so shows all the SaaS offers that can be purchased for that customer.

You can also find information about these products on the [Azure Marketplace](https://azuremarketplace.microsoft.com/marketplace) page.

> [!NOTE]
> This page also includes information about other types of products that must be purchased from the Azure portal, not Partner Center.

For more information, see [Overview of the CSP commercial marketplace](CSP-commercial-marketplace-overview.md)

## Add products page details

The following table identifies each of the new areas on the **Add products** page.

|New area                                                   | What it is   |
|-------------------------------------------------------------------------------------------------------------------------------------------------------|---|
|Add products   | Includes all types of products available for you to sell to your customers.    |
| Product categories  | Azure, Online services, Software <br> Select the type of product you're interested in to display only those products.  |
| Segment                                    | Identifies the general type of business that you want to sell to, for example commercial or government.  |
| Publisher                                    | Select which types of products you want to see—apps created by Microsoft or apps created by third-party publishers.  |
| Billing type                                                  | Identifies whether the product is billed by number of licenses or by usage.            |
| Category                                                 |  Identifies the type of business the product supports and whether it offers a trial version. |
| View SKU—View product  | Toggles between the **SKU** and **Product** pages. <br> The **Products** page lists each product individually. <br>The **SKU** page lists product groups.  |

## Buy CSP offers

> [!NOTE]
> To buy a CSP offer, it must be available in both your tenant country/region and in your customer's tenant country/region.
>
> For example, if your tenant is located in Slovakia and the customer's tenant is in Germany, you can't sell Dynamics 365 Business Central Premium to that customer, because that offer isn't available in Slovakia.

To buy products and services on behalf of your CSP customers, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Select the customer you want to buy from, select the down arrow at the end of the customer's row to expand the customer's record, and then select **Add products**.

   At this point, you're creating an order. An order can include several items of different types, but they must all be for the same customer.

3. On the **Add products** page, select from **Azure**, **Online services**, or **Software**.

4. Fine-tune the available filters to more easily find the products you're looking for.

   To see the full list of what's available, set applicable filters to **any**.

5. Select the product the customer wants, enter the quantity, and then select **Add to cart**.

6. Repeat steps 4 and 5 until you've added all the items that you want to your cart.

7. Select **Review**.

8. On the **Review your orders** page, verify or change the products and the quantity, and then select **Buy**.

   The details of your order, including your order number, are displayed on the next page.

9. Select **Done** to go to your **Order history** page.
## View a customer's order history

To view a customer's order history:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. On the **Customers** page, find the customer whose order history you want to view.

3. Select the down arrow to expand the customer's record.

4. Choose **View orders** to display the customer's order history.

## Rules for special segments

Some license-based offers can only be purchased under certain conditions.

Special segment offers include:

- Education
- Nonprofit
- Government Community Cloud (GCC) offers.

To learn more about purchase conditions for these segments, see [Purchase rules for special segments](get-special-pricing-for-offers.md#purchase-rules-for-special-segments).

## Troubleshooting catalog purchases

There might be various reasons why you can't find an offer you're looking for in the catalog. Here are some things to check if you can't find the offer you expect.

- **Verify that your customer is qualified**. Many offers require special qualifications to be sold to customers. These special segments include Education, Nonprofit, and Government Community Cloud (GCC). If, for example, you're trying to purchase Education for a customer who isn't qualified, you won't see those offers in the catalog.

  Before logging an issue, first verify that the customer's qualifications are set correctly.
  
  You can check qualifications by selecting the customer from the customer list and viewing the account. The account will have a Special Qualification set if applicable.  
  
  For more information on qualifying your customers, see the [special segments documentation](get-special-pricing-for-offers.md).

- **Decide whether you are trying to purchase an Add-on or a Base-offer**. Many of the license-based services such as Microsoft 365 and Dynamics 365 enable both catalog purchases of the Base offers and Add-ons. New commerce license-based purchased enable add-ons to be purchased from the catalog. Older versions of license-based add-ons required them to be applied to the base offer on the manage subscriptions page.

- **Verify that the products are available in your market**. Many products and services are configured to be sold only to customers in specific countries/regions. You can find the list of supported countries/regions in the various price list or offer matrix files. License-based services supported countries/regions are in the Offer List Matrix on the pricing and offers page.

- **Verify that the offers are available in the price list**. The offers that are available can change from month to month. If you can't find an offer in the catalog, verify that it's available in the current price lists on the [Pricing and offers](pricing-and-offers.md) page.

### Recommended documents related to purchasing items in Partner Center

- [Pricing and offers in Partner Center](pricing-and-offers.md)
- [Overview of partner offers in the Cloud Solution Provider program](csp-offers.md)
- [How to sell offers to education customers and create an education customer](sell-to-education-customers.md)
- [Sell to specialized industries like education, non-profit, and government users](get-special-pricing-for-offers.md)
- [Purchase rules for special segments](get-special-pricing-for-offers.md#purchase-rules-for-special-segments)

## Next steps

- [Billing basics](billing-basics.md).
- [Purchase the Azure plan](purchase-azure-plan.md).
