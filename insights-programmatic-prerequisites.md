---
title: Prerequisites to programmatically access analytics data
description: Prerequisites to programmatically access analytics data
ms.topic: article
ms.service: partner-dashboard
ms.subservice: partnercenter-insights
author: kshitishsahoo
ms.author: ksahoo
ms.date: 8/1/2022
---

# Prerequisites to programmatically access analytics data

**Appropriate roles:** Global admin | MPN admin

Before you can programmatically access partner insights analytics data, you must meet the requirements described in this article.

## Microsoft AI Cloud Partner Program enrollment

To access partner insights analytics data programmatically, you must be enrolled in the Microsoft AI Cloud Partner Program program and have a Partner Center account. To learn how, see [Create a Microsoft AI Cloud Partner Program account in Partner Center](mpn-create-a-partner-center-account.md)

## Create Microsoft Azure Active Directory (Azure AD) application

Regular user credentials can't be used for programmatic access of Partner Insights Analytics data. To access the programmatic access APIs, a Microsoft Azure Active Directory (Azure AD) application must be created along with a secret (application + user access).

To learn how to create an Azure AD application and secret, see [Quickstart: Register an application with the Microsoft identity platform](/azure/active-directory/develop/quickstart-register-app).

Permission is required to access Microsoft Partner API. To learn how to add permission, see [Partner API authentication - Partner](/partner/develop/api-authentication#application-and-user-access)

## Assign the Executive report viewer (ERV) role to the user

To access partner insights analytics data programmatically, you must be assigned the Executive report viewer (ERV) role. To learn how to assign the ERV role to a user, see [Partner Center Insights role-based access - Partner Center](insights-roles.md)

## Generate a Microsoft Azure Active Directory (Azure AD) token

You need to generate an Azure AD token using the Application (client) ID, client secret, your user ID, and password. To generate an Azure AD token, see [Token generation](insights-programmatic-first-api-call.md#token-generation).

> [!NOTE]
> The token is valid for one hour.

## Next steps

[Programmatic access paradigm](insights-programmatic-access-paradigm.md)
