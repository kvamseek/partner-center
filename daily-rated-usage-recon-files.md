---
title: Daily-rated usage reconciliation files
ms.topic: article
ms.date: 11/8/2022
description: Learn how to read daily-rated usage reconciliation files in Partner Center. Includes descriptions for specific fields in the recon file.
ms.service: partner-dashboard
ms.subservice: partnercenter-billing
author: sodeb
ms.author: sodeb
---

# Learn how to read daily-rated usage reconciliation files in Partner Center

**Applies to**: Partner Center | Partner Center for Microsoft Cloud for US Government

**Appropriate roles**: Admin agent | Billing admin | Sales agent | Helpdesk agent

This article explains how to read daily-rated usage reconciliation files.

> [!NOTE]
>Generally, daily rated unbilled usage data is available via API or the Partner Center portal after 24 hours. Depending on your location and when the meters report usage, additional delays may occur.
>
>Sometimes, you might not see the most recent unbilled usage data from the beginning of the month until the previous month’s billed usage data is delivered. This is to make sure the billed usage data is delivered efficiently within the SLA. Once you receive the billed usage data, you can start retrieving all the updated unbilled usage data from the beginning of the month.
>

> [!NOTE]
> The following charges are not included in the daily rated usage file:
>
> - Azure Reservation (only shows quantity, no cost)
> - Azure Savings Plan (only shows quantity, no cost)
> - Office
> - Dynamics
> - Power Apps
> - Perpetual software
> - Software subscriptions
> - Third-party SaaS products

## Fields in daily-rated usage reconciliation files

| Column | Description |
| ------ | ----------- |
| PartnerId | CSP Partner identifier. |
| PartnerName | Partner name. |
| CustomerId | Customer identifier. |
| CustomerName | Customer’s organization |
| CustomerDomainName | Customer’s domain name. |
| CustomerCountry | Customer location. |
| MPNID | Microsoft partner identifier. |
| ResellerMPNID | Reseller on record. ***It’s blank in the unbilled usage data.*** |
| InvoiceNumber | Invoice number. |
| ProductId | Product identifier. |
| SkuId | SKU identifier. |
| AvailabilityId | Availability identifier|
| SkuName | SKU name. |
| ProductName | Product name. |
| PublisherName | Publisher’s name. |
| PublisherId | Publisher identifier. |
| SubscriptionDescription | Service offering name. (This column is an identical field to **OfferName**). |
| SubscriptionId | Subscription identifier in the Microsoft billing platform. Not used for reconciliation. *This identifier isn’t the same as the **Subscription ID** on the partner admin console.* |
| ChargeStartDate | Billing start date. |
| ChargeEndDate | Billing end date. It could be the end of the month or the first of the following month. The charges, however, are based on the **Usage Date,** not this date. |
| UsageDate | Service usage/consumption date.|
| MeterType | Meter type. |
| MeterCategory | Top-level service for the usage. |
| MeterId | Meter identifier. |
| MeterSubCategory | Azure service type. |
| MeterName | Unit of measure for the meter consumption. |
| MeterRegion | Data center location within the region. |
| Unit | Unit of the resource **Name**. |
| ResourceLocation |Data center where the meter is running. |
| ConsumedService | Azure platform service used. |
| ResourceGroup | Resource container. |
| ResourceURI | URI of the resource. |
| ChargeType | Charge or adjustment type.  |
| UnitPrice | Price per unit, as published in the price list at the time of purchase. Make sure this price matches the information stored in your billing system during reconciliation. |
| Quantity | Number of units. |
| UnitType | Unit used for charging.  |
| BillingPreTaxTotal | The total bill amount before tax, but after deducting any applicable PEC. |
| BillingCurrency | Partner billing/invoice currency. |
| PricingPreTaxTotal | Total bill amount in the pricing currency before taxes. |
| PricingCurrency | Currency in the price list. |
| ServiceInfo1 | Number of Service Bus connections. |
| ServiceInfo2 | Legacy field for service-specific metadata. |
| Tags | Logical organization of Azure resources set by the user. |
| AdditionalInfo | Additional information. |
| EffectiveUnitPrice | Actual value charged per unit after discounts or adjustments. |
| PCToBCExchangeRate | Exchange rate for pricing to billing currency. |
| PCToBCExchangeRateDate | Date of exchange rate calculation. |
| EntitlementId | Azure subscription ID. |
| EntitlementDescription | Azure subscription name. |
| PartnerEarnedCreditPercentage | Partner Earned Credit (PEC) percentage. Either 0 or 15 percent. |
| CreditPercentage | Azure credit percentage.|
| CreditType | Credit type (e.g., **Azure Credit Applied.** |
| BenefitOrderId | Azure savings plan identifier, similar to the reservation order ID for Azure reservations. It matches the **ReservationOrderID** in monthly reconciliation data to map the monthly total cost to daily charges. *It can be left blank for other product types*. |
| BenefitId      | Identifier for each Azure savings plan. *It can be left blank for other product types*.|
| BenefitType    | Savings plan type identifier (e.g., **SavingsPlan** )|
