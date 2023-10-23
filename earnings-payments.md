---
title: Earnings - Payments report page in Partner Center
description: Learn about payments reports in the earnings page on Partner Center
ms.date: 9/20/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-earnings
ms.topic: article
author: deeparamani
ms.author: deramani
---

# Earnings – Payments report in Partner Center

**Appropriate roles**: *Incentives*: Incentives admin | Incentives user; *Marketplace/Store*: Financial contributor

The **Payments** report shows payment order details for all incentive, marketplace and store programs.

To get this report:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Earnings**.
1. Select **Download report > Earnings | Payments**, and follow the instructions to get the report. To learn more, see [Get detailed earnings reports](earnings-reports.md). The report contains the following attributes:

## Schema

| Attribute name | Description |
| -------------- | ----------- |
| participantID | The primary identity of the partner earning under the program |
| participantIDType | Usually program ID for Incentives programs and Seller ID for Store programs |
| participantName | Name of the earning partner |
| programName| Incentives/store program name |
| earned | Amount earned in the Pay To currency for that program/participantID |
| earnedUSD | Amount earned for the program/participant ID, in USD |
| withheldTax| Amount of tax withheld in the Pay To currency for the program/participantID |
| salesTax | Total amount of sales tax in the Pay To currency for the program/participantID (applicable for incentives programs only) |
| serviceFeeTax | Total amount of serviceFeeTax in Pay To currency for the program/participantID (applicable for store programs and Azure Marketplace only) |
| totalPayment | Total payment in local currency excluding the withholding tax and including the sales tax (if applicable) for the program/participantID |
| currencyCode | Pay To currency code |
| paymentMethod | The method used to pay the partner, for example, electronic bank transfer, credit note |
| paymentID | Unique identifier for the payment. This number is usually visible in your bank statement (applicable for SAP payments only).|
| paymentStatus | Payment status |
| paymentStatusDescription | Friendly description of payment status |
| paymentDate| Date payment was sent from Microsoft |

## Next steps

- [Earnings - Default](./earnings-default.md)
