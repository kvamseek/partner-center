---
title: Get a new commerce migration schedule
description: Learn how to get a new commerce migration schedule.
ms.date: 10/27/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: brentserbus
ms.author: brserbus
---

# Get a new commerce migration schedule

**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud for US Government

This article describes how to get a new commerce migration schedule.

> [!IMPORTANT]
> This API is currently only available in the Sandbox tenant.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with both standalone App and App+User credentials.

- A customer ID (`customer-tenant-id`). If you don't know the customer's ID, you can look it up in [Partner Center](https://partner.microsoft.com/dashboard) by selecting the **Customers** workspace, then the customer from the customer list, then **Account**. On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section. The Microsoft ID is the same as the customer ID (`customer-tenant-id`).

- A current subscription ID

## REST request

There are two different ways partners can query.

- To Query a particular schedule
- Get the list of schedules for a given criteria

### Request syntax

| **Method** | **Request URI**                                                                                                                                                                     |
|------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **GET**    | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/migrations/newcommerce/schedules/{scheduleID}    |

### URI parameter

This table lists the required query parameters to create a new commerce migration.

| **Name**           | **Type** | **Required** | **Description**                                       |
|--------------------|----------|--------------|-------------------------------------------------------|
| customer-tenant-id | string   | Yes          | A GUID-formatted string that identifies the customer. |

| **Method** | **Request URI**                                                                                                                                                             |
|------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **GET**    | [*{baseURL}*](partner-center-rest-urls.md)/v1/migrations/newcommerce/schedules?CustomerTenantId={customer-tenant-id}  |

### URI parameter

This table lists the required query parameters to create a new commerce migration. Anyone of the query parameter can be used.

| **Name**              | **Type** | **Description**                                                      |
|-----------------------|----------|----------------------------------------------------------------------|
| customerTenantId      | string   | A GUID-formatted string that identifies the customer.                |
| currentSubscriptionID | string   | A GUID-formatted string that identifies the current Subscription ID  |
| externalReferenceID   | string   | A GUID-formatted string that identifies the migration batch          |

### Request headers

For more information, see [Partner Center REST headers](headers.md).

### Response body

This table describes the [subscription](subscription-resources.md) properties in the response.

| **Property**          | **Type** | **Required** | **Description**                                                                                                                                                                                                                                                                                                 |
|-----------------------|----------|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| currentSubscriptionId | string   | Yes          | A subscription identifier that indicates which subscription requires validation for migration.                                                                                                                                                                                                                  |
| termDuration          | string   | No           | Term duration can be specified to be changed upon migration.                                                                                                                                                                                                                                                    |
| billingCycle          | string   | No           | Billing cycle can be specified to be changed upon migration.                                                                                                                                                                                                                                                    |
| purchaseFullTerm      | bool     | No           | A new term can be started in NCE upon migration.                                                                                                                                                                                                                                                                |
| quantity              | int      | No           | License quantity for a subscription can be increased or decreased upon migration.                                                                                                                                                                                                                               |
| customTermEndDate     | datetime | No           | An end-date can be set to align with an existing non-trial OnlineServicesNCE subscription or calendar month. There is more information on aligning subscription end dates here: [Align subscription end dates in Partner Center](../align-subscription-end-dates.md) |
| targetDate            | datetime | No           | Target Date when to schedule the migration.                                                                                                                                                                                                                                                                     |
| migrateOnRenewal      | bool     | No           | Indicates if the schedule needs to happen on renewal                                                                                                                                                                                                                                                              |
| status                | string   | No           | Status of the schedule migration                                                                                                                                                                                                                                                                                |
| createdTime           | datetime | No           | When the schedule was created                                                                                                                                                                                                                                                                                   |
| lastModifiedTime      | datetime | No           | When the schedule was last modified                                                                                                                                                                                                                                                                             |

### REST response

If successful, this method returns details of the [subscriptions](subscription-resources.md) being migrated (migration object) in the response body.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Partner Center REST error codes](error-codes.md).

### Response examples

```json
[
{
"id": "f016c025-a873-47af-8b52-2516fbef4c65",
"currentSubscriptionId": "c6105a9c-36cb-4f88-92ea-9573040725c4",
"subscriptionEndDate": "2023-07-19T00:00:00Z",
"status": "Created",
"customerTenantId": "6f297517-16e6-4313-8c6d-4e10496d2871",
"quantity": 25,
"termDuration": "P1Y",
"billingCycle": "Monthly",
"purchaseFullTerm": false,
"targetDate": "2022-10-30T00:00:00",
"createdTime": "2022-10-18T21:20:50.9668605+00:00",
"lastModifiedTime": "2022-10-18T21:29:32.8992819+00:00"
}
]
```

## See also

- [Schedule a new commerce migration](schedule-a-new-commerce-migration.md)
- [Update a new commerce migration schedule](update-a-new-commerce-migration-schedule.md)
- [Cancel a new commerce migration schedule](cancel-a-new-commerce-migration-schedule.md)