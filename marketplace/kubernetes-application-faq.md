---
title: Frequently asked questions about Kubernetes applications
description: Kubernetes application FAQ to help during the publishing process# Add a meaningful description for search results
author: maanasagovi
ms.author: maanasagovi
ms.service: marketplace
ms.subservice: partnercenter-marketplace-publisher
ms.topic: faq
ms.date:  06/28/2023
---

# Frequently asked questions about Kubernetes applications

Find answers to some common questions about Kubernetes applications.

## When we release a new version of a container offering, what actions should we take? What do our customers who already have our container installed on their cluster need to do?

- **For ISVs**:
  - Test the clean install scenario as you would for the first release. Along with it, test the upgrade scenario.
    - For this, deploy the preview version released before and test the customer scenarios as listed next.
- **For customers**:
  - If autoupgrade is *disabled*, patch the extension using the portal or CLI with the new version.
  - If autoupgrade is *enabled*, the extension upgrade happens automatically without customer interventions. 

## What's the recommended procedure for testing a new release of the CNAB version before it's published?

1. Make sure the HELM chart is functional.
1. Test the CreateUIDef in the Azure portal sandbox.
1. Feed the output from the Azure portal sandbox for the CreateUIDef to the ARM template and then deploy it.
   - The only deployment that can fail is the extension deployment with version unavailability. 

## Is there a way to upgrade a customer's plan without redeploying the container?

**Scenario**:

- Customer installed our container on June 1 using the "Free plan" and ran it for a month. After that month, we agreed on a price per core. Can we "migrate" the customer to a paid private plan without the customer needing to take an action to redeploy? In the ideal world, they would just accept the price change based on the new plan. 

For a case like this, there's no migration between plans; the customer must deploy the new plan.

## How can I mass deploy a container offering from the AKS marketplace that works with Terraform?

The [azurerm_kubernetes_cluster_extension](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fregistry.terraform.io%2Fproviders%2Fhashicorp%2Fazurerm%2F3.61.0%2Fdocs%2Fresources%2Fkubernetes_cluster_extension&data=05%7C01%7Catchub%40microsoft.com%7C1ba7863ea3c94f235ea808db6e071697%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C638224749065067556%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C3000%7C%7C%7C&sdata=HNrKND1JKsO92AZB5%2FGWoz37H91XdM30%2BZmjmhu4KCg%3D&reserved=0) (managedClusters) can be used to deploy the offering with Terraform.

## Is there a way of mass-deploying the offering if Terraform isn't in the picture? 

Yes - Azure policy is recommended!

## What happens to the container offering once the contract expires? Would the container in the customer's cluster keep on running, or is it handled differently? 

The extension/deployment continues to exist until explicitly deleted by the customer. The extension infrastructure isn't aware of external contracts unless the logic is embedded into the billing or application. 

