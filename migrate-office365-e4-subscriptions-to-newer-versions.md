---
title: Migrate Office 365 E4 subscriptions
ms.topic: article
ms.date: 11/10/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Microsoft Office 365 Enterprise E4 edition is retired as of April 7, 2017. Learn how to migrate your customer subscriptions to newer versions of Office 365.
author: BrentSerbus
ms.author: brserbus
ms.custom: intro-migration
---

# Migrate Office 365 E4 subscriptions to newer Office 365 versions

**Appropriate roles**: Global admin | User management admin | Admin agent | Sales agent

The Office 365 Enterprise E4 plan is retired, effective April 7, 2017. You can no longer purchase new Office 365 E4 subscriptions after this date. Existing E4 subscriptions won't renew automatically when they expire.

When E4 subscriptions end, they'll be canceled. To ensure continuity for customers, you should transition customers with expiring E4 subscriptions to a supported SKU option, listed below. We recommend moving customers to new subscriptions before the subscription's yearly end date to avoid any service outages for customers.

> [!NOTE]
> Both Office 365 Enterprise E4 commercial and government SKUs are retired.

On the subscription's detail page, the E4 subscription status has changed to "Expires on [date]" from "Auto renews on [date]".

If you use the API (either CREST or Partner Center), you can discover expiring subscriptions by evaluating the end date of the subscription along with the auto renew = False property.

The E4 subscriptions will be set to auto renew=False in April 7, 2017. You can move customers to a new plan at any time.

## Office 365 Enterprise E4 edition replacement plans

You can choose to maintain the same functionality with E4 or have your customers take advantage of newer features and functionality in Office 365 and Skype for Business Online. Pricing details are found on the price list and offer list matrix in Partner Center. Secure Product Enterprise E3 or Secure Productive Enterprise E5 may be substituted in the following options for Office 365 Enterprise E3 or Office 365 Enterprise E5 respectively.

- Option 1: Office 365 Enterprise E5

- Option 2: Office 365 Enterprise E3 + Skype for Business Cloud PBX

- Option 3: Office 365 Enterprise E3 + Skype for Business Plus CAL (price and functionality parity with E4)

- Option 4: Office 365 Enterprise E3

| Feature | Option 1 | Option 2 | Option 3 | Option 4 |
| :---    | :------: |   :---:  |   :---:  |   :---:  |
| Get all the features included in Office 365 Enterprise E4? | Yes | Yes | Yes | No |
| Phone numbers managed in Office 365? | Yes | Yes | No | No |
| Phone numbers managed both on-premises and in Office 365 (hybrid deployment)? | Yes | Yes | No | No |
| Option to add a PSTN voice calling plan? | Yes | Yes | No | No |
| PSTN Conferencing? | Yes | No | No | No |
| Advanced tools for collaboration, analytics, and security? | Yes | No | No | No |
| Interactive reports, dashboards, and data visualizations? | Yes | No | No | No |
| More control over data security and compliance with built-in privacy, transparency, and refined user controls? | Yes | No | No | No |

## Transition customers to new product plans

Microsoft continuously offers new products and services to our partners. In these cases, you may need to upgrade customers to new services or migrate their subscriptions from SKUs that will eventually be shut down. Migrating customers from retired SKUs to newer ones requires the following steps:

- Purchase the new subscription
- Reassign current user licenses
- Cancel the old subscription

Follow these steps to migrate a customer's Office 365 Enterprise E4 subscription to one of the options in the table above.

### Step 1 - Purchase the new subscription

1. From the **Partner Center** menu, select **Customers**, select the customer you wish to move, and then select **Add subscriptions**.

2. Select the subscription you want to purchase from the catalog (in this case, one of the options above), enter the number of licenses, and then select **Submit**.

   Your customer should now have both old and new subscriptions, the old Office 365 Enterprise E4 subscription and the new "target" subscription, for example, Option 1 - Office 365 Enterprise E5.

### Step 2 - Reassign the customer's users' licenses

1. From the **Partner Center** menu, select **Customers**, select the customer you wish to move, and then select **Users and licenses**. The customer's Users and Licenses page opens.

2. To reassign user licenses, select the user to reassign and then select **Manage licenses**.

3. On the **Manage licenses** page, clear the **Office 365 Enterprise E4** license check box and select a new service plan for the subscription the customer is moving to.

4. Select **Submit**. A confirmation page lists the new license assignments.

5. Continue the same steps with any other customer users that need license reassignment.

After moving the user licenses to the new service, you can safely cancel the retired subscription at the top Customer level.

### Step 3 - Cancel the old subscription

1. From the **Partner Center** menu, select **Customers**. Select the customer you want to move, and select the subscription you want to cancel.

2. In the subscription details page, set the subscription status to **Suspended**.

3. Select **Submit**.

The old subscription is suspended and the new subscription is active. The suspended subscription will be de-provisioned automatically after 120 days. The customer incurs no additional costs for the old subscription.
