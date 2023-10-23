---
title: Audit operations of Partner Center activity
description: Learn about the type of Partner Center API audit operations you can use to get a record of Partner Center activity.
ms.date: 06/16/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: vijay-vala
ms.author: vijvala
---

# Audit activity

The Partner Center APIs provide auditing features so you can get a record of Partner Center activity.

You can retrieve audit records for the previous 30 days from the current date, or for a date range specified by including the start date and/or the end date. Note, however, that for performance reasons activity log data availability is limited to the previous 90 days. Requests with a start date greater than 90 days prior to the current date will receive a bad request exception (error code: 400) and an appropriate message.

## Retrieve audit records

Get detailed historical audit records of operations performed by a partner user or application:

- [Get a record of Partner Center activity](get-a-record-of-partner-center-activity-by-user.md)
- [Auditing resources](auditing-resources.md)
