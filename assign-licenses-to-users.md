---
title: Manage users and licenses
ms.topic: how-to
ms.date: 06/06/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Manage permissions and licenses for users in a customer account in Partner Center 
author: amitravat
ms.author: amrava
ms.custom: engagement-fy23
---

# Manage permissions and licenses for users in a customer account

**Appropriate GDAP roles**: License Administrator | User Administrator | Directory Writer

Pilot users: Use these steps to change permissions or add or remove user licenses for Microsoft products for a single user.

To add or remove user licenses for license-based SaaS subscriptions in the commercial marketplace, see [Add or remove licenses for a SaaS subscription](csp-commercial-marketplace-manage.md#add-or-remove-licenses-for-a-saas-subscription).

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.
1. Select the customers to be restored from the **Customer list**.
1. In the customer menu, select **Users and licenses**.
1. Select the user, and then select **Edit** in the right pane.
   :::image type="content" source="./media/users/edit-user-edit.png" alt-text="Screen shot of editing a user." :::
1. Modify any user info, and select **Next**.
   :::image type="content" source="./media/users/edit-user-userinfo.png" alt-text="Screen shot of the Edit user - User Info page." :::
1. Update permission settings, then select **Next**.
   :::image type="content" source="./media/users/edit-user-permissions.png" alt-text="Screen shot of the Edit user - Permissions page." :::
1. Add or revoke licenses, then select **Next**.
   :::image type="content" source="./media/users/edit-user-licenses.png" alt-text="Screen shot of the Edit user - Assign licenses page." :::
1. Review the changes, then select **Complete**.
   :::image type="content" source="./media/users/edit-user-review.png" alt-text="Screen shot of the Edit user - Review page." :::

## CSP licenses in the Microsoft 365 Admin Center


CSP subscriptions appear in both the **Licenses** and **Your products** tabs for **Customers** under **Billing**.

*Office 365 Extra Storage* or *Defender for Office 365 for Faculty* don't appear in the **Licenses** tab because they aren't assignable to customers. However they do appear in the **Your products** tab, which customers can see.

Software purchases appear in the **Your products** tab, which only customers can see. Partners should use Partner Center to view software purchases with associated key and/or download media.

NCE licenses appear as **Not Available** in the **Your Products** page in **Assigned Licenses** tab. The purchased quantity shows the license count, but **Assigned Licenses** always appears as **Not Available**.

## Next steps

- [Manage user accounts](./manage-user-accounts.md).
- [Add or remove licenses for a SaaS subscription](csp-commercial-marketplace-manage.md#add-or-remove-licenses-for-a-saas-subscription).
- [Assign or revoke licenses to multiple users](bulk-license-provisioning-for-multiple-users.md).
- [Sell software subscriptions through CSP](csp-software-subscriptions.md#activate-and-manage-software-subscriptions).
