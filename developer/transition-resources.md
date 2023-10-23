---
title: Transition resources
description: Describes the resources used to transition new commerce subscriptions.
ms.date: 09/22/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: migolova
ms.author: migolova
---

# Transition resources

**Applies To**

- Partner Center

**Appropriate roles**

- Global admin
- Admin agent

> [!Note]
> The new commerce experiences for license-based services include many new capabilities and are available to all Cloud Solution Provider (CSPs). For more information, see **[new commerce experiences overview](../new-commerce-license-based.md)**.

Describes the resources used to transition from one new commerce subscription to another.

## TransitionEligibility

Describes the behavior of an individual subscription transition resource.

| Property          | Type                    | Description                                                                                  |
|-------------------|-------------------------|----------------------------------------------------------------------------------------------|
| CatalogItemId | string                  | The catalog item ID being checked for. |
| Title  | string                  | The SKU title. |
| Description | string                  | The SKU description. |
| Quantity | integer                 | The quantity of the new offer to be purchased. |
| Eligibilities | list of TransitionEligibilityDetail | A list of transition eligibility details. |
|SubscriptionEligibilities|list of TargetSubscriptionEligibilityDetail|A list of subscriptions that are eligible to be transitioned to.

## TransitionEligibilityDetail

Describes the behavior of an individual target subscription eligibility detail resource.

| Property                 | Type                    | Description                                                                                  |
|--------------------------|-------------------------|----------------------------------------------------------------------------------------------|
| IsEligible               | boolean                 | Returns the eligibility is valid or not.                                       |
| SubscriptionId           | string                  | Returns the subscription's ID.                                                 |
| SubscriptionFriendlyName | string                  | Returns the subscription's friendly name.                                      |
| SubscriptionTermDuration | string                  | Returns the subscription's term duration.                                      |
| SubscriptionBillingCycle | BillingCycleType        | Returns the subscription's billing cycle type.                                 |
| Errors                   | List of TargetSubscriptionErrors | The reasons why the target subscription is not eligible to be transitioned to. |

## TargetSubscriptionEligibilityDetail

Describes the behavior of an individual target subscription eligibility detail resource.

| **Property**             | **Type**                         | **Description**                                                                |
| ------------------------ | -------------------------------- | ------------------------------------------------------------------------------ |
| IsEligible               | boolean                          | Returns the eligibility is valid or not.                                       |
| SubscriptionId           | string                           | Returns the subscription's id.                                                 |
| SubscriptionFriendlyName | string                           | Returns the subscription's friendly name.                                      |
| SubscriptionTermDuration | string                           | Returns the subscription's term duration.                                      |
| SubscriptionBillingCycle | BillingCycleType                 | Returns the subscription's billing cycle type.                                 |
| Errors                   | List of TargetSubscriptionErrors | The reasons why the target subscription is not eligible to be transitioned to. |

## Transition

Describes the behavior of an individual subscription transition resource.

| Property          | Type                    | Description                                                                                  |
|-------------------|-------------------------|----------------------------------------------------------------------------------------------|
| FromCatalogItemId | string                  | The From catalog item ID. |
| FromSubscriptionId | string                 | The From subscription ID. |
| ToCatalogItemId   | string                  | The To catalog item ID. |
| ToSubscriptionId  | string                  | The To subscription ID. This is only populated if the subscription changes. Currently only Legacy Upgrade needs this, but modern partial transition will also. |
| Quantity          | integer                 | The quantity being transitioned to the target catalog item. |
| TermDuration          | string                 | The term duration for the subscription. |
| BillingCycle          | string                 | The billing cycle for the subscription. |
| TransitionType    | string       | The transition type. Possible values - `transition_only`, `transition_with_license_transfer`.   |
| Events            | list of TransitionEvents | The events of the transition. |
| promotionId | string | The promotion ID that was applied to the transition. |

## TransitionEvent

Describes the different events that have taken place on a subscription.

| Property          | Type               |Description                                                                                                                                                |
|-------------------|--------------------|------------------------------------------------------------------------------|
| Name | string | The name of the transition event. Possible values - `Conversion` or `LicenseReassignment`. |
| Status | string  | The status of transition event. Possible values - `Started`, `Completed` or `Failed`.  |
| Timestamp | DateTime | The UTC timestamp of the event. |
| Errors | List of TransitionErrors | The metadata attributes corresponding to the error. |

## TransitionError

Represents an error for subscription transfer eligibility. Provides a reason why a transition cannot be performed.

| Property          | Type               | Description                                                                  |
|-------------------|--------------------|--------------------------------------------------------------|
| Code | TransitionErrorCode | The error code associated with the issue. |
| Description | string  | Friendly text describing the error. |

## TargetSubscriptionErrors

Represents an error for when target subscription is not eligible to be transitioned to. Provides a reason.

| Property          | Type               | Description                                                                  |
|-------------------|--------------------|--------------------------------------------------------------|
| Code | TargetSubscriptionErrorCode | The error code associated with the issue. |
| Description | string  | Friendly text describing the error. |
