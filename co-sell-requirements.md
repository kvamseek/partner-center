---
title: Co-sell requirements 
description: Learn about the requirements an offer in the Microsoft commercial marketplace must meet to qualify for co-sell-ready or co-sell incentive status.
ms.service: partner-dashboard 
ms.subservice: partnercenter-referrals
ms.topic: how-to
author: Saksham-PM
ms.author: sasolanki
ms.date: 08/24/2023
---

# Co-sell requirements

**Appropriate roles**: Co-sell solution admin

This article describes the requirements for various levels co-sell status.

- For a list of offer types that support co-sell, see  [Configure co-sell for a commercial marketplace offer](co-sell-configure.md).
- For an overview of co-sell, see [Co-sell with Microsoft sales teams and partners overview](co-sell-overview.md).

##### Co-sell statuses

The following table shows the four co-sell statuses:

| Status | Comment |
| ------------ | ------------- |
| In market | The solution is linked to a commercial marketplace offer that is live in the marketplace, but [requirements for co-sell-ready status](#requirements-for-co-sell-ready-status) _have_ _not_ been met. |
| Co-sell ready | [Requirements for co-sell-ready status](co-sell-requirements.md#requirements-for-co-sell-ready-status) _have_ been met. |
| Azure IP co-sell eligible | Requirements for co-sell-ready status have been met.<br>[Four more requirements](#requirements-for-azure-ip-co-sell-eligible-status) for Azure IP co-sell eligibility have also been met. |
| Business Applications co-sell eligible | This status applies to _Dynamics 365 apps on Dataverse_ and _Power Apps_ offers in the [Microsoft Business Applications ISV Connect program](/azure/marketplace/business-applications-isv-program) and indicates that all [requirements for this status](#requirements-for-business-applications-co-sell-eligible-status) have been met. |

## Requirements for co-sell-ready status

For a solution to achieve co-sell-ready status:

All partners must complete the following steps:

- Have a PartnerID (formerly MPNID) and an active [commercial marketplace account in Partner Center](/azure/marketplace/create-account).
- Have a complete [business profile](./create-a-marketing-profile.md) in Partner Center.
- [Publish the offer on the commercial marketplace](#publish-your-offer-live).
- Provide a sales contact for each co-sell-eligible geography.
- Provide the required listing and document information on [the Co-sell > Solutions page](co-sell-configure.md).

Services partners must complete the following step:

- For Consulting Service solutions (also known as Marketplace offers) of the any _Solution_ type, have at least one solution partner designation in Microsoft AI Cloud Partner Program.

Business Applications independent software vendors (ISVs) must complete the following step:

- Have [ISV Connect program](/azure/marketplace/business-applications-isv-program) enrollment for Dynamics 365 apps on Dataverse and Power Apps and Dynamics 365 Operations Apps solutions.

> [!NOTE]
> Any offer published through the commercial marketplace developer program in Partner Center is eligible for co-sell-ready status if co-sell-ready requirements are met.
>
> Apps and add-ins for Microsoft Office (for Microsoft Teams, Microsoft Outlook, and Microsoft Excel, for example) are not eligible for co-sell-ready status.

### Publish your offer live

To qualify for co-sell-ready status, your offer or solution must be published live to at least one of the online stores: _Azure Marketplace_ or _Microsoft commercial marketplace_.

For information about publishing offers to the commercial marketplace, see [Publishing guide by offer type](/azure/marketplace/publisher-guide-by-offer-type).

If you haven't published an offer in the commercial marketplace before, make sure you have a [commercial marketplace account](/azure/marketplace/create-account).

### Complete the Co-sell > Solutions page

You must provide all the required information on the **Co-sell > Solutions** page, including a one-pager and a pitch deck. We provide templates to help you create these documents.

For more information, see [Configure Co-sell solution](./co-sell-configure.md).

## Requirements for Azure IP co-sell eligible status

_Azure IP co-sell eligible_ status applies to the following offer types:

- Azure Application
- Azure Container
- Azure Virtual Machine
- IoT Edge module
- Software as a service (SaaS)

In addition to the offer type requirements listed below, the solution type for your offer must be "IP" in order to be eligible for Azure IP co-sell eligible status

After achieving co-sell-ready status, there are four more requirements to achieve _Azure IP co-sell eligible_ status:

- Requirement 1: Reach the required revenue threshold.

   At the _organization level_, generate at least USD100,000 of Azure Consumed Revenue over the trailing 12-month period. This threshold can be reached with a combination of Azure solutions. If the offer is transactable in the commercial marketplace, you can meet this requirement by meeting a billed revenue threshold of USD100,000 over the trailing 12-month period.

- Requirement 2: Microsoft technical validation for an Azure-based solution which is subset of RAD review.
   All IPCS eligible solutions must meet the [Azure Marketplace policies](/legal/marketplace/certification-policies), [be primarily platformed in Azure, and pass the Azure platformed technical validation process](/legal/marketplace/certification-policies).
  
- Requirement 3: Provide a reference architecture diagram.

   Upload a reference architecture diagram with your co-sell documents in Partner Center for review. This item is not mandatory for offer types Azure App, Containers, VMs and IoT Edge module. For guidance on creating this diagram, see [Reference architecture diagram](reference-architecture-diagram.md). For information about uploading the diagram, see [Configure co-sell for a commercial marketplace offer](./co-sell-configure.md).

- Requirement 4: Offer Transactability on marketplace. **Effective July 11, 2023**, your new offers (aka solutions) should be transactable on Azure marketplace. This condition is applicable only to get IP co-sell eligible status. 

## Requirements for Business Applications co-sell eligible status

This status applies to IP-based solutions built on Dynamics 365 apps on Dataverse, and Power Apps and Dynamics 365 Operations Apps that are enrolled in the ISV Connect program. However, offers must also complete the requirements for co-sell-ready status (described previously) for Microsoft sellers to be able to co-sell the offer with you.

## What is the difference between a co-sell solution and a commercial marketplace offer?

**Co-sell solution**: A live marketplace offer that a publisher intends to co-sell with Microsoft. The publisher must upload additional co-sell-specific collateral documents with a co-sell solution. That collateral undergoes automated and manual review before determining the co-sell program status the solution can be given. This solution is available in internal Microsoft catalogs along with the uploaded collateral.

**Commercial marketplace offer**: A commercial marketplace is an autonomic sellable unit. An offer can be configured as one of several available offer types. You must have a developer/manager role and a seller account to publish an offer. To learn more, see [Publishing guide by offer type](/azure/marketplace/publisher-guide-by-offer-type).

## Next steps

- [Configure co-sell solution](./co-sell-configure.md)

