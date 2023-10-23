---
title: Retrieve validation status of a customer
description: How to retrieve the validation status of a customer.
ms.author: alikhaki
author: khakiali
ms.date: 10/27/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
---

# Retrieve the validation status of a customer

A partner can retrieve the status of a customer validation upon demand.

### Prerequisites

- Established credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with App+User credentials only.

- A customer ID (customer-tenant-id). If you don't know the customer's ID, you can look it up in [Partner Center](https://partner.microsoft.com/dashboard) by selecting the **Customers** workspace, then the customer from the customer list, then **Account**. On the customer's Account page, look for the **Microsoft ID** in the **Customer Account Info** section. The Microsoft ID is the same as the customer ID (customer-tenant-id).

## C\#

To retrieve a customer's validation status for their account, first create an enum representing the [**ValidationType**](/dotnet/api/microsoft.store.partnercenter.models.validationstatus.enums.validationtype) to retrieve. Then, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier. Then, use the [**ValidationStatus**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.validationstatus) property to retrieve a [**IValidationStatus**](/dotnet/api/microsoft.store.partnercenter.validationstatus.ivalidationstatus) interface. Finally, call `GetValidationStatus()` or `GetValidationStatusAsync()` with the validation type enum variable as an input parameter.

``` csharp
var validationTypeToFetch = ValidationType.Account;
var eduCustomerQualification = partnerOperations.Customers.ById(existingCustomer.Id).ValidationStatus.GetValidationStatus(validationTypeToFetch);
```

**Sample**: [Console Sample App](https://github.com/microsoft/Partner-Center-DotNet-Samples). **Project**: SdkSamples **Class**: GetValidationStatus.cs

## REST Request

### Request syntax 
|    Method    |  URI         |
|:------|:--------------------|
| GET   | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/validationStatus?type=account |   

#### URI parameter
Use the following query parameter to specify the customer you are retrieving validation status for.

|    Name    |  Type         | Required | Description      |
|:------|:-------------------|:---------|:-----------|
| {customer-id} | guid       |   Y      | The value is a GUID formatted CustomerTenantId that allows you to specify a customer. |
| type | string | Y | The type of validation status to retrieve. |

### Request headers
For more information, see [Partner Center REST headers](headers.md).

## REST response
Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Partner Center REST error codes](error-codes.md).


### Response fields
|    Field    |  Type         | Description | Notes      |
|:------|:-------------------|:---------|:-----------|
| Type | Enum       |  Validation information type      | Same data as *validation-type*. Validation type returns *account* as the response type. |
| Status  |  	Enum |	Validation status  |Available statuses: Unknown, UnderReview, Allowed, NotAllowed, Not Ready |
|Latest Update Time	|string|	last status update time in UTC | |

### Response examples

#### Allowed status

``` HTTP
{
    "type": "account",
    "status": "Allowed",
    "lastUpdateDateTime": "2021-07-14T18:02:00"
}
```
#### In review status
``` HTTP
{
    "type": "account",
    "status": "UnderReview",
    "lastUpdateDateTime": "2021-07-14T18:02:00"
}
```

#### NotAllowed status
``` HTTP 
{
    "type": "account",
    "status": "NotAllowed",
    "lastUpdateDateTime": "2021-07-14T18:02:00"
}
```

#### Unknown status
``` HTTP
{
    "type": "account",
    "status": "Unknown",
    "lastUpdateDateTime": "2021-07-14T18:02:00"
}
```
#### Not Ready status
```HTTP
{
    "type": "account",
    "status": "Not Ready",
    "lastUpdateDateTime": "2021-07-14T18:02:00"
}
```

#### 404 not found error
``` HTTP
{
    "code": 600074,
    "message": "Account Status for the customer, {customer-id} was not found.",
    "description": "Account Status for the customer, {customer-id} was not found.",
    "errorName": "AccountStatusNotFound",
    "isRetryable": false,
    "errorMessageExtended": "InternalErrorCode=600074"
```
#### Purchase eligibility
Customer's transactions will be blocked when their account has any of the statuses below:
* UnderReview
* NotAllowed
* Unknown

Customer's transactions won't be blocked when they meet the following conditions:
* Customer has an Allowed status
* Customer doesn't have account status
