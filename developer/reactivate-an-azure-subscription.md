---
title: Reactivate an Azure subscription
description: This section describes the ways that Cloud Solution Provider partners can use the Partner Center to programmatically reactivate an Azure subscription.
ms.date: 8/29/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: migolova
ms.author: migolova
---

# Reactivate an Azure subscription

**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud for US Government

This API reactivates an Azure subscription that has been previously [canceled](cancel-an-azure-subscription.md). To reactivate more than one subscription, call the API separately to reactivate each subscription.  

Partners must be Global Administrators with Admin Agent roles to reactivate.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with both standalone App and App+User credentials.
- Customer_id
- Subscription_id
- Entitlement_id
- Version

## C#

To reactivate an Azure subscription, you'll need to identify your customer ID, subscription ID, and entitlement ID for the Azure subscription you want to reactivate.

- To get a customer ID, refer to [Get a customer by ID](get-a-customer-by-id.md) and [Get customer by customer ID - REST API](/rest/api/partner-center/manage-customer-accounts/get-customer-by-customer-id).

- To get a subscription ID, refer to [Get a subscription by ID](get-a-subscription-by-id.md#rest-request) and [Get subscription by ID - REST API](/rest/api/partner-center/manage-orders/get-subscription-by-id).

- To get an entitlement ID, refer to [Get an Azure entitlement for a subscription - REST API](/rest/api/partner-center/azure-spending/get-an-azure-entitlement-for-a-subscription).

## REST request

### Request syntax

| Method   | Request URI |
|----------|-------------|
| **POST** | [_{baseURL}_](partner-center-rest-urls.md)/v1/customers/{customer_id}/subscriptions/{subscription_id}/azureEntitlements/{entitlement_id}/reactivate HTTP/1.1 |

### URI parameter

This table lists the required query parameters to reactivate an Azure subscription.

| Name            | Type     | Required | Description                                                                              |
| --------------- | -------- | -------- | ---------------------------------------------------------------------------------------- |
| customer_id     | String   | Y        | The value is a string that denotes the identifier of the customer.                       |
|                 |          |          |                                                                                          |
| subscription_id | String   | Y        | The value is a string that denotes the identifier of the customer.                       |
| entitlement_id  | String   | Y        | The value is a string that denotes the identifier of the Azure subscription entitlement. |
| version         | String   | Y        | The API version.                                                                         |

### Request headers

See [Partner Center REST headers](headers.md).

## REST response

If successful, this method returns HTTP Code 202, which indicates that the reactivation of the Azure entitlement of a subscription request has been accepted.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and other debugging information. Use a network trace tool to read this code, error type, and other parameters. For the full list, see [Partner Center REST error codes](error-codes.md).

| HTTP Status | HTTP Code | Error code | Description                                                                                                                                         |
| ----------- | --------- | ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| BadRequest  | 400       | 900118     | Invalid customer ID.                                                                                                                                |
| BadRequest  | 400       | 800002     | Customer ID {0} should have GUID format (xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).                                                                     |
| BadRequest  | 400       | 800002     | Subscription ID is required.                                                                                                                        |
| BadRequest  | 400       | 800002     | Entitlement ID is required.                                                                                                                         |
| Forbidden   | 403       | 900159     | The partner with account ID {0} and organization ID {1} has no commerce relationship with the customer with account ID {2} and organization ID {3}. |
| BadRequest  | 400       | 900337     | Partner cannot reactivate Azure entitlement with ID {0}.                                                                                            |
| Forbidden   | 403       | 900335     | Partner doesn't have required permissions to reactivate Azure entitlement with ID {0}.                                                              |
| NotFound    | 404       | 800111     | Azure entitlement with ID {0} is not found.                                                                                                         |

## Next steps

Recommended content:

- [Azure plan - Manage subscriptions & resources - Partner Center | Microsoft Learn](../azure-plan-manage.md#cancel-an-azure-subscription)
- [Cancel an Azure subscription - Partner app developer | Microsoft Learn](cancel-an-azure-subscription.md)
