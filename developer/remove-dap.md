---
title: Remove a DAP relationship with a customer
description: How to remove a delegated admin relationship with a customer.
ms.date: 3/24/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: Vamseek
ms.author: vijvala
---

# Remove a delegated admin relationship with a customer

Remove a delegated admin (DAP) relationship with a customer that you no longer need to manage.

## Prerequisites

- Credentials as described in [Partner Center authentication](./partner-center-authentication.md). This scenario supports authentication with App+User credentials only.
- A customer ID (`customer-tenant-id`). If you don't know the customer's ID, you can look it up in [Partner Center](https://partner.microsoft.com/dashboard). Select the **Customers** tile, then select the customer from the customer list, then select **Account**. On the customer's Account page, look for the **Microsoft ID** in the **Customer Account Info** section. The Microsoft ID is the same as the customer ID (customer-tenant-id).
- All Azure Reserved VM Instance orders must be canceled before a reseller relationship is removed. Call Azure support for canceling any open Azure Reserved VM Instance orders.

## REST request

### Request syntax

| **Method** | **Request URI**                                                                                                                             |
|------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| **PATCH**  | [*{baseURL}*](./partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/ HTTP/1.1 |

### URI parameter

This table lists the required query parameters to remove a reseller relationship.

| **Name**               | **Type** | **Required** | **Description**                                                                    |
|------------------------|----------|--------------|------------------------------------------------------------------------------------|
| customer-tenant-id     | guid     | Y            | The value is a GUID formatted **customer-tenant-id** that identifies the customer. |

### Request headers

For more information, see [Partner Center REST headers](./headers.md).

### Request body

A **Customer** resource is required in the request body. Ensure the AllowDelegatedAccess property has been set to false. 

### Request example

```html
HTTPCopy
PATCH https://api.partnercenter.microsoft.com/v1/customers/\<customer-tenant-id\> HTTP/1.1
Authorization: Bearer \<token\>
Content-Length: 74
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 9b4bf2ca-f374-4d51-9113-781ca87b8380
MS-RequestId: 9fef8b23-6e3e-45d2-8678-e9fe89c35af5
Date: Fri, 12 Jan 2018 00:31:55 GMT
{
"AllowDelegatedAccess":false,
"attributes":{
"objectType":"Customer"
}
}
```

## REST response

If successful, this method removes a DAP relationship for the specified customer.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and other debugging information. Use a network trace tool to read this code, error type, and other parameters. For the full list, see [Partner Center REST error codes](./error-codes.md).

### Response example

```html
HTTPCopy
HTTP/1.1 200 OK
MS-RequestId: 7988dde4-b516-472c-b226-6d53fb18f04e
MS-CorrelationId: 9b4bf2ca-f374-4d51-9113-781ca87b8380
X-Locale: en-US
Content-Type: application/json
Content-Length: 242
Expect: 100-continue
}
```
