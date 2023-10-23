---
title: Migrate Dynamics 365 Business Edition
ms.topic: article
ms.date: 1/11/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Learn how to migrate qualified Dynamics 365 Business Edition offers to newer versions before they expire.
author: BrentSerbus
ms.author: brserbus
ms.custom: intro-migration
---

# Migrate Dynamics 365 Business Edition Offers to newer versions

**Appropriate roles**: Global admin | User management admin | Admin agent | Sales agent

Effective January 1, 2019, customers with Dynamics 365 Business Edition subscriptions can no longer renew; existing subscriptions won't renew automatically when they expire. On the subscription's detail page, the subscription status will change to "Expires on [date]" from "Auto renews on [date]".

To ensure continuity for customers, you should transition their expiring subscriptions to a supported option. We recommend moving customers to new subscriptions before the subscription's yearly end date to avoid any service outages for customers.

If you use the API (either CREST or Partner Center), you can find expiring subscriptions by evaluating the end date of the subscription along with the auto renew = False property. The subscriptions in question will be set to auto renew=False on January 1, 2019. You can move customers to a new plan at any time.

## The Dynamics 365 Business Editions being retired

- Dynamics 365 for Finance and Operations, Business edition
- Dynamics 365 for Team Members, Business edition

## Dynamics Business Central - the Dynamics 365 Business Edition new offers

With the new Dynamics Business Central offers, your customers can connect their financial, sales, service, and operations to streamline business processes, improve customer interactions, and make better decisions. Dynamics 365 Business Central is cloud-based and available through Cloud Solution Provider (CSP) program partners only.
Dynamics 365 Business Edition customers are eligible to receive discounted transition pricing for the new Business Central offers until June 30, 2020.

## Transition customers to new product plans

 Moving customers from retired SKUs to newer ones requires the following steps in this order:

- Purchase the new subscription
- Reassign current user licenses
- Cancel old subscription

## Purchase the new plan for your customer

1. Select **Customers** from the left nav and then select the customer you want to move to the new subscription.
2. Select **Add Subscription**.
3. Select the subscription you want to purchase from the catalog (in this case, one of the options included in this topic), enter the number of licenses, and then select **Submit**.

Your customer will now have both the old subscription and the new one. Your next step is to reassign licenses to the customer's users.

1. Select **Customers** from the left nav and then select the customer you're moving.
2. Select **Users and licenses**.
3. To reassign a license to a user, select the user and then select **Manage licenses**.
4. On the **Manage licenses** page, clear the Dynamics 365 for Sales/ Customer Engagement Plan from Basic (Qualified Offer) license check box and select a new service plan for the subscription the customer is moving to.
5. Select **Submit**. Do this for each user who needs the new license.

Once you've moved the licenses over to the new subscription, you can cancel the old subscription.

1. Select **Customers** from the left nav and then select the customer you're moving.
2. On the subscription detail page, set the old subscription to **Suspended** and select **Submit**.

The old subscription is now suspended, and the new subscription is active. The suspended subscription will be de-provisioned automatically after 120 days. Your customer will incur no more costs for the old subscription.
