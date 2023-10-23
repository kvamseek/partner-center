---
title: Transition a new commerce subscription
description: Upgrades a customer's new commerce subscription to a specified target subscription.
ms.date: 7/14/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: migolova
ms.author: migolova
---

# Transition a new commerce subscription

**Applies To**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud for US Government

**Appropriate roles**

- Global admin
- Admin agent

These methods support both traditional and new commerce source subscriptions.

> [!NOTE]
> The new commerce experiences for license-based services includes many new capabilities and are available to all Cloud Solution Provider (CSPs). For more information, see [new commerce experiences overview](../new-commerce-license-based.md).

Used to upgrade a customer's new commerce subscription to a target subscription or convert an NCE trial to a paid subscription. In order to transition a subscription, two API requests need to be made. First **GET eligible transitions** to get the SKUs available for upgrade. Then **POST transition** to execute the transition.

## Get transition eligibilities

Returns a list of eligible transitions for a given customer, subscription and requested type. Also returns destination subscription upgrade eligibility.

### Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with both standalone App and App+User credentials.

- A customer ID (`customer-tenant-id`). If you don't know the customer's ID, you can look it up in [Partner Center](https://partner.microsoft.com/dashboard) by selecting the **Customers** workspace, then the customer from the customer list, then **Account**. On the customer's Account page, look for the **Microsoft ID** in the **Customer Account Info** section. The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).

- A subscription ID for the initial subscription.

### GDAP roles

You'll need at least one of the following GDAP roles:

- Directory Reader
- Global Reader

>[!NOTE]
> While this API is available for legacy and NCE, GDAP is only required for legacy.

### REST request

#### Request syntax

| Method   | Request URI                                                                                                                         |
|----------|-------------------------------------------------------------------------------------------------------------------------------------|
| **GET**  | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/transitionEligibilities?eligibilityType={immediate, scheduled} HTTP/1.1 |

#### URI parameter

Use the following query parameters to return eligible transitions.

| Name                    | Type     | Required | Description                                       |
|-------------------------|----------|----------|---------------------------------------------------|
| **customer-tenant-id**  | **guid** | Y        | A GUID corresponding to the customer's tenant.             |
| **subscription-id** | **guid** | Y        | A GUID corresponding to the initial subscription. |
| **eligibilityType**       | **string** | N        | Describes when the transition is to be executed; can be immediate or scheduled. Default is `Immediate`.  |

#### Request headers

For more information, see [Partner Center REST headers](headers.md).

#### Request body

None

#### Request example

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/transitionEligibilities?eligibilityType=immediate HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
X-Locale: en-US
```

### REST response

If successful, this method returns a list of the eligible transitions for the given subscription in the response body.

#### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and more debugging information. Use a network trace tool to read this code, error type, and other parameters. For the full list, see [Error Codes](error-codes.md).

#### Eligibility errors

Error descriptions and meaning.

| Error description | Meaning  |
|-------------------------|----------|
|Subscription can't be Transitioned - source subscription isn't active. | Original sub status not Active |
|Subscription can't be Transitioned - source subscription isn't provisioned yet. | Original sub FulfillmentState isn't successful |
|Transition type isn't compatible - AzureAD subscription mapping is required. | LegacyCannotConvertSubscriptionId error when calling GetSubscriptionUpgradeConflicts |
|Transition type isn't compatible - conflicting subscriptions for license transfer exist. | If any Azure Active Directory (Azure AD) service has subscription IDs from a different subscription, add it to the conflict list (includes purchases made with either legacy or modern purchase flow) |

#### Subscription eligibility errors

If a destination subscription is not eligible to be upgraded to, one of the following reasons will be returned.  

Empty lists will be returned if the source subscription is a trial or if the eligibilityType is specified as Scheduled. You can only transition into an existing subscription with an immediate (also known as "midterm") transition, not a scheduled change.

| Error description | Error code   |
|-------------------------|----------|
|Subscription is not active.  | SubscriptionNotActive = 1  |
|Subscription is within cancellation window.  | SubscriptionInCancellationWindow = 2  |
|Subscription term duration is shorter than the source subscription's term duration. | SubscriptionTermDurationShorterThanSourceTermDuration = 3  |
|Subscription term end date is before the source subscription's term end date. | Subscription term end date is before the source subscription's term end date. = 4   |

#### Response example

```http
HTTP/1.1 200 OK
Content-Length: 138
Content-Type: application/json
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
Date: Fri, 26 Feb 2021 20:42:26 GMT

{
  "totalCount": 2,
  "items": [
    {
      "operationId": "1caf8ec7-62cc-4ab5-b35d-572d2a62974c",
      "catalogItemId": "CFQ7TTC0KZCR:0001:CFQ7TTC0K71H",
      "title": "Microsoft 365 E5 Test Sku Title",
      "description": "Microsoft 365 E5 Test Sku Description",
      "quantity": 1,
      "subscriptionEligibilities": [
        {
          "isEligible": false,
          "subscriptionId": "92301b7d-7598-4938-d6f2-d31e080e9da6",
          "subscriptionFriendlyName": "Microsoft 365 Business Premium",
          "subscriptionTermDuration": "P1M",
          "subscriptionBillingCycle": "monthly",
          "errors": [
            {
              "code": 3,
              "description": "The subscription's term duration is shorter than the source subscription's term duration."
            }
          ]
        },
        {
          "isEligible": true,
          "subscriptionId": "151467a1-4246-4a00-da7b-3405463d9b78",
          "subscriptionFriendlyName": "Microsoft 365 Business Premium",
          "subscriptionTermDuration": "P1Y",
          "subscriptionBillingCycle": "monthly",
          "errors": []
        }
      ],
      "eligibilities": [
        {
          "isEligible": true,
          "transitionType": "transition_only",
          "errors": []
        },
        {
          "isEligible": false,
          "transitionType": "transition_with_license_transfer",
          "errors": [
            {
              "code": 3,
              "description": "Subscription cannot be transitioned because there are conflicting services."
            }
          ]
        }
      ],
      "attributes": {
        "objectType": "TransitionEligibility"
      }
    },
    {
      "operationId": "1caf8ec7-62cc-4ab5-b35d-572d2a62974c",
      "catalogItemId": "CFQ7TTC0L4M3:0001:CFQ7TTC0K78T",
      "title": "Business Premium Test Sku Title",
      "description": "Business Premium Test Sku Description",
      "quantity": 1,
      "eligibilities": [
        {
          "isEligible": false,
          "transitionType": "transition_with_license_transfer",
          "errors": [
            {
              "code": 3,
              "description": "Subscription cannot be transitioned because there are conflicting services."
            }
          ]
        }
      ],
      "attributes": {
        "objectType": "TransitionEligibility"
      }
    }
  ],
  "attributes": {
    "objectType": "Collection"
  }
}
```

## Post Transition

Posts a transition request for a given customer and subscription. Returns the transition with its initial status.

### Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with both standalone App and App+User credentials.

- A customer ID (`customer-tenant-id`). If you don't know the customer's ID, you can look it up in [Partner Center](https://partner.microsoft.com/dashboard) by selecting the **Customers** workspace, then the customer from the customer list, then **Account**. On the customer's Account page, look for the **Microsoft ID** in the **Customer Account Info** section. The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).

- A subscription ID for the initial subscription.

### GDAP roles

You'll need at least one of the following GDAP roles:

- Directory Reader or Global reader (transition only)
- Directory Writer (transition with license transfer)

> [!NOTE]
> While this API is available for legacy and NCE, GDAP is only required for legacy.

### REST request

#### Request syntax

| Method   | Request URI                                                                                                                         |
|----------|-------------------------------------------------------------------------------------------------------------------------------------|
| **POST**  | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/transitions HTTP/1.1 |


#### URI parameter

Use the following query parameters to execute a transition.

| Name                    | Type     | Required | Description                                       |
|-------------------------|----------|----------|---------------------------------------------------|
| **customer-tenant-id**  | **guid** | Y        | A GUID corresponding to the customer's tenant.             |
| **subscription-id** | **guid** | Y        | A GUID corresponding to the initial subscription. |

#### Request headers

For more information, see [Partner Center REST headers](headers.md).

#### Request body

This table describes the [Transition](transition-resources.md#transition) properties in the request body.

| Property              | Type             | Required        | Description                                                                                               |
|-----------------------|------------------|-----------------|-----------------------------------------------------------------------------------------------------------|
| fromCatalogItemId     | string           | No              | The catalog item you are transitioning from.                                                              |
| fromSubscriptionId    | string           | No              | The subscription ID you are transitioning from.                                                       |
| toCatalogItemId       | string           | Yes             | The catalog item you are transitioning to.                                                                |
| toSubscriptionId      | string           | No              | The subscription ID  you are transitioning to.                                                        |
| quantity              | integer          | Yes              | The number of licenses to transition over.                                                                |
| termDuration          | string           | No              | Specifying the term duration of the subscription.                                                        |
| billingCycle          | string           | No              | Specifying the billing cycle of the subscription.                                                        |
| transitionType        | string           | Yes              | The transition type. Possible values - `transition_only`, `transition_with_license_transfer`.             |

#### Request example

```http
POST https://api.partnercenter.microsoft.com/v1/customers/{customerId}/subscriptions/{subscriptionId}/transitions HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
X-Locale: en-US

{
    "fromCatalogItemId": "CFQ7TTC0LF8Q:0001:CFQ7TTC0K39X",
    "fromSubscriptionId": "e487e8dc-421e-4275-cb42-3c1c8daccf70",
    "toCatalogItemId": "CFQ7TTC0LF8R:0001:CFQ7TTC0KCSV",
    "toSubscriptionId": "0af52192-4a2a-4364-d25b-c8ecab3a5697",
    "quantity": 2,
    "termDuration": "P1M",
    "billingCycle": "Monthly",
    "transitionType": "transition_only"
}
```

### REST response

If successful, this method returns a [Transition](transition-resources.md#transition) resource with its initial status.

#### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and more debugging information. Use a network trace tool to read this code, error type, and other parameters. For the full list, see [Error Codes](error-codes.md).

#### Response example

```http
HTTP/1.1 200 OK
Content-Length: 138
Content-Type: application/json
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
Date: Fri, 26 Feb 2021 20:42:26 GMT

{
    "fromCatalogItemId": "CFQ7TTC0LF8Q:0001:CFQ7TTC0K39X",
    "fromSubscriptionId": "e487e8dc-421e-4275-cb42-3c1c8daccf70",
    "toCatalogItemId": "CFQ7TTC0LF8R:0001:CFQ7TTC0KCSV",
    "toSubscriptionId": "0af52192-4a2a-4364-d25b-c8ecab3a5697",
    "quantity": 2,
    "termDuration": "P1M",
    "billingCycle": "Monthly",
    "transitionType": "transition_only"
    "Events": [
        {
            "name": "Conversion",
            "status": "Started ",
            "timestamp": "2021-01-08T18:01:14.7488618Z",
            "attributes":
            {
                "objectType": "TransitionEvent"
            }
        }
    ],
    "attributes":
    {
        "objectType": "Transition" 
    }
}
```