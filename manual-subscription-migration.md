---
title: Migrate qualified Dynamics 365 subscriptions
ms.topic: article
ms.date: 1/11/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Learn how to migrate from qualified, basic Dynamics 365 subscriptions to a new subscription before existing subscriptions expire.
author: Brentserbus
ms.author: brserbus
ms.custom: intro-migration
---

# Migrate Dynamics 365 and Customer Engagement Plan from Basic (qualified offers) to newer versions

**Appropriate roles**: Global admin | User management admin | Admin agent | Sales agent

Since January 1, 2019, customers with Dynamics 365 for Sales/ Customer Engagement Plan from Basic (Qualified Offers) subscriptions can't renew these legacy offers; existing subscriptions won't renew automatically when they expire. On the subscription's detail page, the subscription status will change to "Expires on [date]" from "Auto renews on [date]".

To ensure continuity for customers, transition those with expiring subscriptions to a supported option, listed below. We recommend moving customers to new subscriptions before the subscription's yearly end date to avoid any service outages for customers.

If you use the API (either CREST or Partner Center), you can find expiring subscriptions by evaluating the end date of the subscription along with the auto renew = False property. The subscriptions in question will be set to auto renew=False on January 1, 2019. You can move customers to a new plan at any time.

## The Dynamics 365 offers being retired

- Dynamics 365 for Sales Enterprise Edition CRMOL Basic (Qualified Offer)
- Dynamics 365 for Sales Enterprise Edition CRMOL Basic (Qualified Offer) for Faculty
- Dynamics 365 for Sales Enterprise Edition CRMOL Basic (Qualified Offer) for Students
- Dynamics 365 for Sales Enterprise Edition (Government Pricing) CRMOL Basic (Qualified Offer)
- Dynamics 365 for Sales Enterprise Edition From SA for CRM Basic (Qualified Offer)
- Dynamics 365 for Sales Enterprise Edition From SA for CRM Basic (Qualified Offer) for Faculty
- Dynamics 365 for Sales Enterprise Edition From SA for CRM Basic (Qualified Offer) for Students
- Dynamics 365 for Sales Enterprise Edition (Government Pricing) From SA for CRM Basic (Qualified Offer)
- Dynamics 365 for Sales Enterprise Edition Add-On for CRM Basic (Qualified Offer)
- Dynamics 365 for Sales Enterprise Edition Add-On for CRM Basic (Qualified Offer) for Faculty
- Dynamics 365 for Sales Enterprise Edition Add-On for CRM Basic (Qualified Offer) for Students
- Dynamics 365 for Sales Enterprise Edition (Government Pricing) Add-On for CRM Basic (Qualified Offer)
- Dynamics 365 Customer Engagement Plan Enterprise Edition CRMOL Basic (Qualified Offer)
- Dynamics 365 Customer Engagement Plan Enterprise Edition (Government Pricing) CRMOL Basic (Qualified Offer)
- Dynamics 365 Customer Engagement Plan Enterprise Edition CRMOL Basic (Qualified Offer) for Students
- Dynamics 365 Customer Engagement Plan Enterprise Edition CRMOL Basic (Qualified Offer) for Faculty
- Dynamics 365 Customer Engagement Plan Enterprise Edition From SA for CRM Basic (Qualified Offer)
- Dynamics 365 Customer Engagement Plan Enterprise Edition (Government Pricing) From SA for CRM Basic (Qualified Offer)
- Dynamics 365 Customer Engagement Plan Enterprise Edition From SA for CRM Basic (Qualified Offer) for Students
- Dynamics 365 Customer Engagement Plan Enterprise Edition From SA for CRM Basic (Qualified Offer) for Faculty
- Dynamics 365 Customer Engagement Plan Enterprise Edition Add-On for CRM Basic (Qualified Offer)
- Dynamics 365 Customer Engagement Plan Enterprise Edition (Government Pricing) Add-On for CRM Basic (Qualified Offer)
- Dynamics 365 Customer Engagement Plan Enterprise Edition Add-On for CRM Basic (Qualified Offer) for Students
- Dynamics 365 Customer Engagement Plan Enterprise Edition Add-On for CRM Basic (Qualified Offer) for Faculty

## Dynamics 365 for Sales/ Customer Engagement Plan from Basic (Qualified Offers) replacement plans

### Retired offers

- Dynamics 365 for Sales from CRM Basic or CRMOL Basic (Qualified Offer)
- Dynamics 365 Customer Engagement Plan from CRM Basic or CRMOL Basic (Qualified Offer)

### Replacement options

- Dynamics 365 for Sales Professional (NEW)
- Dynamics 365 for Sales Professional (NEW)
- Dynamics 365 for Customer Service
- Dynamics 365 Customer Engagement Plan, or
- Dynamics 365 Team Members

## Transition customers to new product plans

Moving customers from retired SKUs to newer ones requires the following steps in this order:

1. Purchase the new subscription.
1. Reassign the current user licenses.
1. Cancel the old subscription.

## Purchase the new plan for your customer

1. Select **Customers** from the left nav and then select the customer you want to move to the new subscription.
2. Select **Add Subscription**.
3. Select the subscription you want to purchase from the catalog (in this case, one of the options above), enter the number of licenses, and then select **Submit**.

Your customer will now have both the old subscription and the new one. Your next step is to reassign licenses to the customer's users.

1. Select **Customers** from the left nav and then select the customer you're moving.
2. Select **Users and licenses**.
3. To reassign a license to a user, select the user and then select **Manage licenses**.
4. On the **Manage licenses** page, clear the Dynamics 365 for Sales/ Customer Engagement Plan from Basic (Qualified Offer) license check box and select a new service plan for the subscription the customer is moving to.
5. Select **Submit**. You'll do this for each user who needs the new license.

After you've moved the licenses over to the new subscription, you can cancel the old subscription.

1. Select **Customers** from the left nav and then select the customer you're moving.
2. On the subscription detail page, set the old subscription to **Suspended** and select **Submit**.

The old subscription is now suspended, and the new subscription is active. The suspended subscription will be de-provisioned automatically after 120 days. Your customer will incur no additional costs for the old subscription.
