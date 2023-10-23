---
title: Earnings – MaxCapBalance report in Partner Center
description: Learn about MaxCapBalancereports
ms.service: partner-dashboard
ms.subservice: partnercenter-earnings
ms.topic: article
author: deeparamani
ms.author: deramani
ms.date: 10/19/2023
---

# Earnings – MaxCapBalance report in Partner Center

**Appropriate roles**: *Incentives*: Incentives admin | Incentives user

The **MaxCapBalance** report shows the maximum cap balance, the total earnings and the balance available with the required attributes at which level the max cap scope is defined. Currently this information is only available for incentives engagements offered to Cloud solution providers transacting in new commerce, Modern Work usage and Surface.

Depending on the level at which max cap is defined, this file shows only those attributes.

To get this report:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Reports**.
1. Select **Download report** > **MaxCapBalance**, and follow the instructions to get the report. To learn more, see [Get detailed earnings reports](earnings-reports.md). The report contains the following attributes:

| Attribute name | Description | Applicability |
| --- | --- | --- |
|participantID | Partner identifier enrolled in the program | |
|participantType | Type of partner identifier, such as seller, MPN, and so on| |
|participantName  | Enrolled partner organization name | |
|earningParticipantID | Partner identity in the relationship | |
|earningParticipantIDType | Type of partner identifier, such as seller, MPN, and so on | |
|earningParticipantName | Earning participant name; useful when multiple transacting partner IDs are mapped into a single enrollment ID | |
|earningParticipantCountryCode | Earning participant country or region code | |
|programName | Incentive program name | |
|programID | Incentive program identity | |
|engagementName | Engagement name; applicable only for Microsoft commerce incentives | |
|engagementID | Engagement identity; applicable only for Microsoft commerce incentives | 
|leverName | Incentive rule | Available only if max cap is defined at lever level|
|customerID | Customer identity | Available only if max cap is defined at customer level|
|customerName | Customer name | Available only if max cap is defined at customer level|
|customerCountryCode | Customer country or region code | Available only if max cap is defined at customer level|
|maxCapUSD | Maximum amount that can be earned in USD, for the engagement/lever/policy period | |
|maxCapEffectiveStartDate | Maximum cap effective start date for this engagement/lever/policy period | |
|maxCapEffectiveEndDate | Maximum cap effective end date for this engagement/lever/policy period | |
|totalEarningsUSD | Total earnings in USD for the engagement/lever/policy period | |
|balanceEarningOpportunityUSD | Pending earning opportunity in USD for engagement/lever/policy period<br><br>maxCapUSD - totalEarningsUSD | |
|targetRevenueUSD | Target revenue above which partner can earn | Applicable only for Surface engagements at this time|
|maxCapBalanceRefreshDate | Maximum cap balance refresh date | Incentives only|
