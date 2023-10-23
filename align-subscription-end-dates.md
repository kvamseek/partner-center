---
title: Align subscription end dates in Partner Center
ms.topic: how-to
ms.date: 07/24/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Learn how to align subscription end dates to simplify subscription and billing management.
author: migolova
ms.author: migolova
---

# Align new commerce experience subscription end dates

**Applies to**: Partner Center | Partner Center for Microsoft Cloud for US Government

**Appropriate roles**: Admin agent | Billing admin | Global admin | Helpdesk agent | Sales agent

> [!NOTE]
> The new commerce experiences for license-based services includes many new capabilities. These capabilities are available to all Cloud Solution Providers (CSPs). For more information, see [new commerce experiences overview](new-commerce-license-based.md). Aligning end dates is only enabled in license-based new commerce experiences.

Starting March 10, 2022, you can ensure that new subscriptions or renewed subscriptions align with your term end dates. This capability is called **coterminosity** and is available from both the Partner Center user interface and APIs.

We've recently introduced another way to **align your charge cycle with a calendar month.** Like the corterminosity feature, you can end your subscription as close to the **end of the calendar month** as possible based on monthly, annual, or other billing terms, **not exceeding the term length.**

## Benefits of aligning end dates

As a partner, you have various benefits and reasons for aligning your subscription term end dates:

- *Add-on management*: You can terminate/renew add-on subscription at the same time as existing subscription, so you don't need to pay for an add-on subscription alone without having to use it.
- *Align subscription renewals with fiscal year*: A subscription's renewal dates can be aligned with fiscal year begin date, so that budget can be allocated accordingly each year
- *Consistent & efficient invoicing*: All subscriptions will have uniform invoicing experience and it streamlines customer billing. The billing period and charge cycle for consumption and license-based subscriptions will be consistent with a calendar-month charge cycle. Moreover, you don't need to worry about buying subscriptions on different dates because the charge cycle will always align with the calendar month, and we'll prorate the cost for you to bill your customers.
- *Flexibility for end dates*: Each group of subscriptions can have their own coterminous date.

## How to align end dates

### Align end dates in Partner Center

**Coterminosity:**

You can specify the **End date Alignment** value field while purchasing a new subscription. As a partner, you can select **View subscription end-dates** to view all subscriptions and the corresponding term end date an existing subscription will align to. Pick the end-date you want to align to from one of these existing subscriptions.

You can also set the end date alignment for an existing subscription by going to manage renewal settings and populating the **End date alignment** field, selecting from an existing subscription.

**Calendar-month charge cycle:**

You can select the **Align end date with calendar month** checkbox while purchasing a new subscription. You can also make this selection when renewing an existing subscription.

### Align end dates using the Partner Center APIs

To see valid custom term end dates for new customer subscriptions, use the [Get Custom Term End Dates API](/partner-center/developer/custom-term-end-dates). You can also calculate a custom term end date based on the example transactions above.

The *customTermEndDate* is the new field introduced in the cart APIs. You can then set the date for a new subscription purchase or by updating the subscription's renewal settings. You can find more details about *customTermEndDate* in the following API documents:

- Setting *customTermEndDate* when [purchasing a new subscription](/partner-center/develop/create-a-cart#request-sample)
- Setting *customTermEndDate* on *scheduledNextTermInstructions* when [scheduling changes](/partner-center/develop/create-scheduled-changes)
- [Cart line resources](/partner-center/develop/cart-resources#cartlineitem)
- [Partner Center API error codes](/partner-center/develop/error-codes)

When you choose to **align the subscription's charge cycle with the calendar month,** you need to use the same *ustomTermEndDate* attribute of the API. However, depending on the billing term, you need to calculate the date. For example, if you choose an annual billing term, you need to use the last day of the 11th calendar month from your purchase date.

## Setting custom term end dates

Keep the following details in mind when setting custom term end dates.

- Coterminosity is only available for license-based new commerce subscriptions. This feature doesn't cover other types of product SKUs available in Partner Center (for example, third-party, Azure reservations, or software subscriptions). Trial subscriptions are also excluded.
- Coterminosity is designed to enable partners to align a new subscription to an existing subscription end date. New subscription purchases for customers without any existing subscriptions need to respect the term of the subscription being acquired. For example, in a new customer scenario, an annual subscription purchased on 2/4/2023 can have a coterm end date, but it needs to be the last day of the term, or in this example, 1/31/2024. All dateTime values considered for coterm are in UTC.
- As a partner, you can set end dates to coterminate on any date. The user experience displays existing subscriptions listed to aid you in choosing the date are based on your customer's subscriptions only.  
- Mid-term adjustments of subscription durations aren't allowed. Changes to set a new term end date only occur following the subscription's current term.
- Subscription end dates can't be adjusted after coterminosity is turned on.
- An existing subscription can be moved in or out of coterminous subscriptions at renewal time only.
- Annual and triannual term subscriptions can't be coterminated with a monthly term subscription.
- You can coterminate add-on subscriptions to existing subscription end dates that belong to same customer/reseller. Also, existing subscriptions can be co-terminated with any add-on subscription.
- Changing seat counts for an existing subscription or transitioning subscriptions doesn't affect or change the renewal dates.
- You can coterminate after a subscription is migrated from legacy to new commerce. Coterminosity must be applied after migrating subscription to modern.
- You can decide that some subscriptions coterminate on a particular date while other subscriptions coterminate on a different date. These different end dates are sometimes referred to as **Groups**.
- Charges to partners will be prorated if the original term is reduced via a coterminous setting.  
- You can define a subscription with coterminosity before your current term ends. Partners can use the coterminosity feature custom end date before the term ends, but it gets applied only during renewal time. The first term after setting up coterminosity can be shorter than the full term to align the renew date with an existing subscription subsequent to that subscription will run for the full term only. The charges will be prorated for the first short term.
- You can only set the end dates for subscriptions you've purchased for your customers. These subscriptions don't include web direct purchased subscriptions or subscriptions from other partners.
- The custom term end date must be within the first term duration, and for **monthly term products, it cannot align with a subscription ending on the 28th, 29th, or 30th of the month, unless that date is the last day of the month.**
- Setting a coterminous date on purchasing a subscription still enables you to cancel the new subscription as long it complies with the new commerce cancellation policies.  
- You can't coterminate an annual and triannual term subscription with a monthly term subscription. A monthly term subscription can coterminate with any other subscription. Trial subscriptions are excluded.
- Your **subscription end date** should be as close to the **end of the calendar month** as possible based on monthly, annual, or other billing terms, **not exceeding the term length.**
- The subscription **charges** will be **calculated for the billable days in the calendar month,** which corresponds to your **billing period** if you **pay monthly.** The costs will be prorated to the number of billable days in the billing term **for one-time payments.**

### Examples of custom term end dates

The following examples show how the new subscription term durations are defined.

(In these examples, an *existing subscription* is a subscription a partner wants to align an end date with.)

#### Three-year-term subscription examples

**Coterminosity:**

- Existing subscription: **one year**, ending October 1, 2022
- New subscription: three years, purchased July 1, 2022
- Result: The subscription is prorated to 27 months, ending on October 1, 2024. (The next term is October 2, 2024, to October 1, 2027.)
- Existing subscription: **three-years**, ending October 1, 2022
- New subscription: three-years, purchased July 1, 2022
- Result: The subscription is prorated to three months, ending October 1, 2022. (The next term is October 2, 2022, to October 1, 2025, so both three-year subscriptions renew on October 2, 2025.)

**Calendar-month charge cycle:**

- New subscription: three-year billing term, purchased July 15, 2022
- Result: The subscription is prorated, ending on June 30, 2025. (The next term is July 1, 2025, to June 30, 2028.)

#### One-year-term subscription example

**Coterminosity:**

- Existing subscription: one-year or three-year subscription, ending October 1, 2022
- New subscription: one-year subscription, purchased July 1, 2022
- Result: The subscription is prorated to three months, ending October 1, 2022. (The next term is October 2, 2022, to October 1, 2023.)

**Calendar-month charge cycle:**

- New subscription: one-year billing term, purchased July 15, 2022
- Result: The subscription is prorated, ending on June 30, 2023. (The next term is July 1, 2023, to June 30, 2024.)

#### One-month-term subscription example

**Coterminosity:**

- Existing subscription: one-year or three-year or one-month term subscription, ending April 2, 2022
- New subscription: one-month term subscription, purchased March 2, 2022
- Result: The subscription is prorated to 27 days, ending on April 2, 2022. (The next term is April 3, 2022, to May 2, 2022.)

**Calendar-month charge cycle:**

- New subscription: one-month billing term, purchased July 15, 2022
- Result: The subscription is prorated, ending on July 31, 2022. (The next term is August 1, 2022, to August 31, 2022.)

## Next steps

- [Create a new subscription](create-a-new-subscription.md#create-a-new-subscription)
- [Scheduling changes for a subscription](create-a-new-subscription.md#scheduled-changes-for-managing-new-commerce-license-based-subscription-renewals)
