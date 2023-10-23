---
title: Create user accounts and assign roles
description: Every employee must be assigned a role before they can access Partner Center. Learn how to create user accounts, assign roles, and set permissions.
ms.topic: how-to
ms.service: partner-dashboard
ms.subservice: partnercenter-account
ms.custom: contperf-fy21q2
author: sharath-satish-msft
ms.author: shsatish
ms.date: 11/15/2022
---

# Create user accounts

**Appropriate roles**: Account admin | Global admin | User management admin

This article describes how to create user accounts for employees who need access to Partner Center.

Your company's account includes user accounts for anyone on your team. The work they do may include adding or managing customers, selling subscriptions, working with billing and invoicing, creating business profiles, managing referrals, working with incentives programs, providing support, and more.

## Prerequisites

To perform the tasks described in this article, you must be:

- An *Account admin*, *Global admin*, or *User management admin* at Partner Center

  \-and-
- A *User admin* or *Global admin* for Microsoft Azure Active Directory (Azure AD)

For more information about user roles, see [Azure AD built-in roles](/azure/active-directory/roles/permissions-reference) and [Assign roles, permissions, and workspace access to users](permissions-overview.md).

## Assign user roles

Partner Center access is role-based. To work in Partner Center, a new user must have one or more assigned roles.

Roles can be in the following categories:

- Cloud Solution Provider (CSP) roles
- Azure AD tenant roles
- Non-Azure AD company roles

A user might need to be assigned roles in all these categories.

Assigning appropriate roles to new users ensures that they can view the information and perform the tasks they need to work effectively, without granting them unnecessary permissions.

> [!IMPORTANT]
>Users must be listed in your tenant to access Partner Center. Role assignments provide additional access.

Users who need changes to their assigned roles can request changes from a Global admin. They can find Global admins by going to **User management** and filtering on *Global admin*.

## Create a new user

To create a new user, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Settings** (gear).

2. Select the **Account settings** workspace and then **User management**.

3. Select **Add user**.

4. In **Add user**, select **Create new users**.

   :::image type="content" source="media/create-user-accounts-and-set-permissions/add-user.png" alt-text="Screenshot of selecting 'Create new users' in the 'Add user' dialog box in Partner Center.":::

5. Enter the user's full name and unique email address.

6. Select the user roles that you want to assign to the user.

7. Select **Add** to create the user account.

8. Confirm the user information displayed on the next page, and make a copy the user sign-in information.

   > [!IMPORTANT]
   > Be sure to copy the new user's sign-in information. You won't be able to access it again later.

9. Send the information to the new user.

   When a new user signs in to the Partner Center for the first time, they're prompted to change their password.

## Next steps

- [Assign roles, permissions, and workspace access to users](permissions-overview.md)
