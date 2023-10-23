---
title: Assign licenses to a user
description: Learn how to assign licenses to a customer user via Partner Center APIs, such as the use of C\# or REST APIs.
ms.date: 07/28/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: amitravat
ms.author: amrava
---

# Assign licenses to a user via Partner Center APIs

How to assign licenses to a customer user.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with App+User credentials only.

- A customer ID (`customer-tenant-id`). If you don't know the customer's ID, you can look it up in [Partner Center](https://partner.microsoft.com/dashboard) by selecting the **Customers** workspace, then the customer from the customer list, then **Account**. On the customer's Account page, look for the **Microsoft ID** in the **Customer Account Info** section. The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).

- A customer user identifier. This ID identifies the user to whom to assign the license.

- A product SKU identifier that identifies the product for the license.

## GDAP roles

You'll need at least one of the following GDAP roles:

- License Administrator
- User Administrator
- Directory Writers

## Assigning licenses through code

When you assign licenses to a user, you must choose from the customer's collection of subscribed SKUs. Then, having identified the products that you want to assign, you must obtain the product SKU ID for each product in order to make the assignments. Each [**SubscribedSku**](/dotnet/api/microsoft.store.partnercenter.models.licenses.subscribedsku) instance contains a [**ProductSku**](/dotnet/api/microsoft.store.partnercenter.models.licenses.subscribedsku.productsku) property from which you can reference the [**ProductSku**](/dotnet/api/microsoft.store.partnercenter.models.licenses.productsku) object and get the [**ID**](/dotnet/api/microsoft.store.partnercenter.models.licenses.productsku.id).

A license assignment request must contain licenses from a single license group. For example, you cannot assign licenses from [**Group1**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licensegroupid) and **Group2** in the same request. An attempt to assign licenses from more than one group in a single request will fail with an appropriate error. To find out what licenses are available by license group, see [Get a list of available licenses by license group](get-a-list-of-available-licenses-by-license-group.md).

Here are the steps to assign licenses through code:

1. Instantiate a [**LicenseAssignment**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment) object. You use this object to specify the product SKU and service plans to assign.

    ``` csharp
    LicenseAssignment license = new LicenseAssignment();
    ```

2. Populate the object properties as shown below. This code assumes that you already have the product SKU ID, and that all of the available service plans will be assigned (that is, none will be excluded).

    ```csharp
    license.SkuId = selectedProductSkuId;
    license.ExcludedPlans = null;
    ```

3. If you don't have the product SKU ID, you need to retrieve the collection of subscribed SKUs and get the product SKU ID from one of them. Here is an example if you know the product SKU name.

    ```csharp
    var customerSubscribedSkus = partnerOperations.Customers.ById(selectedCustomerId).SubscribedSkus.Get();
    var sku = customerSubscribedSkus.Items.Where(n => n.ProductSku.Name == "Office 365 Enterprise E3").First();
    license.SkuId = sku.ProductSku.Id;
    license.ExcludedPlans = null;
    ```

4. Next, instantiate a new list of type [**LicenseAssignment**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment), and add the license object. You can assign more than one license by adding each individually to the list. The licenses included in this list must be from the same license group.

    ```csharp
    List<LicenseAssignment> licenseList = new List<LicenseAssignment>();
    licenseList.Add(license);
    ```

5. Create a [**LicenseUpdate**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate) instance and assign the list of license assignments to the [**LicensesToAssign**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate.licensestoassign) property.

    ```csharp
    LicenseUpdate updateLicense = new LicenseUpdate();
    updateLicense.LicensesToAssign = licenseList;
    ```

6. Call the [**Create**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.createasync) method and pass the license update object as shown below to assign the licenses.

    ```csharp
    var assignLicense = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(selectedCustomerUserId).LicenseUpdates.Create(updateLicense);
    ```

## C\#

To assign a license to a customer user, first instantiate a [**LicenseAssignment**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment) object, and populate the [**Skuid**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment.skuid) and [**ExcludedPlans**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment.excludedplans) properties. You use this object to specify the product SKU to assign and service plans to exclude. Next, instantiate a new list of type **LicenseAssignment**, and add the license object to the list. Then create a [**LicenseUpdate**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate) instance and assign the list of license assignments to the [**LicensesToAssign**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate.licensestoassign) property.

Next, use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer, and the [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method with the user ID to identify the user. Then get an interface to customer user license update operations from the [**LicenseUpdates**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.licenseupdates) property.

Finally, call the [**Create**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.createasync) method and pass the license update object to assign the license.

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerUserId;
// string selectedCustomerId;
// string selectedProductSkuId;

// Instantiate and populate a LicenseAssignment object.
LicenseAssignment license = new LicenseAssignment();
license.SkuId = selectedProductSkuId;
license.ExcludedPlans = null;

// Instantiate a list of licenses to assign and add the license to it.
List<LicenseAssignment> licenseList = new List<LicenseAssignment>();
licenseList.Add(license);

// Instantiate a LicenseUpdate object and add the list of licenses to assign.
LicenseUpdate updateLicense = new LicenseUpdate();
updateLicense.LicensesToAssign = licenseList;

// Update the user licenses.
var assignLicense = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(selectedCustomerUserId).LicenseUpdates.Create(updateLicense);
```

**Sample**: [Console test app](console-test-app.md). **Project**: Partner Center SDK Samples **Class**: CustomerUserAssignLicenses.cs

## REST request

### Request syntax

| Method   | Request URI                                                                                                    |
|----------|----------------------------------------------------------------------------------------------------------------|
| **POST** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/users/{user-id}/licenseupdates HTTP/1.1 |

#### URI parameters

Use the following path parameters to identify the customer and user.

| Name        | Type   | Required | Description                                       |
|-------------|--------|----------|---------------------------------------------------|
| customer-id | string | Yes      | A GUID formatted ID that identifies the customer. |
| user-id     | string | Yes      | A GUID formatted ID that identifies the user.     |

### Request headers

For more information, see [Partner Center REST headers](headers.md).

### Request body

Include a [LicenseUpdate](license-resources.md#licenseupdate) resource in the request body that specifies the licenses to assign.

### Request example

```http
POST https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/users/554526aa-cf5e-46fa-95df-98dbc55d8a1e/licenseupdates HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: a37d3009-665d-4e12-b76e-1aa10cf80140
MS-CorrelationId: c73c9570-c352-459e-98a3-dafe4bd8c821
X-Locale: en-US
MS-PartnerCenter-Client: Partner Center .NET SDK
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 183
Expect: 100-continue

{
    "LicensesToAssign": [{
            "ExcludedPlans": null,
            "SkuId": "f8a1db68-be16-40ed-86d5-cb42ce701560"
        }
    ],
    "LicensesToRemove": null,
    "LicenseWarnings": null,
    "Attributes": {
        "ObjectType": "LicenseUpdate"
    }
}
```
> [!IMPORTANT]
> As of June 2023, the latest Partner Center .NET SDK release 3.4.0 is now archived. You can [download the SDK release from GitHub](https://github.com/microsoft/partner-center-sdk-for-dotNET), along with a [readme file](https://github.com/microsoft/partner-center-sdk-for-dotNET#readme) that contains useful information.
>
> Partners are encouraged to continue to use the [Partner Center REST APIs](partner-center-rest-api-reference.md).

## REST response

If successful, an HTTP response status code 201 is returned and the response body contains a [LicenseUpdate](license-resources.md#licenseupdate) resource with the license information.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Partner Center REST error codes](error-codes.md).

### Response example (success)

```http
HTTP/1.1 201 Created
Content-Length: 139
Content-Type: application/json; charset=utf-8
MS-CorrelationId: c73c9570-c352-459e-98a3-dafe4bd8c821
MS-RequestId: a37d3009-665d-4e12-b76e-1aa10cf80140
MS-CV: 5AnzcZQrvUqCq3kd.0
MS-ServerId: 030020525
Date: Thu, 20 Apr 2017 21:50:39 GMT

{
    "licensesToAssign": [{
            "skuId": "f8a1db68-be16-40ed-86d5-cb42ce701560"
        }
    ],
    "licenseWarnings": [],
    "attributes": {
        "objectType": "LicenseUpdate"
    }
}
```

### Response example (license isn't available)

```http
HTTP/1.1 400 Bad Request
Content-Length: 341
Content-Type: application/json; charset=utf-8
MS-CorrelationId: c73c9570-c352-459e-98a3-dafe4bd8c821
MS-RequestId: f4f3b748-8b22-4d07-a5a1-dceb32824192
MS-CV: 5npA0K22CUmWPOzB.0
MS-ServerId: 102030524
Date: Thu, 20 Apr 2017 22:12:36 GMT

{
    "code": 60012,
    "description": "We are sorry, it looks like you have run out of licenses. Buy more licenses, and then try again.",
    "data": ["LicenseQuotaExceededException : Subscription with Account 0c39d6d5-c70d-4c55-bc02-f620844f3fd1 and SKU f8a1db68-be16-40ed-86d5-cb42ce701560 does not have any available licenses left."],
    "source": "PartnerFD"
}
```

### Response example (invalid token)

```http
HTTP/1.1 400 Bad Request
Content-Length: 342
Content-Type: application/json; charset=utf-8
MS-CorrelationId: c5359db2-fb21-485c-90b1-0a2c3b484783
MS-RequestId: f0caf048-380c-4d6f-968a-3ccce01e11c1
MS-CV: 6npA0K22CUmWPOzC.0
MS-ServerId: 102045524
Date: Thu, 20 Apr 2023 21:12:36 GMT

{
    "code": 900316,
    "description": "Partner token is not allowed in license management calls. Please call with Partner Access Token. To learn more, see https://learn.microsoft.com/partner-center/developer/enable-secure-app-model#get-access-token",
    "source": "PartnerFD"
}
```


### Response example (Conditional Access Policy Issue)

```http
HTTP/1.1 403 Forbidden
Content-Length: 342
Content-Type: application/json; charset=utf-8
MS-CorrelationId: c5359db2-fb21-485c-90b1-0a2c3b484783
MS-RequestId: f0caf048-380c-4d6f-968a-3ccce01e11c1
MS-CV: 6npA0K22CUmWPOzC.0
MS-ServerId: 102045524
Date: Thu, 20 Apr 2023 21:12:36 GMT

{
    "code": 900309,
    "description": "Access has been blocked by Conditional Access policies. The access policy does not allow token issuance. Learn more at https://learn.microsoft.com/azure/active-directory/conditional-access/concept-conditional-access-users-groups.",
    "source": "PartnerFD"
}
```
