---
title: Billing frequency changes at Partner Center
description: Information about changing the billing frequency of CSP license-based subscriptions from monthly to annual or from annual to monthly
author: sourishdeb
ms.author: sodeb
ms.service: partner-dashboard
ms.subservice: partnercenter-billing
ms.topic: conceptual
ms.date: 11/8/2022
---

# Billing frequency changes

**Appropriate roles**: Admin agent | Billing admin | Global admin

You can change how often license-based subscriptions are billed, from annual billing to monthly, or from monthly billing to annual.

To learn about changing billing frequency using application programming interfaces (APIs), see [Change the billing cycle for a customer subscription](/partner-center/develop/change-the-billing-cycle).

## Prerequisites

To change the billing frequency of a subscription, you must be a partner in the Cloud Solution Provider (CSP) program, and every subscription in an order must be:

- Active
- A paid subscription
- On the current price list
- On the same billing cycle
- Part of license-based offer
- Part of an *active* promotion (if part of a promotion)

## What happens when you change the billing frequency

When you change the billing frequency of a subscription:

- Promotional pricing or discounts are removed.
- The term of the subscription is reset to 12 months.
- The price is reset to the price on the current price list.
- The billing frequency of every subscription in the order is changed.
- The billing frequency of any add-ons associated with the subscription is changed.
- A pro-rata credit and a new monthly or annual charge appear on the next invoice and reconciliation file.

Note that billing frequency is changed at the order level. When you change the billing frequency of a subscription in an order, the revised billing frequency is applied to all the subscriptions within that order.

## Other considerations

The following considerations also apply to billing frequency changes:

- You can change billing frequency as often as you like.
- You can change billing frequency at any time during a subscription.
- The subscription GUID doesn't change when you change the billing frequency of the subscription.
- There's no charge for changing billing frequency. However, any promotional pricing or discounts are removed, and the subscription is billed at the price on the current price list after you make the change.

## Change legacy billing frequency

To learn about changing billing frequency using application programming interfaces (APIs), see [Change a customer subscription billing cycle](/partner-center/develop/change-the-billing-cycle) at the Partner Center [developer documentation](/partner-center/develop/).

## How to change legacy billing frequency

Billing frequency is changed at the order level. After billing frequency is changed, the revised billing cycle is applied to all the subscriptions within that order.

Use the following steps to change the billing frequency of an online service for a customer:

1. Sign in to the [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Select the customer whose subscription billing frequency you want to change.

3. On the customer's page, select the subscription that you want to change. Notice the renewal date in the following example:

   :::image type="content" source="media/change-billing-frequency/subscriptions-view.png" lightbox="media/change-billing-frequency/subscriptions-view.png" alt-text="Screenshot of subscriptions view in Partner Center showing renewal date before changing billing frequency.":::

4. On the **Subscriptions** page, you can see the current billing frequency:

    :::image type="content" source="media/change-billing-frequency/billing-frequency.png" lightbox="media/change-billing-frequency/billing-frequency.png" alt-text="Screenshot of Partner Center Details screen showing that the current billing frequency is monthly.":::

5. Scroll down, and under **Billing frequency**, select **Monthly** or **Annual**:

    :::image type="content" source="media/change-billing-frequency/billing-monthly-annual.png" lightbox="media/change-billing-frequency/billing-monthly-annual.png" alt-text="Screenshot of selecting monthly or annual billing in Partner Center.":::

6. A confirmation window appears with important information about changing billing frequency, and a list of the subscriptions about to be changed. Select **OK** to make the change.

    :::image type="content" source="media/change-billing-frequency/ok-to-change-billing.png" lightbox="media/change-billing-frequency/ok-to-change-billing.png" alt-text="Screenshot of OK to change billing cycle window at Partner Center.":::

7. The new renewal date is displayed with the user's subscription information.

    :::image type="content" source="media/change-billing-frequency/new-renewal-date.png" lightbox="media/change-billing-frequency/new-renewal-date.png" alt-text="Screenshot of Partner Center screen showing the changed renewal date.":::

8. You can see the changed billing frequency in the subscription details:

    :::image type="content" source="media/change-billing-frequency/billing-change-result.png" lightbox="media/change-billing-frequency/billing-change-result.png" alt-text="Screenshot of Partner Center window showing changed billing frequency.":::

## Next steps

For step-by-step instructions for how to change billing frequency, see [Billing frequency changes](./billing-frequency-changes.md).

- To see examples of reconciliation files following billing frequency changes, see [Renew with annual billing, convert to monthly billing](common-billing-scenarios-annual.md#renew-with-annual-billing-convert-to-monthly-billing) and [Change license quantity and convert from monthly to annual billing](common-billing-scenarios-monthly.md#change-license-quantity-and-convert-from-monthly-to-annual-billing)

- To learn about changing billing frequency using application programming interfaces (APIs), see [Change the billing cycle for a customer subscription](/partner-center/develop/change-the-billing-cycle).
