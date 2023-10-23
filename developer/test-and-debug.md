---
title: Test and debug with integration sandbox
description: Learn how to use your Partner Center integration sandbox account (and related tokens) to test and debug your code so you don't accidentally incur new charges.
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: JulCsc
ms.author: raormeni
ms.date: 07/03/2023
---

# Test and debug with your Partner Center integration sandbox to avoid paying unexpected charges

**Applies to**: Partner Center | Partner Center operated by 21Vianet |  Partner Center for Microsoft Cloud for US Government

To test your code, you should use your integration sandbox account in Partner Center (and the corresponding tokens) so that you don't accidentally incur new charges that your company is responsible for paying. For more information about this test-in-production (TiP) environment, see [Set up API access in Partner Center](set-up-api-access-in-partner-center.md).

## Integration sandbox constraints

If you run automated build verification tests, conduct testing in production, or perform manual testing in the integration sandbox, you may reach the maximum limits for the integration sandbox. These limits are 75 customers, 5 subscriptions per customer, and 25 licenses per subscription.

The 25-licenses limit means you can't acquire an offer in the sandbox that has a minimum license requirement that exceeds 25 licenses. This limitation includes trials.

There are various invoice and reconciliation files available in the Sandbox environments but, not all of them are available on legacy or modern platforms. Verify the table below to know more.

| **Files**                    | **Available  in Legacy** | **Available  in Modern** |
| ---------------------------- | ------------------------ | ------------------------ |
| Invoice PDF                  | No                       | Yes                      |
| Invoice  Reconciliation File | No                       | Yes                      |
| Invoice Estimate  File       | No                       | Yes                      |
| Daily Billed  Usage File     | No                       | Yes                      |
| Daily  Unbilled Usage File   | No                       | Yes                      |

>[!NOTE]
>  You won't see any data in the Insights Cloud Solution Provider pages for the Sandbox tenant, because pages and reports under the Insights workspace: Cloud Solution Provider section aren't covered in the Sandbox environment.

### Azure plan

By default, partners can't provision Azure plans using their sandbox accounts. Partners who need to do so with their sandbox account must apply for access.

Create a [Partner Center support](https://partner.microsoft.com/support/v2/?stage=2&topicid=e1b8d2f4-8db5-0819-e2dd-b5a646a5c55b) ticket to request access from your **Sandbox tenant** and include your **Production tenant** ID in the ticket details.

For partners whose sandbox accounts have been approved to provision Azure plans, the following limits apply:

- Each sandbox partner account can have up to 10 Azure plans across all customer tenants (no matter how the plans are distributed among the customers).

- A direct bill partner can create up to one Azure plan per customer tenant.

- An indirect provider can create up to three Azure plans per customer tenant (for different indirect resellers specified as the Partner-of-Record).

- Each Azure plan can have up to three Azure subscriptions.

- Each CSP Azure subscription under your sandbox account is limited to four virtual machine (VM) cores per data center. Therefore, you can't provision VM SKUs that require more than four VM cores. Certain specialized VM SKUs such as GPU cores are also excluded.

- Each sandbox partner account has a spending limit of $2000 (USD) per billing cycle across all Azure plans. Once a partner reaches the spend limit, all Azure plans will be temporarily disabled until the next billing cycle.

### Cloud Solution Provider (CSP) Azure subscription offers

CSP Azure subscription offers are no longer available by default to sandbox accounts. These include MS-AZR-0146P, MS-AZR-DE-0146P and MS-AZR-USGOV-0146P for CSP Azure subscriptions in Microsoft Public Cloud, German Cloud, and Government Cloud respectively. Partners who need access to these offers with their sandbox account must apply for access. To apply for access, discuss with your Microsoft account manager or business contact.

For partners whose sandbox accounts have been approved for CSP Azure subscription offers, the following limits apply:

- You can have up to a maximum of 375 active subscriptions (75 customers x 5 subscriptions per customer). However, only 10 of which can be CSP Azure subscriptions.

- When a CSP Azure subscription reaches $200 of Azure usage, its resources are temporarily disabled until its next billing cycle. It's still considered an active subscription and is counted towards the 10 active Azure subscriptions limit.

- Each CSP Azure subscription under your sandbox account is limited to four virtual machine (VM) cores per data center. Therefore, you cannot provision VM SKUs that require more than four VM cores. Certain specialized VM SKUs such as GPU cores are also excluded.

> [!IMPORTANT]
> All existing CSP Azure subscriptions provisioned with sandbox accounts prior to August 1, 2018 are no longer supported and will be deprovisioned by Microsoft between October 16 - October 31, 2018. After the subscriptions have been deprovisioned, they cannot be re-enabled, and associated data are no longer accessible. Partners who have valuable data stored under these subscriptions must back up the data before October 16, 2018.

### Azure Reserved VM instance

If you're [purchasing an Azure Reserved VM instance](purchase-azure-reservations.md) with your sandbox account, you're limited to two VM instances per customer. You're also limited to selecting only from the following Azure Reserved VM instance product SKUs:

| Product Title  | Effective Date  | Sku Title                                               | Region [ArmRegionName] | Instance Key [ArmSkuName] | Duration | Consumption Meter ID       |
|----------------|-----------------|---------------------------------------------------------|------------------------|--------------|----------|----------------------------|
| B Series       | 12/1/2017 0:00  | Reserved VM instance, Standard_B1s, KR South, 1 year    | KoreaSouth             | `Standard_B1s` | `1Year`    | 3f913071-0dd7-4258-8ec4-6fad05bd976d |
| B Series       | 12/1/2017 0:00  | Reserved VM instance, Standard_B1s, US East, 1 year     | eastus                 | `Standard_B1s` | `1Year`    | f4d7a5a5-1b67-45ea-b1a0-282fbdd34b05 |
| B Series       | 12/1/2017 0:00  | Reserved VM instance, Standard_B1s, US West 2, 1 year   | westus2                | `Standard_B1s` | `1Year`    | 222e39f5-e99f-4fa3-a323-f46402977888 |
| B Series       | 12/1/2017 0:00  | Reserved VM instance, Standard_B1s, US North Central, 1 year    | northcentralus | `Standard_B1s` | `1Year`    | 4e1716fc-4842-43f1-aa96-7c1b1b1395a7 |
| B Series       | 12/1/2017 0:00  | Reserved VM instance, Standard_B1s, CA East, 1 year     | CanadaEast             | `Standard_B1s` | `1Year`    | ab8a5993-5db7-47c8-b3b1-2e1365b353fb |

### Subscriptions for commercial marketplace products

In production, after you've [created a subscription to commercial marketplace SaaS products](create-subscription-azure-marketplace-products.md), you need to retrieve a personalized activation link from Partner Center and visit the publisher's site to complete the setup process. Subscription billing will begin only after setup is complete.

In the CSP sandbox environment, there's no integration with ISVs. If you try to retrieve an activation link from Partner Center, a dummy link will be returned. You can't use this dummy link to complete the setup process at the publisher's site. To use the integration sandbox account to test billing for subscriptions to commercial marketplace SaaS products, see [Activate a sandbox subscription for commercial marketplace products](activate-sandbox-subscription-azure-marketplace-products.md) instead. Subscription billing will begin after successful activation.

To clean up at the end of your test run so there's space for the next round of testing, see the following articles:

- [Delete a customer account from the integration sandbox](delete-a-customer-account-from-the-integration-sandbox.md)

- [Decrease the quantity of a subscription](change-the-quantity-of-a-subscription.md)

- [Suspend a subscription](suspend-a-subscription.md) so that you can remove it.

### Azure Savings Plan

> [!NOTE]
> You cannot currently purchase an Azure Savings Plan through the sandbox environment of the Partner Center, but we may allow this in the future.

### PO Upload Testing

In Production, Partners may be required to provide Customer Purchase Order and/or Tender or Request for Proposal (RFP) information to complete a transaction within Partner Center.

To test this flow in the Sandbox environment, the purchase of the following offers will trigger the PO Upload flow for their respective orders:
- Access LTSC 2021 (Perpetual Software, Product ID DG7GMGF0D7FV)
- Excel LTSC 2021 (Perpetual Software, Product ID DG7GMGF0D7FT)

## Best practices for REST development

- Use a network trace tool so that you can see your request, the response, and if there were any errors in the HTTP status code in the response. For more information about error handling, see [Partner Center REST error codes](error-codes.md).

- Use a new Correlation ID for each call made to the Partner Center REST API. This practice ensures better logging and will help during debugging. For more information, see [Partner Center REST headers](headers.md).

## Troubleshooting tips for common REST problems

- Review all header properties, including the URL and API version.

- Ensure properties are included if necessary, and correctly formatted.

- Incorrect array formatting is a common error.

- **ETags** are temporary and as result, shouldn't be stored. When a function call requires an **ETags**, use the latest **ETags** value by getting the resource again. **ETags** values should be included in double quotation marks, like a string:

   ```rest
   If-Match : "eyJpZCI6IjUwMWE4NjBjLTE2OTgtNDQyYi04MDhjLTRiNjEyY2NmMzVmMiIsInZlcnNpb24iOjF9"
   ```
