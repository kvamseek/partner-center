---
title: Update report API
ms.topic: reference
ms.date: 07/14/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-insights
description:  Use this API to update report parameters  in Partner Center insights.
author: kshitishsahoo
ms.author: ksahoo
---
# Update report API

This API helps you modify a report parameter.

## Request syntax

|    Method    |    Request URI    |
|    ----    |    ----    |
|    PUT    |    `https://api.partnercenter.microsoft.com/insights/v1/mpn/ScheduledReport/{Report ID}`    |
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
|    reportId     |    string    |    No    |    ID of the report being modified     |
|        |        |        |        |

## Query parameter

None

## Request payload

```json
{
  "ReportName": "string",
  "Description": "string",
  "StartTime": "string",
  "RecurrenceInterval": 0,
  "RecurrenceCount": 0,
  "Format": "string",
  "CallbackUrl": "string",
 "CallbackMethod": "string"
}
```

## Request glossary

This table lists the key definitions of elements in the response.

|    Parameter    |    Required    |    Description    |    Allowed Values    |
|    ----    |    ----    |    ----    |    ----    |
|    ReportName     |    Yes     |    Name to be assigned to the report     |    String     |
|    Description     |    No     |    Description of the created report     |    String     |
|    StartTime     |    Yes    |    Timestamp after which the report generation will begin     |    String     |
|    RecurrenceInterval     |    No     |    Frequency at which the report should be generated in hours. Minimum value is 4     |    Integer     |
|    RecurrenceCount     |    No     |    Numbers of report to be generated. Default is indefinite.     |    Integer     |
|    Format     |    No    |    File format of the exported file. Default is CSV     |    CSV/TSV     |
|    CallbackURL     |    No     |    https callback URL to be called on report generation     |    String     |
|    CallbackMethod    |    No    |    Http method to be used for callback    |    GET/POST    |
|        |        |        |        |

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
|    ReportId     |    Universally unique identifier (UUID) of the report being updated     |
|    ReportName     |    Name given to the report in the request payload     |
|    Description     |    Description given to the report in the request payload     |
|    QueryId     |    Query ID passed at the time the report was created     |
|    Query     |    Query text that will be executed for this report     |
|    User     |    User ID used to create the report     |
|    CreatedTime     |    Time the report was created. The time format is yyyy-MM-ddTHH:mm:ssZ     |
|    ModifiedTime     |    Time the report was last modified. The time format is yyyy-MM-ddTHH:mm:ssZ     |
|    ExecuteNow     |    ExecuteNow flag set at the time the report was created    |
|    StartTime     |    Time the report execution will begin. The time format is yyyy-MM-ddTHH:mm:ssZ     |
|    ReportStatus     |    Status of the report execution. The possible values are Paused, Active, and Inactive.     |
|    RecurrenceInterval     |    Recurrence interval provided in the request payload     |
|    RecurrenceCount     |    Recurrence count provided in the request payload     |
|    CallbackUrl     |    Callback URL provided in the request     |
|    CallbackMethod    |    Callback method provided in the request    |
|    Format     |    Format of the report files     |
|    TotalCount     |    Number of datasets in the Value array     |
|    Message     |    Status message from the execution of the API     |
|    StatusCode     |    Result Code. The possible values are 200, 400, 401, 403, 500     |
|        |        |
