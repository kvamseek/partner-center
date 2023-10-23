---
title: Get co-sell insights
ms.topic: article
ms.date: 08/28/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-insights
description: Review your co-sell insights regularly in Partner Center to see trends to address or improvement areas to help you reach your business goals.
author: JulCsc
ms.author: rohankaushik
---

# Get co-sell opportunities related insights in Partner Center

**Appropriate roles**: Referrals admin

> [!NOTE]
> Referral analytics can be accessed from both the Insights workspace and the Referral workspace.

The **Co-sell opportunities** page under the **Analyze** section in Referrals lets you see how your referrals are doing. These referrals include both IP co-sell and services co-sell referrals. Review these metrics regularly to identify trends or areas that need attention, and start driving towards your business goals.

The dashboard displays metrics for IP co-sell and Services co-sell referrals in different tabs, and an **All** tab displaying both types of referrals together.

> [!IMPORTANT]
> The deal type filter is preapplied with the **Co-sell** and **Partner-led** type selected for all the data. Remove the filter, if you want to analyze the data for all or specific type of deals.

## Navigating the co-sell opportunities insights dashboard

Co-sell opportunities insights dashboard has many page level features for improved user experience and usability.

:::image type="content" source="media/referrals/cosell-insights-page-features.png" alt-text="Image showing the page level features." lightbox="media/referrals/cosell-insights-page-features.png" :::

### Download

You can download the raw data and download as PDF.

:::image type="content" source="media/referrals/cosell-insights-download.png" alt-text="Image showing the page level download option." lightbox="media/referrals/cosell-insights-download.png" :::

### Share

You can share the link or screenshot to this page via Email or Teams.

:::image type="content" source="media/referrals/share-referral-insights.png" alt-text="Image showing option to share the insight page with team members." lightbox="media/referrals/share-referral-insights.png" :::


### What's new

You can view all the updates related to the page in this section. You can also take a **Quick tour** and **Page guide tour** from this panel.

:::image type="content" source="media/referrals/referral-insights-whats-new.png" alt-text="Screenshot showing the What's new panel." lightbox="media/referrals/referral-insights-whats-new.png" :::

### Data refresh details and Feedback

You can view the data refresh details for all the widgets available in the page. You can also share your feedback at page level along with screenshot and other details.

:::image type="content" source="media/referrals/summary-data-refresh-know-more.png" alt-text="Image showing the more options at page level." lightbox="media/referrals/summary-data-refresh-know-more.png" :::

:::image type="content" source="media/referrals/referral-insights-data-refresh-details.png" alt-text="Image showing data refresh details panel." lightbox="media/referrals/referral-insights-data-refresh-details.png" :::

:::image type="content" source="media/referrals/referral-insights-page-feedback.png" alt-text="Image showing the option to provide page level feedback." lightbox="media/referrals/referral-insights-page-feedback.png" :::

### Time range filters

You can find a time range selection at the top-right corner of each page. You can customize the output of the **Overview** page graphs by selecting a time range based on the past 1, 3, 6, or 12 months, or by selecting a custom time range. The default time range selection is three months.

:::image type="content" source="media/referrals/referral-insights-time-range.png" alt-text="Image showing the option to select time range." lightbox="media/referrals/referral-insights-time-range.png" :::

### Feedback button

Each widget in the page is incorporated with a feedback button to let you provide instant feedback with screenshots and details.

### Apply filters

You can select the **Filters** button to open the panel that lets you filter this data in different ways:

- **Customer name**: The default is **All**, but you can limit the data to one or more customers that you select.
- **Country**: The default is **All**, but you can limit the data to one or more countries of the customer that you select.
- **Deal type**: The default includes both **Co-sell** and **Partner-led** deals. Other options include **Private** deals, and **All** (by selecting all deal types).
- **Deal direction** The default is **All**, but you can limit the data to either **Incoming** referrals (ones that you received) or **Outgoing** referrals (ones that you sent).
- **Solution name**: The default is **All**, but you can limit the data to referrals that contains one or more solutions that you select.
- **Marketplace purchase intent**: The default is **All**, but you can limit the data to referrals where customer intended to transact in the marketplace. Use **Not Applicable** to include referrals that were created before this information was captured (June 1, 2023).
- **Customer MACC eligibility**: The default is **All**, but you can limit the data to referrals for customers that are Microsoft Azure Consumption Commitment (MACC) eligible at the time of referral creation. Select **Not Applicable** to include historic referrals. To learn more, see [Azure Consumption Commitment enrollment](./marketplace/azure-consumption-commitment-enrollment.md).
- **Partner Program**: The default is All, but you can limit the data to referrals in a specific GTM program. This is applicable only for Services co-sell deals and is available in All and Services co-sell tabs only.
- **Partner Role**: The default is **All**, but you can limit the data to referrals role that a services partner can play in the opportunity based on their endorsements. This is applicable only for Services co-sell deals and is available in All and Services co-sell tabs only.

The info in all of the following charts reflect the date range and any filters you've selected, except as noted below. Some sections also allow you to apply extra filters, such as filtering to a specific solution.

## Summary

This card shows an overview of how your Co-sell opportunities are performing for IP co-sell and Services co-sell deals.

The chart shows the total deals, count of deals accepted, marked as won and lost, and the total deal value won (in USD) for the selected time period.

This chart also shows the count of deals registered, deals approved, deals rejected, total deal approved value (in USD), and the annual contract value (in USD) for the selected time period. This is only available for IP co-sell types of deals.

The percentage change metrics (shown in red or green, with an arrow indicator) indicate the difference between the **last full month in the selected date range** and the **first full month in that range**. For example, say the current date is June 15, and you've selected the **3M** filter to show data for the last three months. In this case, these metrics would show the difference between May (the last full month in the selected time period) and March (the first full month in the selected time period) the date range selected is last **3M**, the comparison would be between the data for May and the data for March.

> [!NOTE]
> Deal registration related widgets will only be shown when partners have Azure IP co-sell eligible solutions and corresponding registered deals.

:::image type="content" source="media/referrals/cosell-analytics-summary.png" alt-text="Image showing the summary card of Co-sell opportunities analytics." lightbox="media/referrals/cosell-analytics-summary.png" :::

## Conversion funnel

This section shows a visual indicator of how your deals are moving from one state to another through their life cycle. You can view the entire life cycle based on the deal volume. You can also view the deal value in USD based on the main pivot for this section. The first section is labeled both with the state and the type of the deal to give you a visual indicator of the volume or value by type. There's also a section, **Referrals from the past**, which is used to indicate the deals for which you have taken action of either accepting/declining them or marking them as won/lost in the time period that has been selected for the report. You can apply filters to view the progress of the deals across various stages in their life cycle.

You can also view the average acceptance time and average time taken from opportunity created/received to win in this widget.

Co-sell inbound deals can merge into accepted, declined, or expired because partners must accept or decline inbound co-sell deals.

:::image type="content" source="media/referrals/inbound.png" alt-text="Image showing the states for inbound referrals." lightbox="media/referrals/inbound.png" :::

Partner-led, Private, and Co-sell outbound deals will merge into Created as Partners create these types of deals.

:::image type="content" source="media/referrals/outbound.png" alt-text="Image showing the states for outbound referrals." lightbox="media/referrals/outbound.png" :::

:::image type="content" source="media/referrals/cosell-analytics-funnel.png" alt-text="Image showing the conversion funnel for referrals." lightbox="media/referrals/cosell-analytics-funnel.png" :::

## Deal registration

This section shows a visual indicator of how your registered deals are moving from one state to another through their life cycle. You can view the entire life cycle based on the deal volume and the deal value in USD based on the main pivot for this section.
This section is shown only to the partners who have Azure IP co-sell eligible solutions and have registered deals.
You can apply filters to view the progress of the deals across various stages in their lifecycle.

:::image type="content" source="media/referrals/deal-registration-funnel.png" alt-text="Image showing the conversion funnel for deal registration." lightbox="media/referrals/deal-registration-funnel.png" :::

This widget isn't applicable for Services co-sell types of referrals and isn't visible in Services co-sell tab.

## Geographical spread

This section shows the countries/regions where deals came from, along with details for each country/region. There's a table view of the deal details for each country.

:::image type="content" source="media/referrals/cosell-analytics-geo-distribution.png" alt-text="Image showing the geo distribution of referrals." lightbox="media/referrals/cosell-analytics-geo-distribution.png" :::

## Solutions

This chart lets you see which of your solutions are driving the most referrals and the highest deal value. The table has pivots - All, Co-sell, Partner-led, and Private.
Based on your pivot selection, you can see the performance of the deals aggregated by solution.

> [!NOTE]
> If multiple solutions are included in a deal, the table will show the same deal counted against all those solutions. You should not add up the values related to solutions and compare it with other referral volume metrics. This view is meant to help you understand the deal performance with solution pivot.

The table has total deals that have the solution included in them and the corresponding states like deals won, deals lost, deals expired. It also shows the total deals value won and lost in USD currency.

:::image type="content" source="media/referrals/cosell-analytics-solutions.png" alt-text="Image showing the solutions performance." lightbox="media/referrals/cosell-analytics-solutions.png" :::

## Capabilities

This chart lets you see which of your capabilities are driving the most referrals and the highest deal value. The table has pivots – Partner Program, and Partner Role. Based on your pivot selection, you can see the performance of the deals aggregated by the pivot.

> [!NOTE]
> If multiple Partner programs are included in a deal, the table will show the same deal counted against all those programs. You shouldn't add up the values related to programs and compare it with other referral volume metrics. This view is meant to help you understand the deal performance with Partner Program pivot.

The table has total deals that have the role/program included in them and the corresponding states like deals won, deals lost, deals expired. It also shows the total deals value won and lost in USD currency.

:::image type="content" source="media/referrals/capabilities-partner-role.png" alt-text="Screenshot of the Capabilities: Partner role section, with deals won, lost, expired, won value, and lost value." lightbox="media/referrals/capabilities-partner-role.png" :::

## *Declined* and *Lost* reasons

This section helps you analyze the reasons why the deals are getting marked as **Declined** or **Lost** by your company. The options in these representations are the same reasons that your sellers have chosen while closing the deal as declined or lost.

:::image type="content" source="media/referrals/cosell-analytics-reasons.png" alt-text="Screenshot of the Declined/Lost tab: Lost, showing the reasons selected by partner when declining or making a deal as lost." lightbox="media/referrals/cosell-analytics-reasons.png" :::

## Comparison charts

The comparison section helps you to compare the data related to referrals based on multiple dimensions on the volume, deals value won (in USD), and deals approved value (in USD) pivot. The four dimensions that you can choose to compare data are:

- Deal type
- Markets
- Solutions
- Co-sell type (only available in **All** tab)

When deal type is selected, you can compare the referrals performance with respect to Co-sell opportunities, Partner-led, and Private deals. For both markets and solutions, you can pick up to three different options to compare their performance. The first graph, which is a bar chart, has data presented with a month-on-month trend based on the main pivot, which is volume or the deals value won or the deals approved value. There's also a pie chart to the right of the bar chart, which shows the distribution by percentage for the same data. With Co-sell type, you can compare the distribution of IP co-sell and Services co-sell referrals.

:::image type="content" source="media/referrals/cosell-analytics-compare.png" alt-text="Image showing the comparison section." lightbox="media/referrals/cosell-analytics-compare.png" :::

> [!NOTE]
> Referrals that are closed as error, won't be considered in the insights widgets and data download.

## Download the analytics

You can download the analytics for co-sell opportunities and deal registration. The following information describes the download functionality.

- You can download a **maximum of 5000 records** by selecting the **Download data** button. Records are sorted in descending order based on referral creation date.
- The download function considers the timeline and the filters that have been applied.
- Partner can choose to download the report in either CSV (Comma-separated value) or TSV (Tab-separated value) format.
- It can take few minutes to download the records.
- You have to wait for the download to complete. Navigating away cancels the download.

> [!NOTE]
> This will download analytics data for the selected period. Go to **co-sell opportunities** page in **Referral** workspace for exporting transactional data.

## No data

There can be multiple reasons why you're getting a blank chart like the following one when accessing the Co-sell analytics as described in the following section.

- There's no data for this account. Try creating deals to get this report populated.
- There's a network connectivity issue. Check your internet connection and try again.
- The page loads with the default filter for Co-sell deals. If you only have Private deals, reset the deal type filter.
- There are no records matching the filters that you applied. Try resetting the filters.
- There's a delay between the opportunity state change and for the same to be updated in the analytics report. Check the report after 24 hours.

:::image type="content" source="media/referrals/nodata.png" alt-text="Image showing no data visualization for referrals.":::

> [!TIP]
> To see how your business profile is performing in the [Microsoft Appsource](https://appsource.microsoft.com/marketplace/partner-dir) experience, review the [Leads insights page](referral-leads-insights.md).

## Next steps

- [Grow your business with Microsoft referrals](referrals.md)
- [Insights around your leads](referral-leads-insights.md)
- [Data definition for referrals](referral-analytics-data-definition.md)
