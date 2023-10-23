---
title: Migrate Skype for Business subscriptions
description: Learn how and when to migrate certain customers with expiring Skype for Business Online Plan 1 subscriptions to new Office 365 versions.
ms.topic: article
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
author: BrentSerbus
ms.author: brserbus
ms.date: 01/11/2023
---

# Migrate Skype for Business Online Plan 1 subscriptions to newer Office 365 versions

**Appropriate roles**: Sales agent

The Skype for Business Online Plan 1 was retired, effective August 1, 2018. After that date, customers could no longer purchase new Skype for Business Plan 1 subscriptions, and existing subscriptions do not renew automatically when they expire and won't provide a renewal option. On the subscription's detail page, the Skype for Business Online Plan 1 subscription status has changed to "Expires on [date]" from "Auto renews on [date]".

To ensure continuity for customers, you should transition customers with expiring Skype for Business Online Plan 1 subscriptions to a supported SKU option, listed below. We recommend moving customers to new subscriptions before the subscription's yearly end date to avoid any service outages for customers.

> [!NOTE]
>Both Skype for Business Online Plan 1 commercial and government SKUs are retired.

If you use the API (either Commerce REST (CREST) or Partner Center), find expiring subscriptions by evaluating the end date of the subscription along with the auto renew = False property.
The Skype for Business Online Plan 1 subscriptions will be set to auto renew=False on September 1, 2018. You can move customers to a new plan at any time.

## Skype for Business Online Plan 1 replacement plans

With the new plans, your customers take can advantage of newer features and functionality in Office 365. Pricing details are found on the price list and offer list matrix in Partner Center.

- Option 1: Office 365 Enterprise F1
- Option 2: Microsoft 365 Enterprise F1
- Option 3: Other Office 365 plans

|**Feature**    |**Option 1**   |**Option 2**   |**Option 3**   |
|:-----------------|:-----------------|:-------------|:------------|
|Get all the features included in Skype for Business Online Plan 1|Yes   |Yes   |Yes   |
|IM and presence |Yes   |Yes   |Yes   |
|Peer-to-peer Audio and Video over IP|Yes   |Yes   |Yes
|Join meetings as an authenticated user| Yes   |Yes   |Yes   |

## Transition customers to new product plans

Microsoft continuously offers new products and services to our partners. In these cases, you may need to upgrade customers to new services or migrate their subscriptions from SKUs that will eventually be shut down. Migrating customers from retired SKUs to newer ones requires the following steps:

- Purchase the new subscription
- Reassign current user licenses
- Cancel old subscription

### Migrate your customers to new plans

1. To purchase the new subscription, from the **Partner Center menu**, select **Customers**, select the customer you want to move, and then select **Add subscriptions**.

2. Select the subscription you want to purchase from the catalog (in this case, one of the options above), enter the number of licenses, and then select **Submit**.

   Your customer should now have both old and new subscriptions, the old Skype for Business Online Plan 1  subscription and the new 'target' subscription, for example, Option 1 - Office 365 Enterprise F1.

3. To reassign the customer's users' licenses, from the **Partner Center** menu, select **Customers**, select the customer you're moving, and then select **Users and licenses**. The customer's Users and Licenses page opens.

4. To reassign user license, select the user to reassign and then select **Manage licenses.**

5. On the **Manage licenses** page, clear the Skype for Business Online Plan 1 license check box and select a new service plan for the subscription the customer is moving to.

6. Select **Submit**. A confirmation page lists the new license assignments. Continue this same process for other users who need license assignments.

   After moving the user license to the new service, you can safely cancel the retired subscription at the customer level.

7. From the **Partner Center** menu, select **Customers**. Select the customer whose subscription you're canceling.

8. In the subscription detail page, set the subscription to **Suspended**.

9. Select **Submit.**

The old subscription is suspended, and the new subscription is active. The suspended subscription will be de-provisioned automatically after 120 days. The customer incurs no additional costs for the old subscription.

## Next steps

- [Advisors: Create and send a trial invitation for clients to try Office 365](advisors-create-a-trial-invitation.md)
- [Advisors: Build your client base with Office 365 trial invitations and purchase offers](advisors-build-your-business.md)
- [Advisors: Create a purchase offer](advisor-create-a-purchase-offer.md)
