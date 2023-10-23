---
title: Reset user password for a customer
description: Resetting a password is similar to updating other details in an existing user account for your customer.
ms.date: 07/28/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: amitravat
ms.author: amrava
---

# Reset user password for a customer

Resetting a password is similar to updating other details in an existing user account for your customer.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with App+User credentials only.

- A customer ID (`customer-tenant-id`). If you don't know the customer's ID, you can look it up in [Partner Center](https://partner.microsoft.com/dashboard). Select the **Customers** workspace from the Partner Center Home page. Select the customer from the **Customer list**, then select **Account**. On the customer's Account page, look for the Microsoft ID in the **Customer Account details section**. The Microsoft ID is the same as the customer ID (`customer-tenant-id`).

## GDAP roles

You'll need at least one of the following GDAP roles:

- User Administrator
- Privileged Authentication Administrator

### C\#

To reset a password for a specified customer user, first retrieve the specified customer ID and the targeted user. Then, create a new **CustomerUser** object that contains the information for the existing customer, but with a new **PasswordProfile** object. Then, use your **IAggregatePartner.Customers** collection and call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid?view=partnercenter-dotnet-latest#microsoft-store-partnercenter-customers-icustomercollection-byid(system-string)&preserve-view=true) method. Then call the **Users** property, the **ById()** method, and then the **Patch** method.

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// CustomerUser specifiedUser;

var selectedCustomer = partnerOperations.Customers.ById(selectedCustomerId).Get();
var userToUpdate = new CustomerUser()
   {
      PasswordProfile = new PasswordProfile() { ForceChangePassword = true, Password = "newPassword" },
      DisplayName = "Roger Federer",
      FirstName = "Roger",
      LastName = "Federer",
      UsageLocation = "US",
      UserPrincipalName = Guid.NewGuid().ToString("N") + "@" + selectedCustomer.CompanyProfile.Domain.ToString()
   };

// update customer user information
User updatedCustomerUserInfo = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(specifiedUser.Id).Patch(userToUpdate);

```

#### Example

[Console test app](console-test-app.md). **Project**: PartnerSDK.FeatureSamples **Class**: CustomerUserUpdate.cs

### REST request

#### Request syntax

| Method    | Request URI                                                                                  |
|-----------|----------------------------------------------------------------------------------------------|
| **PATCH** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users/{user-id}/resetpassword HTTP/1.1 |

#### URI parameter

Use the following query parameter to identify the correct customer.

| Name                   | Type     | Required | Description                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| **customer-tenant-id** | **guid** | Y        | The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller. |
| **user-id**            | **guid** | Y        | The value is a GUID formatted **user-id** that belongs to a single user account.                                                                       |

#### Request headers

For more information, see [Partner Center REST headers](headers.md).

#### Request example

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/users/<user-id>/resetpassword HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: b1317092-f087-471e-a637-f66523b2b94c
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
{
     "passwordProfile":{
        password: "Renew456*",
        forceChangePassword: true
      },

      "attributes": {
        "objectType": "CustomerUser"
      }
}
```

#### REST response

If successful, this method returns the user information, along with the updated password information.

#### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Error Codes](error-codes.md).

#### Response example

```http
HTTP/1.1 200 OK
Content-Length: 31942
Content-Type: application/json
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
MS-RequestId: b1317092-f087-471e-a637-f66523b2b94c
Date: June 24 2016 22:00:25 PST
{
  "usageLocation": "AX",
  "id": "95794928-9abe-4548-8b43-50ffc20b9404",
  "userPrincipalName": "aaaa4@abcdefgh1234.ccsctp.net",
  "firstName": "aaaa4",
  "lastName": "aaaa4",
  "displayName": "aaaa4",
  "passwordProfile": {
    "forceChangePassword": false,
    "password": "Renew456*"
  },
  "lastDirectorySyncTime": null,
  "userDomainType": "none",
  "state": "active",
  "softDeletionTime": null,
  "links": {
    "self": {
      "uri": "/customers/eebd1b55-5360-4438-a11d-5c06918c3014/users/95794928-9abe-4548-8b43-50ffc20b9404",
      "method": "GET",
      "headers": [

      ]
    }
  },
  "attributes": {
    "objectType": "CustomerUser"
  }
}
```
