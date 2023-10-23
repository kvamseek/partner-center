---
title: Get a list of margins in comma delimited format for a given partner.
description: Get a list of margins in comma delimited format for a given partner.
ms.date: 10/03/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: migolova
ms.author: migolova
---

# Download margins

**Applies to**: Partner Center

**Appropriate roles**: Global admin | Admin agent

Partners can get a list of active margins for a given partner. This method returns margins based on the partner and available start and end dates. **Download margins** returns the data in a comma delimited format.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with both standalone App and App+User credentials.

## REST request

[GET] /v1/margins/download

### Request syntax

| Method   | Request URI                                                                                                                         |
|----------|-------------------------------------------------------------------------------------------------------------------------------------|
| **GET**  | [*{baseURL}*](partner-center-rest-urls.md)/v1/margins/download?country={countrycode} HTTP/1.1 |

For a list of country codes, see [Co-sell country, region, state, and province codes](../commercial-marketplace-co-sell-location-codes.md#country-and-region-codes).

### URI parameter

This table lists the required query parameters.

| Name    | Type   | Required | Description |
|---------|--------|----------|-------------|
| country | String | Y        | The value is a string that denotes the country code. |

### Request headers

For more information, see [Partner Center REST headers](headers.md).

### Request body

None

### Request example

```http
GET https://api.partnercenter.microsoft.com/v1/margins/download?country=US HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
X-Locale: en-US
```

## REST response

If successful, this method returns the price list as a file stream as a.csv file

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and more debugging information. Use a network trace tool to read this code, error type, and more parameters. For the full list, see [Error Codes](error-codes.md).

### Response example

```http
HTTP/1.1 200 OK
Content-Length: 138
Content-Type: application/json
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
Date: Fri, 26 Feb 2021 20:42:26 GMT

"b82103f870af_e71f19b1-27cf-43d3-be46-3d87a9d908a2","US","Percentage","Test PMC 2 PC","DZH318Z0FTST","HelloWorld3","0002","plan1","Dynamics 365","3b274863-227e-4b2c-a463-330b949e2e34","3pptesting","8.0","","","","","","","","","8/14/2023 6:09:28 PM","10/31/2023 11:59:59 PM","live","8/14/2023 6:09:28 PM" 
```
