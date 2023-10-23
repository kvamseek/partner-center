---
title: Get started with Partner Center APIs
description: The Partner Center REST APIs are used by partners to use to manage customer, subscription, and order data.
ms.date: 06/22/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
ms.custom: intro-get-started
ms.author: juliegray
---

# Get started with Partner Center APIs

**Applies to**: Partner Center | Partner Center operated by 21Vianet |  Partner Center for Microsoft Cloud for US Government

Partner Center provides a REST API for partners to use to manage customers, subscriptions, and orders.

## Get the code

[Download the Partner Center SDK](https://go.microsoft.com/fwlink/p/?LinkId=746681)

> [!NOTE]
> API access to Partner Center for indirect resellers isn't supported.

## Determine your version of Partner Center

Some versions of Partner Center do not have the entire SDK available. For more information, see [Developing for Partner Center for Microsoft National Cloud](developing-for-partner-center-for-microsoft-national-cloud.md).

## Get the samples

For more information about C# snippets, REST samples, and the sample app, see [Partner Center samples](partner-center-samples.md).

## Test environments

While you are initially writing and testing your code, you should use your integration sandbox account (and the corresponding tokens) so that you don't accidentally incur new charges that your company is responsible for paying. For more information about this testing environment, see [Set up API access in Partner Center](set-up-api-access-in-partner-center.md).

When your solution is tested and ready to use on real customer accounts, you'll have to update your tokens so that you're using an Azure AD client app and secret that correspond to your Primary Partner Center account.

For tips and suggestions about testing and debugging, including more information about Test-in-Production (TiP) and the Integration Sandbox, see [Test and debug](test-and-debug.md).

## Authentication

To configure your Azure AD authentication so that you can use the Partner Center APIs, see [Partner Center authentication](partner-center-authentication.md).

> [!IMPORTANT]
> Microsoft is introducing a secure, scalable framework for authenticating cloud solution provider (CSP) partners and control panel vendors (CPV) through the Microsoft Azure multi-factor authentication (MFA) architecture.
Partner Center uses Azure AD for authentication, and to use the Partner Center APIs you must configure your authentication settings correctly.
>
> For more information, see [Enable secure application model](enable-secure-app-model.md).

## Get support

Partners can get support at the [Partner Center SDK Yammer group](https://go.microsoft.com/fwlink/p/?LinkID=717360). To get more personalized help, developers can use their Microsoft AI Cloud Partner Program support benefits or Premier Support.

## Join the Partner Center API Early Adopter Program

To find out how you can collaborate with Microsoft on the development of Partner features and capabilities, see [Join the Partner Center API Early Adopter Program](early-adopter-program.md).
