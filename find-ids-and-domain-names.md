---
title: Find tenant ID, domain name, user object ID
ms.topic: how-to
ms.date: 11/15/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-account
description: Learn how to find IDs in the Azure portal - an organization's Azure AD tenant ID, domain name, or specific user object ID. Some tasks need this information - Account settings workspace.
author: sharath-satish-msft
ms.author: shsatish
---

# Locate important IDs for a user

**Appropriate roles**: Global admin

This article describes how to use the [Azure portal](https://portal.azure.com/) to locate the following information for a user:

- [The Microsoft Azure Active Directory (Azure AD) *tenant ID* of the user's organization or company](#find-the-microsoft-azure-ad-tenant-id-and-primary-domain-name)

- [The *primary domain name* of the organization or company associated with the Azure AD tenant](#find-the-microsoft-azure-ad-tenant-id-and-primary-domain-name)

- [The *user object ID*](#find-the-user-object-id)

## Find the Microsoft Azure AD tenant ID and primary domain name

Follow these steps to locate the Azure AD *tenant ID* or *primary domain name* at the Azure portal. (If you'd like to find a tenant ID programmatically, see [Find tenant ID with PowerShell or CLI](/azure/active-directory/fundamentals/how-to-find-tenant#find-tenant-id-with-powershell).)

> [!NOTE]
> The *tenant ID* may be called different names in different applications or resources. For example, the tenant ID may be referred to as the *directory ID*, the *Azure Active Directory (Azure AD) tenant*, *Microsoft ID*, or for certain reports, the *tenantguid*.

To find a tenant ID and a primary domain name, use the following steps:

1. Sign in to the [Azure portal](https://portal.azure.com/).

2. Select **Azure Active Directory** from the menu.

   :::image type="content" source="media/id/1-find-id-azure-portal-home-screen.png" lightbox="media/id/1-find-id-azure-portal-home-screen.png" alt-text="Shows Azure portal selecting the Azure Active Directory option from the menu.":::

3. The Azure Active Directory **Overview** page appears. To find the Azure AD tenant ID or primary domain name, look for **Tenant ID** and **Primary domain** in the **Basic information** section.

   You can also find a tenant ID in the Azure portal in other ways:

   - Select **Azure Active Directory** from the menu. Then, locate the **Manage** section on the menu and select **Properties**.

   - The **Properties** page also displays a user's associated Tenant ID.

   :::image type="content" source="media/id/3-find-id-azure-portal-aad-properties-tenant-id-partial.png" lightbox="media/id/3-find-id-azure-portal-aad-properties-tenant-id-partial.png" alt-text="Screenshot showing the Properties page with the Tenant ID highlighted.":::

## Find the user object ID

Just finding the domain name and tenant ID may not always be enough. You may also need to locate the object ID assigned to a user.

To find a user's object ID, use the following steps:

1. Sign in to the [Azure portal](https://portal.azure.com/).

2. Select **Azure Active Directory** from the menu.

3. Locate the **Manage** section on the menu and then select **Users**.

      :::image type="content" source="media/id/4-find-id-azure-portal-aad-manage-users-option.png" alt-text="Screenshot that shows the Azure Active Directory menu with the Users option highlighted.":::

4. On the **Users** page, enter the user's name in the **Search** box.

      :::image type="content" source="media/id/5-find-id-azure-portal-aad-all-users-search.png" alt-text="Screenshot that shows the Users page with a search box to search for a user.":::

5. Select the user's name where it appears on the list.

      :::image type="content" source="media/id/6-find-id-azure-portal-select-user-name-partial.png" lightbox="media/id/6-find-id-azure-portal-select-user-name-partial.png" alt-text="Screenshot showing the User page displaying a row for the searched user.":::

6. Locate the **Basic info** section on the user's **Profile** page. The **Object ID** that is displayed is the user's unique object ID.

      :::image type="content" source="media/id/7-find-id-azure-portal-aad-user-profile-object-id.png" lightbox="media/id/7-find-id-azure-portal-aad-user-profile-object-id.png" alt-text="Screenshot that shows the User Profile page with Identity section and the Object ID highlighted.":::

## Next steps

- [Find your tenant ID programmatically with PowerShell or CLI](/azure/active-directory/fundamentals/how-to-find-tenant)
- [Learn more about user profiles in Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)
- [Find out how partners can see or export customer details in Partner Center](see-your-customer-list.md)
