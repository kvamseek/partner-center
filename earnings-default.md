---
title: Earnings - Default page in Partner Center
description: Learn about the default schema for the earnings page
ms.date: 9/20/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-earnings
ms.topic: article
author: deeparamani
ms.author: deramani
---

# Earnings – Default report in Partner Center

**Appropriate roles**: *Incentives*: Incentives admin | Incentives user; *Marketplace/Store*: Financial contributor

The **Default** report shows details on earnings, payments, and associated reconciliations. The template includes incentive-specific, store-specific, and marketplace-specific attributes. The info is applicable for all incentive, store and marketplace programs on Partner Center.

Transactional details like customers and subscriptions aren't available for earnings resulting from multiple consumption, usage, or transactions in this report. To see details, download the [Earnings- Growth report](./earnings-growth.md). Transactional details aren't available for global, local campaigns, or manual adjustments by design.

To get this report:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Earnings**.
1. Select **Download report > Earnings | Default**, and follow the instructions to get the report. To learn more, see [Get detailed earnings reports](earnings-reports.md). The report contains the following attributes:

## Schema

| Attribute name | Description | Applicability for incentive programs/ marketplaces |
| ---| ---| --- |
| agreementEndDate | Agreement end date | Applicable for Enterprise agreement based programs only |
| agreementNumber | Agreement number | Incentive programs. Applicable for Enterprise agreement based setup only. |
| agreementStartDate | Start date of the agreement | Applicable for Enterprise agreement based programs only |
| baseline | Indicates the value that the partner must surpass in order to earn incentives | Applicable for Microsoft commerce incentives quarter over quarter growth, high water mark based engagements<br><br>Introduced and available effective January 2023 |
| baselineType | Indicates the type of baseline measure, for example, $ or HWM (high water mark) | Applicable for Microsoft commerce incentives quarter over quarter growth, high water mark based engagements<br><br>Introduced and available effective January 2023 |
| bucketSize | Indicates the bucket-size for milestone based programs | Incentive programs only |
| calculationDate | Date the earning was calculated in the system | All |
| claimId | Claim identity number generated at the time of POE submission in the Claim management page (or) planId in the Plan management page (or) CPOR claim. | Incentive programs only |
| compensableUnits | Compensable units are calculated by subtracting the Prior High Water Mark (HWM) at the start of the month by the tenant/workload from the paid seats at the end of the month by tenant/workload. For example, Compensable units by tenant and workload = Paid seats – Prior HWM. | Applicable for Microsoft commerce incentives – Modern Workplace Usage and Online Advisor. Available only from October 2023. |
| customerCountry | Customer country/region | Marketplaces |
| customerEmail | End customer email ID | Marketplace |
| customerName | May be blank | Incentive programs only (exception: OEM) and marketplaces. For CSP transactions, Marketplace shows the name of the CSP |
| customerTenantId | Tenant ID of the end customer | Available for all new commerce transactions, usage based incentives and Marketplace |
| desktopCount | Number of desktops per agreement | Applicable for Enterprise agreement based programs only |
| distributorId | Distributor identifier | Incentives - some programs only |
| distributorName | Distributor name | Incentives - some programs only |
| earningAmount | Earning Amount in the original transaction currency | All |
| earningAmountInLastPaymentCurrency | Earning amount in the last payment currency (This field is empty when no prior payments have been paid) | |
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
| fundCategory | Name of the fundCategory. Populated only for paid claims. | Plan based OEM programs only |
| instantRebateAmount | Total instant rebate applied on the invoice at the time of purchase. | OEM Jumpstart Tier 1 only |
| invoiceDate | Date of the invoice | Available only for OEM Jumpstart Tier 1 |
| invoiceNumber | Invoice number (applicable for enterprise only) | Incentives and marketplaces - some programs only |
| isPrivateOffer | Indicates if offer is private or public. True indicates Private and false indicates Public offer | Marketplaces<br><br>Available from December 1, 2022. |
| lastPaymentCurrency | Last payment currency (Blank if no prior payment paid) | |
| lever | Indicates business rule for the earning | All |
| LicensingProgramName | Name of the licensing program | |
| LineItemId | Individual line in a customer's invoice | |
| localProviderSeller | Local provider/seller of record | |
| Maturity month | The estimated payment month | All |
| milestone | Earning milestone attained | Milestone based incentive programs |
| OrderId | Relates to a customer's invoice | Marketplaces |
| parentProductId | Unique parent product identifier. If there isn't a parent product for the transaction, then Parent Product ID = Product ID. | Marketplaces |
| parentProductName | Name of the parent product. If there isn't a parent product for the transaction, then parentProductName = productName. | Marketplaces |
| participantId | The primary identity of the partner earning under the program | All |
| participantIdType | Mostly program ID for incentive programs and Seller IF for Marketplaces | All |
| participantName | Name of the earning partner | All |
| partnerAssociation | Type of relationship partner has to a customer. Examples: reseller, PAL.Owner | For all incentive, store and marketplace programs. Available from October 2021. |
| partnerCountryCode | Location/country/region of the earning partner | All |
| partnerRole | Categorization of the kind of engagement. Examples: build intent, transact, deploy and use. | For Microsoft commerce incentives only. Available from October 2021. |
| partNumber | Always blank | Some incentive programs and marketplaces |
| paymentId | Unique identifier correlates all transactions in the transaction report with a payment in the payment report | All |
| paymentStatus | Payment status | All |
| paymentStatusDescription | Friendly description of payment status | All |
| productId | Unique product identifier | Marketplaces |
| productName | Product name linked to the transaction | All |
| productType | Type of product, such as App, Add-on, or Game | Marketplaces |
| Program Code | String to map with the program name | |
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
| resellerCountry | | |
| resellerId | Reseller identifier | Incentives - some programs only |
| resellerName | Reseller name | |
| resourceId | The identity of the customer resource managed by partner. | Available only for certain cases like Business Applications usage as PAL association can only be at resource level. |
| SkuId | SKU ID as defined during publishing. An offer may have many SKUs, but a SKU can only be associated with a single offer. | Incentives - some programs only |
| solutionArea | High level product categorization. For example, Azure, ModernWork and Security. | For Microsoft commerce incentives only. Available from October 2021. |
| storeFee | The amount retained by Microsoft as a fee for making the app or add-on available in the Store | Marketplaces |
| subscriptionEndDate | Subscription end date | Incentives - some programs only |
| subscriptionId | Subscription identifier associated with customer | Incentives - some programs only |
| subscriptionStartDate | Subscription start date | Incentives - some programs only |
| taxCity | | |
| taxCountry | | |
| taxRemitModel | Party responsible for remitting taxes (sales, use, or VAT/GST taxes) | Marketplaces |
| taxRemitted | Amount of tax remitted (sales, use, or VAT/GST taxes) | Marketplaces |
| taxState | Customer's state | |
| taxZipCode | Customer's ZIP/postal code | |
| tpan | Indicates the third-party ad network | Marketplaces Ads only |
| transactionAmount | Transaction amount in the original transaction currency based on which earning is generated | All |
| transactionAmountUSD | Transaction amount in USD | All |
| transactionCountryCode | Country/region code in which the transaction happened | |
| transactionCurrency | Currency in which the original customer transaction occurred (which isn't partner location currency) | All |
| transactionDate | Date of the transaction. Useful for programs where many transactions contribute to one earning | All |
| transactionExchangeRate | Exchange rate data used to show the corresponding transaction USD amount | All |
| transactionId | Unique identifier for the transaction | All |
| transactionPaymentMethod | Customer payment instrument used for the transaction, such as Card, Mobile Carrier Billing, or PayPal | Marketplaces |
| transactionType | Type of transaction, such as purchase, refund, reversal, or chargeback | Marketplaces |
| userCount | Number of users per agreement | Applicable for Enterprise agreement based programs only |
| workload | Name of the workload, service name, for example, spo (for Sharepoint), powerbistandalone (Power BI Standalone), Virtual Machines | Available for Azure consumption and Modern Workplace/BizApps usage based incentives |

## Next steps

- [Earnings growth schema](./earnings-growth.md)
- [Earnings marketplace schema](./earnings-marketplace.md)
- [Earnings store schema](./earnings-store.md)
- [Earnings payments](./earnings-payments.md)
- [Ineligible revenue usage schema](./earnings-ineligible-revenue-usage.md)
