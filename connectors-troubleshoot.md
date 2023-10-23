---
title: Troubleshoot co-sell referrals connectors
ms.topic: how-to
ms.service: partner-dashboard
ms.subservice: partnercenter-referrals
description: Learn answers to common questions about using co-sell connectors. Read this FAQ on how to troubleshoot co-sell connectors.
author: Saksham-PM
ms.author: sasolanki
ms.date: 08/24/2023
---

# Troubleshoot co-sell referrals connectors

**Applies to**: Dynamics 365 CRM | Salesforce CRM

**Appropriate roles**: Referrals admin | System admin or System customizer on the CRM

This article covers [co-sell referrals connectors](connector-salesforce.md) fundamentals and troubleshooting in three sections:

- [Fundamentals FAQ](#fundamentals-faq)
- [Configuration troubleshooting](#configuration-troubleshooting)
- [Run and maintenance troubleshooting](#run-and-maintenance-troubleshooting)

## Fundamentals FAQ

This section answers questions about the fundamentals of using co-sell referrals connectors, such as permissions, subscriptions, and setup.

##### Can I use a trial co-sell referrals connectors solution for my environment?

   Yes. You can download the connector solutions for free from [AppSource](https://appsource.microsoft.com/marketplace/apps?search=partner%20center%20referrals%20connector&page=1).

##### What role must I have to create sections in a CRM environment?

Users who are *System admins* or *System customizers* can apply changes for everyone.

All app users can personalize the system and share some of their customizations with others.

##### Do partner sellers need special roles to work on Partner Center?

Yes. Partner sellers must be assigned the *Referrals admin* role. For more information, see the [Permissions overview](create-user-accounts-and-set-permissions.md).

##### What fields should be set up first in my CRM environment?

- Make sure your *currency* setting is appropriate for your location and is in your CRM environment accurately.
- Your sales team should be listed in your CRM environment as CRM users.
  
  For more information, see [Dynamics](connector-dynamics.md) and [Salesforce](connector-salesforce.md).

##### What prerequisites are required for Power Automate environment creation?

To use the Power Automate environment, you need:

- A Power Automate license
- A minimum of 1 GB of storage

##### Do I need a Dynamics 365 subscription to use the Salesforce Connectors solution?

No. The Salesforce Connector solution that supports synchronizing with other CRM systems is of type *Dynamics Flow*. The solution doesn't require you to have a Dynamics 365 instance or a subscription.

When you install the Salesforce solution:

- A dropdown menu with the existing CDS environment in your company may appear. Select that existing CDS environment.
- If you get the error "We couldn't find a Dynamics 365 organization connected to signed-in user," create a new environment for connectors.

___

## Configuration troubleshooting

This section describes configuration issues that you might encounter and how to address them

##### I get the *WorkflowTriggerNotFound* error while activating flows in the Power Automate Platform

To correct a WorkflowTriggerNotFound error, use the following steps:

1. Delete the CDS connection and then recreate it.
2. Turn the child flow off and on.
3. Delete solution and reinstall it.

- Error example:

  `Error: Request to Azure Resource Manager failed with error: '{"error":{"code":"WorkflowTriggerNotFound","message":"The workflow 'e14d00f1-1fdf-4b1b-aaac-54a5064093d3' trigger 'manual' couldn't be found."}}'.`

##### I get a "Sign in" error while adding a Partner Center connector in Power Automate Platform

:::image type="content" source="media/cosellconnectors/failure.png" lightbox="media/cosellconnectors/failure.png" alt-text="Screenshot showing the error message requiring sign-in.":::

To fix the sign-in error, use the following steps:

1. Ensure that the user who is installing and using the connectors has the *Referrals admin* role.
2. Use your Partner Center credentials to sign in to the Power Automate environment.

##### I get a "Requiring updates" error while activating the Partner-Center-to-CRM flow in the Power Automate platform

To correct the "requiring updates" error, use the following step:

- Before you activate the Partner-Center-to-CRM flow, activate the following child flows:
  - Partner Center to CRM - Helper (Insider Preview)
  - Partner Center Microsoft Co-sell Referral Updates to CRM (Insider Preview)

- Error message:

   :::image type="content" source="media/cosellconnectors/powererror.png" lightbox="media/cosellconnectors/powererror.png" alt-text="Screenshot showing the error message requiring updates.":::

##### I can't add connections to the flow when I try to edit the flow

If you can't add connections to the flow when you try to edit the flow, use the following steps:

- Add connections to the flow while the flow is running, and add to each flow separately.

- If a dialog box to add connections doesn't open automatically while editing the flow, you can edit each of the steps and substeps of the flows individually:

  - Select each flow and edit it individually.
  - Expand all the steps in the flow.

  :::image type="content" source="media/cosellconnectors/flowsteps.png" lightbox="media/cosellconnectors/flowsteps.png" alt-text="Screenshot showing steps that need connections.":::

  - Select the steps where you see a warning icon asking to associate connections, and add connections.

  :::image type="content" source="media/cosellconnectors/editflow.png" lightbox="media/cosellconnectors/editflow.png" alt-text="Screenshot showing the step-by-step edit flow.":::

##### Flows of the co-sell referrals connectors solution don't turn on

If flows of the co-sell referrals connectors solution don't turn on, use the following steps:

- In Power Automate, turn on the flows in the following order and update them to use the correct connections:

  **Salesforce:**
  - Partner Center Webhook Registration (Insider Preview).
  - [Customize] Create or Get Details from Salesforce.
  - Create Co-sell Referral-Salesforce to Partner Center (Insider Preview)
  - Partner Center Microsoft Co-sell Referral Updates to Salesforce (Insider Preview)
  - Partner Center to Salesforce (Insider Preview)
  - Salesforce to Partner Center (Insider Preview)
  - Salesforce Opportunity to Partner Center (Insider Preview)
  - Salesforce Microsoft Solutions to Partner Center (Insider Preview)

  **Dynamics CRM:**
  - Partner Center Webhook Registration (Insider Preview)
  - [Customize] Create or Get Details from Dynamics 365 flow.
  - Create Co-sell Referral – Dynamics 365 to Partner Center (Insider Preview)
  - Partner Center to Dynamics 365 - Helper (Insider Preview)
  - Partner Center Microsoft Co-sell Referral Updates to Dynamics 365 (Insider Preview)
  - Partner Center to Dynamics 365 (Insider Preview)
  - Dynamics 365 to Partner Center (Insider Preview)
  - Dynamics 365 Opportunity to Partner Center (Insider Preview)
  - Dynamics 365 Microsoft Solutions to Partner Center (Insider Preview)

  For each of flows, select the **Run only users** option. Select **Use this connection** instead of **Provided by run-only user**.
  
 :::image type="content" source="media/cosellconnectors/run-permissions.png" alt-text="Screenshot showing the Manage run-only permissions screen.":::

- Activate the following flows:
  - [Customize] Create or Get Details from Salesforce.
  - Partner Center Microsoft Co-sell Referral Updates to Salesforce (Insider Preview)
  - Salesforce to Partner Center (Insider Preview)

- Activate all the remaining flows.

- At the flow **Partner Center Webhook Registration (Insider Preview)**, select **Run**. Copy the **HTTP Post URL** from the first action in **Partner Center to Salesforce (Insider Preview)** flow and update in **Http Trigger Endpoint** of **Partner Center Webhook Registration (Insider Preview)** flow run.
  
:::image type="content" source="media/cosellconnectors/http-connector.png" alt-text="Screenshot showing the HTTP connector.":::

- Select all four options under **Events to register**, and select **Yes** for Overwrite.
  
:::image type="content" source="media/cosellconnectors/http-trigger.png" alt-text="Screenshot showing the HTTP trigger.":::

___

## Run and maintenance troubleshooting

##### Power Automate flow execution failures troubleshooting

- To ensure that your Power Automate flows run as you expect, see [Fix flow failures](/power-automate/fix-flow-failures).

##### Referrals aren't synchronized properly in Partner Center or the CRM environment

To determine the status of the referral synchronization, use the following steps:

1. Select **Audit**.
2. Ensure that the following conditions are met:

   - Solution ID is provided as part of the opportunity.
   - Two-letter country code is required.
   - When help from Microsoft is selected for the opportunity, customer contact information is required.
  :::image type="content" source="media/cosellconnectors/synch.png" lightbox="media/cosellconnectors/synch.png" alt-text="Screenshot showing how to synchronize referrals.":::

##### Ensuring that a referral synchronizes bidirectionally

To ensure that a referral will synchronize bidirectionally, use the following steps:

- Ensure that the `Referral ID` field has been updated in the CRM or Partner Center.
- Ensure that users will see the success synchronize/update message in the audit field.
  - In there's a synchronization failure, the audit field gets updated with a failure message detail.
:::image type="content" source="media/cosellconnectors/enablesynch.png" lightbox="media/cosellconnectors/enablesynch.png" alt-text="Screenshot showing the confirmation that you've enabled sync.":::

##### A connector gets disconnected and I miss a referral synchronization

**You can try some of the following things:**

- Check whether the username or password has expired for the Partner Center user with Referral admin roles.
- Go to the unsynchronized opportunity, make a minor update, and check to see if the referral has synchronized.
- If the flows have run and failed, select the flow and resubmit the run that has failed.

##### I get an "Access denied" error

If you get an "Access denied" error, use the following steps:

- Make sure the appropriate roles exist:
  - *Referral administrator* role for Partner Center seller
  - *System Administrator* or *System customizer* role on your CRM instance
- Ensure that the Power Automate flow account user logs into **[Microsoft flow](<https://flow.microsoft.com>)** at least once beforehand.

##### A customer account country code is missing while creating a co-sell opportunity

- Make sure you provide the ISO two-letter country code to the customer account in the CRM (for example, "US" for United States).

##### I get a "Solution ID is required" error while creating a co-sell opportunity

- A solution is required to sync a co-sell opportunity. Make sure that your CRM has valid Microsoft co-sell-ready solutions added.

##### Co-sell opportunities are created in Partner Center, and they aren't synchronized to the CRM even though there are no flow errors

**Follow these steps:**

  1. After you've created a new co-sell deal in Partner Center, check whether Partner-Center-to-Dynamics-365 flow is invoked. (It might get invoked multiple times).
  2. If the flow gets invoked, check all invoked flows and identify the flow run that would update the CRM.
  
     You can follow the actions and verify whether it updated the CRM or encountered a problem.
  3. Check **New deal** in Partner Center to see if that gets populated with CRM ID.
  4. Make sure that the deal wasn't accidentally closed as **Won** or **Lost** in Partner Center.

##### Leads aren't synchronizing from Partner Center to Salesforce CRM or Dynamics CRM

To synchronize leads from Partner Center to Salesforce CRM or Dynamics CRM, use the following steps:

1. Go to connector solution and run the flow **Partner Center Webhook Registration (Insider Preview)** to reregister the webhook again, and make sure users select **Overwrite existing endpoints** = **Yes**.

2. After successful registration, check the synchronization again.

   :::image type="content" source="media/cosellconnectors/overwrite-trigger.png" alt-text="Screenshot showing how to overwrite the trigger.":::

- You might have multiple tenants in Partner Center, and you might need to enable a multi-tenancy setting to get leads into your CRM.
  - To check the tenants, use the following steps:

  1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) as a referral admin and navigate to account settings, under organization profile select tenants.

  2. If you see multiple tenants, contact the Microsoft support team to enable the multi-tenancy option for Partner Center.

     :::image type="content" source="media/cosellconnectors/settings-tenants.png" alt-text="Screenshot showing the settings for tenants.":::

##### Leads aren't synchronizing as an opportunity at Salesforce or Dynamics CRM

- If a lead *is* accepted in Partner Center, it will synchronize as an opportunity to the CRM.
- If a lead *isn't* accepted in Partner Center, it will only synchronize as a lead.
  
##### Partner Center to Dynamics Flow isn't getting triggered even after successful Webhook registration
  
To check the tenants, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) as a Referral admin.
2. Go to **Account settings**.
3. Under **Organization profile**, select **Tenants**.
4. If you see multiple tenants, contact the Microsoft support team to enable the multitenancy option for Partner Center.
  :::image type="content" source="media/cosellconnectors/multiple-tenants.png" alt-text="Screenshot showing multiple tenants.":::

##### Flow is getting triggered multiple times, or I can see duplicate opportunities in Dynamics CRM

- Check the opportunity audit history in Dynamics CRM to identify referrals.
  
  You must wait for up to one minute to complete synchronization before making another change and save the opportunity.

##### Installed connector solution version checking
  
You can use the following two procedures to check the installed connector solution for *Dynamics 365* or for *Salesforce*.

To check the version of the installed connector solution for Dynamics 365, use the following steps:

1. Sign in to **[Microsoft Power Automate](https://powerautomate.microsoft.com/)**.
2. Select the environment in which you've configured the connector solution.
3. Select **Solutions.**
  
   From there, you can see the Partner Center Referrals Synchronization for Dynamics 365 solution version.

   :::image type="content" source="media/cosellconnectors/solutions.png" alt-text="Screenshot showing the solutions options.":::

To check the version of the installed connector solution for Salesforce, use the following steps:

1. Sign in to **[Microsoft Power Automate](https://powerautomate.microsoft.com/)**.
2. Select the environment in which you've configured the connector solution.
3. Select **Solutions.**

   From there, you can see the Partner Center Referrals Synchronization for Salesforce solution version.

   :::image type="content" source="media/cosellconnectors/synchronization.png" alt-text="Screenshot showing the synchronization solution.":::

##### I get an XRM API error when turning on Customize Flow at Salesforce

**If you receive an XRM API error when turning on Customize Flow in Salesforce:**

Partner CRM has various custom fields for objects such as opportunity, lead, and account.

You can only expose the required custom fields from these CRM objects to Power Automate the connector.

For more information about custom fields, see the **[Custom field mapping guide](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RWxL6S)**.

- Error message example:

  Request to XRM API failed with error: 'Message: An unexpected error occurred. Code: 0x80040216
:::image type="content" source="media/cosellconnectors/error.png" alt-text="Screenshot showing the unexpected error message.":::

##### I get a "Require the property item/Status" error when turning on Customize Flow in the Salesforce CRM connector solution?

- Error message example:

   :::image type="content" source="media/cosellconnectors/xrm-salesforce-error.png" lightbox="media/cosellconnectors/xrm-salesforce-error.png" alt-text="Screenshot showing the XRM Salesforce error.":::

To address the error, use the following steps:

1. Edit the **(Customize) Create or Get Details from Salesforce** flow.
2. Go to **Create or update lead in CRM**.
3. Go to **Create a new lead action**.
4. Update the **Status** field value to your lead default status value from the pick list. (See the following image.)
5. Save the flow and turn it on again.
  
    :::image type="content" source="media/cosellconnectors/salesforce-status.png" alt-text="Screenshot showing the Salesforce status.":::

##### Troubleshooting flow run issues or opening the logs at Salesforce or the Dynamics CRM connector solution

You can use the following procedures for Dynamics 365 or Salesforce to open the logs or troubleshoot flow run issues.

> [!NOTE]
> Get more details in Power Automate by selecting **See history** or **Analytics for flow**.

To troubleshoot a flow run for Dynamics 365, use the following steps:

1. Go to Cloud flows in **Partner Center Referrals Synchronization for Dynamics 365** solution.
:::image type="content" source="media/cosellconnectors/cloud-flows.png" alt-text="Screenshot showing the cloud flows.":::
2. Select the required flow and select **See analytics**.
:::image type="content" source="media/cosellconnectors/see-analytics.png" alt-text="Screenshot showing the See Analytics window.":::
3. The following analytics window opens. Go to the **Errors** tab, where you can see **Error details**. :::image type="content" source="media/cosellconnectors/error-details.png" alt-text="Screenshot showing error details.":::
4. Select the **Last Error Detail** icon for an error.
:::image type="content" source="media/cosellconnectors/last-error-detail.png" alt-text="Screenshot showing the last error detail icon.":::
In **Confirm Navigation**, select **OK**.
:::image type="content" source="media/cosellconnectors/confirm-navigation.png" alt-text="Screenshot showing the Confirm Navigation screen.":::
5. The following flow run history page appears.
:::image type="content" source="media/cosellconnectors/flow-run-history.png" alt-text="Screenshot showing the flow run history.":::
6. Expand the steps and go to **Action or Trigger Name** step mentioned in the **Error details** mentioned in step 4, where you can troubleshoot the actual error.

To troubleshoot a flow run for Salesforce, use the following steps:

Do the following to troubleshoot a flow run:

1. Go to Cloud flows in **Partner Center Referrals Synchronization for Salesforce** solution. :::image type="content" source="media/cosellconnectors/power-automate.png" alt-text="Screenshot showing Power Automate.":::
2. Select the required flow and select **See analytics**.
:::image type="content" source="media/cosellconnectors/get-details-from-salesforce.png" alt-text="Screenshot showing the Get Details from Salesforce window.":::
3. The following analytics window opens. Go to the **Errors** tab where you can see the **Error details**. :::image type="content" source="media/cosellconnectors/error-details.png" alt-text="Screenshot showing the Error details.":::
4. Select the **Last Error Detail** icon for an error.
:::image type="content" source="media/cosellconnectors/last-error-detail.png" alt-text="Screenshot showing the last error detail icon.":::
This step opens the following **Confirm Navigation**, select **OK**.
:::image type="content" source="media/cosellconnectors/confirm-navigation.png" alt-text="Screenshot showing navigation confirmation.":::
5. The following flow run history page appears.
:::image type="content" source="media/cosellconnectors/flow-run-history.png" alt-text="Screenshot showing the flow run history.":::
6. Expand the steps and go to the **Action or Trigger Name** step mentioned in **Error details** in step 4. Here you can troubleshoot the actual error.

##### Syncing the latest data from Partner Center to CRM

  The bidirectional connectors solution only supports update sync for the mentioned field.
  
- Currency Code
- Deal Value
- Closing Date
- Notes
- Status and substatus

:::image type="content" source="media/cosellconnectors/syncing-items1.png" lightbox="media/cosellconnectors/syncing-items1.png"alt-text="Screenshot showing syncing items between the Customer Relationship Management systems and Partner Center.":::
  
If you want to configure the fields, you can configure the flow called "Customize". Create or Get Details from Dynamics 365" under the section **Update Opportunity** as shown in the following image.
  
:::image type= "content" source="media/cosellconnectors/creating-opportunity2.png" alt-text="Screenshot showing creating an opportunity in the Customer Relationship Management system." lightbox="media/cosellconnectors/creating-opportunity2.png":::

##### Syncing the latest data from CRM to Partner Center

The bidirectional connectors solution only supports update sync for the mentioned field.

- Currency Code
- Name
- Budget Amount
- Description
- State changes in the corresponding Partner Center referrals.

The update functionality checks whether there's any difference between the previously mentioned fields in CRM ("Currency Code," and so on). It initiates an update only if it detects a difference.
:::image type= "content" source="media/cosellconnectors/crm-to-pc-sync3.png" alt-text="Screenshot showing the CRM to Partner Center field sync." lightbox="media/cosellconnectors/crm-to-pc-sync3.png":::
  
If you want to configure the fields, you can configure the flow called `Dynamics 365 to Partner Center (Insider Preview)` for the action **Update a referral with opportunity data** as shown in the following image.
  
:::image type="content" source="media/cosellconnectors/config-field-to-update4.png" alt-text="Screenshot showing fields to update in the CRM system." lightbox="media/cosellconnectors/config-field-to-update4.png":::

##### Contact Microsoft support team for connector configuration or any other issues with connectors

- To connect with Microsoft support, contact **[Microsoft Support](https://support.microsoft.com/)**.

## Next steps

- [Manage leads](manage-leads.md)
- [Manage co-sell opportunities](manage-co-sell-opportunities.md)
