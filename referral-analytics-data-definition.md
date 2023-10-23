---
title: Data definition for referral insights
ms.topic: article
ms.service: partner-dashboard
ms.subservice: partnercenter-referrals
description: The document lists various reports and their data definitions, which you can download from the referral insights pages.
ms.date: 08/28/2023
author: JulCsc
ms.author: rohankaushik
---

# Referral insights download – Data definitions

**Appropriate roles**: Referrals admin

## Introduction

By using the Download button on the Lead and Co-sell analytics page, you can download the raw datasets.

The various reports, which you can download along with their data definitions, are listed in the following tables:

## Leads download

| Column Name | Data description |
|----|----|
|Referral ID|Unique ID for referral|
|Creation Date| Creation date of referral |
|Updated Date | Last updated date of referral |
|PartnerID | Microsoft AI Cloud Partner Program ID of the partner |
|Customer Country | Country/region of the customer |
|Customer City | City of the customer |
|Customer Name | Name of the customer |
|Lead Type | Type of the lead (Qualified lead, offer lead, profile lead) |
|Lead Source | Source of the referral: Appsource, Azure Marketplace, Azure portal |
|Call to action | Call to action (CTA) against which the lead is generated: Contact me, Get it now, Test drive |
|Referral program | Referral program from which qualified lead is generated |
|Business profile ID | Business profile ID |
|Offer ID | List of the offer ID |
|Offer name | List of offer name |
|Lead currency | Currency of the lead |
|Lead value | Estimated lead value provided by partner |
|Lead value (USD) | Estimated lead value provided by partner in USD |
|Status   | Latest status of referral |
|Status Reason | Remarks or reason for the status |

## Co-sell download

| Column Name | Data description |
|    ----    |    ----    |
| Referral ID | Unique ID for referral |
| Customer Country | Country/region of the customer |
| Customer City | City of the customer |
| Customer Name | Name of the customer |
| Referral Creation Date | Creation date of referral |
| Deal Type   | Type of the deal: co-sell, partner-led, private |
| Deal Direction | Direction of the deal: Incoming and Outgoing |
| Deal currency | Currency of the deal |
| Estimated Deal value | Estimated deal value provided by partner |
| Estimated Deal value (USD) | Estimated deal value provided by partner in USD |
| Solution ID   | List of the solution ID |
| Solution Name | List of the solution names |
| PartnerID | Microsoft partner network ID of the partner |
| Partner Name | Name of the partner |
| Deal ID | ID of the deal |
| Engagement ID | Unique engagement ID |
| Microsoft MSX ID   | MSX ID of deal |
| Microsoft Referral Creation Date | Referral creation date by Microsoft |
| Contract Currency | Currency of the contract provided during deal registration |
| Contract Value | Total contract value provided during deal registration. This value includes software and service fees but not hardware costs |
| Contract Value (USD) | Total contract value in USD provided during deal registration |
| Contract Start Date | Start date of the contract provided during deal registration |
| Contract End Date | End date of the contract provided during deal registration |
| Contract Sign Date | Sign date of the contract provided during deal registration |
| Contract Term | Term of the contract - Finite and Perpetual |
| Registered deal solution ID | ID of solution for deal registration |
| Registered deal solution name | Name of solution for deal registration |
| Registered deal solution currency | Currency for solution provided during deal registration |
| Registered deal solution value | Solution value provided during deal registration. Generally, this is total contract value less any non-recurring implementation fees. |
| Registered deal solution value (USD) | Solution value in USD provided during deal registration |
| Deployed On | Indicates if the solution is deployed on Azure or Others |
| Primary Deployment On | Indicates if the solution is deployed on Customer Tenant or Partner Tenant |
| Deal Creation Date | Creation date of deal registration |
| Deal Review Pending Date   | Date when deal registration is picked for Review |
| Deal Approved Date    | Date when deal registration is approved |
| Deal Review Passed Date    | Date when deal registration review is passed |
| Deal Review Failed Date    | Date when deal registration review is failed |
| Annual Contract Value    | Annualized contract value for approved and review passed deals |
| Pricing Model    | Pricing model for registered deals - Pay as you go and others |
| US Federal Deal | Indicates if it's a US federal deal |
| Is Marketplace Transacted Deal | Indicates if it's a Marketplace transacted deal |
| Marketplace transaction date | Marketplace transaction date if the deal is transacted on marketplace|
| Status   | Latest status of referral |
| Status Reason | Remarks or reason for the status |
| Partner Program | Indicates if this referral was shared because of your enrollment or participation in a specific go-to-market (GTM) program (for services co-sell deals). |
| Partner Role | Role that a services partner can play in the opportunity based on their endorsements (for services co-sell deals). |

## Next steps

- [Insights summary for referral](referral-insights-summary.md)
- [Insights around your co-sell opportunities](referral-cosell-insights.md)
- [Insights around your leads](referral-leads-insights.md)
