---
title: Get a price sheet
description: Obtain a price sheet for a given market and view. Supports filters to get history by month.
ms.date: 08/07/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: denysseD
ms.author: denyssediaz
---

# Get a price sheet

This article explains how to get a price sheet for a given market and view. This method supports filters to get history by month.

## Prerequisites

- Credentials as described in [Partner API authentication](partner-center-authentication.md). This scenario only supports application user authentication. Application-only isn't yet supported. Partners that experience **http error:400** should consult the [Partner API authentication](partner-center-authentication.md) documentation.
- This API currently supports only user access where partners must be in one of the following roles: Global Admin, Admin Agent or Sales Agent.

## Details

- Current returns data only for Azure plan consumption and reservations, Licensed based (new commerce experience), and Marketplace products.
- Current pricing includes all meters and products available during the current month to the date the API is called. Previous months include all meters and products available for the given month.
- Consumption meter prices are only in USD, partners are to use the foreign exchange rates API to calculate local currency costs.
- Consumption meter prices are estimated retail prices. Partner discounts are available via [partner earned credit](../partner-earned-credit-explanation.md).
- Reservations meter prices include the CSP partner discounts. Estimated retail prices for reservations can be found in the reservations shared services downloadable from the Partner Center "Pricing and offers" page.
- More information about Azure plan pricing can be found in the [Azure plan pricing documentation](../azure-plan-price-list.md).
- Partner pricing and foreign exchange rate APIs aren't part of the [Partner Center SDK](get-started.md).
- This method returns the price list as a file stream. File stream is either a .csv file or a zip compressed version of the .csv. Details about how to request compressed files are included below.

## REST request

### Request syntax

| Method   | Request URI                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| **GET** | `https://api.partner.microsoft.com/v1.0/sales/pricesheets(Market='{market}',PricesheetView='{view}')/$value`                                     |

### URI required parameters

Use the following path parameters to request the market and type of price sheet you want.

| Name                   | Type     | Required | Description                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
|Market                      | string   | Yes       | Two letter country code for the market being requested       |
|PricesheetView| string   | Yes       | The type of price sheet being requested, which can be azure_consumption, azure_reservations,  updatedlicensebased, marketplace, or software.

> [!NOTE]
> updatedlicensebased PriceSheetView is currently available only to partners who are part of the M365/D365 new commerce experience technical preview.

> [!NOTE]
> The software price list will be available via API starting April 1, 2022.

### URI filter parameters

Use the following filter parameters.

| Name                   | Type     | Required | Description                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
|Timeline| string   | No| Defaults to current if not passed. Possible values are history, current and future.       |
|Month| string   | No| Only required if history is requested, must adhere to YYYYMM for the price sheet being requested.       |

> [!NOTE]
> Future pricing is not supported for Marketplace. From April 1, 2022, partners will be able to view software price list history via API, starting with March 2022 history.

### Request headers

- For more information, see [Partner REST headers](headers.md).

In addition to the above headers, pricing files can be retrieved as compressed reducing bandwidth and download times. By default the files aren't compressed. To get compressed versions of the files, you can include the below header value. Realize that compressed sheets are only available from April 2020 onward, all sheets prior to April 2020 are only available as not compressed.

| Header                   | Value Type     | Value | Description                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
|Accept-Encoding| string   | deflate| Optional. If omitted file stream isn't compressed.       |

### Request example

```http
GET https://api.partner.microsoft.com/v1.0/sales/pricesheets(Market='ad',PricesheetView='azure_consumption')/$value?timeline=history&month=201909 HTTP/1.1
Authorization: Bearer
Host: api.partner.microsoft.com
```

### Request example for new commerce

> [!NOTE]
> updatedlicensebased PriceSheetView is currently available only to partners who are part of the M365/D365 new commerce experience technical preview.

```http
GET https://api.partner.microsoft.com/v1.0/sales/pricesheets(Market='US',PricesheetView='updatedlicensebased')/$value?timeline=history&month=202101 HTTP/1.1
Authorization: Bearer
Accept-Encoding: deflate
Host: api.partner.microsoft.com

```

## REST response

If successful, this method returns the price list as a file stream. File stream is either a .csv file or a zip compressed version of the .csv.

### Response example for new commerce

> [!NOTE]
> updatedlicensebased PriceSheetView is currently available only to partners who are part of the M365/D365 new commerce experience technical preview.

``` http
HTTP/1.1 200 OK
Cache-Control: private
Content-Length: 42180180
Content-Type: application/octet-stream
Content-Disposition: attachment; filename=sheets.csv
Request-ID: 9f8bed52-e4df-4d0c-9ca6-929a187b0731
Date: Wed, 02 Feb 2021 03:41:20 GMT

"ProductTitle","ProductId","SkuId","SkuTitle","Publisher","SkuDescription","UnitOfMeasure","TermDuration","BillingPlan","Market","Currency","UnitPrice","PricingTierRangeMin","PricingTierRangeMax","EffectiveStartDate","EffectiveEndDate","Tags","ERP Price“
"Advanced Communications","CFQ7TTC0HDK0","0001","Advanced Communications","Microsoft Corporation","Advanced meetings, calling, workflow integration, and management tools for IT.","","P1Y","Annual","US","USD","115.2","","","2/1/2019 12:00:00 AM","2/4/2021 8:35:31 PM","License","144"
======= Truncated ==============

```

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and other debugging information. Use a network trace tool to read this code, error type, and other parameters. For the full list, see [Error Codes](error-codes.md).

If there are no changes expected for the new commerce licensed-based future price list, there will be no future price list returned. When passing future into the Timeline requested for the updatedlicensebased PriceSheetView, partners will see the following API response code:  404 Not Found.

## Next steps

- [Get an offer matrix](get-an-offer-matrix.md)