---
title: Get all datasets API - Insights data
ms.topic: reference
ms.date: 07/14/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-insights
description:  Use this API to get details of all available datasets in Partner Center insights.
author: kshitishsahoo
ms.author: ksahoo
---
# Get all datasets API

The Get all datasets API gets all the available datasets. Datasets list the tables, columns, metrics, and time ranges.

## Request syntax

|    Method    |    Request URI    |
|    ----    |    ----    |
|    GET    |    `https://api.partnercenter.microsoft.com/insights/v1/mpn/ScheduledDataset?datasetName={Dataset Name}`     |
|        |        |

## Request header

|    Header    |    Type    |    Description    |
|    ----    |    ----    |    ----    |
|    Authorization    |    string    |    Required. The Microsoft Azure Active Directory (Azure AD) access token in the form `Bearer <token>`    |
|    Content-Type    |    string    |    `Application/JSON`    |
|        |        |        |

## Path parameter

None

## Query parameter

|    Parameter Name    |    Type    |    Required    |    Description    |
|    ----    |    ----    |    ----    |    ----    |
|    datasetName    |    string    |    No    |    Filter to get details of only one dataset    |
|        |        |        |        |

## Request payload

None

## Request glossary

None

## Response

The response payload is structured as follows:

Response code: 200, 400, 401, 403, 404, 500

Response payload example:

```json
{
   "Value":[
      {
         "DatasetName ":"string",
         "SelectableColumns":[
            "string"
         ],
         "AvailableMetrics":[
            "string"
         ],
         "AvailableDateRanges":[
            "string"
         ],
         "minimumRecurrenceInterval":0
      }
   ],
   "TotalCount":0,
   "Message":"<Error Message>",
   "StatusCode": 0,
}
```

## Response glossary

This table defines the key elements in the response:

|    Parameter    |    Description    |
|    ----    |    ----    |
|    DatasetName     |    Name of the dataset that this array object defines     |
|    SelectableColumns     |    Raw columns that can be specified in the select columns     |
|    AvailableMetrics     |    Aggregation/metric column names that can be specified in the select columns     |
|    AvailableDateRanges     |    Date range that can be used in report queries for the dataset     |
|    minimumRecurrenceInterval     |    Minimum value of Recurrence Interval     |
|    TotalCount     |    Number of datasets in the Value array     |
|    Message     |    Status message from the execution of the API     |
|    StatusCode     |    Result Code. The possible values are 200, 400, 401, 403, 500     |
|        |        |
