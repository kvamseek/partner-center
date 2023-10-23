---
title: Get custom term end dates
description: How to get custom term end dates for a new customer subscription
ms.date: 07/18/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: iragulati1
ms.author: iragulati
---

# Get custom term end dates

**Applies to**: Partner Center | Partner Center operated by 21Vianet |  Partner Center for Microsoft Cloud for US Government

Partners can view allowed custom term end dates for NCE license-based subscriptions they are purchasing for their customers. Partners can view end dates that align with the end of the calendar month or that co-term with existing customer subscriptions.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with both standalone App and App+User credentials.

- A CustomerTenantId. If you don't know the customer's ID, you can look it up in [Partner Center](https://partner.microsoft.com/dashboard) by selecting the **Customers** workspace, then the customer from the customer list, then **Account**. On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section. The Microsoft ID is the same as the customer ID.

## REST request

### Request syntax

| Method  | Request URI                                                                                                      |
|---------|------------------------------------------------------------------------------------------------------------------|
| **GET** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customerId}/subscriptions/customTermEndDates            |

### Query Strings

This table lists the query strings needed to filter and retrieve custom term end dates. Inputting multiple IDs to query is accepted but not required.

| Name                            | Required | Description                                                             |
|---------------------------------|----------|-------------------------------------------------------------------------|
| TermDuration                    | Yes      | A GUID-formatted string that identifies the customer.                   |
| TermStartDate                   | No       | A GUID-formatted string that identifies a migrated legacy subscription. |
| TargetCotermSubscriptionId      | No       | A GUID-formatted string that identifies the migration batch.            |

### Request headers

For more information, see [Partner Center REST headers](headers.md). The response of the API returns a maximum of 300 page records. If over 300 records are returned in an inputted query, a continuation token will be provided in the response header. The continuation token can be input in the header of a following request to return additional page records queried.

### Request body

None.

## REST response

If successful, this method returns details of the [Subscriptions](subscription-resources.md) that were migrated (migration object) in the response body. This includes the migration ID.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Partner Center REST error codes](error-codes.md).

### Request URL examples

```http
baseurl/v1/customers/94cd6638-11b6-4323-8c9f-6ae3088adc59/subscriptions/customTermEndDates?term_duration=P1M
```

### Response examples

```http
 {​
    "totalCount": 2,​
    "items": [​
        {​
            "allowedCustomTermEndDateType": "calendarMonthAligned",​
            "allowedCustomTermEndDate": "2023-07-31T00:00:00"​
        },​
        {​
            "allowedCustomTermEndDateType": "subscriptionAligned",​
            "cotermSubscriptionIds": [​
               "5fcf618b-1daa-4604-da99-cc3e1c9ee422",​
               "d30a9ff9-713e-4546-c97e-f06b9dcf6ef6"​
            ],​
            "allowedCustomTermEndDate": "2023-08-01T00:00:00"​
        }​
    ],​
    "links": {​
        "self": {​
            "uri": "/customers/94cd6638-11b6-4323-8c9f-6ae3088adc59/subscriptions/customTermEndDates?term_duration=P1M",​
            "method": "GET",​
            "headers": []​
        }​
    },​
    "attributes": {​
        "objectType": "Collection"​
    }​
 }
```
