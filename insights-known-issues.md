---
title: Cloud product performance insights FAQ
ms.topic: article
ms.date: 11/09/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-insights
description: Read about any known issues associated with Partner Center Insights (PCI) reports. Information may include known rendering issues or reporting limitations.
author: kshitishsahoo
ms.author: ksahoo
---

# Cloud product performance insights FAQ

**Appropriate roles**: Report viewer | Executive report viewer

This article covers known issues for viewing or rendering reports associated with Insights.

## I don't see the Insights hub in my Partner Center account. What should I do?

Make sure you have logged in into the Microsoft AI Cloud Partner Program account for your organization. You cannot access the Insights dashboard from your Cloud Solution Provider (CSP) account. Also ensure that you have been provided Report viewer or Executive report viewer role access by your Global admin. For more information about roles, see [this article](./insights-roles.md).

## I am unable to see Billed Revenue or Azure Consumed Revenue (ACR) data in my reports. Why is that?

Billed Revenue and ACR data is available only to users who are Executive report viewers. For more information about roles, see [Membership role-based access](./insights-roles.md).

## The country/region reported for my customer seems to be incorrect. Why is that?

The customer country/region is derived from the country/region of the Global parent organization of that customer. This country/region might be different from the country/region of the customer with whom you might have transacted. Hence, the customer-reported country/region might be different from what you expect it to be.

## I see a few customer names are obfuscated in the reports. Is that expected?

Customer names are obfuscated for certain subscriptions because of compliance reasons. However, the customer Top Parent ID (TPID) is available, and you can use that to look up customer names.

## What is the typical latency of the reports?

Subscriptions and Customers data is refreshed daily and data is reported with a latency of five days. Azure usage data is reported with a latency of four days. Office 365, Teams, Dynamics 365, Enterprise Mobility and Security (EMS), and Power BI usage data is reported with a latency of one month. For more information, see [Insights data frequency](insights-data-frequency.md).

## I've added a new customer but it's not showing in my reports, why is that?

New customers will be added to the reports during the next data refresh cycle. The data refresh cycle is completed by the 20th of each month. For example, if you add a new customer March 25, they'll appear in the reports updated by April 20. If you add a new customer April 15, they may appear in the reports updated by April 20 but if the data refresh is complete for April, they'll appear in the reports updated by May 20.

## The reports are not rendering in Internet Explorer. Is that expected?

The reports have rendering issues with Internet Explorer. They work well with Microsoft Edge and other browsers.

## Next steps

- Learn more about [Partner Center Insights](partner-center-insights.md).


