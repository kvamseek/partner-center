---
title: Get a list of products (by country/region)
description: You can use the Product resource to get a collection of products by customer country/region.
ms.date: 08/23/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: iragulati1
ms.author: iragulati
---

# Get a list of products (by country/region)

**Applies to**: Partner Center | Partner Center operated by 21Vianet |  Partner Center for Microsoft Cloud for US Government

You can use the following methods to get a collection of products available in a particular country/region.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with both standalone App and App+User credentials.

- A country/region.

## C\#

To get a list of products:

1. Use your **IAggregatePartner.Products** collection to select the country/region by using the **ByCountry()** method.

2. Select the catalog view using the **ByTargetView()** method.

3. (Optional) Select the reservation scope using the **ByReservationScope()** method.

4. (Optional) Select the target segment using the **ByTargetSegment()** method.

5. Call the **Get()** or **GetAsync()** method to return the collection.

```csharp
IAggregatePartner partnerOperations;

// Get the products for the specified catalog view.
ResourceCollection<Products> products = partnerOperations.Products.ByCountry("US").ByTargetView("MicrosoftAzure").Get();

// Get the products filtered by target view and target segment.
ResourceCollection<Products> products = partnerOperations.Products.ByCountry("US").ByTargetView("MicrosoftAzure").ByTargetSegment("commercial").Get();

// Get the products for Azure reservations which are applicable to Microsoft Azure (MS-AZR-0145P) subscriptions only.
ResourceCollection<Product> products = partnerOperations.Products.ByCountry("US").ByTargetView("AzureReservations").Get();

// Get the products for Azure reservations which are applicable to Azure plans only.
ResourceCollection<Product> products = partnerOperations.Products.ByCountry("US").ByTargetView("AzureReservations").ByReservationScope("AzurePlan").Get();

```

## Java

[!INCLUDE [Partner Center Java SDK support details](./includes/java-sdk-support.md)]

To get a list of products:

1. Use your **IAggregatePartner.getProducts** function to select the country by using the **byCountry()** function.

2. Select the catalog view using the **byTargetView()** function.
3. (Optional) Select the target segment using the **byTargetSegment()** function.

4. Call the **get()** function to return the collection.

```java
// IAggregatePartner partnerOperations;

// Get the products for the specified catalog view.
ResourceCollection<Products> products = partnerOperations.getProducts().byCountry("US").byTargetView("Azure").get();

// Get the products filtered by target view and target segment.
ResourceCollection<Products> products = partnerOperations.getProducts().byCountry("US").byTargetView("Azure").byTargetSegment("commercial").get();
```

## PowerShell

[!INCLUDE [Partner Center PowerShell module support details](./includes/powershell-module-support.md)]

To get a list of products:

1. Execute the [**Get-PartnerProduct**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProduct.md) command.

2. Select the catalog by specifying the **Catalog** parameter.
3. (Optional) Select the target segment by specifying the **Segment** parameter.

```powershell
Get-PartnerProduct -Catalog 'Azure' -Segment 'commercial'
```

## REST request

### Request syntax

| Method  | Request URI                                                                                                                                    |
|---------|----------------------------------------------------------------------------------------------------------------------------------------------- |
| **GET** | [*{baseURL}*](partner-center-rest-urls.md)/v1/products?country={country}&targetView={targetView}&targetSegment={targetSegment} HTTP/1.1 |

#### URI parameters

Use the following path and query parameters to get a list of products.

| Name                   | Type     | Required | Description                                                             |
|------------------------|----------|----------|-------------------------------------------------------------------------|
| country                | string   | Yes      | The country/region ID.                                                  |
| targetView             | string   | Yes      | Identifies the target view of the catalog. The supported values are: <br/><br/>**Azure**, which includes all Azure items<br/><br/>**AzureReservations**, which includes all Azure reservation items<br/><br/>**AzureReservationsVM**, which includes all virtual machine (VM) reservation items<br/><br/>**AzureReservationsSQL**, which includes all SQL reservation items<br/><br/>**AzureReservationsCosmosDb**, which includes all Cosmos database reservation items<br/><br/>**MicrosoftAzure**, which includes items for Microsoft Azure subscriptions (**MS-AZR-0145P**) and Azure plans<br/><br/>**OnlineServices**, which includes all online service items such as traditional license-based services and new commerce license-based services.<br/><br/>**Software**, which includes all software items<br/><br/>**SoftwareSUSELinux**, which includes all software SUSE Linux items<br/><br/>**SoftwarePerpetual**, which includes all perpetual software items<br/><br/>**SoftwareSubscriptions**, which includes all software subscription items<br/><br/>**SpecializedOffers**, which includes specialized offers that have been made available to some partners<br><br>**MarketplaceSaaS**, which includes all commercial marketplace offers published by Independent Software Vendors (ISVs)  |
| targetSegment          | string   | No       | Identifies the target segment. The view for different target audiences. The supported values are: <br/><br/>**commercial**<br/>**education**<br/>**government**<br/>**nonprofit**  |
| reservationScope | string   | No | When querying for a list of products for Azure Reservations, specify `reservationScope=AzurePlan` to get a list of products that are applicable to Azure plans. Exclude this parameter to get a list of products for Azure reservations, which are applicable to Microsoft Azure (**MS-AZR-0145P**) subscriptions.  |
### Request headers

For more information, see [Partner Center REST headers](headers.md).

### Request body

None.

### Request examples

#### Products by country

Follow this example to get a list of products by country for Microsoft Azure (MS-AZR-0145P) subscriptions and Azure plans.

```http
GET https://api.partnercenter.microsoft.com/v1/products?country=US&targetView=MicrosoftAzure HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

#### Azure VM reservations (Azure plan)

Follow this example to get a list of products by country for Azure VM reservations that are applicable to Azure plans.

```http
GET https://api.partnercenter.microsoft.com/v1/products?country=US&targetView=AzureAzureReservationsVM&reservationScope=AzurePlan HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

#### Azure VM reservations for Microsoft Azure (MS-AZR-0145P) subscriptions

Follow this example to get a list of products by country for Azure VM reservations that are applicable to Microsoft Azure (MS-AZR-0145P) subscriptions.

```http
GET https://api.partnercenter.microsoft.com/v1/products?country=US&targetView=AzureReservationsVM HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

#### New commerce license-based services

> [!Note] 
> The new commerce experiences for license-based services include many new capabilities and are available to all Cloud Solution Provider (CSPs). For more information, see [new commerce experiences overview](../new-commerce-license-based.md).

Follow this example to get a list of products by country for new commerce license-based services as part of the new commerce experience technical preview. New commerce license-based services will be identified by ID and displayNames values of **OnlineServicesNCE**. See response example below.

```http
GET https://api.partnercenter.microsoft.com/v1/products?country=US&targetView=OnlineServices HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

## REST response

If successful, the response body contains a collection of [**Product**](product-resources.md#product) resources.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Partner Center error codes](error-codes.md).

This method returns the following error codes:

| HTTP Status Code     | Error code   | Description                                                                                               |
|----------------------|--------------|-----------------------------------------------------------------------------------------------------------|
| 403                  | 400030       | Access to the requested targetSegment is not allowed.                                                     |
| 403                  | 400036       | Access to the requested targetView is not allowed.                                                        |

### Response example for Azure VM reservations (Azure plan)

```http
{
    "totalCount": 19,
    "items": [
        {
            "id": "DZH318Z0BQ3Q",
            "title": "Virtual Machines DSv2 Series",
            "description": "Dsv2-series instances are the latest generation of D-series instances that will carry more powerful CPUs which are on average about 35% faster than D-series instances, and carry the same memory and disk configurations as the D-series. Dsv2-series instances are based on the latest generation 2.4 GHz Intel Xeon® E5-2673 v3 (Haswell) processor, and with Intel Turbo Boost Technology 2.0 can go to 3.2 GHz.",
            "productType": {
                "id": "Azure",
                "displayName": "Azure",
                "subType": {
                "id": "VirtualMachines",
                "displayName": "VirtualMachines"
                }
            },
            "isMicrosoftProduct": true,
            "publisherName": "Microsoft",
            "links": {
                "skus": {
                    "uri": "/products/DZH318Z0BQ3Q/skus?country=US",
                    "method": "GET",
                    "headers": []
                },
                "self": {
                    "uri": "/products/DZH318Z0BQ3Q?country=US",
                    "method": "GET",
                    "headers": []
                }
            }
        },
        ...
    ],
    "links": {
        "self": {
            "uri": "/products?country=US&targetView=Azure",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```

### Response example for new commerce license-based services

> [!NOTE] 
> The new commerce experiences for license-based services include many new capabilities and are available to all Cloud Solution Provider (CSPs). For more information, see [new commerce experiences overview](../new-commerce-license-based.md).

```http
{
  "totalCount": 19,
  "items": [{
      "id": "CFQ7TTC0LH18",
      "title": "Microsoft 365 Business Basic",
      "description": "Best for businesses that need professional email, cloud file storage, and online meetings & chat. Desktop versions of Office apps like Excel, Word, and PowerPoint not included. For businesses with up to 300 employees.",
      "productType": {
        "id": "OnlineServicesNCE",
        "displayName": "OnlineServicesNCE"
      },
      "isMicrosoftProduct": true,
      "publisherName": "Microsoft Corporation",
      "links": {
        "skus": {
          "uri": "/products/CFQ7TTC0LH18/skus?country=US",
          "method": "GET",
          "headers": []
        },
        "self": {
          "uri": "/products/CFQ7TTC0LH18?country=US",
          "method": "GET",
          "headers": []
        }
      }
    },
    ...
  ],
  "links": {
    "self": {
      "uri": "/products?country=US&targetView=OnlineServices",
      "method": "GET",
      "headers": []
    }
  },
  "attributes": {
    "objectType": "Collection"
  }
}
```
