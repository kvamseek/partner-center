---
title: Configure co-sell solution
description: The information you provide on the Co-sell with Microsoft tab for your solution is used by Microsoft sales teams to learn more about your solution when evaluating its fit for customer needs.
ms.service: partner-dashboard 
ms.subservice: partnercenter-referrals
ms.topic: how-to
author: Saksham-PM
ms.author: sasolanki
ms.date: 07/03/2023
---

# Configure a co-sell solution

**Appropriate roles**: Co-sell solution admin

This article describes how to configure a solution for co-sell with Microsoft.

Providing the information described in this article is optional, but it's required to achieve [Co-sell-ready and IP co-sell Eligibility status](/legal/marketplace/certification-policies#3000-requirements-for-co-sell-status).

The information that you provide is used by Microsoft sales teams to learn more about your solution when evaluating its fit for customer needs. The information isn't made available directly to customers.

The co-sell option is available for the following commercial marketplace offer types:

- Azure Application
- Azure Container
- Azure Virtual Machine
- Consulting service
- Dynamics 365 apps on Dataverse and Power Apps
- Dynamics 365 Operations Apps
- Dynamics 365 Business Central
- IoT Edge Module
- Managed Service
- Power BI App
- Software as a service (SaaS)

For more information about co-sell, see [Co-sell with Microsoft sellers and partners overview](./co-sell-overview.md) and [Co-sell with Microsoft](https://partner.microsoft.com/membership/co-sell-with-microsoft).

## Prerequisites

- You must have the *Co-sell solutions admin* role to view the **Co-sell solutions** page described here, and to configure co-sell solutions.

  - For more information about the roles and permissions related to referrals, see [Manage referrals](permissions-overview.md#manage-referrals).

  - To learn more about how to create accounts and assign roles, see [Create user accounts](create-user-accounts-and-set-permissions.md).

- You can only configure co-sell for a commercial marketplace offers if they're live at the marketplace.

## Go to the Co-sell > Solutions page

1. To get started configuring a co-sell solution, sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Referrals**.
2. Select **Co-sell**, then **Solutions**.

   :::image type="content" source="media/co-sell-configure/co-sell-solutions-nav-resized.png" alt-text="Screenshot of a dropdown menu with co-sell solutions selected in the Partner Center Referrals workspace." :::

   You must be a *Co-sell solutions admin* to view this page.

## Add a listing

Co-sell listings help the Microsoft sales teams market your solution to a wider audience.

You can configure co-sell for commercial marketplace offers only if they're live in the marketplace.

To add a listing, use the following steps:

1. To get started configuring a co-sell solution, sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Referrals**.
2. Select **Co-sell**, then **Solutions**.
3. On the solution pane that appears on the right side of the page, verify that you've opened the correct solution.
4. Select **Add/Edit** next to the **Listing** header on the solution pane to update the required listing information.

The **Listing** page appears.

:::image type="content" source="media/referrals/co-sell-listing-section.png" alt-text="Screenshot shows the co-sell listing section of the Co-sell Solutions page.":::

### Select Microsoft platforms

- On the **Listing** page, select one or more *Microsoft platforms* that your solution is built with, extends, or integrates with.

### Select a solution type

A *solution type* helps to define the scenarios that your solution is designed to address.

- From the **Select a solution type** list, select the solution type that best matches your solution. The following table describes the available solution types.

#### Solution types

| **Solution type**    | **Description**  |
| :------------------- | :-------------------|
| Device (hardware) | Solution that involves building or selling hardware from a device manufacturer |
| IP (application) | Apps or other copyrightable material (intellectual property, or *IP*) licensed for the customer's use (for example, a CRM program that can be licensed and installed on-premises) |
| Managed service | Hands-on expertise for a cloud-based project, usually on an ongoing basis (for example, providing a platform and tools for running an online database, with ongoing management provided by the managed service provider) |
| Service | Hands-on expertise for a one-time project, often delivered by consultants (for example, setting up a customer database for a customer, with the customer assuming responsibility for operating the database after delivery) |

### Select solution areas and sales plays

*Solution areas* help to further define your solution, which helps Microsoft sales teams to find and understand your solution's value proposition.

A *sales play* is a series of sales actions that focus efforts to produce a successful outcome.

To add solution areas and sales plays, use the following steps:

1. Select **+ Add solution area (5 Max)**.
2. Select a solution area from the dropdown list that appears.
3. Select at least one and up to five solution sales plays.

   To select multiple sales plays, use the `CTRL` key (on Windows) or `Command` key (on macOS).

4. To add another solution area, repeat steps one to three.

## Upload documents

You must provide collateral documents that contain details of your solution as part of configuring a co-sell solution. Microsoft sales teams use the information to evaluate whether your solution fits customer needs so they can recommend and sell your solution. The more information you provide, the more information Microsoft sales teams have to understand and promote your product.

> [!NOTE]
> A *solution one-pager* and *solution pitch deck* are required to attain co-sell ready status. They are also prerequisites for some solutions to be classified as Azure IP co-sell eligible.
> A *reference architecture diagram* that includes SaaS offers is also required for solutions to achieve Azure IP co-sell eligible status.
> The other documents described in the following table are optional but recommended.
- Recommended file types: .pdf, .ppt, .pptx, .doc, and .docx.
- Other supported file types: .xls, .xlsx, .jpg, .png, and .mp4.

   Templates for some documents are provided in the following table.

### Documents that support co-sell

| **Documents**    | **Description**  |
| :------------------- | :-------------------|
| Solution one-pager (required) | Drive awareness among potential customers with a professionally designed one-pager that showcases the value proposition of your solution.<br><br>You can use one of the relevant templates to provide a customer-ready description of your solution. (Templates download silently and automatically to your *Downloads* folder.)<br><ul><li> [Microsoft Azure one-pager template](https://aka.ms/Customer-One-Pager_MicrosoftAzure)</li><li>[Microsoft Dynamics 365 one-pager template](https://aka.ms/Customer-One-Pager_MicrosoftDynamics365)</li> <li>[Microsoft 365 one-pager template](https://aka.ms/Customer-One-Pager_MicrosoftOffice365) </li><li>[Windows 10 one-pager template](https://aka.ms/Customer-One-Pager_Windows)</li></ul> <br> Microsoft sales teams may share this information with customers to help determine if your solution may be a good fit, and to ensure that it's customer ready. |
| Solution pitch deck (required) | You can use the [Customer presentation template](https://aka.ms/GTMServices_CustomerPresentation) to create your pitch deck. This deck should reference the [Reference architecture diagram](reference-architecture-diagram.md). The purpose of this slide deck is to pitch your solution and its value proposition. After ensuring that your solution is customer-ready, Microsoft sales teams may share this presentation with customers to articulate the value that your company and Microsoft bring when deploying a joint solution. The presentation should cover what your solution does, how it can help customers, what industries the solution is relevant for, and how it compares with competing solutions. |
| Reference architecture diagram (required for SaaS offers only) | A diagram that represents your solution and its relationship with Microsoft cloud services. It may also demonstrate how your solution meets the technical requirements for Azure IP co-sell incentive status. [Learn more about the reference architecture diagram.](reference-architecture-diagram.md) |
| Customer case study (optional)| Use the [Case study template](https://aka.ms/GTM_Case_Study_Template) to create your customer case study. This information shows a potential customer how you and Microsoft have successfully deployed your solution in prior cases. |
| Verifiable customer wins (optional) | Provide specific examples of customer successes after your solution has been deployed. |
|Channel pitch deck (optional) | A slide deck with information that helps channel resellers learn more about your solution and get their sales teams ready to sell it. This deck typically includes an elevator pitch, information about target customers, questions to ask customers, talking points, and links to videos, documentation, and support information. |
| Other documents (optional) | You can upload up to five more documents or videos to help Microsoft sales teams and channel resellers learn more about your solution, organization, and how it's different from other solutions. |

> [!IMPORTANT]
> When creating any kind of collateral documents, make sure they're welcoming and inclusive for all. To learn more about how to create accessible collateral documents, see [Create accessible media](https://www.microsoft.com/accessibility/supplier-toolkit-resources).

- After you create your documents, drag them to the appropriate box under **Documents**, or select **Browse your files** to upload then from your computer.

:::image type="content" source="media/cosellconnectors/document-section.png" alt-text="Screenshot shows the document section of the Co-sell solution page.":::

## Link to your product landing page

- Under **Documents**, in the **Product landing page** box, enter the link to your product's website, where Microsoft sales teams and channel resellers can learn more about your solution and view the latest updates.

## Enter your contacts

A *contact* is required for each geography in which your solution is available.

Microsoft sales teams and channel resellers use your contact information to request more information from the appropriate resource in your organization. Contact information is available to all Microsoft sales teams.

If you choose to make your solution available in the CSP program, the contact information you enter is also available to channel resellers.

> [!IMPORTANT]
> It is critical that you keep your contact information up to date.

> [!NOTE]
> If you face error "Cannot upload file" while using correct format. It is because regional excel settings. Go to advance settings and uncheck the "Use system seperator as shown in image"
> :::image type="content" source="https://user-images.githubusercontent.com/102616797/203766910-c4459558-9860-4d26-be76-027ec6d87ae8.png" alt-text="image":::

Use the following steps to enter contact information:

1. Under **Contacts**, select **Download contacts template (.csv)** to download the template (as seen in the screenshot).

   :::image type="content" source="media/referrals/co-sell-contacts-section.png" alt-text=" Screenshot shows the Contacts section of the Co-sell > Solutions forms.":::
   If you have uploaded contacts previously, you can export your existing list of contacts for a solution and then make changes in that .csv file.

2. Open the .csv file in an application such as Microsoft Excel and then fill in each row with the following required information about each contact.

   - **Name**: The contact's name
   - **Email**: The contact's email address
   - **Job title**: The contact's job title
   - **Role**: Select a role from the following [Description of roles](#description-of-roles) table.

    > [!NOTE]
    > Special characters cannot be used in the **Name** and **Job title** fields.
    > 

3. Save and close the .csv file.

4. In Partner Center, select **Import contacts (.csv)**.

   > [!NOTE]
   > Importing a .csv file overwrites any existing contacts.

5. Select the .csv file and then select **Open**.

   A message appears stating that the contacts have been successfully imported.

### Description of roles

| **Role**    | **Description**  |
| :------------------- | :-------------------|
| Partner marketing | Markets your solution and collaborates on marketing efforts with Microsoft sales teams and channel resellers. Partner marketing is the main point of contact for marketing engagements and solution listing content, such as product descriptions, images, and videos. |
| Partner sales | Sells your solution and collaborates on sales with Microsoft sales teams and channel resellers.<br>Include at least one partner sales contact for each region in which you want your solution to be co-sell-ready.<br>One sales contact can cover multiple regions. |
| Partner technical sales | Supports technical architecture and deployment considerations during the sales cycle, the post-sales integration, and deployment periods. |
| Partner customer success manager | Supports customers post-deployment to help them get the most out of your solution and increase its usage within the customer's organization. |

- **Countries and regions** (required): Countries and regions should reflect each contact's territory.

   Microsoft sales teams and channel resellers use this information when requesting information or collaborating on sales within a country or region.

   When entering *Countries and regions* information about a contact in the template:
  - Use a two-letter [co-sell country and region code](./commercial-marketplace-co-sell-location-codes.md#country-and-region-codes).
  - If a contact covers more than one country or region, enter each of the two-letter codes, separated by a comma (for example, *US, CA, FR*).
  - If a contact covers all countries and regions, use the three-letter code *OOO*.

- **States/Provinces** (optional): When filling out the template, use the XX-XX format (for example, *US-WA*) as listed in the [states, provinces, and territories tables](./commercial-marketplace-co-sell-location-codes.md#state-and-province-codes).

## Save and submit for review

- After you complete all required fields on the **Co-sell > Solutions** page, select **Submit for review**.

   We'll review your solution to determine if it meets the requirements for co-sell status.

> [!NOTE]
> You no longer need to contact us to nominate your solution for co-sell.

## Next steps

- For information about republishing an offer, see [How to review and publish an offer to the commercial marketplace](/azure/marketplace/review-publish-offer).
- For information about commercial marketplace rewards and technical benefits, see [Your commercial marketplace benefits](/azure/marketplace/gtm-your-marketplace-benefits).

