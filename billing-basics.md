---
title: Overview of Partner Center billing
ms.topic: article
ms.date: 1/11/2023
description: Learn basic billing and invoice information for key terminology for CSP partners in Partner Center.
ms.service: partner-dashboard
ms.subservice: partnercenter-billing
author: sodeb
ms.author: sodeb
---

# Billing overview for the Partner Center CSP program

**Appropriate roles**: Admin agent | Billing admin | Global admin | Helpdesk agent | Sales agent

This article provides the basic billing and invoice information for CSP partners in Partner Center.

## Bill your customers

Microsoft has no requirements or conditions regarding your billing practices.

Check reconciliation files for customer transactions. Use the `CustomerID` and other applicable attributes to find the transactions.

### Billing types

Billing types in Partner Center include:

- Legacy billing (license- and usage-based)
- New Commerce billing (license-based, usage-based, software subscriptions, perpetual software, marketplace, reservations, and savings plans)

### Billing currency

- **Legacy billing**: You’re billed for products in the currency of the country or region in which you’re located. You’re billed the same regardless of the location of the customer to whom you sold the products.

- **New commerce billing**: You’re billed in the partner location currency, regardless of the location of the customer to whom you sold the products. 

## Invoices

Your invoice is a summary of all charges for the current billing period.

The summary includes charges across the program, all products, and all customers.

For examples of monthly and annual billing scenarios, see [Common billing scenarios](common-billing-scenarios.md)

- **Legacy billing:**

  - The billing period is a month but it starts on your billing anniversary date.
  - Your invoices are available two days after your billing anniversary. If your anniversary is on September 12, your invoice will be available after September 14.

- **New commerce billing:**

  - The billing period is a full calendar month.
  - Invoice and reconciliation files are available by the 8th of each month.
  - The products you bought with the label `"New Commerce Experience"` should be on this invoice.

## Invoice in partner location currency

Azure services bought through an Azure plan are priced in US dollars (USD) and billed in your local currency. The exchange rate used is shown on the last page of the invoice. FX rates are updated monthly and applied to the invoice. For a full list of country/region currencies, see [new commerce offers country/region availability and partner currency matrix](https://go.microsoft.com/fwlink/?linkid=2112354).

Thomson Reuters sets the exchange rate two business days before the end of the previous month (1600 UTC). This rate applies to all purchases made during the following month.

**For example,** the exchange rate for December would be the mid-rate published by Thomson Reuters on November 29 and used for all purchases made from December 1 to 31.

## Price lists

Price lists are updated monthly.

Preview price lists are available one month in advance.

To see the latest Cloud Solution Provider programs and offers, use the following steps:

- From the Partner Center, select **Pricing**.

   You find separate price lists for the different types of products that are available.

The following price lists are available on the **Price lists** page:

- **License-based prices** are guaranteed for the term of the subscription, usually 12 months from the purchase date.

- **Usage-based prices** can change on a monthly basis.

- **Prices for products, services, and software subscriptions** are guaranteed for until the subscription is valid. However, prices may change when you renew.

**Adjustments** and **credits** in arrears appear on your next billing invoice, after the credit or adjustment is applied.

> [!IMPORTANT]
> When comparing prices from the price list and reconciliation data, consider your customer’s location if it’s different from yours. However, your invoice is based on your location’s currency.
> 

## New Commerce pricing and billing currencies for different types of products.

| **Product Type**                                | **Pricing Currency**           | **Billing Currency**      |
| ----------------------------------------------- | ------------------------------ | ------------------------- |
| Azure Pay-As-You-Go                             | USD                            | Partner location currency |
| Azure Reservation                               | USD                            | Partner location currency |
| Azure Savings Plan                              | USD                            | Partner location currency |
| Marketplace                                     | USD                            | Partner location currency |
| License-based (Office, Dynamics, and PowerApps) | All supported local currencies | Partner location currency |
| Software subscription                           | All supported local currencies | Partner location currency |
| Perpetual software                              | All supported local currencies | Partner location currency |

> [!NOTE]
> Please be advised that the subscription cost for a charge cycle may be affected by foreign exchange (FX) rates if the product is not priced in the partner billing currency. The FX rate will be determined based on the date of the charge and may vary from the rate in effect at the time of purchase. Please check the applicable FX rate before making a purchase to make sure you get the best price.

## Payment terms

The payment terms for the services provided are net 60 days from the date of the invoice. If the payment isn’t received by the due date, the account will be considered delinquent. Delinquency may result in the suspension of enrollment in the CSP program. Once the past-due amounts have been paid, you’ve full access to your account again.

### Payment Processing

Invoice payments show up in the Partner Center **Billing** workspace in **5 business days.** Check that billing information is up to date before submitting a payment to make sure that payments go through smoothly.

## Credit notes

You might get a credit or rebill because:

- Make corrections to important attributes such as the address, purchase order, cost, and other relevant information.
- Include a tax or regular refund for the original invoice that has already been created.

The first invoice is voided after you get rebilled.

## License-based billing in Partner Center

### Billing frequency

#### Legacy

Billed **monthly** or **annually**. 

#### New commerce

Billed **upfront**, **monthly,** or **annually**.

### Billing period

#### Legacy

Billing period is monthly and starts on the anniversary date you chose when you signed up. Let’s say you signed up on the 15th of the month. This means that your billing period starts on the 15th of every month.

#### New commerce

Billing period is one full calendar month.

### Billing term

#### Legacy

The length of your subscription is 12 months from the date of purchase. However, the number of billing days may change depending on the billing anniversary date. For more information, see the below link:

- [Common legacy billing scenarios](./common-billing-scenarios.md)

#### New commerce

The length of your subscription can be 1, 12, or 36 months from the date of purchase. If you choose to have your subscription end on a specific date (align with the calendar month or coterminate with another subscription), the billing term may be shorter than the full subscription term.

### Charge cycle

#### Legacy

The charge cycle begins on the date of purchase. Depending on your preferences, you can be billed either monthly or annually. It’s important to note that the first charge cycle may be prorated, meaning you’ll be charged until your next billing anniversary date.

#### New commerce

The charge cycle begins on the date of purchase. Depending on your preferences, you can be billed either monthly, annually, or one-time. It’s important to note that the first charge cycle may be prorated if you co-terminate or align the end date with a calendar month. This means you’ll be charged only until the end of the month or the charge end date of the co-terminating subscription. For more information, see the below link:

- [Align subscription end dates](./align-subscription-end-dates.md)

### Subscription cancelation

If you’re considering canceling your subscription, it’s important to understand the refund policy. Here’s what you need to know:

#### Legacy

If you decide to cancel your subscription within the first month of your purchase or renewal, you’re eligible for a full refund. However, if you cancel after the first month, your refund will be prorated. The amount of your refund will be calculated based on how much time is left in your billing term and you’ll only be charged for the time you’ve used.

#### New commerce

If you decide to cancel your subscription within 24 hours of purchasing or renewing it, you’re eligible for a full refund. If you cancel your subscription after 24 hours but before seven days have passed, you’ll get a refund based on how much time has passed since the start of your billing term. The refund will be calculated based on how much time is left in your billing term, so you’ll only be charged for the time you’ve used.

However, if you decide to cancel after seven days have passed, you won’t be eligible for any refund. You’ll be charged for the full term of your subscription, regardless of whether you continue to use the product or not. 

Learn more about the [New Commerce cancellation policy](./create-a-new-subscription.md).

### Subscription renewal

#### Legacy

All license-based subscriptions renew automatically after 12 months.

#### New commerce

All subscriptions with us are set to automatically renew. The exact renewal frequency is determined by the billing term you selected when you first purchased your subscription.

If you choose the monthly billing term, your subscription automatically renews every month. If you select the annual billing term, your subscription renews every 12 months. And if you select the three-year billing term, your subscription renews every 36 months.

This process of automatic renewal makes sure that you can continue to use all of our products and services without interruption. Also, it makes it easier for you to manage your subscription because you don’t have to remember to manually renew it.

Keep in mind that you can stop your subscription from automatically renewing at any time before the next billing term. Learn more about the [New Commerce auto-renew policy](./create-a-new-subscription.md#subscription-renewals).

### Unbilled charges

#### Legacy

Doesn’t support unbilled transactions.

#### New commerce

Unbilled charges may become available within 24 hours, but it could take up to seven days. If you haven’t received it after seven days, contact support.

## Usage-based billing in Partner Center

When you buy a usage-based Azure or marketplace resource through an Azure subscription, you’ll only be charged for how much you use that resource at a **pay as you go** rate.

It’s important to note that this charging model doesn’t apply to certain types of products. For instance, Azure reservations and savings plans offer lower prices if you agree to use it for a certain amount in advance. SaaS products, on the other hand, have their own pricing structures.

However, for all other usage-based Azure and marketplace resources, you can be sure that you’ll only be charged for what you use. You don’t have to worry about being locked into fixed pricing plans or adjusting your usage as needed.


### Billing frequency

#### Legacy

Billed **monthly**. 

#### New commerce

Billed **monthly**.

### Billing period

#### Legacy

Billing period is monthly and starts on the anniversary date you chose when you signed up. Let’s say you signed up on the 15th of the month. This means that your billing period starts on the 15th of every month.

#### New commerce

Billing period is one full calendar month.

### Billing term

#### Legacy

Pay-As-You-Go resources are billed continuously while in use.

#### New commerce

Pay-As-You-Go resources are billed continuously while in use. However, Azure reservations or savings plans have a billing term of either one year or three years.

### Charge cycle

#### Legacy

Charge cycle is monthly starting from the billing anniversary date.

#### New Commerce

Charge cycle is one full calendar month.

### Subscription cancelation

#### Legacy

Cancel your Azure subscription anytime.

#### New Commerce

Cancel your Azure subscription anytime.

### Subscription renewal

####  Legacy

Once you purchase a subscription, it remains active until you cancel it. You have full control over your subscription, allowing you to decide how you want to use the products and services.

#### New Commerce

Once you purchase a subscription, it remains active until you cancel it. You have full control over your subscription, allowing you to decide how you want to use the products and services.

### Unbilled charges

#### Legacy

Doesn’t support unbilled charges.

#### New commerce

Unbilled charges will be available after 24 hours, but sometimes it could take up to a few days depending on several conditions. If you haven’t received it after seven days, contact support.

## Next steps

- [Understand your bill and reconciliation file](read-your-bill.md)
- [Common billing scenarios for CSP program partners](common-billing-scenarios.md)
- [Change billing frequency](common-billing-scenarios.md)
