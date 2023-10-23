---
title: Partner Center samples
description: To help you get up and running quickly with the Partner Center APIs, we provide a sample program, C\ managed code snippets, and REST sample requests and responses.
ms.date: 6/30/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: denysseD
ms.author: vijvala
---

# Partner Center samples

**Applies to**: Partner Center | Partner Center operated by 21Vianet |  Partner Center for Microsoft Cloud for US Government

To help you get up and running quickly with the Partner Center APIs, we provide a sample program, C# managed code snippets, and REST sample requests and responses.

[!INCLUDE [Partner Center Java SDK support details](./includes/java-sdk-support.md)]

[!INCLUDE [Partner Center PowerShell module support details](./includes/powershell-module-support.md)]

| Sample                 | Details                                             |
|------------------------|-----------------------------------------------------|
| Code snippets          | For pointers and .NET, Java, and PowerShell code snippets that show how to use the Partner Center managed API to manage customer accounts, get analytics, place orders, manage billing and subscriptions, provide support, and manage accounts and profiles, see [Scenarios](scenarios.md).     |
| REST samples           | For sample requests and responses that show how to use the Partner Center REST API to manage customer accounts, get analytics, place orders, manage billing and subscriptions, provide support, and manage accounts and profiles, see [Scenarios](scenarios.md).        |
| [Console test app](console-test-app.md)   | This app is available in C# and Java, it provides code and some error handling for all of the scenarios listed in the scenarios section.    |
| Store web site      | This application shows how to build a web store based on the catalog of offers available to Cloud Solution Provider partners. Customers can create a store account and order software subscriptions through your site.<br/><br/>                  **Get the code:**<br/> [Download the sample code](https://go.microsoft.com/fwlink/p/?LinkId=746683)<br/><br/>                                            **What to configure before release:**<br/><br/> - Authentication: App ID & secret<br/> - Branding: logo and company name<br/> - Welcome message<br/> - Offers, including descriptions and prices. The app assumes that the list prices include any applicable taxes. Alternatively, you can add more logic to calculate tax during checkout.<br/> - Payment information: provide your own credit card options, PayPal, or other payment types. Before you configure this part, read the guide [Nonpayment, fraud, or misuse](../non-payment-fraud-misuse.md). |