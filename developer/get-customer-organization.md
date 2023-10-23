---
title: Get a customer organization
description: Gets a customer's organization details.
ms.date: 7/31/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: jischulz
ms.author: jischulz
---

# Get a customer organization

**Applies to**: Partner Center 

Gets a **Customer Organization** resource.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports app+user credentials or app-only authentication.

- A customer ID (`customer-tenant-id`). If you don't know the customer's ID, you can look it up in [Partner Center](https://partner.microsoft.com/dashboard). Select the **Customers** workspace from the Partner Center Home page. Select the customer from the **Customer list**, then select **Account**. On the customer's Account page, look for the Microsoft ID in the **Customer Account details section**. The Microsoft ID is the same as the customer ID (`customer-tenant-id`).

> [!IMPORTANT]
> GDAP Roles are required to call this API. DAP is not supported.
> Partner Authentication is still required (AdminAgent/HelpDeskAgent/SalesAgent)

## GDAP roles

You'll need at least one of the following GDAP roles:

- Global Administrator
- Directory Writer
- Global Reader

## REST request

### Request syntax

| Method  | Request URI                                                                            |
|---------|----------------------------------------------------------------------------------------|
| **GET** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/organization HTTP/1.1 |

### URI parameter

Use the following query parameter to a specific customer.

| Name                   | Type     | Required | Description                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| **customer-tenant-id** | **guid** | Y        | The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller. |

### Request headers

For more information, see [Partner Center REST headers](headers.md).

### Request body

None.

### Request example

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/organization HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-CorrelationId: a176c585-b5de-4d65-824c-67a6deb45cd9
MS-RequestId: 74ca1db9-df92-41c6-a362-a16433b0542b
```

## REST response

If successful, this method returns a [Customer](customer-resources.md#customer) resource in the response body.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Error Codes](error-codes.md).

### Response example

```http
HTTP/1.1 200 OK
Content-Length: 1530
Content-Type: application/json; charset=utf-8
MS-CorrelationId: a176c585-b5de-4d65-824c-67a6deb45cd9
MS-RequestId: 74ca1db9-df92-41c6-a362-a16433b0542b

[
  {
    "street": "1 Microsoft Way",
    "countryLetterCode": "US",
    "postalCode": "98052-8300",
    "city": "Redmond",
    "state": "WA",
    "displayName": "Contoso",
    "technicalNotificationMails": [
      "test@contoso.com"
    ]
  }
]
```

## Next steps

- [Get a customer's custom domain](./get-customer-custom-domain.md)

