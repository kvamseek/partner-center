---
title: Partner Center account setup
ms.topic: overview
ms.date: 06/27/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-account
description: Learn how to use Partner Center to manage your company's profile, bank and tax information, roles, permissions, and more.
author: sharath-satish-msft
ms.author: shsatish
ms.reviewer: sbhansali
---

# Partner Center account setup

**Appropriate roles**: Global admin | Account admin

The account you create when you enroll in Partner Center is your work email plus your business information.

After you create an account in Partner Center, you can set up your company's full profile including support details, file tax exemptions (if appropriate), and primary contact information.

Your company's account includes user accounts for anyone on your team. The work they do may include adding or managing customers, selling subscriptions, working with billing and invoicing, creating business profiles, managing referrals, working with incentives programs, providing support, and more.

To learn more, see [Invite employees to join Partner Center](partner-membership-center-retirement-faq.md) and [Add a new user](create-user-accounts-and-set-permissions.md).

## Organization profile

Use the Organization profile pages to:

:::image type="content" source="media/account-settings/account-settings-new.png" alt-text="Legal info menu.":::

### Legal info

When you first join Partner Center, your company goes through a verification process with Microsoft. You can track the status of your verification on the **Legal info** page. It shows the primary contact (whom Microsoft contacts about partner questions) and the primary legal contact (the person who manages your legal information and status). All of your company's business locations are listed and can be added here.

### Provide your company's legal business details

You can either look up your company profile or enter company information manually. If your company is registered with [Dun & Bradstreet](https://partner.microsoft.com/marketing/usisvshowcase/dunandbrad), use the DUNS ID to look up your company info. If you want to provide your company details yourself, select **Manual**.

If your company is located in **Armenia**, **Hungary**, **Kyrgyzstan**, **Moldova**, **Uzbekistan**, or **Russia**, and you enter your address manually, we validate your address for you. If the one you enter differs from the validated one, we suggest you use the validated address. Verification ensures that the address is both accurate and can be shipped to.

### Primary contact email

The Primary contact email is what we use to notify you about the verification of your account. It's important that the email you provide for the primary contact is one that is regularly managed and watched.

Learn more about [Verification and your account information](verification-responses.md).

### Tenants profile

The Tenants profile page contains all of the information about your Azure AD tenants, both commercial and developer. This profile is where the global admin can associate new tenants to the partner global account.

> [!NOTE]
> The **Microsoft ID** shown in this section is the same as your Azure Active Directory (Azure AD) tenant ID.

### Identifiers

The Identifiers page contains the Partner Center identities for your company: PartnerIDs, publisher IDs, Windows publisher IDs, and more.  Each area can be expanded and edited so that, for example, the primary contact for your publishing business is easily located.

### Company profile

The Company profile page identifies the type of partnership you have with Microsoft, such as independent software vendor or CSP program partner. It shows the number of customers you're working with, annual revenue, and the current size of your company. Expand company information on the **Company details** page to tell Microsoft the type of work you want to do with Microsoft, such as build applications, resell Microsoft and third-party software, or be a systems integrator. Optionally, define where you currently do business and the locales where you'd like to expand your business in the future.

### Account merge profile

When you invite a company that has an active account in Partner Center to merge their account with yours, this information is managed on the **Account merge** page. Look up the PartnerID for the company you'd like to merge with yours, view current mergers, and send invitations to companies. Accept or reject an invitation to merge your company account into another company's account here. For details, see [Merge your partner account with another partner account](merge-accounts.md).

## Payout and tax

The Payout and tax page contains your payout and tax details, including **Bill to** information, **PO number**, tax ID information for your company, VAT ID number if you have one, and the currency you use.

## User management

What you work on in Partner Center and the areas you're able to update or see depends on your role and the permissions attached to that role. For example, if you aren't an Incentives admin, you can't change anything on the Incentives pages even though you may be able to view the data. Learn more about [roles and permissions](permissions-overview.md)

### Update preferred email

To update your preferred email to receive Partner Center notifications:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select the **Action Center notification** (bell) icon from the top right.
1. Select [**My preferences**](https://partner.microsoft.com/dashboard/actioncenter/mypreferences).
1. Edit **Contact details** > **Email address** for notifications.
1. Select **Change**, update the email address, and select **Save**.

### Update contact information for overdue notices

Overdue invoice and late payment notices are sent to your Alternate email address, not your Preferred email address. You can update the Alternate email address in the Azure portal.

1. Sign in to the [Azure portal](https://portal.azure.com).
1. Find your profile in the Azure AD.
1. In the **Alternate email** field, enter your organization's email address with the "yourorganization.com>>" domain, as shown below.

> [!NOTE]
>We do not send emails to the "onmicrosoft.com" domain.

:::image type="content" source="media/account-settings/update-email.png" lightbox="media/account-settings/update-email.png" alt-text="Screenshot showing where to enter an Alternate email address.":::

### Find your user role

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) select the **Settings** (gear) icon.
1. Select the **Account settings** workspace, then **Overview**.
1. On the overview page, you see your personal information as it pertains to your work and your permissions.
1. Select **View permissions** next to Partner Center permissions to see all the roles you've been assigned and the permissions those roles provide.

## Programs in which you're enrolled

The work you do to manage your Partner Center account relates to the specific programs you're enrolled in and the user roles and permissions you've been assigned in Partner Center.

### Enrolling in programs

There are many Partner Center programs available. Each program has different requirements your company needs to meet before it can enroll in that program.

To learn about enrolling in Partner Center programs, see the following partial list:

- [Commercial Marketplace program](/azure/marketplace/partner-center-portal/create-account)
- [Microsoft AI Cloud Partner Program membership benefits](mpn-overview.md)
- [Cloud Solution Provider program](./enrolling-in-the-csp-program.md)
- [Office Store](https://partner.microsoft.com/dashboard/account/v3/enrollment/introduction/office)

To learn more about enrolling in Partner Center programs, see also [Partner network resources](https://partner.microsoft.com/).

## Next steps

- [Update your partner profile](update-your-partner-profile.md)
- [Create user accounts and set permissions](create-user-accounts-and-set-permissions.md)
- [Assign users roles and permissions](permissions-overview.md)
