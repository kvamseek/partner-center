---
title: Payout schedules and processes
description: Learn about payouts and transactions, such as payment schedules and recoupment processes for Azure Marketplace and other transactions.
ms.service: partner-dashboard
ms.subservice: partnercenter-payouts
ms.topic: conceptual
author: deeparamani
ms.author: deramani
ms.date: 03/30/2023
---

# Payout schedules and processes

**Appropriate roles**: Account admin | Global admin

This article describes:

- Microsoft's payment schedule
- Where to find the status of a payout
- The process for customer nonpayment

## Payment schedules

The following sections describe the payouts process for transactions when a customer has:

<!-- no toc -->
- [An Enterprise Agreement](#transactions-when-a-customer-has-an-enterprise-agreement)
- [A Microsoft Customer Agreement or Cloud Solution Provider](#transactions-when-customer-has-a-microsoft-customer-agreement-or-cloud-solution-provider)

### Transactions when a customer has an Enterprise Agreement

When a customer purchases a product from the Microsoft commercial marketplace or Azure Marketplace using their existing Microsoft Enterprise Agreement for transactions, Microsoft issues payouts in the next payout cycle. Payouts are based on usage or subscription purchase per the following table.

Payouts often occur before Microsoft collects payment from a customer. For the actions we take if a customer fails to pay Microsoft but we've already issued a payout, see the [Process for customer nonpayment](#process-for-customer-nonpayment).

This table shows Enterprise Agreement transactions (usage).

| Event | Description | Reporting Visibility | Timing |
| --- | --- | --- | --- |
| Usage | Customer uses a service. | [Usage](/azure/marketplace/usage-dashboard) dashboard | Month 1 |
| Microsoft calculates billing amount | Determine total usage over previous month period.* | [Usage](/azure/marketplace/usage-dashboard) dashboard | Month 2 |
| Transaction reported | Determine agency fee and payout earnings. | Marked *Unprocessed* in *Transaction History* in the [transaction history](transaction-history.md). | Month 2 |
| Prepare payout | Earnings are prepared for monthly payment. | Marked *Upcoming* in *Transaction History* in the [transaction history](transaction-history.md). | Month 3 (First week) |
| Payout sent | Payment is sent to publisher. | Marked *Sent* in *Transaction History* and in the *Payments* section of the [transaction history](transaction-history.md). | Month 3 (no later than the 15th) |
| Invoice paid by customer | Microsoft collects payment from customer. | No change | Months 3 through 12 |

\* Usage date in reporting shows as beginning of the month in which the usage occurred (for example, 10/1 for usage that occurred anytime in October). The payout date is in Pacific Standard Time (PST).

:::image type="content" source="media/payouts/timeline-enterprise-1.png" lightbox="media/payouts/timeline-enterprise-1.png" alt-text="Diagram of the timeline of payments for Enterprise Agreement customers.":::

This table shows Enterprise Agreement transactions for orders or subscriptions.

| Event | Description | Reporting Visibility | Timing |
| --- | --- | --- | --- |
|Month of transaction|Customer buys a service|[Order](/azure/marketplace/orders-dashboard) dashboard|Month 1|
|Transaction reported|Determine store service fee and calculate earnings| Marked *Unprocessed* in *Transaction History* in the [transaction history](transaction-history.md)|Month 1|
|Prepare payout|Earnings are prepared for monthly payment| Marked *Upcoming* in *Transaction History* in the [transaction history](transaction-history.md)|Month 2 (First week)|
|Payout sent|Payment is sent to publisher| Marked *Sent* in *Transaction History* and in the *Payments* section of the [transaction history](transaction-history.md)|Month 2 (no later than the 15th)|
|Invoice paid by customer|Microsoft collects payment from customer|No change|Month 3 through 12|

:::image type="content" source="media/payouts/timeline-enterprise-orders.png" lightbox="media/payouts/timeline-enterprise-orders.png" alt-text="Diagram of the timeline of payments for Enterprise Agreement customers with orders or subscriptions.":::

### Transactions when customer has a Microsoft Customer Agreement or Cloud Solution Provider

When a customer purchases a product from the Microsoft commercial marketplace or Azure Marketplace using a Cloud Solution Provider (CSP) or the Microsoft Customer Agreement (MCA), we issue payouts cycle based on usage or subscription purchase per the following tables.

Transactions become eligible for payment once Microsoft has collected payment from the customer.

This table shows the process for MCA, CSP, and usage.

| Event | Description | Reporting Visibility | Timing |
| --- | --- | --- | --- |
|Usage|Customer uses a service|[Usage](/azure/marketplace/usage-dashboard) dashboard|Month 1|
|Microsoft calculates billing amount|Determine total usage over previous month period\*|[Usage](/azure/marketplace/usage-dashboard) dashboard|Month 2|
|Invoice sent to Customer|Microsoft sends invoice to customer|[Revenue](/partner-center/marketplace/revenue-dashboard) dashboard|Month 2|
|Invoice paid by customer|Microsoft collects payment from customer|[Usage](/partner-center/marketplace/usage-dashboard) dashboard|Month 3|
|Transaction reported|Determine store service fee and payout earnings| Marked *Unprocessed* in *Transaction History* in the [transaction history](transaction-history.md)|Month 3|
|Prepare payout|Earnings are prepared for monthly payment| Marked *Upcoming* in *Transaction History* in the [transaction history](transaction-history.md)|Month 4 (First week)\* \- +1 month for credit card|
|Payout sent|Payment is sent to publisher| Marked *Sent* in *Transaction History* and in the *Payments* section of the [transaction history](transaction-history.md)|Month 4 (no later than the 15th)\* \- +1 month for credit card|

\* *Usage date in reporting shows as beginning of the month in which the usage occurred (that is, 10/1 for usage that occurred anytime in October). The payout date is in Pacific Standard Time (PST).*

:::image type="content" source="media/payouts/timeline-enterprise.png" lightbox="media/payouts/timeline-enterprise.png" alt-text="Diagram of payments for Enterprise Agreement customers.":::

This table shows the process for MCA, CSP, and orders or subscriptions.

| Event | Description | Reporting Visibility | Timing |
| --- | --- | --- | --- |
|Month of transaction|Customer buys a service|[Order](/azure/marketplace/orders-dashboard) dashboard|Month 1|
|Invoice sent to Customer|Microsoft sends invoice to customer|[Revenue](/partner-center/marketplace/revenue-dashboard) dashboard|Month 2|
|Invoice paid by customer|Microsoft collects payment from customer|[Order](/azure/marketplace/orders-dashboard) dashboard|Month 3|
|Transaction reported|Determine store service fee and payout earnings| Marked *Unprocessed* in *Transaction History* in the [transaction history](transaction-history.md)|Month 3|
|Prepare payout|Earnings are prepared for monthly payment| Marked *Upcoming* in *Transaction History* in the [transaction history](transaction-history.md)|Month 4 (First week): +1 month for credit card|
|Payout sent|Payment is sent to publisher| Marked *Sent* in *Transaction History* and in the *Payments* section of the [transaction history](transaction-history.md)|Month 4 (no later than the 15th): +1 month for credit card|

:::image type="content" source="media/payouts/timeline-credit-card-invoice-orders.png" lightbox="media/payouts/timeline-credit-card-invoice-orders.png" alt-text="Diagram of the timeline of payments for orders or subscriptions.":::

## Process for customer nonpayment

On rare occasions, Microsoft can't collect payments from customers for their commercial marketplace purchases. When a customer fails to pay Microsoft according to their billing schedule, we begin the collections process. This process takes approximately four months and involves persistent communication from Microsoft. If payment isn't received by the end of this process, Microsoft writes off the funds as non-collectable.

Per the payout process articulated here, Microsoft may have already paid out funds that are ultimately non-collectable to publishers (you). Therefore, we have a process for reconciling these amounts.

Microsoft recoups any payouts already paid to you using one of the following methods:

- Microsoft may subtract the unpaid amounts from future payouts. For example, if USD1,000 in payouts are deemed non-collectable and written off, your future payouts will be withheld until the USD1,000 is recovered.
- Microsoft may request a refund, or invoice publishers for any uncollected amounts.

**The following schedule is an example:**

| Event | Approximate date* | Partner visibility |
| --- | --- | --- |
| Example payout date | 10/15/2020 |  Marked *Sent* in *Transaction History* and in *Payments* section of [Transaction history](transaction-history.md) |
| **If customer does not pay Microsoft** | 12/2/2020 – 12/5/2020 | No change, same as above |
| Customer receives first late payment email | 12/6/2020 | None |
| Customer receives regular emails of increasing urgency | 12/7/2020 – 1/31/2021 | None |
| Publisher is notified write-off is likely | 1/7/2021 | - |
| Customer receives termination notice | 2/1/2021 | None |
| Collection process ends / funds are written off | 2/15/2021 | Email notification sent to publisher that funds have been written off. |
| Payout is deducted | 3/1/2021 | Publisher will see negative transaction in Partner Center [transaction history](transaction-history.md). |
| Payout is withheld | 3/15/2021 | Future payouts will be shown in Partner Center [transaction history](transaction-history.md). Publisher won't receive payment until balance is no longer negative.|

\* *The payout date is in Pacific Standard Time (PST).*

## Time required for payments to reach a payout account

We typically send payments due by the 15th day of the month, but more time is required for the payment to reach your account. The time required depends on the payment method we use for your account, as described in the following table.

> [!NOTE]
> The intervals in the table are approximate. Payments might take more or less time to reach your account.

| Payment method     | Number of days to reach payout account     |
|--------------------|--------------------------------------------|
| PayPal             | One business day                             |
| ACH/SEPA           | 2 to 3 business days                          |
| Wire transfer      | 7 to 10 business days                         |

## Next steps

- [Tax details](tax-details-marketplace.md)
- [Setup commercial marketplace payout and tax profiles](set-up-your-payout-account.md)
