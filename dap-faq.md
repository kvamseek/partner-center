---
title: Delegated administration privileges (DAP) FAQ
ms.topic: article
ms.date: 06/09/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Frequently asked questions regarding DAP Monitoring.
author: kvamseek
ms.author: vamseekk
---

# Delegated administration privileges (DAP) FAQ

**Appropriate roles**: Admin agent | Helpdesk agent

Delegated administration privileges (DAP) enable a partner to manage a customer's service or subscription on their behalf.

The customer must grant a partner permission before the partner can use delegated administration privileges.

To get delegated administrator permissions from a customer, send an email to [Request a reseller relationship with the customer](request-a-relationship-with-a-customer.md).

After the customer approves the request, the partner's Admin agent or Helpdesk agent can sign in to the service's admin portal and manage the service on the customer's behalf. For example, a partner can:

- Use Helpdesk agent privileges to deliver support for the customer.
- Use Admin agent privileges to perform work on behalf of the customer.

###### DAP monitoring tool

The DAP monitoring tool captures how partner agents are accessing customer tenants across all their customer tenants through DAP.

Partners' Admin agents can use the DAP monitoring tool to audit DAP with their customers. Partners can then review usage data and remove DAP connections that aren't in use. This self-serve removal capability helps to improve security by controlling access.

## Removing DAP: Consequences

##### What capabilities does a partner lose when DAP is removed and GDAP is not enabled?

Disabling DAP access for a customer:

- Ends privileges to manage capabilities on the customer tenant.
  - To reenable management capabilities, you must reenable DAP.

- Ends the ability to create support requests for the customer.
  - To reenable the ability to create support tickets for the customer, you must reenable DAP.  

- Affects Microsoft 365 subscriptions in the following ways:

  - Can't upgrade a subscription because having [DAP](add-licenses-or-services-to-an-existing-subscription.md#conditions) is a prerequisite.

  - Can't [get subscription provisioning status](/partner-center/develop/get-subscription-provisioning-status#prerequisites) because provisioning requires DAP.
  
    To reenable Microsoft 365 subscription capabilities, you must reenable DAP on the customer tenant.

- Affects Azure subscriptions in the following ways:

  - Partners lose the ability to manage Azure subscriptions through Partner Center (but can manage the Azure subscription from [Microsoft Azure](https://portal.azure.com/)).

  - Partner admins can't see owners or reinstate any owners for Azure subscriptions that were provisioned after [DAP removal](./reinstate-csp.md).

    - However, customer Global admins can reinstate owner access on all the Azure subscriptions and assign roles to other agents in the customer tenants. To learn more, see [Reinstate admin privileges for Azure CSP](reinstate-csp.md).

    To reenable Azure subscription capabilities, you must reenable DAP on the customer tenant.

- Affects the response received from the [Get a customer by ID](/partner-center/develop/get-a-customer-by-id) API call.

  - The Get Customer ID API call won't return the following attributes if the partner doesn't have DAP access on the customer tenant.
  
    - CompanyProfileAddress
    - CompanyProfileEmail
    - CustomDomains

- Stops partners earning Partner Earned Credit (PEC) when RBAC is removed on existing new commerce Azure subscriptions.

- Doesn't affect PEC on existing new commerce Azure subscriptions.

  (For more information, see the [Partner Earned Credit and DAP](#partner-earned-credit-and-dap) section.)

## Monitoring DAP activity

##### What is DAP monitoring (the Administrative Relationships dashboard)?

In Partner Center, partners have access to a reporting tool that identifies and displays all active delegated administrative privilege connections and helps organizations discover inactive DAP connections. The reporting captures how partner agents are accessing customer tenants through those privileges and enables partners to remove connections that aren't in use. To improve security, Microsoft recommends that partners remove DAP connections that are no longer in use.  

To learn more, see [Monitoring administrative relationships and self-service DAP removal](dap-monitor-self-serve-removal.md).

##### How often is DAP monitoring data refreshed?

Data is refreshed daily for cross-tenant (AOBO) sign-in to customer tenants.

DAP monitoring data is available from December 7, 2021.

##### Does the DAP monitoring tool include all of the customers of an indirect provider along with customers through indirect resellers?

Yes. You get all your customers and your indirect resellers' customers.

##### When will the API for DAP monitoring and self-serve removal be available?

The API is expected to be available during Q1 of 2022.

## Reporting: DAP activity

##### Who can see DAP activity reporting (Administrative Relationships dashboard)?

Partners can see the DAP activity reporting/administrative relationships dashboard in **Account settings > Defender for Cloud > Administrative Relationships**.  

DAP activity reporting is available in Partner Center to partners in the Cloud Solution Provider program: direct-bill partners, indirect providers, and indirect resellers.

Users with the Partner Center role of *Admin agent* have access to the DAP activity report.

##### How many days of sign-in activities can partners see in DAP reporting?

Partners can see data since December 7, 2021 across all their customers. If there has been DAP activity by a partner user in a customer tenant since December 7, 2021, *Days Inactive* displays that value or is blank. However, if *Days Inactive* is greater than 90 days, "90+" is displayed (which means that the partner hasn't logged into the customer tenant for more than 90 days).

Partners with a subscription to Azure Active Directory (Azure AD) Premium Plan 2 can also view [Sign-in logs in Azure Active Directory](/azure/active-directory/reports-monitoring/concept-sign-ins) up to 30 days.

The following attributes display counts for the last one day:

- Number of agents sign-in
- Number of times the partner agent signed in

> [!NOTE]
> We are offering CSPs a free two-year subscription to [Azure Active Directory Premium Plan 2](https://partner.microsoft.com/resources/detail/cybersecurity-with-azure-ad-pdf) to help them further manage and get reports about access privileges.

##### What should partners do with DAP relationships that are no longer used or that have been inactive for more than 90 days?

To improve security, Microsoft recommends that partners remove delegated administrative privileges that are no longer in use or that have been inactive for 90 days or more. For guidance about using the DAP report and self-service removal, see [Monitoring administrative relationships and self-service DAP removal](dap-monitor-self-serve-removal.md).

## Reporting: Filtering users

##### Can indirect providers filter customers by indirect resellers in DAP reporting?

No. That kind of filtering isn't available in DAP reporting, but we're evaluating whether to add that capability in a future release.

___

## Azure and DAP

##### Can partners purchase new modern Azure plans after removing DAP?

Yes. Partners can still transact modern Azure plans. DAP isn't required to transact.  

##### After DAP is removed, how will a partner be able to reinstate owner rights on new commerce Azure plan and subscriptions?

To reinstate owner rights, a partner must request a new DAP relationship. However, a customer Global admin can reinstate owner access on all the Azure subscriptions and assign roles to other agents in the customer tenants. To learn more, see [Reinstate admin privileges for Azure CSP](reinstate-csp.md).

___

## Partner Earned Credit and DAP

To learn more about Partner Earned Credit, see [Partner earned credit: an overview of how it works in the new commerce experience in CSP](partner-earned-credit.md).

##### Do partners continue to earn PEC on the new Azure subscriptions added after the DAP is removed?

Yes. Partners continue to earn PEC on new Azure subscriptions added after DAP is removed.

##### Is PEC affected when DAP or GDAP are removed?

- If a partner customer has only DAP, and DAP is removed, PEC isn't lost.
- If a partner customer has DAP, and they move to GDAP for Office and Azure simultaneously, and DAP is removed, PEC isn't lost.
- If a partner customer has DAP, and they move to GDAP for Office but keep Azure as-is (that is, they don't move to GDAP), and DAP is removed, PEC won't be lost, but Azure subscription access will be lost
- If an RBAC role is removed, PEC is lost. (Removing GDAP doesn't remove RBAC.)


___

## Competencies and DAP

To learn more about Microsoft competencies, see [Differentiate your business by attaining Microsoft competencies](./mpn-benefits-map-competency-learning-option-enroll.md).

##### Will disabling DAP or transitioning to GDAP affect my legacy competency benefits or Solutions Partner designations I've attained?

DAP and GDAP are not eligible association types for Solutions Partner designations and disabling or transitioning from DAP to GDAP will not impact your attainment of Solutions Partner designations. Your renewal of legacy competency benefits or Solutions Partner benefits will also not be impacted.

Go to [Partner Center Solutions Partner designations](https://partner.microsoft.com/dashboard/mpn/program/solutionspartner/solutionareas/overview) to view what other partner association types are eligible for Solutions Partner designations.

