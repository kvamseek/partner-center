---
title: FastTrack – Cloud Product Performance
ms.topic: article
ms.service: partner-dashboard
ms.subservice: partnercenter-insights
description: Read about FCU, the focused user experience created for FastTrack Ready partners (FRPs), including how to access the tool, how to update information, and answers to some frequently asked questions.
author: kshitishsahoo
ms.author: ksahoo
ms.date: 06/27/2023
---

# FastTrack – Cloud Product Performance

**Appropriate roles**: Report viewer | Executive report viewer

The FastTrack report provides access to customer insights (usage information, customer opportunities, referrals, etc.) for partners participating in one of the FastTrack Partner Community efforts that focus on driving usage across Microsoft 365 workloads.

## Access

> [!IMPORTANT]
> Access to the Insights workspace and FastTrack page requires either the **Executive Report Viewer** or **Report viewer** role.
>
> - Executive report viewer gives access to all reporting data sets.
> - Report viewer gives access to most reporting data sets but not to sensitive data, such as revenue and customer or employee personal information.
>
> A Global admin or an Account admin can assign users these roles, which are assigned either for an entire company or for a specific Microsoft AI Cloud Partner Program location.
>
> For more information, see [CPP role-based access](insights-roles.md).

To access the FCU, follow these steps:

1. Sign in to [Partner Center](https://partnercenter.microsoft.com/) and select the **Insights** workspace.
1. From the left navigation pane, select **FastTrack**.

## Review tenant usage details

To view the tenant's usage information, select the percentage from the **Usage %** column.

:::image type="content" source="media/insights-fasttrack/fasttrack-tenant-usage.png" lightbox="media/insights-fasttrack/fasttrack-tenant-usage-lightbox.png" alt-text="Screenshot showing detailed information of a tenant's usage.":::

The tenant's account displays the following information:

- Workloads
  - Those claimed by your organization show the claim number.
  - Those unclaimed include a **Claim workload** link.
  - Those claimed by other partners aren't listed.
  - For claimed and unclaimed workloads, usage information is visible once there is at least one claimed workload on the tenant.
- Incentives available
- Usage %
- Monthly Active Users
- Paid Available Units
- Potential Earnings

:::image type="content" source="media/insights-fasttrack/fasttrack-potential-earnings.png" lightbox="media/insights-fasttrack/fasttrack-potential-earnings-lightbox.png" alt-text="Screenshot showing an example of a tenant's usage.":::

## Create and review status notes

Status notes are used to document the onboarding scope, risks, next actions, next action date, and next action owner. FastTrack Ready Partners (FRPs) need to create status notes for each customer throughout the partner-customer relationship as major milestones are met or as requested by members of the FastTrack team.

To create a status note, follow these steps:

1. Select the account for which you need to create or review a status note. The tenant details page opens.
1. To add a new note, select **+ Add note** from below **Status Note updates**.
1. In the **Add Status Note updates** window, enter details for the note and select **Save**.

:::image type="content" source="media/insights-fasttrack/fasttrack-add-notes.png" lightbox="media/insights-fasttrack/fasttrack-add-notes-lightbox.png" alt-text="Screenshot illustrating how to add a new status note.":::

To review an existing status note, follow these steps:

1. Select the account for which you need to create or review a status note. The tenant details page opens.
1. Select the status note you'd like to review.
   - The last four status notes are visible by default.
   - If the note is truncated, select the **read more** link to see the entire note. - To see more than the last four notes, select the **View all history** button.

## Create and update contacts

In the contacts section, you can take the following actions:

- **Add** contacts by selecting **New**
- **Update** contacts by selecting **Edit**
- **Delete** contacts by selecting **Delete**

### Customer versus partner contact

In the new contact list, either "Customer" or "Partner" can be selected. At least one customer contact should be selected as "survey eligible."

- **Customer** contacts have the following required fields:
  - Name
  - Email
  - Country/Region
  - Survey Language
  - Services assisted with
  - Survey Eligible
- **Partner** contacts have the following required fields:
  - Name
  - Email
  - Services assisted with

> [!NOTE]
> The **Survey eligible** box isn't available when the "Partner" contact type is chosen.

## Update service status

Read on to learn how to update the service status for a tenant using L1-L2-L3 and service intent notes.

### L1-L2-L3

To understand a customer's intent to use a service, FastTrack uses a L1-L2-L3 taxonomy.

|Designation|Description|
|---|---|
|L1|Status of the customer's service deployment|
|L2|Reason for the status of the customer's service deployment|
|L3|Engineering reason|

L1-L2-L3 is used to understand scenarios in which a customer:

- Is continuing to make progress with service adoption
- May have encountered something blocking them from deployment, and the FRP needs to provide details as to why
  - In the event the customer is blocked, and the reason why is captured, there may be options available to help unblock the customer and let them continue with deployment.

If the customer expresses they don't have intent to adopt a service, this taxonomy enables us to understand the reason behind the lack of intent.

:::image type="content" source="media/insights-fasttrack/fasttrack-add-entitlement-status.png" alt-text="Screenshot illustrating how to add entitlement status and indicate L1, L2, or L3.":::

The L1, L2, and L3 options are dependent on one other:

- Depending on the value selected for the L1, there may or may not be L2 options listed.
- Depending on the L2 reason (if applicable), there will be different L3 options.

There could be some entitlements in progress and others that are blocked for the same workload; for example:

- If the L1 is set to "In Progress," the L2 and L3 reasons aren't applicable.
- If the L1 is set to "Blocked," the L2 list is populated with options. If L2 is populated, depending on the value selected, there may be L3 options to select.

The entitlement sum should match the **Total entitlements** count regardless of status. When adding or editing the service status, the entitlement count is visible at the top of the pane.

### Service intent notes

When reporting customer status in the FCU, service intent notes provide a current picture of the customer intent for each workload.

Partners need to provide service intent notes in the FCU. These notes are concise statements that describe a customer's intent, or lack thereof, to consume the service. When summarizing the current service intent, make sure to include the "why" or "reason" method. This is one of the key components of your statement. Only a sentence or two is needed to sufficiently state the status. Updates should be provided as needed so that the workload entitlements have a clear and up-to-date description that accurately reflects the customer's intent for the service.

Guidelines for writing service intent notes:

- **Do** summarize the intent for service, or lack of intent, and include the "why" behind it.
- **Do** convey whether the customer is successfully moving forward with onboarding.
- **Do** explain the primary blocker keeping your customer from moving forward if blocked.
- **Do** use clear language:
  - Words and phrases like *unable*, *problem*, *blocked*, *don't have intent*, *issues*, *no value*, or *lack of features* help clarify the intent for the service.
- **Don't** use ambiguous language:
  - Words and phrases like *for now*, *currently*, or *yet* don't clarify the service intent.
- **Don't** record information about the engagement in the service intent note.
- **Don't** copy and paste the same note for each workload:
  - This is discouraged because the same note is frequently not applicable to multiple workloads.
  
If you need assistance concisely describing the technical aspects of the note, you should work with your FastTrack Partner Manager to make sure the technical detail required is included.

For more information on the use of L1-L2-L3 and service intent notes, see the [FastTrack Playbook](https://fasttrack365-kb.powerappsportals.com/?id=KB-02040).

## Referrals tab

The **Referrals** tab allows FRPs to see all referrals in one location. On this tab, FRPs can see a list of tenants that have been assigned to their partner organization. The tenant name, RFA ID, and date of assignment are visible on the main page. Selecting a tenant name gives more information:

- Tenant domain
- Tenant ID
- RFA ID
- RFA workloads
- Active usage (AU%)
- Contacts
- Notes History

If the AU% information at the time of the referral isn't available, a link to the FRP Dashboard is presented. Data on the FRP Dashboard will be available two to three days after assignment.

The existing referral emails will continue to be sent. The referral will take about 15 minutes to appear in the FCU after being assigned. If you get the email and immediately check the **Referrals** tab, you may not see it; refresh the page after 15 minutes.

## Frequently asked questions about FCU

The following are some common questions about the FCU.

### What if I can't access the FCU?

Users are required to have the **Report Viewer** or **Executive Report Viewer** role to access the FCU because it’s hosted in the Insights workspace of Partner Center.

To verify **Report Viewer** or **Executive Report Viewer** role assignment:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home).
1. Select the **Settings** (gear) icon on the top right, and then select **Account settings**.
1. Select **User management** and then **Search** for your account or the account in question.
1. Open the account details by selecting the user in question.
1. Confirm that the **View data and reports for one or more locations (select the locations where the user needs to be able to view data and reports)** option is selected.
   - The user can have access to the Entire organization or to specific locations by filtering on specific MPNs.
   - If filtered by **MPN** instead of **Entire organization**, only the tenants claimed using these MPNs are visible. Some partners may want to segment which tenants their users see in the FCU. This can be achieved by only granting access to the user for their respective MPN locations.
   - Confirm that the **Report viewer** or **Executive report viewer** is selected in the drop-down.

### Why don’t I see any tenants when logging into the FCU?

This can happen if the account does not belong to the same tenant where the Claiming Partner of Record (CPOR) claims were submitted.

### Why don’t I see any tenant data, even though my tenant is listed in the FCU?

When onboarding into the FRP program, a TenantID was provided that allowed access for accounts in that tenant to access FastTrack data. If you’re accessing the FCU from a different account, we may need to update the TenantID used to allow access to the FastTrack details. Open a ticket using the [FRP Partner Support tool](https://aka.ms/FRPHelp).

### Why do I get a message saying, “An error occurred while fetching data, please refresh the page and retry” when selecting a tenant name in the FCU?

If this happens for all tenants, it’s likely that the account the user is logged in with hasn't been onboarded to the FRP program. See [this answer](#why-dont-i-see-any-tenant-data-even-though-my-tenant-is-listed-in-the-fcu) for more details.

If this happens only for specific tenants, they likely don't exist in FastTrack. This is expected if the tenant has fewer than 150 licenses of a [FastTrack-eligible](/microsoft-365/fasttrack/eligibility) plan. If the tenant has more than 150 licenses of a FastTrack-eligible plan, open a ticket using the [FRP Partner Support tool](https://aka.ms/frphelp) and include the TenantID and workload in question.

### How do I assign partner FMs/FEs?

Partners are no longer required to add a partner FastTrack Manager (FM) or FastTrack Engineer (FE) assignment before editing.

### Where do I submit FCU-related support tickets?

If you experience an issue with the FCU itself, FRPs should continue to open support tickets using the [FRP Partner Support tool](https://aka.ms/frphelp).

### Where can I find the TenantID of a tenant in the FCU?

When selecting the tenant name, the TenantID is located at the top of the tenant details page.
