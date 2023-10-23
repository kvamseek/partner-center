---
title: Delete report queries API - Insights data
ms.topic: reference
ms.date: 07/14/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-insights
description:  Use this API to delete user defined query in Partner Center insights.
author: kshitishsahoo
ms.author: ksahoo
---
# Delete report queries API

This API deletes user-defined queries.

## Request syntax

|    Method    |    Request URI    |
|    ----    |    ----    |
|    DELETE    |    `https://api.partnercenter.microsoft.com/insights/v1/mpn/ScheduledQueries/{queryId}` |
|        |        |

## Request header

|    Header    |    Type    |    Description    |
|    ----    |    ----    |    ----    |
|    Authorization    |    string    |    Required. The Microsoft Azure Active Directory (Azure AD) access token in the form `Bearer <token>`    |
|    Content-Type    |    string    |    `Application/JSON`    |
|        |        |        |

## Path parameter

|    Parameter Name    |    Type    |    Required    |    Description    |
|    ----    |    ----    |    ----    |    ----    |
|    queryId     |    string     |    No    |    Filter to get details of only queries with the ID given in the argument     |
|        |        |        |        |

## Query parameter

None

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
  "Value": [
    {
      "QueryId": "string",
      "Name": "string",
      "Description": "string",
      "Query": "string",
      "Type": "string",
      "User": "string",
      "CreatedTime": "string",
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
|    QueryId     |    Unique UUID of the query that was deleted    |
|    Name     |    Name of the query that was deleted    |
|    Description     |    Description of the deleted query     |
|    Query     |    Report query string of the deleted query    |
|    Type     |    Set to userDefined for user created queries     |
|    User     |    User ID who created the query     |
|    CreatedTime     |    Time of creation of query     |
|    TotalCount     |    Number of datasets in the Value array     |
|    Message     |    Status message from the execution of the API     |
|    StatusCode     |    Result Code. The possible values are 200, 400, 401, 403, 500     |
|        |        |
