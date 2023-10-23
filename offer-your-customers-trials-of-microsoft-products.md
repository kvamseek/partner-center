---
title: Offer customers trials of Microsoft products
ms.topic: article
ms.date: 09/09/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Let customers try Microsoft subscription products. Sign up for these free trials in the catalog just like many other online services.
author: migolova
ms.author: migolova
---

# Give your customers free trials of Microsoft products

**Appropriate roles**: Global admin | User management admin | Sales agent

A good way to introduce customers to new Microsoft products is to offer 30-day free trials.

You can sign up for the trials in the catalog just as you sign up for many other online services.

All partners can participate.

## Available trial offers

You can find all of your outstanding trial offers on the **Customer** page. This page lists all subscriptions, including free trials and paid subscriptions. (This feature isn't available in China.)

Each customer is entitled to one free trial for each available offer. For example, they can get one free trial for Microsoft 365 Business Standard and one free trial for Office 365 E3. However, if the customer already owns the offer, they can't use a free trial for that offer.

### Available products

Free trials are available for the more most comprehensive and popular license-based offers. New trial offers may be introduced on a monthly basis.

Partners can find  trials in the monthly price list on the **Pricing and offers** page in Partner Center. Trial offers have *TRIAL* listed in the price list **Secondary License Type** column.

There are **no free trials** for government offers, education offers, or add-on offers.

## Licenses for free trial offers

All free trials provide 25 licenses.

- You can add more licenses to the subscription after the trial is converted to a paid subscription.
- Trial licenses should be assigned to users in the same way that paid services license are assigned.
- You can't change the number of licenses during the trial.
- You can't add or remove licenses during the free trial.

## Sign customers up for trials

To get a trial for your customer in Partner Center, use the following steps:

1. From **Sell** on Partner Center, go to **Catalog**.
2. In the catalog, from **Billing frequency**, select **Trial offer**.

   Doing so enables only free trials to appear and disables other offers that aren't free. Trials appear on the **Trials** tab in the catalog.
3. Select the free trial you want to offer and then select **submit**.

   All trials are for 30 days, during which you won't be billed.

   You can convert a free trial  to a paid subscription at any time during the trial.

## Converting trials to paid subscriptions

A free trial isn't automatically converted to a paid subscription for traditional offers. You must convert a free trial into a paid subscription yourself. You can do so [in Partner Center](#convert-trials-using-partner-center) or [using the Partner Center APIs](#convert-trials-using-apis).

If a free trial isn't converted into a paid subscription within 30 days, it [expires](#expiring-offers).

Free trials can't be extended.

> [!NOTE]
> Customer free trials for the Cloud Solution Provider (CSP) program can't be converted to another program tenant (such as EA, Open, or MOSP).

### Convert trials using Partner Center

To convert trials to paid subscriptions in Partner Center, use the following steps:

1. Go to the customer's subscription page, and select the free trial.
2. Select **Convert trial to paid subscription**.
3. Enter the desired license quantity and billing frequency, and select **Apply**.

   Billing for the paid subscription begins on the conversion date.

   The subscription auto-renews 12 months from the conversion date.

### Convert trials using APIs

You might need to alter your APIs to accommodate the conversion of a free trial to a paid subscription. For more information, see the following developer documentation:

- [Convert a trial subscription to paid](/partner-center/develop/convert-a-trial-subscription-to-paid)
- [Get a list of trial conversion offers](/partner-center/develop/get-a-list-of-trial-conversion-offers)

### Trials without conversions

- Not all trials can be converted to paid subscriptions.
- Partners can use a trial that can't be converted until the expiration date.
- Partners can purchase compatible offers that support the same services as the trial offer. Those offers should be purchased before the trial expires to ensure that the newly purchased offers' services align with the trial's services.

|**Trial**   |**Compatible Small Business offers**   |**Compatible Enterprise offers**   |
|----------------------------|:---------------------------------|:------------------------------------------|
|Microsoft Teams Commercial Cloud (User Initiated) Trial   |- Microsoft 365 Business Basic <br>- Microsoft 365 Business Standard <br>- Microsoft 365 Business Premium   | - F3 (formerly F1) <br> - Office 365 for Enterprise (E1, E3, and E5) <br> - Microsoft 365 F1/F3 <br> - Microsoft 365 Enterprise (E3)   |

> [!NOTE]
> The preceding offers have similar service plans with similar functionality, however there might be some differences between the offers.

### Expiring offers

You won't be notified of expiring offers. You can track upcoming expiration dates using the **Customer** view at Partner Center or by querying the API. It's a good idea to monitor these dates frequently so you can take the appropriate follow-up actions with customers as they approach a decision point.

After a trial expires, a customer who attempts to sign in to that trial will see an expiration message. Their data in accordance with data retention standards. After you purchase a new subscription with the same service plans, your customer's data can be accessed again from the newly activated subscription.

## Converting new commerce trials to paid subscriptions

For new commerce license-based offers, your free trial auto-renews into the equivalent paid subscription after 30 days.

> [!IMPORTANT]
> To convert a free trial into a paid subscription, **auto-renew must be turned on**.

If partners don't want a trial subscription to convert to a paid subscription by default, they can turn off auto-renew so the trial will expire at the end of the trial period.

There are two ways to convert a trial to a new paid subscription: [Immediate conversion](#immediate-conversion) and [Scheduled conversion](#scheduled-conversion).

#### Immediate conversion

- When doing an *immediate conversion*, you can convert a free trial to a paid subscription at any time before the end of the 30-day trial period.
- When doing an immediate conversion, all 25 seats (at minimum) must be converted to the new paid subscription.
- Partners can add more than 25 seats during conversion, but reducing the number of seats isn't allowed.
- Changes go into effect immediately.

#### Scheduled conversion

- When doing a *scheduled conversion*:
  - You can modify billing term and frequency.
  - You can choose the number of seats that you want to convert.
  - Changes go into effect automatically, as soon as the trial period ends.

> [!NOTE]
> At the end of the 30-day trial period, 25 seats are automatically converted to the new paid subscription, with a one-year commitment and monthly billing.

- Trial subscriptions, when automatically converted to full commercial subscriptions,  have the standard seven-day cancellation period.
  - Within the first seven days, partners can *cancel* the licenses and be refunded the full amount minus the prorated amount for the days the subscriptions were used. For more information about NCE cancellation, see [Cancel a subscription](create-a-new-subscription.md#cancel-a-subscription).
  - Within the first seven days, partners can *decrease the number* of licenses and be refunded the full amount minus the prorated amount for the days the subscriptions were used. For more information, see [Increase or decrease licenses in new commerce license-based subscriptions](create-a-new-subscription.md#increase-or-decrease-licenses-in-new-commerce-license-based-subscriptions).
  - If more than seven days elapse after conversion, partners can't cancel licenses or decrease the number of licenses until the next cancellation window at renewal.

Partners can also convert trials to existing paid subscriptions. In this scenario, the existing subscription must be a subscription that is eligible for the trial conversion. If so, the trial seats will be added to the existing subscription and the end date will remain the same for the existing paid subscription.

> [!NOTE]
> To convert a free trial to an existing paid subscription, the end date of the existing subscription must occur on the same day or after the end date of the free trial.

When partners convert a trial to a new paid subscription, they can choose to convert to the same paid SKU or upgrade to a higher SKU.

If you want to convert your trial to a paid subscription before the end of the trial period, you can do so using Partner Center APIs or in Partner Center itself using the following steps.

### Convert new commerce trials using Partner Center

To **immediately convert** new commerce trials to paid subscriptions using Partner Center, use the following steps:

1. Go to the customer's subscription page, and select the free trial.
2. Select **Convert trial to paid subscription**.
3. Choose the paid equivalent and then select **Submit**.

   Billing for the paid subscription begins on the conversion date, and the subscription auto-renews 12 months from the conversion date.

To **schedule** trial conversions to take place automatically at the end of the trial period, use the following steps:

1. In Partner Center, go to the customer's subscription page and select the free trial.
2. Ensure that **Auto-renew** is enabled.
3. Select **Manage renewal**.
4. Make the updates you want for the conversion and then select **Submit**.

   Billing for the paid subscription begins on the conversion date. The subscription auto-renews 12 months after the conversion date.

> [!NOTE]
> Customer free trials for the Cloud Solution Provider (CSP) program can't be converted to another program tenant (such as EA, Open, or MOSP).

Trial conversions must be managed by partners. There isn't any subscription-based alerting in Partner Center to let partners know when a trial is expiring.

> [!NOTE]
> On conversion to a new subscription, subscription duration defaults to one-year, and the billing cycle defaults to a monthly plan.

## Billing

Annual billing and free trials are the same in both the public cloud and sovereign clouds (for example, Azure Government, Azure Germany, and Azure China 21Vianet). The only difference is the trial SKUs available at the time of launch.

### Billing for free trials

- The subscription start date is based on the conversion date.
- Free trials can be used for both monthly and annually billed subscriptions.
- Default conversion settings are a term of one year and a monthly billing cycle.
- You can select the billing frequency when you convert the trial to a paid subscription.
- If a free trial is converted to a paid offer with *annual* billing, the subscription renewal date is 12 months after the conversion date.
- If a free trial is converted to a paid offer with *monthly* billing, the subscription renewal date will be 12 months from the billing date following the conversion date.

### Legacy invoices

You won't see free trials listed in your invoice or license-based reconciliation file.

A free trial appears on your invoice and license-based reconciliation file only after you convert it to a paid subscription.

The converted subscription appears in the same way as any new subscription.

### New commerce invoices

You won't see free trials listed in your invoice, but you can find them in your reconciliation file by checking the *ProductQualifiers* attribute in the reconciliation file.

### Incentives

Free trials don't affect incentives.

## Support

For support for free trials, submit a service request through Partner Center.
