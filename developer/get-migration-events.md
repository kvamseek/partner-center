---
title: Get migration events
description: How to get migration events for a subscription
ms.date: 09/22/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: migolova
ms.author: migolova
---

#  Get new commerce migration events

**Applies to**: Partner Center | Partner Center operated by 21Vianet |  Partner Center for Microsoft Cloud for US Government

How to get details of migration events based on current subscription ID or migration ID

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with both standalone App and App+User credentials.

This API can get migration events based on query strings that are selected by the partner. Selected query strings may be the following two options:

- A CustomerTenantId. If you don't know the customer's ID, you can look it up in [Partner Center](https://partner.microsoft.com/dashboard) by selecting the **Customers** workspace, then the customer from the customer list, then **Account**. On the customer's Account page, look for the **Microsoft ID** in the **Customer Account Info** section. The Microsoft ID is the same as the customer ID.

- A CurrentSubscriptionId (the legacy ID for a subscription that has been migrated)

- A MigrationId (the ID of the migration object associated with the current subscription)

## REST request

### Request syntax

| Method  | Request URI                                                                                                         |
|---------|---------------------------------------------------------------------------------------------------------------------|
| **GET** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/migrations/newcommerce/events HTTP/1.1 |


### Query Strings

This table lists the query strings that can be used to retrieve new commerce migration events. Please note, at least one of the two IDs are required to successfully retrieve the migration events associated with a current subscription. Inputting both migration ID and current subscription ID is accepted but not required.

| Name                            | Description                                                             |
|---------------------------------|-------------------------------------------------------------------------|
| MigrationId                     | A GUID-formatted string that identifies the migration objecy.           |
| CurrentSubscriptionId           | A GUID-formatted string that identifies a migrated legacy subscription. |

### Request headers

For more information, see [Partner Center REST headers](headers.md).

### Request body

None.

## REST response

If successful, this method returns event details of the current [Subscription](subscription-resources.md) that was migrated in the response body.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Partner Center REST error codes](error-codes.md).

### Request URL examples

```http
baseurl/v1/customers/948ebea1-0fe5-4e45-8f2e-900288b7883e/migrations/newcommerce/events?current_subscription_id=02DF825B-D0C9-40BE-8CB6-BAC895510D0A
```


### Response examples

```http
[
    {
        "id": "6eb07675-ba1d-45c2-9d05-c693a4863427",
        "newCommerceMigrationId": "e4c1c037-7c4c-42bd-bb41-dae2aa29ebcc",
        "currentSubscriptionId": "02df825b-d0c9-40be-8cb6-bac895510d0a",
        "customerTenantId": "948ebea1-0fe5-4e45-8f2e-900288b7883e",
        "createdTime": "2022-06-11T00:06:02.7529574Z",
        "eventName": "MigrationStarted"
    },
    {
        "id": "e828079b-c974-4822-977e-f12ac67380db",
        "newCommerceMigrationId": "e4c1c037-7c4c-42bd-bb41-dae2aa29ebcc",
        "currentSubscriptionId": "02df825b-d0c9-40be-8cb6-bac895510d0a",
        "customerTenantId": "948ebea1-0fe5-4e45-8f2e-900288b7883e",
        "createdTime": "2022-06-11T00:06:21.526778Z",
        "eventName": "NewCommerceSubscriptionCreated"
    },
    {
        "id": "7dbdcbd5-7a87-4d9b-bf1f-d9298493e631",
        "newCommerceMigrationId": "e4c1c037-7c4c-42bd-bb41-dae2aa29ebcc",
        "currentSubscriptionId": "02df825b-d0c9-40be-8cb6-bac895510d0a",
        "customerTenantId": "948ebea1-0fe5-4e45-8f2e-900288b7883e",
        "createdTime": "2022-06-11T00:08:08.5185085Z",
        "eventName": "NewCommerceSubscriptionProvisioned"
    },
    {
        "id": "71a3f753-55ca-461e-807d-f541685d5c8b",
        "newCommerceMigrationId": "e4c1c037-7c4c-42bd-bb41-dae2aa29ebcc",
        "currentSubscriptionId": "02df825b-d0c9-40be-8cb6-bac895510d0a",
        "customerTenantId": "948ebea1-0fe5-4e45-8f2e-900288b7883e",
        "createdTime": "2022-06-11T00:10:07.6947014Z",
        "eventName": "MigrationCompleted"
    }
]
```