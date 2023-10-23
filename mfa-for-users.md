---
title: Set up your users with multifactor authentication
ms.topic: how-to
ms.date: 06/09/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-account
description: Learn how to set up your employees with MFA (Account settings workspace).
author: vijay-vala
ms.author: vijvala
---

# Set up your users with multifactor authentication

**Appropriate roles**: Global admin

We strongly recommend that all partners enable multifactor authentication (MFA) for their users in their partner tenant.

- We need everyone in our ecosystem to act and ensure appropriate security protections are in place.
- Greater privacy safeguards and security are among our top priorities.
- Prevention is the best defense, and we're only as strong as our weakest link.

## Add multifactor authentication for your users

It's easiest to enable MFA for your users when you add them to your Azure AD tenant. The following procedure shows how to enable MFA for existing users.

> [!NOTE]
> You must be the Global admin for your company to complete this task.

To add multifactor authentication for your users, use the following steps:

1. Sign in to the [Azure portal](https://portal.azure.com) and select **User management**.
1. Select **Multifactor authentication**.
1. Select the user you want to enable and then select **Enable**.
 "Enabled" in this procedure means that the user is asked to set up MFA verification when they sign in for the first time. Thereafter, they're asked at sign-in to provide a code that's sent to them by email or text message (depending on which method they selected).

:::image type="content" source="media/multi-factor-authentication/security-verification.png" alt-text="Screenshot of setting up security verification in Partner Center.":::

## Enforce MFA

You can enforce MFA  by selecting **Enforce** when using the preceding steps.

- Users start with MFA disabled.
- User state changes to *enabled* when you enroll them in [per-user Azure Active Directory Multi-Factor Authentication](/azure/active-directory/authentication/howto-mfa-userstates).
- User state changes to *enforced* when enabled users sign in and complete the registration process.

To learn more, see [Enable per-user Azure Active Directory Multi-Factor Authentication to secure sign-in events](/azure/active-directory/authentication/howto-mfa-userstates).

## Next steps

- [Assign roles and permissions to users](permissions-overview.md)


