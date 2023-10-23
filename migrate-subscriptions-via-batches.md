---
title: Migrate subscriptions to new commerce via batches
ms.topic: article
ms.date: 03/25/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Learn about migrating subscriptions to NCE in batches.
author: brentserbus
ms.author: brserbus
ms.custom: intro-migration
---

# Migrate subscriptions to new commerce experience using the batch migration tool (BAM)

You can efficiently migrate large numbers of subscriptions into the new commerce experience (NCE) using the batch migration tool (BAM).

(You can also migrate batches of subscriptions using the Migration API from [.NET SDK version 3.0.1](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter)).

> [!IMPORTANT]
> As of June 2023, the latest Partner Center .NET SDK release 3.4.0 is now archived. You can [download the SDK release from GitHub](https://github.com/microsoft/partner-center-sdk-for-dotNET), along with a [readme file](https://github.com/microsoft/partner-center-sdk-for-dotNET#readme) that contains useful information.
>
> Partners are encouraged to continue to use the [Partner Center REST APIs](./developer/partner-center-rest-api-reference.md).

The BAM tool:

- Supports high quality, repeatable, customizable batch migrations.
- Uses Excel to manage migration edits
- Requires no code
- Can be downloaded using [the sample code at GitHub](https://github.com/microsoft/Partner-Center-DotNet-Samples).

## Batch migration tool capabilities

Using the BAM tool, you can:

- Retrieve a list of all customers for a tenant.

- Retrieve customer legacy subscriptions in a .csv file.

- Prepare am exported .csv file for migration, and edit subscriptions (such as changes to seat count, term, and billing cycle) during migration.

- Upload an updated subscription .csv file into the tool, after which the tool executes the migration requests.

- Review the status of migration requests.

- Download all the NCE subscriptions for all of the list of customers in the input file.

## Prerequisites

The .NET 6.0 SDK is required to use the BAM tool.

## SDK and sample code

For details and resources regarding SDK releases, and sample app code that you can use to access the BAM tool:

- [Download SDK versions](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter)
- [Access sample code from GitHub](https://github.com/microsoft/Partner-Center-DotNet-Samples)

## Use the BAM tool

> [!NOTE]
> For  detailed instructions, see [Step-by-step flow of migrating a batch](https://github.com/microsoft/Partner-Center-DotNet-Samples/blob/master/nce-bulk-migration-tool/Readme.md#Step-by-step-flow-of-migrating-a-batch).

To load the workflow options for batch migration, use the following steps:

- [Run the BAM tool](https://github.com/microsoft/Partner-Center-DotNet-Samples/blob/master/nce-bulk-migration-tool/Readme.md#Step-by-step-flow-of-migrating-a-batch), and at the command prompt, enter **ncebulkmigration [app ID] {UPN ID]**.

Among the actions you can perform at this stage are:

- Export a list of customers.
- Export legacy subscriptions with migration eligibility.
- Upload subscriptions to be migrated.
- Export the migration status of batches that have already been uploaded for migration.
- Export a list of new commerce experience subscriptions.

:::image type="content" source="media/migrate-subscriptions-via-batches/bulk-migration-tool-menu.png" alt-text="Screenshot of the bulk migration tool command line menu." :::

### Account authentication

The BAM tool isn't configured for multitenant apps. When completing authentication, use the AppID of an app with single tenant configuration.

Microsoft is evaluating options for enabling the batch migration for multitenant applications.

### Export a list of customers

To export a list of customers, use the following steps:

- [Run the BAM tool](https://github.com/microsoft/Partner-Center-DotNet-Samples/blob/master/nce-bulk-migration-tool/Readme.md#Step-by-step-flow-of-migrating-a-batch) and enter command **1**.

The exported list of customers is saved to the *output* file of the BAM tool's folders.

View exported customers in the file *customers.csv*.

For each customer under a partner tenant ID, you can view:

- Customer tenant ID
- Customer domain
- Customer company name

### Access subscriptions for select customers

You can remove rows of customers from the downloaded *customers.csv* file whose subscriptions you don't want to export in the next file download. The customers who remain in the file are validated for migration eligibility during the next step in the BAM tool's work flow.

- Save the updated *customers.csv* file in the *input* folder so you can execute the next step of receiving subscriptions for the specified customers.
  - The *input* folder has two nested folders, *migrations* and *subscriptions*.
  - Don't place *customers.csv* in the nested folders. Keep it in the *input* folder.

To export subscriptions with migration eligibility, use the following steps:

- [Run the BAM tool](https://github.com/microsoft/Partner-Center-DotNet-Samples/blob/master/nce-bulk-migration-tool/Readme.md#Step-by-step-flow-of-migrating-a-batch) and enter command **2**.

  The tool runs and indicates that subscriptions are being validated for eligibility.
  After export is complete, the list of subscriptions for the specified customers is available in the *output folder* as *subscriptions.csv*, which provides a list of all legacy subscriptions (both active and suspended) for the customers previously specified.

The following fields can be viewed for each subscription:

- Partner tenant ID

- Indirect Reseller PartnerID

- Customer Name

- Customer Tenant ID

- Legacy Subscription ID

- Legacy Subscription Name

- Legacy Product Name

- Expiration Date

- Migration Eligible (True or False)

- Current Term

- Current Billing Plan

- Current Seat Count

- Start New Term (post migration in NCE)

- Term (post migration in NCE)

- Billing Plan (post migration in NCE)

- Seat Count (post migration in NCE)

- Add On (True or False)

- Base Subscription (if an add-on)

- Migration Ineligibility Reason (if subscription isn't eligible for migration)

### Determine which subscriptions will be migrated and how

Using the preceding fields, you can filter the exported list of subscriptions to determine which subscriptions you want to migrate to NCE in a batch. For example, you might filter to migrate a batch of subscriptions of a particular product type or a batch of subscriptions under a particular indirect reseller.

After you have filtered and selected subscriptions, delete any subscriptions that aren't selected for the batch from the .csv file. Doing so prevents unintended migrations.

We recommend exporting no more than 200 subscriptions per batch. (See [Migrate more than 200 subscriptions](#migrate-more-than-200-subscriptions) later in this article if you need to migrate more.)

The next step is to specify how subscriptions are to be migrated (for example, like-to-like, or with updated *start new term*, *billing frequency*, *term duration* or *seat count* attributes).

You can overwrite the following fields in rows for subscriptions you want to migrate:

- *Start New Term*

- *Term*

- *Billing Plan*

- *Seat Count*

The preceding fields represent the instructions or attributes that the NCE subscription will adhere to post-migration. The default values for these fields are the values of the legacy subscriptions being migrated. If no changes are made to a field, the corresponding NCE subscription has the same value as the legacy subscription it migrated from. For example, if a legacy subscription being migrated has a *Current Seat Count* of two, and no changes are made to the *Seat Count* field, the NCE subscription will have a seat count of two after migration.

To start a subscription with a new term in NCE, use the following step:

- Change the *Start New Term* flag from FALSE to TRUE.

  Don't change values outside of the following columns:
  
  - *Start New Term*
  - *Term*
  - *Billing Plan*
  - *Seat Count*

### Upload a batch for migration

After you've specified how a batch is to migrate (that is, after you have filtered subscriptions for migration and have updated NCE values, if desired), save the updated *subscriptions.csv* file in the *subscriptions* folder that is nested in the *input* folder. Each file saved in the *subscriptions* folder represents a batch to migrate.

After a file from the *subscriptions* folder has been processed for migration, the BAM tool moves that file into the nested *processed* folder, indicating that migration requests for that batch have been executed. You don't need to manually move files into the *processed* folder. Files in the *processed* folder aren't read by the BAM tool to execute migration because they've already been processed.

To upload migrations, use the following step:

- At the command prompt, [run the BAM tool](https://github.com/microsoft/Partner-Center-DotNet-Samples/blob/master/nce-bulk-migration-tool/Readme.md#Step-by-step-flow-of-migrating-a-batch) and select option **3**, *upload migrations*, after which:
  - The BAM tool reads batch files from the *subscriptions* folder and executes migration requests.
  - The console window indicates that migration requests are being processed.

    A file for each batch containing the migration IDs is exported and is available in the *migrations* folder that is nested in the *output* folder.
    - Exported files are labeled *[batchID].csv*.
    - *[batchID].csv* has the same fields as the input *subscriptions.csv* file, but with two more columns: *Batch ID* and *Migration ID*.
    - *Batch ID* is the same for every subscription in the file, indicating that these subscriptions belong to the same batch or set of migration requests that were processed together.
    - The *Batch ID* is also reflected in the name of the .csv file: *[batchID].csv*.

### Check migration status

If a migration is successful, its migration status is *Completed*.

If a migration is unsuccessful, its migration status is *Failed*, and you can view the reason for the failure.

A *Migration ID* is unique to each subscription that is migrated, so you can use *Migration ID* to track migration status.

An NCE *Subscription ID* is also populated upon successful migration.

To retrieve a refreshed status file for a batch, use the following step:

- Copy or save the exported *[batchID].csv* file (which is exported to the *migrations* folder nested in *output*) to the *migrations* folder (which is nested in the *input* folder).
  
  Doing so enables the tool to read which batches' status has been requested and prepare reports to export.

Status files aren't updated automatically. To retrieve updated statuses, a new request must be made each time.

To retrieve updated migration statuses, use the following step:

- [Run the BAM tool](https://github.com/microsoft/Partner-Center-DotNet-Samples/blob/master/nce-bulk-migration-tool/Readme.md#Step-by-step-flow-of-migrating-a-batch) and enter command **4**.
  
  The BAM tool runs and indicates that it's looking up migration status and that a file has been exported to the *migrationstatus* folder. The names of the exported migration status files represent the batch ID of subscriptions contained in the CSVs.

The *[batchID].csv* file exported to the *migrationstatus* folder provides updated statuses for migration requests that have been processed. If more than one batch is represented in the file, use the *Batch ID* column to filter to access statuses of requests in a particular batch.

### Export a list of new commerce experience subscriptions

To export NCE subscriptions, use the following step:

- [Run the BAM tool](https://github.com/microsoft/Partner-Center-DotNet-Samples/blob/master/nce-bulk-migration-tool/Readme.md#Step-by-step-flow-of-migrating-a-batch) and enter command **5**.
  
  The exported list is saved in the *output* folder. This step isn't required for migration, but you can use it to organize NCE subscriptions for different customers.

### Migrate more than 200 subscriptions

If you want to migrate more than 200 subscriptions (which is the maximum recommended batch size), you can upload multiple batches into the BAM tool.
You can organize folders by various fields to reduce the size of the files that you want to upload to be migrated. For example, you can organize subscriptions to be migrated by:

- Indirect reseller
- Product name
- Subscription name
- Other criteria
  
If a batch file that you've organized exceeds the maximum recommended size of 200 subscriptions, you can separate one .csv into multiple by effectively copying over subscriptions to new files to maintain the 200 subscription maximum of each batch. For example, if you want to migrate 425 subscriptions, you can be split them into three separate files (two files that contain 200 subscriptions and another that has 25).  

### Upload multiple files

You can upload multiple files into the BAM tool at once. The tool reads migration requests one batch file at a time and automatically begins reading in other batch files saved to the input directory (if multiple batches have been added).

The BAM tool reads batches one-by-one and calls the *Create Migration* API on each subscription individually.

You don't need to wait for one batch file to finish executing to add more batch files to the input directory.  

## Rate limits and throttling

To execute command **2** (retrieving subscriptions for customers and validating those subscriptions for migration), the BAM tool calls the *Validate Migration* API. The rate limit of the *Validate Migration* API is 450 calls per partner + customer combination in five minutes. With this rate limit and the current latency of the *Validate Migration* API, we don't anticipate that you'll experience throttling when you run the BAM tool. Also, the tool has concurrency limits to ensure that throttling doesn't occur.

However, if an issue does occur, you can keep track of which customer's subscriptions weren't pulled and validated. If a customer's subscriptions can't be pulled, or if there are issues while validating subscriptions, a separate .csv titled *failedCustomers.csv* appears in the output folder of the tool. You can retry pulling and validating subscriptions for those customers again.

> [!NOTE]
> The New commerce experiences for license-based services include many new capabilities and are available to all Cloud Solution Provider (CSPs). For more information, see [*New commerce experience for license-based services*](new-commerce-license-based.md).

## Next steps

- For  detailed instructions about using the BAM tool, see [Step-by-step flow of migrating a batch](https://github.com/microsoft/Partner-Center-DotNet-Samples/blob/master/nce-bulk-migration-tool/Readme.md#Step-by-step-flow-of-migrating-a-batch).
