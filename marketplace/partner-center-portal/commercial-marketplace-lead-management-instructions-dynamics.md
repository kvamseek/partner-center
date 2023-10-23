---
title: Lead management for Dynamics 365 Customer Engagement - Microsoft commercial marketplace
description: Learn how to set up Dynamics 365 Customer Engagement to manage leads from Microsoft AppSource and Azure Marketplace.
ms.service: marketplace
ms.subservice: partnercenter-marketplace-publisher
ms.topic: conceptual
author: sudharocks
ms.author: spadmanabhan
ms.date: 02/07/2023
---

# Configure lead management for Dynamics 365 Customer Engagement

This article describes how to set up Dynamics 365 Customer Engagement (previously named Dynamics CRM Online). Read more about the change in [Configure server-based authentication with Customer Engagement and SharePoint Online](/dynamics365/customerengagement/on-premises/admin/on-prem-server-based-sharepoint-online) to process sales leads from your commercial marketplace offer.

> [!NOTE]
> These instructions are specific for the Microsoft-hosted cloud environment for Dynamics 365 Customer Engagement. Connecting directly to a Dynamics on-premises environment isn't currently supported. There are other options for you to receive leads, such as configuring an [HTTPS endpoint](./commercial-marketplace-lead-management-instructions-https.md) or an [Azure table](./commercial-marketplace-lead-management-instructions-azure-table.md).

## Prerequisites

The following user permissions are necessary to complete the steps in this article:

- Administrator rights on your Dynamics 365 Customer Engagement instance to be able to install a solution.
- Tenant admin rights to create a new service account for the lead service used to send leads from commercial marketplace offers.
- Access to the admin portal.
- Access to the Azure portal.

## Install the solution

1. Download the [Microsoft Marketplace Lead Writer solution](https://referralsflowpackages.blob.core.windows.net/documentation/MicrosoftMarketplacesLeadIntegrationSolution_1_0_0_0_target_CRM_6.1_managed.zip), and save it locally to your computer.
1. Log in to [Power Apps](https://make.powerapps.com/) using the credentials you want to import your solution to. Go to the right environment.
 
    :::image type="content" source="media/commercial-marketplace-lead-management-instructions-dynamics/select-environment.png" alt-text="Screenshot of Select Environment image.":::

1. Go to **Solutions** from the left navigation menu  and select **Import Solution.** Select **Browse,** and go to where you saved the **Microsoft Marketplace Lead Writer** solution that you downloaded in step 1.

    :::image type="content" source="media/commercial-marketplace-lead-management-instructions-dynamics/import-solution.png" alt-text="Screenshot of Import Solution image.":::
 
    > [!NOTE]
    > If you don't see the options in the following screen, you don't have the permissions you need to proceed. Contact an admin on your Dynamics 365 Customer Engagement instance.

1. Complete importing the solution by following the Import solution wizard.

## Configure user permissions

To write leads into your Dynamics 365 Customer Engagement instance, you must share a service account with Microsoft and configure permissions for the account.

Use the following steps to create the service account and assign permissions. You can use Azure Active Directory or Office 365.

> [!NOTE]
> Skip to the corresponding instructions based on the authentication option you select. See [Azure Active Directory](#azure-active-directory) or [Office 365](#office-365).

### Azure Active Directory

We recommend this option because you never need to update your username or password to keep getting leads. To use the Azure Active Directory option, you provide the App ID, Application Key, and Directory ID from your Active Directory application.

To configure Azure Active Directory for Dynamics 365 Customer Engagement:

1. Sign in to the [Azure portal](https://portal.azure.com/). In the left pane, select **Azure Active Directory**.
1. Select **Properties**, and copy the **Directory ID** value on the **Directory properties** page. Save this value because you'll need to provide it in the publishing portal to receive leads for your marketplace offer.

    :::image type="content" source="media/commercial-marketplace-lead-management-instructions-dynamics/aad-properties.png" alt-text="Azure Active Directory Properties menu item":::

1. Select **App registrations** from the Azure Active Directory left pane, and then select **New registration** on that page.
1. Enter a meaningful name for the application name.
1. Under **Supported account types**, select **Accounts in any organizational directory**.
1. Under **Redirect URI (optional)**, select **Web** and enter a URI, such as `https://contosoapp1/auth`.
1. Select **Register**.

    :::image type="content" source="media/commercial-marketplace-lead-management-instructions-dynamics/register-an-application.png" alt-text="Register an application page.":::

1. Now that your application is registered, access the application's overview page. Copy the **Application (client) ID** value on that page. Save this value because you'll need to provide it in the publishing portal and in Dynamics 365 to receive leads for your marketplace offer.

    :::image type="content" source="media/commercial-marketplace-lead-management-instructions-dynamics/application-id.png" alt-text="Application (client) ID box.":::

1. Select **Certificates & secrets** from the app's left pane, and select the **New client secret** button. Enter a meaningful description for the client secret, and select the **Never** option under **Expires**. Select **Add** to create the client secret.

    :::image type="content" source="media/commercial-marketplace-lead-management-instructions-dynamics/aad-certificates-secrets.png" alt-text="Certificates & secrets menu item.":::

1. As soon as the client secret is successfully created, copy the **Client secret** value. You won't be able to retrieve the value after you leave the page. Save this value because you'll need to provide it in the publishing portal to receive leads for your marketplace offer. 
1. Select **API permissions** from the app's left pane, and then select **+ Add a permission**.
1. Select **Microsoft APIs**, and then select **Dynamics CRM** as the API.
1. Under **What type of permissions does your application require?**, make sure **Delegated permissions** is selected.
1. Under **Permission**, select the **user_impersonation** check box for **Access Common Data Service as organization users**. Then select **Add permissions**.

    :::image type="content" source="media/commercial-marketplace-lead-management-instructions-dynamics/api-permissions.png" alt-text="Add permissions button.":::

1. After you complete steps 1 through 14 in the Azure portal, go to the [Create an Application User step](/power-platform/admin/manage-application-users) and complete steps 1 through 7. In this step, you'll only create an Application User for the above-created Azure AD-registered application.
1. Go to the "Security settings" section in this article to finish configuring the connection for this user.

### Office 365

If you don't want to use Azure Active Directory, you can register a new user on the Microsoft 365 admin center. You'll be required to update your username and password every 90 days to continue getting leads.

To configure Office 365 for Dynamics 365 Customer Engagement:

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com).
1. Select **Add a user**.

    :::image type="content" source="media/commercial-marketplace-lead-management-instructions-dynamics/ms-365-add-user.png" alt-text="Microsoft 365 admin center Add a user option.":::

1. Create a new user for the lead writer service. Configure the following settings:

    - Enter a username.
    - Enter a password, and clear the **Make this user change their password when they first sign in** option.
    - Select **User (no administrator access)** as the role for the user.
    - Select **Dynamics 365 Customer Engagement Plan** as the product license, as shown in the following screen. You'll be charged for the license you choose. 

Save these values because you'll need to provide the **Username** and **Password** values in the publishing portal to receive leads for your marketplace offer.

:::image type="content" source="media/commercial-marketplace-lead-management-instructions-dynamics/ms-365-new-user.png" alt-text="Microsoft 365 admin center New user pane.":::

## Security settings

The final step is to enable the user you created to write the leads.

1. Sign in to the [Power Platform Admin center](https://admin.powerplatform.microsoft.com/) as a System Administrator.
1. Select **Environments**, and then select an environment from the list.
1. Select **Settings**.
1. Select **Users + permissions**, and then select **Application users**.
1. Select the user that you created in the **Configure user permissions** section of this document. Then select **Edit security roles**.

    :::image type="content" source="media/commercial-marketplace-lead-management-instructions-dynamics/configure-user-permissions.png" alt-text="Screenshot of Configure User Permissions image.":::

1. Search for the role **Microsoft Marketplace Lead Writer**, and select it to assign the user the role.

    :::image type="content" source="media/commercial-marketplace-lead-management-instructions-dynamics/assign-user.png" lightbox="media/commercial-marketplace-lead-management-instructions-dynamics/assign-user.png" alt-text="Screenshot of Assign User image.":::
   
    > [!NOTE]
    > This role is created by the solution that you imported and only has permissions to write the leads and to track the solution version to ensure compatibility.

1. Go back to the **Users + permissions**, and then select **Security Roles**. Search for the role of **Microsoft Marketplace Lead Writer**, and select it.

   :::image type="content" source="media/commercial-marketplace-lead-management-instructions-dynamics/security-role.png" lightbox="media/commercial-marketplace-lead-management-instructions-dynamics/security-role.png" alt-text="Screenshot of Security Role image.":::

1. Select the dropdown to **"Direct User (Basic) access level and Team privileges"** for the **Member's privilege inheritance** as shown in the below screenshot.

    :::image type="content" source="media/commercial-marketplace-lead-management-instructions-dynamics/direct-user.png" lightbox="media/commercial-marketplace-lead-management-instructions-dynamics/direct-user.png" alt-text="Screenshot of Direct User image.":::

1. Select the dropdown to **"Show all tables"** in the **Tables** Tab as shown in the below screenshot.

    :::image type="content" source="media/commercial-marketplace-lead-management-instructions-dynamics/show-tables.png" lightbox="media/commercial-marketplace-lead-management-instructions-dynamics/show-tables.png" alt-text="Screenshot of Show Tables image.":::

1. Search for the **User Entity UI Settings** table under **Core Records** and select the "**User**" privilege dropdown option to Create, Read, and Write permissions for that entity.

    :::image type="content" source="media/commercial-marketplace-lead-management-instructions-dynamics/user-entity-ui-settings.png" lightbox="media/commercial-marketplace-lead-management-instructions-dynamics/user-entity-ui-settings.png" alt-text="Screenshot of User Entity UI Settings image.":::

1. Search for the **System Job** table under **Customization** and select the "**Organization**" privilege dropdown option to Read, Write, and AppendTo permissions for that entity.

    :::image type="content" source="media/commercial-marketplace-lead-management-instructions-dynamics/system-job.png" lightbox="media/commercial-marketplace-lead-management-instructions-dynamics/system-job.png" alt-text="Screenshot of System Job image.":::

1. Select **Save and close**.

## Configure your offer to send leads to Dynamics 365 Customer Engagement

To configure the lead management information for your offer in the publishing portal:

1. Go to the **Offer setup** page for your offer.
1. Under the **Customer leads** section, select **Connect**.

    :::image type="content" source="./media/commercial-marketplace-lead-management-instructions-dynamics/customer-leads.png" alt-text="Customer leads":::

1. In the Connection details pop-up window, select **Dynamics 365 Customer Engagement** for the lead destination.

    :::image type="content" source="media/commercial-marketplace-lead-management-instructions-dynamics/connection-details-lead-destination.png" alt-text="Lead destination box":::

1. Enter the **URL** for the Dynamics 365 instance, such as `https://contoso.crm4.dynamics.com`.
1. Select the method of **Authentication**, either Azure Active Directory or Office 365.
1. If you selected **Azure Active Directory**, enter the **Application (client) ID** (for example, `23456052-aaaa-bbbb-8662-1234df56788f`), **Directory ID** (for example, `12345678-8af1-4asf-1234-12234d01db47`), and **Client secret** (for example, `1234ABCDEDFRZ/G/FdY0aUABCEDcqhbLn/ST122345nBc=`).

    :::image type="content" source="media/commercial-marketplace-lead-management-instructions-dynamics/connection-details-application-id.png" alt-text="Authentication with Azure Active Directory selected":::

1. If you selected **Office 365**, enter the **User name** (for example, `contoso@contoso.onmicrosoft.com`) and **Password** (for example, `P@ssw0rd`).
1. Select **OK**.

To make sure you've successfully connected to a lead destination, select the **Validate** button. If successful, you'll have a test lead in the lead destination.

> [!NOTE]
> You must finish configuring the rest of the offer and publish it before you can receive leads for the offer.








