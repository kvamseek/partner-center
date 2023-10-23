---
title: Set up API access in Partner Center
description: Set up accounts for developing against the Partner Center SDK and test in the integration sandbox.
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: JulCsc
ms.author: raormeni
ms.date: 07/03/2023
---

# Set up API access in Partner Center

**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud for US Government

This article describes the accounts you need to develop against the Partner Center SDK. This article also explains how to create an [integration sandbox account](#integration-sandbox-account) and test in the integration sandbox.

> [!NOTE]
>To get access to APIs, your tenant must be a CSP tenant and you must be either an indirect provider or a Direct bill partner.

## Account definitions

To help you integrate and test your API integration, Partner Center supports two kinds of accounts:

### Primary Partner account

This account is where you create real orders for real customers. If you make any changes or transactions when you are signed in to the primary account, by using either the Partner Center SDK or the Partner Dashboard UI, they will be treated as official orders for real customers. They will be reflected in your invoice, and your company is responsible for paying for them.

### Integration sandbox account

This account is for testing your code and its integration with the Partner Center APIs before you deploy it broadly. Changes and transactions you make when you are signed into the integration sandbox account will appear in your invoice, however, you do not have to pay the invoice amount. Invoice pdf will have a disclaimer as "DO NOT PAY. THIS IS A SANDBOX INVOICE AND NO ACTION IS REQUIRED."

The integration sandbox account and the primary account act independently, and do not share admin accounts, user accounts, customers, orders, subscriptions, or other data.

The integration sandbox supports transactions with a limited number of customers, orders, subscriptions, licenses, etc.

By policy, integration sandbox accounts are for integration testing purposes only.

By default, there is no integration sandbox account. You must create one yourself if you plan to use the Partner Center SDK.

## Set up your accounts

This section describes how to set up a primary Partner account and an integration sandbox account for the Partner Center SDK.

### Create an integration sandbox

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) with a Global admin account and select **Settings** (gear).

2. Select **Account settings**, then **Integration sandbox**.

   > [!NOTE]
   > If you don't see an Integration sandbox option, you might not have a global admin account. You also might be using an integration sandbox account and an integration sandbox has already been set up.

3. Enter the contact information for the integration sandbox admin account. Then, choose **Create account**. Wait a few minutes for a confirmation message that the account has been created.

4. After you see the confirmation message, sign out of Partner Dashboard.

5. Sign back in with your new integration sandbox admin account. Be sure to use the format **username@domain** for your credentials along with the password that you specified.

6. Choose **Set up account** on the [Integration Sandbox page](https://aka.ms/accountexp/sandbox) to complete the sandbox account setup.

### Enable API access

After your account is set up, you must enable API access before you can use the Partner Center SDK with the integration sandbox. You need to enable access to the API separately for both your primary Partner account and your integration sandbox account.

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) with a Global admin account and select **Settings** (gear).

2. Select **Account settings**, then **App management**.

3. If you do not already have an existing app, add a new web app. If you have an existing web app, choose the **Add key** button.

4. Copy the app registration information, especially the **Key** if you're creating a web app, and store it in a safe place.

5. Sign out of Partner Dashboard.

6. Sign back in with your integration sandbox account. Repeat steps 2-5 to enable API access in the integration sandbox.

## Write and test code

You can write code and test code in the integration sandbox. You'll need the following information to [set up Partner Center authentication](partner-center-authentication.md) with Azure AD.

| Item name | Item location |
| --------- | ------------- |
| App ID / Client ID | From **Settings** (gear), select **Account settings**, then **App Management**. The App ID/Client ID is listed as the **Registered application App ID**. |
| Key | If you created a web app in the section [Enable API access](#enable-api-access), this is the key that you saved in step 5. |
| Domain | The domain for the integration sandbox. |

## Run tested code

To use your solution with real customer data, you must change from your integration sandbox credentials to your primary Partner account credentials.

When you're ready to use your tested code in your primary Partner account, you must get an Azure AD security token. This security token is based on your Partner Center app, key, and domain (instead of your integration sandbox app, key, and domain).

1. Follow the steps in [Partner Center authentication](partner-center-authentication.md) to get an Azure AD security token using your primary Partner Center credentials. (You previously followed these steps to get an Azure AD security token for your integration sandbox.)

2. Replace the integration security token in your code with the new security token for your primary Partner account.
