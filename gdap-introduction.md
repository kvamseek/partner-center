---
title: Granular delegated admin privileges (GDAP) introduction
ms.topic: conceptual
ms.date: 07/31/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Introduction to granular delegated admin privileges.
author: kvamseek
ms.author: vamseekk
---

# Introduction to granular delegated admin privileges (GDAP)

**Appropriate roles**: All partners interested in Partner Center

GDAP capabilities allow partners to control access to their customers' workloads in order to better address their security concerns. Partners can offer more services to customers who may be uncomfortable with the current levels of partner access. They can also offer services to customers who have regulatory needs that require least-privileged access to partners.

## What is GDAP in Partner Center?

GDAP is a security feature that provides partners with least-privileged access following the Zero Trust cybersecurity protocol. It lets partners configure granular and time-bound access to their customers' workloads in production and sandbox environments. This least-privileged access needs to be explicitly granted to partners by their customers.

Partners' access can be partitioned per customer. With GDAP, partners no longer have access to all customer tenants across Azure subscriptions through Admin agents by default. Instead, partners managing Azure are part of a separate security group, which is a member of the Admin agent group. This group grants owner role-based access control (RBAC) access on all Azure subscriptions for that customer.

:::image type="content" source="media/gdap/gdap-introduction.png" lightbox="media/gdap/gdap-introduction.png" alt-text="Image of GDAP diagram.":::

Partners managing Azure no longer receive the Global Admin role on their customer's tenant but rather, receive lower permissions to read a customer directory by default.

Partners can transition from DAP to GDAP and eventually remove DAP (Global Admin) on customers' tenant without any effect to partner earned credit (PEC).

## Next steps

- [Obtain permissions to manage customer](gdap-obtain-admin-permissions-to-manage-customer.md)
- [Get your customer's approval](gdap-customer-approval.md)
- [Assign Azure AD roles](gdap-assign-azure-ad-roles.md)
- [Upgrade DAP relations to GDAP in bulk (no consent required)](gdap-bulk-migration-tool.md)
- [Get started with GDAP APIs](/graph/api/resources/delegatedadminrelationships-api-overview)


