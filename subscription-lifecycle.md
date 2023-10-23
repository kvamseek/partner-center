---
title: Subscription lifecycle states
ms.topic: how-to
ms.date: 08/04/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Learn about the different lifecycle states for subscriptions.
author: migolova
ms.author: migolova
---

# Subscription lifecycle states

**Applies to**: Partner Center | Partner Center for Microsoft Cloud for US Government

**Appropriate roles**: Admin agent | Billing admin | Global admin | Helpdesk agent | Sales agent

This document covers the subscription lifecycle states for licensed-based offers for new commerce and legacy.

## New commerce

There are six states that a subscription can have in its lifecycle: Active, Canceled, Suspended, Expired, Disabled, and Deleted.  

### Active

In the **Active** state:

- The default (normal) state of a subscription.
- Partners can access and make changes to subscription properties.
- Customers can access and use services.
- Admins can also access services data and properties.
- Transacting partner continues to be billed.

### Canceled

New commerce subscriptions can be canceled within 7 days, except where otherwise required by law, of purchase or renewal. After this window has passed, subscriptions can no longer be canceled.

### Suspended

Partners can suspend a subscription to temporarily make the services not usable to customers.

At the time that the subscription is suspended:

- If there are next charge instructions, or changes to the billing plan mid term, they're not removed.
- Any other scheduled changes are removed. If the subscription is reactivated, the partner can recreate the changes.

While the subscription is suspended:

- Customers can no longer access and use services.
- Admins can access services data and properties.
- The transacting partner continues to be billed.
- Partners can reactivate the subscription before the end of term.
- Partners can cancel the subscription if they're within the 7-day cancellation window, or reactivate the subscription.
- If the subscription is still suspended by the term's end, the subscription moves to the expired state.

### Expired

**30-day expired state** follows the end of an **Active** subscription's term:

- If autorenew is turned off and the term ends, the previously active subscription expires.
- The subscription stays in this state for 30 days, and users can access files and services.
- After 30 days in the expired state, the subscription moves to a 90-day disabled state.
- Admins can also access data.
- Transacting partner won't be billed.
- Can't be reactivated.

> [!NOTE]
> This status doesn't appear in the Partner Center Subscription page. To view all subscription states, use the **Export all subscriptions** download or the [Get a customer's subscriptions API](./developer/get-all-of-a-customer-s-subscriptions.md) response.

### Disabled

**30-day disabled state** follows the end of a **Suspended** subscription's term:

- Partners that suspend their subscription leading to the term end will find their suspended subscription moved to this 30-day disabled state.
- After 30 days in the disabled state, the subscription moves to a 90-day disabled state.
- Users can't access files and services, and only admins can access the data.
- Transacting partner won't be billed.
- Can't be reactivated.

**90-day disabled state** follows the 30-day **Expired** or a 30-day **Disabled** states:

- 90-day disabled state: Data is retained for 90 days after the end of the previous state.
- Users can't access files and services, and only admins can access the data.
- Transacting partner won't be billed.
- Can't be reactivated.

### Deleted

After the subscription passes through the 90-day disabled state, it stays deleted, however:

- The subscription is nonrecoverable.
- If the partner cancels their subscription, the subscription goes into this state directly.
- Canceled subscriptions that become deleted enable the partner administrator 7 days to backup date before it's removed.
- Transacting partner won't be billed.
- Can't be reactivated.

## Legacy

There are three states that a legacy subscription can have in its lifecycle: Active, Suspended, and Deleted.

### Active

In the **Active** state:

- The default (normal) state of a subscription.
- Partners can access and make changes to subscription properties.
- Customers can access and use services.
- Admins can also access services data and properties.
- Transacting partner continues to be billed.

### Suspended

In the **Suspended** state:

- Partners suspend a subscription to temporarily make the services not usable to customers.
- Partners can reactivate the subscription before the end of term.
- If the subscription is still suspended by the term's end, the subscription is deleted.
- Partners can only reactivate the subscription.
- Customers can no longer access and use services.
- Admins can access services data and properties.
- Transacting partner won't be billed.

### Deleted

After 90 days in the suspended state, the subscription will be deleted and is nonrecoverable.
