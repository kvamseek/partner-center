---
title: Confirm customer acceptance of Microsoft Customer Agreement
description: Learn how to confirm customer acceptance of the Microsoft Customer Agreement using Partner Center APIs.
ms.date: 07/28/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: jischulz
ms.author: jischulz
---

# Confirm customer acceptance of the Microsoft Customer Agreement using Partner Center APIs

**Applies to**: Partner Center

**Does not apply to**: Partner Center operated by 21Vianet |  Partner Center for Microsoft Cloud for US Government

Partner Center currently supports confirmation of customer acceptance of the Microsoft Customer Agreement only in the Microsoft public cloud.

This article describes how to confirm or reconfirm customer acceptance of the Microsoft Customer Agreement.

## Prerequisites

- If you are using the Partner Center .NET SDK, version 1.14 or newer is required.

> [!IMPORTANT]
> As of June 2023, the latest Partner Center .NET SDK release 3.4.0 is now archived. You can [download the SDK release from GitHub](https://github.com/microsoft/partner-center-sdk-for-dotNET), along with a [readme file](https://github.com/microsoft/partner-center-sdk-for-dotNET#readme) that contains useful information.
>
> Partners are encouraged to continue to use the [Partner Center REST APIs](partner-center-rest-api-reference.md).

- Credentials as described in [Partner Center authentication](./partner-center-authentication.md). *This scenario only supports App+User authentication.*

- A customer ID (`customer-tenant-id`). If you don't know the customer's ID, you can look it up in [Partner Center](https://partner.microsoft.com/dashboard) by selecting the **Customers** workspace, then the customer from the customer list, then **Account**. On the customer's Account page, look for the **Microsoft ID** in the **Customer Account Info** section. The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).

- The date (**dateAgreed**) when the customer accepted the Microsoft Customer Agreement.

- Information about the user from the customer organization that accepted the Microsoft Customer Agreement. This includes:
  - First name
  - Last name
  - Email address
  - Phone number (optional)
- If the following values change for a customer, Partner Center  will allow for another agreement to be created for that customer:
        First Name
        Last Name
        Email address
        Phone number
Otherwise partners will receive the following error code, due to a duplicate customer being created


```
{
"code": 600061,
"message": "A partner confirmed agreement already exists for the customer.",
"description": "A partner confirmed agreement already exists for the customer.",
"errorName": "PartnerConfirmedAgreementAlreadyExists",
"isRetryable": false,
"parameters": {},
"errorMessageExtended": "InternalErrorCode=600061"
}
 ```

## .NET

To confirm or reconfirm customer acceptance of the Microsoft Customer Agreement:

1. Retrieve the agreement metadata for the Microsoft Customer Agreement. You must obtain the **templateId** of the Microsoft Customer Agreement. For more information, see [Get agreement metadata for Microsoft Customer Agreement](get-customer-agreement-metadata.md).

   ```csharp
   // IAggregatePartner partnerOperations;

   string agreementType = "MicrosoftCustomerAgreement";

   var microsoftCustomerAgreementDetails = partnerOperations.AgreementDetails.ByAgreementType(agreementType).Get().Items.Single();
   ```

2. Create a new **Agreement** object containing details of the confirmation.

3. Use the **IAgreggatePartner.Customers** collection and call the **ById** method with the specified **customer-tenant-id**.

4. Use the **Agreements** property, followed by calling **Create** or **CreateAsync**.

   ```csharp
   // string selectedCustomerId;

   var agreementToCreate = new Agreement
   {
       DateAgreed = DateTime.UtcNow,
       TemplateId = microsoftCustomerAgreementDetails.TemplateId,
       PrimaryContact = new Contact
       {
           FirstName = "Tania",
           LastName = "Carr",
           Email = "someone@example.com",
           PhoneNumber = "1234567890"
       }
   };

   Agreement agreement = partnerOperations.Customers.ById(selectedCustomerId).Agreements.Create(agreementToCreate);
   ```

A complete sample can be found in the [CreateCustomerAgreement](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/CreateCustomerAgreement.cs) class from the [console test app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) project.

## REST request

To confirm or reconfirm customer acceptance of the Microsoft Customer Agreement:

1. Retrieve the agreement metadata for the Microsoft Customer Agreement. You must obtain the **templateId** of the Microsoft Customer Agreement. For more information, see [Get agreement metadata for Microsoft Customer Agreement](get-customer-agreement-metadata.md).

2. Create a new [**Agreement** resource](agreement-resources.md) to confirm that a customer has accepted the Microsoft Customer Agreement. Use the following [REST request syntax](#request-syntax).

### Request syntax

| Method | Request URI                                                                                        |
|--------|----------------------------------------------------------------------------------------------------|
| POST   | [*\{baseURL\}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/agreements HTTP/1.1 |

#### URI parameter

Use the following query parameter to specify the customer that you're confirming.

| Name               | Type | Required | Description                                                                                 |
|--------------------|------|----------|---------------------------------------------------------------------------------------------|
| customer-tenant-id | GUID | Yes | The value is a GUID-formatted **customer-tenant-id**, which is an identifier that allows you to specify a customer. |

### Request headers

For more information, see [Partner Center REST headers](headers.md).

### Request body

This table describes the required properties in the REST request body.

| Name      | Type   | Description                                                                                  |
|-----------|--------|----------------------------------------------------------------------------------------------|
| Agreement | object | Details provided by partner to confirm customer acceptance of the Microsoft Customer Agreement. |

#### Agreement

This table describes the minimum required fields to create an [**Agreement** resource](agreement-resources.md).

| Property       | Type   | Description                              |
|----------------|--------|------------------------------------------|
| primaryContact | [Contact](./utility-resources.md#contact) | Information about the user from the customer organization who accepted the Microsoft Customer Agreement, including:  **firstName**, **lastName**, **email**, and **phoneNumber** (optional) |
| dateAgreed     | string in UTC date time format |The date when the customer accepted the agreement. |
| templateId     | string | Unique identifier of the agreement type accepted by the customer. You can obtain the **templateId** for Microsoft Customer Agreement by retrieving the agreement metadata for Microsoft Customer Agreement. See [Get agreement metadata for Microsoft Customer Agreement](./get-customer-agreement-metadata.md) for details. |
| type           | string | Agreement type accepted by the customer. Use "MicrosoftCustomerAgreement" if customer accepted the Microsoft Customer Agreement. |

#### Request example

```http
POST https://api.partnercenter.microsoft.com/v1/customers/14876998-c0dc-46e6-9d0c-65a57a6c32ec/agreements HTTP/1.1
Authorization: Bearer <token>
Content-Type: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
{
    "primaryContact": {
        "firstName": "Tania",
        "lastName": "Carr",
        "email": "someone@example.com",
        "phoneNumber": "1234567890"
    },
    "templateId": "117a77b0-9360-443b-8795-c6dedc750cf9",
    "dateAgreed": "2018-06-14T00:00:00.000Z",
    "type": "MicrosoftCustomerAgreement"
}
```

## REST response

If successful, this method returns an [**Agreement** resource](./agreement-resources.md).

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information.

Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Partner Center REST error codes](error-codes.md).

#### Response example

```http
HTTP/1.1 201 Created
Content-Length: 261
Content-Type: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
{
    "userId": "3d6f2c09-eb40-48ca-a4b3-d24c9c007531",
    "primaryContact": {
        "firstName": "Tania",
        "lastName": "Carr",
        "email": "someone@example.com",
        "phoneNumber": "1234567890"
    },
    "templateId": "117a77b0-9360-443b-8795-c6dedc750cf9",
    "dateAgreed": "2018-06-14T00:00:00.000Z",
    "type": "MicrosoftCustomerAgreement"
}
```
