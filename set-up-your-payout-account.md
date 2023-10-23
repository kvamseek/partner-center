---
title: Set up commercial marketplace payout and tax profiles
description: Learn how to set up a payout account and fill out the necessary tax forms so you can receive money from offer sales in the commercial marketplace.
ms.topic: conceptual
ms.service: partner-dashboard
ms.subservice: partnercenter-payouts
author: mingshen-ms
ms.author: mingshen
ms.reviewer: David.Najour
ms.date: 07/31/2023
---

# Set up commercial marketplace payout and tax profiles

**Appropriate roles**: Account admin | Global admin

After you have set up your account, there are two things you need to do in [Partner Center](https://partner.microsoft.com/dashboard/home) before you can sell offers (or add-ons) in the commercial marketplace:

- [Set up your payout account](#payout-account)
- [Fill out your tax forms](#tax-forms)

If your account is registered in a market in which publishers can only submit free offers, you won't have the option to set up a payout account.

If you only plan to list free offers (and don't plan to offer in-app purchases or use Microsoft Advertising), you don't need to fill out any tax forms or set up a payout account. If you change your mind and decide that you do want to sell offers (or add-ons), you can fill out tax forms and set up a payout account then.

> [!NOTE]
> For details about how and when you will be paid for the money your offer makes, see [Getting paid in the commercial marketplace](marketplace-get-paid.md).

## Tax forms

You manage your tax profile and tax forms in the **Payout and tax** page of Partner Center. (Your organization's permissions determine which profiles and information that you see there.)

### Create or update your tax profile

You must fill out United States tax forms to sell any offer or add-ons through the commercial marketplace, regardless of your country/region of residence or citizenship.

You can fill out the required forms online when you complete your tax profile. You usually don't need to print and mail any forms.

- Publishers who satisfy certain United States residency requirements fill out a United States Internal Revenue Service (IRS) [W-9 form](https://www.irs.gov/forms-pubs/about-form-w-9).
  
- Other publishers outside the United States fill out an IRS [W-8 form](https://www.irs.gov/forms-pubs/about-form-w-8).

To create or update a tax profile in Partner Center, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select the **Settings** (gear) icon.

2. Select **Account settings**, then select **Payout and tax profile assignment**.

3. Select the program and seller ID combination for which you want to configure tax information.

4. If you want to use an existing tax profile, select it from the dropdown. Otherwise, select **Create new profile** and select **Submit**.

5. On the tax profiles page, select **Edit**.

6. Select the appropriate radio button, and select your country/region if prompted to do so. (This step determines the Microsoft business entity that will be used to make payouts on your account.)

7. Depending on your selections in step 6, you'll be prompted to provide the tax information required for your country/region.

> [!IMPORTANT]
> Countries and regions have different tax requirements. The exact amount that you must pay in taxes depends on the countries and regions where you sell your offer. See the [Microsoft Azure Marketplace Publisher Agreement](/legal/marketplace/msft-publisher-agreement) to find out for which countries/regions Microsoft remits sales and use tax on your behalf.
>
> In some countries/regions, depending on where you are registered, you might need to remit sales and use tax for your offer sales directly to the local taxing authority.
>
> Proceeds that you receive from app sales might also be taxable as income.
>
> We strongly encourage you to contact the relevant authority for your country or region that can best help you determine the right tax information for your commercial marketplace activities.

### Withholding rates

The information you submit in your tax forms determines your tax withholding rate.

Withholding applies only to sales that you make into the United States. Sales made into non-US locations aren't subject to withholding.

Withholding rates vary, but for most publishers registering outside the United States, the default rate is 30%. You have the option of reducing this rate if your country/region has agreed to an income tax treaty with the United States.

### Tax treaty benefits

If you are outside the United States, you might be able to take advantage of tax treaty benefits. These benefits, which vary from country/region to country/region, might allow you to reduce the amount of taxes that the commercial marketplace withholds.

You can claim tax treaty benefits by completing Part II of the IRS [W-8BEN form](https://www.irs.gov/forms-pubs/about-form-w-8-ben).

We recommend that you communicate with the appropriate resources in your country or region to determine whether these benefits apply to you.

> [!NOTE]
> A United States Individual Taxpayer Identification Number (ITIN) is not required to receive payments from Microsoft or to claim tax treaty benefits.

## Payout account

A payout account is the account to which Microsoft sends the proceeds from your sales.

You can use PayPal as your payout account in some markets. For more information, see [Payment thresholds, methods, and time frames](payment-thresholds-methods-timeframes.md) and [Using PayPal as a payment account](#using-paypal-as-a-payment-account) later in this article.

You can view all the payout accounts that you've entered on the Profile page.

- [Create a payment profile](#create-a-payment-profile)
- [Edit an existing payment profile](#edit-an-existing-payment-profile)

### Create a payment profile

To create a payment profile:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select the **Settings** (gear) icon.

2. Select **Account settings**, then under the **Payout and tax** heading, select **Payout and tax profile assignment**.

   > [!NOTE]
   > Because financial information is sensitive, you might be prompted to sign in again.

3. Select the payment method that you would like to configure.

4. Select an existing payment profile, or select **Create a new payment profile** to create a new profile for the chosen payment method.

### Create a bank-based payment profile

If you elected to use a bank account to receive payouts, you must complete the following process to configure your bank account.

To create a bank-based payment profile:

1. On the **Bank Profile** page, provide the required information about your bank.

2. Provide your bank account details. (Only alphanumeric characters are accepted for bank account details.)

3. Provide beneficiary details.

4. Back on the **Profile assignment** page, select the currency you want Microsoft to use when issuing payouts.

    > [!WARNING]
    > Make sure that your bank accepts the payout currency that you select.

    You must select a payment profile for each program you participate in. However, you can use the same profile for multiple programs.

5. Select **Submit** to save your changes.

   > [!NOTE]
   > It can take up to 48 hours to validate the information in your profile. When verification is complete, your **verification status** will display **Complete**.

To ensure that your payout is successful, make sure that:

- The **Account holder name** that you enter for your payout account is the exact same name associated with your bank account. For example, if your bank account name includes a middle name, include that middle name in **Account holder name**.
- Payouts are transferred directly from Microsoft to your bank or PayPal account in the currency you specify on the profile assignment page.

### Edit an existing payment profile

To edit existing payment profiles:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home), select the **Settings** (gear) icon.

2. Select **Account settings**, then under the **Payout and tax** heading, select **Payout and tax profiles**.

3. Your payment profiles are listed along with their status. Find the profile that you want to edit and select **Edit** at the far right.

> [!IMPORTANT]
> Changing your payout account can delay your payments by up to one payment cycle. This delay occurs because Microsoft must verify the account change, just as when you first set up the payout account. You still get paid for the full amount after your account has been verified. Any payments due for the current payment cycle are added to the next payment cycle. For more information, see [Getting paid in the commercial marketplace](marketplace-get-paid.md).

### Using PayPal as a payment account

In some countries and regions, you can create a payment account by entering your PayPal information. However, before choosing PayPal as a payment account option:

- Check [Payment thresholds, methods, and time frames](payment-thresholds-methods-timeframes.md) to confirm whether PayPal is a supported payment method in your country or region.
- See the following [frequently asked questions](#frequently-asked-questions-about-using-paypal-as-a-payment-method).

To create a PayPal payment profile, see [Create a PayPal payment profile](#create-a-paypal-payment-profile).

#### Frequently asked questions about using PayPal as a payment method

- **Can I use PayPal as a payment option in my country/region?**

  To find out where PayPal is a supported payment method, see [Payment thresholds, methods, and time frames](payment-thresholds-methods-timeframes.md).

- **What PayPal settings do I need to make to receive payments?**
  
  Ensure that your PayPal account doesn't block eCheck payments. This setting is managed in PayPal's **Payment Receiving Preferences** page. For more information, see [PayPal's account setup page](https://go.microsoft.com/fwlink/?linkid=2162542).

- **Does my PayPal account have to be registered in the same country/region as my Partner Center account?**

  No. When you set up a PayPal account, you can accept the default configuration. You shouldn't have any issues with other countries/regions and currencies unless you have blocked payment in some currencies. This setting is managed in PayPal's **Payment Receiving Preferences** page.

- **Do I have to accept PayPal payments manually?**
  
  No. PayPal accounts are set by default to require users to accept payments manually. That means if you don't accept the payment within 30 days, it's returned. You can change this setting by turning off *Ask Me* in PayPal's **More Settings** page.

- **What currencies does PayPal support?**
  For the current list of supported currencies, see [PayPal's support page](https://developer.paypal.com/docs/api/reference/currency-codes/).

### Create a PayPal payment profile

To create a PayPal payment profile that you can use to receive payouts:

1. On the **PayPal** page, provide the required information about your PayPal account.

2. Provide your PayPal account details. (Only alphanumeric characters are accepted for account details.)

3. Provide beneficiary details.

4. On the **Profile assignment** page, select the currency that you want Microsoft to use when issuing your payouts.

5. You must select a payment profile for each program you participate in. However, you can use the same profile for multiple programs.

6. Select **Submit** to save your changes.

### Other requirements for certain countries/regions

In some countries and regions, more requirements for payout accounts must be met.

Note the following requirements if you're a resident of:

- [Pakistan](#pakistan)
- [Russia](#russia)
- [Ukraine](#ukraine)

#### Pakistan

Form-R is a Pakistan banking regulatory requirement. It's used to indicate the purpose and reason for receipt of funds from abroad. Therefore, anytime that you're eligible for a monthly payout from Microsoft, you must submit Form-R to your bank before the payout can be released to your account. Contact your local bank branch for instructions about how to obtain a copy of Form-R.

You must submit a Form-R to your bank each month that you're eligible for a payout. For example, if you expect to receive a payout every month of the year, you must submit a Form-R 12 times (once each month).

After a payout has been submitted to your bank, you have 30 days to submit a Form-R. If it isn't submitted within 30 days, the funds are returned to Microsoft.

#### Russia

If you're a publisher who lives in Russia, you might need to provide documentation to your bank before your bank will deposit funds in your account. When you're eligible to be paid, Microsoft will provide you the following documentation in an email message:

- An Acceptance Certificate (AC) that has the amount of the payout being transferred to your account.
- The [Microsoft Azure Marketplace Publisher Agreement](/legal/marketplace/msft-publisher-agreement), which is a signed copy of the publisher agreement that must be countersigned.

To ensure your payout is successful, make sure that:

- The **Account holder name** entered for your payout account in Partner Center is the exact same name associated with your bank account. For example, if your bank account name includes a middle name, include a middle name in your **Account holder name**.
- Payouts are transferred directly from Microsoft to your bank account in Ruble (RUB) currency.
- Bank information entered in Partner Center in Latin characters is translated to Cyrillic characters.
- Payouts are made to a bank account and not to a bank card.

#### Ukraine

If you're a publisher who lives in Ukraine, you might need to provide documentation to your bank before your bank will deposit funds into your account. When you're eligible to be paid, Microsoft will provide you with the following documentation in an email message:

- An Acceptance Certificate (AC) that has the amount of payout being transferred to your account.
- The [Microsoft Azure Marketplace Publisher Agreement](/legal/marketplace/msft-publisher-agreement), which is a signed copy of the publisher agreement that must be countersigned.
- An Amendment Agreement (AA), which is a document that can be used by your bank to help identify your payout funds.

Microsoft provides all three documents when attempting your first payment. For any subsequent payouts, you'll only receive the Acceptance Certificate. Retain the Microsoft Azure Marketplace Publisher Agreement and Amendment Agreement documents in case you need them to receive future payouts from your bank.

## Next steps

[Getting paid in the commercial marketplace](marketplace-get-paid.md)
