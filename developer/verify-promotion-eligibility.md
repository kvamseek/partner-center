---
title: Verify a promotion eligibility
description: Verifies whether a customer transaction is eligible for a given promotion.
ms.date: 11/17/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: iragulati1
ms.author: iragulati
---

# Verify promotion eligibility

**Applies To**

- Partner Center

**Appropriate roles**

- Global admin
- Admin agent

> [!Note] 
> The new commerce experiences for license-based services include many new capabilities and are available to all Cloud Solution Provider (CSPs). For more information, see [new commerce experiences overview](../new-commerce-license-based.md).

Parters can verify whether a customer transaction is eligible for a given promotion. This method returns *True* if the customer transaction is eligible for a given promotion. Partners can verify eligibility before submitting a transaction to ensure the promotion will be applied.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with both standalone App and App+User credentials.

- Eligibility includes the product sku availability purchased, the promotion ID being evaluated, the quantity, term duration, and billing cycle of the transaction.

## REST request

### Request syntax

| Method   | Request URI                                                                                                                         |
|----------|-------------------------------------------------------------------------------------------------------------------------------------|
| **POST**  | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customerId}/promotionEligibilities HTTP/1.1 |

### URI parameter

Use the following query parameters to return available promotions.

| Name                    | Type     | Required | Description                                       |
|-------------------------|----------|----------|---------------------------------------------------|
| **customerId**  | **string** | Y        | The value is a GUID-formatted customer-tenant-id, which is an identifier that allows you to specify a customer.          |

### Request headers

For more information, see [Partner Center REST headers](headers.md).

### Request body

Body includes a collection of PromotionEligibilitiesRequestItems. This table describes the properties for a [PromotionEligibilitiesRequestItem](promotion-resources.md#promotioneligibilitiesrequestitem).

| Property        | Type             | Required        | Description                                                                                               |
|-----------------|------------------|-----------------|-----------------------------------------------------------------------------------------------------------|
| catalogItemId   | string           | Yes             | The catalog item identifier.                         |
| quantity        | int | Yes        | The number of licenses or instances.                 |
| termDuration    | DateTime         | Yes             | An ISO 8601 representation of the term's duration. The current supported values are P1M (one month), P1Y (one year) and P3Y (three years).   |
| billingCycle    | string | Yes     | The value that indicates the type of billing cycle.   |
| promotionId     | string           | No              | The promotion item identifier.                       | 

### Request example

```http
POST https://api.partnercenter.microsoft.com/v1/customers/46632f71-f052-4384-8f84-4cdb6c12c2a1/promotionEligibilities HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
X-Locale: en-US

 // Request example with promotion ID input
{
    "items": [
        {
            "catalogItemId": "CFQ7TTC0LH2Z:0002:CFQ7TTC0HRVK",
            "quantity": 2400,
            "termDuration": "P1Y",
            "billingCycle": "Monthly",
            "promotionId": "39NFJQT1PM6C:0005:39NFJQT1Q5L7"
        }
    ]
}

```

```http
POST https://api.partnercenter.microsoft.com/v1/customers/46632f71-f052-4384-8f84-4cdb6c12c2a1/promotionEligibilities HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70b
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e133
X-Locale: en-US

 // Request example with no promotion ID input
{
    "items": [
        {
            "id": "0",
            "catalogItemId": "CFQ7TTC0HBSJ:0001:CFQ7TTC0JQH3",
            "quantity": 300,
            "termDuration": "P1M",
            "billingCycle": "monthly"
        }
    ]
}

```

## REST response

If a promotionId is provided and the request is successful, this method returns a collection of eligibility results. If promotionId is not provided and the request is successful, this method returns all promotions available for the offer specified and the corresponding customer eligibility for each promotion.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and more debugging information. Use a network trace tool to read this code, error type, and more parameters. For the full list, see [Error Codes](error-codes.md). 

### Eligibility error types and descriptions

Eligibility will return false if the eligibility checks determine the product SKU being evaluated against the promotion ID don't align. Various conditions and constraints are evaluated and return error types to describe the conditions not met for the eligibility.

| Eligibility error type | Eligibility error description |
|:-----------------------|:-----------------------------------------------|
| InvalidCatalogItemId | The provided CatalogItemId is invalid. |
| InvalidPromotion | The provided promotion is invalid. |
| PrerequisiteProductOwnership | The customer doesn't meet the prerequisite product ownership requirements to be eligible for this promotion. |
| RedemptionLimit | The redemption limit for this promotion has been met. |
| SeatCount | The provided quantity doesn't satisfy the minimum or maximum seat requirements for the promotion. |
| OfferPurchasedPreviously | This offer has been purchased previously for this customer. |
| Term | The provided term isn't applicable for the promotion. |
| NoPromotionsAvailable | There are no promotions available at this time. |

### Response example

```http
HTTP/1.1 200 OK
Content-Length: 138
Content-Type: application/json
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
Date: Fri, 26 Feb 2021 20:42:26 GMT

// Response example with promotion ID provided in the request
{
    "totalCount": 1,
    "items": [
        {
            "id": 0,
            "catalogItemId": "CFQ7TTC0LH2Z:0002:CFQ7TTC0HRVK",
            "quantity": 2400,
            "billingCycle": "monthly",
            "termDuration": "P1Y",
            "eligibilities": [
                {
                    "promotionId": "39NFJQT1PM6C:0005:39NFJQT1Q5L7",
                    "isEligible": false,
                    "errors": [
                        {
                            "minimumRequiredSeats": 1,
                            "maximumRequiredSeats": 2400,
                            "availableSeats": 500,
                            "type": "SeatCount",
                            "description": "The provided quantity does not satisfy the minimum or maximum seat requirements for the promotion."
                        }
                    ]
                }
            ],
            "attributes": {
                "objectType": "PromotionEligibilities"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```

```http
HTTP/1.1 200 OK
Content-Length: 138
Content-Type: application/json
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e133
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70b
Date: Fri, 26 Feb 2021 20:42:26 GMT

// Response example with no promotion ID provided in the request
{
    "totalCount": 1,
    "items": [
        {
            "id": 0,
            "catalogItemId": "CFQ7TTC0HBSJ:0001:CFQ7TTC0JQH3",
            "quantity": 300,
            "billingCycle": "monthly",
            "termDuration": "P1M",
            "eligibilities": [
                {
                    "promotionId": "39NFJQT1XK5L:000J:39NFJQT1Q5D8",
                    "isEligible": true
                },
                {
                    "promotionId": "39NFJQT1XG89:0002:39NFJQT1Q5L2",
                    "isEligible": true
                }
            ],
            "attributes": {
                "objectType": "PromotionEligibilities"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```