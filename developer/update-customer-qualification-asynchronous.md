---
title: Update a customer's qualifications
description: Updates a customer's qualifications asynchronously, including the address associated with the profile.
ms.date: 06/28/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: jischulz
ms.author: jischulz
---

# Update a customer's qualifications asynchronously

Updates a customer's qualifications asynchronously.

A partner can update a customer's qualifications asynchronously to be "Education", "GovernmentCommunityCloud" or "StateOwnedEntity". Other values such as "None" and "Nonprofit" cannot be set.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with App+User credentials only.

- A customer ID (`customer-tenant-id`). If you don't know the customer's ID, you can look it up in [Partner Center](https://partner.microsoft.com/dashboard) by selecting the **Customers** workspace, then the customer from the customer list, then **Account**. On the customer's Account page, look for the **Microsoft ID** in the **Customer Account Info** section. The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).

## C\#

To create a customer's qualification for "Education", First, create a `CustomerQualificationRequest` type object and specify the `Education` qualification type and the `EducationSegment`, along with a `Website` (optional). 

Then, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier.

Then use the [**Qualification**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) property to retrieve a [**ICustomerQualification**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) interface. 

Finally, call `CreateQualifications()` or `CreateQualificationsAsync()` with the `CustomerQualificationRequest` type object as the input parameter.

``` csharp
// Education
var eduRequestBody = new CustomerQualificationRequest 
{
    Qualification = "Education",
    EducationSegment = "K12", // could also be "HigherEducation"
    Website = "example.edu"
};

var eduCustomerQualification = partnerOperations.Customers.ById(existingCustomer.Id).Qualification.CreateQualifications(eduRequestBody);

// State Owned Entity
var soeRequestBody = new CustomerQualificationRequest 
{
    Qualification = "StateOwnedEntity"
};

var soeCustomerQualification = partnerOperations.Customers.ById(existingCustomer.Id).Qualification.CreateQualifications(soeRequestBody);
```

**Sample**: [Console Sample App](https://github.com/microsoft/Partner-Center-DotNet-Samples). **Project**: SdkSamples **Class**: CreateCustomerQualification.cs

To update a customer's qualification to **GovernmentCommunityCloud** on an existing customer without a qualification, the partner is also required to include the customer's validation code. 

First, create a `CustomerQualificationRequest` type object and specify the `GovernmentCommunityCloud` qualification type and the validation code. 

Then, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier.

Then use the [**Qualification**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) property to retrieve a [**ICustomerQualification**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) interface.

Finally, call `CreateQualifications()` or `CreateQualificationsAsync()` with the `CustomerQualificationRequest` type object as the input parameter.

``` csharp
var gccRequestBody = new CustomerQualificationRequest 
{
    Qualification = "GovernmentCommunityCloud",
    ValidationCode = "<validation code>"
};

var gccCustomerQualification = partnerOperations.Customers.ById(existingCustomer.Id).Qualification.CreateQualifications(gccRequestBody);
```

**Sample**: [Console Sample App](https://github.com/microsoft/Partner-Center-DotNet-Samples). **Project**: SdkSamples **Class**: CreateCustomerQualificationWithGCC.cs

## REST request

### Request syntax

| Method  | Request URI                                                                                             |
|---------|---------------------------------------------------------------------------------------------------------|
| **POST** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer_tenant_id}/qualifications HTTP/1.1 |

### URI parameter

Use the following query parameter to update the qualification.

| Name                   | Type | Required | Description                                                                                                                                            |
|------------------------|------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| **customer-tenant-id** | GUID | Yes      | The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller. |

### Request headers

For more information, see [Partner Center REST headers](headers.md).

### Request body

This table describes the qualification object in the request body.

Property | Type | Required | Description
-------- | ---- | -------- | -----------
Qualification | string | Yes | The string value from the [**CustomerQualification**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerqualification) enum.

This table describes request body for the *Education Qualification* specifically.

Property | Type | Required | Description
-------- | ---- | -------- | -----------
Qualification | string | Yes | Education
EducationSegment | string | Yes | K12, HigherEducation
Website | string | No | Website for the education entity

If the qualification is for **Education** then **Education segment** will be a required field.
- Allowed values for EducationSegment are **K12** and **HigherEducation**
- Website will remain an optional field, and is relevant only if the Qualification is for Education. However, including it if available/applicable is highly recommended

This table describes request body for the *GovernmentCommunityCloud Qualification* specifically.

Property | Type | Required | Description
-------- | ---- | -------- | -----------
Qualification | string | Yes | GovernmentCommunityCloud
ValidationCode | string | Yes | Partner's GCC validation code. Example - 123456

If the qualification is for **GovernmentCommunityCloud** then **ValidationCode** will be a required field.

>**Note**: The old contract will be supported for 90 days, after which this new contract will become mandatory. Partner Center SDK will be updated prior to the new request contract becoming mandatory.

### Request example

```http
POST https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/qualifications HTTP/1.1
Accept: application/json
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68

// SOE
{
    "qualification": "StateOwnedEntity"
}

// Education
{
    "qualification": "Education",
    "educationSegment": "HigherEducation", // could also be "K12"
    "website": "contoso.edu"
}

// GCC
{
    "qualification": "GovernmentCommunityCloud",
    "validationCode": "123456"
}

```

## REST response

If successful, this method returns a qualifications object in the response body. Below is an example of the **POST** call on a customer (with a previous qualification of **None**) with the **Education** qualification.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Error Codes](error-codes.md).

### Response example

```http
HTTP/1.1 201 CREATED
Content-Length: 29
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
{
    "qualification": "Education",
    "vettingStatus": "InReview",
    "vettingCreateDate": "2020-12-04T20:54:24Z" // UTC
}
```

## Related articles

- [Get a customer's qualifications](./get-customer-qualification-asynchronous.md)
- [Get a partner's validation codes](get-a-partner-s-validation-codes.md)
