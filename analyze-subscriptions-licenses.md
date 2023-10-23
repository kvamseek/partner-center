---
title: Subscriptions analytics dashboard (Tenant) – Cloud product performance
description: Learn how to use the metrics in the Subscription and license analytics page to identify your successes and areas that need more attention.
ms.service: partner-dashboard
ms.subservice: partnercenter-insights
author: kshitishsahoo
ms.author: ksahoo
ms.topic: article
ms.date: 8/1/2022
---

# Subscriptions analytics dashboard (tenant) – Cloud product performance

**Appropriate roles**: Global admin | User management admin | Admin agent | Sales agent

Data drives business decisions. Use the metrics in the **Subscription and license analytics** page to identify your successes and areas that need more attention. Use this information as you plan new business goals.

**CSP TTM revenue (USD)** represents the aggregated CSP billed revenue (USD) for the trailing 12 months (TTM) for the Partner Location Accounts and Partner Global Account (PGA) the CSP account is associated with. If you have other CSP accounts with a different PGA, you must sign in to each of them to view the corresponding aggregated TTM revenue. Select **Download details** to get a breakdown of the TTM revenue (USD) per PartnerID (formerly MPN ID).

> [!NOTE]
>Local currency prices (Legacy Commerce FX) in Commercial are managed to within +/-5% of US dollars. The Legacy Commerce exchange rate (FX) is different from billing FX rates used by Azure in the Modern Commerce experience. The Modern Commerce billing FX rates are based on Microsoft P&L rates (Reuters FX rates from Treasury feed). Legacy Commerce FX rates are Microsoft confidential.

The rest of the report can pivot based on the following products:

- **Dynamics 365**: Dynamics 365 data
- **EMS**: Enterprise Management Services data
- **Microsoft 365**: Microsoft 365 data
- **Office 365**: Office 365 data

Planning ways to develop your Cloud Solution Provider (CSP) business includes understanding how your customers use their Microsoft products. You have several options for gathering data in Partner Center, and you can gather data on both your business and on whether and how your customers are using the licenses they've purchased.

If you are in the CSP direct model, you also have the opportunity to install and use the Partner Center Analytics app for Power BI to gather additional data.

## Access to the Subscription Analytics

Use the following steps to view subscription analytics.

1. Sign in to Partner Center and select **Insights**.
2. Select **Analyze**, and then select **Subscription analytics**.
3. The trailing twelve-month CSP revenue will be displayed at the top of the page.

## Trailing Twelve-Month (TTM) CSP Revenue

Trailing 12-month CSP revenue represents the trailing Cloud Solution Provider program revenue in USD at a Partner Global Account level. The data is refreshed on the eighth of every month, to display the trailing twelve-month revenue until the prior month. For example, on 9 September 2020, you should be able to see the TTM for the fixed period of September 2019 to August 2020. Software subscriptions are excluded. TTM Revenue will reflect only the eligible revenue for which the invoices have been paid already.

The revenue displayed on Partner Center is calculated for a fixed time interval of 12 months, and cannot be modified to a shorter time frame.

:::image type="content" source="media/insights/trailing-twelve-month.png" alt-text="Screenshot of TTM CSP revenue.":::

To see a breakdown of the revenue at your Partner Location Account level:

- Select the ‘Download Details' link and download a .tsv file that displays the TTM revenue across all your locations.

> [!NOTE]
> Summing up the individual TTM Revenue numbers across PartnerIDs in the .tsv file may appear to be greater than the overall TTM revenue you see displayed on Partner Center. This is because the revenue may be double counted for subscriptions with multiple partner attributions in the downloaded file.

## Types of subscription and license metrics you can view

We're tracking the following metrics, which are described in detail in the following sections.

- [Summary](#summary)
- [Product breakdown](#product-breakdown)
- [Subscription retention](#subscription-retention)
- [Subscription churn](#subscription-churn)
- [Suspended subscriptions](#suspended-subscriptions)
- [Active subscriptions](#active-subscriptions)
- [Trial subscription conversions](#trial-subscription-conversions)
- [Trial subscriptions ending in 30 days](#trial-subscriptions-ending-in-30-days)

### Summary

- **Subscriptions sold**: Number of subscriptions created during the specified time period

- **Licenses sold**: Number of licenses sold during the specified time period

- **Subscriptions renewing in 30 days**: Number of subscriptions for which the status is **Active** for the specified time period and for which **Autorenew** is true

- **Active subscriptions**: Subscriptions for which the status is **Active**

- **Suspended subscriptions**: Number of suspended subscriptions. There's no date filter.

### Product breakdown

- **Subscription count**: Top five products sorted by subscriptions sold

- **License count**: Top five products by sorted licenses sold

### Subscription retention

- **Renewed subscriptions**: Subscriptions that renewed in the last 30 days

### Subscription churn

- **New subscriptions**: Number of new subscriptions for the time period, excluding trial offers

- **Deprovisioned subscriptions**: Number of subscriptions deprovisioned or suspended by date

:::image type="content" source="media/insights/subscription-churn.png" alt-text="Screenshot of subscription churn.":::

### Suspended subscriptions

- List of all subscriptions with a status of **Suspended**, excluding trial offers

### Active subscriptions

- List of all active subscriptions

### Trial subscription conversions

- **Trial conversion**: Number of all **Active** subscriptions for which trial paid to conversion occurred during the specified time period

#### Trial subscriptions ending in 30 days

- List of trials that were started, for which the end date is within 30 days and there's no paid start date associated with the subscription

## Next steps

- [Analyze the performance of your indirect resellers](analyze-indirect-resellers.md)
