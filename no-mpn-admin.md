---
title: What to do if the only admin for your Microsoft AI Cloud Partner Program program has left the company
ms.topic: how-to
ms.date: 11/15/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-account
description: Learn what to do to find a new MPN Admin or get help from your company's Global admin. Also, learn how to add a new Partner Center Global admin.
author: sharath-satish-msft
ms.author: shsatish
---

# What to do if your only admin has left the company

**Appropriate roles**: MPN Partner Admin | Account admin | Global admin

This article describes what to do if your MPN admin/Account admin for your Microsoft AI Cloud Partner Program has left the company in three typical cases: if there are still Global admins left, if there aren't, and if there are no users at all who can access the company's Azure Active Directory (Azure AD).

## You have a Global admin in the account

If there's still a Global admin in the company, they can assign the MPN Partner admin/Account admin role to another person.

To be assigned the MPN Partner Admin/Account admin role:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) with your work account and select the **Settings** (gear) icon.
2. Select the **Account settings** workspace.
3. Select **User Management** in the left navigation menu.
4. In the filter dropdown that says **All users**, select **Global admin** to see who the Global admins for your company are.
5. Contact a Global admin and ask them to assign you the role you need.

## You have no Global admins in the account

At Partner Center, search for any Global admins. (The search procedure is given in the previous answer.)

If there's no Global admin in your company who can assign the Microsoft AI Cloud Partner Program-specific role, follow these steps:

1. Go to [portal.azure.com](https://portal.azure.com/) and sign in with your work account (for example, tom@contoso.com).
2. Select the **Help + Support** option in the left menu nav bar.
3. On the next page, select **New Support request** and **Technical Issue** type in the dropdown menu, insert any other details, and select **Next: Solutions.**

    :::image type="content" source="media/no-mpn-admin/admin-finder.png" lightbox="media/no-mpn-admin/admin-finder.png" alt-text="Screenshot showing how to locate admin in the Azure portal.":::

4. After reviewing the recommended solutions on the next page, select **Next: Details** and enter the required information.
5. Review and create the support request.

## You've completely lost access

If you have a complete loss of access, follow the [Administrator Takeover](/azure/active-directory/users-groups-roles/domains-admin-takeover#internal-admin-takeover) steps to take over an unmanaged directory as Azure Active Directory administrator.

## Not sure if your company already has a work account?

If you're not sure whether your company has a work account, you can follow these steps to check:

1. Sign in to the [Azure admin portal](https://portal.azure.com).
2. Select **Azure Active Directory** from the left menu, and then select **Domain names**.
If you already have a work account, your domain name will be listed.

> [!NOTE]
> If you have an active subscription to Microsoft Azure or Microsoft 365, you already have a work account, and your sign in credentials should be the same as the ones used to access those services.
