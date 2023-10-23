---
title: include file
description: New states for the Partner Center Order History page April 25, 2023
ms.topic: include
ms.service: partner-dashboard
ms.subservice: partnercenter-announcements
author: migolova
ms.author: migolova
ms.reviewer: migolova
ms.date: 04/26/2023
---

## Coming soon: new order history states (suspended and pending review) 

*We're introducing two new states to the Partner Center Order history page and Order APIs in mid-June.*

- **Date**: Mid-June 2023
- **Workspace**: Customers
- **Impacted audience**: Direct-bill partners and indirect providers 

With this update, orders that have been suspended by partners show up as **Suspended** on the **Order history** page and Order APIs. 

As a part of this update, we're also introducing another state that is used when orders are pending an internal review, called **Pending review**. This new state allows partners to understand when their order requires a secondary review.  

**New states:** 

- **Suspended**: The order is suspended. Partners suspend a subscription to temporarily make the services not usable to customers. The transacting partner continues to be billed. To learn more, see: [Subscription lifecycle states - NCE suspended](../../../subscription-lifecycle.md). 
- **Pending Review**: The order is pending secondary review. You may be required to upload documentation. See [Secondary deal review training deck](https://partner.microsoft.com/resources/detail/secondary-review-overview-pdf) to learn what to expect if your deal is selected for a secondary deal review.

For partners who use the API, the new state returns a new Enum value. For partners who use SDK, this state is currently returned as a string. The two possible states for each order are:
- "status": “suspended",
- "status": “pending_review",

To learn more, see [Get an order by ID](../../../developer/get-an-order-by-id.md) and [Get all of a customer's orders](../../../developer/get-all-of-a-customer-s-orders.md).

#### Next steps

- View and try out the new order history states in Sandbox starting mid-May.
- See [March announcement](../../2023-march.md#3) to learn more about the new secondary deal review upload feature. 

#### Questions?

Contact [Support](https://partner.microsoft.com/dashboard/v2/support/servicerequests) if you have questions or need more information.
