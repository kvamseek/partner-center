---
title: License-based reconciliation files
ms.topic: article
ms.date: 11/8/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-billing
description: Learn how to read license-based reconciliation files in Partner Center. This article explains the meaning of each field in your license-based recon file.
author: sodeb
ms.author: sodeb
---

# Understand the fields in Partner Center license-based reconciliation files

**Applies to**: Partner Center | Partner Center for Microsoft Cloud for US Government

**Appropriate roles**: Global admin | User management admin | Billing admin | Admin agent

To reconcile your changes against a customer's orders, compare the **Syndication_Partner_Subscription_Number** from the reconciliation file against the **Subscription ID** from Partner Center.

## Fields in license-based reconciliation files

| Column | Description | Sample value |
| ------ | ----------- | ------------ |
| PartnerId | Unique identifier in GUID format for a specific billing entity. Not required for reconciliation. Same in all rows. | *8ddd03642-test-test-test-46b58d356b4e* |
| CustomerId | Unique Microsoft identifier for the customer in GUID format. | *12ABCD34-001A-BCD2-987C-3210ABCD5678* |
| CustomerName | Customer's organization name, as reported in Partner Center. *Very important field for reconciling the invoice with your system information.* | *Test Customer A* |
| MPNID | Identifier of the CSP partner. | *4390934* |
| ResellerMPNID | Identifier of the reseller of record for the subscription.  |
| OrderId | Unique identifier for an order in the Microsoft billing platform. May be useful to identify the order when contacting support. Not used for reconciliation. | *566890604832738111* |
| SubscriptionId | Unique identifier for a subscription in the Microsoft billing platform. May be useful to identify the subscription when contacting support. Not used for reconciliation. *This value is not the same as the **Subscription ID** on the Partner Admin Console. See **SyndicationPartnerSubscriptionNumber** instead.* | *usCBMgAAAAAAAAIA* |
| SyndicationPartnerSubscriptionNumber | Unique identifier for subscriptions. A customer can have multiple subscriptions for the same plan. This column is important for reconciliation file analysis. This field maps to the **Subscription ID** in the Partner Admin Console. | *fb977ab5-test-test-test-24c8d9591708* |
| OfferId | Unique offer identifier. Standard offer identifier, as defined in the price list. *This value does not match **Offer ID** from the price list. See **DurableOfferID** instead.* | *FE616D64-E9A8-40EF-843F-152E9BBEF3D1* |
| DurableOfferId | Unique durable offer identifier, as defined in the price list. *This value matches the **Offer ID** from the price list.* | *1017D7F3-6D7F-4BFA-BDD8-79BC8F104E0C* |
| OfferName | The name of the service offering purchased by the customer, as defined in the price list. | *Microsoft Office 365 (Plan E3)* |
| SubscriptionStartDate | The subscription start date in UTC. The time is always the beginning of the day, 0:00. This field is set to the day after the order was submitted. Used with the **SubscriptionEndDate** to determine: if the customer is still within the first year of the subscription, or if the subscription has been renewed for the following year. | *2/1/2019 0:00* |
| SubscriptionEndDate | The subscription end date in UTC. The time is always the beginning of the day, 0:00. Either *12 months plus **x** days after the start date* to align with the partner's billing date or *12 months from the renewal date*. At renewal, prices are updated to the current price list. Customer communication may be required in advance of automated renewal. | *2/1/2019 0:00* |
| ChargeStartDate | Start day of the charges. The time is always the beginning of the day, 0:00. Used to calculate daily charges (*pro rata* charges) when a customer changes license numbers. | *2/1/2019 0:00* |
| ChargeEndDate | End day of the charges. The time is always the end of the day, 23:59. Used to calculate daily charges (*pro rata* charges) when a customer changes license numbers. | *2/28/2019 23:59* |
| ChargeType | The [type of charge](recon-file-charge-types.md) or adjustment. | See [charge types](recon-file-charge-types.md). |
| UnitPrice | Price per license, as published in the price list at the time of purchase. Be sure this matches the information stored in your billing system during reconciliation. | *6.82* |
| Quantity | Number of licenses. Be sure this matches the information stored in your billing system during reconciliation. | *2* |
| Amount | Total of price for quantity. Used to check if the amount calculation matches how you calculate this value for your customers. | *13.32* |
| TotalOtherDiscount | Amount of discount applied to these charges. Product licenses included with a competency or MAPS, or new subscriptions eligible for an incentive, will also contain a discount amount in this column. | *2.32* |
| Subtotal | Total before tax. Checks if your subtotal matches your expected total, in case of a discount. | *11* |
| Tax | Tax amount charge. Based on your market's tax rules and specific circumstances. | *0* |
| TotalForCustomer | Total after tax. Checks if you are charged tax in the invoice. | *11* |
| Currency | Currency type. Each billing entity has only one currency. Check if it matches your first invoice. Check again after any major billing platform updates. | *EUR* |
| DomainName | Customer's domain name. This field may appear blank until the second billing cycle. *Don't use this field as a unique identifier for the customer. The customer/partner can update the vanity or default domain through the  Office 365 portal.* | *example.onmicrosoft.com* |
| SubscriptionName | Subscription nickname. If no nickname is specified, Partner Center uses the **OfferName**. | *PROJECT ONLINE* |
| SubscriptionDescription | The name of the service offering purchased by the customer, as defined in the price list. (This is an identical field to **OfferName**.) | *PROJECT ONLINE PREMIUM WITHOUT PROJECT CLIENT* |
| BillingCycleType | One-time billing frequency.| *Monthly* |
