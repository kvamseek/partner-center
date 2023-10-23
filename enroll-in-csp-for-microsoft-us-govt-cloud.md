---
title: Enroll in the CSP program
titleSuffix: Microsoft Cloud for US Government - Partner Center
ms.topic: how-to
ms.service: partner-dashboard
ms.subservice: partnercenter-enroll
description: Learn about CSP program requirements for partners who want to enroll in the Cloud Solution Provider program for Microsoft Cloud for US Government.
author: sharath-satish-msft
ms.author: shsatish
ms.date: 06/09/2022
---

# Enroll in the Cloud Solution Provider program for Microsoft Cloud for US Government

**Applies to**: Partner Center for Microsoft Cloud for US Government

**Appropriate roles**: Global admin

Microsoft partners can now sell Microsoft's cloud solutions and services to US federal, state, local, and tribal entities through the Cloud Solution Provider program (CSP) for Microsoft Cloud for US Government.

Microsoft Cloud for US Government provides a private, dedicated, and isolated instance of Microsoft Azure that meets the US government's requirements for data security, privacy, and compliance. Your company must meet Microsoft's eligibility requirements to participate in the CSP program for Microsoft Cloud for US Government. For more information, see [Partner Center for Microsoft Cloud for US Government](partner-center-for-microsoft-us-govt-cloud.md).

## Before you begin

Before you can enroll in the CSP program for Microsoft Cloud for US Government, we need to verify that your company meets the requirements to sell to US government entities. Before you kick off the enrollment process, complete the [Microsoft Government Cloud Validation form](https://azure.microsoft.com/global-infrastructure/government/request/?ReqType=CSP) so we can verify your company's eligibility. After we verify your company's eligibility, we'll provide you with an Azure Active Directory (Azure AD) tenant specific to the Microsoft Cloud for US Government.  

To create a Partner Center account and enroll in CSP for Microsoft Cloud for US Government, you'll need to supply the following information (you may want to gather this information before you kick off the enrollment process):

- Global admin credentials for your organization's new Azure AD tenant for Microsoft Cloud for US Government
- Your organization's PartnerID
- A business address in the United States

> [!IMPORTANT]
> If you have an existing account in Partner Center and you want to enroll in CSP for Microsoft Cloud for US Government, you must create a new, separate account specifically for the US Government market.

## How to enroll

### Step 1 - Create a Partner Center account for Microsoft Cloud for US Government

**Prerequisite**: Create an Azure tenant for enrollment in the [Cloud Solution Provider Program for the US Government](https://azure.microsoft.com/contact/government-trial/?ReqType=CSP). If you already have an Azure Government Account, continue with step 1.

1. Kick off the enrollment process at [Welcome to Partner Center for Microsoft Cloud for US Government](https://aka.ms/accounts/rncEnrollment).

2. Sign in with global admin credentials for your organization's Azure AD tenant for Microsoft Cloud for US Government. If your organization doesn't have an account for this portal, you can request one by completing the [Microsoft Government Cloud Validation form](https://azure.microsoft.com/global-infrastructure/government/request/?ReqType=CSP).

### Step 2 - Apply to participate in the Cloud Solution Provider program for Microsoft Cloud for US Government

1. Fill in any missing information on the enrollment form, including your PartnerID and your organization's customer support details.

2. Select **Accept and continue**. Reviewing your application may take us several days. We'll email you when we've completed our review.

   > [!IMPORTANT]
   > By selecting **Accept and continue**, you're confirming that you're authorized to act on your organization's behalf, and you're agreeing to allow Microsoft to run a background credit check before reviewing your organization's Cloud Solution Provider application.

### Step 3 - Sign the reseller agreement for Microsoft Cloud for US Government

1. Sign in to Partner Center for Microsoft Cloud for US Government using the link in the application approval email.

2. On the **Agreement** page, read the terms, and if you agree, select **Accept and continue** to digitally sign the reseller agreement for Microsoft Cloud for US Government. Creating your account may take several hours. You can sign out of Partner Center for Microsoft Cloud for US Government and then sign back in later.

### Step 4 - Assign users to the Admin Agent role in the Microsoft Azure admin portal for Microsoft Cloud for US Government

Microsoft Cloud for US Government provides a separate instance of Microsoft Azure that meets government compliance, security, and privacy standards. To allow admins to manage users and licenses in the Microsoft Azure portal, you'll need to manually assign the Admin Agent role to them.

> [!NOTE]
> After you assign users to the Admin Agent role, they'll be able to access your customer list on the **Customers** page and [add new customers](add-a-new-customer.md).

1. Sign in to [Azure portal](https://portal.azure.com).

2. Assign the Admin Agent role to the appropriate users in your organization. To do that, you'll need to add these users to the built-in **AdminAgent** group. See [Manage the members for a group in Azure Active Directory](/azure/active-directory/active-directory-groups-members-azure-portal) for more information.

## Connect with us

- Questions? Email [Azure Government CSP](mailto:azgovcsp@microsoft.com).
- Join us on [Yammer](https://www.yammer.com/cloudpartnercommunity/#/threads/inGroup?type=in_group&feedId=11509777).

## Next steps

- [Partner Center for Microsoft Cloud for US Government](partner-center-for-microsoft-us-govt-cloud.md)
- [User and license management in Partner Center for Microsoft Cloud for US Government](user-management-in-partner-center-for-microsoft-us-govt-cloud.md)
