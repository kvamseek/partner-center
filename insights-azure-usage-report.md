---
title: Azure Usage report - Cloud product performance
ms.topic: article
ms.date: 8/11/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-insights
description: See what you're doing well and where you can improve your use of the Azure subscriptions you sell or manage for your customers.
author: kshitishsahoo
ms.author: ksahoo
---

# Azure Usage report - Cloud product performance

**Appropriate roles**: Global admin | Admin agent | Report viewer | Executive report viewer

The Azure Usage report presents metrics related to your customers' Azure subscriptions. This report includes Azure consumption revenue and usage by meter categories. You can view the following sections from the Azure Usage report.

- Summary
- Azure usage by geography
- Azure utilization
- Azure services with anomalies

 > [!NOTE]
 > This report is available from the Insights dashboard. To view this report, you must be assigned a specific role in Partner Center, such as Global Admin, Account Admin, Report Viewer or Executive Report Viewer. For more information, see your company's Global Admin. Specific types of data in this report may also be available only to users with Executive Report Viewer privileges.

## Summary

The summary section presents a snapshot view of the key performance indicators (KPIs) related to Azure subscriptions sold or managed by you for your customers.

- Azure Subscriptions:
Current count of Azure customer subscriptions sold or managed by you.
Percentage growth or decline of these Azure subscriptions during the selected date range.

The Micro chart presents a month-over-month trend of Azure subscriptions count for your selected date range.

- Active Azure Subscriptions:
Current count of Azure subscriptions sold or managed by you that had active usage over the last 30 days.
Percentage growth or decline of these subscriptions during the selected date range.

The Micro chart presents a month-over-month trend of the Azure active subscription count during your selected date range.

- Azure Consumed Revenue (ACR):
Total Azure Consumed Revenue (in USD) attributed to you over the selected date range.
Percentage growth or decline of attributed ACR US$ during the selected date range.

The Micro chart presents a monthly trend of ACR in USD attributed to you over the selected time period

> [!NOTE]
 > Azure Consumed Revenue (ACR) will only be visible to users who have been assigned the Executive Report Viewer Role.

:::image type="content" source="media/insights/azure-usage-summary.png" alt-text="Azure usage summary.":::

## Azure usage by geography

The table presents the Azure consumed revenue and Usage against the countries/regions where the usage events are generated.

:::image type="content" source="media/insights/azure-usage-by-geography.png" alt-text="Azure usage by geography.":::

## Azure utilization

This view shows the month-over-month Azure consumption revenue or usage hours trends by selected Azure service level/meter categories.

The bar chart presents the monthly revenue/usage hour trend. The line chart presents the growth trend compared to the previous month for the selected Azure service level/meter categories.

:::image type="content" source="media/insights/azure-usage-utilization.png" alt-text="Azure usage utilization.":::

## Azure services with anomalies

Users can now view the anomaly detection on the most valuable workloads usage data in Azure on the Azure usage page. The widget will display all customers and services impacted with anomalies in the last four weeks.

:::image type="content" source="media/insights/anomalies-widget.png" alt-text="Azure services with anomalies widget.":::

To interact with the widget, the user should:

1. Select the Customer from the list of Customers or Search for the Customer.
2. View the impacted services where anomalies are detected in last four weeks.
3. Select a service and the graph for the specific service will be displayed.
4. View the anomaly in the chart and can share feedback if the anomaly information was useful.
5. Download the underlying data for the chart to investigate further.

The Anomaly detection model considers the Azure usage data of workloads for last six months. The ML model learns the usage behavior and is able to detect if there's any spike or dip in the usage detected on any workload in the last four weeks.

## Azure subscriptions at risk of churn

Users can now view the subscriptions which are at the risk of churn and take corrective actions by discussing with the Customers. You can view the ACR trend and usage trend and view the break down by workloads.

:::image type="content" source="media/insights/azure-risk-of-churn.png" alt-text="Screenshot of Azure subscriptions at risk of churn.":::

> [!NOTE]
> You can download the raw data for this report from the [Download Reports section](insights-download-reports.md) in the Insights dashboard.

## Next steps

- For more reports, see [Partner Center Insights](partner-center-insights.md).
