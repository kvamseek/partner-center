---
title: Essential steps to confirm, contain, and secure a compromise
ms.topic: how-to
ms.service: partner-dashboard
ms.subservice: partnercenter-account
description: Account settings workspace - This infographic helps partners take actions to confirm, contain, and secure a compromise.
author: vijvala
ms.author: vijvala
ms.date: 10/02/2023
---

# Essential steps to confirm, contain, and secure a compromise

**Appropriate roles**: Admin agent | Security contact

This article helps you take actions to confirm, contain, and secure a compromise.

:::image type="content" source="media/security/essential-steps-secure-compromise.png" lightbox="media/security/essential-steps-secure-compromise.png" alt-text="Infographic flow showing steps to confirm, contain, secure, and improve security compromises.":::

1. **Confirm**:
   - Review the Azure subscriptions that are compromised and check for the spending anomalies. For more information, see [Microsoft cost management](/azure/cost-management-billing/costs/quick-acm-cost-analysis).
   - Conduct thorough investigations examining the [risky users](/azure/active-directory/identity-protection/howto-identity-protection-investigate-risk#risky-users) and [Azure Monitor activity logs](/azure/azure-monitor/essentials/activity-log?tabs=powershell) to confirm the compromise and contain the exposure immediately. It's important to note that any persistence methods missed during the investigation could result in continued access by the attacker, which could lead to a potential recompromise. Therefore, it's essential to be meticulous in your investigation to prevent any future attacks.
1. **Contain**:
   - If you have determined that a customer has been compromised and there's fraud-in-flight you can try to work with the customer or take unilateral action and cancel the subscription. You can start by immediately [canceling the Azure subscriptions](/partner-center/azure-plan-manage#cancel-an-azure-subscription) that are confirmed to contain the compromise. Then, take the required steps to identify and evict the threat actor quickly. For more information, see [how to quickly remediate the compromised identities](azure-fraud-notification.md#what-should-you-do-if-an-azure-subscription-has-been-compromised).
1. **Secure**:
   - Now that the abuse has been contained you should do the work to secure the tenant. Follow the best practice guidelines for [Cloud Solution Providers](csp-security-best-practices.md) and [customer tenants](customer-security-best-practices.md). For more information, see the [instructions on how to address security alerts](azure-fraud-notification.md#what-should-you-do-if-an-azure-subscription-has-been-compromised).
1. **Improve**:
   - Take some time to investigate and understand how the compromise occurred. Doing so may uncover weaknesses in your overall security posture that can be remediated.
