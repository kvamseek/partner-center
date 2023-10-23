---
title: Offer resources
description: Describes a product listed in the reseller catalog that they can offer to their customers.
ms.date: 08/23/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: iragulati1
ms.author: iragulati
---

# Offer resources

**Applies to**: Partner Center | Partner Center operated by 21Vianet |  Partner Center for Microsoft Cloud for US Government

Describes a product listed in the reseller catalog that can be offered to customers.

## Offer

| Property                    | Type                      | Description                                                                                                                                                                |
|-----------------------------|---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| id                          | string                    | The offer identifier                                                                                           |
| name                        | string                    | The offer name                                                                                                 |
| description                 | string                    | A description of the offer                                                                                     |
| minimumQuantity             | int                       | The minimum quantity available                                                                                 |
| maximumQuantity             | int                       | The maximum quantity available                                                                                 |
| rank                        | int                       | The offer rank or priority compared to other categories in the same product line. This property should be set only if there's more than one offer for a given product line.  |
| uri                         | string                    | The offer URI.                                                                                                  |
| locale                      | string                    | The locale in which the offer applies.                                                                          |
| country                     | string                    | The country/region  where the offer applies.                                                                    |
| category                    | [OfferCategory](#offercategory)           | The category of the offer.                                                                   |
| limitUnitOfMeasure          | string                    | A value that indicates the type of purchase limitation. Possible values include:<br/> "None" - There are no restrictions on the number of subscriptions based on the offer purchased.<br/> "Concurrent" - The number of subscriptions that can exist on the customer tenant at a given time, including subscriptions that are active or canceled. This value applies mostly to small business offers where license counts are less than 300. Deprovisioned subscriptions don't count.<br/> "LifeTime" - The number of subscriptions that can exist for the lifetime of the customer tenant. This value is most applicable to Trials. Deprovisioned subscriptions don't count.      |
| limit                       | int                       | The number of subscriptions that can be purchased of the offer based on the limitUnitOfMeasure.                |
| prerequisiteOffers          | string                    | The prerequisite offers.                                                                                        |
| isAddOn                     | boolean                   | A value indicating whether the instance is an addon.                                                           |
| hasAddOns                   | boolean                   | A value indicating whether the offer has any addons.                                                           |
| isAvailableForPurchase      | boolean                   | A value indicating whether the instance is available for purchase.                                             |
| billing                     | string                    | Specifies the billing type for the line item purchase: "none", "usage", or "license".                           |
| supportedBillingCycles      | array of strings          | Indicates the billing cycles supported for the offer. Supported values are the member names found in [BillingCycleType](product-resources.md#billingcycletype)   |
| isAutoRenewable             | boolean                   | A value indicating whether the offer renews automatically.                                                      |
| upgradeTargetOffers         | array of strings          | The list of offers that the offer can be upgraded to.                                                          |
| conversionTargetOffers      | array of strings          | The list of offers that the offer can be converted to.                                                         |
| reselleeQualifications      | array of strings          | The qualifications required by the customer in order for a partner to purchase the offer for that customer.     |
| resellerQualifications      | array of strings          | The qualifications required by the partner in order to purchase the offer for a customer.                       |
| salesGroupId                | string                    | A string used to group offers into separate orders.                                                             |
| isTrial                     | boolean                   | A value indicating whether the offer is a trial offer.                                                               |
| product                     | [OfferProduct](#offerproduct)           | Gets the offer product.                                                                           |
| unitType                    | string                    | The type of the unit.                                                                                      |
| links                       | [OfferLinks](#offerlinks)               | The offer's "learn more" link.                                                                    |
| attributes                  | [ResourceAttributes](utility-resources.md#resourceattributes) | The metadata attributes corresponding to the offer.                         |
| AttestationProperties       | [AttestationProperties](#attestationproperties) | The attestation properties for a SKU.                   |

## OfferCategory

Describes the categorization of an offer, including the rank or
priority of the offer category compared to others in the same product
line.

| Property   | Type                                                           | Description                                                                                                                                                                |
|------------|----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| id         | string                                                         | The category identifier.                                                                                                                                                   |
| name       | string                                                         | The category name.                                                                                                                                                         |
| rank       | int                                                            | The category rank or priority compared to other categories in the same offer. This property should be set only if there's more than one offer category for a given offer. |
| locale     | string                                                         | The locale in which the offer applies.                                                                                                                        |
| country    | string                                                         | The country/region where the offer applies.                                                                                                                   |
| links      | [ResourceLinks](utility-resources.md#resourcelinks)           | The resource links corresponding to the OfferCategory.                                                                                                                     |
| attributes | [ResourceAttributes](utility-resources.md#resourceattributes) | The metadata attributes corresponding to the OfferCategory.                                                                                                                |

## OfferLinks

Contains links for learning more information about the offer.

| Property  | Type | Description                 |
|-----------|------|-----------------------------|
| learnMore | Link | The "learn more" link.      |
| self      | Link | The self-URI                |
| next      | Link | The next page of items.     |
| previous  | Link | The previous page of items. |

## OfferProduct

A product or service that may have more than one offer associated with it, each with different sets of features and targeted at different customer needs.

| Property | Type   | Description              |
|----------|--------|--------------------------|
| Id       | string | The category identifier. |
| Name     | string | The category name.       |
| Unit     | string | The product unit.        |

## AttestationProperties

Represents an attestation type and if it's required for purchase.

| Property              | Type                                        | Description                                                                         |
|-----------------------|-----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
| attestationType              | string                                      | Indicates the attestation type. For Windows 365, the value is Windows365. Windows 365 attestation text is "I understand that each person using Windows 365 Business with Windows Hybrid Benefit also needs to have a valid copy of Windows 10/11 Pro installed on their primary work device." |
| enforceAttestation           | boolean                                      | Indicates whether attestation is required for purchase.           |
