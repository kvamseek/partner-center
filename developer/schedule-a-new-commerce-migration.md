---
title: Schedule a new commerce migration
description: Learn how to schedule a new commerce migration.
ms.date: 07/24/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: brentserbus
ms.author: brserbus
---

# Schedule a new commerce migration

**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud for US Government

**Appropriate roles**: Global admin | Admin agent | Sales agent

This article describes how to schedule a New Commerce Experience.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with both standalone App and App+User credentials.

- A customer ID (`customer-tenant-id`). If you don't know the customer's ID, you can look it up in [Partner Center](https://partner.microsoft.com/dashboard) by selecting the **Customers** workspace, then the customer from the customer list, then **Account**. On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section. The Microsoft ID is the same as the customer ID (`customer-tenant-id`).

- A current subscription ID

## REST request

### Request syntax

| **Method** | **Request URI**                                                                                                                                                     |
|------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **POST**   | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/migrations/newcommerce/schedules |

### URI parameter

This table lists the required query parameters to create a new commerce migration.

| **Name**           | **Type** | **Required** | **Description**                                       |
|--------------------|----------|--------------|-------------------------------------------------------|
| customer-tenant-id | string   | Yes          | A GUID-formatted string that identifies the customer. |

### Request headers

For more information, see [Partner Center REST headers](headers.md).

### Request body

This table describes the [subscription](subscription-resources.md) properties in the request body.

| **Property**          | **Type** | **Required**                                     | **Description**                                                                                                                                                                                                                                                                                                 |
|-----------------------|----------|--------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| currentSubscriptionId | string   | Yes                                              | A subscription identifier that indicates which subscription requires validation for migration.                                                                                                                                                                                                                  |
| termDuration          | string   | No                                               | Term duration can be specified to be changed upon migration.                                                                                                                                                                                                                                                    |
| billingCycle          | string   | No                                               | Billing cycle can be specified to be changed upon migration.                                                                                                                                                                                                                                                    |
| purchaseFullTerm      | bool     | No                                               | A new term can be started in NCE upon migration.                                                                                                                                                                                                                                                                |
| quantity              | int      | No                                               | License quantity for a subscription can be increased or decreased upon migration.                                                                                                                                                                                                                               |
| customTermEndDate     | datetime | No                                               | An end-date can be set to align with an existing non-trial OnlineServicesNCE subscription or calendar month. There is more information on aligning subscription end dates here: [Align subscription end dates in Partner Center](../align-subscription-end-dates.md) |
| targetDate            | datetime | Required (if the migrateOnRenewal is null/false) | Target Date when to schedule the migration. If targetDate is set for specified date, the migrationOnRenewal can be set to null or false.                                                                                                                                                                        |
| migrateOnRenewal      | bool     | Required (if the targetDate is null)             | If the flag is set true for migrateOnRenewal, there is no need to specify the targetDate for scheduling a migration.                                                                                                                                                                                            |
| addOnMigrationSchedules      | bool     | No     | Includes a list of AddOn subscriptions to be included in the scheduled migration.                                                                                                                                                                                            |

### Request example

```json
{
    "currentSubscriptionId": "2591295E-DDEB-425A-93F9-C1B4F5AD7FB6",
    "quantity": 1,
    "billingCycle": "monthly",
    "purchaseFullTerm": false,
    "termDuration": "P1Y",
    "customTermEndDate": null,
    "targetDate": "2023-08-09T00:00:00.000Z",
    "addOnMigrations": [
        {
            "currentSubscriptionId": "5B882C48-53C6-46AF-B8A4-0691F19BAD94",
            "quantity": 17,
            "billingCycle": "Monthly",
            "purchaseFullTerm": false,
            "termDuration": "P1M",
            "customTermEndDate": null
        },
        {
            "currentSubscriptionId": "C7D0DB12-9482-4297-8F09-190EB04F9C05",
            "quantity": 23,
            "billingCycle": "Monthly",
            "purchaseFullTerm": false,
            "termDuration": "P1Y",
            "customTermEndDate": null
        }
    ]
}
```

### REST response

If successful, this method returns details of the [subscriptions](subscription-resources.md) being migrated (migration object) in the response body.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Partner Center REST error codes](error-codes.md).

### Response examples

```json
{
    "id": "f016c025-a873-47af-8b52-2516fbef4c65",
    "currentSubscriptionId": "2591295E-DDEB-425A-93F9-C1B4F5AD7FB6",
    "quantity": 1,
    "billingCycle": "monthly",
    "purchaseFullTerm": false,
    "termDuration": "P1Y",
    "customTermEndDate": null,
    "targetDate": "2023-08-09T00:00:00.000Z",
    "addOnMigrations": [
        {
            "currentSubscriptionId": "5B882C48-53C6-46AF-B8A4-0691F19BAD94",
            "quantity": 17,
            "billingCycle": "Monthly",
            "purchaseFullTerm": false,
            "termDuration": "P1M",
            "customTermEndDate": null
        },
        {
            "currentSubscriptionId": "C7D0DB12-9482-4297-8F09-190EB04F9C05",
            "quantity": 23,
            "billingCycle": "Monthly",
            "purchaseFullTerm": false,
            "termDuration": "P1Y",
            "customTermEndDate": null
        }
    ]
}
```

## See also

- [Update a new commerce migration schedule](update-a-new-commerce-migration-schedule.md)
- [Cancel a new commerce migration schedule](cancel-a-new-commerce-migration-schedule.md)
- [Get a new commerce migration schedule](get-a-new-commerce-migration-schedule.md)
