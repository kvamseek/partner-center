---
title: Monitoring administrative relationships and self-service DAP removal
ms.topic: how-to
ms.date: 08/09/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Learn how to perform DAP self serve removal.
author: kvamseek
ms.author: vamseekk
---

# Monitoring administrative relationships and self-service DAP removal

**Appropriate roles**: Admin agent | Helpdesk agent

## Overview

Delegated administration privileges (DAP) provide the capability to manage a customer's service or subscription on their behalf. A customer must grant a partner administrative permissions for that service.

To get delegated administrator permissions from a customer, a partner emails them to [Request a reseller relationship with a customer](request-a-relationship-with-a-customer.md). After the customer approves the request, the partner's Admin agent or Helpdesk agent can sign in to the service's admin portal and manage the service on the customer's behalf. For example, using Helpdesk agent privileges, a partner can deliver support for the customer, and using Admin agent privileges, the partner can perform work on behalf of the customer.

Partners' Admin agents can audit DAP with their customers. The DAP monitoring tool captures how partner agents are accessing customer tenants across all their customer tenants through DAP. Partners can then review and remove DAP connections that aren't in use. This self-serve removal capability provides partners an ability to mitigate the risk.

## Impacted partners

Direct-bill partners, indirect providers, and indirect resellers are affected by this change.

> [!IMPORTANT]
> DAP enables a partner to access customer tenant in the following way:
>
> - The Admin agent group is assigned to the Global Administrator role in the customer's Azure AD tenant.
> - The Helpdesk agent group is assigned to the Helpdesk administrator role in the customer's Azure AD tenant.
>
> DAP monitoring data is captured from December 7, 2021. Monitoring administrative relationships only shows cross-tenant sign-in activities (acting on behalf of, AOBO) into the customer tenant from December 7. Sign-in actions before December 7 aren't shown on the administrative relationships dashboard.

## DAP guidance for customer security

To improve security, Microsoft recommends that you remove delegated administrative privileges that are no longer in use or that have been inactive for more than 60 days.

Customers can manage their own DAP privileges in the [Microsoft Admin Center](https://admin.microsoft.com/AdminPortal/Home). For more information, see [Customers can manage a partner's admin privileges](./customers-revoke-admin-privileges.md).

## Impacts of removing DAP

Disabling DAP access for a customer turns off both the Admin agent feature and Helpdesk agent privileges.

- Disabling DAP access won't stop partner earned credit (PEC) from accruing because accrual is based on role-based access control (RBAC) roles on the subscription. Disabling DAP won't allow  partners to manage their customer tenant from Partner Center.
- Disabling DAP access will stop partners from creating service requests on behalf of their customers. If partners need to create service requests, they'll need to request DAP access again from their customer.

For more information on the consequences of removing DAP, see the [DAP frequently asked questions](./dap-faq.md).

> [!NOTE]
> Integration sandbox tenants can disable DAP but they cannot request a reseller relationship with the test customer to re-enable DAP.

## DAP monitoring and self-service removal

A **sign-in activity** is any partner agent accessing a customer tenant via cross-tenant sign-ins to any workload. Partner accessing Partner Center and AOBO into the customer tenant OR Partners accessing API and exchanging tokens to access customer tenant are considered Active DAP.

An **active relationship** is measured by any cross-tenant sign-in activity to any workload by any partner agent accessing the specific customer tenant in the last 90 days.

A customer relationship is classified as **inactive** when there are no cross-tenant sign-in activities to any workload by any partner agent accessing that customer tenant in over 90 days. Partners see a recommendation on the dashboard to remove DAP if a customer relationship is inactive for more than 90 days.

In the [Security Center](https://partner.microsoft.com/commerce/securitycenter/administrativeRelationships) on the Partner Center, you can monitor cross-tenant sign-in activities for administrative privileges, and remove DAP if inactive. The Security Center also provides other functions, which are primary to ensuring a more secure partner-customer ecosystem, including:

- Partner Admin agents can access [Security Center](https://partner.microsoft.com/commerce/securitycenter/administrativeRelationships) for administrative relationships.
- Partners can sign in to the Security Center for administrative relationships to view sign-in activities.
- Partners can see sign-in activities across all their customers.

:::image type="content" source="media/dap-enabled-customers.png" alt-text="Shows the DAP enabled customers screen." lightbox="media/dap-enabled-customers.png":::

- Partners can see sign-in activities by the last 30-60 days, 61-90 days, and 90+ days across all of their customers who have active DAP relationships.
- If any customer DAP relationship is inactive for more than 90 days, the number of inactive days is represented as 90+.
- Partners can select multiple customers at a time to disable DAP.

:::image type="content" source="media/disable-dap.png" alt-text="Shows the disable D A P screen." lightbox="media/disable-dap.png":::

- Customers can be notified by email when a partner disables DAP.

:::image type="content" source="media/disable-dap-confirmation.png" alt-text="Shows the disable DAP confirmation screen." lightbox="media/disable-dap-confirmation.png":::

- Customers see the DAP relationship updated on the [Microsoft Admin Center](https://admin.microsoft.com/AdminPortal/Home).
- When DAP is disabled, it may take a few minutes to see the change in Partner Center.

## Filter attributes

|Filter condition               | Description |
|:------------------------------|:------------|
|Inactive for more than 90 days | Displays the number of customers whose DAP relationship is inactive for more than 90 days. Partners are recommended to remove DAP if inactive for more than 90 days.
|Inactive for 60-90 days        | Displays the number of customers whose DAP relationship is inactive between 60-90 days. Partners are recommended to remove DAP if inactive for more than 60 days.
|Inactive for 30-60 days        | Displays the number of customers whose DAP relationship is inactive between 30-60 days.
|Established in last seven days     | Displays the number of customers whose DAP relationship was established in the last seven days.

## DAP management attributes

|Field name                     | Description |
|:------------------------------|:------------|
|Number of partner agents signed in | Number of unique partner agents signed in to the customer tenant in last one day.
|Number of times partner agents signed in  | Number of times the partner agents signed in to the customer tenant in last one day.
|Days enabled     | Number of the days that the DAP relationship established between the partner and the customer has existed. If the relationship has existed for more than 60 days, *60+* is displayed.
|Days inactive    | Number of the days that the DAP relationship has been between the partner and the customer has been inactive. If that is more than 60 days, the value displayed is 60+ or an exact number. Because data is only available for cross-tenant activity since December 7, 2021, this attribute might be blank if there's no activity.
|Recommendation   | A recommendation to disable DAP is made if the partner agent hasn't signed in to any of the customers' workloads in the last 60 days.

