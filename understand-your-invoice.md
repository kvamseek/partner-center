---
title:  Understand your invoice
ms.topic: article
ms.date: 9/11/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-billing
description: This article helps partners understand their legacy and new commerce invoices.
author: sourishdeb
ms.author: sodeb
---

# Understand your invoice

**Appropriate roles**: Global admin | User management admin | Billing admin | Admin agent | Sales agent

Understand your bill. It is a complete list of all Partner Center charges for your program and products.

## Find your invoice

You can find your invoice on the **Billing** in Partner Center.

You can also find your billing history, spending trends, and reconciliation files on this page.

To find your reconciliation file:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Billing**.
2. Select an invoice to view more detailed information.

You can find a link to your most recent reconciliation file at the top of the page under **Account balance as of last invoice date.**

To download an invoice:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Billing**.
2. Find the invoice in the **Billing history** section by choosing the appropriate year and then selecting the drop-down arrow next to the appropriate billing period.
3. Select the link next to **Invoices (.pdf)**.


## Invoice types

There are two types of invoices. Look at the invoice number.

- Legacy invoices start with "D" (Office 365, 145 P).
- New commerce invoices start with "G" (Azure plan, Azure RI, Azure Savings Plan, per-user M/D 365, software subscriptions, perpetual software, and Marketplace).

All invoices are created in the currency of the partner's location. But before August 2021, some old invoices were created in the currency of the customer's location in the European Union. Past invoices are available in the "Billing" workspace or through the APIs.

## Understanding the invoice PDF

- **Legacy invoice:** Available two days after your billing anniversary date every month.
- **New commerce invoice**: Available by the 8th of every month.

> [!NOTE] 
> Invoices can be found in the "Billing" workspace or through APIs


The following lists common fields of the invoice PDF.

- **Invoice number**: Unique number for each invoice
- **Billing period:** Time frame for when charges will be applied
- **Invoice date**: Date the invoice was generated
- **Payment due date**: Deadline to pay the invoice
- **Charges**: Total charges in the billing period
- **Credits**: Credits given for outages, Azure usage, and other reasons
- **Payment instructions**: Steps to pay the invoice (*Include the invoice number when paying.*)

## New commerce invoice PDF attributes

The table below describes the important attributes of New Commerce LRD and non-LRD invoices. Certain attributes are solely applicable to LRD invoices.

| **Attribute**                     | **Definition**                                                                              |
|-----------------------------------|---------------------------------------------------------------------------------------------|
| Invoice Number                    | Invoice number for a non-LRD partner                                                    |
| Invoice (Document) Date           | Invoice  generation date |
| Payment  Terms                    | Payment  term length     |
| Billing Number                    | Invoice number for an LRD partner                                                       |
| Billing Profile                   | Partner Identifier                                                       |
| PO Number                         | Purchase order number                                                                   |
| State of Destination and Code     | Partner location and unique location  identifier |
| Tax Invoice Number                | Country/region-specific invoice sequence number                                                  |
| Tax Invoice Date                  | Invoice generation date                                                                     |
| Credit Note Number                | Country/region-specific sequence number                                                          |
| Credit Note Date                  | Credit notes generation date                                                                |
| Original Billing Number           | Initial invoice for these products                                                      |
| Total Amount                      | Amount due                                                                     |
| Due on                            | Payment due date                                                                            |
| Sold To                           | Product sale location                                                       |
| Bill To                           | Invoice sent location                                                     |
| Billing Period                    | Month of transactions                                                |
| Charges                           | Total monthly charges                                                              |
| Credits                           | Total monthly credits                                                                       |
| Subtotal                          | Total after deducting the credit                                                          |
| Tax                               | Tax added to the subtotal                                                                   |
| Payment Instructions              | Steps to pay invoices. *Include the invoice number when paying.* |
| Purchases                         | Product name.                                                                               |
| Publisher name                    | Third-party product publisher names                                                   |
| Publisher address                 | Third-party product publisher addresses                                               |
| Pricing Currency                  | Product pricing currency                                                     |
| Exchange rate to billing currency | Exchange rate used to convert to billing currency                             |
| Date range                        | Billing period                                                                          |

## Legacy invoice PDF attributes

The table below describes the important attributes of the legacy invoice:

| **Attribute**               | **Definition**                                                                                                                                                                                                                                                                                                                 |
|-----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| US FEIN                     | Federal Employer Identification Number (FEIN). This is your United States federal tax identifier number.                                                                                                                                                                                                                  |
| Customer number             | Customer number.                                                                                                                                                                                                                                                                                                          |
| Bill to                     | Address where we send your invoice. You can change your company name and address in your Partner Center billing profile.                                                                                                                                                                                                   |
| License-based charges       | Monthly or annual charges for your purchased usage-based licenses, billed in advance of the service. This number is the sum of all charges in the **Subtotal** column (column **T**) in your license-based reconciliation file.                                                                                       |
| Usage-based charges         | Your Azure usage. This includes new services or applications enabled and used during the billing period. This number is the sum of all charges in the **PretaxCharges** column (column **Z**) in your usage-based reconciliation file.                                                                                         |
| Other products and services | Other charge types include cancellation fees, and prorated fees for the following: activation, conversion to the offer, conversion away from the offer, and conversion from the instance. These charge types aren't included directly in the subtotal.                                                                 |
| Discounts                   | Discounts that the customer receives from subscription's normal price. This number is shown as a *total discount amount*, not for per unit or license.                                                                                                                                                                         |
| Credits                     | Credits or adjustments for changes made to subscriptions (for example, license removal).                                                                                                                                                                                                                        |
| Subtotal                    | Total before taxes and tax-exclusive charges and credits.                                                                                                                                                                                                                                                                      |
| Tax                         | Total tax for your current charges, as totaled in the **Details** section beginning on page 2 of your invoice. This number is the sum of all charges in the **TaxAmount** column (column **AA**) in your usage-based reconciliation file, and the **Tax** column (column **U**) in your license-based reconciliation file. |
| Other credits               | Tax-exclusive credits.                                                                                                                                                                                                                                                                                                         |
| Total current charges       | Amount due in your billing currency for the billing period.                                                                                                                                                                                                                |
| Payment instructions        | Description of how to pay your invoice, based on your region. *Always be sure to include your invoice number when making a payment.*                                                                                                                                                                                           |
| Invoice no                  | A unique number to identify each invoice.                                                                                                                                                                                                                                                                                                    |
| Billing period              | Timeline during which transactions occurred.                                                                                                        |
| Invoice date                | Billing anniversary date on which your invoice is generated each month.                                                                                                                                                                                                                                            |
| Payment terms               | Length of time to make payments                                                                                                                                                                                                                                                            |
| Payment due date            | Date by which your payment must be received.                                                                                                                                                                                                                                                                               |
| Customer PO                 | Purchase number order.                                                                                                                                                                                                                                                                                                    |
| Customer service            | Website URL to access customer service.                                                                                                                                                                                                                                                                     |
| Service recipient           | Address where the service is being used. (This is the legal company address associated with company vetting.)                                                                                                                                                                                                              |

## FAQs

### Why do I have different invoice templates?

Your invoices should not only have the correct charges, but they should also meet the legal requirements of your local government. For this reason, we have created LRD and non-LRD invoice templates that provide you with detailed information in a reliable and compliant manner. 
Click on the relevant link below to learn more about these templates:

- [LRD Invoice](#lrd-invoice)
- [Non-LRD Invoice](#non-lrd-invoice)

### LRD Invoice

LRD invoices are a reliable and efficient way to manage your billing needs. Our templates follow strict rules to make sure everything important is included, giving you peace of mind and confidence. The LRD invoice template is divided into three main sections to provide you with a clear and concise overview of your billing information.

#### Section 1: Billing Summary

The first part of the LRD invoice lists all your billing information, like charges, credits, and taxes, in an organized way. Payment instructions are also included.

#### Section 2: Commercial Invoice

The next part is the billing statement that shows everything you were charged for during that period. This includes new purchases, recurring charges, renewals, and any returns made during that same period. Returns are subtracted from the total amount charged. 

> [!NOTE] 
> This section is also given to India and Brazil as a separate document to meet their legal requirements.

#### Section 3: Credit Notes

The last part is for credit notes. This includes a list of products and services that were bought during previous billing periods but are canceled or returned during the current billing period. Each credit note is linked to the original invoice, so it's easy to track refunds. If there are returns from different billing periods, then a separate credit note is generated for each billing period.

> [!NOTE] 
> India and Brazil have a legal requirement that credit notes must be given separately. 

In summary, these invoices provide a summary of charges, a tax invoice, and a credit note, all presented in a clear and easy-to-understand manner that follows rules and regulations.

### Non-LRD Invoice

Non-LRD invoices show charges for products bought, services rendered, or cancelations made during a billing period in a simple and straightforward way. billing information, like charges, credits, and taxes, in an organized way. Payment instructions are also included.

The subsequent pages show everything you were charged for during that period. This includes new purchases, recurring charges, renewals, and any returns made during that period. Returns are subtracted from the total amount charged. 

In conclusion, non-LRD invoices are a simple and straightforward way to bill for purchases, services, or cancelations. You receive a clear and concise list of charges, ensuring that you know exactly what you're paying for.


### Check credit notes using invoice reconciliation data

Follow these steps to check the credit amount:

1. Open the transaction details in Microsoft Excel.
2. Sort the transactions by **product name or ID.**
3. Create a pivot table for the sorted transactions.
4. Place **OrderID** in the **Rows** section and **sum (Total)** in the **Values** section.
5. Add up the negative amount to confirm the credit note amount for the product.

### Why doesn't the tax amount on the invoice match the tax percentage exactly?

The tax amount displayed on the invoice is calculated for each transaction in the reconciliation data by rounding it down to two decimal places and then adding it together. This may result in a slight discrepancy between the calculated tax amount based on the tax percentage of the total amount and the sum of taxes for each transaction in the reconciliation data.


## Next steps

- [Tax and tax exemptions](tax-and-tax-exemptions.md)
