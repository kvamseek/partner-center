---
title: Use your reconciliation files
ms.topic: article
ms.date: 10/12/2023
description: Learn about reconciliation files in Partner Center and how to interpret the detailed, line-item views of charges for a given billing cycle.
ms.service: partner-dashboard
ms.subservice: partnercenter-billing
author: sodeb
ms.author: sodeb
---

# Learn how to read the line items in your Partner Center reconciliation files

**Appropriate roles**: Billing admin | Global admin

You can download your reconciliation files from Partner Center for a detailed, line-item view of each charge in a billing cycle.

Line-item details include charges for each customer's subscriptions, and detailed events (such as a mid-term addition of licenses to a subscription).

For information about how to read your invoice, see [Read your bill](read-your-bill.md).

## Understand reconciliation file fields

|Reconciliation file field                                             |Shows     |
|:---------------------------------------------------------------------|:---------|
| [Legacy License-based](license-based-recon-files.md)                 | Costs and quantities of legacy Office and Dynamics products |
| [Legacy Usage-based](usage-based-recon-files.md)                     | Costs and quantities of legacy Microsoft Azure products |
| [New Commerce Daily rated usage](daily-rated-usage-recon-files.md)   | Daily usage and costs for new commerce consumption-based products (Azure plan) |
| [New Commerce Reconciliation](modern-invoice-reconciliation-file.md) | Monthly costs, quantities, and usage for all new commerce products |

## Understand charge types in reconciliation files

To understand the types of charges in reconciliation files (the **ChargeType** column), see [Reconciliation file charge types](recon-file-charge-types.md).

## Fix formatting issues

Occasionally, a reconciliation file might have formatting issues. For example, this issue might occur if the *en-us* locale isn't used.

To fix any formatting issues in your reconciliation files:

1. Open the reconciliation file (in .csv format) in Microsoft Excel.
2. Select the first column in the file.
3. Open the **Convert Text to Columns Wizard**.
4. On the ribbon, select **Data**, then select **Text to Columns**.
5. In the wizard, select **Delimited file type**, and then select **Next**.
6. In the **Delimiters** field, select **Comma**. (If **Tab** is already selected, you can leave this option selected.) Then, select **Next**.
7. In the **Column data format** field, select **Date:MDY**, and then select **Next**.
8. In the **Column data format** field, select **Text** for all amount columns, and then select **Finish**.

## Download reconciliation files programmatically

Reconciliation files can be large and are sometimes difficult to download. To download reconciliation files programmatically, see [Get invoice line items](/partner-center/develop/get-invoiceline-items).

## Download reconciliation files asynchronously

### What is an asynchronous file download?

*Asynchronous file download* enables you to download files in the background without having to stay at the UI until the download is complete.

To download a file asynchronously, use the following steps:

1. Select a file that you want to download.
2. Request a download.
3. Exit the page.
4. Come back to this page at your convenience to see if the file is ready.

### Where do I download the file asynchronously?

To download the files asynchronously, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Billing** workspace.
2. On the left, go to the **"Download file"** task menu to go to the asynchronous file download UI, **Billing | Download file**.

> [!NOTE]
> **New Commerce** reconciliation files are downloaded asynchronously from the Partner Center portal, which improves the download experience and makes it more efficient.
>
> To download a file:
>
> 1. Go to the **"Billing"** workspace and and select the **"Billing history"** task menu.
> 2. On the **"Billing history"** UI,  select the reconciliation file you want to download.
> 3. A message will appear at the top, informing you that your file is being prepared and will be available in the **"Download file"** UI.

### How do I download the file asynchronously?

Welcome to the **"Download file"**! Here, you can choose what type of report you want to download. To start, select the **"Report type"** option. You'll then see a table that explains the different report types available to you.

Choose the type of report from the table that best fits your needs. Once you have made your selection, you'll be able to proceed with downloading your report.

It's important to note that the report type you choose will affect the format and content of the report. So be sure to choose the type that will provide you with the information you need.

|Report type |Provides  |
|:---------|---------|
|Daily Rated Usage Reconciliation-closed | Billed daily cost and consumption for the Azure plan (pay-as-you-go) in the closed billing period   |
|Daily Rated Usage Reconciliation-recent activity | Estimated daily cost and consumption for the Azure plan (pay-as-you-go) in the open billing period  |
|Reconciliation-closed  |  Total cost of all transactions for the closed billing period   |
|Reconciliation-recent activity  |   Estimates for non-pay-as-you-go transactions in an open billing period   |

To generate a reconciliation-closed report:

1. Choose a year and month to find the relevant invoices.
2. Select the invoice and select the "**Download"** link below the "**Report type"** option.

The system adds your request to a queue, gather the necessary information, and create the report.

Your request's **Download** link becomes active when the data is ready, and the status changes to **Completed**. You can track the progress of your request by using the status.

For an open billing period report, choose the correct currency and period ("current" or "previous") to get the report you need.

When you select "Download," your request is added to the queue, and our system starts gathering and organizing your data. This process can take some time, depending on the amount of data that needs to be processed.

Once the system is done collecting and organizing your data, the **Download** link for your request becomes active, and the status of your request changes to **Completed**.

To check the progress of your download request, look at the status. If it says "Progressing or Checking," our system is still gathering and organizing your data.

Here are the statuses:

- **Queued:** Request submitted
- **Processing:** The system is gathering the report data
- **Checking:** Ensuring data is being prepared in the background
- **Completed:** Report is available for download
- **Failed:** The system couldn't create the report

Filtering your reports is easy and can help you quickly find the information you need. You can filter your reports by **report type, report format, status,** and **date range.** For example, if you only want to see reports of a certain type, you can select that report type from the filter options. If you want to see reports from a certain time period, you can select the date range.

**"Additional info"** is another helpful way to find your downloaded reports. It has details such as **currency, period, billing year, month,** and **invoice number** that can help you quickly find the report you're looking for. For example, you can filter by the billing month if you want to see a report from a specific billing month.

## If your file exceeds the row limit in Excel

If you can download a reconciliation file but can't open it in Microsoft Excel, that probably means the file contains more rows than Excel allows. If that happens, you can:

- [Open a reconciliation file in an Excel Power Query](#open-a-reconciliation-file-in-excel-power-query)
- [Open a reconciliation file in Power BI](#open-a-reconciliation-file-in-power-bi)

## Open a reconciliation file in Excel Power Query

1. Download the reconciliation file from the Partner Center.
1. Open a new blank workbook in Microsoft Excel.
1. Navigate to **Data** tab, then select **Get Data** > **From File** > **From Text/CSV**, and import the CSV (Comma Separated Value) reconciliation file.
1. After a while, you will see a window with the file preview.
1. In that window, select the **Load** dropdown menu > **Load To**.

   :::image type="content" source="media/use-the-reconciliation-files/file-preview-load-to.png" alt-text="Screenshot of the File preview window, with the dropdown next to Load open, and the selection Load To inside the drop-down selected.":::

1. In the Import Data dialog box, select the options as indicated in the following screenshot.

   :::image type="content" source="media/use-the-reconciliation-files/import-data-only-create-connection.png" alt-text="Screenshot of the Import Data window, with two items highlighted: Only Create Connections and Add this data to the Data Model.":::

1. Select **OK**, and wait for the loading process to complete.
1. On the right side, you will find the name of the file and the number of rows. Double-click this area to open the Power Query Editor.

   :::image type="content" source="media/use-the-reconciliation-files/queries-and-connections-test-recon-data.png" alt-text="Screenshot of the Queries & Connections window, with a sample of a report called Test Recon Data highlighted.":::

1. Now, when you scroll down, you'll notice that the new rows are added dynamically.
1. To search for specific transactions, use the filter option as shown in the following screenshot. You can also aggregate transactions or do mathematical calculations using the "Group By" or "Statistics" features.

   :::image type="complex" source="media/use-the-reconciliation-files/power-query-filter.png" lightbox="media/use-the-reconciliation-files/power-query-filter.png" alt-text="Screenshot of Excel Power Query Editor, with two highlighted items, Group By and Statistics.":::
    In the spreadsheet, the PartnerId box drop-down is open, and the Text Filters drop-down is highlighted.
    :::image-end:::

1. For instance, to find the number of billable days in the charge cycle, you can use the **Custom Column** feature to calculate the duration between the charge start and end dates. Additionally, Power Query offers many features that allow various computations.

   :::image type="complex" source="media/use-the-reconciliation-files/power-query-custom-column.png" lightbox="media/use-the-reconciliation-files/power-query-custom-column.png" alt-text="Screenshot of Excel Power Query Editor. In the menu bar, Add Column is highlighted.":::
   In the ribbon, Custom column is highlighted. In the spreadsheet, the BillableDays column is highlighted. On the side, the Query Settings tab shows options for Properties and Applied Steps.":::

1. After applying the required filters in the Power Query, you can transfer the limited transaction data to Excel by following these steps.

   :::image type="content" source="media/use-the-reconciliation-files/power-query-copy-table.png" lightbox="media/use-the-reconciliation-files/power-query-copy-table.png" alt-text="Screenshot of Excel Power Query Editor. In the spreadsheet, the CreditReasonCode drop-down is open. The menu item: Copy Entire Table is highlighted.":::

## Open a reconciliation file in Power BI

To open a reconciliation file in Power BI, use the following steps:

1. Download the reconciliation file as you normally would.
2. Download, install, and open an instance of Microsoft Power BI.
3. On the Power BI **Home** tab, select **Get data**.
4. In the list of **Common data sources**, select **Text/CSV**.
5. When prompted, open your reconciliation file.

## Negative amount displayed

If you see a negative amount for some transactions in your reconciliation file, that's likely because:

- You have recently made changes to the subscription, such as canceling, upgrading, adjusting licenses, or other modifications.
- You received credit for a service level agreement (SLA) violation, Azure consumption, price, or license adjustments.

To get more information about this transaction, refer to the `ChargeType` attribute in the reconciliation file.

## How is the total cost calculated for new commerce license-based purchases?

Cost is calculated using `EffectiveUnitPrice,` not `UnitPrice.` The `UnitPrice` only shows the list price from the price sheet, but the `EffectiveUnitPrice` is determined based on several things:

- Discounts (such as promotions or tiered pricing) and adjustments (like Partner Earned Credit) to the unit price.
- The number of billable days, which are counted from the time an event happens until the end of the charge cycle.
- Local tax amount.

*It's important to know that the **"UnitPrice"** of a subscription stays the same as long as the subscription is active. If it changes in the middle of the term, the reconciliation data can show the new price, but it's not used to calculate the costs.*

To check if the cost is correct, you should focus on the `EffectiveUnitPrice` and use it to create invoices for your customers.

## Why does my invoice reconciliation data show a recurring charge for a product for which there are no daily charges?

If you see a recurring charge on your invoice reconciliation data but daily charges for the product are zero, then don't worry. There's a simple explanation for this: Some products, like Azure Savings Plan or Azure Reservation, have a fixed price that you pay either monthly, annually, or one-time, depending on your billing plan, for a certain number of units or quantities you use in the charge cycle.

Here's what you need to know:

- Even if your daily charges are zero, you'll still have to pay the fixed price that you agreed to at the time of purchase. This is the recurring charge that shows on your invoice reconciliation data.
- Until you exceed that unit, your daily charges will show as zero against your consumed unit or quantity. This means that you won't be charged anything extra for the product until you surpass the agreed unit or quantity.
- However, if you go over the agreed unit or quantity, you'll incur pay-as-you-go charges for the overages. This means that you'll be charged extra for any usage above the agreed unit or quantity.

In short, recurring charges for fixed-priced products like the Azure Savings Plan, Azure Reservation, or other special subscriptions will show up on your invoice reconciliation data even if your daily charges are zero until you go over the agreed unit or quantity. Once you go over that unit, you'll be charged for any additional usage as pay-as-you-go charges.

See how an Azure reservation or savings plan is linked to an Azure subscription to check the costs.

## How do you find the Azure subscription ID for a product?

Follow these steps to learn how to map your Azure subscription ID and figure out the costs and usage:

### Pay-As-You-Go products

- To match your Azure usage with your Azure subscription, start by linking the `SubscriptionID` from your invoice reconciliation with the daily rated usage data. This will help you identify the related `EntitlementID,` which is your Azure subscription ID. Once you have this ID, you can easily map your usage charges.

Follow these steps to find out how much your Azure reservation or savings plan costs and usage:

### Azure Reservations

- For Azure reservations, link the `ReservationOrderId` from your invoice reconciliation to the same ID in the `AdditionalInfo` attribute of the daily rated usage data.

### Azure Savings Plans

- For Azure savings plans, link the `ReservationOrderId` to the `BenefitOrderId` attribute in the daily rated usage data.

Using invoice reconciliation and daily rated usage data, it's easy to track how much you use Azure and how much it costs. Follow these steps to keep track of your subscription and save money with Azure reservations and savings plans.

## How do you find Azure credits in the invoice reconciliation and daily rated usage files?

You can find out how much Azure credit a customer has been given by checking invoice reconciliation and daily usage data.

### Invoice reconciliation

- Azure credits can only be used for first-party Azure services and reservations. Keep in mind that reservations might be applicable in some cases.
- The credit line items display a negative `Subtotal` and `Total`.
- The attribute `ChargeType` for the credit line item is set to **"customerCredit"**, while the `CreditReasonCode` attribute includes text specific to the credit type. For instance, the Azure Credit Offer would be displayed as **"Azure Credit Offer."**
- The invoice reconciliation data displays customer usage and credit received. Organize the transactions by `ProductID`, `SKUID`, `AvailabilityID`, `OrderDate`, and either `CustomerName` or `CustomerID`. Add up the `Total` to know the credit amount.
- The `BillableQuantity` for charge and credit line items must match. Additionally, consumption charges and credits should be offset by each other in the `EffectiveUnitPrice`.

### Daily rated usage

- Sort by customer tenant ID and filter by `CreditType` = **"Azure Credit Applied"** and `CrditPercentage` = "**100."**
- Add up the `BillingPreTaxTotal` to know the credit amount.

> [!NOTE]
> Some Azure credits may not be included in the daily rated usage data, as they aren’t calculated daily but only at the end of the billing period. However, you can always find this credit information in the invoice reconciliation data.

## What do different prefixes for Reservation Order ID mean?

The prefix shows where you bought your Azure reservation.

1. Purchases made via the Partner Center will be prefixed with **"RIOderId".**
2. Purchases made through a test account in the Partner Center will be prefixed with **"PCTest".**
3. **No prefix** is used for purchases made through Azure Cost Management.

## Next steps

- [Understand your bill and reconciliation file&mdash;learn how to find them in Partner Center](read-your-bill.md)
