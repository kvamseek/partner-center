---
title: Update autorenew for commercial marketplace or software subscriptions
description: Update the autorenew property for a Subscription resource that matches the customer and subscription ID.
ms.date: 8/1/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: sourishdeb
ms.author: sodeb
---

# Update autorenew for a commercial marketplace subscription or new commerce subscriptions or software subscriptions

**Applies To**: Partner Center

> [!Note] 
> The new commerce experiences for license-based services include many new capabilities and are available to all Cloud Solution Provider (CSPs). For more information, see [new commerce experiences overview](../new-commerce-license-based.md).

Update the autorenew property for a commercial marketplace, new commerce, or software [Subscription](subscription-resources.md) resource that matches the customer and subscription ID.

In Partner Center, this operation is performed by first [selecting a customer](get-a-customer-by-name.md). Then, select the subscription that you wish to update. Finally, toggle the **Auto-renew** option, then select **Submit**.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with both standalone App and App+User credentials.

- A customer ID (`customer-tenant-id`). If you don't know the customer's ID, you can look it up in [Partner Center](https://partner.microsoft.com/dashboard). Select **Customers** from the home page, then select the customer from the customer list and then select **Account**. On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section. The Microsoft ID is the same as the customer ID (`customer-tenant-id`)."

- A subscription ID.

## C\#

To update a customer's subscription, first [Get the subscription](get-a-subscription-by-id.md), then set the subscription's [**autoRenewEnabled**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.autoRenewEnabled) property. Once the change is made, use your **IAggregatePartner.Customers** collection and call the **ById()** method. Then call the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property, followed by the [**ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) method. Then, finish by calling the **Patch()** method.

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId as string;
// Subscription selectedSubscription;

// turn off auto renew.
selectedSubscription.AutoRenewEnabled = false;
var updatedSubscription = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscription.Id).Patch(selectedSubscription);
```

**Sample**: [Console test app](console-test-app.md). **Project**: PartnerSDK.FeatureSample **Class**: UpdateSubscription.cs

## REST request

### Request syntax

| Method    | Request URI                                                                                                                |
|-----------|----------------------------------------------------------------------------------------------------------------------------|
| **PATCH** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription} HTTP/1.1 |

### URI parameter

This table lists the required query parameter to suspend the subscription.

| Name                    | Type     | Required | Description                               |
|-------------------------|----------|----------|-------------------------------------------|
| **customer-tenant-id**  | **GUID** | Y        | A GUID corresponding to the customer.     |
| **id-for-subscription** | **GUID** | Y        | A GUID corresponding to the subscription. |

### Request headers

For more information, see [Partner Center REST headers](headers.md).

### Request body

A full **Subscription** resource is required in the request body. Ensure that the **AutoRenewEnabled** property has been updated.

### Request example for commercial marketplace subscription

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/subscriptions/<id-for-subscription> HTTP/1.1
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
    "unitType": "License(s)",
    "hasPurchasableAddons": false,
    "creationDate": "2019-01-04T01:00:12.6647304Z",
    "effectiveStartDate": "2019-01-09T00:21:45.9263727+00:00",
    "commitmentEndDate": "2019-02-08T00:21:45.9263727+00:00",
    "status": "active",
    "autoRenewEnabled": false,
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

### Request example for new commerce subscription

> [!Note] 
> The new commerce experiences for license-based services include many new capabilities and are available to all Cloud Solution Provider (CSPs). For more information, see [new commerce experiences overview](../new-commerce-license-based.md).

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/subscriptions/<id-for-subscription> HTTP/1.1
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
    "id": "a4c1340d-6911-4758-bba3-0c4c6007d161",
    "offerId": "CFQ7TTC0LH18:0001:CFQ7TTC0K971",
    "offerName": "Microsoft 365 Business Basic",
    "friendlyName": "Microsoft 365 Business Basic",
    "productType": {
        "id": "OnlineServicesNCE",
        "displayName": "OnlineServicesNCE"
    },
    "quantity": 1, 
    "unitType": "Licenses",
    "hasPurchasableAddons": false,
    "creationDate": "2021-01-14T16:57:15.0966728Z",
    "effectiveStartDate": "2021-01-14T16:57:14.498252Z",
    "commitmentEndDate": "2022-01-13T00:00:00Z",
    "status": "active",
    "autoRenewEnabled": false, // original value = true
    "isTrial": false,
    "billingType": "license",
    "billingCycle": "monthly",
    "termDuration": "P1Y",
    "renewalTermDuration": "",
    "refundOptions": [
        {
            "type": "Full",
            "expiresAt": "2021-01-15T00:00:00Z"
        }
    ],
    "isMicrosoftProduct": true,
    "partnerId": "",
    "attentionNeeded": false,
    "actionTaken": false,
    "contractType": "subscription",
    "links": {
        "product": {
            "uri": "/products/CFQ7TTC0LH18?country=US",
            "method": "GET",
            "headers": []
        },
        "sku": {
            "uri": "/products/CFQ7TTC0LH18/skus/0001?country=US",
            "method": "GET",
            "headers": []
        },
        "availability": {
            "uri": "/products/CFQ7TTC0LH18/skus/0001/availabilities/CFQ7TTC0K971?country=US",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/customers/d8202a51-69f9-4228-b900-d0e081af17d7/subscriptions/a4c1340d-6911-4758-bba3-0c4c6007d161",
            "method": "GET",
            "headers": []
        }
    },
    "publisherName": "Microsoft Corporation",
    "orderId": "34b37d7340cc",
    "attributes": {
        "objectType": "Subscription"
    }
}
```

## REST response

If successful, this method returns updated [Subscription](subscription-resources.md) resource properties in the response body.

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
    "unitType": "License(s)",
    "hasPurchasableAddons": false,
    "creationDate": "2019-01-04T01:00:12.6647304Z",
    "effectiveStartDate": "2019-01-09T00:21:45.9263727+00:00",
    "commitmentEndDate": "2019-02-08T00:21:45.9263727+00:00",
    "status": "active",
    "autoRenewEnabled": false,
    "isTrial": false,
    "billingType": "license",
    "billingCycle": "monthly",
    "termDuration": "P1M",
    "refundOptions": [
        {
            "type": "Full",
            "expiresAt": "2019-01-10T00:21:45.9263727+00:00"
        }
    ],
    "isMicrosoftProduct": false,
    "partnerId": "",
    "contractType": "subscription",
    "links": {
        "product": {
            "uri": "/products/DZH318Z0BXWC?country=US",
            "method": "GET",
            "headers": []
        },
        "sku": {
            "uri": "/products/DZH318Z0BXWC/skus/0001?country=US",
            "method": "GET",
            "headers": []
        },
        "availability": {
            "uri": "/products/DZH318Z0BXWC/skus/0001/availabilities/DZH318Z0BMJX?country=US",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/customers/5921f00a-32c0-4457-aaa1-e8018c650895/subscriptions/6e7aa601-629e-461b-8933-0898c3cc3c7c",
            "method": "GET",
            "headers": []
        }
    },
    "publisherName": "publishe rName",
    "orderId": "ImxjLNL4_fOc-2KoyOxGTZcrlIquzls11",
    "attributes": {
        "etag": "",
        "objectType": "Subscription"
    }
}
```