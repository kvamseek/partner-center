---
title: Gets transition history for a previously transitioned new commerce subscription
description: Gets transition history for a previously transitioned new commerce subscription.
ms.date: 03/13/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: migolova
ms.author: migolova
---

# Get transitions

**Applies To**

- Partner Center

**Appropriate roles**

- Global admin
- Admin agent

> [!Note] 
> The new commerce experiences for license-based services include many new capabilities and are available to all Cloud Solution Provider (CSPs). For more information, see [new commerce experiences overview](../new-commerce-license-based.md).

Used to get the history of transitions for a given customer and subscription. History includes all events that were processed for the transition. This only supports new commerce license-based subscription transitions.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with both standalone App and App+User credentials.

- A customer ID (`customer-tenant-id`). If you don't know the customer's ID, you can look it up in [Partner Center](https://partner.microsoft.com/dashboard) by selecting the **Customers** workspace, then the customer from the customer list, then **Account**. On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section. The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).

- One subscription ID for the transitioned subscription.

## REST request

[GET] customers/{customer-tenant-id}/subscriptions/{subscription-id}/transitions

### Request syntax

| Method   | Request URI                                                                                                                         |
|----------|-------------------------------------------------------------------------------------------------------------------------------------|
| **GET**  | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/transitions HTTP/1.1 |

### URI parameter

Use the following query parameters to return eligible transitions.

| Name                    | Type     | Required | Description                                       |
|-------------------------|----------|----------|---------------------------------------------------|
| **customer-tenant-id**  | **guid** | Y        | A GUID corresponding to the customer's tenant.             |
| **subscription-id** | **guid** | Y        | A GUID corresponding to the initial subscription. |
|**operation-id**        | **guid** | N | A GUID to uniquely identify a Transition and track its status.|

### Request headers

For more information, see [Partner Center REST headers](headers.md).

### Request body

None

### Request example

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/transitions HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
X-Locale: en-US
```

## REST response

If successful, this returns a history of transitions for the provided subscription.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Error Codes](error-codes.md).

### Response example

```http
HTTP/1.1 200 OK
Content-Length: 138
Content-Type: application/json
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
Date: Fri, 26 Feb 2021 20:42:26 GMT

{
    "transition": [
        {
        "operationId": "1caf8ec7-62cc-4ab5-b35d-572d2a62974c", 
        "FromCatalogItemId": "CFQ7TTC0LDPB:0001:CFQ7TTC0LGNT",
        "ToCatalogItemId": "CFQ7TTC0LF8S:0001:CFQ7TTC0K9G9",
        "quantity": 1,
        "transitionType": "transition_with_license_transfer",
        "Events": [
           {
               "name": "Conversion",
               "status": "Started ",
               "timestamp": "2021-01-08T18:01:14.7488618Z",
               "attributes":
                     {
                          "objectType": "TransitionEvent"
                     }
           }, 
           {
               "name": "Conversion",
               "status": "Completed",
               "timestamp": "2021-01-08T18:37:41.591855Z",
               "attributes":
                     {
                          "objectType": "TransitionEvent"
                     }
            }
        ],
        "attributes":
               {
                     "objectType": "Transition"
               }
        }
    ],
    "attributes":
        {
               "objectType": "Collection"
        }
}
```