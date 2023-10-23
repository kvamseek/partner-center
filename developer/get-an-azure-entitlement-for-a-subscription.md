---
title: Get an Azure entitlement for a subscription
description: This section describes the ways that Cloud Solution Provider partners can use the Partner Center to programmatically get an Azure entitlement for a subscription.
ms.date: 12/16/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: migolova
ms.author: migolova
---

# Get an Azure entitlement for a subscription

**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud for US Government

Partners can view their Azure entitlement for a subscription by using this API, which gets the entitlement of the subscription identifier for a customer.

## Prerequisites

- Credentials as described in [Partner Center authentication](./partner-center-authentication.md). This scenario supports authentication with both standalone App and App+User credentials.
- Customer_id.
- Subscription_id.
- Entitlement_id.

### C\#

To cancel an Azure subscription, you'll need to identify your customer ID, subscription ID, and entitlement ID for the Azure subscription you want to cancel.

- To get a customer, refer to [Get a customer by ID](./get-a-customer-by-id.md) and [Get customer by customer ID - REST API](/rest/api/partner-center/manage-customer-accounts/get-customer-by-customer-id) for more help.

- To get a subscription, refer to [Get a subscription by ID](./get-a-subscription-by-id.md#rest-request) and [Get subscription by ID - REST API](/rest/api/partner-center/manage-orders/get-subscription-by-id) for more help.

- To get an entitlement, refer to [Get an Azure entitlement for a subscription - REST API](/rest/api/partner-center/azure-spending/get-an-azure-entitlement-for-a-subscription).

## REST request

### Request syntax

| **Method** | **Request URI**  |
|------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **POST**   | [*{baseURL}*](./partner-center-rest-urls.md)/v1/customers/{customer_id}/subscriptions/{subscription_id}/azureEntitlements/{entitlement_id} HTTP/1.1|

### URI parameter

This table lists the required query parameters to cancel an Azure subscription.

| **Name**        | **Type** | **Required** | **Description**                                                                          |
|-----------------|----------|--------------|------------------------------------------------------------------------------------------|
| customer_id     | String   | Y            | The value is a string that denotes the identifier of the customer.                       |
| subscription_id | String   | Y            | The value is a string that denotes the identifier of the customer.                       |
| entitlement_id  | String   | Y            | The value is a string that denotes the identifier of the Azure subscription entitlement. |

### Request headers

See [Partner Center REST headers](./headers.md).

### Request body

No request body is required.

### Request example

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer_id}/subscriptions/{subscription_id}/azureEntitlements/{entitlement_id}

HTTP/1.1
Accept: application/json
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
```

## REST response

If successful, this method returns an [Azure entitlement for a subscription](./subscription-resources.md#azureentitlement) resource in the response body.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and more debugging information. Use a network trace tool to read this code, error type, and other parameters. For the full list, see [Partner Center REST error codes](./error-codes.md).

| **HTTP Status** | **HTTP Code** | **Error code** | **Description**                                                                                                                                     |
|-----------------|---------------|----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
| BadRequest      | 400           | 900118         | Invalid customer ID.                                                                                                                                |
| BadRequest      | 400           | 800002         | Customer ID {0} should have GUID format (xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).                                                                     |
| BadRequest      | 400           | 800002         | Subscription ID is required.                                                                                                                        |
| BadRequest      | 400           | 800002         | Entitlement ID is required.                                                                                                                         |
| BadRequest      | 400           | 800002         | The Azure entitlement cancellation request content is required.                                                                                     |
| Forbidden       | 403           | 900159         | The partner with account ID {0} and organization ID {1} has no commerce relationship with the customer with account ID {2} and organization ID {3}. |
| BadRequest      | 400           | 900307         | Cancellation reason '{0} is invalid.                                                                                                                |
| NotFound        | 404           | 800111         | Azure entitlement with ID {0} isn't found.                                                                                                         |

### Response example

The response returns the Azure entitlement for a given customer.

```json
HTTP
HTTP/1.1 200 OK
Content-Length: 1132
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 6eacec93-852d-4167-9d96-c57809bea7ed
MS-RequestId: 22bfd0fb-d1e6-4a8f-aa1a-124b7c820d80
MS-CV: cmde2DtbuUWi8JLq.0
MS-ServerId: 201022015
Date: Wed, 14 Dec 2022 00:12:53 GMT

{ 
    "id": "5b76b8c3-dd85-4096-bb2e-9804b1d7b383", 
    "friendlyName": " Cancel_Azure_Subscription", 
    "status": “inactive", 
    "subscriptionId": "065eefc4-915b-453d-c558-152e39ec25b1", 
    "links": { 
        "self": { 
            "uri": "/customers/425829ba-6938-4b55-af29-fbbd28ebeebf/subscriptions/065eefc4-915b-453d-c558-152e39ec25b1/azureEntitlements/5b76b8c3-dd85-4096-bb2e-9804b1d7b383", 
            "method": "GET", 
            "headers": [] 
        } 
    } 

```

## Next steps

- [Azure plan - Manage subscriptions & resources](../azure-plan-manage.md#cancel-an-azure-subscription)
- [Azure spending - Cancel an Azure entitlement - REST API](/rest/api/partner-center/azure-spending/cancel-an-azure-entitlement#code-try-0)
- [Cancel an Azure subscription - Partner Center app developer](./cancel-an-azure-subscription.md)
- [Azure spending - Get an Azure entitlement for a subscription - REST API](/rest/api/partner-center/azure-spending/get-an-azure-entitlement-for-a-subscription)