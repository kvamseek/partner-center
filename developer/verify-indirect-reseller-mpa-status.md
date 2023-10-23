---
title: Verify an indirect reseller's Microsoft Partner Agreement signing status
description: You can use the AgreementStatus API to verify whether an indirect reseller has signed the Microsoft Partner Agreement.
ms.date: 06/29/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: JulCsc
ms.author: shishir
---

# Verify an indirect reseller's Microsoft Partner Agreement signing status

**Applies to**: Partner Center | Partner Center for Microsoft Cloud for US Government

You can verify whether an indirect reseller has signed the Microsoft Partner Agreement using their PartnerID (PGA/PLA) or Cloud Solution Provider (CSP) tenant ID (Microsoft ID). You can use one of these identifiers to check the Microsoft Partner Agreement signing status using the **AgreementStatus** API.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with App+User credentials only.

- The PartnerID (PGA/PLA) or the CSP tenant ID (Microsoft ID) of the indirect reseller. *You must use one of these two identifiers.*

## C\#

To get the Microsoft Partner Agreement signature status of an indirect reseller:

1. Use your **IAggregatePartner.Compliance** collection to call the **AgreementSignatureStatus** property.

2. Call the [**Get()**](/dotnet/api/microsoft.store.partnercenter.compliance.iagreementsignaturestatus.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.compliance.iagreementsignaturestatus.getasync) method.

``` csharp
// IAggregatePartner partnerOperations;

var agreementSignatureStatusByMpnId = partnerOperations.Compliance.AgreementSignatureStatus.Get(mpnId:"Enter MPN Id (PGA/PLA)");

var agreementSignatureStatusByTenantId = partnerOperations.Compliance.AgreementSignatureStatus.Get(tenantId: "Enter Tenant Id");
```

- Sample: **[Console test app](console-test-app.md)**
- Project: **PartnerCenterSDK.FeaturesSamples**
- Class: **GetAgreementSignatureStatus.cs**

## REST request

### Request syntax

| Method | Request URI |
| ------ | ----------- |
| **GET** | *[{baseURL}](partner-center-rest-urls.md)*/v1/compliance/{ProgramName}/agreementstatus?mpnId={MpnId}&tenantId={TenantId} |

#### URI parameters

You must provide one of the following two query parameters to identify the partner. If you don't provide one of these two query parameters, you will receive a **400 (Bad request)** error.

| Name | Type | Required | Description |
| ---- | ---- | -------- | ----------- |
| **MpnId** | int | No | A PartnerID (PGA/PLA) that identifies the indirect reseller. |
| **TenantId** | GUID | No | A Microsoft ID that identifies the CSP account of the indirect reseller. |

### Request headers

For more information, see [Partner Center REST](headers.md).

### Request examples

#### Request using PartnerID (PGA/PLA)

The following example request gets the indirect reseller's Microsoft Partner Agreement signing status using the indirect reseller's PartnerID.

```http
GET https://api.partnercenter.microsoft.com/v1/compliance/csp/agreementstatus?mpnid=1234567 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

#### Request using CSP tenant ID

The following example request gets the indirect reseller's Microsoft Partner Agreement signing status using the indirect reseller's CSP tenant ID (Microsoft ID).

```http
GET https://api.partnercenter.microsoft.com/v1/compliance/csp/agreementstatus?tenantId=a2898e3a-06ca-454e-a0d0-c73b0ee36bba HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## REST response

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Partner Center REST error](error-codes.md).

### Response example (success)

The following example response successfully returns whether the indirect reseller has signed the Microsoft Partner Agreement.

```http
HTTP/1.1 200 OK
Content-Length: 29
Content-Type: application/json; charset=utf-8
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CV: jn3r+1wpE06nCt/0.0
MS-ServerId: 0000005B
Date: Tue, 15 Oct 2019 12:44:34 GMT
Connection: close
{
    "isAgreementSigned": true
}
```

### Response examples (failure)

You may receive responses similar to the following examples when the signing status of the indirect reseller's Microsoft Partner Agreement can't be returned.

#### Non-GUID formatted CSP tenant ID

The following example response is returned when the CSP tenant ID that you passed to the API isn't a GUID.

```http
HTTP/1.1 400 Bad Request
Content-Length: 105
Content-Type: application/json; charset=utf-8
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CV: rbuZl5lbAkyq8WGK.0
MS-ServerId: 00000055
Date: Wed, 16 Oct 2019 08:55:23 GMT
Connection: close
{
    "code": 2000,
    "description": "Tenant Id must be a GUID.",
    "data": [],
    "source": "PartnerApiServiceControllers"
}
```

#### Non-numeric PartnerID

The following example response is returned when the PartnerID (PGA/PLA) that you passed to the API is non-numeric.

```http
HTTP/1.1 400 Bad Request
Content-Length: 103
Content-Type: application/json; charset=utf-8
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CV: cP5JiS4sv0GJxlJ9.0
MS-ServerId: 0000005B
Date: Wed, 16 Oct 2019 08:58:45 GMT
Connection: close
{
    "code": 2000,
    "description": "MPN Id must be numeric.",
    "data": [],
    "source": "PartnerApiServiceControllers"
}
```

#### No PartnerID or CSP tenant ID

The following example response is returned when you haven't passed an PartnerID (PGA/PLA) or CSP tenant ID to the API. You must pass one of the two ID types to the API.

```http
HTTP/1.1 400 Bad Request
Content-Length: 114
Content-Type: application/json; charset=utf-8
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CV: hEV736v4qk6joDMR.0
MS-ServerId: 00000055
Date: Wed, 16 Oct 2019 09:00:30 GMT
Connection: close
{
    "code": 2001,
    "description": "Both MPN Id and Tenant Id cannot be empty.",
    "data": [],
    "source": "ComplianceController"
}
```

#### Both PartnerID and CSP tenant ID passed

The following example response is returned when you pass both the PartnerID (PGA/PLA) and CSP tenant ID to the API. You must pass *only one* of the two identifier types to the API.

```http
HTTP/1.1 400 Bad Request
Content-Length: 119
Content-Type: application/json; charset=utf-8
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CV: WTsLWK5UlUW9sZjH.0
MS-ServerId: 0000005B
Date: Wed, 16 Oct 2019 09:02:30 GMT
Connection: close
{
    "code": 2000,
    "description": "Both MPN Id and Tenant Id should not be passed.",
    "data": [],
    "source": "ComplianceController"
}
```

#### CSP Indirect Reseller PartnerID (PGA/PLA) is either invalid or not migrated from Partner Membership Center to Partner Center

The following example response is returned when Indirect reseller PartnerID (PGA/PLA) passed is either invalid or it is not migrated from Partner Membership Center to Partner Center. [Learn More](https://partner.microsoft.com/resources/detail/migrate-pmc-pc-mpa-guide-pptx)

```http
HTTP/1.1 400 Bad Request 
Content-Length: 321 
Content-Type: application/json; charset=utf-8 
MS-CorrelationId: 9240230a-413f-4880-acbd-96d59a165474 
MS-RequestId: 92caacb1-8c9e-49af-8f85-83f271c85056 
MS-CV: V8eVMXvaBE6LHyq6.0 
MS-ServerId: 0000005B 
Date: Fri, 24 Jul 2020 11:56:46 GMT 
Connection: close 

{ 
    "code": 2200, 
    "description": "Requested MPN Id 123456 is either invalid or does not exist in Partner Center.", 
    "data": [ 

        "https://partner.microsoft.com/resources/detail/migrate-pmc-pc-mpa-guide-pptx" 
    ], 
    "source": "PartnerFD" 
} 
```

#### CSP Indirect Provider region and CSP Indirect Reseller region does not match

The following example response is returned when region of Indirect reseller PartnerID (PGA/PLA) doesn't match with region of the Indirect Provider. [Learn more](../mpa-indirect-provider-faq.yml) about CSP Regions.

```http
HTTP/1.1 400 Bad Request 
Content-Length: 119 
Content-Type: application/json; charset=utf-8 
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6 
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb 
MS-CV: WTsLWK5UlUW9sZjH.0 
MS-ServerId: 0000005B 
Date: Wed, 16 Oct 2019 09:02:30 GMT 
Connection: close 

{ 
    "code": 2201, 
    "description": "The CSP region of the requested PartnerID 123456 is India and doesn't match the CSP region United States of Indirect Provider with Tenant id a2898e3a-06ca-454e-a0d0-c73b0ee36bba.”, 
    "data": [ 

        "https://learn.microsoft.com/partner-center/mpa-indirect-provider-faq"  
    ], 
    "source": "PartnerFD" 
} 
```

#### CSP Indirect Reseller account exists in Partner Center but hasn't signed the MPA

The following example response is returned when CSP Indirect Reseller account in Partner Center hasn't signed the MPA. [Learn More](../mpa-indirect-provider-faq.yml)

```http
HTTP/1.1 400 Bad Request
Content-Length: 321
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 9240230a-413f-4880-acbd-96d59a165474
MS-RequestId: 92caacb1-8c9e-49af-8f85-83f271c85056
MS-CV: V8eVMXvaBE6LHyq6.0
MS-ServerId: 0000005B
Date: Fri, 24 Jul 2020 11:56:46 GMT
Connection: close
{
    "code": 2203,
    "description": "MPN Id 123456 has not signed Microsoft Partner Agreement (MPA) for the CSP region where the order is being placed. Please advise your reseller to sign MPA to continue with the order.",
    "data": [
        "https://learn.microsoft.com/partner-center/mpa-indirect-provider-faq"
    ],
    "source": "PartnerFD"
}
```

#### No CSP Indirect Reseller account is associated with the given PartnerID

The following example response is returned when Partner Center can recognize the PartnerID (PGA/PLA) passed in the request but there is no CSP enrollment associated to the given PartnerID (PGA/PLA). [Learn More](../mpa-indirect-provider-faq.yml)

```http
HTTP/1.1 400 Bad Request 
Content-Length: 321 
Content-Type: application/json; charset=utf-8 
MS-CorrelationId: 9240230a-413f-4880-acbd-96d59a165474 
MS-RequestId: 92caacb1-8c9e-49af-8f85-83f271c85056 
MS-CV: V8eVMXvaBE6LHyq6.0 
MS-ServerId: 0000005B
Date: Fri, 24 Jul 2020 11:56:46 GMT 
Connection: close 

{ 
    "code": 2204, 
    "description": "Requested MPN Id 123456 is not associated with any CSP Indirect Reseller account in Partner Center. Please advise your reseller to enroll into the CSP program as an indirect reseller in Partner Center to be compliant.", 
    "data": [ 

        "https://learn.microsoft.com/partner-center/mpa-indirect-provider-faq" 
    ], 
    "source": "PartnerFD" 
} 
```

#### Invalid Tenant ID

The following example response is returned when Partner Center doesn't find any account associated to the Tenant ID passed in the request.

```http
HTTP/1.1 400 Bad Request 
Content-Length: 321 
Content-Type: application/json; charset=utf-8 
MS-CorrelationId: 9240230a-413f-4880-acbd-96d59a165474 
MS-RequestId: 92caacb1-8c9e-49af-8f85-83f271c85056 
MS-CV: V8eVMXvaBE6LHyq6.0 
MS-ServerId: 0000005B 
Date: Fri, 24 Jul 2020 11:56:46 GMT 

Connection: close 
{ 
    "code": 2205, 
    "description": "Could not find account with id '12345678-ACBD-1234-ABCD-123456789ABC'.", 
    "data": [], 
    "source": "PartnerFD" 
} 
```

#### No MPA found with the given Tenant ID

The following example response is returned when Partner Center can't find any MPA signature with the given Tenant ID. [Learn More](../mpa-indirect-provider-faq.yml)

```http
HTTP/1.1 400 Bad Request
Content-Length: 321
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 9240230a-413f-4880-acbd-96d59a165474
MS-RequestId: 92caacb1-8c9e-49af-8f85-83f271c85056
MS-CV: V8eVMXvaBE6LHyq6.0
MS-ServerId: 0000005B
Date: Fri, 24 Jul 2020 11:56:46 GMT
Connection: close
{
    "code": 2206,
    "description": "Parnter Center Account associated to Tenant Id 12345678-ACBD-1234-ABCD-123456789ABC hasn't signed the agreement",
    "data": [
        "https://learn.microsoft.com/partner-center/mpa-indirect-provider-faq"
    ],
    "source": "PartnerFD"
}
```