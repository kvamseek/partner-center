---
title: Earnings – Growth page in Partner Center
description: Learn about earning growth page reports
ms.date: 9/20/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-earnings
ms.topic: article
author: deeparamani
ms.author: deramani
---

# Earnings – Growth report in Partner Center

**Appropriate roles**: *Incentives*: Incentives admin | Incentives user

The **Growth** report shows earnings, payment, and associated reconciliation details for incentives levers that measure growth. Examples: Azure quarter-over-quarter growth, Surface Accelerate growth incentives.

Use this report to:

- Understand the distinct earnings for growth lever and the corresponding payment status.
- Understand the underlying reconciliation details like customer name, reseller name, subscription ID, and agreement number as applicable for the lever.

  > [!NOTE]
  > Earnings are generated from multiple transactions (multiple customers/resellers/products over a period of time). To enable traceability, each transaction considered to generate earnings is listed and the earning attributes are redundantly printed with associated transactions. Make sure to only sum up distinct earnings based on their earning ID.

To get this report:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Earnings**.
1. Select **Download report > Earnings | Growth**, and follow the instructions to get the report. To learn more, see [Get detailed earnings reports](earnings-reports.md). The report contains the following attributes:

## Schema

| Attribute name  | Description  |
| ---| --- |
| agreementNumber | Agreement Number |
| customerId  | Identity of the end customer |
| customerName  | Name of the end customer |
| distributorId | Distributor identity |
| distributorName | Distributor name |
| earningAmount | Earning Amount in the original transaction currency  |
| earningAmountUSD  | Earning amount in USD  |
| earningDate | Date of the earning  |
| earningExchangeRate | Exchange rate used to show the corresponding USD amount  |
| earningId | Unique identifier for each earning |
| earningRate | Incentives rate applied on transaction amount to generate an earning |
| earningType | Indicates whether it's fee, rebate, co-op, sell, and so on |
| engagementId  | Engagement identifier  |
| engagementName  | Engagement name  |
| estimatedPaymentMonth | Month in which the earning is likely to be paid. Determined based on transaction date. |
| exchangeRateDate  | Exchange rate date used to calculate EarningAmount USD |
| invoiceNumber | Invoice Number |
| lever | Indicates business rule for the earning  |
| participantId | The primary identity of the partner earning under the program  |
| participantIdType | Partner identity |
| participantName | Name of the earning partner  |
| partnerCountryCode  | Location/country/region of the earning partner |
| partNumber  | SKU or part number |
| paymentId | Payment identity as available in the bank payment  |
| paymentStatus | Payment status |
| programName | Incentive program name |
| resellerId  | Reseller identity  |
| resellerName  | Reseller name  |
| subscriptionEndDate | Subscription end date  |
| subscriptionId  | Subscription identity  |
| subscriptionStartDate | Subscription start date  |
| totalTransactionAmountUSD | Transaction amount in USD  |
| transactionCurrency | Currency in which the original customer transaction occurred (which isn't partner location currency) |
| transactionMonth  | Month of transaction, consumption or usage |

## Next steps

- [Earnings - Default](./earnings-default.md)
