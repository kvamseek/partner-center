---
title: View and export GDAP activity logs
ms.topic: article
ms.date: 03/21/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Learn how to access GDAP activity logs.
author: kvamseek
ms.author: vamseekk
---

# View and export GDAP activity logs

**Appropriate roles**: All users

You can view your granular delegated admin privileges (GDAP) relationship activity on the activity log page in your Partner Center account settings.

## Activity logs

The customer's activity data can be viewed and exported as a .csv file. The activity log displays the following columns:

- **Date-Time**: The date and time of the action
- **Affected customer**: The customer's company name
- **Action**: The action taken, such as "granular admin relationship terminated"
- **Performed by**: The partner associated with the activity

:::image type="content" source="media/gdap/gdap-activity-log.png" lightbox="media/gdap/gdap-activity-log.png" alt-text="Activity log page.":::

Use the following steps to generate your activity log.

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select the **Settings** (gear) icon.
2. Select **Account settings**, then select **Activity log**.
3. Input the dates you'd like to view in the **From** and **To** fields. The activity log export defaults to the most recent month.
4. Select the down arrow to view logged details for any previous activity.
5. Select **Export log**.

> [!NOTE]
> Any GDAP relationships that have been in the **Expired** or **Terminated** state for one year and **Approval pending** state for 90 days will automatically be cleaned up. This means the relationship will no longer be accessible or visible to the customer or the partner.

## Next steps

- [Obtain permissions to manage customer](gdap-obtain-admin-permissions-to-manage-customer.md)
- [Customer approval](gdap-customer-approval.md)
- [Assign Azure AD roles](gdap-assign-azure-ad-roles.md)


