---
title: Manage scheduled changes for new commerce subscriptions
description: Learn how to use Partner Center APIs to schedule changes for new commerce subscription resource that only take place on renewal.
ms.date: 2/17/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: migolova
ms.author: migolova
---

# Schedule changes for a new commerce subscription using Partner Center APIs

**Applies To**: Partner Center

This article describes how you can use Partner Center API to schedule changes for a new commerce [subscription](subscription-resources.md), that only take place on renewal.

> [!Note] 
> The new commerce experiences for license-based services include many new capabilities and are available to all Cloud Solution Provider (CSPs). For more information, see [new commerce experiences overview](../new-commerce-license-based.md).

Creating scheduled changes allows you to modify your subscription, automatically, when the next renewal occurs. By scheduling changes, you can choose to increase or decrease the number of licenses, modify the billing term and frequency, and even choose to upgrade the SKU. Scheduling changes allows you to make modifications to your subscription on renewal, rather than immediately during the current term.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with both standalone App and App+User credentials.

- A customer ID (`customer-tenant-id`). If you don't know the customer's ID, you can look it up in [Partner Center](https://partner.microsoft.com/dashboard) by selecting the **Customers** workspace, then the customer from the customer list, then **Account**. On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section. The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).

- A subscription ID.

- Auto-renew is enabled on the subscription.

## Partner Center method

To schedule changes for a subscription in Partner Center:

1. [Select a customer](get-a-customer-by-name.md).

2. Select the subscription that you wish to schedule changes for.

3. Enable Auto-renew.

4. Click Manage renewal.

5. Make modifications to the subscription to take place on renewal.

6. Click Okay to close the side panel.

7. Click Submit to save the changes.

> [!NOTE] 
> Renewals are processed after the final day of a term, starting at 12:00 AM UTC the following day. Renewals are processed in a queue and may take up to 24-hours to be processed.

## C\#

To schedules changes for a customer's subscription:

1. [Get the subscription by ID](get-a-subscription-by-id.md).

2. Create a **ScheduledNextTermInstructions** object and set it to the subscription's property.

3. Call the **Patch()** method to update the subscription with the scheduled changes.

``` csharp
var selectedSubscription = subscriptionOperations.Get();
selectedSubscription.ScheduledNextTermInstructions = new ScheduledNextTermInstructions
{
    Product = new ProductTerm
    {
        ProductId = changeToProductId,
        SkuId = changeToSkuId,
        AvailabilityId = changeToAvailabilityId,
        BillingCycle = changeToBillingCycle,
        TermDuration = changeToTermDuration,
    },
    Quantity = changeToQuantity,
    customTermEndDate = DateTime,
};
var updatedSubscription = subscriptionOperations.Patch(selectedSubscription);
```

## REST request

### Request syntax

| Method    | Request URI                                                                                                                |
|-----------|----------------------------------------------------------------------------------------------------------------------------|
| **PATCH** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id} HTTP/1.1 |

### URI parameter

This table lists the required query parameters to call the API.

| Name                    | Type     | Required | Description                               |
|-------------------------|----------|----------|-------------------------------------------|
| **customer-tenant-id**  | **guid** | Y        | A GUID corresponding to the customer.     |
| **subscription-id** | **guid** | Y        | A GUID corresponding to the subscription. |

### Request headers

For more information, see [Partner Center REST headers](headers.md).

### Request body

A full **Subscription** resource is required in the request body with the `scheduledNextTermInstructions` property defined. To schedule changes for your subscription, ensure that the **AutoRenewEnabled** property has been set to **true**.

| Field                    | Type     | Required | Description                               |
|-------------------------|----------|----------|-------------------------------------------|
| **scheduledNextTermInstructions**  | **object** | Y        | Defines the next term instructions for the subscription. The property contains the `product` object and the `quantity` field.

### Request example

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/subscriptions/<subscription-id> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3831
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105f2c
If-Match: <etag>
Content-Type: application/json
Content-Length: 1029
Expect: 100-continue
Connection: Keep-Alive

{
    "id": "6e7aa601-629e-461b-8933-0898c3cc3c7c",
    "offerId": "DZH318Z0BXWC:0001:DZH318Z0BMJX",
    "offerName": "offer Name",
    "friendlyName": "friendly Name",
    "quantity": 1,
    "customTermEndDate": "2019-01-09T00:21:45.9263727",
    "unitType": "License(s)",
    "hasPurchasableAddons": false,
    "creationDate": "2019-01-04T01:00:12.6647304Z",
    "effectiveStartDate": "2019-01-09T00:21:45.9263727+00:00",
    "commitmentEndDate": "2019-02-08T00:21:45.9263727+00:00",
    "status": "active",
    "autoRenewEnabled": true,
    "scheduledNextTermInstructions": { 
      "product": { 
         "productId":  "DG7GMGF0DVSV", 
         "skuId":  "000P", 
         "availabilityId":  "DG7GMGF0F3Q9", 
         "billingCycle":  "Annual", 
         "termDuration":  "P3Y",
         "promotionId": "39NFJQT1PFPJ:000H:39NFJQT1Q5DK"
        }, 
      "quantity":  1 
      "customTermEndDate" : "2019-01-09T00:21:45.9263727",
     },  // original value = null 
    "isTrial": false,
    "billingType": "license",
    "billingCycle": "monthly",
    "termDuration": "P1M",
    "refundOptions": [{
        "type": "Full",
        "expiresAt": "2019-01-10T00:21:45.9263727+00:00"
    }],
    "isMicrosoftProduct": false,
    "partnerId": "",
    "contractType": "subscription",
    "publisherName": "publisher Name",
    "orderId": "ImxjLNL4_fOc-2KoyOxGTZcrlIquzls11",
    "attributes": {"objectType": "Subscription"},
}
```

## REST response

If the request is successful, this method returns the updated [Subscription](subscription-resources.md) resource properties in the response body.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Error Codes](error-codes.md).

### Response example

```http
HTTP/1.1 200 OK
Content-Length: 1322
Content-Type: application/json; charset=utf-8
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3831
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105f2c
X-Locale: en-US

{
    "id": "6e7aa601-629e-461b-8933-0898c3cc3c7c",
    "offerId": "DZH318Z0BXWC:0001:DZH318Z0BMJX",
    "offerName": "offer Name",
    "friendlyName": "friendly Name",
    "quantity": 1,
    "customTermEndDate": "2019-01-09T00:21:45.9263727",
    "unitType": "License(s)",
    "hasPurchasableAddons": false,
    "creationDate": "2019-01-04T01:00:12.6647304Z",
    "effectiveStartDate": "2019-01-09T00:21:45.9263727+00:00",
    "commitmentEndDate": "2019-02-08T00:21:45.9263727+00:00",
    "status": "active",
    "autoRenewEnabled": true,
    "scheduledNextTermInstructions": { 
      "product": { 
         "productId":  "DG7GMGF0DVSV", 
         "skuId":  "000P", 
         "availabilityId":  "DG7GMGF0F3Q9", 
         "billingCycle":  "Annual", 
         "termDuration":  "P3Y",
         "promotionId": "39NFJQT1PFPJ:000H:39NFJQT1Q5DK"
        }, 
      "quantity":  1 
      "customTermEndDate": "2019-01-09T00:21:45.9263727",
     },  // original value = null 
    "isTrial": false,
    "billingType": "license",
    "billingCycle": "monthly",
    "termDuration": "P1M",
    "refundOptions": [{
        "type": "Full",
        "expiresAt": "2019-01-10T00:21:45.9263727+00:00"
    }],
    "isMicrosoftProduct": false,
    "partnerId": "",
    "contractType": "subscription",
    "publisherName": "publisher Name",
    "orderId": "ImxjLNL4_fOc-2KoyOxGTZcrlIquzls11",
    "attributes": {"objectType": "Subscription"},
}
```
