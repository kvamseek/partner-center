---
title: The co-sell connector for Dynamics 365 CRM Partner Center
description: Synchronize referrals in Partner Center with your co-sell connector for Dynamics 365 CRM. You can then co-sell with Microsoft from within your CRM system.
ms.topic: how-to
ms.service: partner-dashboard
ms.subservice: partnercenter-referrals
author: Saksham-PM
ms.author: sasolanki
ms.date: 08/24/2023
---

# Co-sell connector for Dynamics 365 CRM overview

**Appropriate roles**: Referrals admin | System admin or System customization engineer on the CRM system

Partner Center co-sell connectors enable your sellers to co-sell with Microsoft from within your customer relationship management (CRM) systems.

CRM systems don't have to be trained to use Partner Center to manage co-sell deals.

Partner Center co-sell connectors are based on Power Automate and uses Partner Center APIs.

You can use co-sell connectors to create a new co-sell referral to:

- Engage a Microsoft seller
- Accept or decline referrals
- Receive referrals from the Microsoft seller
- Modify deal data such as deal value and closing date

You can also receive any updates from the Microsoft sellers on these co-sell deals.

You can manage all of your referrals in the CRM of your choice rather than in Partner Center.

## Installation prerequisites

Before you install the solution, make sure you meet the following prerequisites.

| Articles   | Details   | Links   |
|--------------|--------------------|------|
| Microsoft AI Cloud Partner Program |You need a valid PartnerID (formerly MPN ID). | [Join the Partner Network](https://partner.microsoft.com/) |
| Co-sell ready|Your IP/Services solution must be co-sell ready. | [Sell with Microsoft](https://partner.microsoft.com/membership/sell-with-microsoft) |
| Partner Center account | The PartnerID (formerly MPN ID) associated with the Partner Center tenant must be same as the PartnerID associated with your co-sell solution. Verify that you can see your co-sell referrals in the Partner Center before you deploy the connectors. | [Manage your account](create-user-accounts-and-set-permissions.md) |
| Partner Center user roles | The employee who installs and uses the connectors must be a Referrals admin.|[Assign users roles and permissions](create-user-accounts-and-set-permissions.md) |
| Dynamics 365 CRM|The CRM user role is System admin or System customizer.|[Assign roles in Dynamics 365](/dynamics365/customerengagement/on-premises/customize/privileges-required-customization) |
| Power Automate flow account|Create a new production environment with a database for testing, staging, and production. If you have an existing production environment with a database, it can be reused. The user who installs the connector solution must have a Power Automate license and access to this environment. You can monitor progress and get more information in [Power Automate](https://flow.microsoft.com/) if the installation fails—select **See history** under **Solutions**. | [Create or manage environment](/power-platform/admin/create-environment#create-an-environment-with-a-database) |

## Install Partner Center referrals synchronization for Dynamics 365 (Power Automate solution)

To install Partner Center referrals synchronization for Dynamics 365 (Power Automate solution), use the following steps:

1. Go to [Power Automate](https://flow.microsoft.com) and select **Environments** in the upper-right corner to see the available CRM instances.

2. Select the appropriate CRM instance from the drop-down list.

3. Select **Solutions** on the left.

4. Select the **Open AppSource** link on the top menu.

   :::image type="content" source="media/cosellconnectors/open-appsource.png" lightbox="media/cosellconnectors/open-appsource.png" alt-text="Screenshot that shows Open AppSource.":::

5. Search for **Partner Center Referrals Connectors for Dynamics 365** in the pop-up screen.

6. Select the **Get it now** button and then select **Continue**.

7. A page appears where you can select the CRM (Dynamics 365) environment to install the application. Agree to the terms and conditions.

   You can monitor the progress and, if the installation fails, you can get more details in Power Automate by selecting **See history** under **Solutions**.

8. When installation is complete, go back to [Power Automate](https://flow.microsoft.com) and select **Solutions** on the left.

   **Partner Center Referrals Synchronization for Dynamics 365** is now available in the **Solutions** list.

9. Select **Partner Center Referrals Synchronization for Dynamics 365**.

    The following Power Automate flows and entities are available.

    :::image type="content" source="media/cosellconnectors/dynamics-available-crms.png" lightbox="media/cosellconnectors/dynamics-available-crms.png" alt-text="Screenshot that shows available CRMs.":::

## Test before you go live

Before you install, configure, and customize the Power Automate solution on the production environment, test the solution on a staging CRM instance.

To test the environment, use the following steps:

1. Install the Power Automate solution on a staging environment CRM instance.
2. Configure and customize the Power Automate solution in a staging environment.
3. Test the solution on a staging CRM instance.
4. After a successful test, import as a managed solution to the production instance.

## Configure the solution

To configure the solution, use the following steps:

1. After you've installed the solution in your CRM instance, go back to [Power Automate](https://flow.microsoft.com/).

2. From the **Environments** drop-down list in the upper-right corner, select the CRM instance where you installed the Power Automate solution.

3. You'll need to create connections that associate the three user accounts:

   - Partner Center user with Referrals admin credentials
   - Partner Center Events
   - CRM admin with the Power Automate flows in the solution

   a. Select **Connections** on the left, and select the **Partner Center Referrals** solution from the list.

   b. Create a connection by selecting **Create a connection**.

      :::image type="content" source="media/cosellconnectors/dynamics-1.png" lightbox="media/cosellconnectors/dynamics-1.png" alt-text="Screenshot that shows Create a connection.":::

   c. Search for **Partner Center Referrals (preview)** in the search bar in the upper-right corner.

   d. Create a connection for your Partner Center user with the credentials role of Referrals admin.

   e. Next, create a Partner Center Events connection for your Partner Center user with the Referrals admin credentials.

   f. Create a connection for Common Data Service (current environment) for the CRM administrator user.

   After you've added all the connections, you should see the following connections in your environment.

      :::image type="content" source="media/cosellconnectors/dynamics-2.png" lightbox="media/cosellconnectors/dynamics-2.png" alt-text="Screenshot that shows connections.":::

## Edit the connections

To edit the connections, use the following steps:

1. Return to the **Solutions** page and select **Default Solution**. Select **Connection Reference (preview)** by selecting **All**.

   :::image type="content" source="media/connection-reference-video.gif" lightbox="media/connection-reference-video.gif" alt-text="Screenshot that shows Editing the connections.":::

2. Edit each of the connections individually by selecting the ellipsis ("**...**") icon. Add the relevant connections.

   :::image type="content" source="media/cosellconnectors/dynamics-4.png" lightbox="media/cosellconnectors/dynamics-4.png" alt-text="Screenshot that shows connections listed.":::

3. Return to the **Solutions** page, select **Partner Center Referrals Synchronization for Dynamics 365**, and turn on the flow by selecting the ellipsis icon next to each flow in the following sequence.

   If you encounter any issues while you turn on the flow, see [Customization steps](connector-dynamics.md#customize-synchronization-steps) and [Troubleshooting steps](connectors-troubleshoot.md).

   **Turn on the flows in the following sequence:**

   a. Partner Center Webhook Registration (Insider Preview)

   b. [Customize] Create or Get Details from Dynamics 365 flow

   c. Create Co-sell Referral – Dynamics 365 to Partner Center (Insider Preview)

   d. Partner Center to Dynamics 365 - Helper (Insider Preview)

   e. Partner Center Microsoft Co-sell Referral Updates to Dynamics 365 (Insider Preview)

   f. Partner Center to Dynamics 365 (Insider Preview)

   g. Dynamics 365 to Partner Center (Insider Preview)

   h. Dynamics 365 Opportunity to Partner Center (Insider Preview)

   i. Dynamics 365 Microsoft Solutions to Partner Center (Insider Preview)

## Use webhook APIs to register for resource change events

You can use the Partner Center webhook APIs to register for resource change events. These change events are sent to your URL as HTTP posts.

To use webhook APIs to register for resource change events, use the following steps:

1. Select **Partner Center to Dynamics 365 (Insider Preview)**.

2. Select the **Edit** icon and then select **When a HTTP request is received**.

3. Select the **Copy** icon to copy the provided HTTP POST URL.

   :::image type="content" source="media/webhook-video.gif" lightbox="media/webhook-video.gif" alt-text="Screenshot that shows using webhooks to register resource changes.":::

4. Select the **Partner Center Webhook Registration (Insider Preview)** Power Automate flow, and then select **Run**.

5. Ensure that the **Run flow** window opens in the right pane, and select **Continue**.

6. Enter the following details:

   - **Http Trigger Endpoint**: This URL was copied from an earlier step.
   - **Events to Register**: Select all available events (**referral-created**, **referral-updated**, **related-referral-created**, and **related-referral-updated**).
   - **Overwrite existing trigger endpoints if present?**: Yes. Only one URL can be registered for a given webhook event.

7. Select **Run flow**, and then select **Done.**

The webhook can now listen to, create, and update events.

## Customize synchronization steps

CRM systems are highly customized, so you can customize the Power Automate solution based on your CRM setup. When co-sell referrals are synced between Partner Center and your CRM system, the fields that are synced on the Partner Center PC are listed in the [Custom field mapping guide](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RWxL6S).

Follow the field mapping guide, and if necessary make the appropriate changes in **[Customize] Create or Get Details from Dynamics 365 flow** or environment variables.

Don't update any other flows in the Power Automate solution because it can affect future solution upgrades.

**The following customizations are available:**

- **Display check mark in the opportunity name**:
  - By default, a check mark is displayed next to an opportunity name to indicate that synchronization between Partner Center and Dynamics 365 CRM is happening successfully. 
  - Similarly, a cross mark is displayed if synchronization fails.
  
  To avoid adding a check or cross mark in the opportunity name, set the current value of the **Display check mark in the opportunity name** environment variable to **No**.
- **Deal value**: By default, the deal value from Partner Center is synced to and from `estimatedvalue` in the CRM. If you have a different field in the CRM for the deal value to sync from:

  - Update the **Deal value** field name in the Dynamics 365 environment variable with the CRM's field name. Make sure that you provide the field's name, not its display name.
  - If you're using any calculated field for deal value, ensure that the value isn't 0 or empty while updating the opportunity from CRM.
  :::image type="content" source="media/referrals/calculated-field.png" alt-text="Screenshot shows the calculated field for deal value shouldn't be 0.":::

  - Edit **[Customize] Create or Get Details from Dynamics 365 flow**, and go to **Create or update opportunity** in CRM and update **Create a new opportunity** and **Update existing opportunity** actions to assign the **DealValue** value to the correct field in the CRM. Also, remove the **DealValue** assignment from the **Estimated Revenue** field.
  :::image type="content" source="media/referrals/deal-value.png" alt-text="Screenshot shows how to assign deal value.":::

- **Customer Account Country Code**: You must provide a two-letter ([ISO 3166](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)) country code  when you create a new referral. By default, the country code is synced to and from the account's **address1_country** field in the CRM. If you have a different field in the CRM for the country code to sync from:

  - For a nonlookup country code field in the account that contains a two-letter code, update the **Customer Account Country Code** field name in the Dynamics 365 environment variable with the CRM's field name. Make sure that you provide the field's name, not its display name. Edit **[Customize] Create or Get Details from Dynamics 365 flow**, and go to **Create or get customer account** in the CRM action to assign a **Country** value to the correct field in the CRM. Also, remove the **Country** value assignment from the **Address 1: Country/Region** field.

  - For a lookup-based country code field in the account, add a new custom field in the account. Auto-populate it with a two-letter ISO 3166 country code  based on the value selected in the lookup-based field, and vice versa. Follow the preceding steps for the nonlookup country code field to sync a new custom field from the CRM to and from Partner Center.

- **Opportunity fields**: If there are mandatory fields in **Opportunity** that need to be populated, edit **[Customize] Create or Get Details from Dynamics 365 flow** and go to **Create or update opportunity** in the CRM and update **Create a new opportunity action** to assign values to the mandatory fields based on your business requirements.
- **Lead fields**: If there are mandatory fields in **Lead** that need to be populated, edit **[Customize] Create or Get Details from Dynamics 365 flow** and go to **Create or update lead** in the CRM and update **Create a new lead action** to assign values to the mandatory fields based on your business requirements.
- **Customer account**: When a new referral is synced from Partner Center to the CRM, the Power Automate solution searches for an existing account in the CRM using the customer company name and postal code. If it doesn't find one, a new customer account is created in the CRM. To update the search criteria and new account creation details, edit **[Customize] Create or Get Details from Dynamics 365 flow** and go to **Create or get customer account** in the CRM and **Create customer account action**.

## Update environment variable

To update an environment variable value, use the following steps:

1. Go to the **Solutions** page, and select **Default Solution**. Select **Environment Variable** by selecting **All**.

2. Select the environment variable for the value that needs to be updated, and select **Edit** by using the ellipsis icon.

3. Update **Current Value** (don't update **Default Value**) by using the **New value** option and providing the value. The value must match the data type of the variable. For example, the Yes or No data type will accept either the Yes or No value.

   :::image type="content" source="media/cosellconnectors/environment-variables-video.gif" lightbox="media/cosellconnectors/environment-variables-video.gif" alt-text="Screenshot that shows Update environmental variables.":::

## End-to-end bidirectional co-sell referral synchronization

After you've installed, configured, and customized the Power Automate solution, you can test for co-sell referrals synchronization between Dynamics 365 and Partner Center.

### Prerequisites

To synchronize the referrals across Partner Center and Dynamics 365 CRM, the Power Automate solution clearly demarcates Microsoft-specific referral fields. This identification gives your seller teams the ability to decide which referrals they want to share with Microsoft for co-selling.

A set of custom fields and objects are added as part of the solution installation. A CRM admin user must create a separate CRM section with the **Opportunity** custom fields.

The following custom fields should be part of the CRM section:

- **Sync with Partner Center**: Whether to sync the opportunity with Partner Center. By default, the value of this field is **No** and needs to be explicitly set to **Yes** by your seller to share an opportunity with Microsoft. New referrals shared from Partner Center to CRM have this field value set to **Yes**.
- **Referral Identifier**: A read-only identifier field for the Partner Center referral.
- **Referral Link**: A read-only link to the referral in Partner Center.
- **How can Microsoft help?**: Help required from Microsoft for the referral. To create a co-sell referral, select the appropriate help required from Microsoft. A customer contact must be associated to the opportunity to create a co-sell referral. To create a non-co-sell referral, don't select this field. A non-co-sell referral can be converted to a co-sell referral anytime by selecting the appropriate help-required option.
- **Microsoft Partner Center Referral Visibility**: Select visibility for the Partner Center referral. By making it visible to Microsoft sellers, a non-co-sell referral might get converted to co-sell. When Microsoft help is required, the referral is visible to Microsoft sellers by default. After this field is marked as visible, it can't be reverted.
- **Microsoft CRM Identifier**: When a co-sell referral is created and accepted by Microsoft, this field will get populated with Microsoft's CRM identifier.
- **Products: Obsolete**: Don't use this field or add it to the CRM section. It's available for backward compatibility only. Use Partner Center solutions instead.
- **Audit**: A read-only audit trail for syncing with Partner Center referrals.
- **Microsoft Partner Center Solutions**: A custom object to associate co-sell ready solutions or Microsoft solutions with the opportunity. One or more solutions can be added or removed from the opportunity. It's mandatory to add at least one co-sell ready or Microsoft solution to the opportunity before you share it with Microsoft. To associate this object to the opportunity, update the **Opportunity** form in the CRM.

  Select the appropriate tab on the **Opportunity** form, and add a subgrid as shown here.

  :::image type="content" source="media/cosellconnectors/dynamics-6.png" lightbox="media/cosellconnectors/dynamics-6.png" alt-text="Screenshot that shows the Opportunity form.":::

  :::image type="content" source="media/cosellconnectors/dynamics-7.png" lightbox="media/cosellconnectors/dynamics-7.png" alt-text="Screenshot that shows Microsoft Solutions.":::

- After you add Microsoft solutions, you can pre-populate co-sell ready solution details so that your sellers don't have to add them. To add a new solution detail, go to the Microsoft Solution Details object in the CRM and select **Add Record** to add one entry or use **Excel upload** to add multiple entries.

  :::image type="content" source="media/cosellconnectors/dynamics-solution-1.png" lightbox="media/cosellconnectors/dynamics-solution-1.png" alt-text="Screenshot that shows New Microsoft Solution Details.":::

## Scenarios

### Referral synchronization when referral is created or updated in the CRM and synced in Partner Center

   1. Sign in to your Dynamics 365 CRM environment as a user who has visibility in the **Opportunity** section of the CRM.

   2. Ensure that the **Microsoft Partner Center** section is present when you create a new opportunity in the Dynamics 365 environment.

      :::image type="content" source="media/cosellconnectors/dynamics-solution-2.png" lightbox="media/cosellconnectors/dynamics-solution-2.png" alt-text="Screenshot that shows New opportunity.":::

   3. To synchronize this opportunity with Partner Center, ensure that you set the following fields in the card view:

      - **How can Microsoft help?**: To create a co-sell referral, select an appropriate help option.

         :::image type="content" source="media/cosellconnectors/dynamics-solution-3.png" lightbox="media/cosellconnectors/dynamics-solution-3.png" alt-text="Screenshot that shows how to get appropriate fields in card view.":::

      - **Customer contact**: To create a co-sell referral, add a customer contact to the opportunity.
      - **Sync With Partner Center**: Yes.
      - **Microsoft Solutions**: To share a referral with Microsoft, add a valid co-sell ready or Microsoft solution to the opportunity.

        :::image type="content" source="media/cosellconnectors/dynamics-solution-4.png" lightbox="media/cosellconnectors/dynamics-solution-4.png" alt-text="Screenshot that shows Solution ID.":::

   4. After the opportunity is created in Dynamics 365 with the **Sync With Partner Center** option set to **Yes**, wait 10 minutes. Then sign in to [Partner Center](https://partner.microsoft.com/dashboard/home). Your referrals will be synchronized with Dynamics 365 and **Referral Identifier**. **Referral Link** will be populated. If there's a failure, the **Audit** field is populated with error information.

      - Likewise, for an opportunity that had the **Sync With Partner Center** option set to Yes, if you update the opportunity in Dynamics 365 CRM, the changes will be synchronized in your Partner Center account.

      - Opportunities that are synchronized successfully with Partner Center will be identified with ✔icon in Dynamics 365.

### Referral synchronization when the referral is created or updated in Partner Center and synchronized in the Dynamics 365 environment

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Referrals**.
2. Create a new co-sell referral from Partner Center by selecting the **New deal** option.
3. Sign in to your Dynamics 365 CRM environment.
4. Go to **Open Opportunities**. The referral created in Partner Center is now synchronized in Dynamics 365 CRM.
5. When you select a synchronized referral, the card view details are populated.

## Next steps

- [Manage leads](manage-leads.md)
- [Manage co-sell opportunities](manage-co-sell-opportunities.md)
- [Partner Center webhooks](/partner-center/develop/partner-center-webhooks)
