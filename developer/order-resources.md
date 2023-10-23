---
title: Order resources
description: A partner places an order when a customer wants to buy a subscription from a list of offers.
ms.date: 07/14/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: iragulati1
ms.author: iragulati
---

# Order resources

**Applies to**: Partner Center | Partner Center operated by 21Vianet |  Partner Center for Microsoft Cloud for US Government

A partner places an order when a customer wants to buy a subscription from a list of offers.

> [!NOTE]
>The Order resource has a rate limit of 500 requests per minute per tenant identifier.

## Order

Describes a partner's order.

| Property           | Type                                               | Description                                                 |
|--------------------|----------------------------------------------------|-------------------------------------------------------------|
| id                 | string                                             | An order identifier that is supplied upon successful creation of the order.                                   |
| alternateId        | string                                             | A friendly identifier for the order.                                                                          |
|referenceCustomerId | string                                             | The customer identifier. |
| billingCycle       | string                                             | Indicates the frequency with which the partner is billed for this order. Supported values are the member names found in [BillingCycleType](product-resources.md#billingcycletype). The default is "Monthly" or "OneTime" at order creation. This field is applied upon successful creation of the order. |
| transactionType    | string                                             | Read-only. The transaction type of the order. Supported values are 'UserPurchase', 'SystemPurchase', or 'SystemBilling' |
| lineItems          | array of [OrderLineItem](#orderlineitem) resources | An itemized list of the offers the customer is purchasing including the quantity.        |
| currencyCode       | string                                             | Read-only. The currency used when placing the order. Applied upon successful creation of the order.           |
| currencySymbol     | string                                             | Read-only. The currency symbol associated with the currency code. |
| creationDate       | datetime                                           | Read-only. The date the order was created, in date-time format. Applied upon successful creation of the order.                                   |
| status             | string                                             | Read-only. The status of the order.  Supported values are the member names found in [**OrderStatus**](#orderstatus).        |
| links              | [OrderLinks](utility-resources.md#resourcelinks)           | The resource links corresponding to the Order.            |
| attributes         | [ResourceAttributes](utility-resources.md#resourceattributes) | The metadata attributes corresponding to the Order.       |

## OrderLineItem

An order contains an itemized list of offers, and each item is represented as an OrderLineItem.

| Property             | Type                                      | Description                                                                                                                                                                                                                                |
|----------------------|-------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| lineItemNumber       | int                                       | Each line item in the collection gets a unique line number, counting up from 0 to count-1.                                                                                                                                                 |
| offerId              | string                                    | The ID of the offer.                                                                                                                                                                                                                       |
| subscriptionId       | string                                    | The ID of the subscription.                                                                                                                                                                                                                |
| parentSubscriptionId | string                                    | Optional. The ID of the parent subscription in an add-on offer. Applies to PATCH only.                                                                                                                                                     |
| friendlyName         | string                                    | Optional. The friendly name for the subscription defined by the partner to help disambiguate.                                                                                                                                              |
| quantity             | int                                       | The number of licenses or instances.                                                   |
| customTermEndDate    | DateTime                                  | The end date of the first billing term of the new subscription.                        |
| termDuration         | string                                    | An ISO 8601 representation of the term's duration. The current supported values are **P1M** (1 month), **P1Y** (1 year) and **P3Y** (3 years).                               |
| transactionType      | string                                    | Read-only. The transaction type of the line item. Supported Values are 'new', 'renew', 'addQuantity', 'removeQuantity', 'cancel', 'convert', or 'customerCredit'. |
| partnerIdOnRecord    | string                                    | When an indirect provider places an order on behalf of an indirect reseller, populate this field with the PartnerID of the **indirect reseller only** (never the ID of the indirect provider). This ensures proper accounting for incentives. |
| provisioningContext  | [ProvisioningContext](#provisioningcontext)   | Information required for provisioning for some items in the catalog. The provisioningVariables property in a SKU indicates which properties are required for specific items in the catalog.
| links                | [OrderLineItemLinks](#orderlineitemlinks) | Read-only. The resource links corresponding to the order line item.                                                                                                                                                                           |
| renewsTo             | [RenewsTo](#renewsto)                         |Renewal term duration details.                                                                           |
| AttestationAccepted             | bool                 | Indicates agreement to offer or sku conditions. Required only for offers or skus where SkuAttestationProperties or OfferAttestationProperties enforceAttestation is True.                                                                            |
| Pricing              | [Pricing](#pricing)                       | List price details.                                                                                         |
| purchaseCommitment              | [PurchaseCommitment](#purchasecommitment)                       |The fixed amount committed on compute services.                                                   |

## RenewsTo

Represents the renewal term duration details.

| Property              | Type             | Required        | Description |
|-----------------------|------------------|-----------------|-------------------------------------------------------------------------------------------------------------------------|
| termDuration          | string           | No              | An ISO 8601 representation of the renewal term's duration. The current supported values are **P1M** (1 month) and **P1Y** (1 year). |

## Pricing

Represents the price details. Price amounts are provided before taxation.

| Property              | Type             | Required        | Description |
|-----------------------|------------------|-----------------|-------------------------------------------------------------------------------------------------------------------------|
| listPrice             | double           | No              | Price listed in the catalog without any pricing modifiers applied.                                                      |
| discountedPrice       | double           | No              | Price after applying all applicable pricing modifier.                                                      |
| proratedPrice         | double           | No              | Discounted price after proration has been performed.                                                    |
| price                 | double           | No              | Price in the applicable billing currency after all discounts have been applied and proration has been performed.        |
| extendedPrice         | double           | No              | Price of the line item with quantity, discounts and proration applied, in the applicable billing currency.              |

## OrderLinks

Represents the resource links corresponding to the order.

| Property           | Type                                         | Description                                                                   |
|--------------------|----------------------------------------------|-------------------------------------------------------------------------------|
| provisioningStatus | [Link](utility-resources.md#link)            | When populated, the link to retrieve provisioning status for the order.       |
| self               | [Link](utility-resources.md#link)            | The link to retrieve the order resource.                                      |

## OrderLineItemLinks

Represents the full subscription associated with the order.

| Property           | Type                                         | Description                                                                          |
|--------------------|----------------------------------------------|--------------------------------------------------------------------------------------|
| provisioningStatus | [Link](utility-resources.md#link)            | When populated, the link to retrieve the [provisioning status](#orderlineitemprovisioningstatus) of the line item.       |
| sku                | [Link](utility-resources.md#link)            | The link to retrieve SKU information for the catalog item bought.                    |
| subscription       | [Link](utility-resources.md#link)            | When populated, the link to the full subscription information.                       |
| activationLinks    | [Link](utility-resources.md#link)            | When populated, the GET resource for links to activate the subscription.             |

## OrderStatus

An [Enum/dotnet/api/system.enum) with values that indicate the state of the order.

| Value              | Position     | Description                                     |
|--------------------|--------------|-------------------------------------------------|
| unknown            | 0            | Enum initializer.                               |
| completed          | 1            | Indicates that the order is completed.          |
| pending            | 2            | Indicates that the order is processing.      |
| cancelled          | 3            | Indicates that the order has been cancelled.    |
| suspended | 4            | Indicates that the order has been suspended. To learn more, see: [Subscription lifecycle states - NCE suspended](../subscription-lifecycle.md).     |
| pending review  | 5            | Indicates that the order is pending secondary review. Partners may be required to upload documentation. See [Secondary deal review training deck](https://partner.microsoft.com/resources/detail/secondary-review-overview-pdf) to learn what to expect if you're selected for a secondary deal review.     |
| pending po upload             | 6            | Indicates that partner is to upload their Customer Purchase Order and enter details as outlined within for review by Microsoft.
| po upload complete           | 7           | Indicates that Purchase Order has been submitted by partner and Microsoft is reviewing. No further action required by the partner.
| po review rejected             | 8           | Indicates that this order didn't pass the secondary review and won't be processed.      |
| partial success           | 9           | Indicates that one or more subscriptions in the order have an issue. Partners should repurchase unfulfilled subscriptions.    |
| error | 10            | Indicates that the order resulted in an error. Partners should repurchase.     |

## OrderLineItemProvisioningStatus

Represents the provisioning status of an [OrderLineItem](#orderlineitem).

| Property                        | Type                                | Description                                                                                |
|------------------------------------|-------------------------------------|--------------------------------------------------------------------------------------------|
| lineItemNumber                  | int                                 | The unique line number of the order line item. Values range from 0 to count-1.             |
| status                          | string                              | The provisioning status of the order line item. Values include:</br>**Fulfilled**: Fulfillment of the order is successfully completed and the user will be able to use the reservations</br>**Unfulfilled**: Not fulfilled due to cancellation</br>**PrefulfillmentPending**: Your request is still processing, fulfillment isn't yet complete |
| quantityProvisioningInformation | List<[QuantityProvisioningStatus](#quantityprovisioningstatus)> | A list of quantity provisioning status information for the order line item. |

## QuantityProvisioningStatus

Represents the provisioning status by quantity.

| Property                           | Type                                         | Description                                          |
|------------------------------------|----------------------------------------------|------------------------------------------------------|
| quantity                           | int                                          | The number of items.                                 |
| status                             | string                                       | The status of the number of items.                   |

## ProvisioningContext

Information required for provisioning for some items in the catalog. The provisioningVariables property in a SKU indicates which properties are required for specific items in the catalog.

| Property                           | Type                                         | Description                                          |
|------------------------------------|----------------------------------------------|------------------------------------------------------|
| scope                           | string                                          | The scope type for a purchase that indicates where the benefits apply: "Single," "Shared.”                       |
| entitlementId                         | string                                    | The ID of the Azure subscription that would be used for a purchase. Required for Single scope.    |

## PurchaseCommitment

The fixed amount committed on compute services.

| Property                           | Type                                         | Description                                          |
|------------------------------------|----------------------------------------------|------------------------------------------------------|
| amount                           | int                                          | The fixed amount commitment.                           |
| currency                         | string                                       | The currency of the commitment.              |
| grain                            | string                                       | The period of the commitment.                   |
