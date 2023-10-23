---
title: Metered Usage dashboard in commercial marketplace analytics | Azure Marketplace
description: Learn how to access insights around metered usage for offers published to Azure Marketplace.
ms.service: partner-dashboard 
ms.subservice: partnercenter-insights
ms.topic: article
author: saurabhsharmaa
ms.author: saurasharma
ms.date: 06/14/2023
---


# Metered Usage dashboard for offers in commercial marketplace analytics

This article provides information on the **Metered usage** page under Usage dashboard. You will find insights for metered usage of **Virtual Machine (VM), Containers and Azure applications** offers in this page.

This page contains following widgets showing insights:

- Metered Usage
- Metered usage by customers
- Usage details

> [!IMPORTANT]
> The maximum latency between usage event generation and reporting in Partner Center is 48 hours.

## Page level filters

Metered usage page shows insights for Containers, Software as a service (SaaS) and Azure applications offer types. You can view insights by selecting the offer and meter ID.

This page has following dropdown available for selection:

- **Offer type** - This dropdown shows available offer types and have values like Containers, SaaS, and Azure applications.
- **Offers** - This dropdown shows the list of offer names based on selected offer type.
- **Plan type** - This dropdown shows if the Azure app is Solution template or Managed application with Publisher and customer access. This is only applicable for Azure applications.
- **Meter Id** - This dropdown shows the list of meter ID based on selected offer.

:::image type="content" source="./media/usage-dashboard/metered-usage-filters.png" alt-text="Screenshot of the filters on the metered usage dashboard." lightbox="./media/usage-dashboard/metered-usage-filters.png":::

## Metered usage

This widget shows metered usage for the selected offer and meter ID.

:::image type="content" source="./media/usage-dashboard/metered-usage.png" alt-text="Screenshot of the Raw usage chart for containers on the Usage dashboard." lightbox="./media/usage-dashboard/metered-usage.png" :::

Chart provides month over month trend of usage for selected period.

## Customers

This widget shows the metered usage for customers based on selected offer and meter ID.

:::image type="content" source="./media/usage-dashboard/metered-usage-customers.png" alt-text="Screenshot of the usage against customer for containers in usage dashboard." lightbox="./media/usage-dashboard/metered-usage-customers.png" :::

## Usage details table

> [!IMPORTANT]
> To download the data in CSV, please use the Download data option available on top of page.

The **usage details** table displays a numbered list of the top 500 usage records sorted by usage. Note the following:

- Data in this table is displayed based on the page you've selected
- Each column in the grid is sortable.

Click on the ellipsis (three dots '...') to copy the widget image, or download the image as a pdf for sharing purposes.

:::image type="content" source="./media/usage-dashboard/metered-usage-details.png" alt-text="Screenshot of the Usage details widget." lightbox="./media/usage-dashboard/metered-usage-details.png":::

For more information about fields, see [Data dictionary for usage](./usage-dashboard.md#data-dictionary)

## Next steps

- Learn about Usage dashboard, see [Usage Dashboard in commercial marketplace analytics](./usage-dashboard.md)
- View insights around usage for your Virtual Machine (VM) offers, see [Usage Dashboard for VM in commercial marketplace analytics](./usage-vm-dashboard.md)
- View insights around metered usage for your offers, see [ Metered Usage Dashboard in commercial marketplace analytics](usage-metered-dashboard.md)
- View insights around metered usage anomalies, see [ Metered Usage anomalies](anomaly-detection.md)
- For frequently asked questions about commercial marketplace analytics and for a comprehensive dictionary of data terms, see [Commercial marketplace analytics terminology and common questions](./analytics-faq.yml)