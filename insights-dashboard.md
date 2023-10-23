---
title: Marketplace Insights dashboard in commercial marketplace analytics
description: Access a summary of marketplace web analytics in Partner Center, which enables you to measure customer engagement in Microsoft AppSource and Azure Marketplace.
ms.service: partner-dashboard 
ms.subservice: partnercenter-insights
ms.topic: article
author: saurabhsharmaa
ms.author: saurasharma
ms.reviewer: sroy
ms.date: 03/08/2023
---

# Marketplace Insights dashboard in commercial marketplace analytics

This article provides information on the Marketplace Insights dashboard in Partner Center. This dashboard displays a summary of commercial marketplace web analytics that enables publishers to measure customer engagement for their respective product detail pages listed in the commercial marketplace online stores: Microsoft AppSource and Azure Marketplace.

For detailed definitions of analytics terminology, see [Commercial marketplace analytics terminology and common questions](./analytics-faq.yml).

## Marketplace Insights dashboard

The [Marketplace Insights dashboard](https://partner.microsoft.com/dashboard/insights/commercial-marketplace/analytics/marketplaceinsights) presents an overview of Azure Marketplace and AppSource offers’ business performance. This dashboard provides a broad overview of the following:

- Page visits trend
- Call to actions trend
- Page visits and Call to actions against offers, referral domains, and campaign IDs
- Marketplace Insights by geography
- Marketplace Insights details table

The Marketplace Insights dashboard provides click stream data, which shouldn't be correlated with leads generated in the lead destination endpoint.

> [!NOTE]
> The maximum latency between users visiting offers on Azure Marketplace or AppSource and reporting in Partner Center is 48 hours.

### Marketplace Insights dashboard filters

Filter the data by offer names. Filter options are dynamic and based on the selected date range.

To select the filters, in the top-right of the page, select **Filters**.

:::image type="content" source="./media/insights-dashboard/dashboard-filters.png" alt-text="Screenshot of the Filters button in the top menu." lightbox="./media/insights-dashboard/dashboard-filters.png" :::

In the panel that appears on the right, select the offer names you want, and then select **Apply**.

:::image type="content" source="./media/insights-dashboard/dashboard-filters-panel.png" alt-text="Screenshot of the dashboard filters panel." lightbox="./media/insights-dashboard/dashboard-filters-panel.png" :::

### Page visits trends

The Marketplace Insights **Visitors** chart displays a count of _Page visits_ and _Unique visitors_ for the selected computation period.

**Page visits**: This number represents the count of distinct user sessions on the offer listing page (product detail page) for a selected computation period. The red and green percentage indicators represent the growth percentage of page visits. The trend chart represents the month-to-month count of page visits.

**Unique visitors**: This number represents the distinct visitor count during the selected computation period for the offer(s) in Azure Marketplace and AppSource. A visitor who has visited one or more product detail pages will be counted as one unique visitor.

:::image type="content" source="./media/insights-dashboard/visitors.png" alt-text="Screenshot of the Visitors chart on the Marketplace Insights dashboard." lightbox="./media/insights-dashboard/visitors.png":::

Select the ellipsis (three dots) to copy the widget image, download aggregated widget data as .CSV file, and download the image as a PDF for sharing purposes.

:::image type="content" source="./media/insights-dashboard/visitors-ellipsis.png" alt-text="Screenshot of the ellipsis menu on the Page visit count widget." lightbox="./media/insights-dashboard/visitors-ellipsis.png":::

### Call to actions trend

This number represents the count of **Call to Action** button clicks completed on the offer listing page (product detail page). _Calls to action_ are counted when users select the **Get It Now**, **Free Trial**, **Contact Me**, or **Test Drive** buttons. *Consent given* represents the total count of clicks for customer-provided consent to Microsoft or the partner. 

> [!NOTE]
> Consent given is not equivalent to leads. For more information about leads from marketplace, see [Get leads insights](referral-leads-insights.md).

The following screenshot shows two places where *Consent given* clicks appear.

:::image type="content" source="./media/insights-dashboard/consent-given.png" alt-text="Screenshot of location where a consent button is selected." lightbox="./media/insights-dashboard/consent-given.png" :::

The following graph shows the *CTA* vs. *Consent given* metric.

:::image type="content" source="./media/insights-dashboard/call-to-action.png" alt-text="Screenshot of sample graph of Calls to Action vs. Consent Given." lightbox="./media/insights-dashboard/call-to-action.png" :::

Select the ellipsis (three dots) to copy the widget image, download aggregated widget data as a .CSV file, and download the image as a .PDF.

:::image type="content" source="./media/insights-dashboard/call-to-action-ellipsis.png" alt-text="Screenshot of the ellipsis menu on the Calls to action widget." lightbox="./media/insights-dashboard/call-to-action-ellipsis.png":::

### Page visits and Call to action

This widget provides page visits and calls to action against offers, referral domains, and campaign IDs.

#### Offers

Select the **Offer alias** tab to select a specific offer to see the monthly trend of page visits, calls to action, and consent-given clicks on the chart.

Select the ellipsis (three dots) to copy the widget image, download aggregated widget data as .CSV file, and download the image as a .PDF.

:::image type="content" source="./media/insights-dashboard/offer-alias-tab-ellipsis.png" alt-text="Screenshot of the ellipsis menu on the Page visits and Calls to action widget." lightbox="./media/insights-dashboard/offer-alias-tab-ellipsis.png":::

#### Referral domains

Selecting a specific referral domain on the **Referral domain** tab shows the monthly trend of page visits, calls to action, and consent clicks on the chart to the right. Additionally, there is a column for Platform – website and client, displays for AppSource offers only. The funnel view depicts the conversion rates among page views, calls to action, and consent-given clicks on the chart.

:::image type="content" source="./media/insights-dashboard/referral-domains-funnel-graph.png" alt-text="Screenshot of a sample funnel graph of referral domains." lightbox="./media/insights-dashboard/referral-domains-funnel-graph.png" :::

#### Campaign IDs

By selecting a specific campaign ID on the **Campaign** tab, you should be able to understand the success of the campaign. For each campaign, you should be able to see the monthly trend of page visits, calls to action, and consent-given clicks on the chart.

:::image type="content" source="./media/insights-dashboard/campaign-id-funnel-graph.png" alt-text="Screenshot of the campaign chart on the Marketplace Insights dashboard." lightbox="./media/insights-dashboard/campaign-id-funnel-graph.png" :::

### Marketplace Insights by geography

For the selected computation period, the geographical spread widget displays the count of page visits, unique visitors, and calls to action (CTA).

Select the ellipsis (three dots) to copy the widget image, download aggregated widget data as a .CSV file, and download the image as a .PDF.

:::image type="content" source="./media/insights-dashboard/geographical-spread-ellipsis.png" alt-text="Screenshot of the geographical spread chart on the Marketplace Insights dashboard." lightbox="./media/insights-dashboard/geographical-spread-ellipsis.png":::

### Marketplace Insights details table

> [!IMPORTANT]
> To download the data in CSV, please use the Download data option available on top of page.

This table provides a list view of the page visits and the calls to action of your selected offers' pages sorted by date.

- If the count of records is over 1,000, exported data will be asynchronously placed in a downloads page for the next 30 days.
- Filter data by Offer names and Campaign names to display the data you are interested in.

:::image type="content" source="./media/insights-dashboard/marketplace-insights-details.png" alt-text="Screenshot of the Marketplace insights details table." lightbox="./media/insights-dashboard/marketplace-insights-details.png":::

> [!TIP]
> You can provide feedback on each of the widgets by selecting the “thumbs up” or “thumbs down” icon.

| Column name in<br>user interface | Attribute name | Definition | Column name in programmatic<br>access reports |
| ------------ | ------------- | ------------- | ------------- |
| Date | Date of Visit | The date of page visit and/or CTA click event generation on the offer’s page in Azure Marketplace and/or AppSource. | Date |
| Offer Name | Offer Name | The name of the commercial marketplace offering. | OfferName |
| Referral Domain | Referral Domain | The name of the referral domain from where the page visit happened. If there are no referral domains captured for the page visit, then the corresponding entry is “Referral domain not present”. |  ReferralDomain |
| Country Name | Country Name | The name of the country from where the page visit has happened. | CountryName |
| Page Visits | Page Visits | The number of page visits associated with the Offer Name for a particular date. | PageVisits |
| Get It Now | Get It Now | The number of clicks to the “Get It Now” CTA on the offer’s page for a particular date. | GetItNow |
| Contact Me | Contact Me | The number of clicks to the “Contact Me” CTA on the offer’s page for a particular date. | ContactMe |
| Test Drive | Test Drive | The number of clicks to the “Test Drive” CTA on the offer’s page for a particular date. | TestDrive |
| Free Trial | Free Trial | The number of clicks to the “Free Trial” CTA on the offer’s page for a particular date. | FreeTrial |
| Campaign | Name of the Campaign | Ability to understand web telemetry (page visit and CTA clicks) against the campaign name. | Campaign |
| Consent given | Consent given | Total count of clicks for customer-provided consent to Microsoft or the partner | consentGivenCount |
| Platform | Platform | Indicates website or client (in-product store) as the source for page view, CTA, or consent clicks | platforms |
| n/a | Site | The name of the storefront from which the page visit or CTA click occurred. The possible values are:<br>- AZUREMARKETPLACE<br>- APPSOURCE | Site |

## Next steps

- For an overview of analytics reports available in the commercial marketplace, see [Access analytic reports for the commercial marketplace in Partner Center](analytics.md).
- For information about your orders in a graphical and downloadable format, see [Orders dashboard in commercial marketplace analytics](orders-dashboard.md).
- For virtual machine (VM) offers usage and metered billing metrics, see [Usage dashboard in commercial marketplace analytics](usage-dashboard.md).
- For detailed information about your customers, including growth trends, see [Customer dashboard in commercial marketplace analytics](customer-dashboard.md).
- For a list of your download requests over the last 30 days, see [Downloads dashboard in commercial marketplace analytics](downloads-dashboard.md).
- To see a consolidated view of customer feedback for offers on Azure Marketplace and AppSource, see [Ratings & Reviews analytics dashboard in Partner Center](ratings-reviews.md).
- For frequently asked questions about commercial marketplace analytics and for a comprehensive dictionary of data terms, see [Commercial marketplace analytics terminology and common questions](analytics-faq.yml).