---
title: Create a product upgrade entity for a customer
description: You can use the ProductUpgradeRequest resource to create a product upgrade entity to upgrade a customer to a given product family.
ms.date: 09/22/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: migolova
ms.author: migolova
---

# Create a product upgrade entity for a customer

You can create a product upgrade entity to upgrade a customer to a given product family (for example, Azure plan) using the **ProductUpgradeRequest** resource.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with App+User credentials. Follow the [secure app model](enable-secure-app-model.md) when using App+User authentication with Partner Center APIs.

- A customer ID (`customer-tenant-id`). If you don't know the customer's ID, you can look it up in [Partner Center](https://partner.microsoft.com/dashboard) by selecting the **Customers** workspace, then the customer from the customer list, then **Account**. On the customer's Account page, look for the **Microsoft ID** in the **Customer Account Info** section. The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).

- The product family to which you want to upgrade the customer.

## C\#

To upgrade a customer to Azure plan:

1. Create a **ProductUpgradesRequest** object and specify the customer identifier and "Azure" as the product family.

2. Use the **IAggregatePartner.ProductUpgrades** collection.

3. Call the **Create** method and pass in the **ProductUpgradesRequest** object, which will return a **location header** string.

4. Extract the **upgrade-id** from the location header string that can be used to [query the upgrade status](get-product-upgrade-status.md).

```csharp
// IAggregatePartner partnerOperations;

string selectedCustomerId = "58e2af4f-0ad3-4688-8744-be2357cd939a";

string selectedProductFamily = "Azure";

var productUpgradeRequest = new ProductUpgradesRequest
{
    CustomerId = selectedCustomerId,
    ProductFamily = selectedProductFamily
};

var productUpgradeLocationHeader = partnerOperations.ProductUpgrades.Create(productUpgradeRequest);

var upgradeId = Regex.Split(productUpgradeLocationHeader, "/")[1];

```

## REST request

### Request syntax

| Method   | Request URI                                                                                   |
|----------|-----------------------------------------------------------------------------------------------|
| **POST** | [*{baseURL}*](partner-center-rest-urls.md)/v1/productupgrades HTTP/1.1 |

#### Request headers

For more information, see [Partner Center REST headers](headers.md).

#### Request body

The request body must contain a [ProductUpgradeRequest](product-upgrade-resources.md#productupgraderequest) resource.

#### Request example

```http
POST https://api.partnercenter.microsoft.com/v1/productupgrades HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: c245d5f2-1de3-4ae0-9e42-95e38e3cb8ff
MS-CorrelationId: e3f26e6a-044f-4371-ad52-0d91ce4200be
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 340
Expect: 100-continue
Connection: Keep-Alive
{
  "customerId": "4c721420-72ad-4708-a0a7-371a2f7b0969",
  "productFamily": "Azure"
}
```
> [!IMPORTANT]
> As of June 2023, the latest Partner Center .NET SDK release 3.4.0 is now archived. You can [download the SDK release from GitHub](https://github.com/microsoft/partner-center-sdk-for-dotNET), along with a [readme file](https://github.com/microsoft/partner-center-sdk-for-dotNET#readme) that contains useful information.
>
> Partners are encouraged to continue to use the [Partner Center REST APIs](partner-center-rest-api-reference.md).

## REST response

If successful, the response contains a **Location** header that has a URI that can be used to retrieve product upgrade status. Save this URI for use with other related REST APIs.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Partner Center REST error codes](error-codes.md).

### Response example

```http
HTTP/1.1 202 Accepted
Content-Length: 0
Location: productUpgrades/42d075a4-bfe7-43e7-af6d-7c68a57edcb4
MS-CorrelationId: 772871a9-399b-4f3b-b8c7-38f550e4f22a
MS-RequestId: cb82f7d6-f0d9-44d4-82f9-f6eee6e68390
MS-CV: iqOqN0FnaE2y0HcD.0
MS-ServerId: 030020525
Date: Thu, 28 Sep 2019 20:35:35 GMT
```
