---
title: Resume report execution API - Insights data
ms.topic: reference
ms.date: 07/14/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-insights
description:  Use this API to resume execution of any paused report in Partner Center insights.
author: kshitishsahoo
ms.author: ksahoo
---
# Resume report executions API

On execution, this API resumes the scheduled execution of a paused report.

## Request syntax

|    Method    |    Request URI    |
|    ----    |    ----    |
|    PUT    |    `https://api.partnercenter.microsoft.com/insights/v1/mpn/ScheduledReport/resume/{ReportID}`    |

## Request header

|    Header    |    Type    |    Description    |
|    ----    |    ----    |    ----    |
|    Authorization    |    string    |    Required. The Microsoft Azure Active Directory (Azure AD) access token in the form `Bearer <token>`    |
|    Content-Type    |    string    |    `Application/JSON`    |

## Path parameter

|    Parameter Name    |    Type    |    Required    |    Description    |
|    ----    |    ----    |    ----    |    ----    |
|    reportId     |    string    |    No    |    ID of the report being modified     |

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
      "ReportId": "string",
      "ReportName": "string",
      "Description": "string",
      "QueryId": "string",
      "Query": "string",
      "User": "string",
      "CreatedTime": "string",
      "ModifiedTime": "string",
      "ExecuteNow": true,
      "StartTime": "string",
      "ReportStatus": "string",
      "RecurrenceInterval": 0,
      "RecurrenceCount": 0,
      "CallbackUrl": "string",
      "CallbackMethod": "string",
      "Format": "string"
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
|    ReportId     |    Universally unique identifier (UUID) of the resumed report     |
|    ReportName     |    Name given to the report during creation     |
|    Description     |    Description given during creation of the report     |
|    QueryId     |    Query ID passed at the time the report was created     |
|    Query     |    Query text that will be executed for this report     |
|    User     |    User ID used to create the report     |
|    CreatedTime     |    Time the report was created. The time format is yyyy-MM-ddTHH:mm:ssZ     |
|    ModifiedTime     |    Time the report was last modified. The time format is yyyy-MM-ddTHH:mm:ssZ     |
|    ExecuteNow     |    ExecuteNow flag set at the time the report was created    |
|    StartTime     |    Time the report execution will begin. The time format is yyyy-MM-ddTHH:mm:ssZ     |
|    ReportStatus     |    Status of the report execution. The possible values are Paused, Active, and Inactive.     |
|    RecurrenceInterval     |    Recurrence interval provided during report creation     |
|    RecurrenceCount     |    Recurrence count provided during report creation     |
|    CallbackUrl     |    Callback URL provided in the request     |
|    CallbackMethod    |    Callback method provided in the request    |
|    Format     |    Format of the report files     |
|    TotalCount     |    Number of datasets in the Value array     |
|    Message     |    Status message from the execution of the API     |
|    StatusCode     |    Result Code. The possible values are 200, 400, 401, 403, 500     |
