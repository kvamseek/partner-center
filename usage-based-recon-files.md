---
title: Usage-based reconciliation files
ms.topic: article
ms.date: 11/08/2022
description: Learn about all of the items on your usage-based reconciliation file in Partner Center. Includes a few examples.
author: sodeb
ms.service: partner-dashboard
ms.subservice: partnercenter-billing
ms.author: sodeb
---

# Understand usage-based reconciliation files and their specific fields in Partner Center

**Appropriate roles**: Account admin | Billing admin

To reconcile your charges against a customer's usage, compare the **ResellerID**, **ResellerName**, and **ResellerBillableAccount** from the reconciliation file with the **Customer name** and **Subscription ID** from Partner Center.

## Fields in usage-based reconciliation files

The following fields explain which services were used and the rate.

| Column | Description | Sample values |
| ------ | ----------- | ------------ |
| PartnerId | PartnerIDentifier, in GUID format. | *DA41BC5F-C52D-4464-8A8D-8C8DCC43503B* |
| PartnerName | Partner name. | *Contoso, Ltd.* |
| PartnerBillableAccountId | Partner account identifier. | *1010578050* |
| CustomerCompanyName | Customer's organization name, as reported in Partner Center. *This is very important for reconciling the invoice with your system information.* | *Test customer* |
| MPNID | Microsoft AI Cloud Partner Program identifier of the Cloud Solution Provider (CSP) partner. | *4390934* |
| ResellerMPNID | Identifier of the reseller of record for the subscription.  |
| InvoiceNumber | Invoice number where the specified transaction appears. | *D020001IVK* |
| ChargeStartDate | Start date of billing cycle, except when presenting dates of previously uncharged latent usage data (from previous bill cycle). The time is always the beginning of the day, 0:00. | *2/1/2019 0:00* |
| ChargeEndDate | End date of billing cycle, except when presenting dates of previously uncharged latent usage data (from previous bill cycle). The time is always the end of the day, 23:59. | *2/28/2019 23:59* |
| SubscriptionId | Unique identifier for a subscription in the Microsoft billing platform. May be useful to identify the subscription when contacting support. Not used for reconciliation. *This is not the same as the **Subscription ID** on the Partner Admin Console.* | *usCBMgAAAAAAAAIA* |
| SubscriptionName | Nickname for the service offering. | *Microsoft Azure* |
| SubscriptionDescription | Line of business of the service offering. | *Microsoft Azure* |
| OrderID | Unique identifier for an order in the Microsoft billing platform. May be useful to identify the subscription when contacting support. Not used for reconciliation. | *566890604832738111* |
| ServiceName | The name of the Azure service in question. | *VIRTUAL MACHINES* |
| ServiceType | The specific type of Azure service. | *Service Bus – Individual or Pack*, *SQL Azure database – Business or Web Edition* |
| ResourceGuid | Specific unique identifier for all the service data and pricing structure. | *DA41BC5F-C52D-4464-8A8D-8C8DCC43503B* |
| ResourceName | The name of the Azure resource. | *Data Transfer In (GB)*, *Data Transfer Out (GB)* |
| Region | The region to which the usage applies. Primarily used to assign rates to data transfers, because rates vary by region. | *Asia Pacific*, *Europe*, *Latin America*, *North America* |
| Sku | Unique Microsoft identifier for an offer. | *7UD-00001* |
| DetailLineItemId | An identifier and quantity to itemize different rates for a service or resource in a given billing period. For Azure tiered pricing, there may be one rate for up to a certain quantity of billable units, then a different rate after that quantity. | *1* |
| ConsumedQuantity | The amount of service consumed (such as hours or GB) during the reporting period. Also includes any unbilled usage from previous reporting periods. | *11* |
| IncludedQuantity | Units included as part of the offer. Typically not present in CSP. | *0* |
| OverageQuantity | Units not included as part of the offer. These must be paid for by the partner. Equal to **ConsumedQuantity** minus **IncludedQuantity**. | *11* |
| ListPrice | Offer price in effect at subscription's start date. | *$0.0808* |
| PretaxCharges | Equal to **ListPrist** multiplied by **OverageQuantity**, rounded to the nearest cent. | *$0.085* |
| TaxAmount | Tax amount charged. Based on your market's tax rules and specific circumstances. | *$0.08* |
| PostTaxTotal | Total after tax, when tax is applicable. | *$0.93* |
| Currency | Currency type. Each billing entity has only one currency. Check that it matches your first invoice and then after any major billing platform updates. | *EUR* |
| PretaxEffectiveRate | Pretax price per unit. Equal to **PretaxCharges** divided by **OverageQuantity**, rounded to the nearest cent. | *$0.08* |
| PostTaxEffectiveRate | Post tax price per unit. Equal to **PostTaxTotal** divided by **OverageQuantity**, rounded to the nearest cent. Or, equal to **PretaxEffectiveRate** plus the tax rate per unit amount, rounded to the nearest cent. | *$0.08* |
| ChargeType | The [type of charge](recon-file-charge-types.md) or adjustment. | See [charge types](recon-file-charge-types.md). |
| CustomerId | Unique Microsoft identifier for the customer, in GUID format. | *ORDDC52E52FDEF405786F0642DD0108BE4* |
| DomainName | Customer's domain name. This field may appear blank until the second billing cycle. | *example.onmicrosoft.com* |
| BillingCycleType | Time billing frequency.| **Monthly**  |
| Unit | The unit of the resource **Name**. | *GB* or *HOURS* |
| CustomerBillableAccount | Unique account identifier in the Microsoft billing platform. | *1280018095* |
| UsageDate | Date of service deployment. | *2/1/2019 0:00* |
| MeteredRegion | Identifies the location of a data center within the region (for services where this value is applicable and populated). | *East Asia*, *South East Asia*, *North Europe*, *West Europe*, *North Central US*, *South Central US* |
| MeteredService | Identifies the individual Azure service usage when it's not specifically identified in the **ServiceName** column. For example, data transfers are reported as *Microsoft Azure - All Services* in the **ServiceName** column. | *AccessControl*, *CDN*, *Compute*, *Database*, *ServiceBus*, *Storage* |
| MeteredServiceType | Subheading for **MeteredService** field that provides additional clarification of Azure service usage. | *EXTERNAL* |
| Project | Customer-defined name for their service instance. | *ORDDC52E52FDEF405786F0642DD0108BE4* |
| ServiceInfo | The number of Azure Service Bus connections that were provisioned and utilized on a given day. | *1.000000 Connections / 30 days* (if you had an individually provisioned connection during a 30-day month), *25 Connections / 30 Days – Used: 1.000000* (if you had a 25 pack of Service Bus connections provisioned and you utilized 1 during that day) |

## Next steps

- [Understand the fields in Partner Center license-based reconciliation files](license-based-recon-files.md)
