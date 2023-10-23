---
title: Getting paid in Partner Center
description: Learn about receiving payments for earnings as a Microsoft partner. You can receive payments from commercial marketplace offers, incentive programs, and the Cloud Solution Provider program. This article includes payout policy, payout hold status, and payout statements.
ms.service: partner-dashboard
ms.subservice: partnercenter-payouts
ms.topic: conceptual
author: deeparamani
ms.reviewer: david.najour
ms.author: deramani
ms.date: 05/10/2023
---

# Getting paid in Partner Center

**Appropriate roles**: Account admin | Global admin

This article has important information about receiving payment for your offers, add-ons, and advertising earnings. It summarizes:
<!-- no toc -->
- [Payout policies and agreements](#payout-policies-and-agreements)
- [Prerequisites for getting paid](#prerequisites-for-getting-paid)
- [Placing payments on hold](#placing-payments-on-hold)
- [Payout statements](#payout-statements)

> [!TIP]
> To see the partner's view of billing and invoicing in Azure Marketplace, such as through commercial marketplace offers, incentive programs, and the Cloud Solution Provider program, see [Azure Marketplace billing and invoicing](/marketplace/billing-invoicing).

## Payout policies and agreements

To get paid, you must adhere to the agreements and payout policy, which this section provides information about.

| Article  |Description  |
|---------|---------|
|[Microsoft Publisher Agreement (MPA)](/legal/marketplace/msft-publisher-agreement)     | You must accept the MPA before you can be paid.<br> The agreement explains the relationship between you and Microsoft as it pertains to seller offers in the commercial marketplace, including the store fee that Microsoft charges for every sale made.         |
|[Payout schedules and processes](payout-policy-details.md) | Discusses [payment schedules](./payout-policy-details.md), where to find the status of a payout, and the [process for customer non-payment](./payout-policy-details.md). |
|[Tax details for commercial marketplace publishers](tax-details-marketplace.md)     | Explains the tax considerations for price selection and tax responsibility under the  [Microsoft Publisher Agreement](/legal/marketplace/msft-publisher-agreement).        |
|[Store fees](/azure/marketplace/marketplace-commercial-transaction-capabilities-and-considerations) | Officially provided in [Commercial marketplace transact capabilities](/azure/marketplace/marketplace-commercial-transaction-capabilities-and-considerations).        |
|[Payment thresholds, methods, and time frames](payment-thresholds-methods-timeframes.md)   | Outlines the payment methods supported in each country and region.<br> - Payments are made monthly if the payment threshold has been met.<br> - Payments due are typically sent by the 15th day of the month.<br> - Payments usually take 3 to 10 more business days to reach your payout account. |

## Prerequisites for getting paid

Before getting paid the first time, you must set up your payout account and complete the bank and tax forms in which you provide your preferred payment methods and your tax withholding information.

For details, see [Set up commercial marketplace payout and tax profiles](set-up-your-payout-account.md).

## Placing payments on hold

We send payments monthly. However, you can put your payments on hold.

If you put your payments on hold, we continue to display any earnings on the **Payouts** page, but we don't send any payments to your account until you remove the hold.

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Settings** (gear).
1. Select **Account settings**, then **Payout and tax profile assignment**.
1. Locate the program for which you would like payments held.
1. Select the **Hold my Payment** check box to hold payments for the program.

- You can change your payment hold status at any time.
- Changing your payment hold status affects the next monthly payment. For example:
  - If you want to start holding payments in April, set **Hold my Payment** to **On** before the end of March.
  - If you want to resume payments in June, set **Hold my Payment** to **Off** before the end of May.

> [!NOTE]
> Payment holds are applied to each program individually (for example, to advertising, Microsoft Store, or Azure Marketplace). If you want to hold payments for all your programs, you must hold payment for each program individually.

## Payout statements

- The payout statement shows your earnings from the sales from your offers and add-ons in the transaction history.
- You can view payment details and download reports in CSV or TSV format.
- You can use the [Partner Payouts API](/rest/api/partner-center/partner-payouts) to systematically pull  payout reports.
To learn more about how to access the payout statement and the details of the transaction history and payment reports, see [Transaction history](transaction-history.md).

## Next steps

- [Partner Payout API](/rest/api/partner-center/partner-payouts)
- [Payouts FAQ](payout-faq.yml)
