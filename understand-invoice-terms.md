---
title: Understand the terms of your invoice in Partner Center
ms.topic: how-to
ms.date: 9/11/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-membership
description: Learn about the terms of the invoice for the Microsoft AI Cloud Partner Program
author: amitpandey1858
ms.author: pandeyamit
ms.custom: references_regions
---

# Understand the terms of your invoice in Partner Center

**Appropriate roles**: Global admin | MPN Partner admin

The invoice provides a summary of your charges and provides instructions for payment. It's available for download in the Portable Document Format (.pdf) from the [Azure portal](https://portal.azure.com/) or the [Bills and Payments](https://partner.microsoft.com/dashboard/v2/membership/offers/billsandpayments) section in the Partner Center. Or, you can [receive the invoice via email](https://portal.azure.com/#view/Microsoft_Azure_GTM/BillingProfileMenuBlade/~/properties/billingProfileId/%2Fproviders%2FMicrosoft.Billing%2FbillingAccounts%2F9531a623-22b5-570d-4ef5-1375b18b0ce2%3Afccae484-8990-4354-8355-22e82fa14009_2019-05-31%2FbillingProfiles%2FDYVY-2BJB-BG7-TGB).

A few things to note:

- **Immediate settlement invoice**: The invoice is generated shortly after the purchase and is specific to the offer you have purchased, such as MAPS, Solution Partner, etc.
- **Post-pay scenario invoice**: A consolidated invoice is generated for all the purchases made during the month, including Office, Azure, MAPS, etc. This invoice is generated on the 5th, 7th, or 9th day of the month, depending on the terms of your contract with Microsoft.

## Detailed terms and descriptions of your invoice

This section lists the important terms that you see on your invoice and descriptions for each term.

### Account information

The account information section of the invoice is on the top of the first page and shows information about your profile and subscription.

#### Immediate settle invoice

:::image type="content" source="./media/membership/invoice-summary.png" lightbox="./media/membership/invoice-summary.png" alt-text="Screenshot of Invoice Summary page, showing an amount paid.":::

#### Post pay invoice
:::image type="content" source="./media/membership/post-pay-invoice.png" lightbox="./media/membership/post-pay-invoice.png" alt-text="Screenshot of the Invoice Summary page, showing an amount due in the future.":::

| Term            | Description                                                                                                                                                  |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Sold to         | Address of your legal entity, found in billing account properties                                                                                            |
| Bill to         | Billing address of the billing profile receiving the invoice, found in billing profile properties                                                            |
| Billing Profile | The name of the billing profile receiving the invoice                                                                                                        |
| P.O. number     | An optional purchase order number, assigned by you for tracking                                                                                              |
| Invoice number  | A unique, Microsoft-generated invoice number used for tracking purposes                                                                                      |
| Invoice date    | Date that the invoice is generated, typically five to 12 days after end of the billing cycle. You can check your invoice date in billing profile properties. |
| Payment terms   | How you pay for your Microsoft bill. The Net 30 days term means you pay within 30 days of the invoice date.                                                  |

### Billing summary

The Billing Summary shows the charges against the billing profile since the previous billing period, any credits that were applied, tax, and the total amount due.

#### Immediate settle invoice

:::image type="content" source="./media/membership/immediate-settle-invoice.png" lightbox="./media/membership/immediate-settle-invoice.png" alt-text="Screenshot of Billing Summary page, showing an amount paid.":::

#### Post pay invoice

:::image type="content" source="./media/membership/billing-summary-post-pay-invoice.png" lightbox="./media/membership/billing-summary-post-pay-invoice.png" alt-text="Screenshot of Billing Summary page, showing an Azure credit applied.":::

| Term            | Description                                                                                                                                                    |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Unit price      | The effective unit price of the service (in pricing currency) that is used to the rate the usage. It's unique for a product, service family, meter, and offer. |
| Qty             | Quantity purchased or consumed during the billing period                                                                                                       |
| Charges/Credits | Net amount of charges after credits/refunds are applied                                                                                                        |
| Azure Credit    | The amount of Azure credits applied to the charges/Credits                                                                                                     |
| Tax rate        | Tax rate(s) depending on country/region                                                                                                                        |
| Tax amount      | Amount of tax applied to purchase based on tax rate                                                                                                            |
| Total           | The total amount due for the purchase                                                                                                                          |

### Invoice sections

For each invoice section under your billing profile, you'll see the charges, the amount of Azure credits applied, tax, and the total amount due.

Total = Charges - Azure Credit + Tax

#### Details by invoice section

The details show the cost for each invoice section broken down by product order. Within each product order, cost is broken down by the type of service.

:::image type="content" source="./media/membership/cloud-partner-program-subscription.png" lightbox="./media/membership/cloud-partner-program-subscription.png" alt-text="Screenshot of the total amount due.":::

The total amount due for each service family is calculated by subtracting Azure credits from Credits/charges and adding Tax:

| Term            | Description                                                                                                                                                    |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Unit price      | The effective unit price of the service (in pricing currency) that is used to the rate the usage. It's unique for a product, service family, meter, and offer. |
| Qty             | Quantity purchased or consumed during the billing period                                                                                                       |
| Charges/Credits | Net amount of charges after credits/refunds are applied                                                                                                        |
| Azure Credit    | The amount of Azure credits applied to the Charges/Credits                                                                                                     |
| Tax rate        | Tax rate(s) depending on country/region                                                                                                                        |
| Tax amount      | Amount of tax applied to purchase based on tax rate                                                                                                            |
| Total           | The total amount due for the purchase                                                                                                                          |

### How to pay

At the bottom of the invoice, there are instructions for paying your bill.

:::image type="content" source="./media/membership/payment-instructions.png" alt-text="Screenshot of payment instructions: 'Your account has a credit card on file and there is no action for you to take. The card you have on file will be charged.'":::

## What is the Modern Limited Risk Distributor model?

A Limited Risk Distributor (LRD) is a subsidiary that Microsoft established as buy-sell distributor who sells directly or indirectly. The model affects customers buying directly from Microsoft through the Microsoft Customer Agreement. It also demonstrates the Microsoft commitment to our business in the following countries/regions:

- Australia
- New Zealand
- Canada
- France
- United Kingdom
- Germany
- Austria
- Belgium
- Denmark
- Finland
- Italy
- Netherlands
- Norway
- Sweden
- Switzerland
- Spain

Under the LRD model:

- The selling entity is the local LRD subsidiary (sales and distribution rights have been extended to the LRDs).
- The payment methods won't change for customers.
- The LRD can only sell to customers located in the LRD country/region and agreed territories as defined by Tax.
- For LRD sales, the Licensor is either MS Corp or MIOL.
  - For the Americas, the Licensor is MS Corp (1010).
  - For EMEA and APAC, the Licensor is MIOL (1062).

For customers not part of the LRD model and for legacy/regular invoices, the billing entity is:

- For EMEA, the billing entity is Microsoft Ireland Operations Limited (MIOL).
- For Americas, the billing entity is Microsoft Corporation.
- For APAC, the billing entity is Microsoft Regional Sales Pte LTD.
- For Japan, the billing entity is Microsoft Japan Co., LTD.
- For Korea, the billing entity is Microsoft Korea Inc.
- For India, the billing entity is Microsoft Corporation India Private Limited.
- For Brazil, the billing entity is A MICROSOFT DO BRASIL IMP E COM DE SOFTWARE E VIDEO GAMES LTDA.

Microsoft has received guidance that due to decimal point rounding; some LRD invoices may show tax that's under or overcharged. The taxes are compared to the amount that should have been calculated based on the local tax regulation.

While we work to resolve this issue, you're only required to pay the VAT amount calculated at the subtotal level of the invoice. Microsoft will be reporting the same amount in its VAT return and will write off the difference for any overcharges. Microsoft is bearing the risk of the undercharged VAT if there are audits. Unfortunately, it's currently impossible for Microsoft to reissue an amended invoice due to a system limitation.

## Next steps

- [Bills and Payments](https://partner.microsoft.com/dashboard/v2/membership/offers/billsandpayments) section in the Partner Center.
- [Receive invoices via email](https://portal.azure.com/#view/Microsoft_Azure_GTM/BillingProfileMenuBlade/~/properties/billingProfileId/%2Fproviders%2FMicrosoft.Billing%2FbillingAccounts%2F9531a623-22b5-570d-4ef5-1375b18b0ce2%3Afccae484-8990-4354-8355-22e82fa14009_2019-05-31%2FbillingProfiles%2FDYVY-2BJB-BG7-TGB)
 
