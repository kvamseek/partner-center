---
title: Products resources
description: Resources that represent purchasable goods or services. Includes resources for describing the product type and shape (SKU), and for checking the availability of the product in an inventory.
ms.date: 12/09/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: iragulati1
ms.author: iragulati
---

# Products resources

Resources that represent purchasable goods or services. Includes resources for describing the product type and shape (SKU), and for checking the availability of the product in an inventory.

## Product

Represents a purchasable good or service. A product by itself isn't a purchasable item.

| Property           | Type                          | Description                                                              |
|--------------------|-------------------------------|--------------------------------------------------------------------------|
| id                 | String                        | The ID for a product.                                                 |
| title              | String                        | The product title.                                                       |
| description        | String                        | The product description.                                                 |
| productType        | [ItemType](#itemtype)         | An object that describes the type categorization(s) of this product.     |
| isMicrosoftProduct | Bool                          | Indicates if the product is a Microsoft product.                          |
| publisherName      | String                        | The name of the product's publisher if available.                          |
| links              | [ProductLinks](#productlinks) | The resource links contained within the product.                         |

## ItemType

Represents the type of a product.

| Property        | Type                          | Description                                                                          |
|-----------------|-------------------------------|--------------------------------------------------------------------------------------|
| id              | String                        | The type identifier.                                                                 |
| displayName     | String                        | The display name for an item type.                                                      |
| subType         | [ItemType](#itemtype)         | Optional. An object that describes a subtype categorization for an item type.     |

## ProductLinks

Contains a list of links for a [Product](#product).

| Property        | Type                                                          | Description                                          |
|-----------------|---------------------------------------------------------------|------------------------------------------------------|
| skus            | [Link](utility-resources.md#link)                             | The link for accessing the underlying SKUs.          |
| links           | [ResourceLinks](utility-resources.md#resourcelinks)           | The resource links contained within a resource.   |

## Sku

Represents a purchasable Stock Keeping Unit (SKU) under a product. 

| Property               | Type             | Description                                                                           |
|------------------------|------------------|---------------------------------------------------------------------------------------|
| id                     | String           | The ID for the SKU. The ID is unique only within the context of its parent product. |
| title                  | String           | The title of the SKU.                                                                 |
| description            | String           | The description of the SKU.                                                           |
| productId              | String           | The ID of the parent [Product](#product) that contains a SKU.                      |
| minimumQuantity        | Int              | The minimum quantity allowed for purchase.                                            |
| maximumQuantity        | Int              | The maximum quantity allowed for purchase.                                            |
| isTrial                | Bool             | Indicates whether a SKU is a trial item.                                           |
| supportedBillingCycles | Array of strings | The list of supported billing cycles for a SKU. Supported values are the member names found in [BillingCycleType](#billingcycletype). |
| purchasePrerequisites  | Array of strings | The list of prerequisite steps or actions that are needed prior to purchasing an item. The supported values are:<br/>  "InventoryCheck" - Indicates that the item's inventory should be evaluated before attempting to purchase an item.<br/> "AzureSubscriptionRegistration" - Indicates that an Azure subscription is needed and must be registered before attempting to purchase an item.  |
| inventoryVariables     | Array of strings | The list of variables needed to execute an inventory check on an item. The supported values are:<br/> "CustomerId" - The ID of the customer that the purchase would be for.<br/> "AzureSubscriptionId" - The ID of the Azure subscription that would be used for an Azure reservation purchase.</br> "ArmRegionName" - The region for which to verify inventory. This value must match the "ArmRegionName" from the SKU's DynamicAttributes. |
| provisioningVariables  | Array of strings | The list of variables that must be provided into the provisioning context of a [cart line item](cart-resources.md#cartlineitem) when purchasing an item. The supported values are:<br/> Scope - The scope for an Azure reservation purchase: "Single", "Shared".<br/> "SubscriptionId" - The ID of the Azure subscription that would be used for an Azure reservation purchase.<br/> "Duration" - The duration of the Azure reservation: "1Year", "3Year".  |
| dynamicAttributes      | key/value pairs  | The dictionary of dynamic properties that apply to an item. The properties in a dictionary are dynamic and can change without notice. Partners should avoid creating strong dependencies on particular keys existing in the value of a property.    |
| links                  | [ResourceLinks](utility-resources.md#resourcelinks) | The resource links contained within the SKU.                   |
| AttestationProperties                  | [AttestationProperties](#attestationproperties) | The attestation properties for a SKU.                   |
| consumptionType                  | String | Is available only if the sku supports consumption such as *overage*.               |
| specializedOfferProperties      | List of specializedOfferProperties | Is available only if the product is subType of SpecializedOffer.      |
| minimumPurchaseCommitment      | [MinimumPurchaseCommitment](#minimumpurchasecommitment) |The fixed amount committed on compute services.       |

## Dynamic SKU attributes

Notable properties relevant to new commerce license-based products and services.

> [!Note] 
> The new commerce experiences for license-based services include many new capabilities and are available to all Cloud Solution Provider (CSPs). For more information, see [new commerce experiences overview](../new-commerce-license-based.md).

| Property        | Type                        | Description                                                                         |
|-----------------|-----------------------------------------------------|-------------------------------------------------------------------------------------|
|hasConstraints|Boolean|Describes if the SKU contains assetContraints|
|isAddon|Boolean|Describes if the SKU is an add-on|
|prerequisiteSkus|array of strings|Describes products and skus the add-on can work with|
|upgradeTargetOffers|array of strings|A list of products and skus the item can upgrade to|
|conversionInstructions|List of conversionInstructions|List of instructions applicable to convert operations|

## specializedOfferProperties

> [!Note] 
> The new commerce experiences for license-based services include many new capabilities and are available to all Cloud Solution Provider (CSPs). For more information, see [new commerce experiences overview](../new-commerce-license-based.md).
> 

Only applicable for product subTypes "SpecializedOffers"

| Property        | Type                        | Description                                                                         |
|-----------------|-----------------------------------------------------|-------------------------------------------------------------|
| startDate       | String                       | Term IDs the instructions apply to |
| endDate       | String                     | Options that define renewals |
| pricingPolicies | List of pricingPolicies | A list of policies that define the promotion discount types and values. |


## MinimumPurchaseCommitment

Attributes of the minimum amount that can be committed on compute services.

| Property        | Type                        | Description                                                                         |
|-----------------|-----------------------------------------------------|-------------------------------------------------------------|
| grain       | String                       | The period of the minimum purchase commitment. |
| currencyCode       | Dictionary<String, String>                     | The "currency" and "symbol" of the minimum amount that can becommitted. |
| amount | Int | The minimum amount that can be committed on compute services. |

## PricingPolicies

Describe the promotion discount types and values.

| Property          | Type               | Description                                                                  |          
|-------------------|--------------------|------------------------------------------------------------------------------|
| type | String | Describe whether the discount is based on percentages or flat rate discounts. |
| value | String  | Defines the amount of the discount applied. |

## Availability

Represents a configuration in which a SKU is available for purchase (such as country/region, currency, and industry segment).

| Property        | Type                        | Description                                                                         |
|-----------------|-----------------------------------------------------|-------------------------------------------------------------------------------------|
| id              | String                        | The ID for this availability. This ID is unique only within the context of its parent [product](#product) and [SKU](#sku). **Note** Availability IDs can change over time. Partners should only rely on this value within a short time span after retrieving it.  |
| productId       | String                        | The ID of the [product](#product) that contains this availability.           |
| skuId           | String                        | The ID of the [SKU](#sku) that contains this availability.                   |
| catalogItemId   | String                        | The unique identifier for this item in the catalog. This ID must be populated into the [OrderLineItem.OfferId](order-resources.md#orderlineitem) or [CartLineItem.CatalogItemId](cart-resources.md#cartlineitem) properties when purchasing the parent [SKU](#sku). **Note** This ID can change over time. You should only rely on this value within a short time after retrieving it. It should only be accessed and used at the time of purchase.  |
| defaultCurrency | String                        | The default currency supported for this availability.                               |
| segment         | String                        | The industry segment for this availability. Supported values are: Commercial, Education, Government, NonProfit. |
| country         | String                                              | The country or region (in ISO country code format) where this availability applies. |
| isPurchasable   | Bool                                                | Indicates whether this availability is purchasable. |
| isRenewable     | Bool                                                | Indicates whether this availability is renewable. |
| RenewalInstructions     | RenewalInstruction                                              | Represents renewal instructions for a given availability. |
| product      | [Product](#product)               | The product this availability corresponds to. |
| sku          | [Sku](#sku)            | The SKU this availability corresponds to. |
| terms           | Array of [Term](#term) resources  | The collection of terms that are applicable to this availability. |
| links           | [ResourceLinks](utility-resources.md#resourcelinks) | The resource links contained within the availability. |

## Renewal instruction

> [!Note] 
> The new commerce experiences for license-based services include many new capabilities and are available to all Cloud Solution Provider (CSPs). For more information, see [new commerce experiences overview](../new-commerce-license-based.md).
> 

Represents renewal instructions for a given availability.

| Property        | Type                        | Description                                                                         |
|-----------------|-----------------------------------------------------|-------------------------------------------------------------|
| applicableTermIds       | Array of strings                       | Term IDs the instructions apply to |
| RenewalOptions       | Array of RenewalOption                     | Options that define renewals |

## RenewalOption	

> [!Note] 
> The new commerce experiences for license-based services include many new capabilities and are available to all Cloud Solution Provider (CSPs). For more information, see [new commerce experiences overview](../new-commerce-license-based.md).
> 

Represents renewal instructions for a given availability.

| Property        | Type                        | Description                                                                         |
|-----------------|-----------------------------------------------------|-------------------------------------------------------------|
| renewToId       | String       | Represents the product and sku to renew to |
| isAutoRenewable       | Bool       | Whether or not the availability can be auto renewed |

## Term

Represents a term for which the availability can be purchased.

| Property              | Type                                        | Description                                                                         |
|-----------------------|-----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
| duration              | String                                      | An ISO 8601 representation of the term's duration. The current supported values are P1M (one month), P1Y (one year) and P3Y (three years). |
| description           | String                                      | The description of the term.           |

## InventoryCheckRequest

Represents a request to check inventory against certain catalog items.

| Property         | Type                                                | Description                                                                                 |
|------------------|-----------------------------------------------------|---------------------------------------------------------------------------------------------|
| targetItems      | Array of [InventoryItem](#inventoryitem)            | The list of catalog items that the inventory check will evaluate.                           |
| inventoryContext | Key/value pairs                                     | The dictionary of context values that are needed to carry out the inventory check(s). Each [SKU](#sku) of the products will define which values (if any) are needed to carry out this operation.  |
| links            | [ResourceLinks](utility-resources.md#resourcelinks) | The resource links contained within the inventory check request.                            |

## InventoryItem

Represents a single item in an inventory check operation. This resource is used for specifying the target items in an input request and is also used to represent the output results of the inventory check operation.

| Property         | Type                                                              | Description                                                                      |
|------------------|-------------------------------------------------------------------|----------------------------------------------------------------------------------|
| productId        | String                                                            | (Required) The ID of the [product](#product).                            |
| skuId            | String                                                            | The ID of the [SKU](#sku). When using this resource as input to an inventory request, this value is optional. If this value isn't provided, then all SKUs under the product will be considered as target items of the inventory check operation.      |
| isRestricted     | Bool                                                              | Indicates whether this item was found to have a restricted inventory.            |
| restrictions     | Array of [InventoryRestriction](#inventoryrestriction)            | The details of any restrictions that are found for this item. This property will only be populated if **isRestricted** = "true". |

## InventoryRestriction

Represents the details of an inventory restriction. These details are only applicable for inventory check output results, not for input requests.

| Property         | Type                  | Description                                                                                 |
|------------------|-----------------------|---------------------------------------------------------------------------------------------|
| reasonCode       | String                | The code that identifies the reason for the restriction.                                    |
| description      | String                | The description of the inventory restriction.                                               |
| properties       | Key/value pairs       | The dictionary of properties that may provide further details on the restriction.           |

## BillingCycleType

An [Enum/dotnet/api/system.enum) with values that indicate a type of billing cycle.

| Value              | Position     | Description                                                                                |
|--------------------|--------------|--------------------------------------------------------------------------------------------|
| Unknown            | 0            | Enum initializer.                                                                          |
| Monthly            | 1            | Indicates that the partner will be charged monthly.                                        |
| Annual             | 2            | Indicates that the partner will be charged annually.                                       |
| None               | 3            | Indicates that the partner will not be charged. This value may be used for trial items.    |
| OneTime            | 4            | Indicates that the partner will be charged one time.                                       |
| Triennial          | 5            | Indicates that the partner will be charged every three years.                              |

## AttestationProperties

Represents an attestation type and if it is required for purchase.

| Property              | Type                                        | Description                                                                         |
|-----------------------|-----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
| attestationType              | String                                      | Indicates the attestation type. Windows 365 products will have the value of Windows365. Windows 365 attestation text is "I understand that each person using Windows 365 Business with Windows Hybrid Benefit also needs to have a valid copy of Windows 10/11 Pro installed on their primary work device." |
| enforceAttestation           | Boolean                                      | Indicates whether attestation is required for purchase.           |
