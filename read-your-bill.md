---
title: Understand your bill and reconciliation file
ms.topic: article
ms.date: 7/18/2022
description: Learn about your invoice & reconciliation files. Your bill shows Partner Center charges across the program, products, and customers for that monthly period.
ms.service: partner-dashboard
ms.subservice: partnercenter-billing
author: sodeb
ms.author: sodeb
---

# Understand your bill and reconciliation data in the Partner Center

**Appropriate roles**: Global admin | Billing admin | Admin agent

Get a clear understanding of your bill. It’s a complete list of all Partner Center charges for your program, products, and customers.

## Find your reconciliation file

You can find your invoice on the **Billing** in Partner Center.

You can also find your billing history, spending trends, and reconciliation files on this page.

To find your reconciliation file:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Billing**.
2. Select a reconciliation file to view more detailed information.

You can find a link to your most recent reconciliation file at the top of the page under **Account balance as of last invoice date.** 

To download a reconciliation file:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Billing**.
2. Find the invoice in the **Billing history** section by choosing the appropriate year and then selecting the drop-down arrow next to the appropriate billing period.
3. Select the link next to **Reconciliation (.csv)**.

> [!NOTE]
> By default, the Partner Center portal now downloads **billed or closed period** New Commerce reconciliation files asynchronously. 

## Unallocated payments

Occasionally you may see an unallocated payment at your **Billing** workspace. An unallocated payment is a payment you’ve made to Microsoft that you haven’t applied to an invoice.

To view your unallocated payments:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Billing**.
2. In the **Billing history** section, see the **Unallocated payment** section.

Unallocated payments remain unallocated until you assign them to an invoice.

To apply an unallocated amount to an invoice:

- Email `bposcapp@microsoft.com` to tell us which invoice to apply the payment to.

   Be sure to include all of the information that you would use if you were making a payment.

  **Billing history | Unallocated payment** is updated in five to six days.

## Understand reconciliation files

The reconciliation files give a detailed list of your charges. You can use the customer and subscription IDs in the reconciliation files to create invoices for customers. See for more info on reconciliation files. [How to use the reconciliation files](use-the-reconciliation-files.md).

## What products are in the new commerce invoice reconciliation data?

- Azure Pay-As-You-Go
- Azure Reservation 
- Azure Savings Plan 
- License-based products (such as Office, Dynamics, and Power Apps)
- Perpetual software
- Software subscriptions
- Third-party SaaS products

## What products are in the new commerce daily rated usage reconciliation data?
- Azure Pay-As-You-Go
- Azure Reservation (only shows the quantity, not the cost)
- Azure Savings Plan (only shows the quantity, not the cost)

## Map taxes or VAT to your invoice reconciliation data

Here’s how to validate an invoice with taxes or VAT:

1. Add the `Tax` values from your legacy license-based reconciliation data.
2. Add the `TaxAmount` values from your legacy usage-based reconciliation data.
3. Add the `TaxTotal` values from your new commerce reconciliation data.

## Why are some products only in the invoice reconciliation file but not in the daily rated usage file?

The daily rated usage file only includes products charged on a pay-as-you-go, fixed monthly, or one-time price basis depending on daily usage. However, there are other products charged solely on the number of licenses or seats per billing period, independent of usage. These products are charged once per cycle based on the billing plan or payment schedule and do not appear in the daily rated usage data.

> [!NOTE]
> Please note that all products you purchased will appear on your invoice reconciliation file.

## Why does my reconciliation data show a zero tax amount when the corresponding invoice has taxes?

As you may know, in some countries/regions, taxes are calculated based on the total of all transactions or a group of similar transactions, not on each line item. This can cause slight differences between the line-item and total taxes due to rounding.
For example, let’s say you have two transactions of $9.75 and $10.25 each with a 10% tax rate. The total amount before taxes is $20, and the total tax is $2. However, if you look at each line item separately, you may see something like this:

| Transaction | Amount | Tax   |
| ----------- | ------ | ----- |
| 1           | $9.75  | $0.98 |
| 2           | $10.25 | $1.03 |

As you can see, there’s a one-cent difference between the line-item level tax ($2.01) and the total tax ($2). This may not seem like a significant difference, but it’s unacceptable from the compliance perspective.

We’ve decided to exclude taxes from your reconciliation data to make your tax process more accurate and straightforward. Taxes will now only be displayed on your invoices.

This means that when you download or view your reconciliation data from our platform, you see only the amount before taxes for each transaction. The total amount due before taxes are the same for any billing period in both your reconciliation data and your invoice.

Then, when you receive or view your invoice from us, you see the total amount before taxes plus the total tax amount for that billing period.

This way, you don’t have to worry about rounding issues or discrepancies between your reconciliation data and invoices. You can easily report your taxable charges based on the invoice amount without making extra calculations or changes.

We believe this change benefits us in several ways:

- Save time and money by avoiding unnecessary calculations.
- Reduce errors and risks by ensuring compliance with tax regulations.
- Improve transparency and trust by providing clear and consistent information to your customers.
- Enhance customer satisfaction by offering a smooth and easy billing process.

We understand that this change may affect some of your workflows or systems, so we wanted to make sure you were aware of it before we implemented it. We sent emails explaining why it was made, how it works, when it would take effect, and what (if any) actions you need to take. 

We hope this change improves your experience with our product.

## Why are the charges on my invoice reconciliation data different from the daily rated usage data?

Invoice reconciliation and daily rated usage data are two ways of tracking your usage and billing for Azure services. However, they aren’t exactly the same and may show some discrepancies. Here are some reasons why:

- **Exclusion of products:** Firstly, it’s important to note that the **daily rated usage reconciliation applies** only to **pay-as-you-go resources purchased under Azure subscriptions,** while **invoice reconciliation reflects charges** for **all products and subscriptions across all customers.** To learn more about the products that are included in the daily rated usage reconciliation, see the link below.

[Products Included in the Daily Rated Usage Reconciliation](#what-products-are-in-the-new-commerce-daily-rated-usage-reconciliation-data)

If the charges for the same products or subscriptions from the two reconciliations don’t match up, there could be several reasons:

- **Taxes and other fees:** Your invoice reconciliation may include taxes and other fees that are not reflected in your daily rated usage data. If you need to compare the charges for a specific product or subscription, then compare the value of `BillingPreTaxTotal` in **daily rated usage** and the `Subtotal` in the **invoice reconciliation**. These values should be equal or very close before taxes and fees are applied.

- **Discounts and credits:** Your invoice reconciliation may include discounts or credits that are not reflected in your daily rated usage data. These discounts or credits may be applied based on your contract terms, service level agreements, promotional offers, or tier pricing. In that case, the `Subtotal` of the invoice reconciliation may be less than the `BillingPreTaxTotal` of the daily rated usage data.

- **Decimal round off:** The daily rated usage reconciliation shows up to 10 decimal places in the `BillingPreTaxTotal,` while the `Subtotal` in the invoice reconciliation rounds off to two decimal places during billing. This means that there could be a slight difference due to rounding after aggregating multiple line items.

Because of these differences, it’s important to understand that your invoice reconciliation and daily rated usage data may not match up exactly. Therefore, it’s not necessary to contact support teams for further details of these differences, **but you can be confident that you only pay for what you use, the lowest amount possible.**

### When should I contact the support team?

Before deciding that reconciliation is not correct, compare the attributes of both reconciliations. If you notice any discrepancies, contact our support team for help.

- **Quantity or billable quantity**: Compare the quantity or billable quantity of the same product or subscription to see if there are any differences.

- **Customer ID:** This is a unique identifier that represents a customer account in our system. Compare pay-as-you-go charges for customer IDs in both reconciliation data and look for any missing IDs.

- **Product ID, SKU ID, or Subscription ID:** These are unique identifiers that represent a product, a SKU, or a subscription plan in our system. Compare pay-as-you-go charges for them in both reconciliation data and look for any missing IDs.

- **Subtotal and BillingPreTaxTotal:** This is the amount of money that has been charged for a product or service before applying any taxes. Compare these two amounts to see if there is a significant difference.

To ensure accuracy when comparing reconciliations, follow these steps to avoid confusion. 

## Reconciliation data for indirect partners

You can get a detailed reseller view of reconciliation data using these attributes for partners in the **indirect model.**

| MPNID | Description |
| ------ | ----------- |
| MPNID | The Microsoft AI Cloud Partner Program identifier of the Cloud Solution Provider (CSP) partner (direct or indirect). |
| [Reseller MPNID](#reseller-mpnid) | The [Identifier of the reseller of record for the subscription](#reseller-mpnid). This information can be found in the Partner Center under the specific subscription. Note that this attribute only applies to partners in the indirect model and will show up in the reconciliation data. |

### Reseller MPNID

As a CSP, it’s important to know the role of the reseller’s MPN ID when selling subscriptions to customers. To ensure proper billing and tracking, follow these guidelines:

1. If you sell the subscription directly to the customer, the reseller’s MPN ID should be set to **0**.
2. If a reseller sells the subscription, the **reseller’s MPN ID** should be **filled** in. *At the time of the purchase, the reseller’s MPN ID must be active and linked to the partner.*
3. If you want to get rid of the reseller’s MPN ID, set it to **-1**.

To view or update the reseller MPNID:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Select the customer from the list and then select **Subscriptions**.

3. Choose the subscription from the list.

4. Select **Update** to change the Reseller (MPNID).

## Next steps

- [How to use the reconciliation files](use-the-reconciliation-files.md)
