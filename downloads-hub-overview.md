---
title: Downloads hub overview 
ms.topic: article
ms.date: 07/25/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-insights
description: Learn about the Downloads hub and how it enables and enhances reporting for all Insights programs.
author: JulCsC
ms.author: juliacawthra
ms.reviewer: deepganguly
---

# Downloads hub overview

**Appropriate roles**: Executive report viewer | Report viewer

This article explains how to access Downloads hub and create reports. Enhance report discovery and usability while efficiently interacting with data.

## Overview

Downloads hub is a unified report hub, which addresses your reporting needs for all supported programs in Insights. All reports are organized in one place for you to customize and download in order to help you to make data-driven decisions for your business.

Access [Downloads hub](https://partner.microsoft.com/dashboard/insights/analytics/downloadshub).

Now you can also **create templates**, **apply filters**, **schedule reports**, access **curated lists of areas** and **templates**, which would help you in report discovery and usability. As a Power user, you can select columns and filters for use by any analytical tool or use the data directly.

Currently, the download reports from cloud product performance, marketplace offers and apps and games are available in Downloads hub.

:::image type="content" source="media/downloads-hub/downloads-report.png" lightbox="media/downloads-hub/downloads-report.png" alt-text="Screenshot of the program selector screen.":::

## All reports

This section is for downloading reports. It's highly flexible in terms of how users interact with the data. The main functions of this section are:

- **Favorites**: All templates, which are added as Favorites, appear in this section.
- **Reports**: You can find all the reports available for download here, and the ones scheduled (coming soon) or running in the list. The reports table has the following details for each report.
  - **Report name**: Shows the user the defined name or the default name based on the report type for the unique identification of the report.
  - **Report type**: Shows the data source selected during the report creation.
  - **Status**/Actions: Shows the status of the download. These statuses can be running,  prepared for download, or it can be a download link when the report is ready for download.
  - **Columns included**: Shows the list of columns selected for download.
  - **Time range**: Shows the time range for which the report is generated. If you don't choose a predefined format, this field shows a custom format.
  - **Generation timestamp (UTC)**: Shows the exact time and date (in UTC) when the report was generated.

Reports generated during the previous 14 days are available for download.

> [!NOTE]
> You can download reports for two years at a time and the date selection can't be more than the previous three years.
>
> For example, if you want to download data from January 2020 to January 2023, you can’t download the three year report at once. You have to download two reports with different timelines and combine the data after. One report can be January 2020 to January 2021 and the second report can be January 2021 to January 2023 (a two year time range is the maximum).

### Open a report in Excel that includes non-English character sets

To open a report that includes non-English character sets, for example, Simplified Chinese, import the report into Excel using either the generic Unicode UTF-8 code identifer, **65001**, or use a specific [Unicode code page identifier](/windows/win32/intl/code-page-identifiers) for your language. Don't convert the .csv file to the Excel file format (.xlsx), because the conversion can cause data loss or garbled output. Sample instructions for the Excel for Microsoft 365:

1. Save the exported file as a .csv file.
1. Open Excel.
1. On the **Data** tab, select **Get Data** > **From File** > From **Text/CSV**.
1. Browse to the .csv report file.
1. Change the **File Origin** to **65001 UTF** (or a Unicode code page identifier).
1. Change the **Delimiter** to **Comma**.
1. Select **Load**.

The report should show correctly.

## Reports available for download

| Report Name                      | What's in the report?                                                                                                                                                                                             | Aggregation level|
|----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|
| Azure Usage | Usage details for Azure subscriptions sold or managed by the partner. The usage details are split by meter category and other key dimensions. This report is aggregated monthly. | Monthly |
| Cloud Ascent - Agreement propensity | Propensity data shows customers' likelihood to renew the Agreements with Microsoft | No aggregation or lookback is applicable to this report. |
| Cloud Ascent - Azure propensity | Propensity data shows customers' likelihood to purchase Azure products | No aggregation or lookback is applicable to this report. |
| Cloud Ascent - Dynamics 365 propensity | Propensity data shows customers' likelihood to purchase Dynamics products | No aggregation or lookback is applicable to this report. |
| Cloud Ascent - Microsoft 365 propensity | Propensity data shows customers' likelihood to purchase Microsoft 365 products | No aggregation or lookback is applicable to this report. |
| Cloud Ascent - Surface propensity | Propensity data shows customers' likelihood to purchase Microsoft Surface products | No aggregation or lookback is applicable to this report. |
| CPOR - Microsoft 365 usage | Customer details with Monthly Active users, Paid Available units, Claim ID details and Date of association | Monthly |
| CSP Revenue Details| Only for the Partners who are monitoring for the CSP Direct partner eligibility. It gives the break-up of the Eligible revenue with respect to the various cloud products such as Azure, Microsoft 365, Dynamics 365, Power BI and EMS. | Monthly |
| Customers and Tenants | Information about customers that a partner is associated with. Provides information about key metrics, such as licenses sold, aggregated Azure consumed revenue (ACR), and so on. This report is aggregated monthly. | Monthly |
| Dynamics usage | Usage details about Dynamics related SKUs sold or managed by the partner. Provides customer information and key metrics such as MAU, qualified entitlements, and so on. | Monthly |
| EMS Usage | Usage details about Enterprise Mobility licenses sold or managed by the partner. Provides customer information and key metrics such as MAU, qualified entitlements, and so on. | Monthly |
| Microsoft Learn | Microsoft Learn reports show detail of Learners completing Learning path or Module. | N/A |
| Microsoft 365 Usage | Usage details of Microsoft/Office 365 licenses sold or managed by the partner. Provides customer information and key metrics, such as monthly active users (MAU), qualified entitlements, and so on. | Monthly |
| Power BI Usage | Usage details of Power BI licenses sold or managed by the partner. Provides customer information and key metrics such as MAU, qualified entitlement, and so on. | Monthly |
| Partner Profile | Information related to the partner, such as PartnerID, partner name, and partner city. | No aggregation or lookback is applicable to this report. |
| Reseller performance | Reseller information related to the MPA Status, Customer details, Subscriptions, Available Seats, Assigned Seats and Billed Revenue | Monthly |
| Subscriptions Details | Information about the subscriptions sold or managed by the partner, along with customer information. | Monthly |
| Teams usage 3P apps | Third party app usage details for the apps available in Teams | Monthly |
| Teams usage meetings and Calls | For Meetings, Calls or Phone Systems, Customer level details of Meeting count and meeting duration | Daily |
| Teams usage workload | For Meetings, Calls or Phone Systems, user count break up with respect to Desktop, Mobile or Web user count | Monthly |
| Trainings | Shows details about all the Certifications, Examinations and Assessments completed by a User | N/A |

The workloads: **TEAMS (standalone)** , **YAMMER**, **OUTLOOK MOBILE**, and **AZURE INFORMATION PROTECTION** shouldn't be listed on these Insights reports: **CPOR - M365 usage**, **M365 Usage**, **Customers and Tenants**, or **Subscriptions Details**. These workloads won't earn FY23 Incentives. The workloads are only available for active usage recognition. To learn more, see the Program Guide in the **FY23 Microsoft Commercial Partner Incentives Guide**, available for download at [Microsoft Commerce Incentive Resources](https://partner.microsoft.com/asset/collection/microsoft-commerce-incentive-resources).

## Next steps

- [Cloud product performance insights FAQ](insights-known-issues.md)
