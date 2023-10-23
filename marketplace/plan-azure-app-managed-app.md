---
title: Plan an Azure managed application for an Azure application offer
description: Learn what is required to create a managed application plan for a new Azure application offer using the commercial marketplace portal in Microsoft Partner Center.
author: macerru
ms.author: macerr
ms.service: marketplace
ms.subservice: partnercenter-marketplace-publisher
ms.topic: conceptual
ms.date: 08/18/2022
---

# Plan an Azure managed application for an Azure application offer

An Azure _managed application_ plan is one way to publish an Azure application offer in the Commercial Marketplace. If you haven't already done so, read [Plan an Azure Application offer for the commercial marketplace](plan-azure-application-offer.md). Managed applications are transactable offers that are deployed and billed via Marketplace. The customer facing listing option is Get It Now. Use Managed application plans to transact Azure application offers via Marketplace. 

With Managed applications publishers can choose to:  

- Enable or disable publisher management access to the resource group in the customer tenant.  
- Give customers full or restricted access to the resource group. 

To enable transactability on the following configuration modes:  

:::image type="content" source="./media/create-new-azure-app-offer/managed-application-configuration.png" alt-text="Diagram of managed application possible configuration modes by enabling and disabling publisher and customer access." lightbox="./media/create-new-azure-app-offer/managed-application-configuration.png":::

## Managed application offer requirements

| Requirements | Details |
| ------------ | ------------- |
| An Azure subscription | Managed applications must be deployed to a customer's subscription |
| Billing and metering | The resources are provided in a customer's Azure subscription. VMs that use the pay-as-you-go payment model are transacted with the customer via Microsoft and billed via the customer's Azure subscription. <br><br> For bring-your-own-license VMs, Microsoft bills any infrastructure costs that are incurred in the customer subscription, but you transact software licensing fees with the customer directly. |
| Customer usage attribution | For more information about customer usage attribution and how to enable it, see [Azure partner customer usage attribution](azure-partner-customer-usage-attribution.md). |
| Deployment package | You'll need a deployment package that will let customers deploy your plan. If you create multiple plans that require the same technical configuration, you can use the same package. For details, see the next section: Deployment package. |

> [!NOTE]
> Managed applications must be deployable through Azure Marketplace. If customer communication is a concern, reach out to interested customers after you've enabled lead sharing.

## Deployment package

The deployment package contains all the template files needed for this plan, as well as any additional resources, packaged as a .zip file.

All Azure applications must include these two files in the root folder of a .zip archive:

- A Resource Manager template file named [mainTemplate.json](/azure/azure-resource-manager/managed-applications/publish-service-catalog-app?tabs=azure-powershell#create-the-arm-template). This template defines the resources to deploy into the customer's Azure subscription. For examples of Resource Manager templates, see [Azure Quickstart Templates gallery](https://azure.microsoft.com/resources/templates/) or the corresponding [GitHub: Azure Resource Manager Quickstart Templates](https://github.com/azure/azure-quickstart-templates) repo.
- A user interface definition for the Azure application creation experience named [createUiDefinition.json](/azure/azure-resource-manager/managed-applications/create-uidefinition-overview). In the user interface, you specify elements that enable consumers to provide parameter values.

Maximum file sizes supported are:

- Up to 1 Gb in total compressed .zip archive size
- Up to 1 Gb for any individual uncompressed file within the .zip archive

> [!TIP]
> Make sure your offer is compliant with our recommended practices by using the [ARM template test toolkit](/azure/azure-resource-manager/templates/test-toolkit#validate-templates-for-azure-marketplace) before publishing your Azure Application.

## Azure regions

You can publish your plan to the Azure public region, Azure Government region, or both. Before publishing to [Azure Government](/azure/azure-government/documentation-government-manage-marketplace-partners), test and validate your plan in the environment as certain endpoints may differ. To set up and test your plan, request a trial account from [Microsoft Azure Government trial](https://azure.microsoft.com/global-infrastructure/government/request/).

You, as the publisher, are responsible for any compliance controls, security measures, and best practices. Azure Government uses physically isolated data centers and networks (located in the U.S. only).

For a list of countries and regions supported by the commercial marketplace, see [Geographic availability and currency support](marketplace-geo-availability-currencies.md).

Azure Government services handle data that is subject to certain government regulations and requirements. For example, FedRAMP, NIST 800.171 (DIB), ITAR, IRS 1075, DoD L4, and CJIS. To bring awareness to your certifications for these programs, you can provide up to 100 links that describe them. These can be either links to your listing on the program directly or links to descriptions of your compliance with them on your own websites. These links visible to Azure Government customers only.

## Choose who can see your plan

You can configure each plan to be visible to everyone (public) or to only a specific audience (private). You can create up to 100 plans and up to 45 of them can be private. You may want to create a private plan to offer different pricing options or technical configurations to specific customers.

You grant access to a private plan using Azure subscription IDs with the option to include a description of each subscription ID you assign. You can add a maximum of 10 subscription IDs manually or up to 10,000 subscription IDs using a .CSV file. Azure subscription IDs are represented as GUIDs and letters must be lowercase.

Private plans are not supported with Azure subscriptions established through a reseller of the Cloud Solution Provider program (CSP). For more information, see [Private offers in the Microsoft commercial marketplace](private-plans.md).

> [!NOTE]
> If you publish a private plan, you can change its visibility to public later. However, once you publish a public plan, you cannot change its visibility to private.

## Define pricing

You must provide the per-month price for each plan. This price is in addition to any Azure infrastructure or pay-as-you-go software costs incurred by the resources deployed by this solution.

In addition to the per-month price, you can also set prices for consumption of non-standard units using [metered billing](marketplace-metering-service-apis.md). You may set the per-month price to zero and charge exclusively using metered billing if you like.

Prices are set in USD (USD = United States Dollar) and are converted into the local currency of all selected markets using the current exchange rates when saved. Pricing is published in local currency and is not updated as exchange rates fluctuate. To specify customer prices for each market, export the prices from the pricing and availability page, update the respective market and currency, save, and import the file. For more information, see [How we convert currencies](marketplace-geo-availability-currencies.md).

## Publisher Management 

Enabling management access gives publisher access to the managed resource group that hosts your application in the customer tenant. If you choose to enable publisher management access, you will need to specify the Azure tenant and Principal ID that will manage the application.  Disabling management access fully removes management and Read access to the managed resource group and its resources. 

> [!NOTE]
> Publisher management cannot be modified after the plan is published to live in marketplace. 

## Just in time (JIT) access

JIT access enables you to request elevated access to a managed application's resources for troubleshooting or maintenance. You always have read-only access to the resources, but for a specific time period you can have greater access. For more information, see [Enable and request just-in-time access for Azure Managed Applications](/azure/azure-resource-manager/managed-applications/request-just-in-time-access).

> [!NOTE]
> Be sure to update your `createUiDefinition.json` file in order to support this feature.

## Choose who can manage the application

This option is only available when Publisher Management is enabled.  

When Publisher Management is enabled you must indicate who can manage a managed application in each of the selected clouds: _Public Azure_ and _Azure Government Cloud_. Collect the following information:

- **Azure Active Directory Tenant ID** – The Azure AD Tenant ID (also known as directory ID) containing the identities of the users, groups, or applications you want to grant permissions to. You can find your Azure AD Tenant ID on the Azure portal, in [Properties for Azure Active Directory](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties).
- **Authorizations** – Add the Azure Active Directory object ID of each user, group, or application that you want to be granted permission to the managed resource group. Identify the user by their Principal ID, which can be found at the [Azure Active Directory users blade on the Azure portal](https://portal.azure.com/#blade/Microsoft_AAD_IAM/UsersManagementMenuBlade/AllUsers).

For each principal ID, you will associate one of the Azure AD built-in roles (Owner or Contributor). The role you select describes the permissions the principal will have on the resources in the customer subscription. For more information, see [Azure built-in roles](/azure/role-based-access-control/built-in-roles). For more information about role-based access control (RBAC), see [Get started with RBAC in the Azure portal](/azure/role-based-access-control/overview).

> [!NOTE]
> Although you may add up to 100 authorizations per Azure region, we recommend you create an Active Directory user group and specify its ID in the "Principal ID." This lets you add more users to the management group after the plan is deployed and reduces the need to update the plan just to add more authorizations.

## Customer Access 

Enabling customer access gives customers full access to the managed resource group deployed to their Azure tenant. Restricting Access with deny assignments disables customer access to the managed resource group in their Azure tenant. Note that Disabling customer access with deny assignment removes customer access but allows publishers to customize allowed customer actions.  

> [!NOTE]
> Customer Access cannot be modified after the offer is live in marketplace. 

## Deployment mode

You can configure a managed application plan to use either the **Complete** or **Incremental** deployment mode. In complete mode, a redeployment of the application by the customer results in removal of resources in the managed resource group if the resources are not defined in the [mainTemplate.json](/azure/azure-resource-manager/managed-applications/publish-service-catalog-app?tabs=azure-powershell#create-the-arm-template). In incremental mode, a redeployment of the application leaves existing resources unchanged. To learn more, see [Azure Resource Manager deployment modes](/azure/azure-resource-manager/templates/deployment-modes).

## Notification endpoint URL

You can optionally provide an HTTPS Webhook endpoint to receive notifications about all CRUD operations on managed application instances of a plan.

Azure appends `/resource` to the end of your webhook URI before calling it. So, your webhook URL must end in `/resource`, although it should not be included in the URI entered into the **Notification Endpoint URL** box in Partner Center. For example, entering `https://contoso.com` as the Notification Endpoint URI results in a call to `https://contoso.com/resource`.

When listening for events from your managed app notifications, make sure you listen to `https://<url>/resource` and not the set URL alone. For a sample notification, see [Notification schema](/azure/azure-resource-manager/managed-applications/publish-notifications#notification-schema).

## Customize allowed customer actions (optional)

You can optionally specify which actions customers can perform on the managed resources in addition to the `*/read` actions that is available by default.

If you choose this option, you need to provide either the control actions or the allowed data actions, or both. For more information, see [Understanding deny assignments for Azure resources](/azure/role-based-access-control/deny-assignments). For available actions, see [Azure Resource Manager resource provider operations](/azure/role-based-access-control/resource-provider-operations). For example, to permit consumers to restart virtual machines, add `Microsoft.Compute/virtualMachines/restart/action` to the allowed actions.


## Policy settings

You can apply [Azure Policies](/azure/governance/policy/) to your managed application to specify compliance requirements for the deployed solution. For policy definitions and the format of the parameter values, see [Azure Policy Samples](/azure/governance/policy/samples/index).

You can configure a maximum of five policies, and only one instance of each Policy type. Some policy types require additional parameters.

| Policy type | Policy parameters required |
| ------------ | ------------- |
| Azure SQL Database Encryption | No |
| Azure SQL Server Audit Settings | Yes |
| Azure Data Lake Store Encryption | No |
| Audit Diagnostic Setting | Yes |
| Audit Resource Location compliance | No |

For each policy type you add, you must associate Standard or Free Policy SKU. The Standard SKU is required for audit policies. Policy names are limited to 50 characters.

## Next steps

- [Create an Azure application offer](azure-app-offer-setup.md)

**Video tutorial**

- [Azure Managed Applications Overview](https://go.microsoft.com/fwlink/?linkid=2196308)



