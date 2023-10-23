---
title: Nonpayment, fraud, and misuse
description: Learn about the various risks involved in online transactions and the best practices to manage and mitigate those risks in Partner Center.
ms.topic: article
ms.service: partner-dashboard
ms.subservice: partnercenter-account
author: vijay-vala
ms.author: vijvala
ms.date: 11/18/2021
ms.custom: engagement-fy23
---

# Nonpayment, fraud, and misuse

**Applies to**: Partner Center | Partner Center for Microsoft Cloud for US Government

**Appropriate roles**: Global admin | User management admin | Admin agent | Billing admin

We *strongly recommend* that Cloud Solution Provider (CSP) partners implement rigorous fraud prevention and detection risk mitigation controls, because direct-bill and indirect CSPs are financially responsible for fraudulent purchases by their customers and customers' nonpayment of purchased services. By signing the Microsoft Partner Agreement (MPA), CSPs agree to be bound by the terms of our policies, and Microsoft's policy around Azure fraud and non-payment requires partners to be financially liable for fraudulent activity that occurs in any of their Partner Portal accounts.

To avoid fraudulent activity or misuse, or to address them, it's important to understand potential risks and to develop policies and practices that can reduce partners' exposure. This article focuses on the following activities:

- [Onboarding new customers](#onboard-new-customers)
- [Managing customer accounts](#manage-customer-accounts)
- [Managing customer billing](#manage-customer-billing)

For additional strategies for mitigating online risk, see the [Online transaction risk management guide](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4Bhtt).

Microsoft regularly assesses its policies and platforms to ensure we are market competitive. As part of that effort, we are adding an exception request process to the CSP new commerce experience for fraudulent activity that occurs on individual Azure customer tenants on or after April 1, 2023.

Microsoft will review and may provide a limited, one-time discretionary credit for first-time instances of verified account compromises of new commerce platform subscriptions. Requests can only be submitted once per customer tenant ID.

To be eligible for review, the impacted partner must file a refund request support ticket through the Azure portal within 60 calendar days of the first usage date of fraudulent activity, regardless of when the activity is discovered. As part of normal business activity, Microsoft expects partners to address and mitigate any security risk(s) stemming from these incidents moving forward.

## Abuse-of-service risks

*Abuse-of-service* risks are customers who use cloud services in violation of the Microsoft acceptable use policy.

### Examples of abuse-of-service

Some examples of violations of the Microsoft acceptable use policy are:

- Crypto-mining (without Microsoft's prior written approval)
- Spamming
- Hacking
- Distributed denial-of-service (DDoS) attacks
- Malware distribution
- Resale of pirated subscriptions

## Theft-of-service risks

*Theft-of-service* risks are customers who have no intention of paying for consumed services. This theft may involve using stolen payment instruments, providing false billing information, or defaulting on outstanding balances.

### Examples of service-theft

Some examples of online transaction risks are:

- Transactions that don't occur in person ("credit card not present" transactions)
- Misrepresented identities
- Services provisioned and used before initial payment is received
- Emerging markets or high-risk regions for online fraud
- Automated account creation and purchasing by bad actors

## Manage online risk

Partners can use the following recommendations to help you develop policies and practices to reduce their exposure to online transaction risks in their customer relationships.

### Onboard new customers

Suggestions for reducing online risks when onboarding new customers include:

- Establish personal relationships with customers when possible (for example, contacting customers by phone).
- Verify customers' credentials and background through better methods (such as using credit bureaus or business commercial report agencies).
- Use multi-factor authentication (such as SMS verification) during sign-up to minimize exposure to robotic account creation and purchasing.
- Require customers to monitor and secure their tenants using tools such as multi-factor authentication.
- Manage and track identities using services (such as digital identity services).
- Assess customer financial strength through rigorous credit card fraud detection systems.
- Establish a clear collections policy. Detail collections processes and when access to subscriptions will be affected by nonpayment. (Partners can disable access or [suspend a customer's subscriptions](create-a-new-subscription.md#suspend-a-subscription) for nonpayment.)

### Manage customer accounts

Suggestions for managing customer accounts post-purchase include:

- Implement a process to quickly receive, review, act on, and respond to Microsoft notifications.
- Work with customers to understand their cloud usage business needs while setting appropriate monitoring thresholds. (For example, partners can [set a monthly Azure spending budget](set-an-azure-spending-budget-for-your-customers.md) in Partner Center. This understanding allows partners to monitor customer usage during the month, and to be notified when customers are close to their budget.)
- Monitor [customer activity logs](activity-logs.md) regularly via the Account settings workspace to help detect fraud early.
- Take quick action when suspicious activities are detected.
- Avoid giving customers full administrative access to subscriptions without first implementing risk mitigation controls.

### Manage customer billing

Suggestions for managing customer billing post-purchase include:

- Request prepayment prior to initial transactions and billing.
- Don't accept high-risk payment instruments (such as pre-paid cards or stored-value cards).
- Monitor customer payments and aging accounts receivables. Aggressively enforce standardized dunning processes for late payments or nonpayment.

> [!IMPORTANT]
> Invoice payments show up in the Partner Center **Billing** workspace in **5 business days.** Customers should check that billing information is correct before submitting a payment to make sure that payments go through smoothly.

## Enforcement of Microsoft acceptable use policy

When Microsoft detects partner or customer activity that we confirm or suspect violates the acceptable use policy, we take enforcement steps. The customer could be immediately suspended. Partners are notified of enforcement actions or updated on their requests by Microsoft.

> [!NOTE]
> Find Microsoft policies in [Licensing Resources and Documents](https://www.microsoft.com/licensing/docs).
