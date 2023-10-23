---
title: Pay out and tax profiles in Partner Center
ms.topic: how-to
ms.date: 09/16/2022
description: Create and manage your payout and tax profile so you can get paid for your incentives work. Includes creating, managing, and using different profiles.
ms.service: partner-dashboard
ms.subservice: partnercenter-incentives
author: shikhakohli
ms.author: shkohli
ms.custom: references_regions
---

# Create and manage incentives payout and tax profiles in Partner Center

**Appropriate roles**: Incentives admin | Account admin | Global admin

Before you can receive payment for your incentive programs for a particular Microsoft AI Cloud Partner Program location, you must complete your enrollment by associating a valid payout and tax profile with the program and Microsoft AI Cloud Partner Program location. Microsoft uses that payout and tax profile to issue payments. You might be allowed to use an electronic bank transfer or a credit note for payment, depending on the rules of the incentive program.

## Roles, currencies, and multiple Microsoft incentive programs

It's important to understand the following information before you get started with your payout and tax profile.

### Roles and permissions

You must be an Incentives admin to enter bank and tax information for incentive payments. (Incentives *users* can view incentives earnings, payment details, and reports, but they can't edit bank and tax details.)

To request Incentives admin permissions, contact your MPN admin or Global admin.

To find out who in your company has the MPN admin or Global admin roles, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select the **Settings** (gear) icon.
2. Select **Account settings**.
3. Select **User Management** and filter on **MPN Admin** or **Global admin**.

If you're an MPN admin or Account admin, you can assign yourself or a colleague the Incentives admin role.

To assign yourself or a colleague the Incentives admin role, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select the **Settings** (gear) icon.
2. Select **Account settings**.
3. Select **User Management**.
4. Locate your name or your colleague's name in the list of admins, and select the Incentives admin role to be assigned.

For more information about creating users and assigning roles, see [Create user accounts](create-user-accounts-and-set-permissions.md) and [Assign roles and permissions to users](permissions-overview.md).

### Choose your disbursement currency

Incentive payments are made in the currency you selected when you set up your payment profile. Payments are calculated using an exchange rate that's set monthly by Microsoft. You're responsible for any changes in value due to the currency selected.

### Using different profiles for different Microsoft programs

If your company is enrolled in multiple incentive programs, you can use the same payment account for all of them, or you can choose to use different payment accounts for different programs.

## Create and manage payout and tax profiles in Partner Center

The following sections walk you through the process of creating and managing payment and tax profiles in Partner Center.

> [!IMPORTANT]
> You must be an Incentive admin to create or manage payment and tax profiles in Partner Center. Incentive roles must be assigned to each Microsoft AI Cloud Partner Program location under each incentive program. For more information about how to add Incentive admins in Partner Center, see [Create user accounts](create-user-accounts-and-set-permissions.md).

## Access the payout and tax section in Partner Center

To access the payout and tax section in Partner Center:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) using your Azure Active Directory (Azure AD) account (company account), or the appropriate email address if one was assigned.

   * Multiple domains can be registered within one Azure AD account. Contact your Global admin to determine which domains are associated.
   * If you're only able to sign in with the @onmicrosoft.com domain and you need extra domains, contact your Account admin to add extra domains to the Azure AD account.
   * If you're prompted to select **Work or school account** or **Personal Account**, select **Work or school account**.

2. Select the **Settings** (gear) icon, and then select **Account settings**.

3. In the **Account settings** menu, select **Payout and tax**.

## Assign payout and tax profiles to individual programs

To assign payout and tax profiles to individual programs:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select the **Settings** (gear) icon.

2. Select **Account settings**, then select **Payout and tax section**, and then **Payout and tax profile assignment**.

   A list of your programs is displayed. Select the arrow next to a program to see profile details.

3. In the **Tax Profile** dropdown menu, select the tax profile you want, or select the option to create a new profile. When you select the option to create a new profile, you're redirected appropriately.  Select **Continue** in the pop-up window. The process for creating a new tax profile is provided below.

4. Select **Payment method**.

   If you selected **Electronic bank transfer** as your payment method, select the payment profile you want, or select the option to create a new profile. When you select the option to create a new profile, you're redirected appropriately. Select **Continue** in the pop-up window. The process for creating a new payment profile is provided below.

   If you selected **Credit Note** as your payment method, then complete the verification. Verification confirms that the referenced SAP number belongs to your organization.

   > [!NOTE]
   > If there are multiple Microsoft business entities listed, you must select a payment profile for each entity.
   >
   > Payment method availability is dependent on the rules of the incentive program.

   If your PartnerLocationID is paid by a local Microsoft subsidiary for a particular incentive program and allows an LRD (limited risk distributor) credit memo as the payment method, then your payment profile will be pre-populated with the LRD Credit Note payment method. On the LRD credit note payment method row for the respective incentive program and location PartnerID, **Confirmed** or **Verification Needed** appear as the status in the payment profile section.

   Select **Verification needed** to confirm and verify the CSP tenant ID details that are associated with the location Microsoft AI Cloud Partner Program and the payment method to receive the credit note payment. In the **Credit Note Details** dialog box, review and verify that the CSP Tenant ID and details provided are correct. If you're presented with more than one tenant ID, carefully select the CSP tenant ID on which you want to receive payments. Next, select **Confirm** to acknowledge that your company details are correct, and that the incentive payment should be made to the CSP tenant ID that you selected.

   If the status is **Confirmed**, the assignment of the CSP tenant ID has been completed, and no further action is required. You can select **Confirmed** to see the details of the assignment.

   In countries/regions that require partners explicitly to request to apply a tax exemption, you can apply tax exemption next to the tax profile in the tax profile section of the incentive program and location MPN. Checking this box applies tax exemption benefits to your incentive credit note.

   Currently, the LRD Credit Note payment method is available only for partners for the Microsoft Commerce Incentive program and Campaigns Incentive program in the following countries/regions:

   * Australia
   * Austria
   * Belgium
   * Canada
   * Denmark
   * Finland
   * France
   * Germany
   * Netherlands
   * New Zealand
   * Norway
   * Sweden
   * Switzerland
   * United Kingdom
  
   If you're a direct-bill partner or indirect provider in these countries/regions enrolled for the MCI program or the Campaigns program and you don't see LRD credit note as the available payment method, then confirm that your tenant ID is associated with the relevant partner Microsoft AI Cloud Partner Program location account. For more information, see [how to update your organization profile](update-your-partner-profile.md).

5. Select the currency.

6. When you've completed all of the payment fields, select **Submit**.

## Set up a default bank profile

You can set up default bank profiles and assign them to Microsoft AI Cloud Partner Program locations. These default profiles are used by Microsoft for subsequent enrollments for that Microsoft AI Cloud Partner Program location.

To set up a default bank profile, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select the **Settings** (gear) icon.

2. Select **Account settings**, then select **Payout and tax**, and then **Payout and tax profiles**.

3. Select **Manage default profiles** under the **Payment profiles** section.

4. To create a default bank profile, select **Add a default bank profile**.

5. Select a bank profile from the list of available bank profiles of your company. Select the currency to be used with this bank profile. Select the list of Microsoft AI Cloud Partner Program locations for which you want this default profile to apply.

6. Select **Done** when you complete the selections. (The **Done** button can't be selected until all required fields have been completed.)

    > [!NOTE]
    > The same bank and currency pairing can be applied to multiple locations. If the location Microsoft AI Cloud Partner Program has been assigned a default profile and currency combination once, it no longer appears in the location dropdown for future default profile assignments. If the default selection is deleted, the location Microsoft AI Cloud Partner Program reappears for future default profile assignments. Each bank profile and currency combination is added as an unique, editable row.

7. After all the required changes have been made, select **Save**.

## Create your bank profile

Bank profiles are created at a company level. Doing so allows one bank profile to be assigned across multiple PartnerIDs and incentive programs within a company. There might be exceptions when applying a banking profile to different countries/regions, because different banking and tax rules might apply.

> [!NOTE]
> On the pages on which you enter this information, fields with an asterisk are required. If you need more information about a field, select its information icon.

To create your bank profile, use the following steps:

1. On the **Details** page, complete the following fields:

   * **Profile name:** Enter a unique name to identify the payment profile.
   * **Bank account location:** The country/region in which your company's bank is located.
   * **Payment method:** The preferred payment method for Partner Center is electronic bank transfer.

2. Select **Next**.

3. On the **Bank account** page, enter your information.

   Fields shown on this page vary by country/region.

4. Select **Next**.

5. On the **Beneficiary** page, enter the appropriate information.

   The beneficiary is the person in your company that the bank should contact if they need to discuss your account.

6. Select **Finish** after you've entered the required information, and then select **Confirm** to create your bank profile.

   You're redirected to the **Payout and tax profiles** page. The status of your new profile is **Pending Microsoft validation** until the validation is completed. Verification can take up to 48 hours.

   When validation is complete, your profile status is either **Approved** or **Action required**. If the status is **Action Required**, repeat the preceding steps to provide the required information.

## Create your tax profile

Use the following procedure to provide Microsoft with the tax information required for your organization. The pages in the tax information entry section are dynamic and vary according to your country or region. If you need help with identifying the correct tax information, contact the appropriate government sources in your country/region.

For partner companies in the United States, if you require information on completing IRS forms W-8 or W-9, you can get more information by downloading the information at the following addresses:

* IRS form W-8: [http://www.irs.gov/pub/irs-pdf/iw8.pdf](http://www.irs.gov/pub/irs-pdf/iw8.pdf)
* IRS form W-9: [http://www.irs.gov/pub/irs-pdf/iw9.pdf](http://www.irs.gov/pub/irs-pdf/iw9.pdf)

> [!IMPORTANT]
> Never enter personal information. Be sure to only enter information about your company.

To create your tax profile:

1. On the **Business Profile** page, complete the required fields and then select **Next**.

2. On the **Setup** page, select the option that applies to your company.

   * Select the option on the left if your company is incorporated in the United States only, or if this profile is for an individual.
   * Select the option on the right if your company is incorporated outside of the United States, and then select your country/region from the list.

3. Select **Next**.

4. On the **Tax status** page, enter the required information, and then select **Next**.

   Fields on this page vary by country/region.

5. On the **Additional documentation** page, enter the required fields and then select **Next**.

6. Select **Browse** to upload any documents required by your country or region.

   * When the document name is shown, select **Upload**.
   * If you need to remove the document, select **Remove**.

7. To save and continue, select **Finish**.

8. Select **Confirm** on the pop-up message.

   You're returned to the **Payout and tax setup** page.

## Update expired tax profiles

To update expired tax profiles, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select the **Settings** (gear) icon.

2. Select **Account settings**, expand the **Payout and tax** section, and then select **Payout and tax profile**.

3. Select **Tax profile**.

4. Check the column **Expiration Date** and go to the tax profile that is expired or about to expire.

5. Select **Edit**.

6. In the tax form section, update the tax forms by providing the new details.

## Next steps

- [Common questions about payouts and taxes](payout-faq.yml)
