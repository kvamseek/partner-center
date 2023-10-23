---
title: Get an offer matrix
description: Obtain an offer matrix for a given date. Supports filters to get history by month.
ms.date: 08/07/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: denysseD
ms.author: denyssediaz
---

# Get an offer matrix

This article explains how to get an offer matrix for a given month. The offer matrix includes properties and purchase rules for the products and skus. This method supports filters to get history by month.

## Prerequisites

- Credentials as described in [Partner API authentication](partner-center-authentication.md). This scenario only supports application user authentication. Application-only is not yet supported. Partners that experience **http error:400** should consult the [Partner API authentication](partner-center-authentication.md) documentation.
- This API currently supports only user access where partners must be in one of the following roles: Global Admin, Admin Agent or Sales Agent.

## Details

- Current returns data only for updated new commerce license-based products.
- Current pricing includes products available during the current month to the date the API is called. Previous months include date as of the last day of the selected month.
- This method returns data as a file stream. File stream is either a .csv file or a zip compressed version of the .csv. Details about how to request compressed files are included below.

## REST request

### Request syntax

| Method   | Request URI                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| **GET** | `https://api.partner.microsoft.com/v1.0/sales/offermatrix(Month='{date}')/$value` |

### URI filter parameters

Use the following filter parameters.

| Name                   | Type     | Required | Description                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
|Month| string   | No | Must adhere to YYYYMM for the price sheet being requested. |

### Request headers

- See [Partner REST headers](headers.md) for more information.

In addition to the above headers, pricing files can be retrieved as compressed reducing bandwidth and download times. By default the files are not compressed. To get compressed versions of the files you can include the below header value. Realize that compressed sheets are only available from April 2020 onward, all sheets prior to April 2020 are only available as not compressed.

| Header                   | Value Type     | Value | Description                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
|Accept-Encoding| string   | deflate| Optional. If omitted file stream is not compressed.       |

### Request example

```http
GET https://api.partner.microsoft.com/v1.0/sales/offermatrix(Month='202101')/$value HTTP/1.1
Authorization: Bearer
Accept-Encoding: deflate
Host: api.partner.microsoft.com

```

## REST response

If successful, this method returns an offer matrix as a file stream. File stream is either a .csv file or a zip compressed version of the .csv.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Error Codes](error-codes.md).

### Response example

``` http
HTTP/1.1 200 OK
Cache-Control: private
Content-Length: 42180180
Content-Type: application/octet-stream
Content-Disposition: attachment; filename=updatedoffice.csv
Request-ID: 9f8bed52-e4df-4d0c-9ca6-929a187b0731
Date: Wed, 02 Feb 2021 03:41:20 GMT

"ProductTitle","ProductId","SkuId","SkuTitle","ProvisioningId","ProvisioningString","MinLicenses","MaxLicenses","AssetOwnershipLimit","AssetOwnershipLimitType","ProductSkuPreRequisites","ProductSkuConversion","Description","AllowedCountries" 
"Microsoft 365 Business Basic","CFQ7TTC0LH18","0001","Microsoft 365 Business Basic","3b555118-da6a-4418-894f-7df1e2096870","O365_BUSINESS_ESSENTIALS","1","300","2","ConcurrentCount","","CFQ7TTC0LDPB/0001,CFQ7TTC0LF8Q/0001","Best for businesses that need professional...","AD;AE;AF;AG;AI;AL;AM;AO..."
======= Truncated ==============
```

## Next steps

- [Get a price sheet](get-a-price-sheet.md)
