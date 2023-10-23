---
title: Programmatic access of analytics data common questions - commercial marketplace
description: Commonly asked questions about programmatically accessing analytics data in Partner Center for your commercial marketplace offers. 
ms.service: partner-dashboard 
ms.subservice: partnercenter-insights
ms.topic: article
author: smannepalle
ms.author: smannepalle
ms.reviewer: sroy
ms.date: 3/08/2021
---

# Programmatic access of analytics data common questions for commercial marketplace

This article addresses commonly asked questions about how to programmatically access analytics data in Partner Center for your commercial marketplace offers.

## Error messages in API response

This table describes the possible Error messages in API responses and troubleshooting steps.

| Error description | Error code | Troubleshoot |
| ------------ | ------------- | ------------- |
| Unauthorized| 401|This exception is related to authentication. Validate that you're using correct Azure Active Directory (Azure AD) token. The token is valid for 60 minutes, after that you would need to regenerate the token. |
| Invalid table name| 400|You have entered an incorrect dataset name. Use the "Get datasets API" to validate the dataset name. Ensure the correct dataset name is used.|
| Incorrect column name| 400|You have entered incorrect column name. Use the "Get datasets API" to validate the column names for dataset.|
| Null or missing value| 400|You are missing mandatory parameters in request payload of the API. Ensure that you're providing correct value for mandatory parameters. |
| Invalid report parameters for creation - StartTime should follow format: yyyy-MM-ddTHH:mm:ssZ| 400|`StartTime` in the API doesn't follow the suggested format. Ensure that `StartTime` follows format: yyyy-MM-ddTHH:mm:ssZ|
| Invalid report parameters for creation - EndTime should be greater than StartTime| 400|Ensure that `EndTime` is greater than `StartTime`|
| Invalid report parameters for creation - EndTime should follow format: yyyy-MM-ddTHH:mm:ssZ| 400|`EndTime` in the API doesn't follow the suggested format. Ensure that `EndTime` follows format: yyyy-MM-ddTHH:mm:ssZ|
| Invalid report parameters for creation - Report format should be csv/tsv| 400|Ensure that you're providing `Format` as either CSV or TSV.|
| Invalid report parameters for creation - Invalid character (;) in ReportName| 400|Remove invalid character (;) from the `ReportName` parameter.|
| Invalid report parameters for creation - CallbackMethod can only be GET or POST| 400|Ensure that `CallbackMethod` is set as either GET or POST.|
| Invalid report parameters for creation - Recurrence count has to be a positive integer value| 400|Provide positive integer value in `RecurrenceCount` parameter.|
| Invalid report parameters for creation - Limit ReportName and Description length to 256 characters or less| 400|Ensure that `ReportName` and `Description` don't exceed 256 characters.|
| Invalid report parameters for creation - Start time of report should at least be 4 hours from current UTC time| 400|`StartTime` parameter as part of request payload shouldn’t be in the past. The start time of the report should be at least 4 hours from the current UTC time.|
| Invalid QueryId| 400|You have used incorrect `QueryId`. Validate the `QueryId` you're using. |
| Recurrence Interval must be between 4 and 2160| 400|Make sure the value of the `RecurrenceInterval` request parameter is between 4 and 2160.|
| User has exceeded its report creation quota of 50 active reports| 400|You have exceeded the quota of 50 active reports. Review your active reports and delete the ones not being used.|
| User has exceeded its ExecuteNow report creation quota of 5 reports/60 mins| 400|You have generated five reports in last 60 minutes with `ExecuteNow=True`. Wait before generating another report. Please consider scheduling the report as per your need and you won't be hitting the quota.|
| Requested value ‘string’ not found| 400 |Check whether you have updated the request parameters `callbackurl` or `format`.|
| Number of queries exceeded. Delete few queries before creating new queries| 400 |You have exceeded the quota of 100 active queries. Review and delete unused queries before creating new ones.|
| No item found with given filters| 404 |Check the `reportID` parameter used in the Get Report Executions API.|
| There are no executions that have occurred for the given filter conditions. Please recheck the reportId or executionId and retry the API after the report's scheduled execution time| 404 |Make sure that the `reportId` is correct. Retry the API after the report’s scheduled execution time as specified in the request payload.|
| Internal error encountered while creating report. Correlation ID <>| 500|Make sure that the format of date for the fields `StartTime`, `QueryStartTime` and `QueryEndTime` are correct.|
| Service unavailable| 500|If you continuously receive a service unavailable (5xx error), create a [support ticket](./marketplace/support.md).|

## No records

**I have received API response 200 for Get Reports Execution API. Why are there no records in the downloaded file?**

Check whether the string in the query has one of the possible values for the column header.

`SELECT UsageDate, NormalizedUsage, EstimatedExtendedChargePC FROM ISVUsage WHERE SKUBillingType = 'Paided' ORDER BY UsageDate DESC TIMESPAN LAST_MONTH`

In this example, the possible values for SKUBillingType are Paid or Free and since you're using a different value, the query returns no record.

Refer to the following tables for all possible values for the various columns:

- [Orders details table](orders-dashboard.md#orders-details-table)
- [Usage details table](usage-dashboard.md#usage-details-table)
- [Customer details table](customer-dashboard.md#customer-details-table)
- [Marketplace insights details table](insights-dashboard.md#marketplace-insights-details-table)
- [Revenue dashboard](revenue-dashboard.md)
- [Quality of Service dashboard](quality-of-service-dashboard.md)
- [Customer retention dashboard](customer-retention-dashboard.md#dictionary-of-data-terms)

## Next steps

- [APIs for accessing commercial marketplace analytics data](analytics-available-apis.md)


