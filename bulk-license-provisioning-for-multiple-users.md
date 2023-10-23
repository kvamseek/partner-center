---
title: Assign or revoke licenses to multiple users
ms.topic: how-to
ms.date: 6/6/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Learn how to use a customer account to assign or revoke licenses and services to one user or to multiple users at once.
author: amitravat
ms.author: amrava
---

# Assign or revoke licenses at the same time to multiple users in a customer account

**Appropriate roles**: Admin agent | Global admin | Helpdesk agent | Sales agent | User management admin

You can assign licenses and services to one user, or to multiple users at once, in a customer account. You can also revoke license assignments to users.

Partner Center tracks and shows all customer-owned license entitlements.

## Assign licenses to multiple users

1. From the **Partner Center** menu, select **Customers**, and then choose a customer from the list.
1. Select **Users and licenses**.
1. Select the check box for two or more users from the list. (To select all users on the current page, select the check box at the top of the **Users** column.)

    You can find and select users across multiple pages using the **First**, **Previous**, **Next** and **Last** tools.

1. Select the **Selected Users** link. The displayed list shows the selected users.
1. Select the **Manage licenses** link.

    The Manage licenses page shows the list of license entitlements for the customer accounts, and the count of **Available licenses** for each product.

   Pilot users have options to update the user location, and to assign and revoke licenses.
   :::image type="content" source="./media/users/manage-user-licenses.png" alt-text="Screen shot of the Manage License page, with two users selected." :::

    - The check boxes in the **Product** column show the status of all selected users for the customer-entitled products:

       - When all selected users already have a license, the product's check box is filled.

       - If some of the selected users have a product license, the product's check box is partially filled.

       - If none of the selected users have a product license, the check box is clear.

    - Each selected user appears in a small box near the top of the page. Users appear in sorted order.

    - Select any link in the **Assigned** column to view a tooltip list showing the selected users that already have a license.

    - Any product without available licenses shows a **Buy more** link. You can purchase more licenses when customers require them.

1. Under **Assign and revoke licenses**, select product licenses for the new users.

   For example, if none of the selected users have Office 365 Enterprise licenses and you want to add them, select the check box. You need enough licenses for each selected product.

1. Select **Save**. The Partner Center opens a **Licenses updated** confirmation page listing the users and their new licenses.

> [!NOTE]
> Some Microsoft products may not be available in certain locations. Other products are dependent on other products or services, or can't be assigned together to the same user. After you save, the confirmation page lists all users' results from successful license assignment, and any errors from the license assignment.

## Revoke users' license assignments

1. From the **Partner Center** menu, select **Customers**, and then choose a customer from the list.

1. Select **Users and licenses**.

1. Select the check box for one or more users from the list. (To select all users on the current page, select the check box at the top of the **Users** column.)

    Page through the **First**, **Previous**, **Next** and **Last** tools to find and select other users. You can select across multiple pages.

1. After selecting the users, choose the **Selected Users** link. The displayed list shows only the selected users.

1. Select the **Manage licenses** link.

1. Under **Assign and revoke licenses**, clear the check boxes for products assigned to the users.

   For example, if all of the selected users have Office 365 Enterprise licenses and you want to revoke them, select the check box to clear it.

1. Select **Save**.

## Next steps

- [Manage permissions and licenses for users in a customer account](assign-licenses-to-users.md)
- [Reinstate admin privileges for a customer's Azure CSP subscriptions](reinstate-csp.md)
