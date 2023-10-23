---
title: Delete Indirect Reseller in Sandbox
description: Learn how to delete Indirect Resellers in your Sandbox and enable end-to-end testing using Partner Center APIs.
ms.date: 6/15/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: JulCsc
ms.author: raormeni
ms.custom: kr2b-contr-experiment
---

# Delete Indirect Reseller in Sandbox

**Applies to**: Partner Center | Partner Center operated by 21Vianet

This article shows you how to delete Sandbox Indirect Providers and enable end-to-end testing using APIs.

> [!IMPORTANT]
> This document describes features that are only allowed in the Sandbox environment for Indirect Model experiences.

## Prerequisites

You must have the credentials as described in [Partner Center Authentication](partner-center-authentication.md). This scenario supports authentication with App+User credentials.

## Delete Sandbox Indirect Reseller

This feature is only available in the Sandbox and gives Sandbox Indirect Providers an ability to create Sandbox Indirect Resellers.

Before you can delete a Sandbox Indirect Reseller:

- Suspend the subscriptions for each customer of the Sandbox Indirect Reseller.
- Delete all customers of the Indirect Reseller.

There's a limit of five Sandbox Indirect Resellers allowed per Sandbox Indirect Provider. Once the Sandbox Indirect Reseller is deleted, the quota is reset.

## Delete Sandbox Indirect Reseller through API

### REST request

This syntax is the REST request syntax:

| Method     | Request URI                                                                         |
|------------|-------------------------------------------------------------------------------------|
| **DELETE** | [*{baseURL}*](partner-center-rest-urls.md)/v1//sandboxIndirectReseller/{resellerId} |

Using the request headers, keep the following facts in mind:

- This API is idempotent. It doesn't yield a different result if you call it multiple times.
- A request ID and correlation ID are required.

For more information, see [Partner Center REST headers](headers.md).

### Request example

`DELETE https://api.partnercenter.microsoft.com/v1/sandboxIndirectReseller/{resellerID}`

```http
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

### Response example

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5
Date: Wed, 16 Feb 2021 00:43:02 GMT
```

#### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and other debugging information. Use a network trace tool to read this code, error type, and other parameters. For the full list, see [Partner Center error codes](error-codes.md).

This method returns the following status success and error codes:

| HTTP Status Code | Error code | Description                                            |
|------------------|------------|--------------------------------------------------------|
| 401              | 6002       | Unauthorized token or Not a Tip Provider Account       |
| 403              | 6003       | Delete Sandbox Indirect Reseller isn't allowed         |
| 403              | 6004       | Create Sandbox Indirect Reseller operation not allowed |
| 409              | 1003       | Conflict while creating tenant                         |

## Next steps

Review how to [create Indirect Resellers in your Sandbox](create-indirect-reseller-in-sandbox.md).
