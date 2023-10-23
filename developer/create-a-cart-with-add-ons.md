---
title: Create a cart with add-ons
description: Learn how to use Partner Center APIs to add a customer order with add-ons through a cart. Article shares prerequisites and steps to create a cart with add-ons.
ms.date: 12/10/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: iragulati1
ms.author: iragulati
---

# Create a cart with add-ons to a customer order

You can purchase add-ons through a cart. For more information about what is currently available to sell, see [Partner offers in the Cloud Solution Provider program](../csp-offers.md).

> [!Note] 
> The new commerce experiences for license-based services include many new capabilities and are available to all Cloud Solution Provider (CSPs). For more information, see [new commerce experiences overview](../new-commerce-license-based.md).

New commerce carts with add-ons are different from the traditional license-based offers. New commerce add-ons are purchased the same way as base offers, they don't leverage the **addonItems** property. This topic includes request and response examples specifically for a new commerce based product SKU with an add-on product SKU.

Please note, carts expire 7 days from initial creation.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with both standalone App and App+User credentials.

- A customer ID (`customer-tenant-id`). If you don't know the customer's ID, you can look it up in [Partner Center](https://partner.microsoft.com/dashboard) by selecting the **Customers** workspace, then the customer from the customer list, then **Account**. On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section. The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).

## C\#

A cart enables the purchase of a base offer and its corresponding add-ons. Follow these steps to create a cart:

1. Instantiate a [**Cart**](/dotnet/api/microsoft.store.partnercenter.models.carts.cart) object.

2. Create a list of [**CartLineItem**](/dotnet/api/microsoft.store.partnercenter.models.carts.cartlineitem) objects that represent the base offer(s), and assign the list to the cart's [**LineItems**](/dotnet/api/microsoft.store.partnercenter.models.carts.cart.lineitems) property.

3. Under each base offer's cart line item, populate the list of **AddOnItems** with other **CartLineItem** objects that each represent an add-on that will be purchased against that base offer.

4. Obtain an interface to cart operations by using [**IAggregatePartner**](/dotnet/api/microsoft.store.partnercenter.iaggregatepartner) to call the [**ICustomerCollection.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer, and then retrieving the interface from the **Cart** property.

5. Finally, call the [**Create**](/dotnet/api/microsoft.store.partnercenter.carts.icartcollection.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.carts.icartcollection.createasync) method to create the cart.

### C\# example

```csharp
// IAggregatePartner partnerOperations;
// string customerId;

var cart = new Cart()
    {
        LineItems = new List<CartLineItem>()
        {
            new CartLineItem()
            {
                Id = 0,
                CatalogItemId = "A_base_offer_ID",
                FriendlyName = "Myofferpurchase",
                Quantity = 3,
                BillingCycle = BillingCycleType.Monthly,
                AddonItems = new List<CartLineItem>
                {
                    new CartLineItem
                    {
                        Id = 1,
                        CatalogItemId = "An_addon_item_ID",
                        BillingCycle = BillingCycleType.Monthly,
                        Quantity = 2,
                    },
                    new CartLineItem
                    {
                        Id = 2,
                        CatalogItemId = "Another_addon_item_ID",
                        BillingCycle = BillingCycleType.Monthly,
                        Quantity = 3
                    }
                }
            }
        }
    };

var createdCart = partnerOperations.Customers.ById(customerId).Carts.Create(cart);
```

Follow these steps to create a cart that will enable the purchase of add-on(s) against existing base subscription(s):

1. Create a **Cart** with a new **CartLineItem** containing the subscription ID in the **ProvisioningContext** property with key "ParentSubscriptionId".

2. Call the **Create** or **CreateAsync** method.

```csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

var cart = new Cart()
    {
        LineItems = new List<CartLineItem>()
        {
            new CartLineItem()
            {
                Id = 0,
                CatalogItemId = "An_addon_item_ID",
                ProvisioningContext = new Dictionary<string, string>
                {
                    {
                        "ParentSubscriptionId", "An_existing_subscription_Id"
                    }
                },
                Quantity = 1,
                BillingCycle = BillingCycleType.Annual,
            }
        }
    };

var createdCart = partnerOperations.Customers.ById(selectedCustomerId).Carts.Create(cart);
```

## REST request

### Request syntax

| Method   | Request URI                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| **POST** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/carts HTTP/1.1                        |

#### URI parameter

Use the following path parameter to identify the customer.

| Name            | Type     | Required | Description                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| **customer-id** | string   | Yes      | A GUID formatted customer-id that identifies the customer.             |

### Request headers

For more information, see [Partner Center REST headers](headers.md).

### Request body

This table describes the [Cart](cart-resources.md) properties in the request body.

| Property              | Type             | Required        | Description |
|-----------------------|------------------|-----------------|-----------------------------------------------------------------------------------------------------------|
| id                    | string           | No              | A cart identifier that is supplied upon successful creation of the cart.                                  |
| creationTimeStamp     | DateTime         | No              | The date the cart was created, in date-time format. Applied upon successful creation of the cart.         |
| lastModifiedTimeStamp | DateTime         | No              | The date the cart was last updated, in date-time format. Applied upon successful creation of the cart.    |
| expirationTimeStamp   | DateTime         | No              | The date the cart will expire, in date-time format.  Applied upon successful creation of cart.            |
| lastModifiedUser      | string           | No              | The user who last updated the cart. Applied upon successful creation of cart.                             |
| lineItems             | Array of objects | Yes             | An Array of [CartLineItem](cart-resources.md#cartlineitem) resources.                                             |

This table describes the [CartLineItem](cart-resources.md#cartlineitem) properties in the request body.

| Property             | Type                             | Description                                                                                                                                           |
|----------------------|----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
| id                   | string                           | A unique identifier for a cart line item. Applied upon successful creation of cart.                                                                   |
| catalogId            | string                           | The catalog item identifier.                                                                                                                          |
| friendlyName         | string                           | Optional. The friendly name for the item defined by the partner to help disambiguate.                                                                 |
| quantity             | int                              | The number of licenses or instances.                                                                                                                  |
| currencyCode         | string                           | The currency code.                                                                                                                                    |
| billingCycle         | Object                           | The type of billing cycle set for the current period.                                                                                                 |
| participants         | List of Object String pairs      | A collection of PartnerId on Record (PartnerID) on the purchase.                                                                                          |
| provisioningContext  | Dictionary<string, string>       | A context used for provisioning of offer.                                                                                                             |
| orderGroup           | string                           | A group to indicate which items can be placed together.                                                                                               |
| addonItems           | List of **CartLineItem** objects | A collection of cart line items for add-ons that will be purchased towards the base subscription that results from the parent cart line item's purchase. This property is only for traditional license-based, new commerce license-based carts include add-ons as based offers. New-commerce items don't use this **addonItems** property. |
| error                | Object                           | Applied after cart is created if there's an error.                                                                                                    |

### Request example (new base subscription) for traditional license-based

The following REST example shows how to create a cart with add-on items for a new base subscription.

```http
POST https://api.partnercenter.microsoft.com/v1/customers/18ac2950-8ea9-4dfc-92a4-ff4d4cd57796/carts HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: f931348a-6312-47d0-a8dd-31a386dedb8f
MS-CorrelationId: f73baf70-bbc3-43d0-8b29-dffa08ff9511

{
    "LineItems": [
        {
            "Id":0,
            "CatalogItemId":"91FD106F-4B2C-4938-95AC-F54F74E9A239",
            "FriendlyName":"Myofferpurchase",
            "Quantity":3,
            "BillingCycle":"monthly",
            "AddonItems": [
                {
                    "Id":1,
                    "CatalogItemId":"C94271D8-B431-4A25-A3C5-A57737A1C909",
                    "Quantity":2,
                    "BillingCycle":"monthly"
                },
                {
                    "Id":2,
                    "CatalogItemId":"43FCE491-76D1-4BCC-B709-8A288786DBAE",
                    "Quantity":3,
                    "BillingCycle":"monthly"
                }
            ]
        }
    ]
}
```

### Request example (new base subscription) for a new commerce cart for a base offer with an add-on

```http
{
    "LineItems": [
        {
            "Id": 0,
            "CatalogItemId":"CFQ7TTC0LFLX:0001:CFQ7TTC0LB30", - Base
            "Quantity": 20,
            "BillingCycle": "Monthly",
            "TermDuration": "P1M"
        },
        {
            "Id": 1,
            "CatalogItemId":"CFQ7TTC0HDJX:0001:CFQ7TTC0K806", - Add on
            "Quantity": 20,
            "BillingCycle": "Monthly",
            "TermDuration": "P1M"
        }
    ]
}
```

#### Request example (existing base subscription) for traditional license-based

The following REST example shows how to append add-ons to an existing base subscription. This example is only relevant to traditional license-based, not new commerce.

```http
POST https://api.partnercenter.microsoft.com/v1/customers/18ac2950-8ea9-4dfc-92a4-ff4d4cd57796/carts HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 512a777a-5427-452d-9637-18421387e435
MS-CorrelationId: 182474ba-7303-4d0f-870a-8c7fba5ccc4b

{
    "LineItems": [
        {
            "Id":0,
            "CatalogItemId":"C94271D8-B431-4A25-A3C5-A57737A1C909",
            "Quantity":1,
            "BillingCycle":"annual",
            "ProvisioningContext":{"ParentSubscriptionId":"97555B61-7461-477A-A98C-9C76148783E4"}
        }
    ]
}
```

## REST response

If successful, this method returns the populated [Cart](cart-resources.md) resource in the response body.

#### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and more debugging information. Use a network trace tool to read this code, error type, and more parameters. For the full list, see [Error Codes](error-codes.md).

#### Response example (new base subscription) for traditional license-based

```http
HTTP/1.1 201 Created
Content-Length: 958
Content-Type: application/json
MS-CorrelationId: f73baf70-bbc3-43d0-8b29-dffa08ff9511
MS-RequestId: f931348a-6312-47d0-a8dd-31a386dedb8f
X-Locale: en-US,en-US
Date: Thu, 01 Nov 2018 22:29:05 GMT

{
    "id":"dbe2f8d4-f21d-43e2-9356-cff6387c4ba1",
    "creationTimestamp":"2018-11-01T22:29:03.6900182Z",
    "lastModifiedTimestamp":"2018-11-01T22:29:03.6900182Z",
    "expirationTimestamp":"2018-11-01T22:44:05.0025799Z",
    "lastModifiedUser":"1824b7fc-2fac-4478-b177-66823c40ab75",
    "status":"Active",
    "lineItems": [
        {
            "id":0,
            "catalogItemId":"91FD106F-4B2C-4938-95AC-F54F74E9A239",
            "friendlyName":"Myofferpurchase",
            "quantity":3,
            "currencyCode":"USD",
            "billingCycle":"monthly",
            "orderGroup":"OMS-0",
            "addonItems": [
                {
                    "id":1,
                    "catalogItemId":"C94271D8-B431-4A25-A3C5-A57737A1C909",
                    "quantity":2,
                    "currencyCode":"USD",
                    "billingCycle":"monthly",
                    "orderGroup":"OMS-0"
                },
                {
                    "id":2,
                    "catalogItemId":"43FCE491-76D1-4BCC-B709-8A288786DBAE",
                    "quantity":3,
                    "currencyCode":"USD",
                    "billingCycle":"monthly",
                    "orderGroup":"OMS-0"
                }
            ]
        }
],
    "links": {
        "self": {
            "uri":"/customers/18ac2950-8ea9-4dfc-92a4-ff4d4cd57796/carts/dbe2f8d4-f21d-43e2-9356-cff6387c4ba1",
            "method":"GET",
            "headers":[
            ]
        }
    },
    "attributes": {
        "objectType":"Cart"
    }
}
```

#### Response example (existing base subscription) for traditional license-based

```http
HTTP/1.1 201 Created
Content-Length: 707
Content-Type: application/json
MS-CorrelationId: 182474ba-7303-4d0f-870a-8c7fba5ccc4b
MS-RequestId: 512a777a-5427-452d-9637-18421387e435
X-Locale: en-US,en-US
Date: Thu, 01 Nov 2018 22:46:18 GMT

{
    "id":"4d927e27-93d1-448b-abe5-819b66ecca22",
    "creationTimestamp":"2018-11-01T22:46:16.2996364Z",
    "lastModifiedTimestamp":"2018-11-01T22:46:16.2996364Z",
    "expirationTimestamp":"2018-11-01T23:01:18.7543264Z",
    "lastModifiedUser":"1824b7fc-2fac-4478-b177-66823c40ab75",
    "status":"Active",
    "lineItems": [
        {
            "id":0,
            "catalogItemId":"C94271D8-B431-4A25-A3C5-A57737A1C909",
            "quantity":1,
            "currencyCode":"USD",
            "billingCycle":"annual",
            "provisioningContext": {
                "parentSubscriptionId":"97555B61-7461-477A-A98C-9C76148783E4"
            },
            "orderGroup":"OMS-0"
        }
    ],
    "links": {
        "self": {
            "uri":"/customers/18ac2950-8ea9-4dfc-92a4-ff4d4cd57796/carts/4d927e27-93d1-448b-abe5-819b66ecca22",
            "method":"GET",
            "headers":[
            ]
        }
    },
    "attributes": {
        "objectType":"Cart"
    }
}
```
#### Response example for a new commerce license-based base offer and add-on

```http
{
    "id": "ea37ea81-efaf-4113-9785-e1c266aea2ed",
    "creationTimestamp": "2022-02-10T16:04:22.4908435Z",
    "lastModifiedTimestamp": "2022-02-10T16:04:22.4908444Z",
    "expirationTimestamp": "2022-02-17T16:04:26.3085755Z",
    "lastModifiedUser": "a7155e79-65e3-42b0-a62a-a41297979782",
    "status": "Active",
    "lineItems": [
        {
            "id": 0,
            "catalogItemId": "CFQ7TTC0LFLX:0001:CFQ7TTC0LB30", - Base
            "quantity": 20,
            "currencyCode": "USD",
            "billingCycle": "monthly",
            "termDuration": "P1M",
            "promotionId": "39NFJQT1PHSN:0008:39NFJQT1Q5J0",
            "provisioningContext": {},
            "orderGroup": "0"
        },
        {
            "id": 1,
            "catalogItemId": "CFQ7TTC0HDJX:0001:CFQ7TTC0K806", - Add on
            "quantity": 20,
            "currencyCode": "USD",
            "billingCycle": "monthly",
            "termDuration": "P1M",
            "provisioningContext": {},
            "orderGroup": "0"
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/3a15e1df-b095-41d4-9029-27a5974c2458/carts/ea37ea81-efaf-4113-9785-e1c266aea2ed",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Cart"
    }
}
```