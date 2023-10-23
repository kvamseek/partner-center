---
title: Partner cohort analysis
ms.topic: article
ms.date: 09/20/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-insights
description: View how you're performing against other partners in your ML defined cohort and take corrective actions to improve your performance
author: JulCsc
ms.author: rohankaushik
---

# See how you're performing against other partners in your cohort

**Appropriate roles**: Referrals admin

> [!NOTE]
> Referral analytics can be accessed from both the Insights workspace and the Referral workspace.

The **Partner Cohort** page under the **Analyze** section in Referrals lets you see how you're performing against other partners in the cohort.

## Navigating the Partner cohort dashboard

Partner Cohort insights dashboard has many page level features for improved user experience and usability.

:::image type="content" source="media/referrals/cohort-analysis-page-features.png" alt-text="Screenshot showing the page level features." lightbox="media/referrals/cohort-analysis-page-features.png" :::

### Download

You have an option to download the page as PDF by clicking on Download option.

:::image type="content" source="media/referrals/cohort-analysis-download.png" alt-text="Screenshot showing the page level download option." lightbox="media/referrals/cohort-analysis-download.png" :::

### Share

You can share the link or screenshot to this page via Email or Teams.

:::image type="content" source="media/referrals/referral-insights-share.png" alt-text="Screenshot showing option to share the insight page with team members." lightbox="media/referrals/referral-insights-share.png" :::

### What's new

You can view all the updates related to the page in this section. You can also take a **Quick tour** and **Page guide tour** from this panel.

:::image type="content" source="media/referrals/referral-insights-whats-new.png" alt-text="Screenshot showing what's new panel." lightbox="media/referrals/referral-insights-whats-new.png" :::

### Data refresh details and feedback

You can view the data refresh details for all the widgets available in the page. You can also share your feedback at page level along with screenshot and other details.

:::image type="content" source="media/referrals/summary-data-refresh-know-more.png" alt-text="Screenshot showing the more options at page level." lightbox="media/referrals/summary-data-refresh-know-more.png" :::

:::image type="content" source="media/referrals/referral-insights-data-refresh-details.png" alt-text="Screenshot showing data refresh details panel." lightbox="media/referrals/referral-insights-data-refresh-details.png" :::

:::image type="content" source="media/referrals/referral-insights-page-feedback.png" alt-text="Screenshot showing the option to provide page level feedback." lightbox="media/referrals/referral-insights-page-feedback.png" :::

### Feedback button

Each widget in the page is incorporated with a feedback button to let you provide instant feedback with screenshots and more details.

## Partner cohort analysis

Partner Cohort page under the Analyze section in Referrals workspace lets you see how you're performing against the other partners in your cohort.
This page is divided into three sections:
- **Business Performance**: This section shows the comparative analysis on three business metrics
- **Well Performed Areas**: This section shows the metrics where you've performed better than median of cohort
- **Improvement Areas**: This section shows the metrics where you need to improve.

> [!NOTE]
> Blue color of the widget signifies you are performing better than the median of your cohort. Pink color of the widget signifies you are lagging behind the median and there is scope of improvement.

## Cohort definition

Our AI/ML model considers more than 100 parameters to analyze the partners and group the similar partners in cohorts. These cohorts are dynamic in nature as the count and characteristics of partners enrolled in Referral program change over time. This activity is performed monthly, and you may see the number of partners changing in your cohort.

### Benefits of dynamic cohorts

- Automatic Machine Learning (ML) model performing clustering
- Deep holistic analysis of partners by considering more than 100 parameters
- Identifying similarities across all partner types
- Generate insights by looking at data beyond the realm of leads and referrals

## Business performance

This section shows your comparative performance against your partner cohort for these metrics.

- **Won rate**: This widget shows your *average referrals won rate per month* in the trailing twelve months vs the median value in your cohort
- **Value won (USD)**: This widget shows your *average referral won value per month* vs the median value in your cohort
- **Lost rate**: This widget shows your *average referral lost rate per month* vs the median value in your cohort

:::image type="content" source="media/referrals/cohort-business-performance.png" alt-text="Screenshot showing the business performance section." lightbox="media/referrals/cohort-business-performance.png" :::

Widgets will be either Blue or Pink based on your performance against the median value.

## Well performed areas

This section shows the metrics where you've performed better than the median of cohort. All the widgets are Blue signifying that you're performing better than the median value of cohort.

:::image type="content" source="media/referrals/cohort-well-performed.png" alt-text="Screenshot showing the well performed areas section." lightbox="media/referrals/cohort-well-performed.png" :::

This section is dynamic and only shows well performed metrics.

## Improvement areas

This section shows the metrics where you're lagging the median of cohort and there's scope of improvement. You'll also see recommended value and immediate action you can take to improve the metric.

:::image type="content" source="media/referrals/cohort-improvement-areas.png" alt-text="Screenshot showing the Improvement areas section." lightbox="media/referrals/cohort-improvement-areas.png" :::

All the widgets are Pink signifying that there's scope of improvement. This section is dynamic and only shows the metrics where you're lagging.

## Metrics considered for Well performed and Improvement areas

|	Metric	|	Definition	|
| ---- |	----	|
|	Countries	|	This widget captures the number of countries/regions in which the partner is present against the median value of partners in their cohort	|
|	Solution Areas	|	This widget captures the number of solution areas against the median value of partners in their cohort	|
|	Solution Industries	|	This widget captures the number of solution industries against the median value of partners in their cohort	|
|	Solution Published	|	This widget captures the number of solutions published by a partner against the median value of partners in their cohort	|
|	Referrals Outbound	|	This widget captures the average outbound referrals per month against the median value of partners in their cohort	|
|	Acceptance Rate	|	This widget captures the average accepted referral rate of partner per month against the median value of partners in their cohort	|
|	Accept Time (in days)	|	This widget captures the average number of days to accept the referrals against the median value of partners in their cohort	|
|	Declined Rate	|	This widget captures the average declined referral rate of partner per month against the median value of partners in their cohort	|
|	Expired Rate	|	This widget captures the average expired referral rate of partner per month against the median value of partners in their cohort	|

## Frequently asked questions

### Why number of partners are changing in my cohort?

Our Machine Learning model considers more than 100 parameters to identify the similarity among the partners. Model is refreshed every month and considers the data for last 12 months. Based on the count of partners and their performance, there could be some change in number of partners in cohort.

### Why can't I see the partners in my cohort?

We're committed for keeping the partner data protected and available to the people with right authority. Data for all other partners in your cohort is aggregated. We aren't showing the other partner details in your cohort to ensure that you're seeing data for only your organization.

### Why do I see different metrics in Well performed and Improvement area section?

Our machine learning model compares your performance against the partners of your cohort. The model refreshed every month and considers the data for trailing twelve months thus identifying the areas where you are consistently performing better or worse than the median of your cohort.

## Next steps

- [Insights around your leads](referral-leads-insights.md)
- [Insights around your co-sell opportunities](referral-cosell-insights.md)