---
title: Customer approval of partner GDAP request
ms.topic: article
ms.date: 03/31/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Customers can approve partner's Granular Admin privileges in Microsoft 365 admin center.
author: kvamseek
ms.author: vamseekk
---

# Customer approval of partner GDAP request

**Appropriate roles**: Global admin

Customers can approve your request for granular delegated admin privileges in the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).

[Granular delegated admin privileges](gdap-introduction.md) (GDAP) is a security feature that provides partners with least-privileged access following the Zero Trust cybersecurity protocol.

## Prerequisites

Customers must remove delegated admin privileges (DAP) roles ("Reseller" relationship type) before they can approve a request granular delegated admin privileges. Doing so ensures that DAP doesn't override GDAP.

To remove DAP roles, customers can use the following steps:

1. Sign in to [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339) as a Global admin.
2. On the **Partner relationships** page, select the partner of interest.

   :::image type="content" source="media/gdap/gdap-partner-rel-page.png" lightbox="media/gdap/gdap-partner-rel-page.png" alt-text="Screenshot of the Partner relationships page in Partner Center.":::

3. Remove delegated admin privileges (DAP) roles ("Reseller" relationship type) so those don't override granular delegated admin roles.

## Getting approval of your GDAP request

After you [invite your customer to grant granular delegated admin privileges](gdap-obtain-admin-permissions-to-manage-customer.md), they can approve your request.

To approve your request for granular delegated admin privileges, customers can use the following steps:

1. Open the link from your GDAP invitation email.
2. Select **Approve all** on the **Approve partner roles** page that opens in Microsoft 365 admin center.

   :::image type="content" source="media/gdap/gdap-approval.png" lightbox="media/gdap/gdap-approval.png" alt-text="Screenshot of the GDAP relationship approval page with flyout.":::

You receive a confirmation email notification after your customer approves your GDAP request.

   :::image type="content" source="media/gdap/gdap-email-to-partners.png" lightbox="media/gdap/gdap-email-to-partners.png" alt-text="Screenshot of the confirmation email sent to partners.":::

Your customer also receives a confirmation.

   :::image type="content" source="media/gdap/gdap-email-to-customers.png" lightbox="media/gdap/gdap-email-to-customers.png" alt-text="Screenshot of the confirmation email sent to customers.":::

## Next steps

- [Assign Azure AD roles](gdap-assign-azure-ad-roles.md)
- [Least-privileged roles by task](gdap-least-privileged-roles-by-task.md)
- [How to terminate relationship - for partners](gdap-partner-terminate.md)
- [How to terminate relationship - for customers](gdap-customer-terminate.md)
- [Expiring notifications](gdap-expiring-notifications.md)
- [Activity logs](gdap-activity-logs.md)


