---
title: Get a new commerce subscription migration
description: How to get a new commerce subscription migration
ms.date: 11/8/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: brentserbus
ms.author: brserbus
---

#  Get a new commerce subscription migration

**Applies to**: Partner Center | Partner Center operated by 21Vianet |  Partner Center for Microsoft Cloud for US Government

How to get a migration of a subscription to New Commerce Experience in order to check migration status

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with both standalone App and App+User credentials.

- A customer ID (`customer-tenant-id`). If you don't know the customer's ID, you can look it up in [Partner Center](https://partner.microsoft.com/dashboard) by selecting the **Customers** workspace, then the customer from the customer list, then **Account**. On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section. The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).

- A current subscription ID

## REST request

### Request syntax

| Method  | Request URI                                                                                                                           |
|---------|---------------------------------------------------------------------------------------------------------------------------------------|
| **GET** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/migrations/newcommerce/{migration-id} HTTP/1.1           |

### URI parameter

This table lists the required query parameters to create a new commerce migration.

| Name               | Type   | Required | Description                                           |
|--------------------|--------|----------|-------------------------------------------------------|
| customer-tenant-id | string | Yes      | A GUID-formatted string that identifies the customer. |
| migration-id       | string | Yes      | A GUID-formatted string that identifies the customer. |

### Request headers

For more information, see [Partner Center REST headers](headers.md).

### Request body

None.

## REST response

If successful, this method returns details of the [Subscriptions](subscription-resources.md) being migrated (migration object) in the response body.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Partner Center REST error codes](error-codes.md).

### Response examples

```http
{
    "id": "f46fbd87-b204-40e5-b891-d0879ca3bf62",
    "startedTime": "2021-10-13T16:30:32.1446219Z",
    "completedTime": "2021-10-13T16:35:40.3844713Z",
    "currentSubscriptionId": "5C77DC7F-BE2C-4306-A3B5-0EBB4365D7FC",
    "status": "Completed",
    "customerTenantId": "75c5e79e-7e9f-429f-b772-ed3d38768f7c",
    "catalogItemId": "CFQ7TTC0LF8Q:0001:CFQ7TTC0KJ4N",
    "newCommerceSubscriptionId": "8adde5ce-52e3-47b5-c49c-df9c210bd5df",
    "newCommerceOrderId": "8672a13e9197",
    "subscriptionEndDate": "2022-10-13T00:00:00Z",
    "quantity": 1,
    "termDuration": "P1Y",
    "billingCycle": "Monthly",
    "purchaseFullTerm": false
}
```
