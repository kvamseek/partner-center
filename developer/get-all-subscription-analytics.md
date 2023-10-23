---
title: Get all subscription analytics information
description: How to get all the subscription analytics information.
ms.date: 08/02/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: JulCsc
ms.author: rbars
---

# Get all subscription analytics information

**Applies to**: Partner Center | Partner Center operated by 21Vianet |  Partner Center for Microsoft Cloud for US Government

This article describes how to get all the subscription analytics information for your customers.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with User credentials only.

## REST request

### Request syntax

| Method | Request URI |
|--------|-------------|
| **GET** | [*\{baseURL\}*](partner-center-rest-urls.md)/partner/v1/analytics/subscriptions HTTP/1.1 |

#### URI parameters

The following table lists optional parameters and their descriptions:

| Parameter | Type |  Description |
|-----------|------|--------------|
| top | int | The number of rows of data to return in the request. If the value isn't specified, the maximum value and the default value are `10000`. If there are more rows in the query, the response body includes a next link that you can use to request the next page of data. |
| skip | int | The number of rows to skip in the query. Use this parameter to page through large data sets. For example, `top=10000` and `skip=0` retrieves the first 10,000 rows of data, `top=10000` and `skip=10000` retrieves the next 10,000 rows of data. |
| filter | string | One or more statements that filter the rows in the response. Each filter statement contains a field name from the response body and a value that are associated with the **`eq`**, **`ne`**, or for certain fields, the **`contains`** operator. Statements can be combined using **`and`** or **`or`**. String values must be surrounded by single quotes in the **filter** parameter. See the following section for a list of fields that can be filtered and the operators that are supported with those fields. |
| aggregationLevel | string | Specifies the time range for which to retrieve aggregate data. Can be one of the following strings: **day**, **week**, or **month**. If the value isn't specified, the default is **dateRange**. This parameter applies only when a date field is passed as part of the **groupBy** parameter. |
| groupBy | string | A statement that applies data aggregation only to the specified fields. |

### Request headers

For more information, see [Partner Center REST headers](headers.md).

### Request body

None.

### Request example

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/subscriptions
Authorization: Bearer <token>
Accept: application/json
Content-Type: application/json
Content-Length: 0
```

## REST response

If successful, the response body contains a collection of [**Subscription**](partner-center-analytics-resources.md#subscription-resource) resources.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and extra debugging information. Use a network trace tool to read this code, error type, and more parameters. For the full list, see [Error Codes](error-codes.md).

### Response example

```http
{
    "customerTenantId": "76906668-27FC-4F5B-A35C-75A9823E13AF",
    "customerName": "TESTORG65656565",
    "customerMarket": "US",
    "id": "4BF546B2-8998-4838-BEE2-5F1BBE65A04F",
    "status": "ACTIVE",
    "productName": "OFFICE 365 BUSINESS PREMIUM",
    "subscriptionType": "Office",
    "autoRenewEnabled": true,
    "partnerId": "3B33E682-00C3-41EE-9DD2-A548ADF56438",
    "friendlyName": "FULL OFFICE SUITE",
    "partnerName": "Partner Name",
    "providerName": "Provider Name",
    "creationDate": "2016-02-04T19:29:38.037",
   "effectiveStartDate": "2016-02-04T00:00:00",
    "commitmentEndDate": "2019-02-10T00:00:00",
    "currentStateEndDate": "2019-02-10T00:00:00",
    "trialToPaidConversionDate": null,
    "trialStartDate": null,
    "trialEndDate": null,
    "lastUsageDate": null,
    "deprovisionedDate": null,
    "lastRenewalDate": "2018-02-10T02:39:57.729",
    "licenseCount": 2,
    "churnRisk": "High",
    "billingCycleName": "MONTHLY"

}
```

## See also

- [Partner Center Analytics - Resources](partner-center-analytics-resources.md)
