---
title: Register a subscription
description: Register an existing subscription so that it is enabled for ordering Azure reservations.
ms.date: 06/28/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: migolova
ms.author: migolova
---

# Register a subscription

Register an existing [Subscription](subscription-resources.md) so that it is enabled for ordering Azure reservations.

To purchase an Azure reservation, you must have at least one existing CSP Azure subscription. This method allows you to register your existing CSP Azure subscription, enabling it for purchasing Azure reservations.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with both standalone App and App+User credentials.

- A customer ID (`customer-tenant-id`). If you don't know the customer's ID, you can look it up in [Partner Center](https://partner.microsoft.com/dashboard) by selecting the **Customers** workspace, then the customer from the customer list, then **Account**. On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section. The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).

- A subscription ID.

## C\#

To register a customer's subscription, retrieve an interface to subscription operations by calling the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer. Then, call the [**Subscription.ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) method with the subscription ID to identify the subscription that you are registering.

Finally, call the **Registration.Register()** method to register the subscription and retrieve a URI that can be used to get the subscription registration status. For more information, see [Get subscription registration status](get-subscription-registration-status.md).

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId;
// var selectedSubscriptionId;

// Retrieve the subscription registration details.
var subscriptionRegistrationDetails = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).Registration.Register();
```

## REST request

### Request syntax

| Method    | Request URI                                                                                                                        |
|-----------|------------------------------------------------------------------------------------------------------------------------------------|
| **POST**  | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/registrations HTTP/1.1 |

### URI parameters

Use the following path parameters to identify the customer and subscription.

| Name                    | Type       | Required | Description                                                   |
|-------------------------|------------|----------|---------------------------------------------------------------|
| customer-id             | string     | Yes      | A GUID formatted string that identifies the customer.         |
| subscription-id         | string     | Yes      | A GUID formatted string that identifies the subscription.     |

### Request headers

For more information, see [Partner Center REST headers](headers.md).

### Request body

None.

### Request example

```http
POST https://api.partnercenter.microsoft.com/v1/customers/<customer-id>/subscriptions/<subscription-id>/registrations HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105123
Content-Type: application/json
Content-Length: 1029
Expect: 100-continue
Connection: Keep-Alive
```

## REST response

If successful, the response contains a **Location** header with a URI that can be used to retrieve the subscription registration status. Save this URI for use with other related REST APIs. For an example of how to retrieve the status, see [Get subscription registration status](get-subscription-registration-status.md).

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Error Codes](error-codes.md).

### Response example

```http
HTTP/1.1 202 Accepted
Content-Length: 0
Location: /customers/<customer-id>/subscriptions/<subscription-id>/registrationstatus
MS-CorrelationId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-RequestId: ec8f62e5-1d92-47e9-8d5d-1924af105123
MS-CV: iqOqN0FnaE2y0HcD.0
MS-ServerId: 030020525
```
