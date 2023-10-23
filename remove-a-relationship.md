---
title: Remove reseller relationship with a customer
ms.topic: how-to
ms.date: 11/01/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Find out how Microsoft direct partners can remove customers from their list, remove delegated admin privileges, and stop supporting or buying for a customer.
author: jischulz
ms.author: jischulz
---

# How to remove a reseller relationship with a customer in Partner Center

**Appropriate roles**: Global admin

This article describes how to remove a reseller relationship with a customer in Partner Center.

*Direct partners or indirect providers*: if you're no longer transacting with a customer, you can remove the relationship in Partner Center.

## Remove a reseller relationship

### Consequences

Removing a reseller relationship:

- Removes the customer from your list of customers in Partner Center
- Removes you from the [list of available support contacts](assign-support-contacts.md) for your customer
- Removes your delegation admin privileges for the customer
- Prevents you from making future purchases for the customer

> [!NOTE]
> The cancellation policy for Software and seat-based new commerce subscriptions prevents cancellation outside of the 7 day cancellation window. However, the presence of a customer reseller relationship does not prevent the customer from transacting via a different purchasing channel or partner and leaving a reseller relationship in place with no recurring invoicing does not impact the partners obligation in regard to the customer. In this case, any Delegated admin permissions can still be removed by the customer via the Microsoft 365 Admin portal or Azure portal.

### Prerequisites

- [Suspend any active subscriptions](#suspend-active-subscriptions).
- Cancel any [Azure reserved instances](/azure/architecture/framework/cost/optimize-reserved) (Azure RI).
- [Cancel any software purchases](csp-software-subscriptions.md#canceling-a-software-subscription).

#### Suspend active subscriptions

To suspend active subscriptions, use the following steps:

 1. In Partner Center, go to **Customers** and select a customer.

 2. Under **Subscriptions**, select a subscription.

 3. Select **Suspended**.

 4. Repeat the preceding steps for each active subscription.

### Remove the reseller relationship

To remove the reseller relationship, use the following steps:

 1. In Partner Center, go to **Customers** and select a customer.

 2. Select the **Account**.

 3. Select **Remove reseller relationship**.

   > [!NOTE]
   > If any subscriptions are still active, the **Remove reseller relationship** link will be inactive.

## Next steps

- [Request or re-establish a relationship with a customer](request-a-relationship-with-a-customer.md)
