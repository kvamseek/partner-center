---
title: Add Azure Partner Shared Services
description: Use Azure Partner Shared Services to buy Azure subscriptions for your own use, and to have a uniform method for purchasing, tracking, and managing Azure.
ms.topic: article
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
author: brentserbus
ms.author: brserbus
ms.date: 01/11/2023
---

# Add Azure Partner Shared Services so partners can buy Azure subscriptions for their own use

**Appropriate roles**: Global admin | Admin agent | Sales agent

Azure Partner Shared Services (APSS) is a type of offer for partners in the Cloud Solution Provider (CSP) program, enabling partners to purchase Azure subscriptions for their own use.

APSS creates the opportunity for partners to use a uniform method for purchasing, tracking, and managing Azure in addition to the ability to consolidate their Azure licensing and reselling agreements with Microsoft.

With APSS, partners now have the same flexibility to use Azure subscriptions in CSP as they do in the Microsoft Enterprise Agreement and Web Direct programs, opening up scenarios such as: build development and test environments, deploy internal workloads, and host shared services or multi-tenant applications.

## Create the shared services tenant

To create the shared services tenant, use the following steps:

1. Go to **Settings** > **Account settings** > **Shared services**.

   :::image type="content" source="media/shared-services/account-settings-shared-services.png" lightbox="media/shared-services/account-settings-shared-services.png" alt-text="Screenshot of Account settings > Shared services in Partner Center.":::

2. If you don't already have a shared services tenant, select **Create shared services**.

   :::image type="content" source="media/shared-services/create-shared-services.png" lightbox="media/shared-services/create-shared-services.png" alt-text="Screenshot of the Shared services page in Partner Center with the Create shared services button.":::

   Doing so creates a shared services tenant and purchases the Azure CSP Shared Services subscription, to be used for shared resources and internal workload.

   :::image type="content" source="media/shared-services/create-tenant-purchase-subscription.png" lightbox="media/shared-services/create-tenant-purchase-subscription.png" alt-text="Screenshot of creating the tenant and purchasing a subscription in Partner Center.":::

## About the Azure- Internal/Shared Services offer

- The Azure - Internal/Shared Services subscription is an Azure offer type in CSP accessed through Partner Center that partners get for their own use of Azure.

- Azure Partner Shared Services subscriptions are eligible and can be used to purchase reserved instances (RIs).

- The Azure - Internal/Shared Services offer can only be applied to the shared services tenant.

- The primary use for the Azure - Internal/Shared Services subscription is so that you can use Azure for your own development purposes. The shared tenant you use to provision this offer can't be used for other services such as Office 365 or Dynamics licenses.

You can cancel the subscription like any other subscription.

  To cancel a subscription, use the following steps:

  1. Go to **settings** > **View all settings** > **Shared services**.
  2. Select the Azure - Internal/Shared Services subscription and cancel it.

## Accessing Azure Partner Shared Services consumption details

- Azure consumption is on your CSP invoice and reconciliation file.
- Azure consumption is included as part of *Microsoft Azure* line item in the invoice.
- Detailed consumption information is available in the reconciliation file logged against the tenant that was created for the offer.

## Azure Partner Shared Services pricing

To see the new pricing file for APSS, use the following steps:

1. Go to **Sell** > **Pricing and offers**.
2. Select the current month's price list.

## Marketplace offers and Azure Partner Shared Services

APSS no longer supports Marketplace offers.

To take advantage of the full catalog of Marketplace offers available—not just bring-your-own-license (BYOL) and free services—we recommend that you deploy shared services using web direct Azure subscriptions.

If you have deployed third-party BYOL and free service resources from the Marketplace previously and want to continue using them and to deploy more third-party offerings, you're encouraged to migrate the APSS subscription to web direct. For more information, see [Migrating Existing Azure Subscriptions](/azure/azure-resource-manager/management/move-resource-group-and-subscription).

Partners who use APSS subscription after March 1, 2019 and want to deploy new third-party [BYOL services](https://azuremarketplace.microsoft.com/marketplace/apps?filters=byol) or free services can follow the instructions from ISVs to deploy those services to their APSS subscriptions.

## Next steps

- [Sell software subscriptions through CSP](csp-software-subscriptions.md)
