---
title: Manage user accounts
ms.topic: how-to
ms.date: 06/06/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Manage users for your customers in Partner Center - create user accounts, reset passwords, and delete or restore user accounts.
author: jgray42
ms.author: juliegray
ms.custom: engagement-fy23
---

# Manage users for customer accounts

**Appropriate roles**: Admin agent

You can perform many management tasks for a customer, including:

- [Create user accounts](#create-user-accounts-for-a-customer)
- [Delete user accounts](#delete-user-accounts-for-a-customer)
- [Restore deleted user accounts](#restore-deleted-user-accounts)
- [Edit a user's info, permissions, or licenses](#edit-a-users-info-permissions-or-licenses)
- [Reset a customer's password](#reset-a-customers-password)
- [Add or remove user licenses for Microsoft products](./assign-licenses-to-users.md)
- [Assign or revoke licenses to multiple users](./bulk-license-provisioning-for-multiple-users.md).

## Create user accounts for a customer

**Appropriate GDAP roles**: Directory Writer | User Admin

Use the following steps to create customer user accounts:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.
1. Select the customer from the **Customer list**.
1. In the customer menu, select **Users and licenses**.

   :::image type="content" source="./media/users/users-and-licenses-menu-bar.png" alt-text="Screen shot of the Users and licenses menu bar." :::
   
1. To add several users at once by using a spreadsheet, see [Add multiple users for a customer account](adding-multiple-users-to-a-customer-account.md).

   To add users one at a time:
   1. Select **Add user**.
   1. Follow the prompts to enter user information, to assign permissions, and to assign licenses for that user, then select **Close**.
   
      :::image type="content" source="./media/users/add-user-info.png" alt-text="Screen shot of adding a customer." :::
      *Example of Add user screen for pilot users*

   1. To add more users, select **Add another user**.
   1. After you're done adding users, select **Complete**.

      Partner Center displays a list of the new user names and temporary passwords for the users you have added.

   1. Get temporary passwords and send them to your user:
      - Pilot users: For now, you'll need to reset the password after creating each new user. Select the user, select **Reset password**. Record the temporary password, and send them to your user.  
      - All other users: Record the user names and temporary passwords, and send them to your users.

## Delete user accounts for a customer

**Appropriate GDAP roles**: User Admin

Use the following steps to delete a user's account:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.
1. Select the customer from the **Customer list**.
1. In the customer menu, select **Users and licenses**.
1. Delete the user:
   - Pilot users: Select the user, then select **Delete user** from the top of the page.
   - All other users: Select **Users and licenses** > **Delete user**.

When you delete a user account, is set to the status of **Inactive** for 30 days. During this time, you can restore the account, as described in the following section. After 30 days, the account is removed.

## Restore deleted user accounts

When you delete a user account for a customer, the account is set to the status of **Inactive** for 30 days. During this time, you can restore the account.

**Appropriate GDAP roles**: Directory Writer | User Admin

To restore a deleted user account, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.
1. Select the customers to be restored from the **Customer list**.
1. In the customer menu, select **Users and licenses**.
1. Restore the user:

   - **Pilot users**: Select **Restore** from the top of the page, then select the user to restore, then select **Restore**. (If there are no users that can be restored, the **Restore** option is greyed out.)

        :::image type="content" source="./media/users/restore-user.png" alt-text="Screen shot of restoring a customer." :::

   - **All other users**: Select **Users and licenses**, then select **Deleted users (#)**, where # is the number of users you have selected to restore.

   The user accounts reappear in the **Users and licenses** page.

## Edit a user's info, permissions, or licenses

**Appropriate GDAP roles**: License Administrator | User Administrator | Directory Writer

Pilot users can edit user info individually from the Users and Licenses menu:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.
1. Select the customers to be restored from the **Customer list**.
1. In the customer menu, select **Users and licenses**.
1. Select the user, and then select **Edit** in the right pane.
   :::image type="content" source="./media/users/edit-user-edit.png" alt-text="Screen shot of editing a user." :::
1. Follow the prompts to edit user info, permissions, and assign or remove licenses for Microsoft products. After completing all screens,  
   :::image type="content" source="./media/users/edit-user-info.png" alt-text="Screen shot of editing a user - user info pane." :::
1. After all screens are complete, select **Complete** on the Review screen to save changes. 
   :::image type="content" source="./media/users/edit-user-review.png" alt-text="Screen shot of reviewing changes while editing a user." :::


To add or remove user licenses for license-based SaaS subscriptions in the commercial marketplace, see [Add or remove licenses for a SaaS subscription](csp-commercial-marketplace-manage.md#add-or-remove-licenses-for-a-saas-subscription).

License assignment and activation for [Azure Marketplace products](csp-commercial-marketplace-manage.md#assign-licenses-and-activate-a-subscription-on-behalf-of-a-customer) is managed through the independent software vendor (ISV) who published the product.

## Reset a customer's password

**Appropriate GDAP roles**: User Admin | Privileged Authentication Admin (to reset password for license management users) | Privileged Authentication Admin (to reset password for all other users)

Use the following steps to reset a password for a customer:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.
1. Select the customer from the **Customer list**.
1. In the customer menu, select **Users and licenses**.
1. Select the user who's password you want to reset.
1. Select **Reset password**, then select **Yes** to confirm.
1. Send the new temporary password to the customer to send to the user.

## Next steps

- [Assign licenses to users](assign-licenses-to-users.md).
- [Assign or revoke licenses to multiple users](bulk-license-provisioning-for-multiple-users.md).
- [Create multiple users for a customer account](adding-multiple-users-to-a-customer-account.md).
- [Sell software subscriptions through CSP](csp-software-subscriptions.md#activate-and-manage-software-subscriptions).
