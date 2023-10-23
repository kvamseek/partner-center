---
title: Create a self-serve policy
description: How to create a new self-serve policy.
ms.date: 06/28/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: BrentSerbus
ms.author: brserbus
---

# Create a SelfServePolicy

This article explains how to create a new self-serve policy.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with Application+User credentials.

## C\#

Create a self-serve policy:

1. Call the [**IAggregatePartner.SelfServePolicies.Create**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.create?view=partnercenter-dotnet-latest#microsoft-store-partnercenter-genericoperations-ientitycreateoperations-2-create(-0)&preserve-view=true) or [**IAggregatePartner.SelfServePolicies.CreateAsync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.createasync?view=partnercenter-dotnet-latest#microsoft-store-partnercenter-genericoperations-ientitycreateoperations-2-createasync(-0)&preserve-view=true) method with the self-serve policy info.

``` csharp
// IAggregatePartner partnerOperations;
string customerIdAsEntity;

var selfServePolicy = new SelfServePolicy
{
    SelfServeEntity = new SelfServeEntity
    {
        SelfServeEntityType = "customer",
        TenantID = customerIdAsEntity,
    },
    Grantor = new Grantor
    {
        GrantorType = "billToPartner",
        TenantID = partnerIdAsGrantor,
    },
    Permissions = new Permission[]
    {
        new Permission
        {
        Action = "Purchase",
        Resource = "AzureReservedInstances",
        },
    },
    {
        new Permission
        {
        Action = "Purchase",
        Resource = "AzureSavingsPlan",
        },
    },
};

// All the operations executed on this partner operation instance will share the same correlation Id but will differ in request Id
IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

// creates the self-serve policy
SelfServePolicy createdSelfServePolicy = scopedPartnerOperations.selfServePolicies.Create(selfServePolicy);
```

For an example, see the following:

- Sample: [Console test app](console-test-app.md)
- Project: **PartnerSDK.FeatureSamples**
- Class: **CreateSelfServePolicies.cs**


## REST request

### Request syntax

| Method   | Request URI                                                       |
|----------|-------------------------------------------------------------------|
| **POST** | [*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy HTTP/1.1 |

### Request headers

- A request ID and correlation ID are required.
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
| SelfServeEntity       | SelfServeEntity  | The self-serve entity that is being granted access.                                                     |
| Grantor               | Grantor          | The grantor that is granting access.                                                                    |
| Permissions           | Array of Permission| An Array of [Permission](self-serve-policy-resources.md#permission) resources.                                                                     |


### Request example

```http
POST https://api.partnercenter.microsoft.com/v1/SelfServePolicy HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 789
Expect: 100-continue
Connection: Keep-Alive

{
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
    ]
}
```

## REST response

If successful, this API returns a [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) resource for the new self-serve policy.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Partner Center REST error codes](error-codes.md).

This method returns the following error codes:

| HTTP Status Code     | Error code   | Description                                                                |
|----------------------|--------------|----------------------------------------------------------------------------|
| 409                  | 600041       | Self-serve policy already exists.                                                     |


### Response example

```http
HTTP/1.1 201 Created
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
        "etag": "\"933523d1-3f63-4fc3-8789-5e21c02cdaed\"",
        "objectType": "SelfServePolicy"
    }
}
```
