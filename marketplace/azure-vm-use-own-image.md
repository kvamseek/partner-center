---
title: Create an Azure virtual machine offer on Azure Marketplace using your own image
description: Publish a virtual machine offer to Azure Marketplace using your own image.
ms.service: marketplace 
ms.subservice: partnercenter-marketplace-publisher
author: mingshen-ms
ms.author: mingshen
ms.topic: how-to
ms.date: 11/10/2021
---

# Create a virtual machine using your own image

This article describes how to publish a virtual machine (VM) image that you built on your premises.

## Bring your image into Azure

Upload your VHD to an Azure Compute Gallery (formerly know as Shared Image Gallery).

1. On the Azure portal, search for **Azure Compute Galleries**.
2. Create or use an existing Azure Compute Gallery. We suggest you create a separate Azure Compute Gallery for images being published to the Marketplace.
3. Create or use an existing image definition.
4. Select **Create a version**.
5. Choose the region and image version.
6. If your VHD is not yet uploaded to Azure portal, choose **Storage blobs (VHDs)** as the **Source**, then **Browse**. You can create a **storage account** and **storage container** if you haven’t created one before. Upload your VHD.
7. Select **Review + create**. Once validation finishes, select **Create**.

> [!TIP]
> Publisher account must have “Owner” access to publish the Azure Compute Gallery Image. If required, follow the steps in the following section, **Set the right permissions**, to grant access.

## Set the right permissions

If your Partner Center account is the owner of the subscription hosting an Azure Compute Gallery, nothing further is needed for permissions. If you are not sure, refer to these steps to [confirm the right permissions are set](#confirm-your-permissions).
If you only have read access to the subscription, use one of the following two options.
> [!NOTE]
> If you receive an error that indicates that we were unable to access your gallery image upon publishing or when selecting an image version from your compute gallery in Partner Center, then you will need to follow the steps below. 

### Option one – Ask the owner to grant owner permission

Steps for the owner to grant owner permission:

1. Log in to the Azure subscription that contains your Azure compute gallery and associated images. 
1. Search for Azure compute galleries and select the gallery that hosts your images.
1. In the **Overview** page of your Azure compute gallery, click on the link to your subscription. 
1. Select **Access control** (IAM) on the left panel.
1. Go to the **Role assignments** tab.  
1. Click on **+Add** -> **Add role assignment**. 
3. Select **Add**, then **Add role assignment**.<br>
    :::image type="content" source="media/create-vm/add-role-assignment.png" alt-text="The add role assignment window is shown.":::
1. For **Role**, select **Owner** and click **Next**.
1. For **Assign access to**, select **User, group, or service principal**.
1. For Members, click +**Select members** and add the email of the person or group that will be publishing the image through Partner Center. 
1. Select **Next -> Review + assign**.

> [!TIP]
> If you experience any issues granting permissions via Azure portal, try option 2 detailed below.  

### Option Two – Run a command

Ask the owner to run either one of these commands. Regardless of which command you use, be sure to specify the SusbscriptionId with the subscription that contains your Azure compute gallery).
```azurecli
az login
az provider register --namespace Microsoft.PartnerCenterIngestion --subscription {subscriptionId}
```

```powershell
Connect-AzAccount
Select-AzSubscription -SubscriptionId {subscriptionId}
Register-AzResourceProvider -ProviderNamespace Microsoft.PartnerCenterIngestion
```

## Confirm your permissions

Run the following command in Azure CLI to verify your permissions are correctly set.  

```azurecli
az login 
az provider show --namespace Microsoft.PartnerCenterIngestion --subscription {subscriptionId} 
```

Upon running the above command, ensure that the RegistrationState says “Registered”. 

```azurecli
"namespace": "Microsoft.PartnerCenterIngestion",
"registrationPolicy": "RegistrationRequired",
"registrationState": "Registered",
```

## Next steps

- [Test your VM image](azure-vm-image-test.md) to ensure it meets Azure Marketplace publishing requirements (optional).
- If you don't want to test your VM image, sign in to [Partner Center](https://go.microsoft.com/fwlink/?linkid=2165935) and publish the Azure Compute Gallery Image.
- If you encountered difficulty creating your new Azure-based VHD, see [VM FAQ for Azure Marketplace](azure-vm-faq.yml).


