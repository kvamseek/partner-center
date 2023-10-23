---
title: Earnings - Marketplace page in Partner Center
description: Learn about earnings page reports
ms.date: 9/20/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-earnings
ms.topic: article
author: deeparamani
ms.author: deramani
---

# Earnings – Marketplace report in Partner Center

**Appropriate roles**: *Marketplace/Store*: Financial contributor

The **Marketplace** report shows earnings from the commercial marketplace. 

To get this report:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Earnings**.
1. Select **Download report > Earnings | Marketplace**, and follow the instructions to get the report. To learn more, see [Get detailed earnings reports](earnings-reports.md). The report contains the following attributes:

## Schema

| Attribute name | Description  |
| --- | --- |
| assetId  | Asset identifier |
| calculationDate  | Date the earning was calculated in the system  |
| customerCountry  | Customer country/region  |
| customerEmail  | End customer email ID  |
| customerName | May be blank |
| customerId | Tenant ID of the end customer  |
| earningAmount  | Earning Amount in the original transaction currency  |
| earningAmountInLastPaymentCurrency | Earning amount in the last payment currency (This field is empty when no prior payments have been paid)  |
| earningAmountUSD | Earning amount in USD  |
| earningDate  | Date of the earning  |
| earningExchangeRate  | Exchange rate used to show the corresponding USD amount  |
| earningId  | Unique identifier for each earning |
| earningParticipantId, earningParticipantName, and earningParticipantIdType | Partner identity in the transact relationship  |
| earningRate  | Incentives rate applied on transaction amount to generate an earning |
| earningType  | Indicates whether it's fee, rebate, co-op, sell, and so on |
| estimatedPaymentMonth  | Month in which the earning is likely to be paid. Determined based on transaction date. |
| exchangeRateDate | Exchange rate date used to calculate EarningAmount USD |
| externalReferenceId  | Unique identifier for the program  |
| externalReferenceIdLabel | Unique identifier label  |
| invoiceNumber  | Invoice number (applicable for enterprise only)  |
| isPrivateOffer | Indicates if offer is private or public. True indicates Private and false indicates Public offer |
| lastPaymentCurrency  | Last payment currency (Blank if no prior payment paid) |
| lever  | Indicates business rule for the earning  |
| LineItemId | Individual line in a customer's invoice  |
| localProviderSeller  | Local provider/seller of record  |
| Maturity month | The estimated payment month  |
| OrderId  | Relates to a customer's invoice  |
| parentProductId  | Unique parent product identifier. If there isn't a parent product for the transaction, then Parent Product ID = Product ID.  |
| parentProductName  | Name of the parent product. If there isn't a parent product for the transaction, then parentProductName = productName. |
| participantId  | The primary identity of the partner earning under the program  |
| participantIdType  | Mostly program ID for incentive programs and Seller IF for Marketplaces  |
| participantName  | Name of the earning partner  |
| partnerAssociation | Type of relationship partner has to a customer. Examples: reseller, PAL.Owner  |
| partnerCountryCode | Location/country/region of the earning partner |
| partNumber | Always blank |
| paymentId  | Unique identifier correlates all transactions in the transaction report with a payment in the payment report |
| paymentStatus  | Payment status |
| paymentStatusDescription | Friendly description of payment status |
| productId  | Unique product identifier  |
| productName  | Product name linked to the transaction |
| productType  | Type of product, such as App, Add-on, or Game  |
| Program Code | String to map with the program name  |
| programName  | Incentive/store program name |
| quantity | Varies based on program. Indicates billed quantity for transactional programs  |
| quantityType | Indicates the type of quantity, for example, MAU (monthly active users), Seats.  |
| reasonCode | Reason for adjustments |
| resellerCountry  |  |
| resellerId | Reseller identifier  |
| resellerName | Reseller name  |
| SkuId  | SKU ID as defined during publishing. An offer may have many SKUs, but a SKU can only be associated with a single offer.  |
| storeFee | The amount retained by Microsoft as a fee for making the app or add-on available in the Store  |
| subscriptionId | Subscription identifier associated with customer |
| taxCity  |  |
| taxCountry |  |
| taxRemitModel  | Party responsible for remitting taxes (sales, use, or VAT/GST taxes) |
| taxRemitted  | Amount of tax remitted (sales, use, or VAT/GST taxes)  |
| taxState | Customer's state |
| taxZipCode | Customer's ZIP/postal code |
| tpan | Indicates the third-party ad network |
| transactionAmount  | Transaction amount in the original transaction currency based on which earning is generated  |
| transactionAmountUSD | Transaction amount in USD  |
| transactionCountryCode | Country/region code in which the transaction happened  |
| transactionCurrency  | Currency in which the original customer transaction occurred (which isn't partner location currency) |
| transactionDate  | Date of the transaction. Useful for programs where many transactions contribute to one earning |
| transactionExchangeRate  | Exchange rate data used to show the corresponding transaction USD amount |
| transactionId  | Unique identifier for the transaction  |
| transactionPaymentMethod | Customer payment instrument used for the transaction, such as Card, Mobile Carrier Billing, or PayPal  |
| transactionType  | Type of transaction, such as purchase, refund, reversal, or chargeback |
| workload | Name of the workload, service name, for example, spo (for Sharepoint), powerbistandalone (Power BI Standalone), Virtual Machines |

## Next steps

- [Earnings - Default](./earnings-default.md)
