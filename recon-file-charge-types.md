---
title: Reconciliation file charge types
ms.topic: article
ms.date: 11/08/2022
description: Discover the types of charges (such as, license-based, usage-based, and one-time), credits, and discounts in Partner Center reconciliation files.
ms.service: partner-dashboard
ms.subservice: partnercenter-billing
author: sodeb
ms.author: sodeb
---

# Understand the different charge types in Partner Center reconciliation files

**Applies to**: Partner Center | Partner Center for Microsoft Cloud for US Government

**Appropriate roles**: Admin agent | Billing admin | Global admin

This article helps you understand the charges that appear in your reconciliation file. While your invoice provides a summary of your costs, the reconciliation file goes into more detail. It provides a deeper understanding of each transaction and its charge types. By looking at the charges in your reconciliation file, you can get a full picture of your bills and make sure your financial records are correct. See for more info on reconciliation files [how to use reconciliation files](use-the-reconciliation-files.md).

Both [usage-based reconciliation files](usage-based-recon-files.md) and [license-based reconciliation files](license-based-recon-files.md) only show usage-related transactions and charges (units consumed and related charges).

> [!NOTE]
> One-time credits, discounts, or refunds appearing as **“Adjustments”** on your invoice may not always be reflected in the legacy reconciliation data. Consider both when reviewing billing information for accuracy.

## Map charge types to invoice charges

Using the filter options in Microsoft Excel, it’s easy to match the amounts on your invoice to the ones in your reconciliation file. Filter your reconciliation file by charge type. This will let you map the charges on your invoice to the charge breakdowns in the reconciliation file. This quick and easy process will make it easier for you to track your charges and make sure that your billing information is correct.

## Legacy license-based reconciliation charges

To map these license-based charges to your invoice, sum the `Amount` column from the license-based file.

| Charge description (ChargeType column in the reconciliation file) | Charge explanation |
| ------------------------------------------------------------- | ------------------ |
| Activation fee | The amount charged to the customer when they use the subscription after purchase. |
| Cancel fee | Prorated charges refunded to the customer when associated licenses are changed. |
| Cancel instance prorate | Prorated charges canceled when customer with monthly subscription has subscription suspended and associated licenses changed within the same month. |
| Cycle fee | Periodic charges for a subscription. |
| Cycle instance prorate | Prorated charges assessed from the customer when associated licenses are changed. |
| Prorate fees when cancel | Prorated refund for unused portion of service upon cancellation. |
| Prorate fees when convert away from current offering | Prorated charges after converting away from the current monthly subscription to an annual subscription. |
| Prorate fees when convert to a new offering | Prorated charges after converting a monthly subscription to a new annual subscription. |
| New purchase cycle fee | The charge type for a subscription when using both monthly or annual billing. |
| Prorate fees when purchase | The first cycle fee of a net new subscription. |
| Prorate fee when renew     | The first cycle fee of a renewed subscription. |
| Prorate fees when activate | Prorated fees from reactivating suspended subscription until end of billing period. |

## New commerce license-based reconciliation charges

To add these new commerce charges to your invoice, add up the `Total` in the reconciliation file. If there is a credit note, deduct it from the invoice amount.

| Charge description (ChargeType column in the reconciliation file) | Charge explanation |
| ------------------------------------------------------------- | ------------------ |
| new | When you buy a new subscription.  |
| renew | When you renew your subscription. |
| cycleCharge | Regular recurring charges for your subscription.  |
| addQuantity | Refunds and charges when you add seats.  |
| removeQuantity | Refunds and charges when you remove seats.  |
| moveQuantity | When you upgrade to an existing subscription. |
| cancelImmediate | When you cancel your subscription. |
| convert | When you change from a free trial to a paid subscription or upgrade to a new subscription. |
| changeBillingPlan | Changing from monthly to yearly billing or vice versa.  |
| customerCredit | Credits for Azure, SLA, etc.  |
| extendTerm | When you are given a longer trial period. |

## Usage charges for legacy

To map these usage charges to your invoice, sum the `PretaxCharges` column from the usage file.

| Charge description (ChargeType column in the reconciliation file) | Charge explanation |
| ------------------------------------------------------------- | ------------------ |
| Assess usage fee when cancel | Access usage fee upon cancellation for unpaid usage during the current billing period. |
| Assess usage fee for current cycle | Access usage fee for the current billing period. |

### Credits

To map these credits to your legacy invoice:

- Sum the `TotalForCustomer` from the license-based file.
- Sum the `PostTaxTotal` column from the usage-based file.

| Charge description (ChargeType column in the reconciliation file) | Charge explanation |
| ------------------------------------------------------------- | ------------------ |
| Offset a line item | Partial or whole refund to a line item, including taxes. |

### Usage-based discounts for legacy products

To map these usage-based discounts to your invoice, sum the `PretaxCharges` column from the usage file.

| Charge description (ChargeType column in the reconciliation file) | Charge explanation |
| ------------------------------------------------------------- | ------------------ |
| Activation discount | Discount applied when subscription activated. |
| Cycle discount | Discount applied on periodic charges. |
| Renew discount | Discount applied when subscription renewed. |
| Cancel discount | Charges applied when discounts are canceled. |

### License-based discounts for legacy products

To map license-based discounts to your invoice, sum the `TotalOtherDiscount` column from the legacy license-based reconciliation file.

*License-based discounts may be applied to multiple charge types.*
