---
title: Learn about work accounts and Partner Center
ms.topic: article
ms.service: partner-dashboard
ms.subservice: partnercenter-account
description: Create a work account that links your company to your Partner Center account. This work account enables employees in your company to access Partner Center - Account settings workspace.
author: sharath-satish-msft
ms.author: shsatish
ms.date: 04/19/2023
ms.custom: engagement-fy23
---

# Learn about work accounts and Partner Center

**Appropriate roles**: Global admin | User management admin

Partner Center uses company work accounts, also known as [Azure Active Directory (Azure AD) tenants](/azure/active-directory/develop/quickstart-create-new-tenant), for many purposes, including:

- Managing account access for multiple users
- Controlling permissions
- Hosting groups and applications
- Maintaining profile data

Once you link your company's work email account domain to your Partner Center account, others in your organization can sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) using their own work accounts, depending on the [roles they've been assigned](./find-workspaces-roles-admins.md).

> [!NOTE]
> If you have an active subscription to Microsoft Azure or Microsoft 365, you already have a company work account.

## Company work account email address

Your company work account email address is the email address provided to you by your company. A company work account email address is usually in the format *user@yourcompany.com*.

> [!IMPORTANT]
> Personal email addresses can't be used to access your Partner Center account.

If you have more than one company work account email address, use the one that is associated with your corporate headquarters rather than a regional department. For example, use a *contoso.com* email address rather than a *contoso.uk* address.

## About Azure company work accounts

An Azure company work account is a dedicated and isolated virtual representation of your company in the [Azure public cloud](https://azure.microsoft.com/resources/cloud-computing-dictionary/what-are-private-public-hybrid-clouds/#public-cloud). It's created for you when you subscribe to a Microsoft cloud service such as Azure, Microsoft Intune, or Microsoft 365.

Your work account hosts your Azure AD users and the information about them. This information includes their passwords, profile data, and permissions. The work account also contains groups, applications, and other information pertaining to your company and its security.

## Find out if you already have a work account

If you have an active subscription to Azure or Microsoft 365, you already have a company work account.

Use the following steps to check whether your company has a company work account.

1. Sign in to the [Azure portal](https://portal.azure.com).
1. Select **Azure Active Directory** and then **Custom Domain Names**.

   If your company *does* have a company work account, your domain name will be listed.

   If your company *doesn't* have a company work account, you can create one during the enrollment process.

The following diagram can help you determine:

- Whether you have a company work account
- Whether you need to create a company work account
- How to sign in to your company work account

:::image type="content" source="media/onboardingAADFlow.png" lightbox="media/onboardingAADFlow.png" alt-text="Flow chart to determine whether you have a company work account or need to create one.":::

> [!NOTE]
> Before you link an existing company work account to your Partner Center account, think about how many users in the company work account will need access to Partner Center. If you have users in the company work account who won't need access to Partner Center, consider creating a new account only for those users who will need Partner Center access.

For more information about adding domains in Azure AD, see [Add or associate a domain in Azure AD](/azure/active-directory/active-directory-add-domain).

## Next steps

- [Manage your Partner Center account](partner-center-account-setup.md)
- [Track verification status](verification-responses.md)
