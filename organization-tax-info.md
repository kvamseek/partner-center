---
title:  Understand taxes and credits
ms.topic: article
ms.date: 8/18/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-billing
description: Taxes for Partner Center purchases are determined by your business address. Businesses in some countries/regions can provide their VAT number or local equivalent.
author: parthpandyamsft
ms.author: parthp
---

# Understand taxes and credits

**Appropriate roles**: Global admin | User management admin | Billing admin | Admin agent | Sales agent

## Taxes and VAT

You're taxed based on *your* details, not your customers' details, because the billing relationship is between Microsoft and you.

You can submit your tax identifier during the account setup process or through a support request later. You'll see any changes reflected on your next billing cycle.

For **withholding and sales tax exemption**, you must submit tax documentation through a support request. You'll see the changes and appropriate refunds on your next billing cycle. Find out more information on [submitting withholding tax](withholding-tax-credit-form.md).

For **value-added tax (VAT) exemption**, you must submit your VAT ID (validated by Microsoft) through **Accounts Settings** > **Legal Info** > **Reseller** > **Bill-to Info**. If the VAT ID is submitted after account setup, your invoices prior to that request won't have a VAT ID stamped on the invoice PDF. You'll see the changes on your next billing cycle.

For more tax information, consult your local tax office or tax advisor.

## Add a VATID to your billing profile

You can update your billing profile to include your VAT ID by using the following procedure (but not in every country or region).

To update your billing profile with your VAT ID, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select the **Settings** (gear) icon.
2. Select **Account settings**.
3. Select **Legal Info** and click on the **Reseller** tab.
4. In the **Bill-to Info** section, choose **Update**.
5. For **Company Tax ID**, specify your VAT ID number.

> [!NOTE]
> You can update your Microsoft AI Cloud Partner Program tax ID yourself during the renewal period when you start the purchase flow. If you want to update your tax ID and you are not in the renewal window, [create a support ticket](./report-problems-with-partner-center.md) using the Partner Center account associated with Incentives. (To do so, you must be enrolled in one of the Incentives programs.)

## Adjustments/Credits/Cancellations

Cancellation credits for licensed-based services are prorated for unused days for mid-cycle cancellations (and license decreases) according to this formula:

`[ROUND((ROUND(Unit Price * Quantity / Number of days in prorated Month, 2) * Number of prorated days) / Quantity, 2) * Quantity]`

## Next steps

- [Tax and tax exemptions](tax-and-tax-exemptions.md)
