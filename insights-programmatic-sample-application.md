---
title: Sample Application
ms.topic: article
ms.date: 8/1/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-insights
description: Use the sample application to build your own application to programmatically access partner insights data.
author: kshitishsahoo
ms.author: ksahoo
---

# Sample Application

Sample applications are created in C# and JAVA languages and are available on [GitHub](https://github.com/partneranalytics)

- [C# Sample Application](https://github.com/partneranalytics/ProgrammaticExportSampleAppMPN)
- [JAVA Sample Application](https://github.com/partneranalytics/ProgrammaticExportSampleAppMPN_Java)

You can choose to take inspiration from the sample application and build your own application in any language.

The sample application achieves the following objectives:

- Generates an Azure Active Directory (Azure AD) Token.
- Gets available datasets.
- Creates user defined queries.
- Gets user defined and system queries.
- Schedules a report.

The sample application doesn't cover the method of calling APIs for other functionalities. However, the process of calling other APIs remains the same as outlined above.

## How to run the application

- Clone the repository to a local system using this command:

```cli
git clone https://github.com/partneranalytics/ProgrammaticExportSampleAppMPN.git
```

> [!NOTE]
> For more instructions, refer to the ProgrammaticExportSampleAppMPN/README.md file in the GitHub [repository](https://github.com/partneranalytics/ProgrammaticExportSampleAppMPN_Java).

- To quickly run the app, update the client ID and client secret in the **appsettings.Development.json**

:::image type="content" source="media/insights/prog-acc-appsetting-development.png" lightbox="media/insights/prog-acc-appsetting-development.png" alt-text="Illustrating appsetting development json":::

Running the app will start a local web server and a page will open (`https://localhost:44365/ProgrammaticExportSampleApp/sample`).

:::image type="content" source="media/insights/prog-acc-sample-application.png" alt-text="Illustrating UI of sample application":::

This page will make API calls to the webserver running on the local machine, which in turn will make the actual programmatic access API calls.

## Code Snippets

The basic structure of the C# code for doing the programmatic access API calls is as follows:

:::image type="content" source="media/insights/prog-acc-code-snippet.png" lightbox="media/insights/prog-acc-code-snippet.png" alt-text="Illustrating code snippet":::

## Next steps

[APIs for accessing partner insights analytics data](insights-programmatic-analytics-available-api.md)
