---
title: Get agreement metadata for the Microsoft Customer Agreement
description: This article explains how to get agreement metadata for Microsoft Customer Agreement.
ms.date: 07/28/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: jischulz
ms.author: jischulz
---

# Get agreement metadata for the Microsoft Customer Agreement

**Applies to**: Partner Center

**Does not apply to**: Partner Center operated by 21Vianet |  Partner Center for Microsoft Cloud for US Government

Agreement metadata for Microsoft Customer Agreement is currently supported by Partner Center only in the Microsoft public cloud.

You must retrieve the agreement metadata for the Microsoft Customer Agreement before you can:

- [Confirm a customer's acceptance of the Microsoft Customer Agreement](./confirm-customer-consent-customer-agreement.md)
- [Retrieve a download link for the Microsoft Customer Agreement template](./download-customer-agreement-template.md)

## Prerequisites

- If you are using the Partner Center .NET SDK, version 1.14 or newer is required.

  > [!IMPORTANT]
  > As of June 2023, the latest Partner Center .NET SDK release 3.4.0 is now archived. You can [download the SDK release from GitHub](https://github.com/microsoft/partner-center-sdk-for-dotNET), along with a [readme file](https://github.com/microsoft/partner-center-sdk-for-dotNET#readme) that contains useful information.
  >
  > Partners are encouraged to continue to use the [Partner Center REST APIs](partner-center-rest-api-reference.md).

- Credentials as described in [Partner Center authentication](./partner-center-authentication.md). This scenario supports App+User authentication only.

## .NET (version 1.14 or newer)

To retrieve the agreement metadata for Microsoft Customer Agreement:

1. First, retrieve the **IAggregatePartner.AgreementDetails** collection.

2. Call **ByAgreementType** method to filter the collection to Microsoft Customer Agreement.

3. Finally, call **Get** or **GetAsync** method.

```csharp
// IAggregatePartner partnerOperations;

string agreementType = "MicrosoftCustomerAgreement";

var microsoftCustomerAgreementDetails = partnerOperations.AgreementDetails.ByAgreementType(agreementType).Get().Items.Single();
```

A complete sample can be found in the [GetAgreementDetails](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetAgreementDetails.cs) class from the [console test app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) project.

## REST request

To retrieve the agreement metadata for Microsoft Customer Agreement:

1. Create a REST request to retrieve the [AgreementMetaData](./agreement-metadata-resources.md) collection.

2. Use the **agreementType** query parameter to scope the result to only the Microsoft Customer Agreement.

### Request syntax

| Method | Request URI                                                         |
|--------|---------------------------------------------------------------------|
| GET    | [*\{baseURL\}*](partner-center-rest-urls.md)/v1/agreements?agreementType={agreement-type} HTTP/1.1 |

#### URI parameters

| Name                   | Type     | Required | Description                                                             |
|------------------------|----------|----------|-------------------------------------------------------------------------|
| agreement-type | string | No | Use this parameter to scope the query response to specific agreement type. The supported values are: <br/><br/>**MicrosoftCloudAgreement** that includes agreement metadata only of the type *MicrosoftCloudAgreement*<br/><br/>**MicrosoftCustomerAgreement** that includes agreement metadata only of the type *MicrosoftCustomerAgreement*.<br/><br/>**\*** that returns all agreement metadata. (Don't use **\*** unless your code has the necessary runtime logic to handle unfamiliar agreement types because Microsoft may introduce agreement metadata with new agreement types at any time.)<br/><br/> **Note:** If the URI parameter isn't specified, the query defaults to **MicrosoftCloudAgreement** for backward compatibility.  |

### Request headers

For more information, see [Partner Center REST headers](headers.md).

### Request body

None.

### Request example

```http
GET https://api.partnercenter.microsoft.com/v1/agreements?agreementType=MicrosoftCustomerAgreement HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## REST response

If successful, this method returns a collection of [**AgreementMetaData** resources](./agreement-metadata-resources.md) in the response body.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information.

Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Partner Center REST error codes](error-codes.md).

### Response example

```http
HTTP/1.1 200 OK
Content-Length: 620
Content-Type: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
{
    "totalCount": 1,
    "items": [
        {
            "templateId": "117a77b0-9360-443b-8795-c6dedc750cf9",
            "agreementType": "MicrosoftCustomerAgreement",
            "agreementLink": "https://aka.ms/customeragreement",
            "versionRank": 0
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
