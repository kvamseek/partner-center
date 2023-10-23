---
title: include file
ms.topic: include
author: migolova
ms.author: migolova
ms.date: 07/13/2023
---

## Now live: New order history states and eligibility of subscription upgrades

_We've introduced two new states to the Partner Center Order history page and Order APIs. We’ve also added the ability to view subscription eligibility for upgrades._

- **Date**: July 17, 2023
- **Workspace**: Customers
- **Impacted audience**: Direct-bill partners and indirect providers

#### Order history states

Two new order states are available in the Partner Center Order history page and Order APIs, including [Get an order by ID](/partner-center/developer/get-an-order-by-id) and [Get all of a customer's orders](/partner-center/developer/get-all-of-a-customer-s-orders):

- **Suspended**: The order is suspended. Partners suspend a subscription to temporarily make the services not usable to customers. The transacting partner continues to be billed. To learn more, see: [Subscription lifecycle states - NCE suspended](../../../subscription-lifecycle.md).
- **Pending Review**: The order is pending secondary review. You may be required to upload documentation. See [Secondary deal review training deck](https://partner.microsoft.com/resources/detail/secondary-review-overview-pdf) to learn what to expect if your deal is selected for a secondary deal review.

To see the full list of possible order status and definitions, refer to [Order resources](/partner-center/developer/order-resources#orderstatus).

#### Eligibility of subscription upgrades

The Partner Center Upgrades page and [Get transition eligibilities](/partner-center/developer/transition-a-new-commerce-subscription#get-transition-eligibilities) API response now provide subscription eligibility to make it easier for partners to understand which subscriptions are eligible to upgrade to. For ineligible subscriptions, partners will see the reason why, including:

- Subscription isn't active.
- Subscription is within cancellation window.
- Subscription term duration is shorter than the source subscription's term duration.
- Subscription term end date is before the source subscription's term end date.

#### Next steps

- View and try out the new capabilities, available in Sandbox and Production.
- See the [_April announcement_](../../2023-april.md#13) to learn more about the added order history states.
