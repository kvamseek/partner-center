---
title: Register app details for Partner Center for Microsoft National Cloud
description: Learn how and why app developers for Partner Center for Microsoft National Cloud must register details about their app with Azure AD through the Azure portal.
MS-HAID: 
  - 'pc\_apiv2.create\_apps\_for\_partner\_center\_for\_microsoft\_cloud\_germany'
  - 'pc\_apiv2.create\_apps\_for\_partner\_center\_for\_microsoft\_national\_clouds'
ms.date: 09/28/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: jischulz
ms.author: jischulz
---

# Register app details for Partner Center for Microsoft National Cloud through the Azure portal

**Applies to**:  Partner Center for Microsoft Cloud for US Government

Developers must register details about their app with Azure AD through [Microsoft Azure portal](https://ms.portal.azure.com/). This helps ensure that only specified apps are able to connect to partner and customer data.

For Partner Center for Microsoft Cloud for US Government, you currently must manage apps through PowerShell. For more information, see the [Azure PowerShell reference documentation](/powershell/module/Azuread/#applications).

[!INCLUDE [Partner Center PowerShell module support details](./includes/powershell-module-support.md)]

Be aware of the following additional requirements when you create an app for Partner Center for Microsoft Cloud for US Government.

## Web apps

For web apps, use the following procedures to register your application ID.

### Create or update web app

1. Navigate to the [Azure portal - App registrations](https://go.microsoft.com/fwlink/?linkid=2083908) page to register your app. Sign-in to the portal using either a work or school account or a personal Microsoft account.

2. Select **New registration**. For more information, see [Quickstart: Register an application with the Microsoft identity platform](/azure/active-directory/develop/quickstart-register-app).

### Configure API access permissions for web app

3. Choose your app. Go to **Settings** of the Web app.

4. In **API Access** section, choose **Required permissions**

5. For Windows Azure Active directory permissions:

    1. Choose **Windows Azure Active Directory permissions**.

    2. In **Applications permissions**, select Read directory data.

    3. Save the permissions.

6. Note the application ID in the **Properties** section of your web app.

### Add a secret key to your app

7. Go to the **Keys** section of your web app.

8. Enter key description and select duration as 1 or 2 years, as you need.

9. Save and copy the secret key value. **This value will not be shown again once you leave this page.**

You should have the following details from the web app configuration:

- Application ID
- Application secret

### Register the Web app in Partner Center

10. Sign in to [https://partnercenter.microsoft.com](https://partnercenter.microsoft.com).

11. Choose **Dashboard**, then choose **Account settings**, then choose **App Management**.

12. In the **Web App** section, choose **Register existing app**.

13. Select the web app you created in Azure portal.

14. Choose **register your app**.

## Native apps

Native apps do not need to be registered to Partner Center, however, these apps need to be configured to provide access to Partner Center APIs.

> [!NOTE]
>Before creating a native app in the Azure portal, log in into Partner Center using the admin user credentials from the partner tenant. This creates the settings on the tenant to enable app permissions.

### Create native app

15. Navigate to the [Azure portal - App registrations](https://go.microsoft.com/fwlink/?linkid=2083908) page to register your app. Sign-in to the Azure portal using either a work or school account or a personal Microsoft account.

16. Select **New registration**. For more information, see [Quickstart: Register an application with the Microsoft identity platform](/azure/active-directory/develop/quickstart-register-app).

### Configure API access permissions for native app

17. Choose your app. Go to **Settings**.

18. In API Access, choose **Required permissions**.

19. Choose **Windows Azure Active Directory permissions**. In **Delegated permissions**, select these permissions:

    - **Sign in and read user profile**
    - **Read directory data**
    - **Access the directory as the signed-in user**
    - **Read all groups**

20. Save the permissions.

21. Choose **Add** in **Required permissions**.

22. Choose **Select an API**.

    a. In the search box, enter **Microsoft Partner Center** and select it from the results list.

    b. Choose **Select**.

23. Choose **Select permissions**.

    c. Select **Access Partner Center PPE**.

    d. Choose **Select**.

8. Choose **Done**.

> [!IMPORTANT]
> *Note the application ID in the Properties of your app.*

You do not need to register native apps in Partner Center, however the native app must be admin consented.
