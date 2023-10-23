---
title: Prepare the technical assets for Azure application
description: Prepare the technical assets for Azure application using Partner Center.
author: macerru
ms.author: macerr
ms.service: marketplace
ms.subservice: partnercenter-marketplace-publisher
ms.topic: tutorial
ms.date: 06/09/2023
---

# Prepare the technical assets for Azure application

Designing, building, and testing Azure application offers requires technical knowledge of both the Azure platform and the technologies used to build the offer. Your engineering team should have knowledge about the following Microsoft technologies: 

- Basic understanding of [Azure Services](https://azure.microsoft.com/services/). 

- How to [design and architect Azure applications](https://azure.microsoft.com/solutions/architecture/). 

- Learn to configure [customer-deployed ISV solutions](/azure/cloud-adoption-framework/ready/landing-zone/isv-landing-zone?tabs=mg-env-no%2Cminimal)   

- Working knowledge of [Azure Resource Manager](https://azure.microsoft.com/features/resource-manager/) and [JSON](https://www.json.org/). 

- Working knowledge of [Azure Virtual Machines](https://azure.microsoft.com/services/virtual-machines/), [Azure Storage](https://azure.microsoft.com/services/?filter=storage#storage), and [Azure Networking](https://azure.microsoft.com/services/?filter=networking#networking). 

## Technical documentation and resources 

Review the following resources as you plan your Azure application offer for the commercial marketplace. 

- [Understand Azure Resource Manager Templates](/azure/azure-resource-manager/templates/syntax) 
- Getting started: 

  - [Azure Quickstart Templates](https://azure.microsoft.com/resources/templates/) 
  - [Azure templates best practices guide](https://github.com/Azure/azure-quickstart-templates/blob/master/1-CONTRIBUTION-GUIDE/best-practices.md) 
  - [Publish application definition](/azure/azure-resource-manager/managed-applications/publish-service-catalog-app) 
  - [Deploy service catalog app](/azure/azure-resource-manager/managed-applications/deploy-service-catalog-quickstart) 
- Tutorials: 
  - [Create definition files](/azure/azure-resource-manager/managed-applications/publish-service-catalog-app) 

- Samples: 
  - [Azure CLI](/azure/azure-resource-manager/managed-applications/cli-samples)
  - [Azure PowerShell](/azure/azure-resource-manager/managed-applications/powershell-samples)
  - [Managed application solutions](/azure/azure-resource-manager/managed-applications/sample-projects) 
  - [How to publish and configure a Managed applications](https://microsoft.github.io/Mastering-the-Marketplace/ama/)  

- Testing resources 
  - [ARM template test toolkit](/azure/azure-resource-manager/templates/test-toolkit) 

The video [Building Solution Templates, and Managed Applications for Azure Marketplace](/Events/Build/2018/BRK3603) gives a comprehensive introduction to the Azure application offer type: 

## Suggested tools 

Choose one or both of the following scripting environments to help manage your Azure application: 

- [Azure PowerShell](/powershell/azure/) 

- [Azure CLI](/cli/azure) 

We recommend adding the following tools to your development environment: 

- [Azure Storage Explorer](/azure/vs-azure-tools-storage-manage-with-storage-explorer) 

- [Visual Studio Code](https://code.visualstudio.com/) with the following extensions: 

  - Extension: [Azure Resource Manager Tools](https://marketplace.visualstudio.com/items?itemName=msazurermtools.azurerm-vscode-tools) 

  - Extension: [Beautify](https://marketplace.visualstudio.com/items?itemName=HookyQR.beautify) 

  - Extension: [Prettify JSON](https://marketplace.visualstudio.com/items?itemName=mohsen1.prettify-json) 

You can review the available tools on the [Azure Developer Tools](https://azure.microsoft.com/tools/) page. If you're using Visual Studio, see the [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 

## Create the Azure Application

All Azure applications must include these two files in the **root folder of a .zip archive**: 

- An Azure Resource Manager (ARM) template file named [mainTemplate.json](/azure/azure-resource-manager/managed-applications/publish-service-catalog-app?tabs=azure-powershell%22%20%5Cl%20%22create-the-arm-template). This template defines the resources to deploy into the customer's Azure subscription. For examples of Resource Manager templates, see [Azure Quickstart Templates gallery](https://azure.microsoft.com/resources/templates/) or the corresponding [GitHub: Azure Resource Manager Quickstart Templates](https://github.com/azure/azure-quickstart-templates) repo. 

- A user interface definition for the Azure application creation experience named [createUiDefinition.json](/azure/azure-resource-manager/managed-applications/create-uidefinition-overview). In the user interface, you specify elements that enable consumers to provide parameter values. 

 Test your offer’s technical assets prior to publishing using the [ARM template test toolkit](/azure/azure-resource-manager/templates/test-toolkit#validate-templates-for-azure-marketplace)  

## Next steps 

- [Create your Azure application offer](/partner-center/marketplace/azure-app-offer-setup) 


