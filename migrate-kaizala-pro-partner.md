---
title: Migrate Kaizala Pro subscriptions to Microsoft 365
description: Learn how to Migrate Kaizala Pro subscriptions to Microsoft 365 or Office 365 versions. Read this article for more details about transitioning your customers.
ms.topic: article
ms.service: partner-dashboard
ms.subservice: partnercenter-insights
ms.author: sajawas
author: SankalpJws
ms.date: 11/09/2021
ms.custom: intro-migration
---

# Migrate Kaizala Pro Standalone subscriptions to Microsoft 365 or Office 365 versions

**Appropriate roles**: Sales agent

Effective July 1, 2020, Microsoft ended sales of the Kaizala Pro standalone service. Customers could no longer purchase new Kaizala Pro subscriptions after that date, and existing Kaizala Pro subscriptions don't renew automatically when they expire.

To ensure continuity for customers, you should transition customers with expiring Kaizala Pro standalone subscriptions to a supported SKU option, listed below. We recommend moving customers to new subscriptions before the subscription's yearly end date to avoid any service outages for customers.

If you use the API (either CREST or Partner Center), you can discover expiring subscriptions by evaluating the end date of the subscription along with the auto renew property set to false: `auto renew = False`.

The E4 subscriptions will be set to `auto renew=False` on July 1, 2020. You can move customers to a new plan at any time.

## Kaizala Pro Standalone replacement plans

With the new plans, your customers can take advantage of newer features and functionality in Microsoft 365. Pricing details are found on the price list and offer list matrix in Partner Center.

- [**Microsoft 365 for Business**](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-products?&activetab=tab:primaryr2), including:
  - Microsoft 365 Business Basic
  - Microsoft 365 Business Standard
  - Microsoft 365 Business Premium

- [**Microsoft 365 for Frontline**](https://www.microsoft.com/microsoft-365/microsoft-365-enterprise-f3?activetab=pivot:overviewtab), including:
  - Microsoft 365 F3 (formerly Microsoft 365 F1) and Office 365 F3

- [**Microsoft 365 for Enterprise**](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans), including:
  - Office 365 E1
  - Microsoft 365 E3 and Office 365 E3
  - Microsoft 365 E5 and Office 365 E5

- [**Microsoft 365 for Education**](https://www.microsoft.com/education/buy-license/microsoft365), including:
  - Microsoft 365 A1 and Office 365 A1
  - Microsoft 365 A3 and Office 365 A3
  - Microsoft 365 A5 and Office 365 A5

## Transition customers to new product plans

Microsoft continuously offers new products and services to our partners. In these cases, you may need to upgrade customers to new services or migrate their subscriptions from SKUs that will eventually be shut down. Migrating customers from retired SKUs to newer ones requires the following steps:

A. Purchase the new subscription

B. Reassign current user licenses

C. Cancel old subscription

## Migrate your customers to new plans

### A. Purchase the new subscription

1. To purchase the new subscription, from the **Partner Center** menu, select **Customers**, select the customer you want to move, and then select **Add subscriptions**.

2. Select the subscription you want to purchase from the catalog (in this case, one of the options above), enter the number of licenses, and then select **Submit**.

Your customer should now have both old and new subscriptions, the old Kaizala Pro Standalone subscription and the new 'target' subscription, for example, Option 1 - Office 365 Enterprise F1.

### B. Reassign current user licenses

1. To reassign the customer's users' licenses, from the **Partner Center** menu, select **Customers**, select the customer you're moving, and then select **Users and licenses**. The customer's Users and Licenses page opens.

2. To reassign user license, select the user to reassign and then select **Manage licenses**.

3. On the **Manage licenses** page, clear the Kaizala Pro Standalone license check box, and select a new service plan for the subscription the customer is moving to.

4. Select **Submit**. A confirmation page lists the new license assignments. Continue this same process for other users who need license assignments.

### C. Cancel old subscription

After moving the user license to the new service, you can safely cancel the retired subscription at the customer level.

1. From the **Partner Center** menu, select **Customers**. Select the customer whose subscription you're canceling.

2. In the subscription detail page, set the subscription to **Suspended**.

3. Select **Submit**.

The old subscription is suspended, and the new subscription is active. The suspended subscription will be de-provisioned automatically after 120 days. The customer incurs no additional costs for the old subscription.
