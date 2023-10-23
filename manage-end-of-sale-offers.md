---
title: Manage end-of-sale offers  
ms.topic: how-to
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Learn how to manage end-of-sale offers.
author: migolova
ms.author: migolova
ms.date: 04/13/2023
---

# Manage end-of-sale offers  

**Appropriate roles**: Admin agent | Billing admin | Global admin | Helpdesk agent | Sales agent

**End of sale** (EOS) represents offers that are no longer available for purchase in the new commerce experience. EOS scenarios can apply to entire product/SKUs, regions/markets, and specific term durations. For these offers, existing subscriptions aren't impacted (for example, services continue to work). EOS is currently supported for NCE licensed-based services and software products.

**End of life** (EOL) indicates offers that are no longer available for purchase in the new commerce experience, and existing subscriptions will no longer be renewed. EOL isn't currently live, but when it is, partners will receive guidance.

Partners can identify which offers have an upcoming EOS through the price list, see [Pricing and offers](pricing-and-offers.md). When an offer has reached the EOS effective date indicated in the price list, it's no longer available within the Partner Center catalog, including portal and APIs.

## Existing subscriptions

For existing subscriptions purchased before EOS effective date, service won't be impacted. Subscriptions continue to renew until the partner modifies their autorenew settings, the subscription expires, or EOL is enforced. Partners can continue to manage their existing subscriptions (for example, update seats).

## Changes to subscriptions  

For **NCE licensed-based offers**, once EOS effective date has been reached, partners won't be able to:

- Transition (also known as 'upgrade'), convert trials, or schedule changes to EOS offers.  
- Mid-term and scheduled changes for term duration and billing frequency combinations that are EOS.
- If a partner has already submitted a scheduled change prior to EOS effective end date, the change will be allowed and processed.  

For **software offers**, once EOS effective date has been reached, partners will no longer be able to:

- Schedule changes with a billing frequency that has become EOS.  
- If a partner has already scheduled the change prior to EOS effective end date, the change will be allowed and processed.

For **perpetual software**, there's no impact as these are one-time purchases without the ability to renew.

Partners can transition EOS offers to active product/SKUs and term durations.

## Next steps

- [Manage customer subscriptions](create-a-new-subscription.md)
- [Move license-based customers from other channels, tenants, and partners to the Cloud Solution Provider (CSP) program](transition-seat-based-services.md)
- [Migrate subscriptions to new commerce](migrate-subscriptions-to-new-commerce.md)
