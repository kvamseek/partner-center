---
title: Get order provisioning status
description: How to get the provisioning status for an order.
ms.date: 01/03/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: migolova
ms.author: migolova
---

# Get order provisioning status

**Applies to**: Partner Center | Partner Center operated by 21Vianet |  Partner Center for Microsoft Cloud for US Government

**Appropriate roles**: Global admin | Admin agent

Gets a collection of order line item provisioning status for an order.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with App+User credentials only.

- A customer ID (`customer-tenant-id`). If you don't know the customer's ID, you can look it up in [Partner Center](https://partner.microsoft.com/dashboard) by selecting the **Customers** workspace, then the customer from the customer list, then **Account**. On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section. The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).

- An order identifier.

## C\#

To get the provisioning status of an order, use the following code snippet:

``` csharp
// Retrieve an order's provisioning status.
 var customerOrder = partnerOperations.Customers.ById(customerId).Orders.ById(orderId).Get();
 var provisioningStatusList = partnerOperations.Customers.ById(customerId).Orders.ById(customerOrder.Id).ProvisioningStatus.Get();
```

## REST request

### Request syntax

| Method  | Request URI                                                                                                                        |
|---------|------------------------------------------------------------------------------------------------------------------------------------|
| **GET** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/orders/{order-id}/provisioningstatus HTTP/1.1 |

### URI parameters

Use the following path parameters to identify the customer and subscription.

| Name            | Type   | Required | Description                                               |
|-----------------|--------|----------|-----------------------------------------------------------|
| customer-id     | string | Yes      | A GUID formatted string that identifies the customer.     |
| order-id        | string | Yes      | A string that identifies the order.        |

### Request headers

For more information, see [Partner Center REST headers](headers.md).

### Request body

None.

### Request example

```http
GET https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/orders/34828C05-C16C-4D6F-9CFC-4D2650EF19A1/provisioningstatus HTTP/1.1
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
MS-RequestId: d0e38dfd-a2c5-4a14-ac06-12d30f0ec54e
MS-CorrelationId: e937630b-8341-4d70-8f73-450d32ee0189
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## REST response

If successful, the response body contains a [OrderLineItemProvisioningStatus](order-resources.md#orderlineitemprovisioningstatus) resource.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Partner Center REST error codes](error-codes.md).

### Response example

```http
HTTP/1.1 200 OK
Content-Length: 177
Content-Type: application/json; charset=utf-8
MS-CorrelationId: e937630b-8341-4d70-8f73-450d32ee0189
MS-RequestId: d0e38dfd-a2c5-4a14-ac06-12d30f0ec54e
MS-CV: InswEQre402koceL.0
MS-ServerId: 030020344
Date: Thu, 20 Apr 2017 19:23:39 GMT

{
    "totalCount": 1,
    "items": [
        {
            "orderLineItemId": 0,
            "lineItemNumber": 0,
            "status": "fulfilled",
            "quantityProvisioningInformation": [
                {
                    "quantity": 1,
                    "status": "fulfilled"
                }
            ]
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
