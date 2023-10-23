---
title: Verify your company profile
ms.service: partner-dashboard
ms.subservice: partnercenter-account
description: Learn how to verify your company details such as primary contact, address, and program information. You can also update your legal and billing addresses.
author: sharath-satish-msft
ms.author: shsatish
ms.topic: how-to
ms.date: 7/19/2022
ms.custom: contperf-fy21q4
---

# Verify or update your company profile information

**Appropriate roles**: Global admin | Microsoft AI Cloud Partner Program account admin

The first time you sign in to Partner Center as a Global admin, confirm that all of your company details are correct. These include primary contact, legal business name and address, and program information. If your company has more than one location, review your location data for accuracy. As the Global admin, Billing admin, or Admin agent, you'll also be able to see and update your billing and tax information.

> [!NOTE]
> You must be the Global admin to update your billing address.
> You will need to provide [security contact](security-contact.md) information if not already added while updating your profile.

Your partner profile consists of your legal business information, primary contact name and email, the programs in which your company participates, and if relevant, other companies that are now merged under your legal business. Make sure the company name and address in your legal business profile are free of spelling errors and abbreviations, and match your formal company business registration records exactly. If you're operating as a sole proprietor, you need to use your company name as your legal name.

## Locate the legal business profile

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select the **Settings** (gear) icon.

2. Select the **Account settings** workspace, then **Legal info**.

3. Review the values for **Legal business profile**, **Primary contact info**, and **Program info**.

If you've merged your other companies under your legal business, you can review that information as well.

## Update your legal business profile

> [!IMPORTANT]
>  
> - For Microsoft AI Cloud Partner Program accounts, both the Global admin and Account admin can update the legal company name.
> - For Cloud Solution Provider (CSP) Indirect reseller accounts, only the Global admin can update the legal company name.
> - Direct-bill partners and Indirect providers cannot change the legal name of their company if the account verification status is **Authorized**. If you need to change the name, you must create a [support ticket](https://partner.microsoft.com/dashboard/v2/support/servicerequests/create?stage=2&topicid=eb74583c-61b3-2124-bffc-00920e0ae772).

To update your legal company name or address:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select the **Settings** (gear) icon.

2. Select **Account settings**, then **Legal info**.

3. Select the **legal business profile** (partner or reseller) you want to update.

4. Select **Update** next to the company name/address and change the details.

5. When you select **Submit**, your legal identity will be reassessed. We only reassess information that you've changed.

6. If the verification fails, learn how to [fix the problem](verification-responses.md).

> [!IMPORTANT]
> If you are a CSP partner, you can't change the country/region associated with your legal address. Your legal address's country/region is tied to your tenant, services, and the currency you do business with. If a Global Admin/Account Admin is unable to change company name, please Contact Support and attach HAR file/PSR of the steps showing the error.
>
> To learn about Microsoft AI Cloud Partner Program country/region updates, read [MPN country/region updates](manage-locations.md#change-the-countryregion-of-a-partner-global-account).

### Update the legal business name

|Program|Who can update company name|Status when it can be updated|
|---------------------|:-------------------------------|:------------|
MPN|Global admin, Account admin|Authorized, pending, rejected|
|CSP: Indirect reseller|Global admin|Authorized, pending, rejected|

## Update your Microsoft AI Cloud Partner Program global business account

If the wrong business account was identified as the legal business during your migration from the former *Partner Membership Center* to *Partner Center*, you can change the account to the correct legal business account.

To make these updates, you need to be either the Global admin or Account admin. Learn how to [manage your Microsoft AI Cloud Partner Program Global location accounts](manage-locations.md)

## Update your PartnerID associated with your CSP account

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) as a Global admin and select the **Settings** (gear) icon. 

2. Select **Account settings**, then **Legal info**. **Account settings**. (Your Microsoft AI Cloud Partner Program and CSP credentials may be different.)

3. Select **Identifiers**.

4. Under the **CSP** section, use the **Update** link to update the PartnerID associated with your CSP Account.

## Update your CSP legal billing address

If you're the Global admin, you can change the address that appears on your invoice in your **Payout and tax profile**. You can't change the company name on your invoice because of a limitation with the invoice system.

:::image type="content" source="media/billing-profile.png" lightbox="media/billing-profile.png" alt-text="Screen capture of area where billing information is added.":::

|**Field**  |**Description**|
|---------------------|:------------------|
|Bill-to company name|The company name that appears in the *bill-to* information on your CSP invoice.  This information isn't editable in Partner Center.  To update, create a support ticket.|
|Bill-to address|The bill-to address on the CSP invoice can be updated from [Billing profile](https://partner.microsoft.com/dashboard/account/v3/accountsettings/billingprofile#commercial).|
|Bill-to contact|The billing contact details (first name, last name, primary number) for the CSP account can be updated from [Billing profile](https://partner.microsoft.com/dashboard/account/v3/accountsettings/billingprofile#commercial).|
|PO number|The purchase order number displayed on the partner invoice can be updated from [Billing profile](https://partner.microsoft.com/dashboard/account/v3/accountsettings/billingprofile#commercial).|
|Company tax ID|Businesses in some countries/regions can provide their [value-added tax (VAT) number  or local equivalent](./organization-tax-info.md). To update your Tax/VAT ID, you must be a Global admin, billing admin, or admin agent.|
|Billing currency|The billing currency for your CSP account is determined by the legal country/region of the CSP account.  This information can't be changed after the CSP account is created.|

## Next steps

- [Check on your verification status](verification-responses.md)
- [Manage Microsoft AI Cloud Partner Program locations](manage-locations.md)
