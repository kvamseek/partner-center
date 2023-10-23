---
title: Gets a single promotion
description: Gets a single promotion for a given promotion ID and country/region.
ms.date: 06/14/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: IraGulati
ms.author: iragulati
---

# Get promotion by ID

**Applies To**

- Partner Center

**Appropriate roles**

- Global admin
- Admin agent

> [!Note] 
> The new commerce experiences for license-based services include many new capabilities and are available to all Cloud Solution Provider (CSPs). For more information, see [new commerce experiences overview](../new-commerce-license-based.md).

Partners can get a single promotion for a given promotion ID and country/region. This method returns the promotion data, ignoring the promotion start and end dates. This method is used primarily for reconciliation purposes to retrieve promotion details even after the promotion has expired.



## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with both standalone App and App+User credentials.

- Promotion ID is delimited set of strings that represent a specific promotion.

- Country represents the customer country/region promotions are available for. Country is represented by a two character country code.

## REST request

### Request syntax

| Method   | Request URI                                                                                                                         |
|----------|-------------------------------------------------------------------------------------------------------------------------------------|
| **GET**  | [*{baseURL}*](partner-center-rest-urls.md)/v1/productpromotions/{promotion-id}?country={country-code HTTP/1.1 |

### URI parameter

Use the following query parameters to return available promotions.

| Name                    | Type     | Required | Description                                       |
|-------------------------|----------|----------|---------------------------------------------------|
| **promotion-id**  | **string** | Y        | A string defining the promotion to retrieve.           |
| **country** | **string** | Y        | A two letter country code determining which customer country/region promotions are available for. |

### Request headers

For more information, see [Partner Center REST headers](headers.md).

### Request body

None

### Promotional constraints 
Promotional Constraints are now returned by this API. Please see an example in the response below. If a promotion has eligibility constraints, details will be returned in the response. This data can be used to understand if your customer will qualify for the discount.  

| Constraint category      | Constraint value     | Constraint type          | Description                                       | 
|--------------------------|----------------------|--------------------------|---------------------------------------------------| 
| **SeatConstraints**      | **MinSeats**         | SubscriptionQuantity                      | Minimum seats needed for the customer to be eligible for the promo.     | 
| **SeatConstraints**      | **MaxSeats**     | SubscriptionQuantity        | Maximum seats the promo can be applied to.         | 
| **AssetOwnershipLimits**        | **MinAssets** | LifetimeRedemptionCount | The minimum number of times the promo can be applied for a customer, typically  0.   | 
| **AssetOwnershipLimits**        | **MaxAssets** | LifetimeRedemptionCount | The maximum number of times the promo can be applied for customer.                   | 
| **EligibilityConstraints**        | **isApplicable** | FirstPurchase | Flag indicating if this must be the customer's first purchase of the product SKU to receive the promo.           | 
| **ProductOwnershipConstraints**   | **bigId** | N/A | Specified offers the customer must already own to be eligible for the promo (Product SKU).            | 

### Request example

```http
GET https://api.partnercenter.microsoft.com/v1/productpromotions/CFQ7TTC0HD33:0003:CFQ7TTC0K59M?country=US HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
X-Locale: en-US
```

## REST response

If successful, this method returns a single promotion.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and more debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Error Codes](error-codes.md).

### Response example

```http
HTTP/1.1 200 OK
Content-Length: 138
Content-Type: application/json
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
Date: Fri, 24 Apr 2023 20:42:26 GMT

 
{
    "id": "39NFJQT1SNC7:0001:39NFJQT1Q5KM",
    "name": "TEST Promotion May 2023 - Microsoft 365 F3",
    "description": "TEST Promotion May 2023 - Microsoft 365 F3",
    "startDate": "2023-05-03T00:00:00+00:00",
    "endDate": "9999-01-01T00:00:00+00:00",
    "properties": {
        "isAutoApplicable": true
    },
    "requiredProducts": [
        {
            "productId": "CFQ7TTC0LH05",
            "skuId": "0001",
            "term": {
                "duration": "P1Y",
                "billingCycle": "Annual"
            },
            "pricingPolicies": [
                {
                    "policyType": "PercentDiscount",
                    "value": "0.5"
                }
            ]
        }
    ],
    "promotionConstraints": { 
        "seatConstraints": [
            {
                "minSeats": 10,
                "maxSeats": 100,
                "type": "SubscriptionQuantity"
            }
        ],
        "assetOwnershipLimits": [
            {
                "minAssets": 0,
                "maxAssets": 3,
                "type": "LifetimeRedemptionCount"
            }
        ],
        "eligibilityConstraints": [
            {
                "isApplicable": true,
                "type": "FirstPurchase"
            }
        ],
        "productOwnershipConstraints": [
            [
                {
                    "bigId": "CFQ7TTC0MBMD/0002"
                }
            ]
        ]
    }
}
```
