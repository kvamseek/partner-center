---
title: Apps and games download reports 
ms.topic: article
ms.date: 07/26/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-insights
description: Learn how to create a new Apps and Games report, and prepare it for download.
author: JulCsC
ms.author: juliacawthra
ms.reviewer: deepganguly
---

# Apps and games download reports

**Appropriate roles**: Executive report viewer | Report viewer

This article explains how to create a new Apps and Games report, and how to aggregate and frame time for download.

## Authorization required

For the **Apps and games** tile to be enabled within **Downloads hub**, the logged-in user should be enrolled in the AppDev program.

:::image type="content" source="media/downloads-hub/apps-games-authorization-required.png" lightbox="media/downloads-hub/apps-games-authorization-required.png" alt-text="Screenshot of the authorization required screen":::

## Create a new report

Create, download or schedule downloadable reports. Select either of the following paths:

**Basic:** Generate a report with familiar steps in the classic download report's view.

The path for basic is: *Program > Report name > Select columns (Optional) > Select time range > Update the file name > Select the file type > Preview report and select download.*

**Advanced:** With the advanced path, create templates, schedule reports, and access the templates, which help in report discovery and usability.

**Common Elements:**

- **Program Selector**: Select the program for the report to be downloaded.

   :::image type="content" source="media/downloads-hub/apps-games-program-selector.png" lightbox="media/downloads-hub/apps-games-program-selector.png" alt-text="Screenshot of the program selector screen":::

- **Report name:** A generic name is added to the report by default. Update the name to any string and the downloaded file name will have the same name.

   :::image type="content" source="media/downloads-hub/report-name.png" lightbox="media/downloads-hub/report-name.png" alt-text="Screenshot of report name modal.":::

- **Preview Data**: Preview the data after selecting any of the templates (or columns). The first 15 rows of data are shown based on their selection, which is a change from how the report generation currently works.

### Basic path

- **Column selector**: Lets you select the columns that are available for a report.

  :::image type="content" source="media/downloads-hub/apps-games-basic-column-selector.png" lightbox="media/downloads-hub/apps-games-basic-column-selector.png" alt-text="Screenshot of the basic column screen":::

### Advanced path

**Template:** Templates are preselected groups of columns that are applied to the report before downloading.

- Default Templates
- Curated templates - apply to any generic use case.
- Custom Templates – create a template using any set of columns.

  :::image type="content" source="media/downloads-hub/apps-games-template.png" lightbox="media/downloads-hub/apps-games-template.png" alt-text="Screenshot of the games template screen":::

**Column selector** – Select columns available for a report. You might not need all of the columns available in the report, which is true for reports like *Azure usage*, which has around 40 columns.

  :::image type="content" source="media/downloads-hub/apps-games-adv-column-selector.png" lightbox="media/downloads-hub/apps-games-adv-column-selector.png" alt-text="Screenshot of the advanced column selector screen":::

- **Adding to favorites**: Frequently used templates can be saved as favorites, which can be accessed on the download reports landing page. There can be up to five favorites for the user. Any new favorites prompt the user to replace an existing favorite to make room for the new one.
  - Only user defined templates can be added to the favorites.

  :::image type="content" source="media/downloads-hub/file-type.png" alt-text="Screenshot of file type options.":::

- **Reset the report creation**: If you make an error, you can reset the selection, which removes all the selections made in area, template, columns, and filters.

## Reports scheduled

You can find all of the reports scheduled under the Reports Scheduled section.

  :::image type="content" source="media/apps-games-download-reports/reports-apps-games.png" lightbox="media/apps-games-download-reports/reports-apps-games.png" alt-text="Screenshot showing the Scheduling with the configured options.":::

The following details are displayed in this section:

- **Report name:** Shows the user the defined name or the default name based on the report type for unique identification of the scheduled report.
- **Occurrence count:** Shows the number of occurrences, which are planned as per the user.
- **Program details:** Shows the program name to which the report belongs.
- **Columns and filter details:** Shows the count of selected columns and filters applied.
- **Time range:** Shows the time range for which the report is scheduled.

## Aggregation and timeframe for downloading

The following table displays the aggregation and timeframe applicable for the datasets.

> [!NOTE]
> The items marked with an asterisk **(*)** are timeframe additions as part of Downloads hub and applicable for only single app download.

|       Data       |       Frequency          | Downloads hub export for all apps | Downloads hub export for single apps |
| ------------ | --------------- | ------------------------------------ | --------------------------------------- |
|Acquisition | Daily     | 30 days<br>3 months   | 30 days<br>3 months  |
| | Hourly    | 72 hours      | 72 hours |
| | Weekly    | 6 months<br>12 months  | 6 months<br>12 months  |
| | Monthly   | | 4 years (2,3,4)\*  |
|Add-on acquisition | Daily  | 30 days<br>3 months   | 30 days<br>3 months  |
| | Weekly    | 6 months<br>12 months  | 6 months<br>12 months |
| | Monthly   | | 4 years (2,3,4)\*  |
| Usage | Daily  | 30 days<br>3 months   | 30 days<br>3 months  |
| | Monthly    | 6 months<br>12 months  | 6 months<br>12 months<br>4 years (2,3,4)\*   |
| Health  | Hourly  | 72 hours | 72 hours     |
|     | Monthly | | 30 days\*     |
| Channel and conversion | Daily | 30 days<br>30 months   | 30 days<br>30 months   |
|     |  Weekly | 6 months<br>12 months  | 6 months<br>12 months |
|     | Monthly | | 4 years (2,3,4)\*  |
| Install  | Daily  | 30 days<br>30 months   | 30 days<br>30 months   |
|    | Weekly |  6 months<br>12 months   |  6 months<br>12 months  |
|    | Monthly     |     | 4 years (2,3,4)\*  |
| Wishlist | Snapshot |     |    |
| Reviews  |  None | 30 days | 30 days<br>1 year\*  |
| Ratings | Daily   | 30 days<br>30 months   | 30 days<br>30 months  |
|   | Weekly  | 6 months<br>12 months  | 6 months<br>12 months |
|   | Monthly |     | 4 years (2,3,4)\*  |

### Limits to consider

- Favorites: 30 per program
- Templates: 200 per program

#### Restrictions on the scheduling of reports

Because scheduling of the reports results in preparing the report for download, there's opportunity for the scheduling of the reports to be misused. To avoid such scenarios, there are two-level restrictions on the scheduling of the reports:

Program level total scheduled reports count:

- **Level 1:** Per program: 40 scheduled reports per user
- **Level 2:** Allowed maximum time range restriction when scheduled reports are
selected

| **Scheduling frequency** | **Month time range allowed**           |
|--------------------------|----------------------------------------|
| Hourly                   | Last 30 days                           |
| Daily                    | Last 30 days                           |
| Weekly                   | Last 30 days                           |
| Monthly                  | Last two years                         |
| Yearly                   | Lifetime or last years (as applicable) |

Users can't create more than allowed count of scheduled reports and the time range has to comply, as shown in the scheduling frequency.

#### Scheduled report execution limits

- **Hourly**: 30 Days (720 executions)
- **Daily**: Six months (180 executions)
- **Weekly**: One year (52 executions)
  - When the selection for daily is more than seven
days
- **Monthly**: Two years (24 executions)
- **Yearly**: Five years (five executions)


















