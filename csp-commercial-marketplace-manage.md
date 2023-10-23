---
title: Manage marketplace products & offers
ms.topic: how-to
ms.date: 8/31/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Using Partner Center, learn how Cloud Solution Providers can manage third-party ISV offers purchased for customers from the commercial marketplace.
author: migolova
ms.author: migolova
---

# Manage commercial marketplace products and offers for your customers

**Appropriate roles**: Global admin | Admin agent

Partners in the Cloud Solution Provider (CSP) program can use Partner Center to purchase many independent software vendor (ISV) software as a service (SaaS) offers or subscriptions for their customers from the commercial marketplace.

After you purchase an offer, you have various ways to manage it.

## View or edit a subscription

To review or edit a subscription after you purchase it from a third-party ISV publisher, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Select a customer and then select **Subscriptions**.

   Any license-based subscriptions you've purchased for the customer are displayed.

3. In the **Subscription** column, select the subscription that you want to view or edit.

   Information about how set up or provision the offer is displayed.

   You might see **Action Needed** in the **Status** column if more action is needed on the offer. A link to the ISV publisher's site might also be displayed.

4. After you select the subscription that you want to view or edit, you can:

    - Change the subscription nickname.

    - Increase or decrease the number of licenses in the subscription.

    - Cancel the subscription.

    - Turn off auto-renew.

    - Add an indirect reseller PartnerID, if applicable.
    - Perform other actions

> [!NOTE]
> You may need to complete certain steps defined by the ISV publisher before you can perform some changes to a subscription, such as cancelling a subscription.

> [!NOTE]
> Temporarily, persons with the *Sales agent* role cannot update Marketplace SaaS subscription details such as quantity, status, and billing frequency.
>
> This restriction only applies to the Sales agent role. *Admin agents* continue to be able to update subscription information.
>
> To update subscriptions, Sales agents should sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) as an Admin agent if they have an Admin agent account, or they can ask an Admin agent to update the information on their behalf.
>
> Sales agents can still buy new subscriptions.

## Assign licenses and activate a subscription on behalf of a customer

When you purchase a SaaS offer provided by an ISV publisher in the commercial marketplace, the ISV publisher helps manage the process of assigning licenses and activating the subscription on behalf of your customer.

The publisher should provide you with a personalized link and an authorization code that identifies your purchase.

1. Find the personalized link from the ISV publisher in one of the following ways:

   - Select **Go to publisher's site** from the confirmation page that appears after you purchase an ISV SaaS offer.

   - Link from the customer's **Subscriptions** page.

     The publisher link appears on the row associated with the ISV offer or subscription purchased for the customer.

   - Retrieve the link using [Partner Center APIs](/partner-center/develop/get-activation-link-by-order-line-item).

   > [!NOTE]
   > To do this on behalf of your customer, you may need to copy the personalized link, paste it into a private browser, and enter the customer's credentials.

2. Complete the customer setup process and provision or assign licenses by performing any other steps that the publisher tells you about after you are in the ISV publisher's site or system.

3. Performing the following tasks, which you're responsible for as a partner in the CSP program who is working on behalf of your customer:

    - Submit any required information to the publisher.

    - Send any required URL directly to your customer (or otherwise directly communicate details about a subscription to your customer).

   After you provide the required information to the publisher, the publisher provisions and assigns appropriate licenses.

   Subscription billing starts only after the ISV publisher:

    - Successfully assigns appropriate licenses

    - Confirms to Microsoft that account setup has been successfully completed (using a separate, SaaS fulfillment API)

## Cancel a license-based SaaS subscription from an ISV publisher

You can cancel a subscription during its designated cancellation period when subscribed to a license-based SaaS product offered by an ISV publisher within the commercial marketplace.

The cancellation period depends on whether you have a monthly or annual subscription.

You can also choose whether or not to automatically renew a subscription.

For detailed information about cancellation periods, how to cancel, or how to auto-renew a subscription, see [Cancel a subscription](create-a-new-subscription.md#cancel-traditional-license-based-subscriptions).

## Add or remove licenses for a SaaS subscription

To add or remove user licenses for a customer subscription to SaaS commercial marketplace offers, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Select a customer and then select **Subscriptions**.

   Any license-based subscriptions you've purchased for the customer are displayed.

3. In the **Subscription** column, select the subscription that you want to modify.

4. In the subscription details page, locate the **Quantity** field, which is where you can increase or decrease the number of licenses.

5. Change the quantity, then select **Submit**.

## Manage subscriptions using Partner Center APIs

You can also use Partner Center APIs to perform lifecycle management and manage invoices for your subscriptions. For more information, see [Create a subscription for commercial marketplace products](/partner-center/develop/create-subscription-azure-marketplace-products).

## Next steps

- [Purchase commercial marketplace offers](csp-commercial-marketplace-purchase.md)
- [Learn about billing in the commercial marketplace](csp-commercial-marketplace-billing.md)
