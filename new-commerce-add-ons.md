---
title: New commerce add-ons
ms.topic: article
ms.date: 02/28/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Learn about new commerce experiences for purchasing add-ons.
author: BrentSerbus
ms.author: brserbus
---

# Introduction: New commerce add-ons

**Appropriate roles**: Admin agent | Sales agent | Global admin

> [!NOTE]
> The new commerce experiences for license-based services include many new capabilities and are available to all Cloud Solution Provider (CSPs). For more information, see [new commerce experiences overview](new-commerce-license-based.md).

Partners can purchase add-ons in new commerce to enable other services that complement a previously purchased product. Some examples of add-ons are calling plans, more disk space, or other features that can be added if the customer has the base services.

## Add-ons in new commerce

New commerce add-ons include similar concepts to traditional license-based add-ons. New commerce add-ons, like traditional license-based, include the concept of prerequisites. Prerequisites are product SKUs the customer must have for the add-on to function correctly.

Prerequisites for an add-on are found the catalog APIs for a given SKU and in the Partner Center catalog user experience. Purchasing add-ons require one or more of the prerequisites to exist on the customer tenant.

The primary difference between traditional and new commerce add-ons is in **how** they're purchased. Partners apply the add-on to the base offer subscription in traditional license-based scenarios. Partner purchase new commerce add-ons from the catalog itself. This purchase experience aligns the add-on discoverability to the base offer, making it easier to find and purchase the add-ons.

Many of the concepts about how add-ons work, from a services perspective, remain true across traditional and new commerce. Both traditional and new commerce transactions register and provision the add-on services. Provisioning happens the same way in both cases. Also, a single add-on's services can compliment more than one base product SKU the add-on is designed to work with.

## Identifying add-ons

Partners can identify Add-ons and get lists of prerequisites by reviewing the SKU details when getting SKUs via the API. Add-ons are also identified in the new commerce offer matrix `ProductSkuPreRequisites` column. SKUs with `ProductSkuPreRequisites` values are add-ons.

## Purchasing add-ons

Add-ons exist for both traditional license-based and new commerce experiences. The key difference is how the add-ons are discovered. New commerce add-ons are discovered and purchased from the catalog, the same place the base offers or prerequisites are found. Traditional license-based add-ons are only discoverable and added by going to the base offer's subscription details page.

New commerce experience add-ons are discovered and purchased in the catalog itself. Partners can filter by new commerce add-ons by selecting the product type dropdown. Add-on products are identified by the information icon next to product SKU. Partners can select this icon to get more information about the add-on's prerequisites.

Partners can get more details about the required products for an add-on by selecting **View compatible base product subscriptions** to show a list of Product SKUs that must exist for the partner to purchase a given add-on.

## Add-on enforcement

Partners are shown helpful information about add-ons when attempting to purchase a new commerce add-on product when the customer doesn't have the prerequisites. Partners can validate whether an add-on's prerequisites exist in the Partner Center catalog, and review page experiences.

When an add-on doesn't have the support prerequisites, the user interface will display a message `The addon is not purchasable without a compatible base product`.

Partners using the CreateCart API will see an error on the cart line item if the add-on doesn't have the required product SKUs. The error code will be 400041 with the description `The addon is not purchasable without a compatible base product`.

## Important details when purchasing add-ons

Add-ons are purchased as distinct product SKUs if the customer satisfies the prerequisites. Add-on subscriptions have their own distinct term alignment. Partners that purchase add-ons will notice the term and associated end date may not be the same as the prerequisite.

Partners convert a product SKU to a higher SKU that already has the add-on services can file a service request with support to turn an add-on off.

Partners are expected to manage the term end dates for add-ons they acquire to ensure there's alignment as needed to the base offers. Partners should avoid situations where a base product SKU term may end leaving behind dependent add-ons that expire later. Active management and alignment of add-on term end dates to their base subscriptions will ensure their customers aren't paying for add-ons whose base offer has expired.
