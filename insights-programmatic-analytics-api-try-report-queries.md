---
title: Try report queries API
ms.topic: reference
ms.date: 07/14/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-insights
description:  Use this API to test your query and validate the results in Partner Center insights.
author: kshitishsahoo
ms.author: ksahoo
---
# Try report queries API

This API executes a Report query statement. The API returns only 100 records that you as a partner can use to verify if the data is as you expected.

> [!IMPORTANT]
> This API has a query execution timeout of 100 seconds. If you notice the API is taking more than 100 seconds, it is highly likely that the query is syntactically correct or else you would have received an error code other than 200. The actual report generation will pass if the query syntax is correct.

## Request syntax

|    Method    |    Request URI    |
|    ----    |    ----    |
|    GET    |    `https://api.partnercenter.microsoft.com/insights/v1/mpn/ScheduledQueries/testQueryResult?<exportQuery={querytext}\|queryId={queryId}>`    |
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
|    exportQuery     |    string    |    No    |    Report query string that needs to be executed     |
|    queryId     |    string    |    No    |    A valid existing query ID. Mutually exclusive with query string specified in exportQuery parameter    |
|    startTime     |    string    |    No    |    Start time from which we want the data. It overrides timespan specified in the query    |
|    endTime     |    string    |    No    |    End time till which we want the data. It overrides timespan specified in the query    |
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
Top 100 rows of query execution
{
  "Value": [
    {
    }
  ],
  "TotalCount": 0,
  "Message": "string",
  "StatusCode": 0,
}
```

## Response glossary

This table defines the key elements in the response:

|    Parameter    |    Description    |
|    ----    |    ----    |
|    TotalCount     |    Number of datasets in the Value array     |
|    Message     |    Status message from the execution of the API     |
|    StatusCode     |    Result Code. The possible values are 200, 400, 401, 403, 500     |
|        |        |
