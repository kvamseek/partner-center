---
title: Begin using pay-as-you-go rates with the Azure plan
description: Learn what you and your customers need to know about using the Azure pay-as-you-go plan, including first steps, security precautions, and how to get started.
ms.topic: article
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
author: brentserbus
ms.author: brserbus
ms.date: 2/28/2022
---

# Begin using pay-as-you-go rates with the Azure plan

**Appropriate roles**: Admin agent | Sales agent

Microsoft has introduced a new commerce experience in Partner Center.  With this new commerce experience, partners will gain access to Azure services at pay-as-you-go rates for customers under the Microsoft Customer Agreement.

This plan simplifies the purchase experience because you can have multiple Azure subscriptions in an Azure plan. You no longer need to submit a separate order per Azure subscription. And in this new commerce experience for Azure, we have aligned to a single global pricing principle that enables Cloud Solution Provider (CSP) partners to offer Azure at the published prices.

The digital transformation needs of our customers require new skills from partners. Many customers look for partners to provide services above and beyond the transaction to make their cloud journey smoother and help consume Azure services efficiently. Microsoft partners play a critical role in all stages of the customer lifecycle. These kinds of partner services are on-going in nature and include Azure estate monitoring, policy and governance management, set up and configuration fine-tuning, technical support and various other services. They require a partner to be intimately familiar with the customer's Azure environment and have continuous and appropriate governance and control of the underlying resources they manage. Billing partners who provide this 24 X 7 cloud-operations management will become eligible for a **Partner earned credit for services managed** for that work.

## Make sure your customers have signed the Microsoft Customer Agreement

Since October 1, 2019, the Microsoft Customer Agreement, a perpetual agreement that simplifies and streamlines the customer purchasing experience with a fully digital process, is available. All customers who want to take advantage of the new commerce experience in CSP for Azure must sign the Microsoft Customer Agreement.

Partners who want to transact under the new Azure plan and make a new order should confirm customer acceptance of the Microsoft Customer Agreement using the Partner Center and API in production.

Since February 2020, partner confirmation (attestation) of the customer acceptance for the new Microsoft Customer Agreement has been required for all other offers including Microsoft 365, Dynamics 365, and existing Azure. Partners in the CSP can't make a new order for the customer without attestation of the Microsoft Customer Agreement.

For full details, read [Confirm customer acceptance of the Microsoft Customer Agreement](confirm-customer-agreement.md)

## Security and access control practices

To help safeguard partners and customers, we have introduced a set of mandatory security requirements for Advisors, Control Panel Vendors, and partners participating in the Cloud Solution Provider program.

Partners who do not implement the mandatory security requirements will not be able to transact in the Cloud Solution Provider program or manage customer tenants using delegate admin rights, once these requirements are enforced. We are in the process of establishing a technical enforcement date for the requirements and will notify partners of the date with detailed information.

## Actions to take to implement MFA

Given the highly privileged nature of being a partner we need to ensure that each user has an MFA challenge for every single authentication. This can be accomplished through one of the following ways:

- Implementing Azure AD Premium and ensure that multifactor authentication (MFA) is enforced for each user
- Implementing the [Azure AD security defaults](/azure/active-directory/conditional-access/concept-conditional-access-security-defaults)
- Implementing a third-party solution and ensure MFA is enforced for each user

Starting August 1, 2019, all partners are required to enforce multifactor authentication for all users, including service accounts, in their partner tenant. Detailed information on these security requirements can be found at [Partner security requirements](partner-security-requirements.md).

Microsoft recommends partners make use of role-based access control (RBAC) diligently, following best practices enabled through [Azure Active Directory Privileged Identity Management resources](/azure/active-directory/privileged-identity-management/pim-configure). We also recommend using [Azure Lighthouse](/azure/lighthouse/concepts/cloud-solution-provider) for a more scalable, secure, and simplified management experience.

## Read more about the Azure plan

- [Purchase the Azure plan](purchase-azure-plan.md)

- [Compare Azure offers](compare-azure-offers.md)

- [Partner earned credit - overview](partner-earned-credit.md)

- The partner earned credit (PEC) calculations and the roles and permissions that are eligible to earn partner earned credits are available from your Partner Center price list (sign-in required).

## Next steps

- [How the partner earned credit is determined - details](partner-earned-credit-explanation.md)
- [Azure plan price list explained](azure-plan-price-list.md)
- [Transition your customer to Azure plan](azure-plan-transition.md)
- [Manage subscriptions and resources under the Azure plan](azure-plan-manage.md)
- [The full list of countries/regions where Azure plan is available](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE3QN0x)
