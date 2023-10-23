---
title: New commerce-specialized offers
ms.topic: article
ms.date: 02/01/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Learn about new commerce-specialized offers.
author: iragulati1
ms.author: iragulati
---

# New commerce-specialized offers

**Appropriate roles**: Admin agent | Sales agent | Global admin

> [!NOTE]
> The new commerce experiences for license-based services include many new capabilities and are available to all Cloud Solution Provider (CSPs). For more information, see the [new commerce experiences overview](new-commerce-license-based.md).

Specialized offers are a new commerce capability. Microsoft enables customized offers for a specific (pre-qualified) set of partners to purchase. These specialized offers are created to address a particular partner's unique business, which needs special offers modeled for their circumstances.

The partner's situation often leads to conversations between Microsoft's business teams and the partner organization. The conversations might result in agreements and terms for specialized offers.

## Discovering and purchasing

Specialized offers can be found by accessing the **Catalog** in Partner Center next to the other offer types. Select **Special offers** to see if there are any specialized offers configured for the partner tenant.

> [!IMPORTANT]
> Many partners will not have specialized offers configured for them as these are very targeted offers.

You can also find specialized offers returned in the catalog APIs, specifically `getSKU`. The SKU information will be consistent with other new commerce SKUs with extra details about the specialized offers. Information about the catalog APIs can be found in the [getSKUs articles](/partner-center/develop/get-a-sku-by-id).

> [!IMPORTANT]
>
> - If you are purchasing using the Partner Center catalog you may see duplicate SKUs for a given specialized offer product. These SKUs have specific terms and billing plans.
> - You should review the term and billing plans on the **review** screen prior to submitting your purchase.
> - You can select the SKUs for a given product and then remove SKUs containing the billing plans and terms you do not want to purchase.

## Managing subscriptions

Subscription management for specialized offers is done similarly to regular new commerce offers. For more information, see [Create a new subscription](create-a-new-subscription.md#increase-or-decrease-licenses-in-new-commerce-license-based-subscriptions).

See [Upgrade a subscription](add-licenses-or-services-to-an-existing-subscription.md#upgrade-a-subscription) for information on identifying eligible transition paths and executing transitions. It is important to identify if your target subscription, post-transition, is intended to be a specialized offer or a standard offer (a generally available offer). If eligible, standard offers, can be upgraded to other standard offers or specialized offers. Specialized offers can also be upgraded to other specialized offers or to standard offers.

Upgrade paths for specialized offers will not appear on the Offer List Matrix. Midterm transitions from a standard offer to a specialized offer of the same base offer are not permitted; however, a scheduled change request can be set to enable this transition type at renewal.

## Pricing and billing

Specialized offers aren't found in the new commerce price lists. Specialized offers and their terms and conditions are available via the catalog APIs or when browsing the specialized offers in the Partner Center catalog.

The catalog enables you to select and view details of offers to verify their terms and other properties.

Specialized offers will show up in the recon file like all other new commerce purchases. These line items will have the product SKU IDs of the special offer purchased, the amounts, and unit prices like other purchases. **DiscountDetailsDescription** in the recon file may include information if the specialized offer includes discount details.

## API details

Specialized offers can be found using the `getSKU` APIs. The SKU object will identify these specialized offers where the product is (what) and the SKU contains (what). Partners can purchase the specialized offers like any other new commerce product SKU as part of the **catalogItemId** when creating and checking out a cart.

## Next steps

- [Promotions resources](/partner-center/develop/promotion-resources)
- [New commerce promotions](new-commerce-promotions.md)
