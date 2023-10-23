---
title: Earnings - Reports overview in Partner Center
description: Get details about your earnings through reports in Partner Center
ms.date: 9/20/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-earnings
ms.topic: article
author: deeparamani
ms.author: deramani
---

# Earnings – Reports overview in Partner Center

**Appropriate roles**: *Incentives*: Incentives admin | Incentives user; *Marketplace/Store*: Financial contributor

The **Reports** page is the download hub of all reports available in the various pages of the Earnings workspace.

You can download reports that were created in either the **Earnings** or **Revenue** page with the desired filters applied. Or, you can create new reports from this page using the **New report** option.

To start a new report download:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Earnings** > **Reports**.
1. Select a report from the **New report** dropdown.

   :::image type="content" source="./media/earnings/new-report-dropdown.png" lightbox="./media/earnings/new-report-dropdown.png" alt-text="Screenshot shows the Earnings Reports screen, with the New report dropdown open. The dropdown shows several report options.":::

     | Report name | Purpose | Applicability |
     | --- | ---| --- |
     | Earnings - Default | Contains earnings, payment and associated reconciliation details. Template includes incentive-specific, store-specific and marketplace-specific attributes. See [Earnings default schema](./earnings-default.md). | For all incentive programs, store and marketplace programs |
     | Earnings - Growth | Contains earning, payment and associated reconciliation details for incentives levers that measure growth. See [Earnings growth schema](./earnings-growth.md). | For incentive programs – growth levers only |
     | Earnings – Marketplace | Contains earnings, payment and associated reconciliation details. Template includes marketplace specific attributes only. See [Earnings marketplace schema](./earnings-marketplace.md). | For marketplace program only. |
     | Earnings - Store | Contains earnings, payment and associated reconciliation details. Template includes store specific attributes only. See [Earnings store schema](./earnings-store.md). | For store programs only |
     | Payments | Contains payment order details only. See [more about payments](./earnings-payments.md). | For all incentive, store and marketplace programs. |
     | Ineligible revenue usage | Contains transaction/usage reconciliation information for $/MAU that became ineligible for Microsoft commerce incentives. See [Ineligible revenue usage schema](./earnings-ineligible-revenue-usage.md). | For Microsoft commerce incentives only |

1. Choose the format and time period for the report to be downloaded, then select **Next**.

   :::image type="content" source="./media/earnings/configure-report-details.png" lightbox="./media/earnings/configure-report-details.png" alt-text="Screenshot shows the Configure report: Report details page, which includes the CSV and TSV formats, and time periods including 3 months, 6 months, 12 months, and custom.":::

1. Choose the filters to apply and select **Next**.

   :::image type="content" source="./media/earnings/configure-report-filters.png" lightbox="./media/earnings/configure-report-filters.png" alt-text="Screenshot shows the Configure report: Filters page, which includes enrollment IDs (Example: Denmark), program names (Example: Azure incentives), Engagement name (Example: Azure CSP motion incentives), and Levers (Example: AMMP Infra/Database Migration (Large))":::

1. Review details and select **Complete**. This queues the report to be downloaded.

   :::image type="content" source="./media/earnings/configure-report-review-complete.png" lightbox="./media/earnings/configure-report-review-complete.png" alt-text="Screenshot shows the Configure report: Review and complete page, which includes report details including the report name, format, time period, as well as filters selected.":::

1. Wait for the report to move from the **Queued** state to the **Completed** state. Then, select the checkbox next to the report you want to download, and select **Download**.

   :::image type="content" source="./media/earnings/earnings-reports-list.png" lightbox="./media/earnings/earnings-reports-list.png" alt-text="Screenshot shows the Earnings Reports screen, with one report's status showing Queued, and two more that show as Completed.":::

   If the Status shows as failed, retry in a few minutes.

1. Find the downloaded file or files. Compressed download files are organized as follows:
   - If the total record count for the export request results in less than or equal to 50,000, a single file is produced.
   - If the total record count for the export result set is greater than 50,000 and less than or equal to 500,000, the files will be split by each earning month, up to the maximum file size limit of 1 GB.
   - If the total record count for a month is > 500,000, the export might result in multiple files, up to the maximum file size limit of 1 GB.
 
   :::image type="content" source="./media/earnings/file-explorer-data-split-across-two-files.png" lightbox="./media/earnings/file-explorer-data-split-across-two-files.png" alt-text="Screenshot of File Explorer showing exported data for multiple months. The data for April 2022 are split across two files, 2022-04_25 and 2022-04_26.":::

You can also get the earnings, payouts and the corresponding transactional details through an API, through a .CSV file. To learn more, see [Manage earnings - Partner app developer](./developer/manage-earnings.md). API support is not yet available for ineligible revenue usage details.

## Next steps

- [Earnings default schema](./earnings-default.md)
- [Earnings growth schema](./earnings-growth.md)
- [Earnings marketplace schema](./earnings-marketplace.md)
- [Earnings store schema](./earnings-store.md)
- [Earnings payments](./earnings-payments.md)
- [Ineligible revenue usage schema](./earnings-ineligible-revenue-usage.md)
- [Manage earnings - Partner app developer](./developer/manage-earnings.md)
