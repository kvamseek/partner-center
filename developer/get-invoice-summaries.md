---
title: Get invoice summaries
description: You can use an invoice summaries resource for each currency type to show the balance and total charges of both recurring and one-time charges.
ms.date: 6/3/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: sourishdeb
ms.author: sodeb
---

# Get invoice summaries

**Applies to**: Partner Center | Partner Center operated by 21Vianet |  Partner Center for Microsoft Cloud for US Government

You can use the **InvoiceSummaries** to retrieve an invoice summary that shows the balance and total charges of both recurring and one-time charges. The **InvoiceSummaries** resource contains an invoice summary for each currency type.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with App+User credentials only.

- A valid invoice identifier.

## C\#

To retrieve an [**InvoiceSummaries**](invoice-resources.md#invoicesummaries) collection that contains an [**InvoiceSummary**](invoice-resources.md#invoicesummary) for each currency type:

1. Use your **IAggregatePartner.Invoices** collection to call the **Summaries** property.

2. Call the **Get()** method.
3. To get the balance of an individual [**InvoiceSummary**](invoice-resources.md#invoicesummary), access the **BalanceAmount** property for that member of the collection.

``` csharp
// IAggregatePartner scopedPartnerOperations;

// Get the invoice summaries collection.
var invoiceSummaries = scopedPartnerOperations.Invoices.Summaries.Get();

// Display the balance on the first invoice summary in the collection.
Console.Out.WriteLine("Current Account Balance:  {0:C}", invoiceSummaries[0].BalanceAmount);
```

For more information, see the following example code:

- Sample: [Console test app](console-test-app.md)
- Project: **PartnerSDK.FeatureSample**
- Class: **GetInvoiceSummaries.cs**

## REST request

### Request syntax

| Method  | Request URI                                                                   |
|---------|-------------------------------------------------------------------------------|
| **GET** | [*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/summaries HTTP/1.1     |

#### URI parameter

None.

### Request headers

For more information, see [Partner Center REST headers](headers.md).

### Request body

None.

### Request example

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/summaries HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: a45e6643-1caf-4429-8f90-07c03d85bc2b
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
Connection: Keep-Alive
```

## REST response

If successful, this method returns an [**InvoiceSummaries**](invoice-resources.md#invoicesummaries) resource in the response body.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Error Codes](error-codes.md).

### Response example

```http
HTTP/1.1 200 OK
Content-Length: 256
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
MS-RequestId: a45e6643-1caf-4429-8f90-07c03d85bc2b
Date: Thu, 24 Mar 2016 05:21:01 GMT

{
    "totalCount": 3,
    "items": [
        {
            "balanceAmount": 751094.39,
            "currencyCode": "GBP",
            "currencySymbol": "£",
            "accountingDate": "2018-03-16T00:00:00",
            "firstInvoiceCreationDate": "2017-01-21T00:00:00Z",
            "lastPaymentDate": "2017-01-01T12:00:00Z",
            "lastPaymentAmount": 1000,
            "latestInvoiceDate": "2018-03-16T00:00:00",
            "details": [
                {
                    "invoiceType": "Recurring",
                    "summary": {
                        "balanceAmount": 202955.87,
                        "currencyCode": "GBP",
                        "currencySymbol": "£",
                        "accountingDate": "2017-02-27T00:00:00Z",
                        "firstInvoiceCreationDate": "2017-01-21T00:00:00Z",
                        "lastPaymentDate": "2017-01-01T12:00:00Z",
                        "lastPaymentAmount": 1000,
                        "latestInvoiceDate": "0001-01-01T00:00:00",
                        "attributes": {
                            "objectType": "InvoiceSummary"
                        }
                    }
                },
                {
                    "invoiceType": "OneTime",
                    "summary": {
                        "balanceAmount": 548138.52,
                        "currencyCode": "GBP",
                        "currencySymbol": "£",
                        "accountingDate": "2018-03-16T00:00:00",
                        "firstInvoiceCreationDate": "2018-03-16T00:00:00",
                        "lastPaymentDate": "0001-01-01T00:00:00",
                        "lastPaymentAmount": 0,
                        "latestInvoiceDate": "2018-03-16T00:00:00",
                        "attributes": {
                            "objectType": "InvoiceSummary"
                        }
                    }
                }
            ],
            "links": {
                "self": {
                    "uri": "/invoices/summary",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "InvoiceSummary"
            }
        },
        {
            "balanceAmount": 1230.33,
            "currencyCode": "CHF",
            "currencySymbol": "CHF",
            "accountingDate": "2018-03-16T00:00:00",
            "firstInvoiceCreationDate": "2018-03-16T00:00:00",
            "lastPaymentDate": "0001-01-01T00:00:00",
            "lastPaymentAmount": 0,
            "latestInvoiceDate": "2018-03-16T00:00:00",
            "details": [
                {
                    "invoiceType": "OneTime",
                    "summary": {
                        "balanceAmount": 1230.33,
                        "currencyCode": "CHF",
                        "currencySymbol": "CHF",
                        "accountingDate": "2018-03-16T00:00:00",
                        "firstInvoiceCreationDate": "2018-03-16T00:00:00",
                        "lastPaymentDate": "0001-01-01T00:00:00",
                        "lastPaymentAmount": 0,
                        "latestInvoiceDate": "2018-03-16T00:00:00",
                        "attributes": {
                            "objectType": "InvoiceSummary"
                        }
                    }
                }
            ],
            "links": {
                "self": {
                    "uri": "/invoices/summary",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "InvoiceSummary"
            }
        },
        {
            "balanceAmount": 1001.12,
            "currencyCode": "EUR",
            "currencySymbol": "€",
            "accountingDate": "2018-03-16T00:00:00",
            "firstInvoiceCreationDate": "2018-03-16T00:00:00",
            "lastPaymentDate": "0001-01-01T00:00:00",
            "lastPaymentAmount": 0,
            "latestInvoiceDate": "2018-03-16T00:00:00",
            "details": [
                {
                    "invoiceType": "OneTime",
                    "summary": {
                        "balanceAmount": 1001.12,
                        "currencyCode": "EUR",
                        "currencySymbol": "€",
                        "accountingDate": "2018-03-16T00:00:00",
                        "firstInvoiceCreationDate": "2018-03-16T00:00:00",
                        "lastPaymentDate": "0001-01-01T00:00:00",
                        "lastPaymentAmount": 0,
                        "latestInvoiceDate": "2018-03-16T00:00:00",
                        "attributes": {
                            "objectType": "InvoiceSummary"
                        }
                    }
                }
            ],
            "links": {
                "self": {
                    "uri": "/invoices/summary",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "InvoiceSummary"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/invoices/summaries",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
