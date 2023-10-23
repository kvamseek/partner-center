---
title: GDAP Migration FAQ for customers
ms.topic: article
ms.date: 06/13/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Granular delegated administrative privileges (GDAP) migration frequently asked questions for customers
author: kvamseek
ms.author: vamseekk
---

# GDAP Migration FAQ for customers

**Appropriate roles**: All users interested in Partner Center

Granular delegated admin permissions (GDAP) give partners access to their customers' workloads in a way that is more granular and time-bound, which can help to address customer security concerns.

With GDAP, partners can provide more services to customers who may be uncomfortable with high levels of partner access.

GDAP also helps customers who have regulatory requirements provide least-privileged access to partners.

## What is Delegated administration privileges (DAP)?

Delegated administration privileges (DAP) enable a partner to manage a customer's service or subscription on their behalf.

For more, see [Delegated administration privileges](dap-faq.md).

## When was our CSP granted DAP permissions to their customers’ tenant?

- When the CSP sets up a new customer relationship, a delegated admin privilege (DAP) is established.
- When a partner requests a [reseller relationship](customers-revoke-admin-privileges.md#invitesteps), there's an option to establish DAP by sending the invitation to the customer. The customer has to accept the request.

## Can a customer revoke DAP access to their tenant?

Yes, either party, the CSP or Customer, can cancel DAP access.

## Why is Microsoft retiring Delegated administrative privileges (DAP)?

DAP is susceptible to security attacks due to its longevity and high privileged access.

For more, see [NOBELIUM targeting delegated administrative privileges to facilitate broader attacks](https://www.microsoft.com/security/blog/2021/10/25/nobelium-targeting-delegated-administrative-privileges-to-facilitate-broader-attacks/).

## What is GDAP?

Granular delegated administrative privilege (GDAP) is a security feature that provides partners with least-privileged access following the Zero Trust cybersecurity protocol. It lets partners configure granular and time-bound access to their customers' workloads in production and sandbox environments. This least-privileged access needs to be explicitly granted to partners by their customers.

For more, see [Azure AD built-in roles](/azure/active-directory/roles/permissions-reference).

## How does GDAP work?

GDAP utilizes an Azure AD feature named Cross-Tenant Access Policy (sometimes referred to as XTAP [Cross-tenant access overview](/azure/active-directory/external-identities/cross-tenant-access-overview)), aligning CSP Partner and customer security models with the Microsoft Identity Model. When a request for a GDAP relationship is made, from the CSP partner to their customer, it contains one or more Azure AD built-in roles and time-bound access measured in days (1 to 730). When the customer accepts the request an XTAP policy is written into the customer's tenant, consenting to the limited roles and given time span solicited by the CSP partner.

The CSP partner can request multiple GDAP relationships, each with their own limited roles and given time span, adding more flexibility than the previous DAP relationship.

## What is the GDAP bulk migration tool?

The GDAP bulk migration tool provides the CSP partners a means for moving active DAP access to GDAP and removing legacy DAP permissions. Active DAP is defined as any CSP / Customer DAP relationship that is currently established. The CSP partners can't request a level of access greater than what was established with DAP.

For more, see [GDAP bulk migration tool](gdap-bulk-migration-tool.md) and [GDAP bulk migration tool FAQ](gdap-bulk-migration-tool-faq.md).

## Will running the GDAP Bulk migration tool cause a new service principal to be added as an enterprise application in the customer's tenant?

Yes, The GDAP bulk migration tool uses a functioning DAP to authorize the establishment of a new GDAP relationship. The first time a GDAP relationship is accepted, there are two Microsoft first-party service principals that come into play in the customer tenant.

## What are the two Azure Active Directory GDAP service principals that are created in the customer's tenant?

|Name |Application ID|
|---|---|
|Partner customer delegated administration|2832473f-ec63-45fb-976f-5d45a7d4bb91|
|Partner customer delegated admin offline processor|a3475900-ccec-4a69-98f5-a65cd5dc5306|

In this context, "first-party" means that consent is implicitly provided by Microsoft at API call time and the `OAuth 2.0 Access Token` is validated on each API call to enforce role or permissions for the calling identity to managed GDAP relationships.

The **283*** service principal is required at the time of the acceptance of a GDAP relationship. The **283*** Service Principal sets up the XTAP "service provider" policy and prepares permissions to allow expiration and role management. Only the GDAP SP may set or modify the XTAP policies for Service Providers.

The **a34*** identity is required for the entire lifecycle of the GDAP relationship and will be automatically removed at the time the last GDAP relationship ends. The **a34*** identity's primary permission and function is to manage XTAP policies and access assignments. A customer admin shouldn't attempt to manually remove the **a34*** identity. The **a34*** identity implements functions for trusted expiration and role management. The recommended method for a customer to view or remove existing GDAP relationships is via the [admin.microsoft.com](https://admin.microsoft.com/Adminportal/Home#/homepage) portal.

## Next steps

- [GDAP introduction](gdap-introduction.md)
- [GDAP FAQ](gdap-faq.md)
- [GDAP Microsoft-led transition](./gdap-microsoft-led-transition.md)


