---
title: Azure AD service principal
ms.topic: how-to
ms.date: 03/16/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-enroll
description: Find out how to add a service principal to your Azure AD tenant. Doing so means adding an Azure AD application (service principal) in Partner Center.
author: sharath-satish-msft
ms.author: shsatish
---

# Add an Azure AD application (service principal) in Partner Center

**Appropriate roles**: Global admin

In the Commercial Marketplace program in Partner Center, you are now able to add a Microsoft Azure Active Directory (Azure AD) application (service principal) as a user in your Partner Center account. (You were able to do so previously in your Cloud Partner Portal (CPP) account. Now that you have migrated to Partner Center, the CPP account is read-only.)

> [!NOTE]
>Service principal is synonymous with Azure AD application.

## Add an Azure AD application (service principal)

1. From the Partner Center, select **Settings** and then select **Developer settings**.

2. Select **Users** and then select **Add Azure AD Applications**.

3. Select an existing Azure AD application or create a new one.

4. If you create a new Azure AD application, include the following information:

   - **Reply URL**: The URL where users can sign in to use your Azure AD application.

   - **App ID URI**: A logical identifier for the Azure AD application that is presented when it sends a single sign-on request to Azure AD.

   - **Security roles**: The roles **Manager** (the same as  ‘Owner' role in CPP) and **Developer** (the same as ‘Contributor' role in CPP) apply to the Commercial Marketplace program in Partner Center, and they can be associated with this Azure AD Application.

## Next steps

- [Overview of the commercial marketplace in Partner Center](csp-commercial-marketplace-overview.md)
