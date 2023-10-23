---
title: Bulk upload and download co-sell opportunities via Excel/CSV files in Referrals
description: Learn how to download, create, or update Azure IP co-sell deal registrations using Excel (CSV) files in Partner Center
ms.topic: article
ms.service: partner-dashboard
ms.subservice: partnercenter-referrals
author: pragneMS
ms.author: pragne
ms.date: 08/24/2023
---

# Bulk operations for Azure IP co-sell deal registrations using comma-separated value (CSV) files

**Appropriate roles**: Referrals admin | Referrals user

Bulk operations for Azure IP co-sell deal registrations in Partner Center help your company download and upload IP co-sell deal registration data. Go to the **Co-sell opportunities** page to find the **upload** and **download** links on the command bar of the grid view. Users with both **Referrals admin** and **Referrals User** permissions can use this functionality.

> [!IMPORTANT]
> The create/update actions done through bulk upload are not reversible. Use caution when you are modifying or creating a large number of records. Only a subset of fields can be modified after creating a deal. **No actions are permitted after any deal reaches a terminal state, such as Approved, Passed, Failed, or Closed.**

## Download Azure IP co-sell deal registrations

The following information describes the download functionality:

- You can download a **maximum of 5,000 records** by selecting the download button and then Azure IP co-sell deal registration from the drop-down.
- The deals registration records that are downloaded are based on your access levels. Referral admins and Referral users may get different results based on their scope and inclusion as team members in the deals. Learn more about [referrals permissions](permissions-overview.md#manage-referrals).
- The download function considers the current tab in the co-sell opportunities page and the filters that have been applied.
- A CSV file with all the data based on the applied filters is generated.
- Downloading the records can take up to one minute.
- You don't have to wait for the download action to complete. Even if you go to other pages in Partner Center, the file is downloaded as soon as the download function is complete.
- You can reuse the downloaded file to modify the deal details and upload to update any records if they are in "Action Pending" state.

## Upload Azure IP co-sell deal registrations

- You can create or update a **maximum of 1,000 records** using the upload functionality.
- You can build the template from scratch by downloading the template from the upload page on Partner Center.
- You can also use the download functionality to download the existing records and update them.
- If the file has more than 1,000 records, it can't be processed.
- After the file is processed, a summary is displayed with the number of deal registration records that were created, updated, and not processed in the last processed file card.
- You  can download the details of the processed records, fix any errors, and upload the same file to create or update the records that failed in the previous run. **Remove all the successful records from the file before uploading the corrected records that failed in the previous run.**

> [!NOTE]
> You don't have to wait for processing to complete. The details of the last processed file are available for download when processing is complete. **It can take up to 30 minutes if you are uploading files with 1,000 records.**

> [!IMPORTANT]
> Read all the instructions carefully and check the format of each column from the following table before creating or updating deals using CSV files in Partner Center.

Not every field in the template is editable. There are fields that are [always read-only](#fields-that-are-always-read-only) and [fields that change to read-only after you change them to a specific value](#fields-that-become-read-only-after-you-first-submit-the-deal-registration-record).

### Fields that are always read-only

- Registration Date
- Registration Status Reason
- Action Required Date
- Passed Date
- Failed Date
- Approved Date
- Errors
- Microsoft team member

### Fields that become read-only after you first submit the deal registration record

- **Registration Type** becomes read-only after you submit the details for registration

### CSV file values, descriptions, and examples

Details of all the columns with their details and sample values are in the following table.

|**Column name**|**Required?**|**Description**|**Possible Values**|**Example**|
|-----|:-----|:---------|:---|:---|
Referral ID|Yes|Fill it in with the referral ID for which the Azure IP co-sell deal registration record is getting created or updated. |N/A|f7eaae47-0b84-4ac4-b4ea-5b2587d42cee
Registration Date|No|It's a system generated date based. Format is mm/dd/yyyy.|N/A|10/12/2022
Registration Type|No|This field is to identify the type of deal registration. Only AzureIPCosell is the supported value as of now.|AzureIPCoSell|AzureIPCoSell
Registration Status|No|The current state of the registration record.|•ReviewPending •ActionRequired •Approved •Passed •Failed •Closed|Approved
Registration Status Reason|No|The reason provided by the deal review team when the move a registration record to Passed or Failed state.|N/A|Passed after reviewing the contract document.
Is Marketplace Transacted|Yes|This information is required to understand whether the customer is purchasing the solution included in the referral from a Microsoft marketplace. These deals are automatically validated (like non-marketplace deals) if they meet the criteria.|Yes/No|Yes
Marketplace Transaction Date|Depends|This field is mandatory if the selection for the previous question (Is marketplace transaction?) is Yes. The information provided in this field helps Microsoft to automate transactions in the marketplace to a specific referral. You can then proceed to provide other details. Format is mm/dd/yyyy.|N/A|9/30/2022
Is Deployed on Azure|Yes|Registration is applicable only for solutions deployed on Azure. If the selection for this question is No, referral will be moved to closed state without Azure IP co-sell deal registration|Yes/No|Yes
Contract Value|Yes|The contract value as per the legal document signed with the customer. This value should include software and services but not hardware cost.|N/A|25000
Contract Currency|Yes|The currency in which the contract value is specified. Use three digit ISO code for the currency values|N/A|USD
Contract Term|Yes|If the contract between the partner and customer is perpetual, the total contract value entered in the registration form is spread over a six-year period to determine the annual contract value. Registration is allowed only if the annual contract value is greater than USD25,000.| Perpetual or Finite |Perpetual
Contract Sign Date|Yes|The date on which the contract has been signed with the customer and is mentioned in the contract with the customer. Format is mm/dd/yyyy.|N/A|10/12/2022
Contract Start Date|Yes|The date from which the customer started using the solution mentioned in the referral. Format is mm/dd/yyyy.|N/A|10/12/2022
Contract End Date|Depends|This field isn't required for perpetual contracts. It's required for non-perpetual contracts. For perpetual contracts, the end date is deemed to be six years from the contract start date for annual contract value calculations. Format is mm/dd/yyyy.|N/A|10/12/2022
Solution Value|Yes|Total contract value, less any non-recurring implementation fee. If renewing, increase the solution value by the amount for the renewal period, and extend the end date.|N/A|12354
Solution Currency|Yes|The currency in which the contract value is specified. Use three digit ISO code for the currency values|[List of ISO currency codes](https://www.iso.org/iso-4217-currency-codes.html) [List of ISO 3166 country codes - Wikipedia](https://en.wikipedia.org/wiki/List_of_ISO_3166_country_codes)|USD
Primary Deployment On|Yes|This field indicates if the solution in the referral is deployed on the customer or partner tenant.|Customer/Partner|Customer
Pricing Model|Yes|This information specifies whether the pricing model is pay-as-you-go.|PayAsYouGo/Other|PayAsYouGo
Review Pending Date|No|The date on which the deal registration record moved to the review pending state. Format is mm/dd/yyyy.|N/A|10/12/2022
Action Required Date|No|The date on which the deal registration record moved to the action required state. Format is mm/dd/yyyy.|N/A |10/12/2022
Passed Date|No|The date on which the deal registration record moved to the passed state. Format is mm/dd/yyyy.|N/A|10/12/2022
Failed Date|No|The date on which the deal registration record moved to the failed state. Format is mm/dd/yyyy.|N/A|10/12/2022
Approved Date|No|The date on which the deal registration record moved to the approved state. Format is mm/dd/yyyy.|N/A|10/12/2022
Errors|No|Errors if any related to the create/update operations regarding the Azure IP co-sell deal registration are included in this column. If there are multiple errors, all of them are listed separated by a semicolon|N/A|Required field Contract value is missing.

## Next steps

You can use these Partner Center co-sell connectors to co-sell with Microsoft from within your CRM systems.

- [Co-sell connector for Dynamics 365 CRM – Overview](connector-dynamics.md)
- [Co-sell connector for Salesforce CRM - overview](connector-salesforce.md)
