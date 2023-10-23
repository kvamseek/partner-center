---
title: Credit limit enforcement
ms.topic: how-to
ms.date: 04/25/2022
description: Learn about your credit limit and how it's calculated. Includes FAQ.
ms.service: partner-dashboard
ms.subservice: partnercenter-billing
author: sodeb
ms.author: sodeb
---

# Credit limit enforcement (CLE)

**Appropriate roles**: Billing admin

## Your credit limit and how it works

Your credit limit is the maximum amount (in US dollars) that you as a partner can spend to purchase products or subscriptions in Partner Center. If you exceed your credit limit, you'll be unable to make new purchases until sufficient payment has been made. Your existing subscriptions will continue uninterrupted.

Credit limits apply to offers in Azure plan, Azure reservations, Software, Marketplace, Azure 145 P, Office, and Dynamics products. Credit limits do not apply to renewals and ongoing consumption.

We assign your credit limit at the tenant level during your onboarding period. We base it on your forecasted revenue, purchasing prowess, and payment history. We then use the following formula to calculate your available balance:

**[Credit Limit – (Incoming Purchase + Outstanding Unpaid Invoices + Unbilled Charges – Overpayment)]**

## Frequently Asked Questions

### Is my credit limit set at the tenant or global level?

The tenant level. For example, suppose you operate from the US, Canada, and Japan. If the Canadian tenant reaches its credit limit, then that tenant will receive a notification when they attempt to make a purchase in Partner Center. The other tenants will not be affected.

### If I exceed my credit limit, can I continue servicing existing customers and subscriptions with full access?

Yes. Your customers' existing subscriptions will continue without interruption. However, you cannot buy new subscriptions for your customers.

### Does CLE apply to both direct bill partners and indirect providers?

Yes, it applies to both.

### After I submit my payment to reinstate my account, when can I purchase more subscriptions?

You should be able to resume purchasing within 24 hours of your payment, assuming Microsoft has received all of the requirements to proceed with the credit check process.

### How can I check my credit limit?

Contact [ucmwrcsp@microsoft.com](mailto:ucmwrcsp@microsoft.com) to see your credit limit and get information about recent purchases.

### Do invoices that are in dispute count against the credit limit?

Yes. However, you can contact Microsoft at [ucmwrcsp@microsoft.com](mailto:ucmwrcsp@microsoft.com) to resolve the issue.

### How soon will I hear back if I write to ucmwrcsp@microsoft.com?

You should receive a response in less than 24 hours.

### What criteria does Microsoft use for setting a partner's credit limit?

We determine your credit limit based on your forecasted revenue, purchasing prowess, and payment history.

### Is the credit limit currently enforced on the New Commerce Experience?

Yes. Credit limits apply to all CSP programs and products in Partner Center.

### Who will receive the notification when my organization is nearing its credit limit?

Your organization's Finance Account Payable contact should receive the notification.

## Next steps

[Billing basics](./billing-basics.md)
