---
title: Billing for one-time and recurring purchases in new commerce
ms.topic: article
ms.date: 11/8/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-billing
description: New commerce billing examples from the Partner Center for one-time and recurring purchases.
author: sodeb
ms.author: sodeb
---

# Billing scenarios for one-time and select recurring purchases in new commerce experience

**Appropriate roles**: Admin agent | Billing admin | Helpdesk agent | Sales agent

> [!NOTE]
> For a list of legacy billing scenarios, see [Common billing scenarios for legacy CSP program partners working in Partner Center](common-billing-scenarios.md).

## What is an NCE billing cycle or billing period?

A [new commerce experience (NCE)](https://partner.microsoft.com/membership/new-commerce) *billing cycle*, or *billing period*, is one full calendar month. Any product purchased within a calendar month should be invoiced based on the billing term and plan chosen at the time of purchase.

Invoices and reconciliation files become available at Partner Center or via APIs between the sixth and eighth days of the following month. For example, the billing cycle for January is from January 1 to 31. Your January invoice and reconciliation file become available between February 6 and 8.

## What is an NCE charge cycle?

An *NCE charge cycle* is how often you are charged for the product. It isn't the same as a billing period or a calendar month, and it depends on when you bought the product and how often you pay for it.

Your subscription **charge cycle days** are based on the calendar days of the month when you *buy for the first time, or pay recurring cycle charges, or renew* your subscription.

Let’s say you bought a *Microsoft Office* product on February 21, 2022, with an annual billing term and a monthly billing plan. Your first charge cycle would be from February 21, 2022, to March 20, 2022. If you made any changes to your subscription between February 21 and March 20, 2022, we would count the **charge cycle days as 28** because February has 28 calendar days *(except for leap years)*, and the February charge cycle would end on March 20, 2022. However, if you made any changes between March 21 and April 20, 2022, we would count the **charge cycle days as 31** because the monthly recurring cycle charge started from March 21, 2022, and March has 31 calendar days.

> [!IMPORTANT]
> You can coterminate subscriptions or align charge cycles with calendar months. See [*Align subscription end dates*](align-subscription-end-dates.md) for details.

## How are one-time and recurring charges calculated?

> [!IMPORTANT]
> When reconciling, the billing lines are *Charge Start Date*, *Charge End Date*, *Effective Unit Price*, *Billable Quantity*, *Billing Frequency*, *Subscription Start Date*, *Subscription End Date*, and *Amount*.
>
> You can find an explanation of these attributes in the article [*CSP one-time purchase reconciliation file fields*](modern-invoice-reconciliation-file.md).

Let’s say that on June 18, 2020, you bought 10 licenses (10 seats) of a Microsoft 365 Business Standard subscription with a monthly billing term and a price of EUR 10.08 per seat. 

Let’s look at what you can expect to see on your June billing cycle reconciliation file, which you’ll get in July. In this case, only one billing line will show the details of your subscription purchase transaction. 

| **Order Date** | **Charge Start Date** | **Charge End Date** | **Charge Type** | **Effective Unit Price** | **Billable Quantity** | **Amount** |
| -------------- | ----------------------- | ------------------- | --------------- | -------------------------- | --------------------- | ---------- |
| June 18, 2021 | June 18, 2021 | July 17, 2021 | new | 10.08 | 10 | 100.8 |

If you decide to renew your subscription, you’ll see a new transaction with the `ChargeType` **“renew”** and the `ChargeStartDate` “July 18, 2021.”

| **Order Date** | **Charge Start Date** | **Charge End Date** | **Charge Type** | **Effective Unit Price** | **Billable Quantity** | **Amount** |
| -------------- | ----------------------- | ------------------- | --------------- | -------------------------- | --------------------- | ---------- |
| July 18, 2021 | July 18, 2021 | August 17, 2021 | renew | 10.08 | 10 | 100.8 |

On the other hand, if you opt for a one-year billing term instead of a monthly billing plan, your billing line will show a charge of EUR 100.8 but with a `ChargeType` of **“cycleCharge”** until the June 2022 billing cycle.

| **Order Date** | **Charge Start Date** | **Charge End Date** | **Charge Type** | **Effective Unit Price** | **Billable Quantity** | **Amount** |
| -------------- | ----------------------- | ------------------- | --------------- | -------------------------- | --------------------- | ---------- |
| July 18, 2021 | July 18, 2021 | August 17, 2021 | cycleCharge | 10.08 | 10 | 100.8 |

Lastly, if you decide to prepay your subscription, only one billing line will show up in your June billing cycle reconciliation file.

| **Order Date** | **Charge Start Date** | **Charge End Date** | **Charge Type** | **Effective Unit Price** | **Billable Quantity** | **Total** |
| -------------- | ----------------------- | ------------------- | --------------- | -------------------------- | --------------------- | --------- |
| June 18, 2021 | June 18, 2021 | June 17, 2022 | new | 120.96 | 10 | 1,209.6 |

This makes it easier for you to keep track of how much you spend on your subscriptions.

> [!IMPORTANT]
> A *complex product like Microsoft 365 E5* combines **telecommunication (Skype)** and **non-telecommunication (Microsoft 365 E3 Office)** components into one unified product. This integration gives users a seamless experience while ensuring that telco and non-telco revenue are kept separate for billing purposes.
>
> When you purchase Microsoft 365 E5, you will find **two separate lines** for "Microsoft 365 E5" in your **reconciliation data**: one for the **telco charges** and one for the **non-telco charges.**

## How do I differentiate between one-time and recurring payments in a reconciliation file

**One-time payment:**

- *Charge Start Date* and *Charge End Date* are the same as the *Subscription Start Date* and *Subscription End Date*.
- *Billing Frequency* is blank.

**Recurring payment or billing plan:**

- *Charge Start Date* and *Charge End Date* are separated by one month.
- *Billing Frequency* says "Monthly."
- *Charge Start Date* and *Charge End Date* are separated by one year.
- *Billing Frequency* says "Annual."

## How do you calculate the costs of a product with both subscription and pay-as-you-go charges?

Maximizing the benefits of your subscription-based products is easy and straightforward. But some subscriptions may come with a set number of prepaid units for a specific price. If you use more, you’ll be charged the pay-as-you-go rate for any extras. For example, if you buy one of these products:

- Microsoft 365 subscription: For USD 10/month, you can make calls for 100 minutes. Each additional minute will cost 10 cents.
- SendGrid product: For USD 10/month, you can send 100 emails. Each additional email will cost 10 cents.

If you make calls for 150 minutes or send 150 emails in a month, you go over your limit, resulting in extra pay-as-you-go charges.

For such complicated subscriptions, you need to use the daily rated usage and invoice reconciliation data together to figure out the costs in the billing period.

Here’s how:

1. Look at the `BillingPreTaxTotal` attribute of the daily rated usage data to find the daily pay-as-you-go charges. In this example, that’s **50 \* 0.1 = USD 5**
2. Check  the `Total` attribute in the invoice reconciliation data to see the monthly costs for your pay-as-you-go charges, which should be  the same as USD 5. The `BillableQuantity` attribute shows  the units, which in this case should be **50.**
3. Find   the subscription cost in the `Total` attribute based on  the billing plan in the invoice reconciliation data. For example, the cost  will appear each month if you pay monthly. In this case, it should be **USD 10.**
4. Lastly, check the Product and SKU IDs in the invoice reconciliation file to get  the total cost, which may include two separate lines for the subscription and pay-as-you-go costs. In this case, it should be **USD 15.**

With these easy steps, you can keep track of your subscription costs and make smart choices about how you use them. 

## How do I determine the product category?

You can determine the product category in the reconciliation data using the methods listed below. Except in rare cases, this workaround can determine the product category for most transactions.

| **Condition** | **Product Category** |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| `PublisherName` attribute says "Microsoft" or "Microsoft Corporation" | First-party product|
| `PublisherName` attribute says something other than "Microsoft" or "Microsoft Corporation," and "PublisherID" has a value. | Third-party product|
| `TermAndBillingCycle` attribute has the keyword "Reservation." | Azure Reservation|
| `TermAndBillingCycle` attribute has the keyword "Savings Plan." | Azure Savings Plan|
| `TermAndBillingCycle` attribute has the keyword "Subscription." <br>This attribute doesn't always include the keyword. In that case, use the SKU name, such as "SQL Server," "Windows Server," and so on. | Software subscription|
| `TermAndBillingCycle` attribute has the phrase "one-month," "one-year," or "three-year." | License-based. *However, double-check to confirm.*|
| `TermAndBillingCycle` attribute is blank, and "ChargeEndDate" column is empty. | Perpetual software|
| `SubscriptionDescription` attribute says "Azure plan." |Azure plan|
| Remaining conditions|After eliminating all of the preceding product categories, the remaining category should be referred to as an Azure plan. (Partners can assign unique subscription names.) *Double-check that nothing is missing.*|

## How do I find the billing term in a reconciliation file?

`TermAndBillingCycle` is a description that shows different texts to describe the billing term and plan. However, billing terms and plans for different subscriptions can differ, so there is no standard text to describe them.

But don’t worry—if you need to know the **billing term**, check the **subscription** start and end dates to see the duration of your subscription. To find out the **billing plan**, check the **charge** start and end dates to see the timeframe of your charge cycle. 

See the examples below:

| **TermAndBillingCycle** | **SubscriptionStartDate** | **SubscriptionEndDate** |
| ---------------------------------------------------- | ------------------------- | ----------------------- |
| One-year commitment for monthly/yearly billing | April 15, 2021 | April 14, 2022 |
| One-year term duration | April 22, 2021 | April 2, 2022 |
| One-month commitment for monthly billing | April 14, 2021 | May 13, 2021 |
| Three-year commitment for monthly/yearly billing | May 25, 2021 | May 24, 2024 |

## Monthly term subscription expiration dates on special cases

Here’s how monthly subscriptions expire when you buy near the end of a month:

- [If you buy on the last day of a month](#when-you-buy-on-the-last-day-of-a-month)
- [If you buy on *the day before* the last day of a month](#when-you-buy-on-the-day-before-the-last-day-of-a-month)

### When you buy on the *last day* of a month

If you buy on the last day of a month, your subscription will end on the:

- 30th day of a month with 31 days
- 29th day of the month with 30 days
- 28th day of February in a leap year
- 27th day of February in non-leap years

> [!NOTE]
> Remember, these purchases were made on different dates and are unrelated.

The dates in the reconciliation file are in Coordinated Universal Time (UTC).

If you purchase a monthly subscription, the charge cycle should look like this:

| Billing Term | Order Date | Charge Type | Subscription Start Date | Subscription End Date | Renew Date | Charge Start Date | Charge End Date |
| :----------- | :--------- | ----------- | :---------------------- | :-------------------- | :--------- | :---------------- | :-------------- |
| Monthly | January 31, 2021 | new | January 31, 2021 | February 27, 2021 | February 28, 2021 | January 31, 2021 | February 27, 2021 |
| Monthly | February 28, 2021 | new | February 28, 2021 | March 27, 2021 | March 28, 2021 | February 28, 2021 | March 27, 2021 |
| Monthly | May 31, 2021 | new | May 31, 2021 | June 29, 2021 | June 30, 2021 | May 31, 2021 | June 29, 2021 |
| Monthly | June 30, 2021 | new | June 30, 2021 | July 29, 2021 | July 30, 2021 | June 30, 2021 | July 29, 2021 |
| Monthly | July 31, 2021 | new | July 31, 2021 | August 30, 2021 | August 31, 2021 | July 31, 2021 | August 30, 2021 |

If you purchase an annual subscription with a monthly billing plan, the charge cycle should look like this:

| Billing Term | Billing Plan | Order Date         | Charge Type | Subscription Start Date | Subscription End Date | Renew Date       | Charge Start Date | Charge End  Date   |
| ------------ | ------------ | ------------------ | ----------- | ----------------------- | --------------------- | ---------------- | ------------------ | ------------------ |
| Annual       | Monthly      | January 31, 2021   | new         | January 31, 2021         | January 30, 2022       | January 31, 2022 | January 31, 2021   | February 27, 2021  |
| Annual       | Monthly      | February 28, 2021  | cycleCharge | January 31, 2021         | January 30, 2022       | January 31, 2022 | February 28, 2021  | March 30, 2021     |
| Annual       | Monthly      | March 31, 2021     | cycleCharge | January 31, 2021         | January 30, 2022       | January 31, 2022 | March 31, 2021     | April 29, 2021     |
| Annual       | Monthly      | April 30, 2021     | cycleCharge | January 31, 2021         | January 30, 2022       | January 31, 2022 | April 30, 2021     | May 30, 2021       |
| Annual       | Monthly      | May 31, 2021       | cycleCharge | January 31, 2021         | January 30, 2022       | January 31, 2022 | May 31, 2021       | June 29, 2021      |
| Annual       | Monthly      | June 30, 2021      | cycleCharge | January 31, 2021         | January 30, 2022       | January 31, 2022 | June 30, 2021      | July 30, 2021      |
| Annual       | Monthly      | July 31, 2021      | cycleCharge | January 31, 2021         | January 30, 2022       | January 31, 2022 | July 31, 2021      | August 30, 2021    |
| Annual       | Monthly      | August 31, 2021    | cycleCharge | January 31, 2021         | January 30, 2022       | January 31, 2022 | August 31, 2021    | September 29, 2021 |
| Annual       | Monthly      | September 30, 2021 | cycleCharge | January 31, 2021         | January 30, 2022       | January 31, 2022 | September 30, 2021 | October 30, 2021   |
| Annual       | Monthly      | October 31, 2021   | cycleCharge | January 31, 2021         | January 30, 2022       | January 31, 2022 | October 31, 2021   | November 29, 2021  |
| Annual       | Monthly      | November 30, 2021  | cycleCharge | January 31, 2021         | January 30, 2022       | January 31, 2022 | November 30, 2021  | December 30, 2021  |
| Annual       | Monthly      | December 31, 2021  | cycleCharge | January 31, 2021         | January 30, 2022       | January 31, 2022 | December 31, 2021  | January 30, 2022   |
___

### When you buy on *the day before the last day* of a month

If you buy on *the day before* the last day of a month, your subscription will end on the:

- 29th day of a month with 31 days
- 28th day of a month with 30 days

> [!NOTE]
> Remember, these purchases were made on different dates and are unrelated.

The dates in the reconciliation file are in UTC.

If you purchase a monthly subscription, the charge cycle should look like this:

| **Billing Term** | **Order Date** | **Charge Type** | **Subscription Start Date** | **Subscription End Date** | **Renew Date** | **Charge Start Date** | **Charge End Date** |
| ----------------- | -------------- | --------------- | ---------------------------- | -------------------------- | -------------- | ---------------------- | -------------------|
| Monthly | January 30, 2021 | new | January 30, 2021 | February 27, 2021 | February 28, 2021 | January 30, 2021 | February 27, 2021 |
| Monthly | February 27, 2021 | new | February 27, 2021 | March 26, 2021 | March 27, 2021 | February 27, 2021 | March 26, 2021 |
| Monthly | May 30, 2021 | new | May 30, 2021 | June 29, 2021 | June 30, 2021 | May 30, 2021 | June 29, 2021 |
| Monthly | June 29, 2021 | new | June 29, 2021 | July 28, 2021 | July 29, 2021 | June 29, 2021 | July 28, 2021 |
| Monthly | July 30, 2021 | new | July 30, 2021 | August 29, 2021 | August 30, 2021 | July 30, 2021 | August 29, 2021 |
___

If you purchase an annual subscription with a monthly billing plan, the charge cycle should look like this:

| **Billing Term** | **Billing Plan** | **Order Date**     | **Charge Type** | **Subscription  Start Date** | **Subscription  End Date** | **Renew Date**   | **Charge Start  Date** | **Charge End  Date** |
| ---------------- | ---------------- | ------------------ | --------------- | ---------------------------- | -------------------------- | ---------------- | ---------------------- | -------------------- |
| Annual           | Monthly          | January 30, 2021   | new             | January 30, 2021             | January 29, 2022           | January 30, 2022 | January 30, 2021       | February 26, 2021    |
| Annual           | Monthly          | February 27, 2021  | cycleCharge     | January 30, 2021             | January 29, 2022           | January 30, 2022 | February 27, 2021      | March 29, 2021       |
| Annual           | Monthly          | March 30, 2021     | cycleCharge     | January 30, 2021             | January 29, 2022           | January 30, 2022 | March 30, 2021         | April 28, 2021       |
| Annual           | Monthly          | April 29, 2021     | cycleCharge     | January 30, 2021             | January 29, 2022           | January 30, 2022 | April 29, 2021         | May 29, 2021         |
| Annual           | Monthly          | May 30, 2021       | cycleCharge     | January 30, 2021             | January 29, 2022           | January 30, 2022 | May 30, 2021           | June 28, 2021        |
| Annual           | Monthly          | June 29, 2021      | cycleCharge     | January 30, 2021             | January 29, 2022           | January 30, 2022 | June 29, 2021          | July 29, 2021        |
| Annual           | Monthly          | July 30, 2021      | cycleCharge     | January 30, 2021             | January 29, 2022           | January 30, 2022 | July 30, 2021          | August 29, 2021      |
| Annual           | Monthly          | August 30, 2021    | cycleCharge     | January 30, 2021             | January 29, 2022           | January 30, 2022 | August 30, 2021        | September 28, 2021   |
| Annual           | Monthly          | September 29, 2021 | cycleCharge     | January 30, 2021             | January 29, 2022           | January 30, 2022 | September 29, 2021     | October 29, 2021     |
| Annual           | Monthly          | October 30, 2021   | cycleCharge     | January 30, 2021             | January 29, 2022           | January 30, 2022 | October 30, 2021       | November 28, 2021    |
| Annual           | Monthly          | November 29, 2021  | cycleCharge     | January 30, 2021             | January 29, 2022           | January 30, 2022 | November 29, 2021      | December 29, 2021    |
| Annual           | Monthly          | December 30, 2021  | cycleCharge     | January 31, 2021             | January 30, 2022           | January 30, 2022 | December 30, 2021      | January 29, 2022     |
___

## How are licenses (seats) added or removed?

If you have Microsoft license-based products and need to adjust the number of seats or licenses you’ve purchased, it’s important to understand how billing works. In this guide, we’ll walk you through the process of adjusting seats and explain how the charges are calculated.

Let’s say you purchased ten “Microsoft 365 Business Standard” licenses on June 18, 2021, for EUR 10.08 each, with a monthly billing term and plan. You added two more seats on June 20, and on the following July reconciliation file for the June billing period, you’ll see the following bill lines:

| **Order Date** | **Charge Type** | **Unit Price** | **Charge Start Date** | **Charge End Date** | **Effective Unit Price** | **Billable Quantity** | **Total** |
| -------------- | --------------- | -------------- | --------------------- | ------------------- | ------------------------ | --------------------- | --------- |
| June 18, 2021 | new | 10.08 | June 18, 2021 | July 17, 2021 | 10.08 | 10 | 100.8 |
| June 20, 2021 | addQuantity | 10.08 | June 20, 2021 | July 17, 2021 | -9.408 | 10 | -94.08 |
| June 20, 2021 | addQuantity | 10.08 | June 20, 2021 | July 17, 2021 | 9.408 | 12 | 112.89 |

Adjusting seats is handled in two steps:

- Refund (wipe): a refund for the original seat count from the adjustment day to the end of the charge cycle.
- Charge (recreate): a charge for the adjusted seat count for the same period.

The charges are calculated using a formula based on the *Effective Unit Price*.

`Effective Unit Price = unit price / charge cycle days \* billing days (Discounts and adjustments may affect the effective unit price).`

*Billing days are counted from when an event occurs until the charge cycle ends. Charge cycles and billing plans have the same duration.*

> [!NOTE]
> The purchase month determines the charge cycle or billable days: June has 30, August has 31, and a year has 365 or 366 (in a leap year).

In the above example, first transaction is a charge of EUR 100.8 for 10 licenses for **30 days** from June 18 to July 17.

`Total cost (before taxes and exchange rates) = effective unit price \* billable quantity.`

The second transaction is a refund of EUR 94 for 10 licenses for **28 days** from June 20 to July 17.

`Refund amount = Effective Unit Price (10.08 / 30 \* 28) \* Billable Quantity (10) = 94.08`

The third transaction is the adjusted charge of EUR 112.8 for 12 licenses for **28 days** from June 20 to July 17.

`Total cost = Effective Unit Price (10.08 / 30 \* 28) \* Billable Quantity (12) = 112.89`

Let’s say you removed four seats or licenses on June 20. We’ll give you a refund and recalculate the fees as we did before. 

Reconciliation data should include the following billing lines:

| **Order Date** | **Charge Type** | **Unit Price** | **Charge Start Date** | **Charge End Date** | **Effective Unit Price** | **Billable Quantity** | **Total** |
| -------------- | --------------- | -------------- | --------------------- | ------------------- | ------------------------ | --------------------- | --------- |
| June 20, 2021 | removeQuantity | 10.08 | June 20, 2021 | July 17, 2021 | -9.408 | 12 | -112.89 |
| June 20, 2021 | removeQuantity | 10.08 | June 20, 2021 | July 17, 2021 | 9.408 | 8 | 75.26 |

The first transaction is a refund of EUR112.89 for 12 licenses for **28 days** from June 20 to July 17.

`Refund amount = Effective Unit Price (10.08 / 30 \* 28) \* Billable Quantity (12) = 112.89`

The adjusted transaction is a EUR75.26 charge for 8 licenses for **28 days** from June 20 to July 17.

`Total cost = Effective Unit Price (10.08 / 30 \* 28) \* Billable Quantity (8) = 75.26`

## How do I calculate the total number of seats (licenses) after multiple changes during a billing period?

Let’s take an example where you bought 10 Microsoft 365 Business Standard seats for your client Contoso on March 5, 2022. You made several changes to the subscription, such as adding 5 seats on March 7 and 10 on March 10, and removing 2 seats on March 12 and 3 on March 14. Finally, on March 25, you added 10 seats. Now, you need to know the total number of seats at the end of the March billing period.

The reconciliation file or API doesn't show your changes in chronological order.

To arrange transactions chronologically and logically, use the following steps:

1. Use the subscription ID from the first purchase. To find the first purchase according to this example, set the order date to March 5, 2022, the charge type to “new,” and the product or SKU to “Microsoft 365 Business Standard.”
2. Sort the order date from oldest to newest and link each seat addition and removal event with its “ReferenceID.” For more information, see [How are licenses (seats) added or removed](#how-are-licenses-seats-added-or-removed) later in this article.
3. The last positive charge transaction will show the total number of seats in the billing period. In this example, the total number of seats is **30** for the subscription in March.
4. However, if you make multiple adjustments to your seat within a day, you may notice more than one positive charge for that day. This can make it difficult to determine which charge is the most recent. To figure out how many seats you have for a subscription during a billing period, look for the `OrderDate` of the transactions with `ChargeType` *“new,” “renew,” or “cycleCharge”* in that period. Then, calculate the **sum** of the `BillableQuantity` for all *positive charges from that day* for all charge types (excluding *customerCredit* from other billing periods) and **subtract** the *total* of the `BillableQuantity` for all *negative charges from that day* from the *total quantity of the positive charges*. The **result is the number of licenses** during the billing period.

By summarizing, sorting the transactions in order of when they occurred, and linking them to the ReferenceID, you can keep track of multiple seat changes in a billing period and figure out how many seats there are in total.

See the table below to correlate the events.

| **OrderDate**  | **ProductName**                  | **ChargeType** | **UnitPrice** | **BillableQuantity** | **EffectiveUnitPrice** | **Subtotal** | **SubscriptionId**                   | **ChargeStartDate** | **ChargeEndDate** | **ReferenceId**                      |
| -------------- | -------------------------------- | -------------- | ------------- | -------------------- | ---------------------- | ------------ | ------------------------------------ | ------------------- | ----------------- | ------------------------------------ |
| March 5, 2022  | Microsoft 365 Business  Standard | new            | 12            | 10                   | 12.00                  | 120          | 284b0ff0-0e74-4f65-cb23-f8ad95867994 | March 5, 2022       | April 4, 2022     | 7d71c595-4635-40d1-a9e2-b34e63b01764 |
| March 7, 2022  | Microsoft 365 Business  Standard | addQuantity    | 12            | 10                   | -11.23                 | -112.25      | 284b0ff0-0e74-4f65-cb23-f8ad95867994 | March 7, 2022       | April 4, 2022     | 12d33e18-061e-4040-ad77-fcd77c1a9943 |
| March 7, 2022  | Microsoft 365 Business  Standard | addQuantity    | 12            | 15                   | 11.23                  | 168.38       | 284b0ff0-0e74-4f65-cb23-f8ad95867994 | March 7, 2022       | April 4, 2022     | 12d33e18-061e-4040-ad77-fcd77c1a9943 |
| March 10, 2022 | Microsoft 365 Business  Standard | addQuantity    | 12            | 15                   | -10.06                 | -150.96      | 284b0ff0-0e74-4f65-cb23-f8ad95867994 | March 10, 2022      | April 4, 2022     | dc2a0a41-6a51-4837-8956-af5ffd92b094 |
| March 10, 2022 | Microsoft 365 Business  Standard | addQuantity    | 12            | 25                   | 10.06                  | 251.61       | 284b0ff0-0e74-4f65-cb23-f8ad95867994 | March 10, 2022      | April 4, 2022     | dc2a0a41-6a51-4837-8956-af5ffd92b094 |
| March 12, 2022 | Microsoft 365 Business  Standard | removeQuantity | 12            | 25                   | -9.29                  | -232.25      | 284b0ff0-0e74-4f65-cb23-f8ad95867994 | March 12, 2022      | April 4, 2022     | 2f8965ff-512b-4233-9a74-1f54a6ad71d0 |
| March 12, 2022 | Microsoft 365 Business  Standard | removeQuantity | 12            | 23                   | 9.29                   | 213.67       | 284b0ff0-0e74-4f65-cb23-f8ad95867994 | March 12, 2022      | April 4, 2022     | 2f8965ff-512b-4233-9a74-1f54a6ad71d0 |
| March 14, 2022 | Microsoft 365 Business  Standard | removeQuantity | 12            | 23                   | -8.52                  | -195.87      | 284b0ff0-0e74-4f65-cb23-f8ad95867994 | March 14, 2022      | April 4, 2022     | 73b3dc36-f36d-4bbf-af8f-30c9b73ac4f6 |
| March 14, 2022 | Microsoft 365 Business  Standard | removeQuantity | 12            | 20                   | 8.52                   | 170.32       | 284b0ff0-0e74-4f65-cb23-f8ad95867994 | March 14, 2022      | April 4, 2022     | 73b3dc36-f36d-4bbf-af8f-30c9b73ac4f6 |
| March 25, 2022 | Microsoft 365 Business  Standard | addQuantity    | 12            | 20                   | -4.26                  | -85.16       | 284b0ff0-0e74-4f65-cb23-f8ad95867994 | March 25, 2022      | April 4, 2022     | 6759acd5-a8a9-4402-94b7-803baa64a78e |
| March 25, 2022 | Microsoft 365 Business  Standard | addQuantity    | 12            | 30                   | 4.26                   | 127.74       | 284b0ff0-0e74-4f65-cb23-f8ad95867994 | March 25, 2022      | April 4, 2022     | 6759acd5-a8a9-4402-94b7-803baa64a78e |

## How are the refunds calculated if I cancel a subscription within seven days of buying or renewing it?

Let’s say you bought 10 seats of a Microsoft 365 Business Standard subscription on July 15, 2021, for EUR 10.08 each with a monthly billing term and plan, then canceled the subscription on July 17. 
In this case, the following billing line will appear on the August reconciliation data for the July billing cycle:

| **Order Date** | **Charge Type** | **Unit Price** | **Charge Start Date** | **Charge End Date** | **Effective Unit Price** | **Billable Quantity** | **Total** |
| -------------- | --------------- | -------------- | --------------------- | ------------------- | ------------------------ | --------------------- | --------- |
| July 15, 2021 | new | 10.08 | July 15, 2021 | August 14, 2021 | 10.08 | 10 | 100.8 |
| July 17, 2021 | cancelImmediate | 10.08 | July 17, 2021 | August 14, 2021 | -9.42 | 10 | -94.2 |

The first transaction is a charge of EUR 100.8 for 10 licenses for **31 days** from July 15 to August 14.

`Total cost = Effective Unit Price (10.08 / 31 \* 31) \* Billable Quantity (10) = 100.8`

The second transaction is a refund of EUR 94.2 refund for cancellation for **29 unused days** from July 17 to August 14.

`Refund amount = (Effective Unit Price (10.08 / 31 \* 29) \* Billable Quantity (10) = 94.2`

> [!IMPORTANT]
> You can get a full refund if you cancel within 24 hours of purchase or renewal, or a prorated refund if you cancel within 7 days.

## How should I reconcile and link upgraded transactions?

There are two types of upgrades:

* [*Full* upgrade](#full-upgrade), when you upgrade every license (seat) of the base subscription to an advanced one.
* [*Partial* upgrade](#partial-upgrade), when you upgrade some of the licenses (seats) of the base subscription to an advanced one.

You might have multiple subscriptions with different billing terms, prices, and charge cycles. Managing these subscriptions can be complicated and confusing, especially if you want to upgrade.

You can link transactions that happened during the upgrade in your reconciliation data.

### Full upgrade

Let’s say you purchased 300 licenses of a Microsoft 365 Business Standard subscription on June 18th with a monthly billing term. The monthly price for each license was EUR 10.08. However, on June 25th, you decided to upgrade your subscription to Office 365 E1, which would cost EUR 6.43 per month for each license.

When you upgrade your subscription, you’ll receive a refund for the base subscription and be charged for the upgraded one from the day of the upgrade until the charge cycle ends. This ensures that you only pay for the services you use and that your billing is accurate and up-to-date.

The *Effective Unit Price* determines the charges.

`Effective Unit Price = unit price / charge cycle days \* billing days (Discounts and adjustments may affect the effective unit price).`

*Billing days are counted from when an event occurs until the charge cycle ends. Charge cycles and billing plans have the same duration.*

`Total cost *(before taxes and exchange rates)* = effective unit price \* billable quantity.`

The July reconciliation data for June billing will include these billing lines:

| **Order Date** | **Product**                     | **Charge Type** | **Unit Price** | **Charge Start Date** | **Charge End Date** | **Effective Unit Price** | **Billable Quantity** | **Total** | **Subscription ID**                  | **Reference ID**                     |
| -------------- | ------------------------------- | --------------- | -------------- | --------------------- | ------------------- | ------------------------ | --------------------- | --------- | ------------------------------------ | ------------------------------------ |
| June 18, 2021  | Microsoft 365 Business Standard | new             | 10.08          | June 18, 2021         | July 17, 2021       | 10.08                    | 300                   | 3024      | 284b0ff0-0e74-4f65-cb23-f8ad95867994 | 7d71c595-4635-40d1-a9e2-b34e63b01764 |
| June 25, 2021  | Microsoft 365 Business Standard | convert         | 10.08          | June 25, 2021         | July 17, 2021       | -7.72                    | 300                   | -2316     | 284b0ff0-0e74-4f65-cb23-f8ad95867994 | 12d33e18-061e-4040-ad77-fcd77c1a9943 |
| June 25, 2021  | Office 365 E1                   | convert         | 6.43           | June 25, 2021         | July 17, 2021       | 4.92                     | 300                   | 1476      | 284b0ff0-0e74-4f65-cb23-f8ad95867994 | 12d33e18-061e-4040-ad77-fcd77c1a9943 |

The first line is a charge of EUR 3024 for the *Microsoft 365 Business Standard* subscription for the whole month from June 18 to July 17.

The second line is a refund of EUR 2,316 for the same subscription because you didn’t use it for **23 days** from June 25 to July 17.

`Refund = Effective Unit Price (10.08 / 30 \* 23) \* Billable Quantity (300) = 2,316.`

The third line is a charge of EUR 1,476 for the upgraded subscription for the same **23 days** from June 25 to July 17.

`Total cost = Effective Unit Price (6.43 / 30 \* 23) \* Billable Quantity (300) = 1,476.`

#### How do I calculate the total seats for the base and upgraded subscriptions in a billing period for a full upgrade?

The reconciliation file or API doesn't show your changes in chronological order.

To arrange transactions chronologically and logically, use the following steps:

1. Use the subscription ID from the first purchase. To find the first purchase according to this example, set the order date to June 18, 2021, the charge type to “new,” and the product or SKU to “Microsoft 365 Business Standard.”

2. Sort the order date from oldest to newest. “ReferenceID” and “SubscriptionID” connect these transactions. For more information, see [how can I link my upgraded subscriptions](#how-can-i-link-my-upgraded-subscriptions).

3. The base and upgraded subscriptions will have the charge type “convert.”

4. The last positive charge transaction with the charge type “convert” will show the upgraded subscription’s seat count in the billing period. In this example, the total number is 300 for the upgraded subscription in March.

5. However, if you make multiple upgrades to your subscription within a day, you may notice more than one positive charge for that day. This can make it difficult to determine which charge is the most recent. To figure out how many seats you have for a subscription during a billing period, look for the `OrderDate` of the transactions with `ChargeType` *“new,” “renew,” or “cycleCharge”* in that period. Then, calculate the **sum** of the `BillableQuantity` for all *positive charges from that day* for all charge types (excluding *customerCredit* from other billing periods) and **subtract** the *total* of the `BillableQuantity` for all *negative charges from that day* from the *total quantity of the positive charges*. The **result is the number of licenses** during the billing period.

> [!NOTE]
> When buying a new advanced subscription, the charge type “convert” is used for upgraded transactions, while “moveQuantity” is used when the advanced subscription already exists.

### Partial upgrade

Let’s say you purchased 300 licenses of a Microsoft 365 Business Standard subscription on June 18th with a monthly billing term. The monthly price for each license was EUR 10.08. However, on June 25th, you decided to upgrade your 100 seats to Office 365 E1, which would cost EUR 6.43 per month for each license.

When you upgrade your subscription, you’ll receive a refund for the base subscription and be charged for the upgraded one from the day of the upgrade until the charge cycle ends. This ensures that you only pay for the services you use and that your billing is accurate and up-to-date.

The *Effective Unit Price* determines the actual charges.

`Effective Unit Price = unit price / charge cycle days \* billing days (Discounts and adjustments may affect the effective unit price).`

*Billing days are counted from when an event occurs until the charge cycle ends. Charge cycles and billing plans have the same duration.*

`Total cost (before taxes and exchange rates) = effective unit price \* billable quantity.`

The July reconciliation file for June billing will include these billing lines:

| **Order Date** | **Product**                     | **Charge Type** | **Unit Price** | **Charge Start Date** | **Charge End Date** | **Effective Unit Price** | **Billable Quantity** | **Total** | **Subscription ID**                  | **Reference ID**                     |
| -------------- | ------------------------------- | --------------- | -------------- | --------------------- | ------------------- | ------------------------ | --------------------- | --------- | ------------------------------------ | ------------------------------------ |
| June 18, 2021  | Microsoft 365 Business Standard | new             | 10.08          | June 18, 2021         | July 17, 2021       | 10.08                    | 300                   | 3024      | 284b0ff0-0e74-4f65-cb23-f8ad95867994 | 7d71c595-4635-40d1-a9e2-b34e63b01764 |
| June 25, 2021  | Microsoft 365 Business Standard | convert         | 10.08          | June 25, 2021         | July 17, 2021       | -7.72                    | 100                   | -772      | 284b0ff0-0e74-4f65-cb23-f8ad95867994 | 12d33e18-061e-4040-ad77-fcd77c1a9943 |
| June 25, 2021  | Office 365 E1                   | convert         | 6.43           | June 25, 2021         | July 17, 2021       | 4.92                     | 100                   | 492       | 6759acd5-a8a9-4402-94b7-803baa64a78e | 12d33e18-061e-4040-ad77-fcd77c1a9943 |

The first line item is a charges of EUR 3024 for the *Microsoft 365 Business Standard* subscription for the whole month from June 18 to July 17.

The second line is a refund of EUR 772 refund for 100 licenses of the base subscription because you didn’t use it for **23 days** from June 25 to July 17.

`Refund = Effective Unit Price (10.08 / 30 \* 23) \* Billable Quantity (100) = 772`

The third line is a charge of EUR 492 for the upgraded subscription for the same **23 days** from June 25 to July 17.

`Total cost = Effective Unit Price (6.43 / 30 \* 23) \* Billable Quantity (100) = 492.`

> [!NOTE]
> The refund amount is a way to adjust the cost of the remaining charge cycle.

#### How do I calculate the total seats for the base and upgraded subscriptions in a billing period for a partial upgrade?

The reconciliation file or API doesn't show your changes in chronological order.

To arrange transactions chronologically and logically, use the following steps:

1. Use the subscription ID from the first purchase. To find the first purchase according to this example, set the order date to June 18, 2021, the charge type to “new,” and the product or SKU to “Microsoft 365 Business Standard.”

2. Sort the order date from oldest to newest. “ReferenceID” and “SubscriptionID” connect these transactions. For more information, see [how can I link my upgraded subscriptions](#how-can-i-link-my-upgraded-subscriptions).

3. The base and upgraded subscription will have the charge type “convert.”

4. The last positive charge transaction with the charge type “convert” will show the upgraded subscription’s seat count for the billing period. In this example, it's 100 in March. The base subscription seats are calculated by subtracting the billable quantity of the “convert” charge type from the “new” charge type. In this example, it's 200 in March.

5. However, if you make multiple upgrades to your subscription within a day, you may notice more than one positive charge for that day. This can make it difficult to determine which charge is the most recent. To figure out how many seats you have for a subscription during a billing period, look for the `OrderDate` of the transactions with `ChargeType` *“new,” “renew,” or “cycleCharge”* in that period. Then, calculate the **sum** of the `BillableQuantity` for all *positive charges from that day* for all charge types (excluding *customerCredit* from other billing periods) and **subtract** the *total* of the `BillableQuantity` for all *negative charges from that day* from the *total quantity of the positive charges*. The **result is the number of licenses** during the billing period.

> [!NOTE]
> When buying a new advanced subscription, the charge type “convert” is used for upgraded transactions, while “moveQuantity” is used when the advanced subscription already exists.

## How can I link my upgraded subscriptions?

If you want to track the transactions that happened when you upgraded your subscriptions, you need to use two identifiers: the `SubscriptionID` and the `ReferenceID.`

Use the `SubscriptionID` of the base product to find the corresponding `ReferenceID.` This will enable you to see all the related transactions. You can then use the `SubscriptionID` and `ReferenceID` to link all the transactions that occurred during an upgrade event.

## How do I reconcile after I convert a trial version to a paid subscription?

Let’s say you bought 25 “Dynamics 365 Guides” licenses (seats) on June 25 as a free trial. Trial products last one month before you can upgrade to the paid version, which is like an upgrade. 

The July reconciliation file will include the following billing line for the June billing cycle:

| **Order Date** | **Charge Type** | **Unit Price** | **Charge Start Date** | **Charge End Date** | **Effective Unit Price** | **Billable Quantity** | **Product Qualifier** | **Total** |
| -------------- | --------------- | -------------- | --------------------- | ------------------- | ------------------------ | --------------------- | --------------------- | --------- |
| June 25, 2021 | new | 0 | June 25, 2021 | July 24, 2021 | 0 | 25 | ["Trial"] | 0 |
| June 25, 2021 | convert | 0 | June 25, 2021 | July 24, 2021 | 0 | 25 | ["Trial"] | 0 |
| June 25, 2021 | convert | 52.61 | June 25, 2021 | July 24, 2021 | 52.61 | 25 | | 1,315.25 |

The first line item shows no charge for the “Dynamics 365 Guides” trial subscription. Using the `ProductQualifiers` attribute, you can verify it. Later on the same day, you turned it into a paid version. The refund should be on the second line. Since it’s a trial, there’s no refund.

The third line shows an EUR 1,315.25 cost for the paid version from June 25, 2021, to July 24, 2021.

`Total cost = Effective Unit Price (52.61 / 30 * 30) * Billable Quantity (25) = 1,315.25`

## How do I reconcile transactions after changing billing plans?

You can change your billing plan after the first charge cycle. For example, if you want to switch from an annual to a monthly billing plan, you can do so after one year.

Let’s look at an example.

You bought ten licenses for Dynamics 365 Commerce on September 20, 2021, with a three-year billing term and an annual billing plan. You can change the billing plan to monthly on September 19, 2022, after the end of the annual charge cycle. The monthly charge will show up in the September 2022 reconciliation data, and its `ChargeCycle` will show **“changeBillingPlan”** to confirm the change.

> [!NOTE]
> Changing billing plans doesn’t change the start and end dates of the subscription.

**Annual to monthly:**

| **Charge Type** | **Quantity** | **Unit Price** | **Effective Unit Price** | **Total** | **Charge Start Date** | **Charge End Date** | **Billing Frequency** |
| ----------------- | ------------ | -------------- | ------------------------ | --------- | --------------------- | ------------------- | --------------------- |
| new | 10 | 250 | 250 | 2,500 | September 20, 2021 | September 19, 2022 | Annual |
| changeBillingPlan | 10 | 20 | 20 | 200 | September 20, 2022 | October 19, 2022 | Monthly |

 **Monthly to annual:**

| **Charge Type** | **Quantity** | **Unit Price** | **Effective Unit Price** | **Total** | **Charge Start Date** | **Charge End Date** | **Billing Frequency** |
| ----------------- | ------------ | -------------- | ------------------------ | --------- | --------------------- | ------------------- | --------------------- |
| new | 10 | 20 | 20 | 200 | September 20, 2021 | October 19, 2021 | Monthly |
| changeBillingPlan | 10 | 250 | 229.16 | 2291.6 | October 20, 2021 | September 19, 2022 | Annual |

## How do I validate charges in legacy and NCE reconciliation data after migrating to NCE?

When you migrate to New Commerce in the middle of a legacy charge cycle, your charges will be split between two invoices.

Any prepaid charges will be prorated and refunded on the next legacy bill after the migration. The new commerce subscription will then bill new charges in the same way, so you won’t lose money or miss out on any services during the migration.

To help you understand this better, let’s look at an example:

Let’s say that on July 21, 2021, you bought a legacy Microsoft Office 365 E3 subscription with an annual billing term and a monthly billing plan. But on January 24, 2022, you decided to migrate the subscription to new commerce while keeping the same billing term and plan.

Here’s what will happen to your charges: 

Your **legacy invoice** will show you all of your **legacy subscription charges up to January 23, 2022. From January 24, 2022,** your **new commerce subscription charges** will appear **on the new commerce invoice.** 

### Consider the following details

**Purchased licenses (seats):** One

**Price of a license/seat for a month:** USD 16

**Legacy billing anniversary date:** The 21st day of each month

**Legacy monthly reconciliation file of January 2022:**

| **Subscription Name** | **Charge Type** | **Unit Price** | **Subscription Start Date** | **Subscription End Date** | **Billing Cycle** | **Charge Start Date** | **Charge End Date** |
| ----------------------- | -------------------------- | -------------- | --------------------------- | ------------------------- | ----------------- | --------------------- | ------------------- |
| Microsoft Office 365 E3 | Prorate fees when purchase | 16 | July 21, 2021 | July 2, 2022 | Monthly | January 2, 2022 | February 20, 2022 |

**Legacy monthly reconciliation file of February 2022:**

| **Subscription Name** | **Charge Type** | **Unit Price** | **Subscription Start Date** | **Subscription End Date** | **Billing Cycle** | **Charge Start Date** | **Charge End Date** |
| ----------------------- | --------------------------- | -------------- | --------------------------- | ------------------------- | ----------------- | --------------------- | ------------------- |
| Microsoft Office 365 E3 | Prorate fees when purchase | 16 | July 21, 2021 | July 21/2022 | Monthly | February 21/2022 | March 20, 2022 |
| Microsoft Office 365 E3 | Cancel fee | -16 | July 21, 2021 | July 21/2022 | Monthly | February 21/2022 | March 20, 2022 |
| Microsoft Office 365 E3 | Cancel fee | -13.93 | July 21, 2021 | July 21/2022 | Monthly | January 25, 2022 | February 20, 2022 |

**NCE monthly reconciliation file of January 2022:**

In January, the charges will be prorated after the migration.

| **Subscription Name** | **Charge Type** | **Unit Price** | **Effective Unit Price** | **Subscription Start Date** | **Subscription End Date** | **Term & Billing Cycle** | **Billing Frequency** | **Charge Start Date** | **Charge End Date** |
| ----------------------- | --------------- | -------------- | ------------------------ | --------------------------- | ------------------------- | ------------------------ | --------------------- | --------------------- | ------------------- |
| Microsoft Office 365 E3 | new | 16 | 15.42 | January 25, 2022 | July 20, 2022 | Annual | Monthly | January 25, 2022 | February 20, 2022 |

If you switched the billing plan to annual while migrating, the transactions would look like this:

**NCE monthly reconciliation file of January 2022:**

| **Subscription Name** | **Charge Type** | **Unit Price** | **Effective Unit Price** | **Subscription Start Date** | **Subscription End Date** | **Term & Billing Cycle** | **Billing Frequency** | **Charge Start Date** | **Charge End Date** |
| ----------------------- | --------------- | -------------- | ------------------------ | --------------------------- | ------------------------- | ------------------------ | --------------------- | --------------------- | ------------------- |
| Microsoft Office 365 E3 | new | 192 | 95.21 | January 25, 2022 | July 20, 2022 | Annual | | January 25, 2022 | July 20, 2022 |

If you changed both the billing plan and the billing term to annual while migrating, the transactions would look like this:

**NCE monthly reconciliation file of January 2022:**

| **Subscription Name** | **Charge Type** | **Unit Price** | **Effective Unit Price** | **Subscription Start Date** | **Subscription End Date** | **Term & Billing Cycle** | **Billing Frequency** | **Charge Start Date** | **Charge End Date** |
| ----------------------- | --------------- | -------------- | ------------------------ | --------------------------- | ------------------------- | ------------------------ | --------------------- | --------------------- | ------------------- |
| Microsoft Office 365 E3 | new | 192 | 192 | January 25, 2022 | January 24, 2023 | Annual | | January 25, 2022 | January 24, 2023 |

If you changed the billing plan to monthly and the billing term to annual while migrating, the transactions would look like this:

**NCE monthly reconciliation file of January 2022:**

| **Subscription Name** | **Charge Type** | **Unit Price** | **Effective Unit Price** | **Subscription Start Date** | **Subscription End Date** | **Term & Billing Cycle** | **Billing Frequency** | **Charge Start Date** | **Charge End Date** |
| ----------------------- | --------------- | -------------- | ------------------------ | --------------------------- | ------------------------- | ------------------------ | --------------------- | --------------------- | ------------------- |
| Microsoft Office 365 E3 | new | 16 | 16 | January 25, 2022 | January 24, 2023 | Annual | Monthly | January 25, 2022 | February 24, 2023 |

## Next steps

* [Sample monthly billing scenarios for new subscriptions, changing license amounts, or suspensions](common-billing-scenarios-monthly.md)
