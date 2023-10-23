---
title: Get partner profile
description: Gets an object representing the partner's Microsoft AI Cloud Partner Program profile.
ms.date: 6/16/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: JulCsc
ms.author: shishir
---

# Get partner profile

**Applies to**: Partner Center | Partner Center operated by 21Vianet |  Partner Center for Microsoft Cloud for US Government

Gets an object representing the partner's Microsoft AI Cloud Partner Program profile.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with App+User credentials only.

## C\#

To get a partner network profile, use your **IAggregatePartner.Profiles** collection and call the **MpnProfile** property. Finally, call the [**Get()**](/dotnet/api/microsoft.store.partnercenter.profiles.impnprofile.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.profiles.impnprofile.getasync) methods.

``` csharp
// IAggregatePartner partnerOperations;

var mpnProfile = partnerOperations.Profiles.MpnProfile.Get();
```

**Sample**: [Console test app](console-test-app.md). **Project**:PartnerCenterSDK.FeaturesSamples **Class**: GetMPNProfile.cs

## Java

[!INCLUDE [Partner Center Java SDK support details](./includes/java-sdk-support.md)]

To get a partner network profile, use your **IAggregatePartner.getProfiles** function and call the **getMpnProfile** function. Finally, call the **get()** function.

```java
// IAggregatePartner partnerOperations;

MpnProfile mpnProfile = partnerOperations.getProfiles().getMpnProfile().get();
```

## PowerShell

[!INCLUDE [Partner Center PowerShell module support details](./includes/powershell-module-support.md)]

To get a partner network profile, execute the [**Get-PartnerMpnProfile**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerMpnProfile.md) command.

```powershell
Get-PartnerMpnProfile
```

## REST request

### Request syntax

| Method  | Request URI                                                          |
|---------|----------------------------------------------------------------------|
| **GET** | [*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/mpn HTTP/1.1 |

### Request headers

For more information, see [Partner Center REST headers](headers.md).

### Request body

None.

### Request example

```http
GET https://api.partnercenter.microsoft.com/v1/profiles/mpn HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 76879323-92d1-437e-90dd-c84dbb9f7dec
MS-CorrelationId: cb9f3209-d020-4bf9-871c-e1f1c75348f8
Connection: Keep-Alive
```

## REST response

If successful, this method returns a **MPNProfile** object in the response body.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Error Codes](error-codes.md).

### Response example

```http
HTTP/1.1 200 OK
Content-Length: 177
Content-Type: application/json; charset=utf-8
MS-CorrelationId: cb9f3209-d020-4bf9-871c-e1f1c75348f8
MS-RequestId: 76879323-92d1-437e-90dd-c84dbb9f7dec
Date: Mon, 21 Mar 2016 05:51:29 GMT

{
    "mpnId":"<mpnID>",
    "profileType":"MpnProfile",
    "links":{
        "self":{
            "uri":"/profiles/mpn",
            "method":"GET",
            "headers":[]
        }
    },
    "attributes":{
        "objectType":"MpnProfile"
    }
}
```
