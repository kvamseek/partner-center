---
title: Create a new commerce migration
description: How to create a new commerce migration
ms.date: 10/13/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: brentserbus
ms.author: brserbus
---

# Create a new commerce migration

**Applies to**: Partner Center | Partner Center operated by 21Vianet |  Partner Center for Microsoft Cloud for US Government

How to create a migration of a subscription to New Commerce Experience

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with both standalone App and App+User credentials.

- A customer ID (`customer-tenant-id`). If you don't know the customer's ID, you can look it up in [Partner Center](https://partner.microsoft.com/dashboard) by selecting the **Customers** workspace, then the customer from the customer list, then **Account**. On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section. The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).

- A current subscription ID

## Rate limit

The Create Migration API limit is 100 calls by a partner in 5 minutes. More information about rate limits and throttling is available at [API throttling guidance](api-throttling-guidance.md).

## REST request

### Request syntax

| Method  | Request URI                                                                                                            |
|---------|------------------------------------------------------------------------------------------------------------------------|
|**POST** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/migrations/newcommerce HTTP/1.1           |

### URI parameter

This table lists the required query parameters to create a new commerce migration.

| Name               | Type   | Required | Description                                           |
|--------------------|--------|----------|-------------------------------------------------------|
| customer-tenant-id | string | Yes      | A GUID-formatted string that identifies the customer. |

### Request headers

For more information, see [Partner Center REST headers](headers.md).

### Request body

This table describes the [Subscription](subscription-resources.md) properties in the request body.

| Property              | Type             | Required        | Description |
|-----------------------|------------------|-----------------|-----------------------------------------------------------------------------------------------------------|
| currentSubscriptionId | string           | Yes             | A subscription identifier that indicates which subscription requires validation for migration.            |
| termDuration          | string           | No              | Term duration can be changed upon migration.                                              |
| billingCycle          | string           | No              | Billing cycle can be changed upon migration.                                              |
| purchaseFullTerm      | bool             | No              | A new term can be started in NCE upon migration.                                                          |
| quantity              | int              | No              | License quantity for a subscription can be increased or decreased upon migration.                         |
| customTermEndDate     | datetime         | No              | An end-date can be set to align with an existing nontrial OnlineServicesNCE subscription or calendar month. There's more information on aligning subscription end dates here: [Align subscription end dates in Partner Center](../align-subscription-end-dates.md) |

### Request example

Note, Nested add-ons (add-on subscriptions with add-on subscriptions) should be written in the request body as a flat list within addOnMigrations and not be nested inside other add-on subscriptions in the request; see the last request example for how add-ons can be written in the request body.

```http
{
    "currentSubscriptionId" : "9beb6319-6889-4d28-a155-68ca9c783842"
}
```

```http
{ 
    "currentSubscriptionId": "5C77DC7F-BE2C-4306-A3B5-0EBB4365D7FC", 
    "termDuration": "P1M", 
    "billingCycle": "Monthly", 
} 
```

```http
{
    "currentSubscriptionId": "5C77DC7F-BE2C-4306-A3B5-0EBB4365D7FC", 
    "purchaseFullTerm": true 
}
```

```http
{
    "currentSubscriptionId": "66E738D6-E0BC-4FFB-8818-BDE99BC7008B",
    "quantity": 1,
    "billingCycle": "Annual",
    "purchaseFullTerm": false,
    "termDuration": "P1Y",
    "addOnMigrations": [
        {
            "currentSubscriptionId": "359011DC-B5B0-4660-850B-A8FA9B2E3309",
            "quantity": 1,
            "billingCycle": "Monthly",
            "purchaseFullTerm": false,
            "termDuration": "P1M"
        },
        {
            "currentSubscriptionId": "159D9F87-CE39-4EBD-B9C2-ECF0892A85A1",
            "quantity": 1,
            "billingCycle": "Monthly",
            "purchaseFullTerm": false,
            "termDuration": "P1Y"
        }
    ]
}
```

## REST response

If successful, this method returns details of the [Subscriptions](subscription-resources.md) being migrated (migration object) in the response body.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and extra debugging information. Use a network trace tool to read this code, error type, other parameters. For the full list, see [Partner Center REST error codes](error-codes.md).

### Response examples

```http
{
    "addOnMigrations": [
        {
            "currentSubscriptionId": "E3AFD30D-D6E7-45AF-A6C5-FB905992AE00",
            "customerTenantId": "75c5e79e-7e9f-429f-b772-ed3d38768f7c",
            "catalogItemId": "CFQ7TTC0LH0T:0001:CFQ7TTC0K4KQ",
            "subscriptionEndDate": "2023-02-22T00:00:00Z",
            "quantity": 1,
            "termDuration": "P1Y",
            "billingCycle": "Monthly",
            "purchaseFullTerm": false
        },
        {
            "currentSubscriptionId": "80906BD9-E45C-4D1B-92A8-EA3F3FB6E105",
            "customerTenantId": "75c5e79e-7e9f-429f-b772-ed3d38768f7c",
            "catalogItemId": "CFQ7TTC0LH0R:0001:CFQ7TTC0K0SK",
            "subscriptionEndDate": "2023-02-22T00:00:00Z",
            "quantity": 1,
            "termDuration": "P1Y",
            "billingCycle": "Monthly",
            "purchaseFullTerm": false
        },
        {
            "currentSubscriptionId": "72E424F4-10FF-4C76-B101-C274F73BA498",
            "customerTenantId": "75c5e79e-7e9f-429f-b772-ed3d38768f7c",
            "catalogItemId": "CFQ7TTC0LHXJ:0001:CFQ7TTC0KHTR",
            "subscriptionEndDate": "2023-02-22T00:00:00Z",
            "quantity": 1,
            "termDuration": "P1Y",
            "billingCycle": "Monthly",
            "purchaseFullTerm": false
        }
    ],
    "id": "7123c075-fc05-42d6-a21e-1d2036fa490b",
    "startedTime": "2022-02-23T13:00:48.4489832Z",
    "currentSubscriptionId": "2E56C7F5-E120-4CA4-BFF3-7DA763B4D777",
    "status": "Processing",
    "customerTenantId": "75c5e79e-7e9f-429f-b772-ed3d38768f7c",
    "catalogItemId": "CFQ7TTC0LF8Q:0001:CFQ7TTC0KQDF",
    "subscriptionEndDate": "2023-02-22T00:00:00Z",
    "quantity": 1,
    "termDuration": "P1Y",
    "billingCycle": "Monthly",
    "purchaseFullTerm": false
}
```
