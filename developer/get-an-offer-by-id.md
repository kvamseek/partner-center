---
title: Get an offer by ID
description: Gets an Offer resource that matches the offer ID.
ms.date: 08/23/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: iragulati1
ms.author: iragulati
---

# Get an offer by ID

**Applies to**: Partner Center | Partner Center operated by 21Vianet |  Partner Center for Microsoft Cloud for US Government

Gets an **Offer** resource that matches the offer ID.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with both standalone App and App+User credentials.

- An offer ID.

## C\#

To find a specific offer by ID, use your **IAggregatePartner.Offers** collection, establish the country/region with a call to **ByCountry()**, and then call the [**ByID()**](/dotnet/api/microsoft.store.partnercenter.offers.ioffercollection.byid) method. Then, call the [**Get()**](/dotnet/api/microsoft.store.partnercenter.offers.ioffercollection.get) or [**Get Async()**](/dotnet/api/microsoft.store.partnercenter.offers.ioffercollection.getasync) method.

```csharp
// IAggretagePartner partnerOperations;
// string countryCode;
// string offerId;

// retrieve the offer
var offer = partnerOperations.Offers.ByCountry(countryCode).ById(offerId).Get();
```

**Sample**: [Console test app](console-test-app.md). **Project**: PartnerSDK.FeatureSample **Class**: GetOffer.cs

## Java

[!INCLUDE [Partner Center Java SDK support details](./includes/java-sdk-support.md)]

To find a specific offer by ID, use your **IAggregatePartner.getOffers** function, establish the country/region with a call to the **byCountry()** function, and then call the **byID()** function. Then call the **get()** function.

```java
// IAggretagePartner partnerOperations;
// String countryCode;
// String offerId;

// Retrieve the offer
Offer offer = partnerOperations.getOffers().byCountry(countryCode).byId(offerId).get();
```

## PowerShell

[!INCLUDE [Partner Center PowerShell module support details](./includes/powershell-module-support.md)]

To find a specific offer by ID, execute the [**Get-PartnerOffer**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerOffer.md) command, and specify the **CountryCode** and **OfferId** parameters.

```powershell
# $countryCode
# $offerId

Get-PartnerOffer -Country $countryCode -OfferId $offerId
```

## REST request

### Request syntax

| Method  | Request URI                                                                                    |
|---------|------------------------------------------------------------------------------------------------|
| **GET** | [*{baseURL}*](partner-center-rest-urls.md)/v1/offers/{offer-id}?country={country-id} HTTP/1.1 |

### URI parameter

| Name           | Type       | Required | Description                           |
|----------------|------------|----------|---------------------------------------|
| **offer-id**   | **guid**   | Y        | A GUID that corresponds to the offer. |
| **country-id** | **string** | Y        | The country/region ID.                |

### Request headers

- A **locale-id** formatted as a string is required.
For more information, see [Partner Center REST headers](headers.md).

### Request body

None.

### Request example

```http
GET https://api.partnercenter.microsoft.com/v1/offers/<offer-id>?country=<country-id> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ac943950-ba3d-47a0-bd2a-c5617a7fefe8
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
X-Locale: <locale-id>
Connection: Keep-Alive
```

## REST response

If successful, this method returns an **Offer** resource in the response body.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Error Codes](error-codes.md).

### Response example

```http
HTTP/1.1 200 OK
Content-Length: 1918
Content-Type: application/json
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
MS-RequestId: ac943950-ba3d-47a0-bd2a-c5617a7fefe8
Date: Mon, 23 Nov 2015 23:13:01 GMT

{
    "id": "031C9E47-4802-4248-838E-778FB1D2CC05",
    "name": "Office 365 Business Premium",
    "description": "For businesses with 1 to 300 users that need the latest desktop version of Office,
                    plus anywhere access to email, filesharing, and online conferencing.",
    "minimumQuantity": 1,
    "maximumQuantity": 300,
    "rank": 56,
    "uri": "/3c95518e-8c37-41e3-9627-0ca339200f53/Offers/031C9E47-4802-4248-838E-778FB1D2CC05",
    "locale": "en-us",
    "country": "US",
    "category": {
        "id": "SmallBusiness_Key",
        "name": "Small Business",
        "rank": 30,
        "locale": "en-us",
        "country": "US",
        "attributes": {
            "objectType": "OfferCategory"
        }
    },
    "prerequisiteOffers": [],
    "isAddOn": false,
    "isAvailableForPurchase": true,
    "billing": "license",
    "isAutoRenewable": true,
    "product": {
        "id": "f245ecc8-75af-4f8e-b61f-27d8114de5f3",
        "name": "Office 365 Business Premium",
        "unit": "Licenses"
    },
    "unitType": "Licenses",
    "links": {
        "learnMore": {
            "uri": "http: //g.microsoftonline.com/0BXPS00en/909",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Offer"
    }
}
```
