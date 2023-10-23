---
title: Manage metered billing anomalies in Partner Center
description: Learn how automatic anomaly detection for metered billing helps ensure your customers are billed correctly for metered usage of your commercial marketplace offers.
ms.service: partner-dashboard 
ms.subservice: partnercenter-insights
ms.topic: conceptual
author: sayantanroy83
ms.author: sroy
ms.reviewer: janeguo-msft
ms.date: 05/08/2023
---

# Manage metered billing anomalies in Partner Center

The custom metered billing option is currently available to [Software as a service](./marketplace/plan-saas-offer.md) (SaaS) offers, [Azure Applications](./marketplace/plan-azure-application-offer.md#types-of-plans) with a Managed application plan and [Kubernetes app offers](./marketplace/marketplace-containers.md).

If you're using the metered billing option to create offers in the commercial marketplace program that lets you charge for usage based on nonstandard units, you need to know when your customer has used more of a service than expected.

## Use the Anomaly detection feature

Microsoft relies on you, the partner, to report your customers’ overage usage of their SaaS, Azure Managed application or Kubernetes app offers before Microsoft invoices the customer. If the wrong usage is reported, the customer could potentially receive an incorrect invoice, undermining both Microsoft’s and the partner’s credibility.

To help ensure that your customers are billed correctly, use the **Anomaly detection** feature for both SaaS Apps and Azure application managed application plans. This feature monitors usage against metered billing and predicts the expected value of usage within the expected range. If the usage is outside the expected range, it's treated as unexpected (an anomaly), and you'll receive an alert notification on your Offer Overview page in the commercial marketplace program of Partner Center. You can track your customers’ usage daily for every custom meter dimension that you’ve set.

## View and manage metered usage anomalies

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home).
1. On the Home page, select the **Insights** tile.

    :::image type="content" source="./media/workspaces/partner-center-insights-tile.png" alt-text="Illustrates the Insights tile on the Partner Center Home page." lightbox="./media/workspaces/partner-center-insights-tile.png":::

1. In the left menu, select **Usage**.
1. Select the **Metered usage anomalies** tab.

    :::image type="content" source="./media/anomaly-detection/metered-usage-anomalies-workspaces.png" alt-text="Illustrates the Metered usage anomalies tab on the Usage page." lightbox="./media/anomaly-detection/metered-usage-anomalies-workspaces.png":::<br>
    ***Figure 1: Metered usage anomalies tab***

1. For any usage anomalies detected against metered billing, as a publisher you'll be asked to investigate and confirm if the anomaly is true or not. Select **Mark as anomaly** to confirm the diagnosis.

     :::image type="content" source="./media/anomaly-detection/mark-as-anomaly-workspaces.png" alt-text="Illustrates the Mark as anomaly dialog box." lightbox="./media/anomaly-detection/mark-as-anomaly-workspaces.png":::<br>
    ***Figure 2: Mark as an anomaly dialog box***

1. If you believe that the overage usage anomaly we detected isn't genuine, you can provide that feedback by selecting **Not an anomaly** for the Partner Center flagged anomaly on the particular overage usage.

    :::image type="content" source="./media/anomaly-detection/why-is-it-not-an-anomaly-workspaces.png" alt-text="Illustrates the Why is it not an anomaly dialog box." lightbox="./media/anomaly-detection/why-is-it-not-an-anomaly-workspaces.png":::
    ***Figure 3: Why is it not an anomaly? dialog box***

1. You can scroll down the page to see an inventory list of unacknowledged anomalies. The list provides an inventory of anomalies that you have not acknowledged. You can choose to mark any of the Partner Center-flagged anomalies as genuine or false.

   :::image type="content" source="./media/anomaly-detection/unacknowledged-anomalies-workspaces.png" alt-text="Illustrates the Partner Center unacknowledged anomalies list on the Usage page." lightbox="./media/anomaly-detection/unacknowledged-anomalies-workspaces.png":::<br>
    ***Figure 4: Partner Center unacknowledged anomalies list***

    By default, flagged anomalies that have an estimated financial impact greater than 100 USD are shown in Partner Center. However, you can select **All** from the **Estimated financial impact of anomaly** list to see all flagged anomalies.

    :::image type="content" source="./media/anomaly-detection/all-anomalies.png" alt-text="Screenshot of all metered usage anomalies for the selected offer." lightbox="./media/anomaly-detection/all-anomalies.png":::

1. You would also see an anomaly action log that shows the actions you took on the overage usages. In the action log, you'll be able to see which overage usage events were marked as genuine or false.

   :::image type="content" source="./media/anomaly-detection/anomaly-action-log-workspaces.png" alt-text="Illustrates the Anomaly action log on the Usage page." lightbox="./media/anomaly-detection/anomaly-action-log-workspaces.png":::<br>
   ***Figure 5: Anomaly action log***

1. Partner Center analytics won't support restatement of overage usage events in the export reports. Partner Center lets you enter the corrected overage usage for an anomaly and the details are passed on to the correct Microsoft team for investigation. Based on the investigation, Microsoft will issue credit refunds to the overcharged customer, as appropriate. When you select any of the flagged anomalies, you can select **Mark as anomaly** to mark the usage overage anomaly as genuine.

   :::image type="content" source="./media/anomaly-detection/mark-as-anomaly-workspaces.png" alt-text="Illustrates the Mark as an anomaly dialog box." lightbox="./media/anomaly-detection/mark-as-anomaly-workspaces.png":::<br>
   ***Figure: 6: Mark as anomaly dialog box***

The first time an overage usage is flagged as irregular in Partner Center, you'll get a window of 30 days from that instance to mark the anomaly as genuine or false. After the 30-day period, as the publisher you wouldn't be able to act on the anomalies.

> [!IMPORTANT]
> Under-reported overage usage units are not eligible for restatement and financial adjustment.

You can see all the anomalies (acknowledged or otherwise) for the selected computation period. The various computation periods are the last 30 days, last 60 days, and last 90 days.

> [!IMPORTANT]
> You're requested to act on the flagged anomalies within 30 days of the time from when the anomalies are first reported in Partner Center.

The filter modal in the widget lets you select individual offers and individual custom meters.

After you mark an overage usage as an anomaly or acknowledge a model that flagged an anomaly as genuine, you can’t change the selection to “Not an Anomaly”.

> [!IMPORTANT]
> You can resubmit overage usages in the event of overcharge situations.

## Next steps

- [Metered billing for SaaS using the commercial marketplace metering service](./marketplace/partner-center-portal/saas-metered-billing.md)
- [Metered billing for Azure Containers using the commercial marketplace metering service](./marketplace/azure-container-metered-billing.md)
- [Managed application metered billing](./marketplace/marketplace-metering-service-apis.md)
- [Anomaly detection service for metered billing](./marketplace/partner-center-portal/anomaly-detection-service-for-metered-billing.md)
