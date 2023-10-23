---
title: Troubleshoot issues while packaging a Kubernetes application-based Container offer
description: Learn about potential issue and solutions when packaging a Kubernetes application based Container offer in Microsoft AppSource.
ms.service: marketplace 
ms.subservice: partnercenter-marketplace-publisher
ms.topic: article
author: maanasagovi
ms.author: maanasagovi
ms.date: 04/04/2023
---

# Troubleshoot issues while packaging a Kubernetes application-based Container offer

This article describes troubleshooting steps when packaging a Kubernetes Container offer. Read on for solutions to common issues.

## Packaging fails with "ResourceGroup AllowExisting must be set to true in the CreateUIDefinition's config" error

This error occurs if the parameters > config > basics > resourceGroup > allowExisting property in the `createUiDefinition.json` file doesn't exist or isn't set to true.

To fix this error, ensure the property is set to true as shown in the following example:

:::image type="content" source="./media/azure-container/resource-group.png" alt-text="Screenshot of createUiDefinition.json file with appropriate parameters.":::

By setting the `allowExisting` property to true, your application can be deployed to a resource group, which isn't empty. For a sample CreateUIDefinition file, see the example at [createUiDefinition.json](https://github.com/Azure-Samples/kubernetes-offer-samples/blob/main/samples/k8s-offer-azure-vote/createUIDefinition.json).

## Error parsing artifacts from your CNAB bundle 

This error occurs when an old packaging tool is being used and there's an issue with the artifacts that prevents you from packaging and publishing your CNAB bundle. If this error occurs, update your container-package-app tool to the latest docker image, repackage your application, and try to publish again. For more information, see [Use the container packaging tool](azure-container-technical-assets-kubernetes.md?tabs=linux#use-the-container-packaging-tool) section.

## Internal operation error

This error occurs when there's a platform issue (that is, the platform isn't functioning as expected). If this error occurs, try resubmitting your offer. 

Example of the error message:

`PublisherId:{dbObject.PublisherId}, OfferId:{dbObject.OfferId}, CorrelationId:{dbObject.CorrelationId}.`

## Docker error

If this error occurs, try upgrading to the latest version of docker engine. To upgrade to the latest version follow the instructions outlined here: [upgrade docker engine](https://docs.docker.com/engine/install/).
