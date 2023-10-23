---
title: Cart resources
description: A partner places an order in a cart when a customer wants to buy a subscription from a list of offers.
ms.date: 08/23/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: iragulati1
ms.author: iragulati
---

# Cart resources

**Applies to**: Partner Center | Partner Center operated by 21Vianet |  Partner Center for Microsoft Cloud for US Government

A partner places an order when a customer wants to buy a subscription from a list of offers.

## Cart

Describes a cart.

| Property              | Type             | Description                                                                                            |
|-----------------------|------------------|--------------------------------------------------------------------------------------------------------|
| id                    | string           | A cart identifier that is supplied upon successful creation of the cart.                               |
| creationTimeStamp     | DateTime         | The date the cart was created, in date-time format. Applied upon successful creation of the cart.      |
| lastModifiedTimeStamp | DateTime         | The date the cart was last updated, in date-time format. Applied upon successful creation of the cart. |
| expirationTimeStamp   | DateTime         | The date the cart will expire, in date-time format. Applied upon successful creation of cart.          |
| lastModifiedUser      | string           | The user who last updated the cart. Applied upon successful creation of cart.                          |
| lineItems             | Array of objects | An Array of [CartLineItem](#cartlineitem) resources.                                                   |
| status                | string           | The status of the cart. Possible values are "Active" (can be updated/submitted) and "Ordered" (has already been submitted). |

## CartLineItem

Represents one item contained in a cart.

| Property             | Type                             | Description                                                                                                                                           |
|----------------------|----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
| id                   | string                           | A unique identifier for a cart line item. Applied upon successful creation of cart.                                                                   |
| catalogItemId        | string                           | The catalog item identifier.                                                                                                                          |
| friendlyName         | string                           | Optional. The friendly name for the item defined by the partner to help disambiguate.                                                                 |
| quantity             | int                              | The number of licenses or instances.                                                                                                                  |
| currencyCode         | string                           | The currency code.                                                                                                                                    |
| billingCycle         | Object                           | The type of billing cycle set for the current period.                                                                                                 |
| termDuration         | string                           | An ISO 8601 representation of the term's duration. The current supported values are P1M (one month), P1Y (one year) and P3Y (three years).                                |
| participants         | List of Object String pairs      | A collection of PartnerID on Record on the purchase.                                                                                          |
| provisioningContext  | Dictionary<string, string>       | Additional context used when provisioning the purchased item. To determine which values are needed for a particular item, refer to the SKU's provisioningVariables property. |
| orderGroup           | string                           | A group to indicate which items can be submitted together in the same order.                                                                          |
| addonItems           | List of **CartLineItem** objects | A collection of cart line items for addons. These items will be purchased towards the base subscription that results from the root cart line item's purchase. |
| error                | Object                           | Applied after cart is created if an error occurred.                                                                                                    |
| renewsTo             | Array of objects                 | An array of [RenewsTo](#renewsto) resources.                                                                            |
| AttestationAccepted             | bool                 | Indicates agreement to offer or sku conditions. Required only for offers or skus where SkuAttestationProperties or OfferAttestationProperties enforceAttestation is True.   |
| promotionId             | string                 | The promotion ID that is about to be applied to the cart line item.     |
| customTermEndDate     | DateTime                | The end date of the first billing term of the new subscription. |

## Pricing

Represents the price details. Price amounts are provided before taxation.

| Property              | Type             | Required        | Description |
|-----------------------|------------------|-----------------|-------------------------------------------------------------------------------------------------------------------------|
| listPrice             | double           | No              | Price listed in the catalog without any pricing modifiers applied.                                                      |
| discountedPrice       | double           | No              | Price after applying all applicable pricing modifier.                                                      |
| proratedPrice         | double           | No              | Discounted price after proration has been performed.                                                    |
| price                 | double           | No              | Price in the applicable billing currency after all discounts have been applied and proration has been performed.        |
| extendedPrice         | double           | No              | Price of the line item with quantity, discounts and proration applied, in the applicable billing currency.              |

## RenewsTo

Represents one item contained in a cart line item.

| Property              | Type             | Required        | Description |
|-----------------------|------------------|-----------------|-------------------------------------------------------------------------------------------------------------------------|
| termDuration          | string           | No              | An ISO 8601 representation of the renewal term's duration. The current supported values are **P1M** (one month) and **P1Y** (one year). |

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Partner Center error codes](error-codes.md).

## CartError

Represents an error that occurs after a cart is created.

| Property         | Type                                   | Description                                                                                   |
|------------------|----------------------------------------|-----------------------------------------------------------------------------------------------|
| errorCode        | [CartErrorCode](#carterrorcode) | The type of cart error.                                                                       |
| errorDescription | string                                 | The error description, including any notes about supported values, default values, or limits. |
| additionalInformation | [AdditionalInformation](#additionalinformation) | Additional information for the error. |

## AdditionalInformation

Additional information about the error.

| Property         | Type                                   | Description                                                                                   |
|------------------|----------------------------------------|-----------------------------------------------------------------------------------------------|
| availableQuantity   | int | The number of remaining licenses that can be purchased for the given product SKU.  |
| purchasedQuantity | int| The number of licenses being purchased.  |

## CartErrorCode

Types of cart errors.

| Name                             | ErrorCode   | Description
|----------------------------------|-------------|-----------------------------------------------------------------------------------------------|
| CurrencyIsNotSupported           | 10000   | Currency isn't supported for given market  |
| CatalogItemIdIsNotValid          | 10001   | Catalog item ID isn't valid  |
| QuotaNotAvailable                | 10002   | Not enough quota available  |
| InventoryNotAvailable            | 10003   | Inventory isn't available for selected offer  |
| ParticipantsIsNotSupportedForPartner  | 10004   | Setting participants isn't supported for Partner  |
| UnableToProcessCartLineItem      | 10006   | Unable to process cart line item.  |
| SubscriptionIsNotValid           | 10007   | Subscription isn't valid.  |
| SubscriptionIsNotEnabledForRI    | 10008   | Subscription isn't enabled for reservation purchases.  |
| SandboxLimitExceeded             | 10009   | The sandbox limit has been exceeded.  |
| InvalidInput                     | 10010   | Generic input isn't valid.  |
| SubscriptionNotRegistered        | 10011   | Subscription isn't valid.  |
| AttestationNotAccepted           | 10012   | Attestation hasn't been accepted.  |
| MaxAllowedSeatsPerSubscriptionExceeded          | 10015   | Requested number of seats exceeds the limit. |
| Unknown                          | 0   | Default value   |

## CartCheckoutResult

Represents the result of a cart checkout.

| Property    | Type                                              | Description                     |
|-------------|---------------------------------------------------|---------------------------------|
| orders      | List of [Order](order-resources.md#order) objects.         | The collection of orders.       |
| orderErrors | List of [OrderError](#ordererror) objects. | The collection of order errors. |

## OrderError

Represents an error that occurs during a cart checkout when an order is created.

| Property     | Type   | Description                                     |
|--------------|--------|-------------------------------------------------|
| orderGroupId | string | The order group ID of the order with the error. |
| code         | int    | The error code.                                 |
| description  | string | The description of the error.                   |
