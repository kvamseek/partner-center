---
title: How to check incentives admin access
ms.topic: how-to
ms.date: 1/10/2023
description: Read these guidelines to understand on how to check your incentives admin permission in PC
ms.service: partner-dashboard
ms.subservice: partnercenter-incentives
author: Karthic83
ms.author: kashanum
---

# How to check your incentives user permission

**Appropriate roles**: Incentives admin or Incentives user

> [!NOTE]
> CHIP live ID authentication isn't supported after March 18, 2022. You must have *Incentives admin* or *Incentives user* access in Partner Center to view the incentives in the CHIP platform.

## How to check correct access

To check if you have **Incentives admin** or **Incentives user** permission, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Settings** (gear).

2. Select **Account settings**.

   :::image type="content" source="media/incentives/configure-settings.png" alt-text="Screenshot showing settings." lightbox="media/incentives/configure-settings.png":::

3. Select **My profile** in the left navigation menu, then **Click here to view permissions.**

   :::image type="content" source="media/incentives/configure-user-profile.png" alt-text="Screenshot showing my profile." lightbox="media/incentives/configure-user-profile.png":::

4. In the results page, scroll down to **Manages your organization's incentives for one or more locations**.
5. Check if you have **Incentives admin** or **Incentives user** permission to the entire organization or to the locations to which you need access.

   :::image type="content" source="media/incentives/configure-user-settings.png" alt-text="Screenshot showing incentive permissions." lightbox="media/incentives/configure-user-settings.png":::

6. If you're an *Incentives admin* or *Incentives user*, you can access CHIP after March 18, 2022. If you don't have *Incentives admin* or *Incentives user* permission, contact your global admin for access.

## Provide admin consent

You might receive the following message saying that admin approval is required. It's a one-time approval that must be provided by a Global admin to authorize the CHIP application.

   :::image type="content" source="media/incentives/admin-approval-message.png" alt-text="Screenshot showing message to get admin consent." lightbox="media/incentives/admin-approval-message.png":::

[Contact your Global admin](./find-workspaces-roles-admins.md#find-your-admins) if you get the *Need admin approval* message. They can follow the instructions,  [Admin consent - How to approve](chip-check-access.md#admin-consent---how-to-approve), to grant the access.

## Admin consent - How to approve

To grant admin consent, use the following steps:

1. Sign in to [CHIP](https://channelincentives.microsoft.com) with your Microsoft Azure Active Directory (Azure AD) identity that has Global admin permission.
2. Select **Consent on behalf of your organization**.
3. Select **Accept**.

> [!NOTE]
> A Global admin doesn't need access to the CHIP application to grant admin consent.

   :::image type="content" source="media/incentives/admin-acceptance.png" alt-text="Screenshot showing on how to provide admin consent." lightbox="media/incentives/admin-acceptance.png":::

## Next steps

- [How to find your global admin](./find-workspaces-roles-admins.md#find-your-admins)
- [Partner Center permissions overview](permissions-overview.md)
