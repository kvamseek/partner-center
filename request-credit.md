---
title: Request a credit from Microsoft
ms.topic: article
description: Learn the benefits, restrictions, and procedures to request a credit from Microsoft.
ms.service: partner-dashboard
ms.subservice: partnercenter-billing
author: sodeb
ms.author: sodeb
ms.date: 5/4/2023
---

# How and when to request a credit from Microsoft

**Appropriate roles**: Admin agent | Global admin

This article explains how Cloud Solution Provider (CSP) direct and indirect providers can request credit for:

- [Accidental purchases](#accidental-purchase-credit)
- [Duplicate orders](#duplicate-orders-credit)
- [Service outages (service-level agreement issues)](#service-outages-service-level-agreement-issues-credit)
- Technical issues
- Incorrect information from Microsoft

## Considerations

Credit requests are accepted only from CSP direct and indirect providers. Requests aren't accepted from indirect resellers.

[Creating a service request for a customer in Microsoft Azure](./report-problems-on-behalf-of-a-customer.md) is a separate process.

## Request credit

To request a credit:

1. Download and complete the [Request for Credit or Refund Form](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RWN4vE). (Selecting the preceding link downloads the form directly to your default download folder.)
1. Create a support ticket in [Partner Center](https://partner.microsoft.com/support/v2/?stage=2&topicid=cb49dd48-9497-e427-1a6e-f4d5f51da512).
1. Attach the completed form and submit.

## Types of credits

### Accidental purchase credit

For credit requests for legacy offers of *Microsoft 365* or *Microsoft Dynamics 365* (for example, when the number of licenses was increased accidentally, or the wrong product was purchased):

- Cancellations of subscriptions within 30 days of purchase are refunded 100% with no need to create a service request. The credit appears in the invoice/reconciliation file issued after the subscription is suspended.
- If you suspend a subscription in months 2 to 12, you'll be credited on a prorated basis. To receive a full refund from the start of the subscription, a request must be submitted within 90 days of purchase, except:
  - **All Microsoft Power BI Premium SKUs**: A request must be submitted within seven days for 100% refund. After seven days, fixed costs amounting to USD33 per day, regardless of the number of licenses, will be deducted from the credit.
  - **Microsoft 365 A1**: Full credit is provided only if the request is submitted within 30 days of purchase and no users are assigned to the subscription. No refunds are issued after 30 days from purchase.

> [!NOTE]
> This policy only applies to offers purchased via the **legacy** commerce experience. For offers purchased via the new commerce experience, see the policy published at [Create customer subscriptions](create-a-new-subscription.md#cancel-new-commerce-license-based-subscriptions).

### Duplicate orders credit

For credit requests for duplicate licenses (for example, when a customer has duplicate licenses after migrating to another tenant or to another CSP partner):

- Credit requests must be submitted within **120** days of the **new** subscription purchase.
- Customers who voluntarily transition between partners or tenants lose all the offers on their agreements.
- Previous promotions aren't carried over if they're no longer available.
- New offers are purchased at the current price.

> [!NOTE]
> This policy only applies to offers purchased via the **legacy** commerce experience. For offers purchased via the new commerce experience, see the policy published at [Create customer subscriptions](create-a-new-subscription.md#cancel-new-commerce-license-based-subscriptions).

### Service outages (service-level agreement issues) credit

For credit requests for service outages:

- SLA credits from Microsoft are determined based on which services were affected. For example, if your customer has an *Office 365* suite but only experienced a SharePoint outage, the SLA credit is approved only for SharePoint and not the customer's entire plan.
- Credits are prorated based on the service affected and the duration of the outage. To see the types of scenarios that qualify for SLA credits, see the Online [Services Consolidated SLA document](https://www.microsoft.com/licensing/docs/view/Service-Level-Agreements-SLA-for-Online-Services). This information applies to services sold through the Cloud Solution Provider (CSP) program, too.
- For claims related to Microsoft Azure, credit requests must be submitted within two months from the end of the billing month in which the incident occurred.  For claims related to all other services, credit requests must be submitted within one month from the end of the billing month in which the incident occurred. (More details are in the *Request for Credit or Refund Form*).
- You must provide evidence that the customer was affected by the outage and that they requested an SLA credit. Customer tenant ID and outage ID (from the Service Health Dashboard) must be provided. The customer email submitted as evidence must come from the domain of the affected tenant. (Email from a personal address isn't acceptable).

> [!NOTE]
> Advisory incidents are generally not eligible for SLA credits. An incident posted to the Service Health Dashboard indicates that a tenant *might* be affected and represents the best information Microsoft has at the time of publishing. Health page data represents the general availability of a service. Effects on individual service, mitigation, and resolution might vary. You can review the final Incident Post and Post Incident Review for more details. For more information about service health, see [How to check Microsoft 365 service health](/microsoft-365/enterprise/view-service-health).

> [!NOTE]
> This policy applies to offers purchased both the **legacy** commerce experience and the **new** commerce experience.

### Required information

Customer name, tenant identifier, partner ticket number, and ticket created date and time stamp aren't sufficient for a claim to be processed.

Before you [submit an SLA credit request](https://www.microsoft.com/licensing/docs/view/Service-Level-Agreements-SLA-for-Online-Services) to Microsoft, you must gather all the following information to include in your support ticket:

- The customer tenant's GUID
- The [outage incident identifier](#outage-incident-identifier)
- Evidence that the customer was affected by the outage and has requested an SLA credit
- Were the affected subscriptions purchased through CSP? (**Yes** or **no**)

### Evidence that proves customer impact

- Information regarding the time and duration of the downtime
- The number and locations of affected users (if applicable)
- Descriptions of your attempts to resolve the incident at the time of occurrence
- An email from the affected customer requesting support and subsequently credit
- The support ticket number and details of customer contact regarding resolving service impact

### Outage incident identifier

You can find the identifier for the outage incident on the Service Health page in the Microsoft 365 admin center. The Outage Incident ID is a number preceded by a two-letter abbreviation that indicates the affected service (for example, EX25194 for an Exchange Online outage).

The following table describes common service abbreviations:

| Two-letter abbreviation | Microsoft service |
| ----------------------- | ----------------- |
| EX | Exchange Online |
| FO | Exchange Online Protection |
| SB | Skype for Business Online (formerly Lync Online) |
| OS | Office Subscription |
| PB | Power BI for Office 365 |
| SP | SharePoint Online |
| YA | Yammer Enterprise |
| MO | Portal error |

## Next steps

- [Report problems on behalf of your customer](report-problems-on-behalf-of-a-customer.md)
