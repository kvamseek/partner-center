---
title: Move license-based customers to CSP program
description: Learn how to move license-based customers from other channels, tenants, or another partner into the Cloud Solution Provider (CSP) program in Partner Center.
ms.topic: how-to
ms.date: 01/11/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
author: brentserbus
ms.author: brserbus
---

# Move license-based customers from other channels, tenants, and partners to the Cloud Solution Provider (CSP) program

**Appropriate roles**: Account admin | Sales agent | Billing agent

You can move your customer manually if they want to:

- Hire multiple partners
- Transfer their subscriptions to another partner or to another tenant
- Manage subscriptions they purchased elsewhere

You can also move customers into Partner Center from another channel.

> [!NOTE]
> You must be in the same region as the customer tenant to transition that customer to you.

> [!NOTE]
> For tenant-to-tenant migrations, customers must migrate the data to the new tenant themselves. For more information, see [Microsoft 365 tenant-to-tenant migrations](/microsoft-365/enterprise/microsoft-365-tenant-to-tenant-migrations).

## Move your customer's license-based subscriptions to the CSP Program

To move your customer's license-based subscriptions to the CSP Program, use the following steps:

1. Select **Customers** from the Partner Center menu and then select **Request a reseller relationship**. (To provide support for multi-channel accounts, do the same thing.)
1. After the customer accepts your invitation, you can provision the desired subscriptions and licenses for them (for example, the same Office 365 offer that the customer purchased previously).

## Transfer a customer subscription between partners through cancellation and expiration

A customer can cancel the original subscriptions or allow them to expire.

Because there are no refunds for canceled subscriptions, it's best to wait until the subscriptions are near their natural expiration dates.

- To transfer seat-based licenses at renewal of the subscription, ensure that autorenew is turned off. See [Subscription renewals](create-a-new-subscription.md#subscription-renewals).
- On the subscription end date, the state changes to [Expired](subscription-lifecycle.md#expired).
- The new subscription must be provisioned by the end of the expiry state of the asset (that is, 30 days from the term end date) to prevent data loss.

> [!NOTE]
> For scenarios where you are transferring more than 150 active customer subscriptions (examples: partner-to-partner transfers or transfers between channels), the tenant maximum would be exceeded by duplicating subscriptions. To address this:
> The source partner may turn off the auto-renew and allow the subscription to go into **Expired** state. This won't cause service disruption, because the subscription stays in this state for 30 days. During this time, users can continue to access files and services. To learn more, see [Subscription lifecycle states](subscription-lifecycle.md#expired).
> The destination partner or customer can repurchase the subscription during the 30 day grace period of the **Expired** state without service interruption.

## Subscription credit

The customer might be eligible for a credit if they purchased through the Microsoft 365 admin portal (for example, through monthly or yearly billing direct from Microsoft).

Credits for subscriptions purchased directly from Microsoft are handled by **Microsoft 365 billing support**.

For guidance on how to cancel your Microsoft 365 subscription, see [Cancel your Microsoft business subscription](/microsoft-365/commerce/subscriptions/cancel-your-subscription).

- If you have delegated administration privileges (DAP) for the customer, you can contact Microsoft 365 support on behalf of your customer.
- If you don't have DAP, ask your customer to contact Microsoft 365 support directly to find out how much credit they're eligible for and how any credit will be given to them.

For more information about delegated admin privileges, see [Obtain permissions to manage a customer's service or subscription](customers-revoke-admin-privileges.md).

## Disruption, data loss, and reassigning licenses

- You don't need to reassign licenses, there's no data loss, and there's no disruption to end users if:
  - You provision the same offers as your customer has been using.
  - The number of licenses remains the same.
  - The offer is equivalent.
- If you move a customer to a different offer, you must update their license assignment.
- If you move a customer who is on a discontinued offer, you must find an equivalent offer to prevent data loss.

## Next steps

- [Begin using pay-as-you-go-rates with the Azure plan](azure-plan-get-started.md)
- [Different ways you can work with other partners in Partner Center](work-with-other-partners.md)
