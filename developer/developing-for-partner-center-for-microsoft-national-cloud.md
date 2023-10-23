---
title: Developing for Partner Center for Microsoft National Clouds
description: Partner Center SDK differences when developing for Partner Center for Microsoft National Clouds.
MS-HAID: 
  - 'pc\_apiv2.developing\_with\_different\_partner\_center\_versions'
  - 'pc\_apiv2.developing\_for\_partner\_center\_for\_microsoft\_national\_cloud'
ms.date: 09/28/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: jischulz
ms.author: jischulz
---

# Developing for Partner Center for Microsoft National Clouds

**Applies to**: Partner Center operated by 21Vianet |  Partner Center for Microsoft Cloud for US Government

## Partner Center operated by 21Vianet

The differences for partners between *Partner Center* and *Partner Center operated by 21Vianet* are:

- You can't programmatically reset a password for a customer user or full partner user.

- Subscriptions to Azure aren't available.

- You can't manage the licenses for your customer's user. Instead, your customers must use the [Microsoft 365 admin center](https://admin.microsoft.com/adminportal/home?#/homepage) to manage their licenses.

- All support requests are managed through Partner Center operated by 21Vianet. Service requests and service updates don't apply.

## Partner Center for Microsoft Cloud for US Government

The differences for partners between *Partner Center* and *Partner Center for Microsoft Cloud for US Government* are:

- Office 365 subscriptions aren't currently available for Partner Center for Microsoft Cloud for US Government.

- Existing partners supporting Microsoft Cloud for US Government must create new accounts in Partner Center for Microsoft Cloud for US Government.

- Microsoft Cloud for US Government customers must transact with a single partner.
  - Multichannel and multi-partner and request relationship with an existing customer within Microsoft Cloud for US Government scenarios don't apply. This limitation is because Office 365 isn't currently available.

- Partners can't create users for their customer's organization or assign roles.
  - Partners can read fields, but they cannot write or update them. Partners must manually create or update their customers' users in [Microsoft Azure portal](https://ms.portal.azure.com/). See [Azure Active Directory Documentation](/azure/active-directory/).

- You cannot programmatically reset a password for a customer user or full partner user. Use the Azure portal to do so: see [Reset the password for a user in Azure Active Directory](/azure/active-directory/active-directory-users-reset-password-azure-portal). For step 1, you must sign-in to [Microsoft Azure portal](https://ms.portal.azure.com/) for Microsoft Cloud for US Government.

- REST endpoints for Partner Center for Microsoft Cloud for US Government are the same as for Partner Center.

- Developers must register their app ID manually to integrate Partner Center API functionality in their app for Partner Center for Microsoft Cloud for US Government. For more information, see [Register app details for Partner Center for Microsoft National Cloud](create-apps-for-partner-center-for-microsoft-national-clouds.md).
