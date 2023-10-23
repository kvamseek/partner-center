---
title: Resellers performance dashboard (tenant) – Cloud product performance
description: Use analytics to learn how your indirect resellers are doing, both their successes and areas that may need more attention.
ms.service: partner-dashboard
ms.subservice: partnercenter-insights
author: kshitishsahoo
ms.author: ksahoo
ms.topic: article
ms.date: 11/09/2022
---

# Resellers performance dashboard (tenant) – Cloud product performance

**Appropriate roles**: Global admin | User management admin

Data drives business decisions. Use the metrics in the **Reseller analytics** page to identify your successes, your indirect resellers' successes, and areas that need more attention. Use this information as you plan new business goals.

> [!NOTE]
> Indirect reseller analytics is available only for indirect providers in the Cloud Solution Provider program.

## Types of reseller analytics metrics you can view

We're tracking the following metrics, which are described in detail in the following sections.

- [Summary](#summary)
- [Resellers by market](#resellers-by-market)
- [Top resellers by subscriptions sold](#top-resellers-by-subscriptions-sold)
- [Top products by subscription count](#top-products-by-subscription-count)
- [New subscriptions](#new-subscriptions)
- [Subscription churn](#subscription-churn)
- [New reseller details](#new-reseller-details)
- [MPA signed status](#mpa-signed-status)

### Summary

- **Total resellers**: Number of active resellers on the last day of the subscription
- **New resellers**: Number of new indirect resellers for the specified time period
- **Active resellers**: Number of indirect resellers for which the PartnerID is at least one subscription, and for which the subscription status isn't "deprovisioned"
- **Transacting resellers**: Number of indirect resellers with a subscription sold in the specified time period

  :::image type="content" source="media/insights/resellers-transacting.png" alt-text="Screenshot of transacting resellers.":::

### Resellers by market

- Total resellers by geographic location

  :::image type="content" source="media/insights/resellers-by-geo-location.png" lightbox="media/insights/resellers-by-geo-location.png" alt-text="Screenshot of total resellers by geographic location.":::

### Top resellers by subscriptions sold

- A list of resellers, sorted by the number of subscriptions they've sold

  :::image type="content" source="media/insights/resellers-by-sub-sold.png" alt-text="Screenshot of total resellers by subscriptions sold.":::


### Top products by subscription count

- **Dynamics 365**: Dynamics 365 products sorted by subscriptions sold
- **EMS**: Number of Enterprise Management Services subscriptions sold
- **Microsoft 365**: Number of Microsoft 365 subscriptions sold
- **Office 365**: Office 365 products sorted by subscriptions sold

  :::image type="content" source="media/insights/reseller-top-products.png" alt-text="Screenshot of total resellers by top products sold.":::

### New subscriptions

- The number of new subscriptions added by date

### Subscription churn

- **New subscriptions**: Number of new subscriptions added by date
- **Deprovisioned subscriptions**: Number of subscriptions deprovisioned or suspended by date

  :::image type="content" source="media/insights/resellers-breakup-by-status.png" alt-text="Screenshot of total resellers breakup by status.":::

### New reseller details

- **Reseller name**: Names of indirect resellers
- **Location**: Markets where the indirect resellers operate
- **Subscriptions**: Number of subscriptions the reseller has sold
- **Licenses**: Total number of licenses the reseller has sold across all subscriptions

### MPA signed status

This section provides the status of MPA signed status of the CSP indirect resellers.

- **Reseller name**: Name of the CSP indirect reseller
- **PartnerID**: PartnerID of the indirect reseller
- **Region**: Region where the indirect reseller operates
- **Vetting status**: Vetting status of the indirect reseller
- **MPA signed status**: MPA signing status for the indirect reseller

  :::image type="content" source="media/insights/resellers-mpa-status.png" lightbox="media/insights/resellers-mpa-status.png" alt-text="Screenshot of resellers by MPA status.":::

Select the download icon in the chart to download MPA signed status data with additional dimensions

## Next steps

- [Analyze subscriptions and licenses to help drive business decisions](analyze-subscriptions-licenses.md)
