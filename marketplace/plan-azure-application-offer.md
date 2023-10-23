---
title: Plan an Azure Application offer for the commercial marketplace
description: Plan an Azure application offer for Azure Marketplace using Partner Center.
author: macerru
ms.author: macerr
ms.service: marketplace
ms.subservice: partnercenter-marketplace-publisher
ms.topic: tutorial
ms.date: 08/18/2022
---

# Plan an Azure Application offer

Azure Application is the offer type to sell and deploy solutions hosted in your customer’s Azure tenant. Azure applications automate the deployment and configuration of your application by using Azure Resource Manager (ARM) template to include VMs, containers, networking, storage and many other Azure resources. Azure Application offers can be configured as Solution Templates or Managed Applications:  

- [Managed applications](plan-azure-app-managed-app.md)  plans are transactable in the commercial marketplace and can be managed by the publisher or the customer. When managed by the publisher, an identity in the publisher's tenant has access to the resource group in the customer subscription. When managed by the customer, the publisher has no access to the customer tenant. Customer access can be fully enabled or restricted by using deny assignments and allowed actions. Use the managed application plan to sell an Azure Application via Marketplace. 

- [Solution templates](plan-azure-app-solution-template.md)  are not transactable in the commercial marketplace, but they can be used to deploy paid VM offers that are billed through the commercial marketplace. Use the solution template plan type when your solution leverages an ARM template for deployment and is not transacted via Marketplace 
An Azure application offer can include multiple plans and plan types.  

## Listing options

After your offer is published, the listing options for your offer appear as a button in the upper-left corner of your offer's listing page. For example, the following screenshot shows an offer listing page in Azure Marketplace with the _Get It Now_ button. If you had chosen to offer a test drive, the _Test Drive_ button would also be shown.

:::image type="content" source="media/create-new-azure-app-offer/azure-app-listing-page.png" alt-text="Illustrates a listing page on Azure Marketplace.":::

## Test drive

You can choose to enable a test drive for your Azure Application offer that lets customers try your offer before purchasing it. To learn more about test drives, see [What is a test drive?](what-is-test-drive.md). For information about configuring different kinds of test drives, see [Test drive technical configuration](test-drive-technical-configuration.md).

You can also read about [test drive best practices](https://github.com/Azure/AzureTestDrive/wiki/Test-Drive-Best-Practices) and download the [Test drives overview](https://assetsprod.microsoft.com/mpn/azure-marketplace-appsource-test-drives.pdf) PDF (make sure your pop-up blocker is off).

> [!NOTE]
> Azure applications are implemented using an Azure Resource Manager template, the only type of test drive available for an [Azure Application is an Azure Resource Manager based test drive](azure-resource-manager-test-drive.md).

## Customer leads

The commercial marketplace will collect leads with customer information so you can access them in the [Referrals workspace](https://partner.microsoft.com/dashboard/referrals/v2/leads) in Partner Center. Leads will include information such as customer details along with the offer name, ID, and online store where the customer found your offer.

You can also choose to connect your CRM system to your offer. The commercial marketplace supports Dynamics 365, Marketo, and Salesforce, along with the option to use an Azure table or configure an HTTPS endpoint using Power Automate. For detailed guidance, see [Customer leads from your commercial marketplace offer](partner-center-portal/commercial-marketplace-get-customer-leads.md).

## Categories and subcategories

You can choose at least one and up to two categories for grouping your offer into the appropriate commercial marketplace search areas. You can choose up to two subcategories for each primary and secondary category. For a full list of categories and subcategories, see [Offer Listing Best Practices](marketplace-categories-industries.md#categories).

## Legal contracts

To simplify the procurement process for customers and reduce legal complexity for software vendors, Microsoft offers a standard contract you can use for your offers in the commercial marketplace. When you offer your software under the standard contract, customers only need to read and accept it one time, and you don't have to create custom terms and conditions.

If you choose to use the standard contract, you have the option to add universal amendment terms and up to 10 custom amendments to the standard contract. You can also use your own terms and conditions instead of the standard contract. You'll manage these details in the **Properties** page. For detailed information, see [Standard contract for Microsoft commercial marketplace](standard-contract.md).

> [!NOTE]
> After you publish an offer using the standard contract for the commercial marketplace, you cannot use your own custom terms and conditions. It is an "or" scenario. You either offer your solution under the standard contract or your own terms and conditions. If you want to modify the terms of the standard contract you can do so through Standard Contract Amendments.

## Offer listing details

When you create a new Azure Application offer in Partner Center, you'll enter text, images, optional videos, and other details on the Offer listing page. This is the information that customers will see when they discover your offer listing in Azure Marketplace, as shown in the following example.

:::image type="content" source="media/create-new-azure-app-offer/example-azure-marketplace-app.png" alt-text="Illustrates how this offer appears in Azure Marketplace.":::

#### Call-out descriptions

1. Logo
2. Categories
3. Support address (link)
4. Terms of use
5. Privacy policy address (link)
6. Offer name
7. Summary
8. Description
9. Screenshots/videos

The following screenshot shows how offer information appears in the Azure portal:

:::image type="content" source="media/create-new-azure-app-offer/example-virtual-machine-container-iot-edge-saas.png" alt-text="Illustrates how this offer appears in the Azure portal." lightbox="media/create-new-azure-app-offer/example-virtual-machine-container-iot-edge-saas.png":::

#### Call-out descriptions

1. Title
2. Description
3. Useful links
4. Screenshots

> [!NOTE]
> Offer listing content is not required to be in English if the offer description begins with the phrase "This application is available only in [non-English language]".

To help create your offer more easily, prepare some of these items ahead of time. The following items are required unless otherwise noted.

- **Name**: This name will appear as the title of your offer listing in the commercial marketplace. The name may be trademarked. It can't contain emojis (unless they're the trademark and copyright symbols) and must be limited to 200 characters.
- **Search results summary**: Describe the purpose or function of your offer as a single sentence, in plain text with no line breaks, in 100 characters or less. This summary is used in the commercial marketplace listing(s) search results.
- **Short description**: Provide up to 256 characters of plain text. This summary will appear on your offer's details page.
- **Description**: This description will be displayed in the Azure Marketplace listing(s) overview. Consider including a value proposition, key benefits, intended user base, any category or industry associations, in-app purchase opportunities, customer need or pain that the offer addresses, any required disclosures, and a link to learn more.

    This text box has rich text editor controls that you can use to make your description more engaging. You can also use HTML tags to format your description. You can enter up to 5,000 characters of text in this box, which includes HTML markup and spaces. For additional tips, see [Write a great app description](/windows/uwp/publish/write-a-great-app-description) and [HTML tags supported in the commercial marketplace offer descriptions](supported-html-tags.md).

- **Search keywords** (optional): Provide up to three search keywords that customers can use to find your offer in the online store. For best results, also use these keywords in your description. You don't need to include the offer **Name** and **Description**. That text is automatically included in search.
- **Privacy policy link**: The URL for your company's privacy policy. You must provide a valid privacy policy and are responsible for ensuring your app complies with privacy laws and regulations.
- **Useful links** (optional): You can provide links to various resources for users of your offer. For example, forums, FAQs, and release notes.
- **Contact information**: You must designate the following contacts from your organization:
  - **Support contact**: Provide the name, phone, and email for Microsoft partners to use when your customers open tickets. You must also include the URL for your support website.
  - **Engineering contact**: Provide the name, phone, and email for Microsoft to use directly when there are problems with your offer. This contact information isn't listed in the commercial marketplace.
  - **CSP Program contact** (optional): Provide the name, phone, and email if you opt in to the Cloud Solution Provider (CSP) program, so those partners can contact you with any questions. You can also include a URL to your marketing materials.
- **Media – Logos**: Provide a PNG file for the **Large** size logo. Partner Center will use this to create a **Small** and a **Medium** logo. You can optionally replace these with different images later.
  - Large (from 216x216 to 350x350 px, required)
  - Medium (90x90 px, optional)
  - Small (48x48 px, optional)

  These logos are used in different places in the online stores:
  - The Small logo appears in Azure Marketplace search results.
  - The Medium logo appears when you create a new resource in Microsoft Azure.
  - The Large logo appears on your offer listing page in Azure Marketplace.

  Follow these guidelines for your logos:

  - The Azure design has a simple color palette. Limit the number of primary and secondary colors on your logo.
  - The theme colors of the portal are white and black. Don't use these colors as the background color for your logo. Use a color that makes your logo prominent in the portal. We recommend simple primary colors.
  - If you use a transparent background, make sure that the logo and text aren't white, black, or blue.
  - The look and feel of your logo should be flat and avoid gradients in the logo or background. Don't place text on the logo, not even your company or brand name. Blurry images will cause your submission to be rejected.
  - Make sure the logo isn't stretched.

- **Media - Screenshots** (optional): We recommend that you add screenshots that show how your offer works. You can add up to five screenshots with the following requirements, that show how your offer works:
  - 1280x720 pixels
  - .PNG file
  - Must include a caption
- **Media – Videos** (optional): You can add up to five videos with the following requirements, that demonstrate your offer:
  - Name
  - URL: Must be hosted on YouTube or Vimeo only.
  - Thumbnail: 1280x720 .PNG file

> [!NOTE]
> Your offer must meet the general [commercial marketplace certification policies](/legal/marketplace/certification-policies#100-general.md) to be published to the commercial marketplace.

## Preview audience

A preview audience can access your offer prior to being published live in the online stores in order to test the end-to-end functionality before you publish it live.

> [!NOTE]
> A preview audience differs from a private plan. A private plan is one you make available only to a specific audience you choose. This enables you to negotiate a custom plan with specific customers.

You define the preview audience using Azure subscription IDs, along with an optional description for each. Neither of these fields can be seen by customers.

## Technical configuration

For managed applications that emit metering events using the [Marketplace metering service APIs](marketplace-metering-service-apis.md), you must provide the identity that your service will use when emitting metering events.

For managed applications that emit metering events using the [Marketplace metering service APIs](marketplace-metering-service-apis.md), you must provide the identity that your service will use when emitting metering events.

- **Azure Active Directory tenant ID** (required): Inside the Azure portal, you must [create an Azure Active Directory (AD) app](/azure/active-directory/develop/howto-create-service-principal-portal) so we can validate the connection between our two services is behind an authenticated communication. To find the [tenant ID](/azure/active-directory/develop/howto-create-service-principal-portal#sign-in-to-the-application) for your Azure Active Directory (Azure AD) app, to the [App registrations](https://portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade) blade in your Azure Active Directory. In the **Display name** column, select the app. Then look for **Properties**, and then for the **Directory (tenant) ID** (for example `50c464d3-4930-494c-963c-1e951d15360e`).
- **Azure Active Directory application ID** (required): You also need your [application ID](/azure/active-directory/develop/howto-create-service-principal-portal#sign-in-to-the-application) and an authentication key. To find your application ID, go to the [App registrations](https://portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade) blade in your Azure Active Directory. In the **Display name** column, select the app and then look for the **Application (client) ID** (for example `50c464d3-4930-494c-963c-1e951d15360e`). To find the authentication key, go to **Settings** and select **Keys**. You'll need to provide a description and duration and will then be provided a number value.

> [!NOTE]
> The Azure application ID will be associated to your publisher ID and can only be re-used within this publisher account.

## Additional sales opportunities

You can choose to opt into Microsoft-supported marketing and sales channels. When creating your offer in Partner Center, you'll see two tabs toward the end of the process:

- **Resell through CSPs**: Use this option to allow Microsoft Cloud Solution Providers (CSP) partners to resell your solution as part of a bundled offer. See [Cloud Solution Provider program](./cloud-solution-providers.md) for more information.
- **Co-sell with Microsoft**: This option lets Microsoft sales teams consider your IP co-sell eligible solution when evaluating their customers' needs. For detailed information on how to prepare your offer for evaluation, see [Co-sell option in the commercial marketplace](../co-sell-configure.md). For details about IP co-sell requirements, see [Requirements for co-sell status](/legal/marketplace/certification-policies#3000-requirements-for-co-sell-status). For more information about marketing your offer through the Microsoft CSP partner channels, see [Cloud Solution Providers](cloud-solution-providers.md).

To learn more, see [Grow your cloud business with Azure Marketplace](https://azuremarketplace.microsoft.com/sell).

## Plans

Azure Application offers require at least one plan. A plan defines the solution scope and limits, and the associated pricing, if applicable. You can create multiple plans for your offer to give your customers different technical and pricing options.

For general guidance about plans, including pricing models, and private plans, see [Plans and pricing for commercial marketplace offers](plans-pricing.md). The following sections discuss additional information specific to Azure Application plans.

### Types of plans

There are two kinds of Azure application plans: _solution template_ and _managed application_. Both plan types support automating the deployment and configuration of a solution beyond a single virtual machine (VM). You can automate the process of providing multiple resources, including VMs, networking, and storage resources to provide complex solutions, such as IaaS solutions. Both plan types can employ many different kinds of Azure resources, including but not limited to VMs.

- **Managed application** plans enable you to sell and deliver a solution via marketplace. The solution can either be  managed by the publisher or by the customer. Managed applications have the same capabilities as solution template plans, with some key differences: 
    - The resources are deployed to a resource group that can be managed by either the publisher or the customer. If it is managed by the publisher, the resource group is present in the consumer’s subscription, but an identity in the publisher’s tenant has access to the resource group.
    - The publisher can configure the resource group to give customers full or restricted access to the resource group. 
   - Monthly and Billing Metered Transactions are supported through the commercial marketplace. As a publisher you can use Private offers to create custom priced deals with custom durations and terms. Learn more [here](isv-customer.md#create-a-private-offer-for-a-customer).
      Use the managed application plan type to sell Azure applications via marketplace or when you or your customer requires that the solution is managed by a partner. 
   
- **Solution template** plans are one of the main ways to publish a solution in the commercial marketplace. Solution template plans aren't transactable in the commercial marketplace, but they can be used to deploy paid VM offers that are billed through the commercial marketplace. Use the solution template plan type when the customer will manage the solution and the transactions are billed through another plan. For more information about building solution templates, see [What is Azure Resource Manager?](/azure/azure-resource-manager/management/overview)

## Usage of Azure Kubernetes Service (AKS) and containers in managed application

**Solution templates:** The Solution Template offers are not changeable by the publisher after customer deployment. Therefore, containers and Azure Kubernetes Service (AKS) resources are not currently allowed in this offer category.

**Managed applications:** See [Reference Kubernetes Apps in Azure Apps](referencing-kubernetes-apps-azure-app.md) to learn how to reference Container offers in a Managed application.   
Referencing containers and Azure Kubernetes Service (AKS) resources from within the managed app *<u>is provisionally allowed</u>* since Managed Applications can be configured to allow the publisher to access and control the resources created during deployment in the customer’s subscription.  

### Rules and known issues for AKS and containers in managed applications

- AKS Node Resource Group does not inherit the Deny Assignments as a part of the Azure Managed Application. This means the customer will have full access to the AKS Node Resource Group that is created by the AKS resource when it is included in the managed application while the Managed Resource Group will have the proper Deny Assignments.

- The publisher can include Helm charts and other scripts as part of the Azure Managed Application. However, the offer will be treated like a regular managed application deployment and there will be no automatic container-specific processing or Helm chart installation at deployment time. It is the publisher’s responsibility to execute the relevant scripts, either at deployment time, using the usual techniques such as VM custom script extension or Azure Deployment Scripts, or after deployment.

- Same as with the regular Azure Managed Application, it is the publisher’s responsibility to ensure that the solution deploys successfully and that all components are properly configured, secured, and operational. For example, publishers can use their own container registry as the source of the images but are fully responsible for the container security and ongoing vulnerability scanning.


## Next steps

- To plan a solution template, see [Plan a solution template for an Azure application offer](plan-azure-app-solution-template.md).
- To plan an Azure managed application, see [Plan an Azure managed application for an Azure application offer](plan-azure-app-managed-app.md).

**Video tutorials and hands-on labs**

- [Mastering Azure Managed Application offers](https://go.microsoft.com/fwlink/?linkid=2201395)
- [Metered Billing for Azure Managed Applications – Demo](https://go.microsoft.com/fwlink/?linkid=2196412)
- [Azure Managed Application Deployment Package Overview](https://go.microsoft.com/fwlink/?linkid=2196244)


