---
title: Programmatic access paradigm for insights data
description: Understand the High-level flow of the API call pattern for programmatic analytics. The APIs for accessing partner insights analytics reports are also covered.
ms.topic: article
ms.service: partner-dashboard
ms.subservice: partnercenter-insights
author: kshitishsahoo
ms.author: ksahoo
ms.date: 8/1/2022
---

# Programmatic access paradigm

This diagram shows the API call pattern used to create a new report template, schedule the custom report, and retrieve failure data.

:::image type="content" source="media/insights/prog-acc-paradigm.png" lightbox="media/insights/prog-acc-paradigm.png" alt-text="High-level flow":::
***Figure 1: High-level flow of the API call pattern***

This list provides more details about Figure 1.

1. The Client Application can define the custom report schema/template by calling the [Create Report Query API](#create-report-query-api). Alternatively, you can pick a report template (QueryId) from the report template library samples at [List of system queries for partner insights programmatic access](insights-programmatic-system-queries.md).
2. On success, the Create Report Query API returns the QueryId.
3. The client application then needs to call the [Create Report API](#create-report-api) using the QueryId along with the report start date, Repeat Interval, Recurrence, and an optional Callback URI.
4. On Success, the [Create Report API](#create-report-api) returns the ReportId.
5. The client application gets notified at the callback URL as soon as the report data is ready for download.
6. The client application then uses the [Get Report Executions API](#get-report-execution-api) to query the status of the report with the Report ID and date range.
7. On success, the report download link is returned and the application can initiate download of the data.

## Report query language specification

While we do provide [system queries](insights-programmatic-system-queries.md) you can use to create reports, you can also create your own queries based on your business needs. To learn more about custom queries, see [Custom Query Specification](insights-programmatic-custom-query.md).

## Create report query API

The API helps to create custom queries that define the dataset from which columns and metrics need to be exported. The API provides the flexibility to create a new reporting template based on your business needs.

You can also use the [system queries](insights-programmatic-system-queries.md) we provide. When custom report templates are not needed, you can call [Create Report API](#create-report-api) directly using the QueryIds of the system queries that are provided.

The following example shows how to create a custom query to get top 10 customers by revenue for last month.

### Request syntax

|    Method     |    Request URI     |
|----- | -----|
|    POST     |    `https://api.partnercenter.microsoft.com/insights/v1/mpn/ScheduledQueries`|

### Request header

|    Header     |    Type     |    Description     |
|-------|-----|------|
|    Authorization     |    string |Required. The Azure Active Directory (Azure AD) access token. The format is `Bearer <token>`.|
|    Content-Type     |string |`Application/JSON` |

### Path parameter

None

### Query parameter

None

### Sample request payload

```json
{
  "Name": "CustomersRevenueQuery",
  "Description": "Query to get top 10 customers by revenue for last month",
  "Query": "SELECT CustomerName, Product, BilledRevenueUSD FROM CustomersAndTenants ORDER BY BilledRevenueUSD LIMIT 10 TIMESPAN LAST_MONTH"
}
```

### Request glossary

This table provides the key definitions of elements in the request payload.

|Parameter|    Required     |    Description     |    Allowed Values     |
|-----|    -----    |    -----    |    -----    |
|Name |    Yes     |    Friendly name of the query     |    string     |
|    Description     |    No     |    Description of what the query returns     |    string     |
|    Query     |    Yes     |    Report query string     |    Data type: string <br> [Custom query](insights-programmatic-custom-query.md) based on business need |
|        |        |        |        |

> [!NOTE]
> For custom query samples, see [Examples of sample queries.](insights-programmatic-sample-queries.md)

### Sample response

The response payload is structured as follows:

Response Codes: 200, 400, 401, 403, 500

Response payload example:

```json
{
  "value": [
    {
      "queryId": "ec8366a4-d96e-4194-8c37-d5dbc0639033",
      "name": "CustomersRevenueQuery",
      "description": "Query to get top 10 customers by revenue for last month",
      "query": "SELECT CustomerName, Product, BilledRevenueUSD FROM CustomersAndTenants ORDER BY BilledRevenueUSD LIMIT 10 TIMESPAN LAST_MONTH",
      "type": "userDefined",
      "user": "GAUser@PITEST2.ccsctp.net",
      "createdTime": "2021-03-30T12:52:39Z"
    }
  ],
  "nextLink": null,
  "totalCount": 1,
  "message": "Query created successfully",
  "statusCode": 200,
  "dataRedacted": false
}
```

### Response glossary

This table provides the key definitions of elements in the request payload.

|    Parameter     |    Description     |
|    ----    |    ----    |
|    QueryId     |    Universally unique identifier (UUID) of the query you created     |
|    Name     |    Friendly name given to the query in the request payload     |
|    Description     |    Description given during creation of the query     |
|    Query     |    Report query passed as input during query creation     |
|    Type     |    Set to `userDefined`     |
|    User     |    User ID used to create of the query     |
|    CreatedTime     |    UTC Time the query was created in this format: yyyy-MM-ddTHH:mm:ssZ     |
|    TotalCount     |    Number of datasets in the Value array     |
|    StatusCode     |    Result Code <br> The possible values are 200, 400, 401, 403, 500     |
|    message     |    Status message from the execution of the API     |
|        |        |

## Create report API

On creating a custom report template successfully and receiving the QueryID as part of [Create Report Query](#create-report-query-api) response, this API can be called to schedule a query to be executed at regular intervals. You can set a frequency and schedule for the report to be delivered.
For system queries we provide, the Create Report API can also be called with [QueryId](insights-programmatic-system-queries.md).

### Callback URL

The create report API accepts a callback URL. This URL will be called once the report generation is successful. The callback URL should be publicly reachable. In addition to the URL, a callback method can also be given. The callback method can only be "GET" or "POST". The default method if no value is passed will be "POST". The reportId that has completed generation will always be passed back during the callback.

POST callback: If the URL passed was `https://www.contosso.com/callback`, then the called back URL will be `https://www.contosso.com/callback/<reportID>`

GET callback: If the URL passed was `https://www.contosso.com/callback`, then the called back URL will be `https://www.contosso.com/callback?reportId=<reportID>`

### ExecuteNow reports

There is a provision to generate a report without scheduling. The report create API payload can accept a parameter `ExecuteNow`, which will enqueue the report to be generated as soon as the API is called. When `ExecuteNow` is set to true, the fields: `StartTime`, `RecurrenceCount`, `RecurrenceInterval` are ignored as these reports are not scheduled.

Two additional fields can be passed when `ExecuteNow` is true, `QueryStartTime` and `QueryEndTime`. These two fields will override the `TIMESPAN` field in the query. These fields are not applicable for scheduled reports as data will get continuously generated for a fixed time period that does not change.

### Request syntax

|    Method     |    Request URI     |
|----- | -----|
|    POST     |`https://api.partnercenter.microsoft.com/insights/v1/mpn/ScheduledReport` |

### Request header

|    Header     |    Type     |    Description     |
|-------|-----|------|
|    Authorization     |    string |Required. The Azure Active Directory (Azure AD) access token. The format is `Bearer <token>`.|
|    Content-Type     |string |`Application/JSON` |

### Path Parameter

None

### Query Parameter

None

### Sample request payload

```json
{
  "ReportName": "Top10_CustomersReport",
  "Description": "Top 10 customers by revenue for last month",
  "QueryId": "ec8366a4-d96e-4194-8c37-d5dbc0639033",
  "StartTime": "2021-03-31T18:41:00Z",
  "ExecuteNow": false,
  "QueryStartTime": null,
  "QueryEndTime": null,
  "RecurrenceInterval": 24,
  "RecurrenceCount": 100,
  "Format": "CSV",
  "CallbackUrl": "https://<SampleCallbackUrl>",
  "CallbackMethod": "GET"
}
```

### Glossary

Key definitions of elements in the request payload are articulated below:

|    Parameter     |    Required     |    Description     |    Allowed Values     |
|    ----    |    ----    |    ----    |    ----    |
|    ReportName     |    Yes     |    Name to be assigned to the report     |    string     |
|    Description     |    No     |    Description of the created report     |    string     |
|    QueryId     |    Yes     |    Report query ID     |    string     |
|    StartTime     |    Yes     |    UTC Timestamp at which the report generation will begin. <br> The format should be: yyyy-MM-ddTHH:mm:ssZ       |    string     |
|    ExecuteNow     |    No     |    This parameter should be used to create a report that will be executed only once. `StartTime`, `RecurrenceInterval`, and `RecurrenceCount` are ignored if this is set to true. The report is executed immediately in an asynchronous fashion     |    true/false     |
|    QueryStartTime     |    No     |    Optionally specifies the start time for the query extracting the data. This parameter is applicable only for one-time execution reports that have `ExecuteNow` set to true. Setting this parameter overrides `TIMESPAN` given in the query. The format should be yyyy-MM-ddTHH:mm:ssZ     |    Timestamp as string     |
|    QueryEndTime     |    No     |    Optionally specifies the end time for the query extracting the data. This parameter is applicable only for one time execution report that have `ExecuteNow` set to true. Setting this parameter overrides `TIMESPAN` given in the query. The format should be yyyy-MM-ddTHH:mm:ssZ     |    Timestamp as string     |
|    RecurrenceInterval     |    Yes     |    Frequency in hours at which the report should be generated. <br> Minimum value is 4 and Maximum value is 2160.      |    integer     |
|    RecurrenceCount     |    No     |    Number of reports to be generated.     |    integer     |
|    Format     |    No     |    File format of the exported file. <br> Default is CSV.    |    "CSV"/"TSV"     |
|    CallbackUrl     |    No     |    Publicly reachable URL that can be optionally configured as callback destination     |    String (http URL)     |
|    CallbackMethod     |    No     |    The method to be used for callback     |    GET/POST     |
|        |        |        |        |

### Sample response

The response payload is structured as follows:

Response Codes: 200, 400, 401, 403, 404, 500

Response payload example:

```json
{
  "value": [
    {
      "reportId": "d9548477-16d4-492a-bf9c-0cf91a9f69bf",
      "reportName": "Top10_CustomersReport",
      "description": "Top 10 customers by revenue for last month",
      "queryId": "ec8366a4-d96e-4194-8c37-d5dbc0639033",
      "query": "SELECT CustomerName, Product, BilledRevenueUSD FROM CustomersAndTenants ORDER BY BilledRevenueUSD LIMIT 10 TIMESPAN LAST_MONTH",
      "user": "GAUser@PITEST2.ccsctp.net",
      "createdTime": "2021-03-30T13:11:58Z",
      "modifiedTime": null,
      "executeNow": false,
      "startTime": "2021-03-31T18:41:00Z",
      "reportStatus": "Active",
      "recurrenceInterval": 24,
      "recurrenceCount": 100,
      "callbackUrl": "https://<SampleCallbackUrl>",
      "callbackMethod": "GET",
      "format": "csv"
    }
  ],
  "nextLink": null,
  "totalCount": 1,
  "message": "Report created successfully",
  "statusCode": 200,
  "dataRedacted": false
}
```

### Glossary

Key definitions of elements in the response are articulated below:

|    Parameter     |    Description     |
|    ----    |    ----    |
|    ReportId     |    Universally unique identifier (UUID) of the report you created     |
|    ReportName     |    Name given to the report in the request payload     |
|    Description     |    Description given during creation of the report     |
|    QueryId     |    Query ID passed at the time you created the report     |
|    Query     |    Query text that will be executed for this report     |
|    User     |    User ID used to create the report     |
|    CreatedTime     |    UTC Time the report was created in this format: yyyy-MM-ddTHH:mm:ssZ     |
|    ModifiedTime     |    UTC Time the report was last modified in this format: yyyy-MM-ddTHH:mm:ssZ     |
|    ExecuteNow     |    `ExecuteNow` flag set at the time the report was created     |
|    StartTime     |    UTC Time the report execution will begin in this format: yyyy-MM-ddTHH:mm:ssZ     |
|    ReportStatus     |    Status of the report execution. The possible values are `Paused`, `Active`, and `Inactive`     |
|    RecurrenceInterval     |    Recurrence interval provided during report creation     |
|    RecurrenceCount     |    Recurrence count provided during report creation.      |
|    CallbackUrl     |    Callback URL provided in the request     |
|    CallbackMethod     |    Callback method provided in the request     |
|    Format     |    Format of the report files. The possible values are `CSV` or `TSV`.     |
|    TotalCount     |    Number of records in the Value array     |
|    StatusCode     |    Result Code     |
|    message     |    The possible values are 200, 400, 401, 403, 500. Status message from the execution of the API     |
|        |        |

## Get report execution API

You can use this method to query the status of a report execution using the ReportId received from [Create Report API](#create-report-api). The method returns the report download link if the report is ready for download. Otherwise, the method returns the status. You can also use this API to get all the executions that have happened for a given report.

> [!IMPORTANT]
>This API has default query parameters set for `executionStatus=Completed` and `getLatestExecution=true`. Hence, calling the API before the first successful execution of the report will return 404. Pending executions can be obtained by setting `executionStatus=Pending`.

### Request syntax

|    Method     |    Request URI     |
|----- | -----|
|    GET    |`https://api.partnercenter.microsoft.com/insights/v1/mpn/ScheduledReport/execution/{reportId}?executionId={executionId}&executionStatus={executionStatus}&getLatestExecution={getLatestExecution}`  |

### Request header

|    Header     |    Type     |    Description     |
|-------|-----|------|
|    Authorization     |    string |Required. The Azure Active Directory (Azure AD) access token. The format is `Bearer <token>`.|
|    Content-Type     |string |`Application/JSON` |

### Path parameter

|    Parameter Name    |    Required    |    Type    |    Description    |
|    ----    |    ----    |    ----    |    ----    |
|    reportId    |    Yes    |    string    |    Filter to get execution details of only reports with the reportId given in this argument. Multiple reportIds can be specified by separating them with a semicolon ";".    |
|        |        |        |        |

### Query parameter

|    Parameter Name    |    Required    |    Type    |    Description    |
|    ----    |    ----    |    ----    |    ----    |
|    executionId    |    No    |    string    |    Filter to get details of only reports with the executionId given in this argument. Multiple executionIds can be specified by separating them with a semicolon ";".    |
|    executionStatus    |    No    |    String/enum    |    Filter to get details of only reports with the executionStatus given in this argument. <br> Valid values are: `Pending`, `Running`, `Paused`, and `Completed`. <br> The default value is `Completed`. <br> Multiple statuses can be specified by separating them with a semicolon ";".    |
|    getLatestExecution    |    No    |    boolean    |    The API will return details of the latest execution. By default, this parameter is set to true.<br> If you choose to pass the value of this parameter as false, then the API will return the last 90 days execution instances.    |
|        |        |        |        |

### Sample Request Payload

None

### Sample Response

The response payload is structured as follows:

Response Codes: 200, 400, 401, 403, 404, 500

Response payload example:

```json
{
  "value": [
    {
      "executionId": "906931dc-4f2f-4195-bbb2-d7295c7550d3",
      "reportId": "d9548477-16d4-492a-bf9c-0cf91a9f69bf",
      "recurrenceInterval": 24,
      "recurrenceCount": 100,
      "callbackUrl": null,
      "callbackMethod": null,
      "format": "csv",
      "executionStatus": "Completed",
      "reportLocation": null,
      "reportAccessSecureLink": "https://<path to report for download>",
      "reportExpiryTime": null,
      "reportGeneratedTime": "2021-03-31T18:41:00Z"
    }
  ],
  "nextLink": null,
  "totalCount": 1,
  "message": null,
  "statusCode": 200,
  "dataRedacted": false
}
```

Once report execution is complete, the execution status `Completed` is shown. You can download the report by selecting the URL in the `reportAccessSecureLink`.

### Glossary

Key definitions of elements in the response.

|    Parameter    |    Description    |
|    ----    |    ----    |
|    ExecutionId    |    Universally unique identifier (UUID) of the execution instance    |
|    ReportId    |    Report ID associated with the execution instance    |
|    RecurrenceInterval    |    Recurrence interval provided during report creation    |
|    RecurrenceCount    |    Recurrence count provided during report creation    |
|    CallbackUrl    |    Callback URL associated with the execution instance    |
|    CallbackMethod    |    Callback method associated with the execution instance    |
|    Format    |    Format of the generated file at the end of execution    |
|    ExecutionStatus    |    Status of the report execution instance. <br> Valid values are: `Pending`, `Running`, `Paused`, and `Completed`    |
|    ReportAccessSecureLink    |Link through which the report can be accessed securely        |
|    ReportExpiryTime    |    UTC Time after which the report link will expire in this format: yyyy-MM-ddTHH:mm:ssZ    |
|    ReportGeneratedTime    |    UTC Time at which the report was generated in this format: yyyy-MM-ddTHH:mm:ssZ    |
|    TotalCount    |    Number of datasets in the Value array    |
|    StatusCode    |    Result Code <br> The possible values are 200, 400, 401, 403, 404 and 500    |
|    message    |    Status message from the execution of the API    |
|        |        |

## Next steps

- Try out the APIs through the [swagger API URL](https://api.partnercenter.microsoft.com/insights/v1/mpn/swagger/index.html)
- [Make your first API call](insights-programmatic-first-api-call.md
