---
title: Control Panel Vendor APIs for customer consent
description: Learn about Partner Center APIs that you can use as a Control Panel Vendor to get and delete customer consent.
ms.date: 08/01/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: JulCsc
ms.author: shishir
---

# Get customer consent as Control Panel Vendor

As a Control Panel Vendor (CPV), you can use REST APIs to acquire and remove consent from your CSP customers to get permissions into their tenants.

```http
POST https://api.partnercenter.microsoft.com/v1/customers/{<customer_id>}/applicationconsents
```

> [!NOTE]
> The rate limit is 50 requests per second (RPS) for each applicationId (Application ID of the CPV partner).

## Acquire consent

### URI parameters

| Name        | In | Required | Type | Description                                |
|-------------|----|--------------|----------|------------------------------------------------|
| customer_id | path   | True         | string   | ID of the customer generated in Partner Center |

### Request header

Media types: `application/json`

| Name         | Required | Type | Description                                                                                                                   |
|------------------|--------------|----------|-----------------------------------------------------------------------------------------------------------------------------------|
| Authorization    | True         | string   | Access Token for audience `https://api.partnercenter.microsoft.com`                     |
| Accept           | True         | string   | Acceptable content type; widely accepted type application/json                                                                   |
| ms-correlationid |              | string   | Used for tracking requests internally. If a ms-correlationid isn't provided, the server generates a new one for each request |
| ms-requestid     |              | string   | Used for idempotency of requests. If a ms-requestid isn't provided, the server generates a new one for each request          |

### Request body

Media types: `application/json`

| Name              | Type                                                          | Description                                                                     |
|-------------------|---------------------------------------------------------------|---------------------------------------------------------------------------------|
| applicationId     | string                                                        | Application ID of the CPV partner                                               |
| applicationGrants | Microsoft.Partner.Core.ApplicationConsents.ApplicationGrant[] | List of application grants to get the access for your customers in their tenant |

### Responses

| Name                      | Type | Description                                                                                                                                                                                  |
|---------------------------|------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 200 OK                    |      | The request succeeded. Media Types: `application/json`, `application/xml`, `text/xml`, `text/json`                                                                                           |
| 201 Created               |      | The application consent is created. Media Types: `application/json`, `application/xml`, `text/xml`, `text/json`                                                                              |
| 400 Bad Request           |      | There was missing or invalid input. The response body contains the error details. Media Types: `application/json`, `application/xml`, `text/xml`, `text/json`                                |
| 401 Unauthorized          |      | The request wasn't authenticated. The client needs to pass a valid access token for valid audience. Media Types: `application/json`, `application/xml`, `text/xml`, `text/json`             |
| 403 Forbidden             |      | The request was authenticated but was refused because the caller doesn't have the rights to invoke it. Media Types: `application/json`, `application/xml`, `text/xml`, `text/json`          |
| 404 Not Found             |      | The resource isn't found or not available with the given input parameters. Media Types: `application/json`, `application/xml`, `text/xml`, `text/json`                                      |
| 500 Internal Server Error |      | The partner API service or one of its dependencies failed to fulfill the request. Callers can retry the request. Media Types: `application/json`, `application/xml`, `text/xml`, `text/json` |

### Definitions

`Microsoft.Partner.Core.ApplicationConsents.ApplicationGrant`

| Name                    | Type   | Description                                            |
|-------------------------|--------|--------------------------------------------------------|
| enterpriseApplicationId | string | The GUID representation of the resource gaining access |
| scope                   | string | Comma separated values of the scope for gaining access |

## Remove consent

```http
DELETE https://api.partnercenter.microsoft.com/v1/customers/{customer_id}/applicationconsents/{application_id}
```

> [!NOTE]
> The rate limit is 50 requests per second (RPS) for each applicationId (Application ID of the CPV partner). 

### URI parameters

| Name           | In | Required | Type | Description                                |
|--------------------|--------|--------------|----------|------------------------------------------------|
| customer_id    | path   | True         | string   | ID of the customer generated in Partner Center |
| Application_id | path   | True         | string   | ID of your CPV application                     |

### Request header

Media types: `application/json`

| Name             | Required     | Type     | Description                                                                                                                       |
|------------------|--------------|----------|------------------------------------------------------------|
| Authorization    | True         | string   | Access token for audience `https://api.partnercenter.microsoft.com`                     |
| Accept           | True         | string   | Acceptable content type, usually type application/json                          |
| ms-correlationid |              | string   | Used for tracking requests internally. If a `ms-correlationid` isn't provided, the server generates a new one for each request |
| ms-requestid     |              | string   | Used for idempotency of requests. If a ms-requestid isn't provided, the server generates a new one for each request          |

### Responses

| Name                      | Type     | Description                                                         |
|---------------------------|----------|-----------------------------------------------------------------------------------------------------|
| 200 OK                    |          | The request succeeded. Media Types: `application/json`, `application/xml`, `text/xml`, `text/json`                                                                                           |
| 201 Created               |          | The application consent is deleted. Media Types: `application/json`, `application/xml`, `text/xml`, `text/json`                                                                              |
| 400 Bad Request           |          | There was missing or invalid input. The response body contains the error details. Media Types: `application/json`, `application/xml`, `text/xml`, `text/json`                                |
| 401 Unauthorized          |          | The request wasn't authenticated. The client needs to pass a valid access token for valid audience. Media Types: `application/json`, `application/xml`, `text/xml`, `text/json`             |
| 403 Forbidden             |          | The request was authenticated but was refused because the caller doesn't have the rights to invoke it. Media Types: `application/json`, `application/xml`, `text/xml`, `text/json`          |
| 404 Not Found             |          | The resource isn't found or not available with the given input parameters. Media Types: `application/json`, `application/xml`, `text/xml`, `text/json`                                      |
| 500 Internal Server Error |          | The partner API service or one of its dependencies failed to fulfill the request. Callers can retry the request. Media Types: `application/json`, `application/xml`, `text/xml`, `text/json` |

## Next steps

- [Confirm customer consent of the customer agreement](./confirm-customer-consent-customer-agreement.md)
