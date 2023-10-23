---
title: Bulk download and upload co-sell opportunities via Excel/CSV files in Referrals
description: Learn how to download, create, or update co-sell opportunities using Excel (CSV) files in Partner Center
ms.topic: article
ms.service: partner-dashboard
ms.subservice: partnercenter-referrals
author: Saksham-PM
ms.author: sasolanki
ms.date: 08/24/2023
---

# Bulk operations for Co-sell opportunities using comma-separated value (CSV) files

**Appropriate roles**: Referrals admin | Referrals user

> [!NOTE]
> Addition of new column in CSV, column name is Marketplace Purchase Intent which is a required filed for referral creation. Accepted values are "Yes", "No" or "Have not decided". The introduction of this column is for capturing customer's interest to transact the deal on Microsoft Azure marketplace.

Bulk operations in Partner Center help your company download and upload co-sell opportunities data.

New functionalities like **Account matching** and **Referral creation** can also be performed by bulk operations.

Go to the **co-sell opportunities** page to find the **Upload** and **Download** links on the top right of the page title banner.

For the new Partner Center view, toggle **Grid View** button and **Upload** and **Download** links will move to left side.

> [!IMPORTANT]
> Create and update actions done through bulk upload are not reversible. Use caution when you create or modify a large number of records.
>
> Only a subset of fields can be modified after creating a deal.
>
> **No actions are permitted after any deal reaches a terminal state, such as Declined, Expired, Won, or Lost.**

> [!NOTE]
> We have added **Customer account search** in upload bulk operation. To learn more, see the [Upload co-sell opportunities](#upload-co-sell-opportunities) section that follows.

## Prerequisites

You must have **Referrals admin** or **Referrals user** permissions to use this functionality.

## Download co-sell opportunities

The following information describes the download functionality:

- You can download a **maximum of 5,000 records** by selecting the **Download** button.
- The deals that are downloaded are based on your access levels. Referral admins and Referral users might get different results based on their scope and inclusion as team members in the deals. To learn more, see [referrals permissions](permissions-overview.md#manage-referrals).
- The download function takes into account the current tab in the co-sell opportunities page and the filters that have been applied.
- A CSV file with all the data based on the applied filters is generated.
- Downloading the records can take up to one minute.
- You don't have to wait for the download action to complete. Even if you go to other pages in Partner Center, the file is downloaded as soon as the download function is complete.
- You can reuse the downloaded file to modify the deal details and upload to update any records.

## Upload co-sell opportunities

> [!NOTE]
> We have introduced an additional step, **Review final account match**, before creating a co-sell opportunity (also known as Referral). This step is to avoid the manual account matching process and to enhance deal-sharing speed.

> [!IMPORTANT]
> Download the new template in Partner Center. Old templates don't work with the updated Co-sell opportunity creation flow.

### Co-sell opportunities (Referral) creation with customer account match

- You can create or update a **maximum of 1,000 records** using the upload functionality.
- You can build the template from scratch by downloading the template from the **Upload** page in Partner Center.
- You can also use the **Download** functionality to download the existing records and update them.
- If a file has more than 1,000 records, it can't be processed.
- After a file is processed, a summary is displayed with the number of **Account search review required**.
- Download the processed file and review the account match results. File holds all prefilled columns, **1 Final Account Matched** (subset of managed accounts) with High, Medium and Low confidence, and **2 managed, 2 unmanaged and 2 DUNS accounts** in file.
- If you're not satisfied with the **Final Account Match** result, copy the customer account, fulfilling your searching criteria, and paste under the **Final Account Matched** column from managed, unmanaged, or DUNS suggestions.
- Upload the file again after you've reviewed the account matches.
- After a file is processed, a summary is displayed with the number of referrals that were created, updated, and not processed in the last process file card.
- You can download the details of the processed records, fix any errors, and upload the same file to create or update the records that failed in the previous run. **Remove all the successful records from the file before uploading the corrected records that failed in the previous run.**
- To add more solutions, add extra columns next to Solution 1 and use the column name as Solution X, where X represents the number of the solution in the deal. For example, Solution 2, Solution 3.
- You can add up to 50 solutions to a deal.
- To add more team members, add extra columns next to Team member 1 and use the column name as Team member x, where "x" represents the number of the team member in the deal (for example, Team member 2, Team member 3).
- You can add up to 50 team members to a deal.

### Special Notes

- If you have details of customer(s) and want to find the corresponding managed/unmanaged account to proceed directly for referral creation, fill all mandatory columns, and directly proceed with upload.
- If you have the Managed/Unmanaged ID of customer(s), you can proceed directly with referral creation by entering ***"MicrosoftID"*** in the ***"Final account match"*** column in the template.
- The only acceptable format for a Microsoft ID is ***"MicrosoftID: Number-Alphanumeric"** (for example ***MicrosoftID: 6-ABCDEFG23XB***).

> [!NOTE]
> You don't have to wait for processing to complete. The details of the last processed file are available for download when processing is complete. **It can take up to 10 minutes if you are uploading files with 1,000 records.**

> [!IMPORTANT]
> Read all the instructions carefully and check the format of each column from the following table before creating or updating deals using CSV files in Partner Center.

Not every field in the template is editable. There are fields that:

- [Are always read-only](#fields-that-are-always-read-only)
- [Change to read-only after referral creation](#fields-that-become-read-only-after-you-create-the-referral)
- [Change to read-only after you change them to a specific value](#fields-that-become-read-only-after-you-first-share-them)

### Fields that are mandatory for account matching

- Customer name
- Customer city

### Newly introduced fields that are auto-populated

- Final account match
- Matched category
- Confidence
- Managed account 1, Managed account 2
- Unmanaged account 1, Unmanaged account 2
- DUNS account 1, DUNS account 2

### Fields that are always read-only

- Errors
- Engagement ID
- Referral ID
- Microsoft referral status
- Microsoft MSX ID
- Migrated PSC deal ID
- Microsoft team member

### Fields that become read-only after you create the referral

- Customer name
- Customer address line 1
- Customer address line 2
- Customer city
- Customer state
- Customer postal code
- Customer country/region
- Customer DUNS ID
- Consent to share customer/partner contact
- PartnerID (formerly MPNID)

### Fields that become read-only after you first share them

Become read-only after you submit the details for co-sell referral creation or upgrade:

- Customer contact first name
- Customer contact last name
- Customer contact phone number
- Customer contact email address

Become read-only after you mark them as Yes:

- Share with Microsoft sales team
- Microsoft help required?

Become read-only after you enter a number in the specified format:

- What specific help from Microsoft?

Becomes read-only after you submit the notes for co-sell referral creation or upgrade:

- Notes to Microsoft

### CSV file values, descriptions, and examples

Details of all the columns with their details and sample values are in the following table.

|**Column name**|**Required?**|**Description**|**Example**|
|-----|:-----|:---------|:---|
|Errors|No|Errors if any related to the create/update operations regarding the referrals are included in this column. If there are multiple errors, all of them are listed separated by a semicolon.|Required field Solution 1 missing|
|Engagement ID|Yes|The engagement ID is generated by Microsoft Partner Center referrals system. Not required for new referral creation. You can use the existing engagement ID if you're updating a record.|f7eaae47-0b84-4ac4-b4ea-5b2587d42cee|
|Referral ID|Yes|Referral ID is generated by Microsoft Partner Center referrals system. Not required for new referral creation. Enter the referral ID if you're updating an existing record.|ebacdkdc-0b84-4ac4-b4ea-5b2587d42cee|
|Deal Name|Yes|Friendly name for the deal for your reference.|UK spring deal|
|Customer Name|Yes|Name of the customer company. Use the legal name of the organization for quick matching on the Microsoft side.|Contoso Corporation|
|Customer Address Line 1|Yes|First line of customer company address. |One Contoso Way|
|Customer Address Line 2|No|Second line of customer company address.|NE 148 street|
|Customer City|Yes|City where the customer organization is located. |Redmond|
|Customer State|No|State where the customer organization is located.|Washington|
|Customer Postal code|No|Postal code of the region where the customer organization is located.|98052|
|Customer Country|Yes|Country/Region where the customer organization is located. Use the two-letter *Alpha-2 code* in this [list of country codes](https://en.wikipedia.org/wiki/List_of_ISO_3166_country_codes).|US|
|Customer D-U-N-S ID|No|Try to fetch the DUNS ID of the customer organization. Doing so helps with faster matching of the customer organization on the Microsoft side, which helps with faster seller assignment. You can get a DUNS ID free from the [D-U-N-S Number Lookup page](https://www.dnb.com/duns-number/lookup.html).|81466849|
|Customer Contact First Name|Depends|First name of the primary contact from the customer organization working on this deal. Required only if you need Microsoft help. |John|
|Customer Contact Last Name|Depends|Last name of the primary contact from the customer organization working on this deal. Required only if you need Microsoft help. |Customer|
|Customer Contact Phone number|Depends|Phone number of the primary contact from the customer organization working on this deal. Required only if you need Microsoft help. |9999999999|
|Customer Contact Email Address|Depends|Email address of the primary contact from the customer organization working on this deal. Required only if you need Microsoft help. |john.customer@contoso.com|
|Partner Referral Status|Yes|Status of the deal from your company's perspective. Required if you're trying to create or modify a referral. Use **New** if you're trying to create a new deal. Values that you can use are listed at [Referral resources](/partner/develop/referral-resources#referralstatus).|Active|
|Partner Referral Substatus|Yes|Exact status of the deal. Use **Accepted** if you're trying to create a new deal. It's also required if you're modifying an existing referral. Values that you can use are listed at [Referral resources](/partner/develop/referral-resources#referralsubstatus).|Accepted|
|Microsoft Referral Status|Depends|Status of the co-sell request that you sent to Microsoft seeking help. This field is a read-only. Any change made to this field while importing the data is ignored.| Pending|
|Declined/Lost/Error reason|Depends| You're required to provide this information only if you're changing the sub status of your field to Declined, Lost, or Error. You can ignore this column otherwise. <br/> **Enter a number based on the following options if you set the Partner Referral Substatus as "Declined" or "Lost":** <br/><br/> **1**- Project budget isn't adequate  <br/> **2**- Customer didn't respond  <br/> **3**- Customer chose another vendor  <br/> **4** - Customer requirement not met  <br/> **5** - Not a customer <br/> **6**- Proposed time line was too short <br/> **7** - Report as abuse, spam, or phishing <br/> **8** - Others <br/><br/> **Enter a number based on the following options if you set the Partner Referral Substatus as "Error"** <br/><br/>  **1**- Duplicate - created through bulk upload  <br/> **2**- Duplicate - created in Partner Center  <br/> **3**- Duplicate - sent by Microsoft  <br/> **4** - Connector data sync issues  <br/> **5** - Customer matching issues <br/> **6**- Solution issues - explain in notes <br/> **7** - Test referral <br/> **8** - Data error <br/> **9** - Others - explain in notes |6|
|Sales Stage|No|Indicates the detailed sales stage of the referral. To learn more about sales stages, see [Manage co-sell opportunities in Partner Center](./manage-co-sell-opportunities.md)|40|
|Estimated Deal Value|Yes|Value of the deal based on the initial conversations with the customer. This value can be changed until the deal reaches one of the terminal states, **"Won"** or **"Lost."**|12563|
|Currency|Yes|Currency in which the deal value is entered. You can find the currency codes [at the ISO 4217 Wikipedia page](https://en.wikipedia.org/wiki/ISO_4217).|USD|
|Estimated Close Date|Yes|Estimated close date of the deal, in MM/DD/YYYY format, based on the initial conversations with the customer. <br/> **The date should be in UTC timezone. All the dates displayed in Partner Center UI are based on localized timezones. There might be +/- one day difference in the Partner Center UI if you are looking at the referral for which you supplied the date in UTC timezone.**|1/30/2020|
|CRM ID|No|Identifier (if any) of this referral in your CRM system. This field is a freeform text entry field.|34234324-sdfsdf-345345-sfd|
|Marketing Campaign ID|No|ID of the marketing campaign that resulted in this referral. Typically used for ROI calculation|BingSummer2020|
|Notes|No|Detailed notes indicating the updates related to the referral|This is a sample note.|
|Microsoft help required?|Yes|Indicates whether you want Microsoft to help you making this co-sell request|Yes|
|What specific help from Microsoft?|Depends|One of the six different ways Microsoft can help you. This entry is applicable only if you choose "Yes" for the question "Microsoft help required? " <br/> **Enter a number based on the following options** <br/><br/> **1**- Workload - specific value proposition  <br/> **2**- Customer technical architecture  <br/> **3**- Proof of concept /Demo  <br/> **4**- Quotes and Licensing  <br/> **5**- Post - sales customer success  <br/> **6**- General or other|1|
|Share with Microsoft sales team|Yes|Indicates whether or not you want to share the details of the deal with Microsoft sales team. Applicable only if you choose "No" for the question "Microsoft help required? "|Yes|
|Notes to Microsoft|No|Any notes to Microsoft if you need help from Microsoft|Need help with a POC for Contoso customer|
|Consent to share Customer/Partner contact|Yes|Consent to share contact details for both the customer and your company employees who are working on the deal. **Deals won't be created or updated if you choose "No."** |Yes|
|CLA Number|Depends|CLA number isn't required when creating or updating an Internet of Things (IOT) deal. It becomes required when you move to the design win stage.||
|Device Category|No|List of all the Internet of Things (IOT) device categories. Select a category from the following options: <br> Arcade/Consumer Gaming Device <br> ATM <br> Automotive & Transportation Systems <br> Azure Sphere Board<br> Azure Sphere Component <br> Azure Sphere Guardian<br> Azure Sphere Module <br> Building Automation<br> Casino Gaming Device <br> Communication Devices<br> Consumer Internet Device <br> Consumer Wearable<br> Digital Picture Frame <br> Digital Signage <br> Gateway <br> HHT/Mobile<br> Industrial Automation Device<br> Industry Tablet(Non-POS) <br> Kiosk<br> Media Player<br> Media Device <br> Mobile POS <br> Navigation Device<br> Network Projector<br> Other<br> Other Banking Device<br> Other Consumer Electronic Device<br> Other Device<br> Other Enterprise Device<br>  Other Sensor/Node <br> Point of Sale Device<br> Printing Device <br> Security/Surveillance <br>  Server<br> Set-Top Box<br> Smart TV <br> Test and Measurement Device<br> Thin Client Device <br/>||
|Silicon Type|No|Enter the chipset model information by selecting an option from the following list: <br> AMD - A10 <br> AMD - A4 <br> AMD - A6 <br> AMD - A8 <br> AMD - E2 <br> AMD - FX 7500 <br> AMD - FX 7600P <br> AMD - FX 9370 <br> AMD - FX 9590 <br> AMD - G Series <br> AMD - Others <br> AMD - R Series <br> AMD - Rest of FX Models <br> Intel - Atom <br> Intel - Celeron - N1900 <br> Intel - Celeron - N2807 <br> Intel - Celeron - N2930 <br> Intel - Celeron - N3060 <br> Intel - Celeron - N3160 <br> Intel - Core i3 <br> Intel - Core i5 <br> Intel - Core i7 <br> Intel - Core M <br> Intel - Others <br> Intel - Pentium <br> Intel - Rest of Celeron <br> Intel - XEON <br> MediaTek MT3620 <br> NXP 8ULP-CS <br> Others <br/>||
|Azure Certified Device|No|Indicates whether Azure compatibility certification has been achieved for the device||
|Attach Services|No|Indicate whether Azure services are to be bundled with the IoT solution at deployment||
|Microsoft MSX ID|No|ID of a deal on the Microsoft MSX system, available for co-sell opportunities only||
|Migrated PSC Deal ID|No|PSC deal ID. Available only for a deal migrated from PSC to PC.||
|PartnerID (formerly MPN ID)|No|PartnerID of the organization for which the co-sell opportunities are being created||
|Marketplace Purchase Intent|Yes|Customer's intent to trasact over Microsoft azure marketplace.|Accepted values are Yes, No or Have not decided|
|Customer Domain Name|No| Domain name of the customer||
|Final Matched Customer Account|No (Auto-Populated)|Best customer match from our records|MicrosoftID: 11-1FG2G, AccountName: Microsoft, AccountAddress: PO BOX 80456|
|Managed Account 1 & 2|No (Auto-Populated)|Managed accounts match from our records|MicrosoftID: 12-1FG2G, AccountName: Microsoft, AccountAddress: PO BOX 80456|
|Unmanaged Account 1 & 2|No (Auto-Populated)|Unmanaged accounts match from our records|MicrosoftID: 13-1FG2G, AccountName: Microsoft, AccountAddress: PO BOX 80456|
|DUNS Account|No (Auto-Populated)|DUNS accounts from our records|DUNSID: 659410848, AccountName:JUNIOR, AccountAddress: 21 TOH GUAN ROAD EAST #07-06 TOH GUAN CENTRE|
|Solution 1|Yes|*Solution ID* (required)<br>*Currency* in which the deal value is entered [(currency codes list)](https://en.wikipedia.org/wiki/ISO_4217) (optional)<br>*Price* of the SKU (optional) <br> *Quantity* of the SKU (optional)  |SOL-1234-PQRS, USD, 10, 100|
|Team member 1|Yes|*First name*, *last name*, *mobile number*, and *email ID* of the respective team member.| Bob, Partner, 999999, Bob.partner@Contoso.com|
|Microsoft team member 1|No|*First name*, *last name*, *mobile number*, and *email ID* of the respective Microsoft team member working on the co-sell opportunity.| Sam, Seller, 999999, Sam.seller@Microsoft.com|

## Next steps

You can use these Partner Center Co-sell connectors to co-sell with Microsoft from within your CRM systems.

- [Co-sell connector for Dynamics 365 CRM – Overview](connector-dynamics.md)
- [Co-sell connector for Salesforce CRM - overview](connector-salesforce.md)
