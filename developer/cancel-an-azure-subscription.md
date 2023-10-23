---
title: Cancel an Azure subscription
description: This section describes the ways that Cloud Solution Provider partners can use the Partner Center to programmatically cancel an Azure subscription.
ms.date: 12/16/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: migolova
ms.author: migolova
---

# Cancel an Azure subscription

**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud for US Government

If compromise or abuse, partners with Azure customer subscriptions can cancel the subscriptions directly from Partner Center portal or by API, shutting down suspicious activity discovered in their Azure plan subscriptions.

This API will cancel an Azure subscription. If partners want to cancel more than one subscription, they'll need to separately call the API to cancel each one.

If partners want to suspend their Azure plan, they should use the existing API available, [Update a subscription by ID](/partner-center/develop/update-a-subscription-by-id).

Cancelling Azure plan isn't supported by the following API.

Partners must be Global Administrators with Admin Agent roles to cancel.

## Prerequisites

- Credentials as described in [Partner Center authentication](./partner-center-authentication.md) This scenario supports authentication with both standalone App and App+User credentials.

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

| **Method** | **Request URI**                                                                                                                                                                                                |
|------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **POST**   | [*{baseURL}*](./partner-center-rest-urls.md)/v1/customers/{customer_id}/subscriptions/{subscription_id}/azureEntitlements/{entitlement_id}/cancel HTTP/1.1 |

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

```http
HTTP
{ "cancellationReason": "compromise" }
```

### Request example

```json
POST
[https://api.partnercenter.microsoft.com/v1/customers/{customer_id}/subscriptions/{subscription_id}/azureEntitlements/{entitlement_id}/cancel](https://api.partnercenter.microsoft.com/v1/customers/%7bcustomer_id%7d/subscriptions/%7bsubscription_id%7d/azureEntitlements/%7bentitlement_id%7d/cancel)
HTTP/1.1
Accept: application/json
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
{
 "id": "5b76b8c3-dd85-4096-bb2e-9804b1d7b383",
 "friendlyName": "Cancel_Azure_Subscription ",
 "status": “active",
 "subscriptionId": "065eefc4-915b-453d-c558-152e39ec25b1",
 "links": {
  "self": {
  "uri":
  "/customers/425829ba-6938-4b55-af29-fbbd28ebeebf/subscriptions/065eefc4-915b-453d-c558-152e39ec25b1/azureEntitlements/5b76b8c3-dd85-4096-bb2e-9804b1d7b383",
  "method": "GET",
"headers": []
   }
  }
}
```

## REST response

If successful, this method returns an [Azure entitlement for a subscription](./subscription-resources.md#azureentitlement) resource in the response body.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and more debugging information. Use a network trace tool to read this code, error type, and other parameters. For the full list, see [Partner Center REST error codes](error-codes.md).

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

The response for canceling a subscription includes the entitlement status. Expect about 10 mins for the status to be reflected (that is, active to inactive).

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
"status": “active",
"subscriptionId": "065eefc4-915b-453d-c558-152e39ec25b1",
"links": {
"self": {
"uri":
"/customers/425829ba-6938-4b55-af29-fbbd28ebeebf/subscriptions/065eefc4-915b-453d-c558-152e39ec25b1/azureEntitlements/5b76b8c3-dd85-4096-bb2e-9804b1d7b383",
"method": "GET",
"headers": []
 }
}
```

## Next steps

- [Azure plan - Manage subscriptions & resources](../azure-plan-manage.md#cancel-an-azure-subscription)
- [Azure spending - Cancel an Azure entitlement - REST API](/rest/api/partner-center/azure-spending/cancel-an-azure-entitlement#code-try-0)
- [Get an Azure entitlement for a subscription - Partner Center app developer](./get-an-azure-entitlement-for-a-subscription.md)
- [Azure spending - Get an Azure entitlement for a subscription - REST API](/rest/api/partner-center/azure-spending/get-an-azure-entitlement-for-a-subscription)