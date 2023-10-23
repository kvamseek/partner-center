---
title: Subscription resources
description: Subscription resources can provide further information about subscriptions throughout the life cycle, such as support, refunds, Azure entitlements.
ms.date: 06/26/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: migolova
ms.author: migolova
---

# Subscription resources

**Applies to**: Partner Center | Partner Center operated by 21Vianet |  Partner Center for Microsoft Cloud for US Government

A subscription lets a customer use a service for a certain period of time. Not all fields will apply to all subscriptions. Many fields only apply at certain points in the life cycle, such as if a subscription is suspended or canceled.

## Subscription

> [!NOTE]
>The **Subscription** resource has a rate limit of 500 requests per minute per tenant identifier.

The **Subscription** resource represents the life cycle of a subscription and includes properties that define the states throughout the subscription life cycle.

| Property             | Type                                                          | Description                                                                                                                                                                   |
|----------------------|---------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  ID                   | string                                                        | The subscription identifier.                                                                                                                                                  |
| offerId              | string                                                        | The offer identifier.                                                                                                                                                         |
| entitlementId        | string                                                        | The entitlement identifier (an Azure subscription ID).                                                                                                                        |
| offerName            | string                                                        | The offer name.                                                                                                                                                               |
| friendlyName         | string                                                        | The friendly name for the subscription defined by the partner to help disambiguate.                                                                                           |
| quantity             | number                                                        | The quantity. This property is set to the license count for license-based billing.                                                            |
| unitType             | string                                                        | The units defining quantity for the subscription: "Licenses", "Usage-based", or  "Benefit”.  |
| parentSubscriptionId | string                                                        | Gets or sets the parent subscription identifier.                                                                                                                              |
| creationDate         | string                                                        | Gets or sets the creation date, in date-time format.                                                                                                                          |
| effectiveStartDate   | string in UTC date time format                                | Gets or sets the effective start date for this subscription, in date-time format. It's used to back date a migrated subscription or to align it with another.                |
| commitmentEndDate    | string in UTC date time format                                | The commitment end date for this subscription, in date-time format. For subscriptions that aren't autorenewable, this represents a date far, far away in the future. End dates are inclusive, meaning the end of the term is at the end of the full day.     |
| commitmentEndDateTime    | string in UTC date time format                                | The commitment end date and time for this subscription, in date-time format. For subscriptions that aren't autorenewable, this represents a date far, far away in the future.       |
| status               | string                                                        | The subscription status: "none", "active", "pending", "suspended", "expired", "disabled" or "deleted".                                                                                                         |
| autoRenewEnabled     | boolean                                                       | Gets a value indicating whether the subscription is renewed automatically.                                                                                                    |
| billingType          | string                                                        | Specifies how the subscription is billed: "none", "usage", "license", or "benefit".                                                                                    |
| billingCycle         | string                                                        | Indicates the frequency with which the partner is billed for this order. Supported values are the member names found in [**BillingCycleType**](product-resources.md#billingcycletype). |
| hasPurchasableAddons | boolean                                                       | Gets or sets a value indicating whether the subscription has purchasable add-ons.                                                                                             |
| isTrial              | boolean                                                       | A value indicating whether the subscription is a trial.                                                                                                                      |
| isMicrosoftProduct   | boolean                                                       | A value indicating whether the subscription is a Microsoft product.                                                                                                                       |
| publisherName        | string                                                        | The publisher name.                                                                                                                                                           |
| actions              | array of strings                                              | Gets or sets the actions that are allowed. Possible values: "edit", "cancel"                                                                                                  |
| partnerId            | string                                                        | The PartnerID of the reseller of record, used in the indirect partner model.                                                                                                     |
| suspensionReasons    | array of strings                                              | Read-only. If the subscription was suspended, indicates why.                                                                                                                  |
| contractType         | string                                                        | Read-only. The type of contract: "subscription", "productKey", or "redemptionCode".                                                                                           |
| refundOptions        | array of [RefundOption](#refundoption) resources   | Read-Only. The set of refund options available for this subscription.                                                                                                            |
| scheduledNextTermInstructions        | [scheduledNextTermInstructions](#schedulednextterminstructions)  | Gets or sets the scheduled instructions executed when the next term starts.                                                                      |
| nextChargeInstructions        | [nextChargeInstructions](#nextchargeinstructions)  | Gets details for the next term billing instructions for pending billing cycle changes at the end of the current term.                                                |
| links                | [SubscriptionLinks](#subscriptionlinks)                       | Gets or sets the subscription links.                                                                                                                                          |
| orderId              | string                                                        | The ID of the order that was placed to begin the subscription.                                                                                                                |
| termDuration         | string                                                        | An ISO 8601 representation of the term's duration. The current supported values are **P1M** (1 month), **P1Y** (1 year) and **P3Y** (3 years).                                                        |
| attributes           | [ResourceAttributes](utility-resources.md#resourceattributes) | The metadata attributes corresponding to the subscription.                                                                                                                    |
| renewalTermDuration  | string                                                        | An ISO 8601 representation of the term's duration. The current supported values are **P1M** (1 month) and **P1Y** (1 year).                                                        |
| ProductType  | [ItemType](product-resources.md#itemtype)                             | Read-only. The type of product the subscription is for.     |
| consumptionType  | array of [overage](subscription-resources.md#overage) resources   | Gets or sets overage for a given customer.     |
| promotionId          | string                                                        | The promotion identifier if applied to the subscription. Format example: "39NFJQT1PJQB:0001:39NFJQT1Q5KN" |
| CancellationAllowedUntilDate | DateTime                                              | The last date for cancellation.   |
| BillingCycleEndDate  | DateTime                                                      | Gets or sets the billing cycle end date for this subscription, in date-time format.   |
| BillingCycleEndDateTime  | DateTime                                                      | Gets billing cycle end date time for this subscription, in date-time format.   |
| productOrderId           | string  | Identifier for a specific product purchase (for example, Reservations or Azure savings plan). |
| lineItems                | [SubscriptionLineItem](#subscriptionlineitem) | A line item contains the purchase details of a particular subscription.  |

## SubscriptionLinks

The **SubscriptionLinks** resource describes the collection of links attached to a subscription resource.

| Property           | Type                               | Description                           |
|--------------------|------------------------------------|---------------------------------------|
| offer              | [Link](utility-resources.md#link) | Gets or sets the offer.               |
| parentSubscription | [Link](utility-resources.md#link) | Gets or sets the parent subscription. |
| product            | [Link](utility-resources.md#link) | Gets the product associated with the subscription. |
| sku                | [Link](utility-resources.md#link) | Gets the product sku associated with the subscription. |
| availability       | [Link](utility-resources.md#link) | Gets the product sku availability associated with the subscription. |
| activationLinks    | [Link](utility-resources.md#link) | Gets the list of activation links associated with the subscription. |
| self               | [Link](utility-resources.md#link) | The self-URI.                         |
| next               | [Link](utility-resources.md#link) | The next page of items.               |
| previous           | [Link](utility-resources.md#link) | The previous page of items.           |

## SubscriptionProvisioningStatus

The **SubscriptionProvisioningStatus** resource provides information about the provisioning status of a subscription.

| Property   | Type                                                           | Description                                                          |
|------------|----------------------------------------------------------------|----------------------------------------------------------------------|
| skuId      | string                                                         | A string that identifies the product SKU.             |
| status     | string                                                         | Indicates the provisioning status: "success", "pending" or "failed". |
| quantity   | number                                                         | Provides the subscription quantity after provisioning.               |
| endDate    | string in UTC date time format                                 | The end date of the subscription.                                    |
| attributes | [ResourceAttributes](utility-resources.md#resourceattributes)  | The metadata attributes.                                             |

## scheduledNextTermInstructions

The **scheduledNextTermInstructions** resource defines the instructions to be applied at the start of the subscription's next term. Only present if scheduled changes are set or for all trial subscriptions.

| Property   | Type                                                           | Description                                                          |
|------------|----------------------------------------------------------------|----------------------------------------------------------------------|
| product    | [product](#product)               | A GUID formatted string that identifies the product SKU.             |
| quantity   | number                                                         | Provides the subscription quantity after provisioning.               |
| customTermEndDate    | string in UTC date time format                       | The custom end date for the subscription when aligned to another subscription's end date                                   |

## Product

The **scheduledNextTermInstructions.product** resource and attributes a scheduled change will apply at the next term.

| Property   | Type                                                           | Description                                                          |
|------------|----------------------------------------------------------------|----------------------------------------------------------------------|
| productId    | String             | The ID for a product.     |
| skuId   | String        | Provides the subscription quantity after provisioning.       |
| availabilityId    | String      | The ID for this availability. This ID is unique only within the context of its parent [product](product-resources.md#product) and [SKU](product-resources.md#sku). **Note** Availability IDs can change over time. Partners should only rely on this value within a short time span after retrieving it.    |
| billingCycle    | String  | Indicates the frequency with which the partner is billed for this order. Supported values are the member names found in [**BillingCycleType**](product-resources.md#billingcycletype).  |
| termDuration    | String | An ISO 8601 representation of the term's duration. The current supported values are **P1M** (1 month) and **P1Y** (1 year).    |
| promotionId    | String | The promotion identifier to be applied for the next scheduled term. Format example: "39NFJQT1PJQB:0001:39NFJQT1Q5KN". |

## nextChargeInstructions

The **nextChargeInstructions** resource defines the billing cycle instructions applied at the start of the subscription's next term. Only present when pending billing cycle changes are pending.

| Property   | Type                                                           | Description                                                          |
|------------|----------------------------------------------------------------|----------------------------------------------------------------------|
| product    | [product](#product)               | A GUID formatted string that identifies the product SKU.             |
| quantity   | number                                                         | Provides the subscription quantity after provisioning.               |

## SubscriptionRegistrationStatus

The **SubscriptionRegistrationStatus** resource describes the collection of links attached to a subscription resource.

| Property           | Type                               | Description                                                                           |
|--------------------|------------------------------------|---------------------------------------------------------------------------------------|
| subscriptionId     | string                             | The subscription identifier.                                                          |
| status             | string                             | Indicates the registration status: "registered", "registering", or "notregistered".    |

## SupportContact

The **SupportContact** resource represents a support contact for a customer's subscription.

| Property        | Type                                                           | Description                                                                     |
|-----------------|----------------------------------------------------------------|---------------------------------------------------------------------------------|
| supportTenantId | string                                                         | A GUID formatted string that indicates the support contact's tenant identifier. |
| supportMpnId    | string                                                         | The contact's Partner identifier.                       |
| name            | string                                                         | The name of the support contact.                                                |
| links           | [ResourceLinks](utility-resources.md#resourcelinks)            | The support contact related links.                                              |
| attributes      | [ResourceAttributes](utility-resources.md#resourceattributes)  | The metadata attributes. Contains "objectType": " SupportContact".              |

## Overage

The **overage** resource represents the consumption subscription overage may be assigned to, whether it's assigned and the Reseller assigned.

| Property        | Type               | Description                                                                     |
|-----------------|--------------------|---------------------------------------------------------------------------------|
| azureEntitlementId | string       | A GUID formatted string that indicates consumption subscription identifier. |
| partnerId    | string            | The partner identifier of the reseller associated with the subscription.        |
| type    | string       | The type of overage can be “PhoneServices”       |
| overage            | boolean      | A value indicating whether overage is enabled.       |
| links           | [ResourceLinks](utility-resources.md#resourcelinks)            | The overage related links.                          |
| attributes      | [ResourceAttributes](utility-resources.md#resourceattributes)  | The metadata attributes. Contains "objectType": "Overage".  |



## RegisterSubscription

The **RegisterSubscription** resource returns a link that can be used to query the registration status of a subscription. The registration status is returned in the response body of a successfully accepted request to register an Azure subscription.

| Property                | Type                               | Description                                                                           |
|-------------------------|------------------------------------|---------------------------------------------------------------------------------------|
| httpResponseMessage     | object                             | Returns HTTP Status Code 202 "Accepted", with a Location header containing a link to query the registration status. For example, `"/customers/{customer-id}/subscriptions/{subscription-id}/registrationstatus"` |

## RefundOption

The **RefundOption** resource represents a possible refund option for the subscription.

| Property          | Type | Description                                                                         |
|-------------------|--------|-------------------------------------------------------------------------------------|
| type | string | The type of refund. The supported values are "Partial" and "Full" |
| expiresAfter      | string in UTC date time format | The timestamp when this option expires. If null, the refund operation has no expiration. |

## AzureEntitlement

The **AzureEntitlement** resource represents the Azure entitlements for the subscription.

| Property          | Type | Description                                                                         |
|-------------------|--------|-------------------------------------------------------------------------------------|
| ID | string | The entitlement identifier |
| friendlyName      | string | The friendly name of the entitlement. |
| status | string | The status of entitlement. |
| subscriptionId | string | The subscription identifier the entitlement belongs to. |


## SubscriptionLineItem

A line item contains the purchase details of a particular subscription. 

| **Property**       | **Type**                                               | **Description**                                                                                        |
| ------------------ | ------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ |
| ID                 | string                                                 | The subscription line item identifier.                                                                 |
| friendlyName       | string                                                 | The friendly name for the subscription line item defined by the partner to help disambiguate.          |
| scope              | [Scope](#scope)                             | Scope indicates where benefits apply.                                                                  |
| autoRenewEnabled   | Boolean                                                | Gets a value indicating whether the subscription is renewed automatically.                             |
| status             | string                                                 | The subscription status: "none", "active", "pending", "suspended", "expired", "disabled" or "deleted". |
| purchaseCommitment | [Purchase Commitment](#purchase-commitment) | The fixed amount committed on compute services.                                                        |

## Scope

Scope indicates where benefits apply.  

| **Property**      | **Type** | **Description**                                                                                                                                               |
| ----------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| type              | string   | The scope type for a purchase: "Single", "Shared”, “Resource group”, or “Management group”.                                                                   |
| subscriptionId    | string   | The ID of the Azure plan that would be used for a purchase. Required for Shared scope.                                                                        |
| entitlementId     | string   | The ID of the Azure subscription that would be used for a purchase. Required for Single scope.                                                               |
| managementGroupId | string   | The ID of the Management group that would be used for a purchase. This scope can only be selected through Azure portal today, but updates will reflect in PC. |
| resourceGroupId   | string   | The ID of the Resource group that would be used for a purchase. This scope can only be selected through Azure portal today, but updates will reflect in PC.   |

## Purchase Commitment

The fixed amount committed on compute services.

| **Property** | **Type** | **Description**                 |
| ------------ | -------- | ------------------------------- |
| amount       | string   | The fixed amount commitment.    |
| grain        | string   | The period for the commitment.  |
| currency     | string   | The currency of the commitment. |
