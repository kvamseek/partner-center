---
title: Update a self-serve policy
description: How to update a self-serve-policy.
ms.date: 6/30/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
ms.author: raormeni
---

# Update a SelfServePolicy

This article explains how to update a self-serve policy.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with Application+User credentials.

## C\#

To update a self-serve policy:

1. Call the [**IAggregatePartner.SelfServePolicies.ById**](/dotnet/api/microsoft.store.partnercenter.selfservepolicies.iselfservepoliciescollection.byid?view=partnercenter-dotnet-latest&preserve-view=true) method with the entity identifier to retrieve an interface to operations on the policies.

2. Call the [**Put**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientityputoperations-1.put?view=partnercenter-dotnet-latest#microsoft-store-partnercenter-genericoperations-ientityputoperations-1-put(-0)&preserve-view=true) or [**PutAsync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientityputoperations-1.putasync?view=partnercenter-dotnet-latest&preserve-view=true) method to update the self-serve policy.

``` csharp
// IAggregatePartner partnerOperations;
SelfServePolicy policy;

// All the operations executed on this partner operation instance will share the same correlation identifier but will differ in request identifier
IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

// updates the self-serve policies
partnerOperations.SelfServePolicies.ById(policy.id).Put(policy);
```

## REST request

### Request syntax

| Method   | Request URI                                                       |
|----------|-------------------------------------------------------------------|
| **PUT** | [*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy HTTP/1.1 |

### Request headers

- A request identifier and correlation identifier are required.
- For more information, see [Partner Center REST headers](headers.md).

### Request body

This table describes the required properties in the request body.

| Name                              | Type   | Description                                 |
|------------------------------------------------------------------|--------|---------------------------------------------|
| [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy)| object | The self-serve policy information. |

#### SelfServePolicy

This table describes the minimum required fields from the [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) resource needed to create a new self-serve policy.

| Property              | Type             | Description                                                                                            |
|-----------------------|------------------|--------------------------------------------------------------------------------------------------------|
| id                    | string           | A self-serve policy identifier that is supplied upon successful creation of the self-serve policy.     |
| SelfServeEntity       | SelfServeEntity  | The self-serve entity that is being granted access.                                                     |
| Grantor               | Grantor          | The grantor that is granting access.                                                                    |
| Permissions           | Array of Permission| An Array of [Permission](self-serve-policy-resources.md#permission) resources.                                                      |
| Etag                  | string           | The Etag.                                                                                               |


### Request example

```http
PUT https://api.partnercenter.microsoft.com/v1/SelfServePolicy HTTP/1.1
Authorization: Bearer <token>
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive

{
    "id": "634f6379-ad54-449b-9821-564f737158ab_0431a72c-7d8a-4393-b25e-ef63f5efb415",
    "selfServeEntity": {
        "selfServeEntityType": "customer",
        "tenantID": "0431a72c-7d8a-4393-b25e-ef63f5efb415"
    },
    "grantor": {
        "grantorType": "billToPartner",
        "tenantID": "634f6379-ad54-449b-9821-564f737158ab"
    },
    "permissions": [
        {
            "resource": "AzureReservedInstances",
            "action": "Purchase"
        },
        {
            "resource": "AzureSavingsPlan",
            "action": "Purchase"
        }
    ],
    "attributes": {
        "etag": "\"933523d1-3f63-4fc3-8789-5e21c02cdaed\"",
        "objectType": "SelfServePolicy"
    }
}
```

## REST response

If successful, this API returns a [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) resource for the updated self-serve policy.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Partner Center REST error codes](error-codes.md).

This method returns the following error codes:

| HTTP Status Code     | Error code   | Description                                                                |
|----------------------|--------------|----------------------------------------------------------------------------|
| 404                  | 600039       | Self-serve policy was not found                                            |
| 404                  | 600040       | Self-serve policy identifier is incorrect                                  |


### Response example

```http
HTTP/1.1 200 Ok
Content-Length: 834
Content-Type: application/json; charset=utf-8
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
Date: Tue, 14 Feb 2017 20:06:02 GMT

{
    "id": "634f6379-ad54-449b-9821-564f737158ab_0431a72c-7d8a-4393-b25e-ef63f5efb415",
    "selfServeEntity": {
        "selfServeEntityType": "customer",
        "tenantID": "0431a72c-7d8a-4393-b25e-ef63f5efb415"
    },
    "grantor": {
        "grantorType": "billToPartner",
        "tenantID": "634f6379-ad54-449b-9821-564f737158ab"
    },
    "permissions": [
        {
            "resource": "AzureReservedInstances",
            "action": "Purchase"
        },
        {
            "resource": "AzureSavingsPlan",
            "action": "Purchase"
        }
    ],
    "attributes": {
        "etag": "\"1ec98034-a249-46f4-b9dd-9cd464fb5e47\"",
        "objectType": "SelfServePolicy"
    }
}
```
