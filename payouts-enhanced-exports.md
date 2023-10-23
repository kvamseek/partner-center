---
title: Payouts export data page
description: Explains how to use the enhanced export data page to generate customized transaction history reports
author: deeparamani
ms.author: deramani
ms.service: partner-dashboard
ms.subservice: partnercenter-payouts
ms.topic: how-to
ms.date: 03/17/2023
ms.custom: template-how-to
---

# Payouts export data page

**Appropriate roles**: Incentives admin | Incentives user

This article discusses enhancements to the data exporting experience for **Payouts** in Partner Center.

This guided experience provides new default templates for exporting your transaction history reports. It also has the dynamic capability to let you create your own customized templates for your transaction history reports.

## Access the export data page

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Payouts**.
2. Select **Incentive export** or **Transaction history** from the menu.

> [!NOTE]
> You will have access to this page if you are an [incentive admin or incentive user](reconciliation-faq.md#roles-and-permissions). What you see will depend on which program and Microsoft AI Cloud Partner Program combinations you have access to (similar to **Transaction history** and **Payment** pages).

## Export your data

1. Select the type of data you'd like to export.
   :::image type="content" source="media/payouts/export-data.png" lightbox="media/payouts/export-data.png" alt-text="Screenshot showing export data options.":::

   - **Earning, transaction, payment status details** – Selecting this provides you a download of the earnings, the associated transactions (and reconciliation details like customer, subscription) along with the payment details. Reference available attributes in [Transaction history](transaction-history.md#transaction-history-download).
   > [!NOTE]
   > Transactional details like customer, subscription etc won’t be available for earning resulting from multiple consumption, usage, or transactions in this report (download the report to get these details. Transactional details will also not be available for global, local campaigns, or manual adjustments by design.  

   - **Earning, transaction, payment status details (Growth Levers)** – If an earning comes from multiple underlying transactions, then this download contains the transactional details (Reference available attributes [here](#earning-transaction-payment-status-details-growth-levers-download-details)). This report must always be read in correlation with Earning, transaction, payment status details using `earningID` to join the dataset. This report must be downloaded for Azure growth engagements in Microsoft Commerce Incentives, as an example.

   - **Payment details** – Download will contain only information about the payment order, payment ID, and the amount sent to your bank and taxes. Reference available attributes in [Payment](payments.md#payments-download).

   - **Ineligible revenue details** – Applicable for Microsoft commerce incentives only. Download this to understand why some revenue or usage became ineligible and why. Reference available attributes in [Revenue summary](revenue-summary.md#exported-data-attributes).

   - **Historical statements** - To download statements 3 years or older.

2. Determine the type of reports you can download.

   :::image type="content" source="media/payouts/report-template.png" lightbox="media/payouts/report-template.png" alt-text="Screenshot showing report template options.":::

   For example, if you select **Earning, transaction, payment status details** in step 1, you see four different template options:

   - **Default transaction history**: This report shows all possible attributes  available in the report across all programs (incentives, commercial and consumer marketplaces). This download template was the template that was available before October 2021.

   - **Default market place**: This report shows all attributes required for Microsoft AI Cloud Partner Program members enrolled in commercial marketplace programs, such as Azure Marketplace.

   - **Default store**: This report shows all attributes required for Microsoft AI Cloud Partner Program members enrolled in the consumer store programs, such as Microsoft Store, Minecraft, and MS Flight Simulator.

   - **Custom transaction history**: This report lets you customize your transaction history report.

   If you select **Earning, transaction, payment status details** **(Growth)** in step 1, you can select the **Transaction summary** template in step 2. If you select **Payment details** in step 1, you see one "Payments" template in step 2. If you select **AGI revenue details** in step 1, you can choose between the **Summarized program revenue** (launched in Jan 2023), **Program revenue** or **Customer adds** templates in step 2.

   Refer to the [table](#attributes-available-to-download) to learn about the attributes available to download in each type of report.

3. Select a report file format.

      :::image type="content" source="media/payouts/report-file-format.png" lightbox="media/payouts/report-file-format.png" alt-text="Screenshot showing report file format selections.":::

4. Choose your time period and apply any other filters, then select **Download data**.

      :::image type="content" source="media/payouts/time-period-filters.png" lightbox="media/payouts/time-period-filters.png" alt-text="Screenshot showing report time period selection and filter option.":::

> [!NOTE]
> You can export data and manage requests from the **Download requests** table.

## Create your customized transaction history report

Customize your transaction history reconciliation report to fit your needs. You can create and manage up to five report templates.

1. Select **+ Custom transaction history** to set up a new reconciliation template.

   :::image type="content" source="media/payouts/custom-trans-history.png" lightbox="media/payouts/custom-trans-history.png" alt-text="Screenshot showing custom transaction history setup.":::

2. Enter a template name and a short description, then select **Next**.

      :::image type="content" source="media/payouts/template-name.png" lightbox="media/payouts/template-name.png" alt-text="Screenshot showing new custom reconciliation template fields.":::

3. Select the data columns you'd like to include and review the default columns already listed on the report. Select **Next**.

     :::image type="content" source="media/payouts/data-selection.png" lightbox="media/payouts/data-selection.png" alt-text="Screenshot showing new custom reconciliation template data-selection options.":::

4. Review your template details and data selections, make edits if needed, and then select **Create custom template**.

      :::image type="content" source="media/payouts/new-custom-template.png" lightbox="media/payouts/new-custom-template.png" alt-text="Screenshot showing confirmation screen for new custom reconciliation template.":::

5. Select **Download** from the next screen to export your data. You can also add, edit, download, or delete other templates from this screen.

      :::image type="content" source="media/payouts/download-manage-templates.png" lightbox="media/payouts/download-manage-templates.png" alt-text="Screenshot showing manage templates and download data options.":::

## Attributes available to download

This table describes the attributes available to download per report type.

| **Column name**                    | **Default Transaction History** | **Default Marketplace** | **Default Store** | **Custom Transaction History** |
|------------------------------------|---------------------------------|-------------------------|-------------------|--------------------------------|
| agreementEndDate                   | Available                       | Not available           | Not available     | Available: Default              |
| agreementNumber                    | Available                       | Not available           | Not available     | Available: Default              |
| agreementStartDate                 | Available                       | Not available           | Not available     | Available: Default              |
| bucketSize                         | Available                       | Not available           | Not available     | Available: Optional             |
| calculationDate                    | Available                       | Available               | Available         | Available: Default              |
| claimId                            | Available                       | Not available           | Not available     | Available: Default              |
| customerCountry                    | Available                       | Available               | Not available     | Not available                  |
| customerEmail                      | Available                       | Available               | Not available     | Not available                  |
| customerId                         | Available                       | Available               | Not available     | Available: Default              |
| customerName                       | Available                       | Available               | Not available     | Available: Default              |
| customerTenantId                   | Available                       | Not available           | Not available     | Available: Optional             |
| desktopCount                       | Available                       | Not available           | Not available     | Not available                  |
| distributorId                      | Available                       | Not available           | Not available     | Available: Optional             |
| distributorName                    | Available                       | Not available           | Not available     | Available: Optional             |
| earningAmount                      | Available                       | Available               | Available         | Available: Default              |
| earningAmountInLastPaymentCurrency | Available                       | Available               | Available         | Available: Optional             |
| earningAmountUSD                   | Available                       | Available               | Available         | Available: Default              |
| earningDate                        | Available                       | Available               | Available         | Available: Default              |
| earningExchangeRate                | Available                       | Available               | Available         | Available: Default              |
| earningId                          | Available                       | Available               | Available         | Available: Default              |
| earningRate                        | Available                       | Available               | Available         | Available: Default              |
| earningType                        | Available                       | Available               | Available         | Available: Default              |
| engagementId                       | Available                       | Not available           | Not available     | Available: Default              |
| engagementName                     | Available                       | Not available           | Not available     | Available: Default              |
| estimatedPaymentMonth              | Available                       | Available               | Available         | Available: Default              |
| exchangeRateDate                   | Available                       | Available               | Available         | Available: Default              |
| externalReferenceId                | Available                       | Available               | Available         | Available: Default              |
| externalReferenceIdLabel           | Available                       | Available               | Available         | Available: Default              |
| fundCategory                       | Available                       | Not available           | Not available     | Available: Optional             |
| instantRebateAmount                | Available                       | Not available           | Not available     | Available: Optional             |
| invoiceDate                        | Available                       | Not available           | Not available     | Available: Optional             |
| invoiceNumber                      | Available                       | Available               | Not available     | Available: Default              |
| lastPaymentCurrency                | Available                       | Available               | Available         | Available: Optional             |
| lever                              | Available                       | Available               | Available         | Available: Default              |
| LicensingProgramName               | Available                       | Not available           | Not available     | Available: Optional             |
| LineItemId                         | Available                       | Available               | Not available     | Not available                  |
| localProviderSeller                | Available                       | Not available           | Not available     | Not available                  |
| milestone                          | Available                       | Not available           | Not available     | Available: Optional             |
| OrderId                            | Available                       | Available               | Available         | Available: Optional             |
| parentProductId                    | Available                       | Available               | Available         | Not available                  |
| parentProductName                  | Available                       | Available               | Available         | Not available                  |
| participantId                      | Available                       | Available               | Available         | Available: Default              |
| participantIdType                  | Available                       | Available               | Available         | Available: Default              |
| participantName                    | Available                       | Available               | Available         | Available: Default              |
| partnerCountryCode                 | Available                       | Available               | Available         | Available: Default              |
| partNumber                         | Available                       | Available               | Available         | Available: Default              |
| paymentId                          | Available                       | Available               | Available         | Available: Default              |
| paymentStatus                      | Available                       | Available               | Available         | Available: Default              |
| paymentStatusDescription           | Available                       | Available               | Available         | Available: Default              |
| productId                          | Available                       | Available               | Available         | Available: Optional             |
| productName                        | Available                       | Available               | Available         | Available: Default              |
| productType                        | Available                       | Available               | Available         | Not available                  |
| Program Code                       | Available                       | Not available           | Not available     | Available: Optional             |
| programName                        | Available                       | Not available           | Available         | Available: Default              |
| purchaseOrderCoverageEndDate       | Available                       | Not available           | Not available     | Not available                  |
| purchaseOrderCoverageStartDate     | Available                       | Not available           | Not available     | Not available                  |
| purchaseOrderType                  | Available                       | Not available           | Not available     | Not available                  |
| purchaseTypeCode                   | Available                       | Not available           | Not available     | Available: Default              |
| purchaseTypeName                   | Available                       | Not available           | Not available     | Not available                  |
| quantity                           | Available                       | Available               | Available         | Available: Default              |
| reasonCode                         | Available                       | Available               | Available         | Available: Default              |
| resellerCountry                    | Available                       | Available               | Not available     | Not available                  |
| resellerId                         | Available                       | Available               | Not available     | Available: Optional             |
| resellerName                       | Available                       | Available               | Not available     | Available: Optional             |
| resourceId                         | Not available                   | Not available           | Not available     | Not available                  |
| SkuId                              | Available                       | Not available           | Not available     | Not available                  |
| storeFee                           | Available                       | Available               | Available         | Not available                  |
| subscriptionEndDate                | Available                       | Not available           | Not available     | Available: Optional             |
| subscriptionId                     | Available                       | Not available           | Not available     | Available: Default              |
| subscriptionStartDate              | Available                       | Not available           | Not available     | Available: Optional             |
| taxCity                            | Available                       | Available               | Available         | Not available                  |
| taxCountry                         | Available                       | Available               | Available         | Not available                  |
| taxRemitModel                      | Available                       | Available               | Available         | Not available                  |
| taxRemitted                        | Available                       | Available               | Available         | Not available                  |
| taxState                           | Available                       | Available               | Available         | Not available                  |
| taxZipCode                         | Available                       | Available               | Available         | Not available                  |
| tpan                               | Available                       | Not available           | Available         | Not available                  |
| transactionAmount                  | Available                       | Available               | Available         | Available: Default              |
| transactionAmountUSD               | Available                       | Available               | Available         | Available: Default              |
| transactionCountryCode             | Available                       | Available               | Available         | Available: Default              |
| transactionCurrency                | Available                       | Available               | Available         | Available: Default              |
| transactionDate                    | Available                       | Available               | Available         | Available: Default              |
| transactionExchangeRate            | Available                       | Available               | Available         | Available: Default              |
| transactionId                      | Available                       | Available               | Available         | Available: Default              |
| transactionPaymentMethod           | Available                       | Available               | Available         | Available: Default              |
| transactionType                    | Available                       | Available               | Available         | Available: Default              |
| userCount                          | Available                       | Not available           | Not available     | Not available                  |
| workload                           | Available                       | Not available           | Not available     | Available: Default              |

## Earning, transaction, payment status details (Growth Levers) download details

| **Attributes**            | **Description**                                                                                      |
|---------------------------|------------------------------------------------------------------------------------------------------|
| agreementNumber           | Agreement Number                                                                                     |
| customerId                | Identity of the end customer                                                                         |
| customerName              | Name of the end customer                                                                             |
| distributorId             | Distributor identity                                                                                 |
| distributorName           | Distributor name                                                                                     |
| earningAmount             | Earning Amount in the original transaction currency                                                  |
| earningAmountUSD          | Earning amount in USD                                                                                |
| earningDate               | Date of the earning                                                                                  |
| earningExchangeRate       | Exchange rate used to show the corresponding USD amount                                              |
| earningId                 | Unique identifier for each earning                                                                   |
| earningRate               | Incentives rate applied on transaction amount to generate an earning                                 |
| earningType               | Indicates whether it's fee, rebate, co-op, sell, and so on                                           |
| engagementId              | Engagement identifier                                                                                |
| engagementName            | Engagement name                                                                                      |
| estimatedPaymentMonth     | Month in which the earning is likely to be paid. Determined based on transaction date.               |
| exchangeRateDate          | Exchange rate date used to calculate EarningAmount USD                                               |
| invoiceNumber             | Invoice Number                                                                                       |
| lever                     | Indicates business rule for the earning                                                              |
| participantId             | The primary identity of the partner earning under the program                                        |
| participantIdType         | Partner identity                                                                                     |
| participantName           | Name of the earning partner                                                                          |
| partnerCountryCode        | Location/country/region of the earning partner                                                       |
| partNumber                | SKU or part number                                                                                   |
| paymentId                 | Payment identity as available in the bank payment                                                    |
| paymentStatus             | Payment status                                                                                       |
| programName               | Incentive program name                                                                               |
| resellerId                | Reseller identity                                                                                    |
| resellerName              | Reseller name                                                                                        |
| subscriptionEndDate       | Subscription end date                                                                                |
| subscriptionId            | Subscription identity                                                                                |
| subscriptionStartDate     | Subscription start date                                                                              |
| totalTransactionAmountUSD | Transaction amount in USD                                                                            |
| transactionCurrency       | Currency in which the original customer transaction occurred (which isn't partner location currency) |
| transactionMonth          | Month of transaction, consumption or usage                                                           |

### Export data file

The compressed download file is organized as below:

- If the total record count for the export request results in less than or equal to 50,000, a single file is produced.
- If the total record count for the export result set is greater than 50,000 and less than or equal to 500,000, the files will be split by each earning month, up to the maximum file size limit of 1 GB. In the event record count for a month is > 500,000, the export might result in multiple files, up to the maximum file size limit of 1 GB

:::image type="content" source="./media/announcements/2023-march/excel.png" alt-text="Screenshot of excel scenario.":::

## Next steps

- [Revenue summary](./revenue-summary.md)
- [Transaction history](./transaction-history.md)
- [Earnings and payment reconciliation FAQ](./reconciliation-faq.md)
