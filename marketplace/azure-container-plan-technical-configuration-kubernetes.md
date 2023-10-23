---
title: Set plan technical configuration for a Kubernetes application based Container offer in Microsoft AppSource.
description: Set plan technical configuration for a Kubernetes application based Container offer in Microsoft AppSource.
ms.service: marketplace 
ms.subservice: partnercenter-marketplace-publisher
ms.topic: article
author: nickomang
ms.author: nickoman
ms.date: 09/28/2022
---

# Set plan technical configuration for an Azure Kubernetes offer

After you submit the offer, your Cloud Native Application Bundle (CNAB) is copied to Azure Marketplace in a specific public container registry. All requests from Azure users to use your module are served from the Azure Marketplace public container registry, not your private container registry.

For more, see [Prepare Azure Kubernetes technical assets](azure-container-technical-assets-kubernetes.md).

## Setting cluster extension type name

[Cluster extensions](/azure/aks/cluster-extensions) enable an Azure Resource Manager driven experience for your application. The following limitations apply when setting the cluster extension type name value:

- You must provide the cluster extension type name in the format of 'PublisherName.ApplicationName'.
- The name should be unique across all your offers and plans.
- You cannot modify this value once the plan is published to *Preview*.
- The maximum allowed length is 50 characters.

## Selecting CNAB bundle

Your payload must be hosted in a private Azure Container Registry (ACR). Use this page to provide reference information for your Cloud Native Application Bundle (CNAB) bundle inside your Azure Container Registry. After you submit the offer for publishing, your bundle is copied to Azure Marketplace in a specific public container registry. All requests from Azure users to use your offer are served from the Azure Marketplace public container registry, not your private container registry.

Select **Add CNAB Bundle** to select the payload reference and enter the cluster extension type like so:

:::image type="content" source="./media/azure-container/add-cnab-inline.png" alt-text="An image showing the Technical configuration screen in the Azure portal. A pane showing the CNAB bundle's information is showing, and the Add CNAB Bundle button is highlighted." lightbox="./media/azure-container/add-cnab-full.png":::

:::image type="content" source="./media/azure-container/cnab-bundle.png" alt-text="Screenshot illustrating technical configuration of a sample plan, with the container CNAB bundle details.":::

> [!NOTE]
> You can save and then choose to Review and publish the offer. All minor updates will be auto-updated for customer deployments, whereas major updates need customer consent to update.

## Next steps

- To **Co-sell with Microsoft** (optional), select it in the left-nav menu. For details, see [Co-sell partner engagement](../co-sell-overview.md?context=%2fazure%2fmarketplace%2fcontext%2fcontext).
- If you're not setting up either of these or you've finished, it's time to [Review and publish your offer](review-publish-offer.md).
