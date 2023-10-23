---
title: The co-sell connector for Salesforce CRM  Partner Center
ms.topic: how-to
ms.service: partner-dashboard
ms.subservice: partnercenter-referrals
description: Synchronize your referrals in Partner Center with your Salesforce CRM. Sellers can then co-sell with Microsoft from within your CRM systems.
author: Saksham-PM
ms.author: sasolanki
ms.date: 08/24/2023
---

# Co-sell connector for Salesforce CRM - overview

**Appropriate roles**: Referrals admin | System admin or system customization engineer on the CRM

Partner Center co-sell connector enables your sellers to co-sell with Microsoft from within your CRM systems. They don't have to be trained to use Partner Center to manage co-sell deals. Using the co-sell connectors, you can create a new co-sell referral to engage a Microsoft seller, receive referrals from the Microsoft seller, accept/decline referrals, modify deal data such as deal value, and closing date.  You can also receive any updates from the Microsoft sellers on these co-sell deals. You can do all of your referrals work within the CRM of your choice rather than in Partner Center.

The solution is based on Microsoft Power Automate Solution and uses Partner Center APIs.

## Before you install

|**Topics**|**Details**|**Links**|
|--------------|--------------------|------|
|Microsoft AI Cloud Partner Program |You need a valid PartnerID (formerly MPNID)| [Join the Partner Network](https://partner.microsoft.com/)|
|Co-sell ready|Your IP/Services solution must be Co-sell ready.|[Sell with Microsoft](https://partner.microsoft.com/membership/sell-with-microsoft)|
|Partner Center account|The PartnerID (formerly MPN ID) associated with the Partner Center tenant must be same as the PartnerID associated with your Co-sell solution. Verify that you can see your co-sell referrals in Partner Center before deploying the connectors.|[Manage your account](create-user-accounts-and-set-permissions.md)|
|Partner Center user roles|The employee who will install and use the connectors must be a Referrals admin|[Assign users roles and permissions](create-user-accounts-and-set-permissions.md)|
|Salesforce CRM|The CRM user role is System admin or System customizer|[Assign roles in Salesforce CRM](https://help.salesforce.com/articleView?id=assigning_users_to_roles.htm&type=5)|
|Power Automate Flow Account|Create a new production environment with a database for testing, staging, and production. If you have an existing production environment with a database, it can be reused. The user who's going to install the connector solution must have a Power Automate license and access to this environment. You can monitor the progress and get more information in [Power Automate](https://flow.microsoft.com/) if the installation fails. Select **See history** under **Solutions**.|[Create or manage environment](/power-platform/admin/create-environment#create-an-environment-with-a-database)|

## Installation of Salesforce package for Microsoft custom fields

To synchronize the referrals across Partner Center and Salesforce CRM, the Power Automate solution needs to clearly identify Microsoft-specific referral fields. This demarcation provides partner seller teams with the ability to decide which referrals they want to share with Microsoft for co-selling.

1. In Salesforce, activate **Notes** and add it to the opportunities related list. [Reference](https://help.salesforce.com/articleView?err=1&id=notes_admin_setup.htm&type=5)

1. Activate **Opportunity teams** by following the steps:
    - In Setup, use the **Quick Find** box to locate Opportunity Team Settings.
    - Define the settings as needed. [Reference](https://help.salesforce.com/articleView?id=sf.opp_team_manage.htm&type=5)

1. In Salesforce, install custom fields and objects using the [package installer](https://login.salesforce.com/packaging/installPackage.apexp?p0=04t2w000006WIwV). Use this installer to install the package into any company.

    > [!NOTE]
    > If you are installing into a sandbox, you must replace the initial portion of the URL with `http://test.salesforce.com`.

1. In Salesforce, add Microsoft Solutions to the **Opportunity** related list. Once added, select the **wrench** icon and update properties

## Best Practice: Test before you go live

Before you install, configure, and customize the Power Automate solution on the production environment, be sure to test the solution on a staging CRM instance.

- Install Microsoft Power Automate solution on a staging environment/CRM instance.

- Make a copy of the solution and run your configuration and Power Automate flow customizations on the staging environment.

- Test the solution on a staging/CRM instance.

- On success, import as a managed solution to the production instance.

## Install Partner Center Referrals Synchronization for Salesforce CRM

1. Go to [Power Automate](https://flow.microsoft.com) and select **Environments** on the right top corner. This will show you the available CRM instances.

1. Select the appropriate CRM instance from the drop-down list in the upper-right corner.

1. Select **Solutions** on the left navigation bar.

1. Select the **Open AppSource** link on the top menu.

   :::image type="content" source="media/cosellconnectors/open-appsource.png" lightbox="media/cosellconnectors/open-appsource.png" alt-text="Screenshot of Open AppSource.":::

1. Search for **Partner Center Referrals Connectors for Salesforce** in the pop-up screen.

   :::image type="content" source="media/salesforce/salesforce-get-it-now.png" lightbox="media/salesforce/salesforce-get-it-now.png" alt-text="Screenshot of Get It Now.":::

1. Select the **Get it now** button, and then select **Continue**.

1. In the next page, select the Salesforce CRM environment to install the application. Agree to the terms and conditions.

1. You're then directed to the **Manage your solutions** page.  Navigate to "Partner Center Referrals" by using the arrow buttons on the bottom of the page. **Installation scheduled** should appear next to Partner Center Referrals solution. Installation will take 10-15 minutes.

1. After the installation is complete, go back to [Power Automate](https://flow.microsoft.com) and select **Solutions** from left navigation area. Notice that **Partner Center Referrals Synchronization for Salesforce** is now available in the Solutions list.

1. Select **Partner Center Referrals Synchronization for Salesforce**. The following Power Automate flows and entities are available:

   :::image type="content" source="media/cosellconnectors/partner-center-referrals-synchronization.png" lightbox="media/cosellconnectors/partner-center-referrals-synchronization.png" alt-text="Screenshot of Salesforce flows.":::

## Configure the solution

1. After you've installed the solution in your CRM instance, go back to [Power Automate](https://flow.microsoft.com/).

1. From the **Environments** drop-down in the upper-right corner, select the CRM instance where you installed the Power Automate solution.

1. You'll need to create connections that associate the three user accounts:

   - Partner Center user with referrals admin credentials
   - Partner Center Events
   - CRM admin with the Power Automate flows in the solution

   1. Select **Connections** from the left navigation bar, and select the **Partner Center Referrals** solution from the list.

   1. Create a connection by selecting **Create a connection**.

        :::image type="content" source="media/cosellconnectors/dynamics-1.png" lightbox="media/cosellconnectors/dynamics-1.png" alt-text="Screenshot that shows Create a connection.":::

   1. Search for **Partner Center Referrals (preview)** in the search bar in the upper-right corner.

   1. Create a connection for your Partner Center user with the credentials role of Referrals admin.

   1. Next, create a Partner Center Events connection for your Partner Center user with the credentials of Referrals admin.

   1. Create a connection for Salesforce for the CRM administrator user.

   1. Create a connection for Microsoft Dataverse for the CRM administrator user.

   1. After you've added all the Connections, you should see the following connections in your environment:

        :::image type="content" source="media/cosellconnectors/salesforce-connections.png" lightbox="media/cosellconnectors/salesforce-connections.png" alt-text="Screenshot that shows how to observe connections.":::

### Edit the connections

1. Return to the **Solutions** page and select **Default Solution**. Select **Connection Reference (preview)** by clicking **All**.

   :::image type="content" source="media/connection-reference-video.gif" lightbox="media/connection-reference-video.gif" alt-text="Screenshot that shows Editing the connections.":::

1. Edit each of the Connections individually by selecting the ellipsis icon. Add the relevant connections.

   :::image type="content" source="media/cosellconnectors/salesforce15.png" lightbox="media/cosellconnectors/salesforce15.png" alt-text="Screenshot that shows how to edit connectors.":::

1. Turn on the flows in the following sequence:
   - Partner Center Webhook Registration (Insider Preview)
   - [Customize] Create or Get Details from Salesforce
   - Create Co-sell Referral-Salesforce to Partner Center (Insider Preview)
   - Partner Center Microsoft Co-sell Referral Updates to Salesforce (Insider Preview)
   - Partner Center to Salesforce (Insider Preview)
   - Salesforce to Partner Center (Insider Preview)
   - Salesforce Opportunity to Partner Center (Insider Preview)
   - Salesforce Microsoft Solutions to Partner Center (Insider Preview)

## Use Webhook APIs to register for resource change events

You can use the Partner Center webhook APIs to register for resource change events. These change events are sent to your URL as HTTP posts.

1. Select **Partner Center to Salesforce CRM (Insider Preview)**.

1. Select the **Edit icon** and select **When an HTTP request is received**.

1. Select the **Copy** icon to copy the provided **HTTP POST URL**.

   :::image type="content" source="media/salesforce/copy-url.png" lightbox="media/salesforce/copy-url.png" alt-text="Screenshot that shows how to copy the URL.":::

1. Select the **Partner Center Webhook Registration (Insider Preview)** Power Automate flow, and then select **Run**.

1. Ensure that the **Run flow** window opens in the right pane, and select **Continue**.

1. Enter the following details:

   - **Http Trigger Endpoint**: This URL was copied from an earlier step.
   - **Events to Register**: Select all available events (**referral-created**, **referral-updated**, **related-referral-created**, and **related-referral-updated**).
   - **Overwrite existing trigger endpoints if present?**: Yes. Only one URL can be registered for a given webhook event.

1. Select **Run flow**, and then select **Done**.

The webhook can now listen to, create, and update events.

## Customize synchronization steps

CRM systems are highly customized, and you can customize the Power Automate solution based on your CRM setup. When co-sell referrals are synced between Partner Center and your CRM system, the fields that are synced on the Partner Center PC are listed in the [Custom field mapping guide](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RWxL6S).

Follow the field mapping guide, and if necessary, make appropriate changes in **[Customize] Create or Get Details from Salesforce** or environment variables. Don't update any other flows in the Power Automate solution because it can affect future solution upgrades.

The following customizations are available:

- **Display check mark in the opportunity name**: By default, a check mark will be displayed next to the opportunity name to indicate that synchronization between Partner Center and Salesforce CRM is happening successfully. Similarly, a cross mark will be displayed if synchronization fails. To avoid adding a check or cross mark in the opportunity name, set the current value of the **Display check mark in the opportunity name** environment variable to No.

- **Stage name**:

  - **Active stage name**: This is the stage in an opportunity's sales pipeline in Salesforce.  It represents an active stage and is equivalent to a referral in accepted state in Partner Center. This can be the next stage in the sales pipeline after the on-hold stage. Moving Opportunity's sales stage out of the on-hold stage into active stage will accept the referral in Partner Center and changes will start synchronizing.

  - **On-hold stage name**: Name of the stage in an opportunity's sales pipeline in Salesforce. It represents an on-hold stage. New co-sell referrals shared from Microsoft that are not yet accepted will be set to this stage in Salesforce. Any changes made in an opportunity while it is on-hold stage will not synchronize to Partner Center. Moving Opportunity's sales stage out of this on-hold stage will accept the referral in Partner Center and changes will start synchronizing.

- **Customer Account Country Code**: It is mandatory to provide a two-letter country code ([ISO 3166](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)) when you create a new referral. By default, the country code will be synced to and from the account's **BillingCountry** field in Salesforce. If you have a different field in Salesforce for the country code to sync from:

  - For a nonlookup country code field in the account that contains a two-letter code:

    - Update the **Customer Account Country Code** field name in the Salesforce environment variable with the CRM's field name. Make sure that you provide the field's name, not its display name.

    - Edit **[Customize] Create or Get Details from Salesforce**, and go to **Create or get customer account in CRM** action to assign a **Country** value to the correct field in the CRM. Also, remove the **Country** value assignment from the **BillingCountry**.

  - For a lookup-based country code field in the account:

    - Add a new custom field in the account, and auto-populate it with a two-letter country code (ISO 3166) based on the value selected in the lookup-based field and vice versa.

    - Follow the preceding steps for the nonlookup country code field to sync a new custom field from the CRM to and from Partner Center.

- **Deal value**: By default, the deal value from Partner Center will be synchronized to and from **Amount** in the CRM. If you have a different field in the CRM for the deal value to synchronize from:

  - Update the **Deal value** field name in the Salesforce environment variable's Current Value with the CRM's field name. Make sure that you provide the field's name, not its display name.
  - Note that if you are using any calculated field for deal value make sure that the value should not be 0 or empty while updating the opportunity from CRM.
  :::image type="content" source="media/referrals/calculated-field.png" alt-text="Screenshot shows the calculated field for deal value should not be 0.":::

  - Edit **[Customize] Create or Get Details from Salesforce** and go to **Create or update opportunity** in CRM and update both **Create a new opportunity** and **Update existing opportunity** actions to assign the **DealValue** to the correct field in Salesforce.  
  :::image type="content" source="media/referrals/deal-value.png" alt-text="Screenshot shows how to assign deal value.":::

- **Deal value currency code**: Name of the deal value currency code field in Salesforce. This field API name will be used to get Opportunity's deal value currency code when creating or updating referral in Microsoft Partner Center. If deal value currency code field is different than default field **CurrencyIsoCode**, update the current value of this environment variable.

  - Update the **Deal value currency** field name in the Salesforce environment variable with the CRM's field name. Make sure that you provide the field's name, not its display name.

  - Edit **[Customize] Create or Get Details from Salesforce** and go to **Create or update opportunity** in CRM and update both **Create a new opportunity** and **Update existing opportunity** actions to assign the **DealValueCurrency** to the correct field in Salesforce.

- **Sync Co-sell opportunity**: If set to **yes**, only co-sell and pipeline sharing opportunities will be synchronized from Partner Center to Salesforce. If set to **no**, leads, co-sell, and pipeline sharing opportunities will be synchronized from Partner Center to Salesforce. This variable does not have any impact on the opportunities synchronized from Salesforce to Partner Center.

## Update environment variable

To update an environment variable value:

1. Go to the **Solutions** page, and select **Default Solution**. Select **Environment Variable** by selecting **All**.

1. Select the environment variable for the value that needs to be updated, and select **Edit** by using the ellipsis icon.

1. Update **Current Value** (don't update **Default Value**) by using the **New value** option and providing the value. The value must match the data type of the variable. For example, the Yes or No data type will accept either the Yes or No value.

   :::image type="content" source="media/cosellconnectors/environment-variables-video.gif" lightbox="media/cosellconnectors/environment-variables-video.gif" alt-text="Screenshot that shows Update environmental variables.":::

## End-to-end bi-directional co-sell referral synchronization

After you've installed, configured, and customized the Power Automate solution, you can test for Co-sell referrals synchronization between Salesforce CRM and Partner Center.

### Prerequisites

To synchronize the referrals across Partner Center and Salesforce CRM, the Power Automate solution needs to clearly demarcate Microsoft-specific referral fields. This identification provides your seller teams with the ability to decide which referrals they want to share with Microsoft for co-selling.

A set of custom fields is available as part of Partner Center Referrals Synchronization for Salesforce CRM solution **Opportunity** entity. A CRM admin user will need to create a separate CRM section with the **Opportunity** custom fields.

The following custom fields should be part of the CRM section:

- **Sync with Partner Center**: Whether to sync the opportunity with Partner Center. By default, the value of this field is No and needs to be explicitly set to Yes by your seller to share an opportunity with Microsoft. New referrals shared from Partner Center to CRM will have this field value set to Yes.

- **Referral Identifier**: A read-only identifier field for Microsoft Partner Center referral.

- **Referral Link**: A read-only link to the referral in Microsoft Partner Center.

- **How can Microsoft help**: Help required from Microsoft for the referral. To create a co-sell referral, select the appropriate help required from Microsoft. A customer contact must be associated to the opportunity to create a co-sell referral. To create a non-co-sell referral, don't select this field. A non-co-sell referral can be converted to a co-sell referral anytime by selecting the appropriate help-required option.

- **Microsoft Partner Center Referral Visibility**: Select visibility for the Partner Center referral. By making it visible to Microsoft sellers, a non-co-sell referral might get converted to co-sell. When Microsoft help is required, the referral is visible to Microsoft sellers by default. After this field is marked as visible, it can't be reverted.

- **Microsoft CRM Identifier**: When a co-sell referral is created and accepted by Microsoft, this field will get populated with Microsoft's CRM identifier.

- **Microsoft Partner Center Solutions**: A custom object to associate co-sell ready solutions or Microsoft solutions with the opportunity. One or more solutions can be added or removed from the opportunity. It's mandatory to add at least one co-sell ready or Microsoft solution to the opportunity before you share it with Microsoft. To associate this object to the opportunity, update the **Opportunity** form in the CRM.

- **Audit**: A read-only audit trail for syncing with Partner Center referrals

### Scenarios

#### Referral synchronization when referral is created or updated in CRM and synced

1. Sign in to your Salesforce CRM environment with user who has visibility in the **Opportunity** section of the CRM.
2. Ensure that the section, **Microsoft Partner Center** is present when you create a **New Opportunity** in Salesforce CRM environment.
3. Opportunities that are synchronized successfully with Partner Center will be identified with ✔ icon in Salesforce CRM.

   :::image type="content" source="media/salesforce/salesforce-environment.png" lightbox="media/salesforce/salesforce-environment.png" alt-text="Screenshot of the Salesforce environment.":::

4. To synchronize this opportunity with Microsoft Partner Center, ensure that you set the following fields in the card view:

   - **How can Microsoft help?**: To create a co-sell referral, select an appropriate help option.

     :::image type="content" source="media/salesforce/salesforce-help-option.png" lightbox="media/salesforce/salesforce-help-option.png" alt-text="Screenshot that shows how to get appropriate fields in card view.":::

   - **Sync with Partner Center**: Yes
   - **Customer contact**: To create a co-sell referral, add a customer contact to the opportunity.
   - **Microsoft Solutions**: To share a referral with Microsoft, add a valid co-sell ready or Microsoft solution to the opportunity.

5. After you have set the opportunity **Sync with Partner Center** option to **Yes**, wait for 10 minutes, sign in to your Partner Center account. Your referrals will be synchronized with Salesforce CRM, and Referral Link will get populated. If there's a failure, the Audit field will be populated with error information.

6. Similarly, when the **Sync with Partner Center** option is set to **Yes**, if you update the opportunity in Salesforce CRM, the changes will synchronize with your Partner Center account.

#### Referral Synchronization when referral is created or updated in Microsoft Partner Center and synchronized in Salesforce CRM environment:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Referrals**.
2. Create a new Co-sell referral from Partner Center by clicking "New deal" option.
3. Sign in to your Salesforce CRM environment.
4. Navigate to **Open Opportunities**. The referral created in Microsoft Partner Center is now synchronized in Salesforce CRM.
5. When you select a synchronized referral, the card view details are populated.

   :::image type="content" source="media/salesforce/salesforce-casino.png" lightbox="media/salesforce/salesforce-casino.png" alt-text="Screenshot of the Salesforce opportunity page.":::

> [!NOTE]
> For assistance with your Co-sell referral connector deployment, you can engage a Partner Technical Consultant. They can provide deployment assistance and best practices for a successful implementation.
>
> For more information, see [How to Submit a technical presales and deployment services request](technical-benefits.md)

## Next steps

- [Manage leads](manage-leads.md)
- [Manage co-sell opportunities](manage-co-sell-opportunities.md)
- [Partner Center webhooks](/partner-center/develop/partner-center-webhooks)
