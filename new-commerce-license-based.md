---
title: New commerce license-based overview
ms.topic: article
ms.date: 02/14/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Learn about new commerce experiences for purchasing license-based online services.
author: brentserbus
ms.author: brserbus
---

# New commerce experience for license-based services

**Appropriate roles**: Admin agent | Sales agent | Global admin

The *new commerce experience* for license-based services offers partners more flexibility and capabilities when purchasing and managing products like Microsoft 365, Dynamics 365, Microsoft Intune, and other services that have been available in Partner Center for years.

Partners can continue to purchase license-bases services in the traditional way if they want, but they'll also see *New commerce* indicators for offers in the catalog.

## New capabilities

New commerce is less about *what* partners are purchasing and more about *how* they're purchasing and managing. Many of the basics remain the same between traditional and new commerce, but new commerce has new capabilities:

- [More flexibility for managing your services](#more-flexibility-for-managing-your-services)
- [New pricing and add-on options](#new-pricing-and-add-on-options)
- [Simplified and enhanced billing](#simplified-and-enhanced-billing)

### More flexibility for managing your services

The new commerce experience offers partners more flexibility for managing services, including the ability to:

- Control subscription renewals
- Upgrade partial seats when moving to new SKUs
- Schedule changes to subscriptions that take effect at the end of terms

There's also new support for enterprise SKU upgrades

### New pricing and add-on options

New pricing and add-on options in the new commerce experience include:

- Ability to get pricing for services programmatically through APIs
- More flexibility to acquire add-on services because purchases are no longer dependent on base-offer transactions
- New monthly term options that give partners more flexibility for their businesses

### Simplified and enhanced billing

Billing has been simplified and enhanced by:

- Consolidating billing and invoicing using the partner's currency
- Making billing dates consistent by basing them on months instead of mid-month dates that can vary across partner tenants
- Supporting monthly, annual, or three-year terms for many subscriptions
- Providing monthly, annual, or up-front billing for many subscriptions

## What isn't changing

Many aspects of how partners do business in Partner Center aren't changing with the new commerce experiences. For example, common tasks and workflows that aren't changing include:

- Creating customers
- Requesting relationships with new customers
- Purchasing and managing scenarios for software subscriptions, perpetual software, Azure services, and marketplace offers

## Learning about new commerce

Partners now have a choice:

- They can continue to purchase traditional, license-based services.
- They can purchase through the new commerce experience.

Partners who decide to transact with the new commerce services need to become familiar with how the new commerce license-based services work. The following articles in this section explain how to do business using the new commerce offers and subscriptions.

### Enhancements and new scenarios

The following scenarios are new or have enhancements to support the new commerce experiences:

- [Discover and get pricing for new commerce offers](pricing-and-offers.md#new-commerce-license-based-pricing) and review the [New commerce price sheet APIs](/partner/develop/get-a-price-sheet)
- Purchasing new commerce license-based services [using the Partner Center APIs](/partner-center/develop/purchase-new-commerce-license-based)
- [Promotions in new commerce](new-commerce-promotions.md), including [Get Promotions](/partner-center/develop/get-promotions) and [Verify Promotions](/partner-center/develop/verify-promotion-eligibility)
- [Telco offers enabling pay-as-you-go overage (E5)](new-commerce-telco-payg.md), including [Get overage](/partner-center/develop/get-subscription-overage) and [update overage](/partner-center/develop/update-subscription-overage)
- [Add-ons in new commerce](new-commerce-add-ons.md)
- [Converting mid-term trials or paid SKUs](create-a-new-subscription.md) with different quantities, terms, and billing plans. New commerce also supports upgraded SKUs as partial seat upgrades to one target subscription.

## Key differences between traditional and new commerce

New commerce offers have new capabilities and flexibility in how partners transact and manage their subscriptions.

**Catalog**:

- Traditional, license-based *offers* were defined by an *offer ID*.
- In new commerce, offers are defined as *product*, *SKU*, and *availability* (or *term*).

  This new commerce identifier for Partner Center API users is described as a *catalogItemId*. For more information about the cart line items, see the [partner center API documentation](/partner-center/develop/create-a-cart).

**Pricing**:

- Traditional, license-based prices were per *currency*.
- In new commerce, pricing is defined by *customer market*. A partner who wants pricing for a customer transaction will need to get the price list for the customer's market.

For more information about price lists in new commerce, see [the pricing and offers article](pricing-and-offers.md#new-commerce-license-based-pricing).

**Promotions**:

- Traditional, license-based promotions were sometimes implemented as discounts and other times as offers with *promo* in their name.
- In new commerce, promotions are simplified by always enabling them as discounts applied to the partner price.

For more information about promotions, see [New commerce promotions](new-commerce-promotions.md).

**Subscription management**:

- In new commerce, *canceling and reducing subscription licenses* is done differently.

For more information about cancellation policies, see [Manage customer subscriptions](create-a-new-subscription.md#cancel-a-subscription).
