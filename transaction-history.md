---
title: Transaction history
description: Learn about transaction history.
ms.subservice: partnercenter-payouts
ms.service: partner-dashboard
ms.topic: article
author: deeparamani
ms.author: deramani
ms.date: 08/14/2023
---

# Transaction history

**Appropriate roles**:

- **Incentives**: Account admin | Global Admin | Incentive admin | Incentive user
- **Marketplace/Store**: Account owner | Financial contributor

## Transaction history page

On the **Transaction history** page, you can view transactions for the current fiscal year (July 1 - June 30) and the preceding two fiscal years.

**Transaction history** shows all earnings eligible for payout, including payments not yet sent, and includes:

- **Earnings sent this year**: Total earnings and breakdown of earnings that have been paid and will be paid in the upcoming month
- **Estimated payment month**: Total earnings expected in the upcoming months
- **Earnings and payment trend**: Monthly earning and payment amounts for the past 36 months
- **Download**: A link you can use to download transaction details in .csv or .tsv format

> [!NOTE]
> You can only see data for PartnerIDs and programs that you're associated with. If you want to see more data, work with your account administrator to be assigned the required permissions.
>

##### Filtering output

- You can filter by *Date range* to show the past 3, 6, 12, or 36 months using the date range selection at the top right corner of the page. You can also select a custom date range up to 36 months. The default date range is 12 months.
- You can also filter by *Enrollment ID*, *Program*, *Payment ID*, *Earning type*, *Lever*, and *Status*.

## Eligible earnings

Earnings are eligible for payout when:

- An ISV has completed all bank and tax information in Partner Center
- As ISV has earned more than USD50
- The ISV account is active
- The customer has been billed (for EA transactions) or the payment has been received (for non-EA transactions)

## Getting more details

To see more details about an earning, use the following step:

- Select the down arrow at the right-hand side of the page.

  Doing so displays the lever, revenue amount, product, and customer.
  
- Contact support if data that you need is unavailable.
  
If an earning is the result of an *adjustment* and not a transaction, the *Product* and *Customer* fields aren't displayed.

## Transaction history summary

**Transaction history** shows earning details, including the origin of the earning from the product sold earning dates, status, and estimated payment month.

Earning transactions are shown when the transaction meets payout eligibility. To understand why you might have missing or unexpected earnings, see [Common questions about commercial marketplace payouts](payout-faq.yml#why-are-my-earnings-missing-).

:::image type="content" source="media/payouts/transaction-history.png" alt-text="Transaction history.":::

The following table explains each column on the **Transaction history** page.

| Column name | Description |
| --- | --- |
| EarnedDate | The date of purchase |
|Earning type |The type of earning, such as Sell, Rebate, or Co-op|
|Total amount |The net earning amount. (In the commercial marketplace, it's after deducting the standard marketplace fee.)
|Status |- *Upcoming*: Earnings are in pending cooling period.<br>- *Processed*: Earnings are prepared for next payment.<br>- *Sent*: Earnings have been paid.|
|Estimated payment month|The estimated month that earnings will be paid. For more information, see the next section, [Estimated payment month](#estimated-payment-month).|

#### Estimated payment month

The **Transaction history** page has a table showing your estimated payments for the next few months. This information makes reconciliations and payment projections easier.

You can also export this information as *Transaction history* and *Summary report*.

*Estimated payment month:*

- Is calculated from program configuration rules and timelines and is processed in the next/upcoming payment cycle.
- Is available for all earning types except co-op, which display as **Not applicable**.
- Appears as **Not available** for earnings before July 1, 2020.

The following table is an example of an estimated payment month:

| Month | Amount |
| ------ | :-----------: |
|  September 2020 |  USD7,273.99   |
|  October 2020 | USD8,692.30  |
|  November 2020 | USD107.89  |

#### Estimated payments versus actual payments

The estimated payment may vary from the actual payment for the following reasons:

- *Earning restatement*: If earnings are recalculated, the actual amount will be different.
- *Adjustments*: The actual amount varies depending on adjustments that occurred or were submitted.
- *Rules change*: A change in rules may result in recalculation of the actual amount paid.
- *Payable*: If there's a payment failure, the actual amount could be different.

## Payment eligibility rules

Your payment is only released in the projected month if your program's threshold and payment eligibility rules are met.

*Payment eligibility rules* include but aren't limited to:

- Your tax profile must be up to date.
- Your earnings must meet or exceed the minimum earning threshold defined in your program guide.
- Payout on hold if you select the *Hold my Payment* option on the profiles assignment page.
- Payout instrument not available: Payment or/and Tax profile isn't completed.

## Transaction history download

To see more details about earnings, select **Download**.

The following table explains each column in the report.

| Column name | Description | Applicability for incentive programs/ Marketplaces|
| --- | --- | --- |
| agreementEndDate | Agreement end date | Applicable for Enterprise agreement based programs only |
| agreementNumber | Agreement number | Incentive programs. Applicable for Enterprise Agreement based setup only. |
| agreementStartDate | Start date of the agreement | Applicable for Enterprise agreement based programs only |
| baseline     | Indicates the value that the partner must surpass in order to earn incentives | Applicable for Microsoft commerce incentives quarter over quarter growth, high water mark based engagements<br><br>  Introduced and available effective January 2023  |
| baselineType | Indicates the type of baseline measure, for example, $ or HWM (high water mark) | Applicable for Microsoft commerce incentives quarter over quarter growth, high water mark based engagements<br><br> Introduced and available effective January 2023 |
| bucketSize | Indicates the bucket-size for milestone based programs | Incentive programs only |
| calculationDate | Date the earning was calculated in the system | All |
| claimId | Claim identity number generated at the time of POE submission in the Claim management page (or) planId in the Plan management page (or) CPOR claim.  |Incentive programs only |
| compensableUnits | Compensable units are calculated by subtracting the Prior High Water Mark (HWM) at the start of the month by the tenant/workload from the paid seats at the end of the month by tenant/workload. For example, Compensable units by tenant and workload = Paid seats – Prior HWM. | Applicable for Microsoft commerce incentives – Modern Workplace Usage and Online Advisor. Available only from October 2023. |
| customerCountry | Customer country/region | Marketplaces |
| customerEmail | End customer email ID | Marketplace |
| customerName | May be blank | Incentive programs only (exception: OEM) and marketplaces. For CSP transactions, Marketplace shows the name of the CSP |
| customerTenantId | Tenant ID of the end customer | Available for all new commerce transactions, usage based incentives and Marketplace |
| desktopCount | Number of desktops per agreement | Applicable for Enterprise agreement based programs only |
| distributorId | Distributor identifier | Incentives - some programs only |
| distributorName | Distributor name | Incentives - some programs only |
| earningAmount | Earning Amount in the original transaction currency | All |
| earningAmountInLastPaymentCurrency | Earning amount in the last payment currency (field will be empty if no prior payments have been paid) |  |
| earningAmountUSD | Earning amount in USD | All |
| earningDate | Date of the earning | All |
| earningExchangeRate | Exchange rate used to show the corresponding USD amount | All |
| earningId | Unique identifier for each earning | All |
| earningParticipantId, earningParticipantName, and earningParticipantIdType | Partner identity in the transact relationship | For all incentive, store and marketplace programs. Useful when multiple transacting partner IDs are mapped into a single enrollment ID. Available from October 2021. |
| earningRate | Incentives rate applied on transaction amount to generate an earning | All |
| earningType | Indicates whether it's fee, rebate, co-op, sell, and so on | All |
| engagementId | Engagement identifier | Applicable for Microsoft commerce incentives |
| engagementName | Engagement name | Applicable for Microsoft commerce incentives |
| estimatedPaymentMonth | Month in which the earning is likely to be paid. Determined based on transaction date. | All |
| exchangeRateDate | Exchange rate date used to calculate EarningAmount USD | All |
| externalReferenceId | Unique identifier for the program | Direct-Pay programs (incentives and marketplaces) |
| externalReferenceIdLabel | Unique identifier label | Direct-Pay programs (incentives and marketplaces) |
| fundCategory | Name of the fundCategory. Populated only for paid claims. | Plan based OEM programs only|
| instantRebateAmount | Total instant rebate applied on the invoice at the time of purchase. | OEM Jumpstart Tier 1 only |
| invoiceDate |  Date of the invoice | Available only for OEM Jumpstart Tier 1 |
| invoiceNumber | Invoice number (applicable for enterprise only) | Incentives and marketplaces - some programs only |
| isPrivateOffer | Indicates if offer is private or public. True indicates Private and false indicates Public offer  | Marketplaces </br></br> Available from December 1, 2022. |
| lastPaymentCurrency | Last payment currency (Blank if no prior payment paid) |  |
| lever | Indicates business rule for the earning | All |
| LicensingProgramName | Name of the licensing program |  |
| LineItemId | Individual line in a customer's invoice |  |
| localProviderSeller | Local provider/seller of record |  |
| Maturity month | The estimated payment month | All |
| milestone | Earning milestone attained | Milestone based incentive programs |
| OrderId | Relates to a customer's invoice  | Marketplaces|
| parentProductId | Unique parent product identifier. If there isn't a parent product for the transaction, then Parent Product ID = Product ID. | Marketplaces|
| parentProductName | Name of the parent product. If there isn't a parent product for the transaction, then parentProductName = productName. | Marketplaces |
| participantId | The primary identity of the partner earning under the program | All |
| participantIdType | Mostly program ID for incentive programs and Seller IF for Marketplaces| All |
| participantName | Name of the earning partner | All |
| partnerAssociation | Type of relationship partner has to a customer. Examples: reseller, PAL.Owner | For all incentive, store and marketplace programs. Available from October 2021. |
| partnerCountryCode | Location/country/region of the earning partner | All |
| partnerRole | Categorization of the kind of engagement, for example, build intent, transact, deploy and use. | For Microsoft commerce incentives only. Available from October 2021. |
| partNumber | Always blank | Some incentive programs and marketplaces |
| paymentId | Unique identifier correlates all transactions in the transaction report with a payment in the payment report | All |
| paymentStatus | Payment status | All |
| paymentStatusDescription | Friendly description of payment status | All |
| productId | Unique product identifier | Marketplaces|
| productName | Product name linked to the transaction | All |
| productType | Type of product, such as App, Add-on, or Game | Marketplaces|
| Program Code | String to map with the program name |  |
| programName | Incentive/store program name | All |
| purchaseOrderCoverageEndDate | Always blank | Incentive program - CRI |
| purchaseOrderCoverageStartDate | Always blank | Incentive program - CRI |
| purchaseOrderType | Type of purchase, for example BEC, TUP, NE orders | Applicable for Enterprise agreement based programs only |
| purchaseTypeCode | Always blank | Incentive program - CRI |
| purchaseTypeName | The purpose of Purchase Type is to group sales transactions that have similar purchase time methods. | Applicable for Enterprise agreement based programs only |
| quantity | Varies based on program. Indicates billed quantity for transactional programs | All |
| quantityAlt | Alternate quantity value | Optionally available for incentive programs, for example, Modern Work usage. Available only from October 2023. |
| quantityAltType | Alternate quantity unit, for example, PAU (Paid available units) | Optionally available for incentive programs, for example, Modern Work usage. Available only from October 2023. |
| quantityType | Indicates the type of quantity, for example, MAU (monthly active users), Seats. | For all incentive programs only. Available from October 2021. |
| reasonCode | Reason for adjustments | All |
| resellerCountry |  |  |
| resellerId | Reseller identifier | Incentives - some programs only |
| resellerName | Reseller name |  |
| resourceId | The identity of the customer resource managed by partner. | Available only for certain cases like Business Applications usage as PAL association can only be at resource level. |
| SkuId | SKU ID as defined during publishing. An offer may have many SKUs, but a SKU can only be associated with a single offer. | Incentives - some programs only |
| solutionArea | High level product categorization. For example, Azure, ModernWork and Security. | For Microsoft commerce incentives only. Available from October 2021. |
| storeFee | The amount retained by Microsoft as a fee for making the app or add-on available in the Store | Marketplaces|
| subscriptionEndDate | Subscription end date | Incentives - some programs only |
| subscriptionId | Subscription identifier associated with customer | Incentives - some programs only |
| subscriptionStartDate | Subscription start date | Incentives - some programs only |
| taxCity |  |  |
| taxCountry |  |  |
| taxRemitModel | Party responsible for remitting taxes (sales, use, or VAT/GST taxes) | Marketplaces|
| taxRemitted | Amount of tax remitted (sales, use, or VAT/GST taxes) | Marketplaces|
| taxState | Customer's state |  |
| taxZipCode | Customer's ZIP/postal code |  |
| tpan | Indicates the third-party ad network | Marketplaces Ads only |
| transactionAmount | Transaction amount in the original transaction currency based on which earning is generated | All |
| transactionAmountUSD | Transaction amount in USD | All |
| transactionCountryCode | Country/region code in which the transaction happened |  |
| transactionCurrency | Currency in which the original customer transaction occurred (which isn't partner location currency) | All |
| transactionDate | Date of the transaction. Useful for programs where many transactions contribute to one earning | All |
| transactionExchangeRate | Exchange rate data used to show the corresponding transaction USD amount | All |
| transactionId | Unique identifier for the transaction | All |
| transactionPaymentMethod | Customer payment instrument used for the transaction, such as Card, Mobile Carrier Billing, or PayPal | Marketplaces|
| transactionType | Type of transaction, such as purchase, refund, reversal, or chargeback | Marketplaces|
| userCount | Number of users per agreement | Applicable for Enterprise agreement based programs only|
| workload | Name of the workload, service name, for example, spo (for Sharepoint), powerbistandalone (Power BI Standalone), Virtual Machines | Available for Azure consumption and Modern Workplace/BizApps usage based incentives |

## Transaction adjustment codes

*Adjustments* are corrections made to earnings.

Adjustments usually don't have references to a single transaction or usage instance; they're performed at a later stage. You can understand the reason for an adjustment by referencing the **reasonCode** column in the download.

The following table lists reason codes for adjustments and their descriptions.

| Reason code   | Description   |
|------------------|:-------------------------------------|
| AR Compliance | Reduces earnings when Microsoft invoices aren't paid on time by the partner |
| Co-op rollover | Transfers co-op earnings to another period, or converts co-op earnings to rebate |
| Ops Adjustment | Corrects Microsoft system calculation errors |
| Ops Adjustment Microsoft incorrect calc | Corrects miscalculations |
| Ops Adjustment Microsoft incorrect enrollment | Corrects enrollment-related miscalculations |
| Partner mapping (subscription) MCI/CSP | Corrects subscription misalignment |
| Policy Exception | Adjustment that overrides a program rule  |
| Previous period earnings | Adjustment for earnings outside of the current earning period |

## Earning status

The following table explains the different earning statuses and whether any action is required.

| Earning status | Reason | Partner action required? |
| --- | --- | --- |
| Unprocessed | The earning is eligible for payment. It stays in this state for a cooling period as defined in the program guide for the Incentives program. | No |
| Upcoming | Payment order generated pending internal reviews before payment is processed. | No |
| Pending tax invoice | Your tax invoice is incomplete or invalid. | You must update your tax invoice to be paid. |
| Rejected during review | Payment was rejected during review. | Contact Microsoft support for details. |
| Failed | Payment failed due to a Microsoft system error. | Contact Microsoft support for details |
| In progress | Payment is in progress. | No |
| Incorrect payment | Payment recouping is in progress. | No |
| Sent | Payment has been sent to your bank. | No |
| Reprocessing | Payment encountered a Microsoft system error and is being reprocessed. | No |
| Reversed | Your bank reversed the payment. The payment will be sent again in the next payment cycle. | No |
| Tax invoice rejected | Your tax invoice was rejected during review. All pending payments are on hold until the tax invoice review is complete. | Contact Microsoft support for details. |
| Tax invoice under review | Your tax invoice is being reviewed. Your payment will be released after the tax invoice has been approved. | No |
| Rejected | Your bank rejected the payment. | Contact your bank for details. |

## Next steps

- [Revenue summary](./revenue-summary.md)
- [New payout data export page](./payouts-enhanced-exports.md)
- [Earnings and payment reconciliation FAQ](./reconciliation-faq.md)

