---
title: Link billing account and profile to Partner Center account
ms.topic: article
ms.date: 07/26/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-account
description: DUring the migration of MCPP purchases to Microsoft's New Commerce platform (NCE), you need to link your Partner Center account to either the existing Microsoft billing account and billing profile or create a new billing account and profile.
author: amitpandey1858
ms.author: pandeyamit
---

# Link billing account and profile to Partner Center account

**Appropriate roles**: Global admin

Microsoft AI Cloud Partner program purchases have been migrated to Microsoft's New Commerce platform (NCE), which offers a unified purchasing experience across Microsoft products such as Office and Azure, in addition to membership purchases. Partner accounts will transition from the existing payment platform to Microsoft's modern commerce payment platform.

As part of this migration, it's necessary for the Global admin to complete this process to make any purchases after **July 2023**. During this process, you can either link your Partner Center account to either the existing Microsoft billing account and billing profile or create a new billing account and profile.

## Billing account

The billing account represents an agreement that a customer accepts to use Microsoft products and services. It contains one or more billing profiles. You use your billing account to manage invoices, payments, and track costs. A billing account contains one or more billing profiles that let you manage your invoices and payment methods. Each billing profile contains one or more invoice sections that let you organize costs on the billing profile's invoice.

The following diagram shows the relationship between a billing account, billing profiles, and invoice sections.

:::image type="content" source="media/account-settings/billing-account-profiles-invoice-sections.png" lightbox="media/account-settings/billing-account-profiles-invoice-sections.png" alt-text="Shows a flowchart with a billing account on top. The billing account has two billing profiles underneath it. Each billing account has an invoice and payment methods associated with it. Under the billing profile are multiple invoice sections, each section has multiple Azure subscriptions.":::

Roles on the billing account have the highest level of permissions. By default, only the user who created the billing account can access the billing account. These roles should be assigned to users that need to view invoices, and track costs for your entire organization, for example, your finance or IT managers. For more information, see [billing account roles and tasks](/azure/cost-management-billing/manage/understand-mca-roles#billing-account-roles-and-tasks).

## Billing profile

The billing profile represents an agreement that a customer accepts to use Microsoft products and services. It contains one or more billing profiles. Use a billing profile to manage your invoice and payment methods. A monthly invoice is generated at the beginning of the month for each billing profile in your account. The invoice lists charges for all purchases from the previous month.

A billing profile needs to be created for your billing account. It contains one invoice section by default. You may create more sections to easily track and organize costs based on your needs whether it's per project, per department, or per development environment. You'll see these sections on the billing profile's invoice reflecting the usage of each subscription and purchases you've assigned to it.

Roles on the billing profiles have permissions to view and manage invoices and payment methods. Assign these roles to users who pay invoices, for example, members of the accounting team in your organization. For more information, see [billing profile roles and tasks](/azure/cost-management-billing/manage/understand-mca-roles#billing-profile-roles-and-tasks).

## Link billing account and billing profile to Partner Center account

For Membership purchases, you need to link a billing profile and corresponding billing account to your Partner Center account. You can either reuse your existing Microsoft billing account and profile, or create a new billing account and profile and link it to your Partner Center account.

### Prerequisites

To link a billing account and profile to your Partner Center account, you need the following:

1. The user should be a global administrator.
1. The Partner Center account should be in an **Active** state.

## Create a new Microsoft billing account and profile

1. You'll receive an email from Microsoft and in-product notification that prompts you to link your MCPP Partner Center account to the Microsoft billing profile. Select **Link Microsoft billing profile**.

   :::image type="content" source="media/account-settings/link-partner-center-account-to-microsoft-billing-profile.png" lightbox="media/account-settings/link-partner-center-account-to-microsoft-billing-profile.png" alt-text="Screenshot of an email about linking a partner account to a Microsoft billing profile.":::

1. Once in the Account settings workspace, select **Start**.

   :::image type="content" source="media/account-settings/billing-profile-mcpp-purchases-have-been-migrated.png" lightbox="media/account-settings/billing-profile-mcpp-purchases-have-been-migrated.png" alt-text="Screenshot of the Billing profile screen with an alert: MCPP purchases have been migrated to Microsoft's New Commerce platform (NCE). There are no billing accounts or profiles linked to the MCPP account.":::

1. Select **Create new billing account**.

   :::image type="content" source="media/account-settings/select-billing-account-create-new-billing-account.png" lightbox="media/account-settings/select-billing-account-create-new-billing-account.png" alt-text="Screenshot of the Select billing account flyout from the Billing profile page.":::

1. Update the details of your billing account. Some information, like your legal profile data, are prefilled by default. Select **Save**.

   :::image type="content" source="media/account-settings/create-new-billing-profile.png" lightbox="media/account-settings/create-new-billing-profile.png" alt-text="Screenshot of the Create new billing profile flyout, under Select billing account, under the Billing profile page.":::

1. Select **Next** to proceed to enter billing profile details. The billing profile is created under the previous billing account.

   :::image type="content" source="media/account-settings/select-billing-account-select-existing-account.png" lightbox="media/account-settings/select-billing-account-select-existing-account.png" alt-text="Screenshot of the Select billing account flyout, under the Billing profile page.":::

1. Select **Create new billing profile**.

   :::image type="content" source="media/account-settings/select-billing-profile-no-existing-billing-profiles.png" lightbox="media/account-settings/select-billing-profile-no-existing-billing-profiles.png" alt-text="Screenshot of the Create billing profile flyout, with no billing account selected.":::

1. Enter a billing profile name, then select **Save.**

   :::image type="content" source="media/account-settings/select-billing-account-create-new-billing-profile.png" lightbox="media/account-settings/select-billing-account-create-new-billing-profile.png" alt-text="Screenshot of the create new billing profile prompt.":::

1. The billing profile details get saved. Select **Next** to move to review page.

   :::image type="content" source="media/account-settings/select-billing-profile-with-profile-selected.png" lightbox="media/account-settings/select-billing-profile-with-profile-selected.png" alt-text="Screenshot of the Select billing profile window.":::

1. Review the details of the billing account and profile that you entered. Check the box to confirm acceptance of the Microsoft Customer Agreement (MCA), then select **Finish**.

   :::image type="content" source="media/account-settings/link-billing-account-profile-finish.png" lightbox="media/account-settings/link-billing-account-profile-finish.png" alt-text="Screenshot of the Link billing account and profile flyout, with a billing account selected, and with Finish highlighted.":::

1. The billing account and profile get created and linked to your Partner Center account successfully. MPN Admin can continue with the Membership purchases on the Membership page.

    :::image type="content" source="media/account-settings/billing-profile-mcpp-successfully-linked.png" lightbox="media/account-settings/billing-profile-mcpp-successfully-linked.png" alt-text="Screenshot of the billing profile page, with a message saying the MCPP account is successfully linked.":::

## Reuse the existing Microsoft billing account and profile and link to your Partner Center account

1. You would receive an email and in-product notification with a link to start the linking of billing account and profile. Select the link to land on the **Billing profile** page in Partner center.

    :::image type="content" source="media/account-settings/link-email.png" lightbox="media/account-settings/link-email.png" alt-text="Screenshot of the linked email.":::

1. Select **Start**.

    :::image type="content" source="media/account-settings/select-start.png" lightbox="media/account-settings/select-start.png" alt-text="Screenshot showing the start button selected.":::

1. Select the billing account that you want to link with your Partner Center account, and select **Next**. If you want to see the list of billing profiles under a billing account, select the billing profile dropdown. If you want to see more details around a billing profile, select **View details** (this will redirect you to Azure portal).

    :::image type="content" source="media/account-settings/select-billing-account.png" lightbox="media/account-settings/select-billing-account.png" alt-text="Screenshot of the select billing account screen.":::

1. Select the billing profile under the selected billing account and select **Next**.

    :::image type="content" source="media/account-settings/select-billing-profile.png" lightbox="media/account-settings/select-billing-profile.png" alt-text="Screenshot of the select billing profile screen.":::

1. Review the details of the billing account and profile you selected. Check the box to confirm acceptance of the MCA. (If you have already signed MCA in the past for the selected billing account, you need not sign it here again. The checkbox would be disabled.) Select **Finish**.

    :::image type="content" source="media/account-settings/select-finish.png" lightbox="media/account-settings/select-finish.png" alt-text="Screenshot of the finish button on the link billing account and profile screen.":::

1. The billing account and profile get linked to your Partner Center account successfully. The Microsoft AI Cloud Partner Program Admin can continue with the membership purchases on the **Membership** page.

    :::image type="content" source="media/account-settings/account-settings-billing-profile.png" lightbox="media/account-settings/account-settings-billing-profile.png" alt-text="Screenshot of the account settings billing profile screen.":::

## Change the billing account and profile linked to your Partner Center account

If you want to change an existing billing account and/or billing profile linked to your Partner Center account to another billing account and/or profile, you can do so on the **Billing profile** page. After the change, all your subsequent purchases would start reflecting on your new billing profile.

1. On the **Billing profile** page, select **Change billing account** if you want to change the billing account linked to your Partner Center account. If you want to change only the billing profile under the billing account linked to your Partner Center account, select **Change billing profile**.

    :::image type="content" source="media/account-settings/start-linking-billing-account.png" lightbox="media/account-settings/start-linking-billing-account.png" alt-text="Screenshot of the account settings billing profile screen with cursor on change billing account button.":::

1. Select the billing account that you want to link with Partner Center account from the existing list for your tenant. Select **Next**. (You can also create a new billing account and link it. If you want to change billing profile, you'll land directly on the **Select billing profile** page.)

    :::image type="content" source="media/account-settings/start-linking-billing-account-select.png" lightbox="media/account-settings/start-linking-billing-account-select.png" alt-text="Screenshot of the account settings billing profile screen with select billing account panel open.":::

1. Select a billing profile from the existing list under the billing account. Select **Next**. (You can also create a new billing profile under the selected billing account and link it. If you already have a billing profile without a payment instrument, you need to reuse the same, you can't create a new billing profile.)

    :::image type="content" source="media/account-settings/start-linking-billing-account-select-profile.png" lightbox="media/account-settings/start-linking-billing-account-select-profile.png" alt-text="Screenshot of the account settings billing profile screen with the select billing profile panel open.":::

1. Review the details of the billing account and profile you selected. Check the box to confirm acceptance of the MCA (if you have already signed MCA in the past for the selected billing account, you need not sign it here again. The checkbox would be disabled). Select **Finish**.

    :::image type="content" source="media/account-settings/link-billing-account-profile.png" lightbox="media/account-settings/link-billing-account-profile.png" alt-text="Screenshot of the account settings billing profile screen with the link billing account and profile panel open.":::

1. The billing account and profile get linked to your Partner Center account successfully. The Microsoft AI Cloud Partner Program Admin can continue with the membership purchases on the **Membership** page.

    :::image type="content" source="media/account-settings/added-successfully.png" lightbox="media/account-settings/added-successfully.png" alt-text="Screenshot of the account settings billing profile page.":::
