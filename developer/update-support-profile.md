---
title: Update support profile
description: Updates a user's support profile.
ms.date: 6/22/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
ms.author: juliegray
---

# Update support profile

**Applies to**: Partner Center | Partner Center operated by 21Vianet |  Partner Center for Microsoft Cloud for US Government

Updates a user's support profile.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with App+User credentials only.

## C\#

To update your support profile, first [get your support profile](get-support-profile.md) and make any changes you wish. Then, use your [**IPartnerOperations.Profiles**](/dotnet/api/microsoft.store.partnercenter.ipartner.profiles) collection. Call the [**SupportProfile**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile) property, followed by the [**Update()**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile.update) or [**UpdateAsync()**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile.updateasync) method.

``` csharp
// IAggregatePartner partnerOperations;

// updated profile
SupportProfile newSupportProfile = new SupportProfile
{
   Email = supportProfile.Email,
   Website = supportProfile.Website,
   Telephone = new Random().Next(10000000, 99999999).ToString(CultureInfo.InvariantCulture)
};

SupportProfile updatedSupportProfile = partnerOperations.Profiles.SupportProfile.Update(newSupportProfile);
```

**Sample**: [Console test app](console-test-app.md). **Project**: PartnerCenterSDK.FeaturesSamples **Class**: UpdateSupportProfile.cs

## REST request

### Request syntax

| Method  | Request URI                                                                     |
|---------|---------------------------------------------------------------------------------|
| **PUT** | [*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/supportprofile HTTP/1.1 |

### Request headers

For more information, see [Partner Center REST headers](headers.md).

### Request body

The full support profile resource.

### Request example

```http
PUT https://api.partnercenter.microsoft.com/v1/profiles/supportprofile HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 603f3cd9-01b8-48f2-b65d-855a246f5bfd
MS-CorrelationId: 20604323-50bf-4738-9968-c5486ab32be0
Content-Type: application/json
Content-Length: 167
Expect: 100-continue

{
    "Email": "email@sample.com",
    "Telephone": "4255555555",
    "Website": "www.microsoft.com",
    "ProfileType": "support_profile",
    "Attributes": {
        "ObjectType": "PartnerSupportProfile"
    }
}
```

## REST response

If successful, this method returns updated **SupportProfile** object properties in the response body.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Error Codes](error-codes.md).

### Response example

```http
HTTP/1.1 200 OK
Content-Length: 502
Content-Type: application/json
MS-CorrelationId: 20604323-50bf-4738-9968-c5486ab32be0
MS-RequestId: 603f3cd9-01b8-48f2-b65d-855a246f5bfd
Date: Wed, 25 Nov 2015 07:16:18 GMT

{
    "email": "email@sample.com",
    "telephone": "4255555555",
    "website": "www.microsoft.com",
    "profileType": "support_profile",
    "links": {
        "self": {
            "uri": "/v1/profiles/support",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "PartnerSupportProfile"
    }
}
```
