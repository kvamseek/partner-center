---
title: Create a cart
description: Learn how to use Partner Center APIs to add an order for a customer in a cart. Topic includes information on creating a cart and any prerequisites.
ms.date: 12/09/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: iragulati1
ms.author: iragulati
---

# Create a cart with a customer order

**Applies to**: Partner Center | Partner Center operated by 21Vianet |  Partner Center for Microsoft Cloud for US Government

You can add an order for a customer in a cart. For more information about what is currently available to sell, see [Partner offers in the Cloud Solution Provider program](../csp-offers.md).

Please note, carts expire 7 days from initial creation.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with both standalone App and App+User credentials.

- A customer ID (`customer-tenant-id`). If you don't know the customer's ID, you can look it up in [Partner Center](https://partner.microsoft.com/dashboard) by selecting the **Customers** workspace, then the customer from the customer list, then **Account**. On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section. The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).

## C\#

To create an order for a customer:

1. Instantiate a Cart object.

2. Create a list of **CartLineItem** objects, and assign the list to the cart's LineItems property. Each cart line item contains the purchase information for one product. You must have at least one cart line item.

3. Obtain an interface to cart operations by calling the **IAggregatePartner.Customers.ById** method with the customer ID to identify the customer, and then retrieving the interface from the **Cart** property.

4. Call the **Create** or **CreateAsync** method to create the cart.

5. To complete attestation and include additional resellers please see the following sample Request and Response Samples:

### Request sample

```csharp

{
    "PartnerOnRecordAttestationAccepted":true,     "lineItems": [
        {
            "id": 0,
            "catalogItemId": "CFQ7TTC0LH0Z:0001:CFQ7TTC0K18P",
            "quantity": 1,
            "billingCycle": "monthly",
            "termDuration": "P1M",
            "renewsTo": null,
            "provisioningContext": {},
            "customTermEndDate": "2022-02-19T00:00:00Z"
        },
        {
            "id": 1,
            "catalogItemId": "CFQ7TTC0LFLS:0002:CFQ7TTC0KDLJ",
            "quantity": 2,
            "billingCycle": "monthly",
            "termDuration": "P1Y",
            "participants": [
                {
                    "key": "transaction_reseller",
                    "value": "5357564"
                },
                 {
                    "key": "additional_transaction_reseller",                     
                    "value": "517285"
                },
                 {
                    "key": "additional_transaction_reseller", 
                    "value": "5357563"
                }
            ]
        }
    ]
}


```

### Response sample

```csharp

{
    "id": "3e22b548-647d-4223-9675-1fcb6cb57665",
    "creationTimestamp": "2021-08-18T17:29:52.3517492Z",
    "lastModifiedTimestamp": "2021-08-18T17:29:52.3517553Z",
    "expirationTimestamp": "2021-08-25T17:30:11.2406416Z",
    "lastModifiedUser": "da62a0dc-35e9-4601-b48e-a047bd3ec7c1",
    "status": "Active",
    "lineItems": [
        {
            "id": 0,
            "catalogItemId": "CFQ7TTC0LH0Z:0001:CFQ7TTC0K18P",
            "quantity": 1,
            "currencyCode": "USD",
            "billingCycle": "monthly",
            "termDuration": "P1M",
	    "customTermEndDate": "2022-02-19T00:00:00Z";
            "provisioningContext": {},
            "orderGroup": "0"
        },
        {
            "id": 1,
            "catalogItemId": "CFQ7TTC0LFLS:0002:CFQ7TTC0KDLJ",
            "quantity": 2,
            "currencyCode": "USD",
            "billingCycle": "monthly",
            "termDuration": "P1Y",
            "participants": [
                {
                    "key": "transaction_reseller",
                    "value": "5357564"
                },
                {
                    "key": "additional_transaction_reseller", 
                    "value": "517285"
                },
                {
                    "key": "additional_transaction_reseller", 
                    "value": "5357563"
                }
            ],
            "provisioningContext": {},
            "orderGroup": "0"
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/f81d98dd-c2f4-499e-a194-5619e260344e/carts/3e22b548-647d-4223-9675-1fcb6cb57665",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Cart"
    }
}


```


### C\# example

```csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string subscriptionId;

var cart = new Cart()
{
    LineItems = new List<CartLineItem>()
    {
        new CartLineItem()
        {
      /* Microsoft Azure Subscription */
            Id = 0,
            CatalogItemId = "MS-AZR-0145P",
            Quantity = 1,
            BillingCycle = BillingCycleType.Monthly,
            TermDuration = "P1Y"
        },
        new CartLineItem()
        {
      /* Azure Reserved Instance */
            Id = 1,
            CatalogItemId = "DZH318Z0BQ36:004G:DZH318Z08C0S",
            Quantity = 1,
            BillingCycle = BillingCycleType.OneTime,
            TermDuration = "P1Y",
            ProvisioningContext = new Dictionary<string, string>
            {
                { "subscriptionId", subscriptionId },
                { "scope", "shared" }
            }
        },
        new CartLineItem()
        {
      /* Azure Reserved Instance */
            Id = 2,
            CatalogItemId = "DZH318Z0BQ36:004J:DZH318Z08B8X",
            Quantity = 1,
            BillingCycle = BillingCycleType.OneTime,
            TermDuration = "P3Y",
            ProvisioningContext = new Dictionary<string, string>
            {
                { "subscriptionId", subscriptionId },
                { "scope", "shared" }
            }
        },
        new CartLineItem()
        {
      /* Perpetual Software */
            Id = 3,
            CatalogItemId = "DG7GMGF0DWM3:0002:DG7GMGF0DT1M",
            Quantity = 1,
            BillingCycle = BillingCycleType.OneTime
        },
        new CartLineItem()
        {
      /* SaaS */
            Id = 4,
            CatalogItemId = "DZH318Z0BXWC:0002:DZH318Z0BMRV",
            Quantity = 1,
            BillingCycle = BillingCycleType.Monthly,
            TermDuration = "P1M"
        },
        new CartLineItem()
        {
      /* SaaS Free Trial */
            Id = 5,
            CatalogItemId = "DZH318Z0C0WF:0001:DZH318Z0BP69",
            Quantity = 10,
            BillingCycle = BillingCycleType.None,
            TermDuration = "P1M",
            RenewsTo = new RenewsTo
            {
                TermDuration = "P1Y"
            }
        }
    }
};

cart = partnerOperations.Customers.ById(customerId).Carts.Create(cart);
```

## Java

[!INCLUDE [Partner Center Java SDK support details](./includes/java-sdk-support.md)]

To create an order for a customer:

1. Instantiate a Cart object.

2. Create a list of **CartLineItem** objects, and assign the list to the cart's line items. Each cart line item contains the purchase information for one product. You must have at least one cart line item.

3. Obtain an interface to cart operations by calling the **IAggregatePartner.getCustomers().byId** function with the customer ID to identify the customer, and then retrieving the interface from the **getCart** function.

4. Call the **create** function to create the cart.

## Java example

```java
// IAggregatePartner partnerOperations;
// String customerId;
// String subscriptionId;
// String catalogItemId;

CartLineItem lineItem = new CartLineItem();

lineItem.setBillingCycle(BillingCycleType.OneTime);
lineItem.setCatalogItemId(catalogItemId);
lineItem.setFriendlyName("Sample RI Purchase");
lineItem.setQuantity(1);

Map<String, String> provisioningContext = new HashMap<String,String>();

provisioningContext.put("duration", "3Years");
provisioningContext.put("scope", "shared");
provisioningContext.put("subscriptionId", subscriptionId);

lineItem.setProvisioningContext(provisioningContext);

List<CartLineItem> lineItemList = new ArrayList<CartLineItem>();
lineItemList.add(lineItem);

Cart cart = new Cart();
cart.setLineItems(lineItemList);

Cart cartCreated = partnerOperations.getCustomers().byId(customerId).getCarts().create(cart);
```

## PowerShell

[!INCLUDE [Partner Center PowerShell module support details](./includes/powershell-module-support.md)]

To create an order for a customer:

1. Instantiate a Cart object.

2. Create a list of **CartLineItem** objects, and assign the list to the cart's line items. Each cart line item contains the purchase information for one product. You must have at least one cart line item.

3. Execute the [**New-PartnerCustomerCart**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/New-PartnerCustomerCart.md) command to create the cart.

```powershell
# $customerId
# $subscriptionId
# $catalogItemId

$lineItem = New-Object -TypeName Microsoft.Store.PartnerCenter.PowerShell.Models.Carts.PSCartLineItem

$lineItem.BillingCycle = 'OneTime'
$lineItem.CatalogItemId = $catalogItemId
$lineItem.FriendlyName = 'Sample RI Purchase'
$lineItem.ProvisioningContext.Add('duration', '1Year')
$lineItem.ProvisioningContext.Add('scope', 'shared')
$lineItem.ProvisioningContext.Add('subscriptionId', $subsciptionId)
$lineItem.Quantity = 10

New-PartnerCustomerCart -CustomerId $customerId -LineItems $lineItem
```

## REST request

### Request syntax

| Method   | Request URI                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| **POST** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/carts HTTP/1.1                        |

### URI parameter

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
| lineItems             | Array of objects | Yes             | An Array of [CartLineItem](cart-resources.md#cartlineitem) resources.                                     |
| PartnerOnRecordAttestationAccepted | Boolean | Yes | Confirms Attestation completion |

This table describes the [CartLineItem](cart-resources.md#cartlineitem) properties in the request body.

|      Property       |            Type             | Required |                                                                                         Description                                                                                         |
|---------------------|-----------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         id          |           string            |    No    |                                                     A unique identifier for a cart line item. Applied upon successful creation of cart.                                                     |
|      catalogId      |           string            |   Yes    |                                                                                The catalog item identifier. Ensure availabilty of the catalog item is for the correct segment.                                                                               |
|    friendlyName     |           string            |    No    |                                                    Optional. The friendly name for the item defined by the partner to help disambiguate.                                                    |
|      quantity       |             int             |   Yes    |                                                                            The number of licenses or instances.                                                                             |
|    currencyCode     |           string            |    No    |                                                                                     The currency code.                                                                                      |
|    billingCycle     |           Object            |   Yes    |                                                                    The type of billing cycle set for the current period.                                                                    |
|    customTermEndDate     |           DateTime            |   No    |                                                                    The end date of an existing subscription to which you want to coterminate the new subscription.   
|    participants     | List of Object String pairs |    No    |                                                                A collection of PartnerId on Record (PartnerID) on the purchase.                                                                 |
| provisioningContext | Dictionary<string, string>  |    No    | Information required for provisioning for some items in the catalog. The provisioningVariables property in a SKU indicates which properties are required for specific items in the catalog. |
|     orderGroup      |           string            |    No    |                                                                   A group to indicate which items can be placed together.                                                                   |
|        error        |           Object            |    No    |                                                                     Applied after cart is created if there is an error.                                                                      |
|     renewsTo        | Array of objects            |    No    |                                                    An array of [RenewsTo](cart-resources.md#renewsto) resources.                                                                            |
|     AttestationAccepted        | Boolean            |    No    |                                                   Indicates agreement to offer or sku conditions. Required only for offers or skus where SkuAttestationProperties or OfferAttestationProperties enforceAttestation is True.                                                                             |
|  transaction_reseller | String | No | When an indirect provider places an order on behalf of an indirect reseller, populate this field with the PartnerID of the **indirect reseller only** (never the ID of the indirect provider). This ensures proper accounting for incentives. |
| additional_transaction_reseller | String | No | When an indirect provider places an order on behalf of an indirect reseller, populate this field with the PartnerID of the **Additional indirect reseller only** (never the ID of the indirect provider). Incentives are not applicable for these additional resellers. Only a maximum of 5 Indirect Resellers can be entered. This is only applicable partners transacting within EU / EFTA countries/regions. |

This table describes the [RenewsTo](cart-resources.md#renewsto) properties in the request body.

| Property              | Type             | Required        | Description |
|-----------------------|------------------|-----------------|-------------------------------------------------------------------------------------------------------------------------|
| termDuration          | string           | No              | An ISO 8601 representation of the renewal term's duration. The current supported values are **P1M** (1 month) and **P1Y** (1 year). |

### Request example

```http
POST /v1/customers/d6bf25b7-e0a8-4f2d-a31b-97b55cfc774d/carts HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 4fa6dad6-a89f-4875-8247-8294a10ae1cf
MS-CorrelationId: 0e93c70c-977a-4a88-9580-7cf084c73286
X-Locale: en-US
MS-PartnerCenter-Client: Partner Center .NET SDK
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 496
Expect: 100-continue

{
  "lineItems": [
    {
    /* Microsoft Azure Subscription */
      "id": 0,
      "catalogItemId": "MS-AZR-0145P",
      "quantity": 1,
      "billingCycle": "monthly",
      "termDuration": "P1Y"
    },
    {
    /* Azure Reserved Instance */
      "id": 1,
      "catalogItemId": "DZH318Z0BQ36:004G:DZH318Z08C0S",
      "quantity": 1,
      "billingCycle": "one_time",
      "termDuration": "P1Y",
      "provisioningContext": {
        "subscriptionId": "1C461A25-F729-4FA5-AADB-280947DD05E8",
        "scope": "shared"
      }
    },
    {
    /* Azure Reserved Instance */
      "id": 2,
      "catalogItemId": "DZH318Z0BQ36:004J:DZH318Z08B8X",
      "quantity": 1,
      "billingCycle": "one_time",
      "termDuration": "P3Y",
      "provisioningContext": {
        "subscriptionId": "1C461A25-F729-4FA5-AADB-280947DD05E8",
        "scope": "single"
      }
    },
    {
    /* Perpetual Software */
      "id": 3,
      "catalogItemId": "DG7GMGF0DWTL:0001:DG7GMGF0DSFM",
      "quantity": 1,
      "billingCycle": "one_time"
    },
    {
    /* SaaS */
      "id": 4,
      "catalogItemId": "DZH318Z0BXWC:0002:DZH318Z0BMRV",
      "quantity": 1,
      "billingCycle": "monthly",
      "termDuration": "P1M"
    },
  {
    /* SaaS Free Trial */
       "id": 5,
       "catalogItemId": "DZH318Z0C0WF:0001:DZH318Z0BP69",
       "quantity": 10,
       "billingCycle": "none",
       "termDuration": "P1M",
       "renewsTo": {
         "termDuration": "P1Y"
       }
    }
  ]
}
```

> [!IMPORTANT]
> As of June 2023, the latest Partner Center .NET SDK release 3.4.0 is now archived. You can [download the SDK release from GitHub](https://github.com/microsoft/partner-center-sdk-for-dotNET), along with a [readme file](https://github.com/microsoft/partner-center-sdk-for-dotNET#readme) that contains useful information.
>
> Partners are encouraged to continue to use the [Partner Center REST APIs](partner-center-rest-api-reference.md).

## REST response

If successful, this method returns the populated [Cart](cart-resources.md) resource in the response body.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Error Codes](error-codes.md).

### Response example

```http
HTTP/1.1 201 Created
Content-Length: 764
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 0e93c70c-977a-4a88-9580-7cf084c73286
MS-RequestId: 4fa6dad6-a89f-4875-8247-8294a10ae1cf
X-Locale: en-US,en-US
MS-CV: sF/wRa2ih0CzbABc.0
MS-ServerId: 000001
Date: Thu, 15 Mar 2018 17:15:01 GMT
{
  "id": "3655b1a0-b1c9-4268-9824-577fdbc4d0be",
  "creationTimestamp": "2019-01-16T00:45:41.6062996Z",
  "lastModifiedTimestamp": "2019-01-16T00:45:41.6062996Z",
  "expirationTimestamp": "2019-01-16T01:00:54.4188497Z",
  "lastModifiedUser": "1824b7fc-2fac-4478-b177-66823c40ab75",
  "status": "Active",
  "lineItems": [
    {
      "id": 0,
      "catalogItemId": "MS-AZR-0145P",
      "quantity": 1,
      "currencyCode": "USD",
      "billingCycle": "monthly",
      "termDuration": "P1Y",
      "orderGroup": "OMS-0"
    },
    {
      "id": 1,
      "catalogItemId": "DZH318Z0BQ36:004G:DZH318Z08C0S",
      "quantity": 1,
      "currencyCode": "USD",
      "billingCycle": "one_time",
      "termDuration": "P1Y",
      "provisioningContext": {
        "subscriptionId": "1C461A25-F729-4FA5-AADB-280947DD05E8",
        "scope": "shared"
      },
      "orderGroup": "0"
    },
    {
      "id": 2,
      "catalogItemId": "DZH318Z0BQ36:004J:DZH318Z08B8X",
      "quantity": 1,
      "currencyCode": "USD",
      "billingCycle": "one_time",
      "termDuration": "P3Y",
      "provisioningContext": {
        "subscriptionId": "1C461A25-F729-4FA5-AADB-280947DD05E8",
        "scope": "shared"
      },
      "orderGroup": "0"
    },
    {
      "id": 3,
      "catalogItemId": "DG7GMGF0DWM3:0002:DG7GMGF0DT1M",
      "quantity": 1,
      "currencyCode": "USD",
      "billingCycle": "one_time",
      "orderGroup": "0"
    },
    {
      "id": 4,
      "catalogItemId": "DZH318Z0BXWC:0002:DZH318Z0BMRV",
      "quantity": 1,
      "currencyCode": "USD",
      "billingCycle": "monthly",
      "termDuration": "P1M",
      "orderGroup": "1"
    },
  {
      "id": 5,
      "catalogItemId": "DZH318Z0C0WF:0001:DZH318Z0BP69",
      "quantity": 10,
      "currencyCode": "USD",
      "billingCycle": "none",
      "termDuration": "P1M",
      "renewsTo": {
  "termDuration": "P1Y"
      },
    "orderGroup": "2"
    }
  ],
  "links": {
    "self": {
      "uri": "/customers/28045616-f6b9-462f-9701-0d89b5e65c44/carts/3655b1a0-b1c9-4268-9824-577fdbc4d0be",
      "method": "GET",
      "headers": []
    }
  },
  "attributes": {
    "objectType": "Cart"
  }
}
```


## Example for new commerce license-based services

> [!Note] 
> The new commerce experiences for license-based services include many new capabilities and are available to all Cloud Solution Provider (CSPs). For more information, see [new commerce experiences overview](../new-commerce-license-based.md).

### Request example

```http
POST /v1/customers/932c4101-dc08-461b-b4c1-75d80e905775/carts HTTP/1.1
Host: api.partnercenter.microsoft.com
Content-Type: application/json
Content-Length: 165

{
	"LineItems": [
		{
			"CatalogItemId":"CFQ7TTC0LFLZ:0002:CFQ7TTC0K4TS",
			"Quantity": 1,
			"TermDuration": "P1M",
            		"BillingCycle": "Monthly"
		}
	]
}

```

### REST response

If successful, this method returns the populated [Cart](cart-resources.md) resource in the response body.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Error Codes](error-codes.md).

### Response example

```http

{
    "id": "2517c51b-58cd-4abe-87ed-3ab812401ab4",
    "creationTimestamp": "2023-07-11T21:16:11.55149Z",
    "lastModifiedTimestamp": "2023-07-11T21:16:11.5515713Z",
    "expirationTimestamp": "2023-07-18T21:16:17.2480482Z",
    "lastModifiedUser": "9db12087-fbc3-481c-8965-73d44ff88e27",
    "status": "Active",
    "lineItems": [
        {
            "id": 0,
            "catalogItemId": "CFQ7TTC0LF8S:0001:CFQ7TTC0VZW5",
            "quantity": 1,
            "currencyCode": "USD",
            "billingCycle": "monthly",
            "termDuration": "P1Y",
            "provisioningContext": {},
            "orderGroup": "0",
            "pricing": {
                "listPrice": 30.4,
                "discountedPrice": 30.4,
                "proratedPrice": 30.4,
                "price": 30.4,
                "extendedPrice": 364.8
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/ebd8b4c2-4069-46a8-bd70-123d6dec3e39/carts/2517c51b-58cd-4abe-87ed-3ab812401ab4",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Cart"
    }
}



```
