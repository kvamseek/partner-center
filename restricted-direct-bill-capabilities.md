---
title: Restricted direct-bill capabilities
ms.topic: article
ms.date: 8/18/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-billing
description: Learn about Cloud Solution Provider (CSP) direct-bill partner requirements and what to do to avoid capabilities being restricted. Find out if your capabilities have been restricted.
author: parthpandyamsft
ms.author: parthp
---

# Restricted direct-bill capabilities and the requirements needed for CSP direct-bill partners

**Appropriate roles**: Global admin

## Overview

Direct-bill partners must meet the new [requirements](direct-partner-new-requirements.md) to remain in the Cloud Solution Provider (CSP) direct-bill partner program. Otherwise, their access to direct-bill capabilities will eventually be restricted, and they'll no longer be able perform tasks such as making new purchases for their customers.

> [!NOTE]
> Direct-bill partners who do not meet the new requirements for the CSP direct-bill partner program will be informed by Microsoft when their direct-bill capabilities will be restricted. This applies to all direct-bill partners, whether they have opted for [transition from direct-bill partner to indirect resellers](transition-direct-to-indirect.md) or not.

## How to tell if your direct-bill capabilities has been restricted

To confirm whether access from the direct-bill partner tenant to direct-bill capabilities has been restricted, follow these steps.

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select the **Settings** (gear) icon.

2. Select **Account settings**, then select **Legal Profile**.

3. Under **Program info**, look for **Microsoft Cloud Solution Provider status**.

4. If the program status has value **restricted**, that means that your direct-bill partner tenant's access to direct-bill capabilities has been restricted.

## Affected direct-bill capabilities

If your direct-bill capabilities have been restricted, you can no longer make new purchases for your customers in Partner Center. This restriction includes:

- Azure subscriptions

- License-based subscriptions

- Adding new add-ons to existing license-based subscriptions

- Making one-time purchases of software and reservation products (for example, software subscriptions, perpetual software, and Azure Reserved Virtual Machine instances).

You also can't use the [Azure partner shared services offer](shared-services.md) under the CSP program to purchase new Azure subscriptions for your own use.

Existing direct-bill subscriptions aren't affected. They remain valid and are autorenewed. You'll continue to be billed directly by Microsoft until they're canceled. You can still manage existing subscriptions in the following ways:

- Suspend existing subscriptions

- Adjust license count of existing license-based subscriptions

- Adjust license count of existing add-ons to a subscription.

    > [!NOTE]
    >You cannot add new add-ons to existing subscriptions because they are treated as a new purchase.

- Deploy new Azure resources and manage existing Azure resources under existing Azure subscriptions. Included are deploying resources that are available through Azure Marketplace and deploying Visual Studio subscriptions.

In addition to new purchases, you can't access the following direct-bill capabilities in Partner Center:

- You can't create new customer tenants. The **Create customer** option under **Customers** page in Partner Center won't be available.

- You can't generate invitations to customers requesting a direct reseller relationship. The **Request a reseller relationship** option under **Customers** page in Partner Center won't be available.

    > [!NOTE]
    >As part of transitioning from direct-bill partner to indirect reseller, if you have already enrolled your direct-bill partner tenant as indirect reseller, you can generate an invitation to a customer requesting an indirect reseller relationship instead.

- You can't create a new sandbox tenant. Each direct-bill partner tenant can create one sandbox tenant for direct-bill API integration. If you haven't created one previously, you aren't allowed to do so after your direct-bill partner capability has been restricted.

## Next steps

- [Additional information on becoming an indirect reseller](https://assetsprod.microsoft.com/csp-directbill-to-indirect-transition.pdf)

- [CSP direct partner new requirements](direct-partner-new-requirements.md)
