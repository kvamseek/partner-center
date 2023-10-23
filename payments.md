---
title: Payments
description: Learn about payout statements and summaries, and how to view and export your payment data from Microsoft Partner Center
ms.subservice: partnercenter-payouts
ms.service: partner-dashboard
ms.topic: article
author: deeparamani
ms.author: deramani
ms.date: 7/12/2022
---

# Payments

**Appropriate roles**:

- Incentives: Account admin | Global Admin | Incentive admin | Incentive User
- Marketplace / Store: Account owner | Financial Contributor

The **Payments** page details the money you've earned with Microsoft. It also shows when and how much you'll be paid.

> [!NOTE]
> To be eligible for payout, your proceeds must reach the [payment threshold](payment-thresholds-methods-timeframes.md) of $50. For more information, see the [Microsoft Publisher Agreement](/legal/marketplace/msft-publisher-agreement).

- **Total paid this year** – The combined total paid out to you this year, in U.S. dollars, for all of your programs.
- **Next estimated payment** – The single next payment coming to you (even if there are others coming soon), in U.S. dollars.
- **Last payment** – The amount (in U.S. dollars), program name, and program of your most recent payment.
- **Payment by source** – Amount of payments (in U.S. dollars), per program, over the last 12 months.

## Payments list

The **List of Payments** table shows paid and pending payments. You can download service fee tax information in PDF format and view the earning details for a given payment.

:::image type="content" source="media/payouts/list-of-payments.png" alt-text="Export transaction history.":::

- **Paid** – All payments sent successfully. Choose the year in the drop-down menu to filter to the payments released in that year.
- **Pending** – Upcoming payments.
- **Service fee tax (PDF form)** – Available for the payments subjected for service fee tax. Service fee taxes are shown in **Other taxes**.
- **View** – Redirects to the transaction history with a list of earnings included in the payment.

To understand why you might have missing or unexpected earnings, see [Common questions about commercial marketplace payouts](payout-faq.yml#why-are-my-earnings-missing-).

## Payments download

 The following table explains each column in the report. To see more details about your payments, select **Download** at the top of the Payments page.

| Column name | Description |
| --- | --- |
| participantID | The primary identity of the partner earning under the program |
| participantIDType | Usually program ID for Incentives programs and Seller ID for Store programs |
| participantName | Name of the earning partner |
| programName | Incentives/store program name |
| earned | Amount earned in the Pay To currency for that program/participantID |
| earnedUSD | Amount earned for the program/participant ID, in USD |
| withheldTax | Amount of tax withheld in the Pay To currency for the program/participantID |
| salesTax | Total amount of sales tax in the Pay To currency for the program/participantID (applicable for incentives programs only) |
| serviceFeeTax | Total amount of serviceFeeTax in Pay To currency for the program/participantID (applicable for store programs and Azure Marketplace only) |
| totalPayment | Total payment in local currency excluding the withholding tax and including the sales tax (if applicable) for the program/participantID |
| currencyCode | Pay To currency code |
| paymentMethod | The method used to pay the partner, for example, electronic bank transfer, credit note |
| paymentID | Unique identifier for the payment. This number is usually visible in your bank statement (applicable for SAP payments only). |
| paymentStatus | Payment status |
| paymentStatusDescription | Friendly description of payment status |
| paymentDate | Date payment was sent from Microsoft |

## Next steps

- [New payout data export page](./payouts-enhanced-exports.md)
- [Payout policy details](payout-policy-details.md)
- [Earnings and payment reconciliation FAQ](./reconciliation-faq.md)