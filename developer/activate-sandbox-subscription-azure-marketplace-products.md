---
title: Activate a sandbox subscription for commercial marketplace products
description: Learn how to use C/# and Partner Center REST APIs to activate a sandbox subscription for commercial marketplace products.
ms.date: 06/30/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: JulCsc
ms.author: raormeni
---

# Activate a sandbox subscription for commercial marketplace SaaS products to enable billing

How to activate a subscription for commercial marketplace Software as a Service (SaaS) products from integration sandbox accounts to enable billing.

> [!NOTE]
> It's only possible to activate a subscription for commercial marketplace SaaS products from integration sandbox accounts. If you have a production subscription, you must visit the publisher's site to complete the setup process. Subscription billing will begin only after setup is complete.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with both standalone App and App+User credentials.
- An integration sandbox partner account with a customer having an active subscription for commercial marketplace SaaS products.
- For partners using Partner Center .NET SDK, you must use SDK version 1.14.0 or higher to access this capability.

> [!IMPORTANT]
> As of June 2023, the latest Partner Center .NET SDK release 3.4.0 is now archived. You can [download the SDK release from GitHub](https://github.com/microsoft/partner-center-sdk-for-dotNET), along with a [readme file](https://github.com/microsoft/partner-center-sdk-for-dotNET#readme) that contains useful information.
>
> Partners are encouraged to continue to use the [Partner Center REST APIs](partner-center-rest-api-reference.md).

## C\#

Use the following steps to activate a subscription for commercial marketplace SaaS products:

1. Make an interface to the subscription operations available. You must identify the customer and specify the subscription identifier of the trial subscription.

   ```csharp
   var subscriptionOperations = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId);
   ```

2. Activate the subscription using the **Activate** operation.

   ```csharp
   var subscriptionActivationResult = subscriptionOperations.Activate();
   ```

## REST request

### Request syntax

| Method     | Request URI                                                                            |
|------------|----------------------------------------------------------------------------------------|
| **POST** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/activate HTTP/1.1 |

### URI parameter

| Name                   | Type     | Required | Description                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| **customer-tenant-id** | **guid** | Y | The value is a GUID-formatted customer tenant identifier (**customer-tenant-id**), which allows you to specify a customer. |
| **subscription-id** | **guid** | Y | The value is a GUID-formatted subscription identifier (**subscription-id**), which allows you to specify a subscription. |

### Request headers

For more information, see [Partner Center REST headers](headers.md).

### Request body

None.

### Request example

```http
POST https://api.partnercenter.microsoft.com/v1/customers/42b5f772-5c5c-4bce-b9d7-bdadeecca411/subscriptions/87363db7-39ab-dd25-d371-94340aaa2f97/activate HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5

```

## REST response

This method returns the **subscription-id** and **status** properties.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Partner Center REST error codes](error-codes.md).

### Response example

```http
HTTP/1.1 200 OK
Content-Length: 79
Content-Type: application/json
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5

{
    "subscriptionId":"87363db7-39ab-dd25-d371-94340aaa2f97",
    "status":"Success"
}
```
