---
title: Common questions for partner insights programmatic access
description: Get answers to commonly asked questions about accessing partner insights data through API.
ms.topic: troubleshooting
ms.service: partner-dashboard
ms.subservice: partnercenter-insights
author: kshitishsahoo
ms.author: ksahoo
ms.date: 8/1/2022
---

# Programmatic access of analytics data common questions

This article addresses commonly asked questions about how to programmatically access partner insights data in Partner Center.

## API responses

What are the different scenarios under which I can receive an API response other than 200 (Success)?

This table describes the API responses and what to do if you receive them.

|    Error description     |    Error code     |    Troubleshoot     |
|    ----    |    ----    |    ----    |
|    Unauthorized     |    401     |    This is an authentication exception. Check the correctness of the Microsoft Azure Active Directory (Azure AD) token. The Azure AD token is valid for 60 minutes, after which time you would need to regenerate the Azure AD token.     |
|    Invalid table name     |    400     |    The name of the dataset is wrong. Recheck the dataset name by calling the "Get All Datasets" API.     |
|    Incorrect column name     |    400     |    The name of the column in the query is incorrect. Recheck the column name by calling the "Get All Datasets" API or refer to the column names in the Data Definitions    |
|    Null or missing value     |    400     |    You may be missing mandatory parameters as part of the request payload of the API.     |
|    Invalid report parameters     |    400     |    Make sure the report parameters are correct. For example, you may be giving a value of less than 4 for RecurrenceInterval parameter.     |
|    Recurrence Interval must be between 4 and 2160     |    400     |    Make sure the value of the RecurrenceInterval request parameter is between 4 and 2160.     |
|    Invalid QueryId     |    400     |    Recheck the generated QueryId.     |
|    Invalid report parameters for creation - Start time of report should at least be 4 hours from current UTC time     |    400     |    Start Time parameter as part of request payload shouldn't be in the past. The start time of the report should be at least 4 hours from the current UTC time.     |
|    Requested value 'string' not found     |    400     |    Check whether you have updated the request parameters `callbackurl` or format.     |
|    No item found with given filters.     |    404     |    Check the reportID parameter used in the Get Report Executions API.     |
|    There are no executions that have occurred for the given filter conditions. Double check the reportId or executionId and retry the API after the report's scheduled execution time     |    404     |    Make sure that the reportId is correct. Retry the API after the report's scheduled execution time as specified in the request payload.     |
|    Internal error encountered while creating report. Correlation ID <>     |    500     |    Make sure that the format of date for the fields *StartTime*, *QueryStartTime*, and *QueryEndTime* are correct.     |
|    Service unavailable    |    500     |    If you continuously receive a service unavailable (5xx error), open a support ticket.    |
|        |        |        |

## No records

I receive API response 200 when I download the report from the secure location. Why am I getting no records?
Check whether the string in the query has one of the allowable values for the column header. For example, this query will return zero results:

```sql
SELECT CustomerTenantId, CustomerTpId, WorkloadName, Month, MonthlyActiveUsers
FROM OfficeUsage
WHERE IsDuplicateRowForPGA = 'False'
ORDER BY CustomerTenantId DESC
```

In this example, the allowable values for `IsDuplicateRowForPGA` are 0 or 1. Refer to the [Data Definitions](insights-data-definitions.md) for all possible values for the various columns.
