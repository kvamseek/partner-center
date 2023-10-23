---
title: Usage dashboard for VM offers in commercial marketplace analytics | Azure Marketplace
description: Learn how to access all usage metrics for VM offers published to Azure Marketplace.
ms.service: partner-dashboard 
ms.subservice: partnercenter-insights
ms.topic: article
author: saurabhsharmaa
ms.author: saurasharma
ms.date: 06/14/2023
---

# Usage dashboard for Virtual Machine (VM) offers in commercial marketplace analytics

This article provides information on the **VM Normalized usage** and **VM Raw usage** pages under Usage dashboard. These pages contain following widgets showing insights:

- Usage trend
- Image versions
- Normalized usage by offers
- Normalized usage by other dimensions: VM Size, Sales Channels, and Offer Types
- Geographical spread
- Usage details

> [!NOTE]
> These widgets are available in both **VM Normalized Usage** and **VM Raw Usage** pages. It will show normalized usage and raw usage in respective pages.

> [!IMPORTANT]
> The maximum latency between usage event generation and reporting in Partner Center is 48 hours.

## Page level filters

You can apply the following filters on usage page for further analysis. Each filter is expandable with multi select values. Filter options are dynamic and based on the selected range.

- Sales Channel
- Is Free Trial
- Marketplace License Type
- Marketplace Subscription ID
- Customer ID
- Customer Company Name
- Country
- Offer Name
- VM subscription

:::image type="content" source="./media/usage-dashboard/usage-filters.png" alt-text="Screenshot of the filters on the Usage dashboard." lightbox="./media/usage-dashboard/usage-filters.png":::

## Usage trend

In this widget, you find total usage hours and trend for your VM offers that are consumed by your customers during the selected computation period. Metrics and growth trends are represented by a line chart. Show the value for each month by hovering over the line on the chart. The percentage value below the usage metrics in the widget represents the amount of growth or decline during the selected computation period.

There are two representations of usage hours: VM normalized usage and VM raw usage.

- Normalized usage hours are defined as the usage hours normalized to account for the number of VM vCPU ([number of VM vCPU] x [hours of raw usage]). VMs designated as "SHAREDCORE" use 1/6 (or 0.1666) as the [number of VM vCPU] multiplier.
- Raw usage hours are defined as the number of time VMs have been running in terms of hours.

:::image type="content" source="./media/usage-dashboard/normalized-usage.png" alt-text="Screenshot of the normalized usage and raw usage data on the Usage dashboard." lightbox="./media/usage-dashboard/normalized-usage.png":::

## VM Image Version

This widget shows the count of active instances and trend for selected VM image version. This helps you to track the usage of different image versions and help you in making decision about deprecation

> [!NOTE]
> You can track insights of image versions for both **Azure VM** and **Core VM** offers.

:::image type="content" source="./media/usage-dashboard/vm-image-version.png" alt-text="Screenshot of the VM image version data on the Usage dashboard." lightbox="./media/usage-dashboard/vm-image-version.png":::

You can download the data for this widget by navigating to **Downloads** page and selecting **VM Image Version Detail** from Report type drop-down.

## Offers

This widget provides the total usage hours and trend for your usage-based offers in commercial Marketplace.

- The **Offers** stacked column chart displays a breakdown of usage hours for the top five offers according to the selected computation period. The top five offers are displayed in a graph, while the rest are grouped in the **Rest All** category.
- The stacked column chart depicts a month-by-month growth trend for the selected date range. The month columns represent usage hours from the offers with the highest usage hours for the respective month. The line chart depicts the growth percentage trend plotted on the secondary Y-axis.
- You can select specific offers in the legend to display only those offers in the graph.

:::image type="content" source="./media/usage-dashboard/normalized-usage-offers.png" alt-text="Screenshot of the normalized usage offers data on the Usage dashboard." lightbox="./media/usage-dashboard/normalized-usage-offers.png" :::

You can select any offer and a maximum of three plans of that offer to view the month-over-month usage trend for the offer and the selected plans.

:::image type="content" source="./media/usage-dashboard/normalized-usage-offers-sku.png" alt-text="Screenshot of the normalized usage offers and plan data on the Usage dashboard." lightbox="./media/usage-dashboard/normalized-usage-offers-sku.png" :::

### Usage: Other dimensions

There are three tabs for the dimensions:

- VM size
- Sales channels
- Offer type

You can see the usage metrics and month-over-month trend against each of these dimensions.

:::image type="content" source="./media/usage-dashboard/normalized-usage-other-dimensions.png" alt-text="Screenshot of the Normalized usage by other dimensions chart on the Usage dashboard." lightbox="./media/usage-dashboard/normalized-usage-other-dimensions.png" :::

## Geographical spread

For the selected computation period, the table displays the total usage against geography dimension.

:::image type="content" source="./media/usage-dashboard/normalized-usage-geographical-spread.png" alt-text="Screenshot of the geographical spread on the Usage dashboard." lightbox="./media/usage-dashboard/normalized-usage-geographical-spread.png" :::

## Usage details table

> [!IMPORTANT]
> To download the data in CSV, please use the Download data option available on top of page.

The **usage details** table displays a numbered list of the top 500 usage records sorted by usage. Note the following:

- Data in this table is displayed based on the page you've selected
- Each column in the grid is sortable.

Click on the ellipsis (three dots '...') to copy the widget image, or download the image as a pdf for sharing purposes.

:::image type="content" source="./media/usage-dashboard/vm-usage-details.png" alt-text="Screenshot of the Usage details widget." lightbox="./media/usage-dashboard/vm-usage-details.png":::

For more information about fields, see [Data dictionary for usage](./usage-dashboard.md#data-dictionary)

## Next steps

- Learn about Usage dashboard, see [Usage Dashboard in commercial marketplace analytics](./usage-dashboard.md)
- View insights around usage for your Containers offers, see [Usage Dashboard for containers in commercial marketplace analytics](./usage-containers-dashboard.md)
- View insights around metered usage for your offers, see [ Metered Usage Dashboard in commercial marketplace analytics](usage-metered-dashboard.md)
- View insights around metered usage anomalies, see [ Metered Usage anomalies](anomaly-detection.md)
- For frequently asked questions about commercial marketplace analytics and for a comprehensive dictionary of data terms, see [Commercial marketplace analytics terminology and common questions](./analytics-faq.yml)