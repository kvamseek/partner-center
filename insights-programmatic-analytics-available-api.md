---
title: List of API for accessing partner insights data
ms.topic: reference
ms.date: 07/14/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-insights
description:  List of API for accessing partner insights data.
author: kshitishsahoo
ms.author: ksahoo
---

# Available APIs for partner insights analytics

Following are the list of APIs for partner insights analytics and their associated functionalities.

## Dataset pull APIs

***Table 1: Dataset pull APIs***

| **API** | **Functionality** |
| --- | --- |
| [Get all datasets](insights-programmatic-analytics-api-get-dataset.md) | Gets all the available datasets. Datasets list the tables, columns, metrics, and time ranges. |

## Query management APIs

***Table 2: Query management APIs***

| **API** | **Functionality** |
| --- | --- |
| [Create Report Query](insights-programmatic-access-paradigm.md#create-report-query-api) | Creates custom queries that define the dataset from which columns and metrics need to be exported. |
| [GET Report Query](insights-programmatic-analytics-api-get-report-queries.md) | Gets all the queries available for use in reports. Gets all the system and user-defined queries by default. |
| [DELETE Report Query](insights-programmatic-analytics-api-delete-report-queries.md) | Deletes user-defined queries. |

## Report management APIs

***Table 3: Report management APIs***

| **API** | **Functionality** |
| --- | --- |
| [Create Report](insights-programmatic-access-paradigm.md#create-report-api) | Schedules a query to be executed at regular intervals. |
| [TRY Report Query](insights-programmatic-analytics-api-try-report-queries.md) | Executes a Report query statement. Returns only 10 records that a partner can use to verify if the data is as expected. |
| [Get Report](insights-programmatic-analytics-api-get-report.md) | Get all the reports that have been scheduled. |
| [Update Report](insights-programmatic-analytics-api-update-report.md) | Modify a report parameter. |
| [Delete Report](insights-programmatic-analytics-api-delete-report.md) | Deletes all the report and report execution records. |
| [Pause Report Executions](insights-programmatic-analytics-api-pause-report-executions.md) | Pauses the scheduled execution of reports. |
| [Resume Report Executions](insights-programmatic-analytics-api-resume-report-executions.md) | Resumes the scheduled execution of a paused report. |

## Report execution pull APIs

***Table 4: Report execution pull APIs***

| **API** | **Functionality** |
| --- | --- |
| [Get Report Executions](insights-programmatic-access-paradigm.md#get-report-execution-api) | Get all the executions that have happened for a given report. |

## Next steps

- You can try out the APIs through the [Swagger API URL](https://api.partnercenter.microsoft.com/insights/v1/mpn/swagger/index.html).
