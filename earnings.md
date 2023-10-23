---
title: Earnings in Partner Center
description: Get a summary of earnings and payments in Partner Center through the Earnings page.
ms.date: 10/04/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-earnings
ms.topic: article
author: deeparamani
ms.author: deramani
---

# Earnings in Partner Center

**Appropriate roles**: *Incentives*: Incentives admin | Incentives user; *Marketplace/Store*: Financial contributor

See earnings and payments you've received through Partner Center.

## Access your earnings statement

Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home), and select the [Earnings](https://partner.microsoft.com/dashboard/earnings/earnings) page.

The page includes a rich filter set with abilities to see your earnings data by solution area, partner association in addition to what is available in current experience in Transaction history.

You can view earnings organized by most earning top 50 customers, or search for any individual customer. Alternatively, view earnings organized by programs, engagements (for Microsoft commerce incentives only) and levers.

You can see and download data about UI views. You can see detailed earnings report downloads available from top of the page for Incentives (standard and growth reports), Store, Marketplace and Payments.

The Earnings page shows the following:

- **Earnings - As of**: Latest earning generation date (also known as Calc date found in the export file) in the UTC timezone
- **Earnings - Total for selected period and filters**: Total sum of unique earnings in USD for the selected time period. Honors all page filters. Doesn't include claims.
- **Earnings - _Previous month total_**: Total sum of unique earnings in USD for the previous month and the month prior. Time filter doesn't apply. Honors all page filters. Doesn't include claims. If the earning is $0, then that month doesn't show.
- **Earnings - _Current month total_**: Total sum of unique earnings in USD for the current month. Time filter doesn't apply. Honors all page filters. Doesn't include claims. If the earning is $0, then that month doesn't show.
- **Payments – As of**: Latest payment order creation date in the UTC timezone.
- **Payments - Total  for selected period and filters**: Total sum of unique payments in USD for the selected time period. Selective filters only apply: Enrollment ID, Program, Earning Type, Payment status and Payment ID.
- **Payments - _Previous month total_**: Total sum of unique payments received in the previous month and month prior in USD. Selective filters only apply: Enrollment ID, Program, Earning Type, Payment status and Payment ID. If the payment is $0, then that month doesn't show.
- **Payments - _Current month total_**:  Total sum of unique payments received in the current month in USD. Selective filters only apply: Enrollment ID, Program, Earning Type, Payment status and Payment ID. If the payment is $0, then that month doesn't show.
- **Estimated payments – As Of**: Latest payment order creation date in UTC.
- **Next estimated payments - Total**: Total sum of estimated payments in USD for the selected time period. Honors all page filters.
- **Next estimated payments: _Current month_, _Next month_ and _Current month +1_**: Breakdown of estimated payments by month in USD. Time filter doesn't apply. Honors all page filters.
- **Earnings - by payment status**: Total earnings in USD by status for the selected time period. Honors all page filters. To learn more, see [Payment status](#payment-status)
- **Earnings – by lever**: Total earnings in USD by lever for the selected time period. Honors all page filters.
- **Earnings - by earning type**: Total earnings in USD by earning type like Co-op, Rebate, Fee, IndirectRebate for the selected time period. Honors all page filters.
- **Earning and Payments**: Earning and payment (pretax) trends. Honors all page filters. Earnings trend doesn't include claims.
- **Earnings summary**: Earnings view by customer or by program.
  - **By customer**: Shows top 50 customers' earnings and the payments (pretax). The view is sorted by default with earnings USD with highest on top. The data can be sorted by all columns, but only on the result sets displayed in the user interface. This view can be downloaded. You can also search for any customer.
  
  > [!NOTE]
  > If the earnings don't have a customer name, it shows up as blank. For example, earnings resulting from manual adjustments, local/global campaign earnings, or growth levers are usually measured at partner ID or product level.
  
  - **By program**: Shows top 50 program/engagement (applicable for Microsoft Commerce Incentives only)/lever earnings and the payments (pretax). The view is sorted by default with earnings USD with highest on the top. The data can be sorted by all columns, but only on the result sets displayed in the user interface. This view can be downloaded.
- **Payout summary**: The payment order view shows the payments that have been sent and are pending.
  
  Because the payment order is an aggregated representation of all earnings belonging to a program, earning type and payment method, there are restrictions on the type of filters that can be applied to this section. Only Enrollment ID/Location, Program Name, Earning Type, Payment status and Payment ID, filters apply.
  
  The **By sent** view shows all payments that have been sent successfully by Microsoft.
  
  Payment Date, Payment ID, Enrollment ID, Program, Earnings (USD), Earnings in payment currency, Payment in payment currency, Documents (Payment remittance letter, Service fee tax, credit note), Withholding Tax, Other taxes, Status, Credit Invoice reference where applicable for all payments received in the past three years. Select customizable columns to view the entire list and select/deselect required columns. This view is sorted by Payment Date with latest on the top. The data can be sorted by all columns, but only on the result sets displayed in the user interface.
  
  The **By pending** view shows all earnings that aren't in **Sent** or **Unprocessed** state. It means a payment order creation has commenced. Any of the other statuses you see other than **Upcoming** means that either the minimum threshold isn't met, or money has been escheated, or bank/tax information isn't up to date, or tax invoice is rejected.
  
  Only earnings (USD), earnings, payment status, and credit invoice reference is shown at this stage.

- **Downloads available via Earnings page**: Detailed earnings and associated reconciliation details and payment status can be obtained from these reports:

  - [Earnings-Default](./earnings-default.md)
  - [Earnings-Growth](./earnings-growth.md)
  - [Earnings-Marketplace](./earnings-marketplace.md)
  - [Earnings-Store](./earnings-store.md)
  - [Earnings-Payments](./earnings-payments.md)

## Page filters

This page contains multiple filters, each of which supports multi-select options.

The time filter includes options for 3 months, 6 months, 12 months, 36 months, or custom dates. When you select three months, the report returns data for the past three months starting from today.

| Filter attribute        | Description        | Applicability   |
| ----------------------- | ------------------ | --------------- |
| Enrollment ID, Location | Partner ID with which you're enrolled in the program.   |  Applies to the whole page. |
| Program Name            | Incentive, store or marketplace program name.   |  Applies to the whole page. |
| Solution Area           | High level product categorization. For example, Azure, Modern Work and Security.  | Useful only for Microsoft Commerce Incentives. Applies to all except the Payments, Estimated Payments and Payment summary views.  |
| Partner Role            | Categorization of the kind of engagement, for example, build intent, transact, consume and use. Learn more about [Partner roles](#partner-roles). | Applicable for Microsoft commerce incentive only. Applies to all except the Payments, Estimated Payments and Payment summary views. |
| Engagement name         | Name of the incentive engagement under Microsoft commerce incentive program.    | Useful only for Microsoft Commerce Incentives. Applies to all except the Payments, Estimated Payments and Payment summary views.  |
| Lever                   | Reflects the calculation rule/policy. |  Applies to the whole page. |
| Earning Type            | Type of earning. Examples: Rebate, Fee, Co-op, Indirect Rebate.        | Applies to the whole page. |
| Status                  | Reflects the status of an earning until it's sent out. |  Applies to the whole page.  |
| Payment ID              | Includes both the payment ID of a payment order as it reflects in the bank payment or credit note, and the payment month.<br>Search by payment ID or by the payment month. | Applies to the whole page. |

## Common tasks using the earnings page

### See earning per program/lever all-up
  
In **Earnings Summary**, select by program view and download the view to get the program lever breakdown. The result set is limited to 50 rows. Apply filters to make it more effective. For example, to understand how a particular country or enrollment location is doing, narrow down the enrollment IDs.

For Microsoft commerce incentives, view all Azure earnings and understand the breakdown by lever.

Set Solution Area filter as **Azure**. Choose **By program** to review the earnings by all levers for Azure based engagements. The result set is limited to top 50 earning levers across Azure engagements.

### See how much you're earning through Modern Workplace and Security workshops

- Set the **Solution Area** filter as **Modern Workplace and Security**.
- Set the **Partner Role** filter as **Build Intent**.

### See earnings per customer

The **Earnings summary – by customer** view shows the earnings per customer for the top 50 customers. To search for a customer, type their name in the search box by Customer view. You can apply program filters, engagement filters, or other filters to understand the customer earnings for the chosen criteria.

This report doesn't include manual adjustments, earnings from growth levers that measure revenue or usage growth at partner or product level.

### See how much you earned for program or lever for the transactions, usage or consumption that you drove in the last month

Refer to the previous month's earnings in the **Earnings** tile on the top left. Completeness of earnings is subject to when the earnings are computed.

### See how much you got paid for this month

All up payment for current or previous month can be obtained by looking at the current and previous month $ value in the Total payments card. For older months, apply the time filter to desired month and consume the Total value.

### Understand the earning breakdown at program lever level for a payment ID

Set the time filter to 36 months if the payment is older than six months and apply the Payment ID filter. You can view the customer level earnings and alternatively the lever level earning breakdown in the Earning summary.

### Look up earnings for a date range

Use the custom time filter to select a date range (for example, from July 1, 2023 to September 30, 2023). The results filter down the page to show earnings belonging to that time period.

### Look for all earnings for which payment orders have been successfully sent out by Microsoft

Set the preferred time filter and set the Status filter to Sent. You can view the earnings by customer and earnings by program/lever in the Earnings summary section. Alternatively, if you just want to know the high-level number without a customer/program/lever breakdown, select **By status** on the Earnings chart on the left.

### Look for earnings corresponding to Dynamics 365 engagements only

Set the preferred time filter and navigate to Lever section of the page filters and type **D365** in the search bar. The results only show all Dynamics 365 levers. To view the corresponding earnings, select **1**, **many**, or **all**.

### See results for your country or region for business applications

Set the preferred time filter and navigate to the **Enrollment ID** section of the filter pane and choose the preferred IDs belonging to country or region and set Solution Area filter as **Business Applications**.

### See top earning engagements in Azure

Set the preferred time filter, and set the **Solution area** filter to **Business applications**. In the **Earnings summary** section, select **By program**. The results show the earnings for all Azure engagements.

### See your monthly earning trend for an Azure engagement, or a lever or solution area

Set the **time filter** as **6 months**, **12 months**, or **Custom**, then apply the right **Solution area**, **Engagement** or **Lever** filter. The **Earnings and Payments** trend chart provides you with the view.

### Show total unpaid earnings

Multiselect all payment statuses except **Sent**. The total earning outcome reflects the amount that is still unpaid except for earning type **Co-op**. The co-op earnings never progress to a state beyond **Upcoming**.
Use the **Claim management experience** to understand the pending co-op amount compared to how much has been claimed.

### See the payment remittance document, credit note, or service fee tax document

Find this document in the **Payment summary** section corresponding to the payment you received.

### Show all the individual payment orders sent to you

See the **Payment summary** to view and download payment order details for the last three years.

### See the earnings corresponding to a single payment ID or payment month

Search for the month in the Payment ID filter and multi-select all the payment IDs you want to view the earnings for. If you're interested in only one payment ID, just select that.

### See the earnings corresponding to the 'By pending view' of Payment summary?

Each payment order is defined at a program, earning type, enrollment ID level. Apply all these filters and choose all Payment status except Sent, Unprocessed to get the page filtered down to earnings corresponding to each line you see in the **Payment Summary – by pending** view.

## Payment status

| **Payment status**   | **Reason**             | **Partner action required?** |
| ------------------------ | ---------------------- | ---------------------------- |
| Unprocessed              | The earning is eligible for payment. It stays in this state for a cooling period as defined in the program guide for the Incentives program.<br> Example: An earning for Azure consumption that happened in June 2023 is usually computed in July 2023 and paid in August 2023. Until end of July 2023, it shows as Unprocessed.<br> | No |
| Upcoming  | Payment order generated pending internal reviews before payment is processed.           | No |
| Pending tax invoice      | Your tax invoice is incomplete or invalid.  | You must update your tax invoice to be paid.|
| Rejected during review   | Payment was rejected during review.     | Contact Microsoft support for details. |
| Failed  | Payment failed due to a Microsoft system error. | No, Microsoft reaches out to you if needed. |
| In progress              | Payment is in progress.| No |
| Incorrect payment        | Payment recouping is in progress.             | No |
| Sent                     | Payment has been sent to your bank.           | No |
| Reprocessing             | Payment encountered a Microsoft system error and is being reprocessed.            | No |
| Reversed                 | Payment was reversed by your bank and will be sent again in the next payment cycle. | No |
| Tax invoice rejected     | Your tax invoice was rejected during review. All pending payments are on hold until the tax invoice review is complete.            | Contact Microsoft support for details.          |
| Tax invoice under review | Your tax invoice is being reviewed. Your payment will be released after the tax invoice has been approved. | No |
| Rejected                 | The payment was rejected by your bank.        | Contact your bank for details. |
| Forfeited                | Applicable to non-US partners only. When we don't have valid payment (bank) and/or tax instruments from the partners to process the payment, Microsoft holds the payment for the partners and continues to attempt to process the payment for up to six months (180 days) after the initial failure of the payment (typical SLA = 45 days). If we still don't have partners valid payment and tax instruments to process the payment, Microsoft forfeits these earnings. These earnings show as **Forfeited** on the partner statement. Alternatively, if partner hasn't accumulated more than $200 within a program year, earnings are forfeited. | Payment Instrument and tax invoice must always be kept up to date. |
| Escheated                | For US-based partners (location partner ID is registered to an address located in the United States). If the partners have no earning for consecutive 18 months, all earnings that we're unable to process for more than 45+180 days after the original earning period should be sent to the Unclaimed Property (UCP) team based in Fargo. | No          |

## Partner roles

| **Partner role**   | **Description** |
| ------------------ | --------------- |
| Build intent – Partner activities <br>Build intent – Advisor <br> Build with | Encourage customers to pursue Microsoft solutions and prove Microsoft solution value. |
| Transact           | Facilitate customer purchasing motions.|
| Use or consume     | Integrate solutions into customer environments and increase consumption. |

## Features that will be available during general availability of the page in the Earnings workspace

In the reports page, you'll be able to select report type, apply filters, and queue a download in addition to queueing up from the respective page.

## Next steps

- [Earnings default](./earnings-default.md)
- [Earnings growth schema](./earnings-growth.md)
- [Earnings marketplace schema](./earnings-marketplace.md)
- [Earnings store schema](./earnings-store.md)
- [Earnings payments](./earnings-payments.md)