---
title: Get support profile
description: Gets an object representing a user's support profile.
ms.date: 6/29/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: JulCsc
ms.author: shishir
---

# Get support profile

**Applies to**: Partner Center |  Partner Center for Microsoft Cloud for US Government

Gets an object representing a user's support profile.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with App+User credentials only.

## C\#

To get your support profile, use your **IAggregatePartner.Profiles** collection. Call the [**SupportProfile**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile) property, followed by the [**Get()**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile.getasync) methods.

``` csharp
// IAggregatePartner partnerOperations;

SupportProfile supportProfile = partnerOperations.Profiles.SupportProfile.Get();
```

**Sample**: [Console test app](console-test-app.md). **Project**: PartnerCenterSDK.FeaturesSamples **Class**: GetSupportProfile.cs

## REST request

### Request syntax

| Method  | Request URI                                                              |
|---------|--------------------------------------------------------------------------|
| **GET** | [*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/support HTTP/1.1 |

### Request headers

For more information, see [Partner Center REST headers](headers.md).

### Request body

None.

### Request example

```http
GET https://api.partnercenter.microsoft.com/v1/profiles/support HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 07029132-385d-416f-a9a6-df5e9e4c78d3
MS-CorrelationId: 20604323-50bf-4738-9968-c5486ab32be0
```

## REST response

If successful, this method returns a **[SupportProfile](profile-resources.md#supportprofile)** object in the response body.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Error Codes](error-codes.md).

### Response example

```http
HTTP/1.1 200 OK 
Content-Length: 502 
Content-Type: application/json 
MS-CorrelationId: 20604323-50bf-4738-9968-c5486ab32be0 
MS-RequestId: 07029132-385d-416f-a9a6-df5e9e4c78d3 
Date: Wed, 25 Nov 2015 07:16:17 GMT 

{ 
    "email": "email@sample.com", 
    "telephone": "4255555555", 
    "website": "www.microsoft.com", 
    "profileType": " SupportProfile", 

    "links": { 
        "self": { 
            "uri": "/v1/profiles/support", 
            "method": "GET", 
            "headers": [] 
        } 
    }, 

    "attributes": { 
        "objectType": "SupportProfile" 
    } 
} 
```
