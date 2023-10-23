---
title: Get a customer's subscriptions
description: How to get a collection of a customer's subscriptions.
ms.date: 06/13/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: migolova
ms.author: migolova
---

# Get a customer's subscriptions

**Applies to**: Partner Center | Partner Center operated by 21Vianet |  Partner Center for Microsoft Cloud for US Government

How to get a collection of a customer's subscriptions.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with both standalone App and App+User credentials.

- A customer ID (`customer-tenant-id`). If you don't know the customer's ID, you can look it up in [Partner Center](https://partner.microsoft.com/dashboard) by selecting the **Customers** workspace, then the customer from the customer list, then **Account**. On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section. The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).

## C\#

To get a list of all of a customer's subscriptions, first use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier to identify the customer. Then use the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property to retrieve an interface to subscription collection operations. Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) methods to retrieve the customer's subscriptions collection.

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;

var customerSubscriptions = partnerOperations.Customers.ById(customerId).Subscriptions.Get();
```

**Sample**: [Console test app](console-test-app.md). **Project**: Partner Center SDK Samples **Class**: GetSubscriptions.cs

## REST request

### Request syntax

| Method  | Request URI                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| **GET** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions HTTP/1.1 |

### URI parameter

This table lists the required query parameter to get all the subscriptions.

| Name               | Type   | Required | Description                                           |
|--------------------|--------|----------|-------------------------------------------------------|
| customer-tenant-id | string | Yes      | A GUID-formatted string that identifies the customer. |

### Request headers

For more information, see [Partner Center REST headers](headers.md).

### Request body

None.

### Request example

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/subscriptions HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: b2d13828-2ca5-41d4-94fb-9946214f4244
MS-CorrelationId: c49004b1-224f-4d86-a607-6c8bcc52cfdd
Connection: Keep-Alive
```

## REST response

If successful, this method returns a collection of [Subscription](subscription-resources.md) resources in the response body.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Partner Center REST error codes](error-codes.md).

### Response examples

```http
HTTP/1.1 200 OK
Content-Length: 73754
Content-Type: application/json
MS-CorrelationId: c49004b1-224f-4d86-a607-6c8bcc52cfdd
MS-RequestId: b2d13828-2ca5-41d4-94fb-9946214f4244
Date: Wed, 25 Nov 2015 05:43:06 GMT

{
    "totalCount": 37,
    "items": [{
        "id": "83ef9d05-4169-4ef9-9657-0e86b1eab1de",
        "entitlementId": "a356ac8c-e310-44f4-bf85-C7f29044af99",
        "friendlyName": "nickname",
        "quantity": 1,
        "unitType": "none",
        "creationDate": "2015-11-25T06: 41: 12Z",
        "effectiveStartDate": "2015-11-24T08: 00: 00Z",
        "commitmentEndDate": "2016-12-12T08: 00: 00Z",
        "status": "active",
        "autoRenewEnabled": false,
        "billingType": "none",
        "contractType": "subscription",
        "links": {
            "offer": {
                "uri": "/v1/offers/0CCA44D6-68E9-4762-94EE-31ECE98783B9",
                "method": "GET",
                "headers": []
            },
            "self": {
                "uri": "/subscriptions?key=<key>",
                "method": "GET",
                "headers": []
            }
        },
        "orderId": "6183db3d-6318-4e52-877e-25806e4971be",
        "attributes": {
            "etag": "<etag>",
            "objectType": "Subscription"
        }
    }],
    "attributes": {
        "objectType": "Collection"
    }
}
```
```
{ 
    "totalCount": 1, 
    "items": [ 
        { 
            "id": "924671ba-eab9-45d7-95ed-dbd9477f182b", 
            "offerId": "DG7GMGF0FKZV:0003:DG7GMGF0DQLM", 
            "offerName": "SQL Server Enterprise - 2 Core License Pack - 3 year", 
            "friendlyName": "SQL Server Enterprise - 2 Core License Pack - 3 year", 
            "productType": { 
                "id": "Software", 
                "displayName": "Software" 
            }, 
            "quantity": 1, 
            "unitType": "Licenses", 
            "hasPurchasableAddons": false, 
            "creationDate": "2021-10-15T21:28:19.3058617Z", 
            "effectiveStartDate": "2021-10-15T21:28:18.4786844Z", 
            "commitmentEndDate": "2024-10-14T00:00:00Z", 
            "cancellationAllowedUntilDate": "2021-11-14T23:59:00Z", 
            "status": "active", 
            "autoRenewEnabled": true, 
            "isTrial": false, 
            "billingType": "license", 
            "billingCycle": "triennial", 
            "termDuration": "P3Y", 
            "renewalTermDuration": "", 
            "isMicrosoftProduct": true, 
            "partnerId": "", 
            "attentionNeeded": false, 
            "actionTaken": false, 
            "contractType": "subscription", 
            "links": { 
                "product": { 
                    "uri": "/products/DG7GMGF0FKZV?country=US", 
                    "method": "GET", 
                    "headers": [] 
                }, 
                "sku": { 
                    "uri": "/products/DG7GMGF0FKZV/skus/0003?country=US", 
                    "method": "GET", 
                    "headers": [] 
                }, 
                "availability": { 
                    "uri": "/products/DG7GMGF0FKZV/skus/0003/availabilities/DG7GMGF0DQLM?country=US", 
                    "method": "GET", 
                    "headers": [] 
                }, 
                "self": { 
                    "uri": "/customers/954ca09a-1132-4088-bb58-30438dea2756/subscriptions/924671ba-eab9-45d7-95ed-dbd9477f182b", 
                    "method": "GET", 
                    "headers": [] 
                } 
            }, 
            "publisherName": "Microsoft", 
            "orderId": "12345678901", 
            "attributes": { 
                "objectType": "Subscription" 
            } 
        } 
    ], 
    "links": { 
        "self": { 
            "uri": "/customers/954ca09a-1132-4088-bb58-30438dea2756/subscriptions", 
            "method": "GET", 
            "headers": [] 
        } 
    }, 
    "attributes": { 
        "objectType": "Collection" 
    } 
} 
```
