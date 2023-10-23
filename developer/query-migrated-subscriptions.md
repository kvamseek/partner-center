---
title: Query migrated subscriptions
description: How to get migrated subscriptions and respective migration ids
ms.date: 07/31/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: brentserbus
ms.author: brserbus
---

# Query new commerce migrations

**Applies to**: Partner Center | Partner Center operated by 21Vianet |  Partner Center for Microsoft Cloud for US Government

How to query for migrated subscriptions based on customer ID, current subscription ID, or external reference ID

**Appropriate roles**: Global admin | Admin agent | Sales agent

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with both standalone App and App+User credentials.

This API can filter based on query strings that are selected by the partner. Selected query strings may be any of the following three options:

- A CustomerTenantId. If you don't know the customer's ID, you can look it up in [Partner Center](https://partner.microsoft.com/dashboard) by selecting the **Customers** workspace, then the customer from the customer list, then **Account**. On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section. The Microsoft ID is the same as the customer ID.

- A CurrentSubscriptionId (the legacy ID for a subscription that has been migrated)

- An ExternalReferenceId (the batch ID returned by the Batch Migration Tool that is available for download via the Partner Center SDK)

## REST request

### Request syntax

| Method  | Request URI                                                                                                      |
|---------|------------------------------------------------------------------------------------------------------------------|
| **GET** | [*{baseURL}*](partner-center-rest-urls.md)/v1/migrations/newcommerce HTTP/1.1                                    |

### Query Strings

This table lists the query strings needed to filter and retrieve new commerce migrations. Please note, at least one of the three IDs are required to successfully query migrations. Inputting multiple IDs to query is accepted but not required.

| Name                            | Description                                                             |
|---------------------------------|-------------------------------------------------------------------------|
| CustomerTenantId                | A GUID-formatted string that identifies the customer.                   |
| CurrentSubscriptionId           | A GUID-formatted string that identifies a migrated legacy subscription. |
| ExternalReferenceId             | A GUID-formatted string that identifies the migration batch.            |

### Request headers

For more information, see [Partner Center REST headers](headers.md). The response of the API returns a maximum of 300 page records. If over 300 records are returned in an inputted query, a continuation token will be provided in the response header. The continuation token can be input in the header of a following request to return additional page records queried.

### Request body

None.

## REST response

If successful, this method returns details of the [Subscriptions](subscription-resources.md) that were migrated (migration object) in the response body. This includes the migration ID.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Partner Center REST error codes](error-codes.md).

### Request URL examples

```http
baseurl/v1/migrations/newcommerce?CustomerTenantId=83c51838-fed5-44a4-a275-afa201d53699&CurrentSubscriptionId=6CCC6A93-93E4-4382-AF1F-E51237232833&ExternalReferenceId=9ab61899-0b2b-4320-bd6d-8196c53607d6
```

```http
baseurl/v1/migrations/newcommerce?CurrentSubscriptionId=6CCC6A93-93E4-4382-AF1F-E51237232833
```


### Response examples

```http
[
{
"addOnMigrations": [],
"id": "8ce7115e-0324-41b1-8ca3-7c7ae3b64f75",
"startedTime": "2022-02-24T23:50:30.4384819Z",
"completedTime": "2022-02-24T23:53:14.0813711Z",
"currentSubscriptionId": "9E289691-2FF3-419D-B39B-26B3E5A817FB",
"status": "Completed",
"customerTenantId": "ce6fcc21-c276-447b-9605-874decb9024b",
"catalogItemId": "CFQ7TTC0LF8Q:0001:CFQ7TTC0KQDF",
"newCommerceSubscriptionId": "f2d6534b-9e30-4cf5-c7b0-5d6393dbf12d",
"newCommerceOrderId": "09714c93092a",
"subscriptionEndDate": "2023-02-14T00:00:00Z",
"quantity": 2,
"termDuration": "P1Y",
"billingCycle": "Monthly",
"purchaseFullTerm": false,
"externalReferenceId": "771317a4-275d-47d9-9724-3eefa4a168ad"
}
]
```
