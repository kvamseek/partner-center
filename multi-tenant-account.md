---
title: Add tenants to your Partner Center account
ms.topic: article
ms.date: 05/25/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-account
description: Learn how to add, consolidate, or manage multiple Azure AD tenants in your Partner Center account, and learn why you might want to do so.
author: sharath-satish-msft
ms.author: shsatish
---

# Add and manage multiple tenants in your Partner Center account

**Appropriate roles**: Global admin | Account admin

This article discusses how to consolidate multiple Microsoft Azure Active Directory (Azure AD) tenants for your company and then add and manage them in your Partner Center account. There are many reasons to do so. For example:

- Let's say your company, Contoso, has acquired another company, Fabrikam. You want the two companies to remain separate, but you want the new employees to be able to use Partner Center. In this case, you associate the new company's Azure AD tenant with your partner global account (PGA). This association enables users in both companies to work in Partner Center.

- If you run your business with more than one tenant (for example, *contoso.com*, *contoso.uk*, and *contoso.in*), you can use multitenancy to group them in the same PC account.

- If mergers and acquisitions guidelines require you to work with tenants of both companies, you would use both the *constoso.com* and *fabrikam.com* tenants.

- Users of any of the tenants need to be able to:
  - Access Partner Center for training, digital downloads, or Microsoft Certified Professional (MCP) association.
  - Be assigned Partner Center roles such as Microsoft AI Cloud Partner Program admin or incentives admin.

## Add an Azure AD tenant to your account

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) as a Global admin and select the **Settings** (gear) icon.

2. Select the **Account settings** workspace, and then select **Tenants**.

3. Select **Associate Azure AD**, and then indicate the tenant you want to associate.

4. Sign in at the prompt as Global admin to the tenant you want to associate and then select **Confirm**.

   After you've confirmed the association, an **All set** message appears.

5. Select **Return to tenant management** to view the newly added tenant.

> [!NOTE]
> You can't associate a tenant with an account if it's already associated with another Partner Center account.

## Remove a tenant from your account

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) as a Global admin and select the **Settings** (gear) icon.

2. Select **Account settings**, and then select **Tenants**.

3. Select the **Partner** tab.

4. Select the radio button next to the tenant you want to remove, and then choose **Remove** on the top of the **Tenants** table.

   :::image type="content" source="media/multi-tenant-account/remove-tenant.png" lightbox="media/multi-tenant-account/remove-tenant.png" alt-text="Screenshot of the current tenant associations and their Remove links in Partner Center.":::

   As shown in the preceding screenshot, the **Remove** option is enabled for all associated tenants, except for the primary tenant and the tenant that you're currently signed in to.

   > [!NOTE]
   > When you remove a tenant, the users on that tenant no longer have access to the Partner Center account, and the removal might have an impact on your [competencies](https://partner.microsoft.com/membership/competencies).

## Next steps

- [Create user accounts](create-user-accounts-and-set-permissions.md)
