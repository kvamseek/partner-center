---
title: Recon file fields for CSP new commerce invoice
ms.topic: conceptual
ms.date: 01/18/2022
description: Learn about all of the items on your new commerce reconciliation file in Partner Center.
ms.service: partner-dashboard
ms.subservice: partnercenter-billing
author: sodeb
ms.author: sodeb
---

# Learn how to read new commerce invoice reconciliation files in Partner Center

**Appropriate roles**: Account admin | Billing agent

## Using the recon file

In the table below, you can read about the fields in the reconciliation file for new commerce purchases and see examples of what they might contain.

For more information on reconciliation files, see [Use the reconciliation files](use-the-reconciliation-files.md).

| Column | Description | Sample value |
| ------ | ----------- | ------------ |
| PartnerId | CSP partner identifier. | *0e195b37-4574-4539-bc42-0e539b9684c0* |
| CustomerId | Customer identifier. | *196e2273-9651-43a3-ba7e-7cbcd918fc40* |
| CustomerName | Customer’s organization. | *Johnny Modern Cust DE2* |
| CustomerDomainName | Customer's domain name. | *testcustomerdomain.onmicrosoft.com* |
| CustomerCountry | Customer’s location. See the full [list of countries/regions](./regional-authorization-overview.md) for your region.  | *DE* |
| InvoiceNumber | Invoice Number.  | *G002297372* |
| MPNID | Microsoft partner identifier. | *6034453* |
| ResellerMPNID | Reseller on record. | *6048879* |
| OrderId | Internal order identifier. When contacting support, the order number may be helpful. | *0ET2qaZvJGfF9wgSKnWzR5JLmhp10lOc1, 6dc5c039750a* |
| OrderDate | UTC date of the transaction. | *10/3/2020* |
| ProductId | Product identifier. | *DZH318Z0BNZ5* |
| SkuId | SKU identifier. | *006G* |
| AvailabilityId | Availability identifier. | *DZH318Z08B80* |
| SkuName | SKU name. | *Tables - LRS* |
| ProductName | Product name. | *Tables* |
| ChargeType | The [type of charge](./recon-file-charge-types.md) or adjustment. | *New* |
| UnitPrice | Price per unit or license, as listed in the price list in supported currencies for applicable countries/regions. | *0.045* |
| Quantity | Purchased units. | *1* |
| Subtotal | Pre-tax cost. See details below: <br>**Usage-based:** *ROUNDDOWN(ROUNDDOWN(EffectiveUnitPrice \* BillableQuantity,2) \* PCToBCExchangeRate, 2)* <br>**License or seat-based:** *ROUNDDOWN(EffectiveUnitPrice \* PCToBCExchangeRate,2) \* BillableQuantity* | 0.01         |
| TaxTotal | Tax amount. Based on your market's tax rules and specific circumstances. | *0* |
| Total | Total cost. Equal to the subtotal plus the tax amount. | *0.045* |
| Currency | Billing currency. Your bill is generated in the context of the partner's billing currency. | *EUR* |
| PriceAdjustmentDescription | Unit price adjustment reason. The value is text-based information that can be rearranged or presented in different formats while keeping the same meaning. | *["15.0% Partner earned credit for services managed"]* |
| PublisherName | Product publisher.  | *Microsoft* |
| PublisherId | Publisher identifier. | *NA* |
| SubscriptionDescription | Service offering name, as defined in the price list. | *Azure plan* |
| SubscriptionId | Subscription identifier. This identifier isn't the same as the Subscription ID on the partner admin console. | *307628f1-d9d2-f09c-ea1f-4183f0cae308* |
| ChargeStartDate | Billing start date. | *9/1/2020* |
| ChargeEndDate | Billing end date. Determined by the charge cycle, billing plan, and coterminosity. For more information, see [How are one-time and recurring charges calculated](./common-billing-scenarios-onetime-recurring.md#how-are-one-time-and-recurring-charges-calculated).| *9/30/2020* |
| TermAndBillingCycle | Subscription term. For more information, see [How do I find the billing term in a reconciliation file?](./common-billing-scenarios-onetime-recurring.md#how-do-i-find-the-billing-term-in-a-reconciliation-file). | *Data Stored (GB/Month), One-Year commitment for monthly/yearly billing* |
| EffectiveUnitPrice | Prorated/discounted unit price. Unit price may change due to discounts, adjustments, billable days or other factors. For more information, see [Effective Unit Price Calculation](./azure-plan-billing.md).  | *0.03825* |
| UnitType | Charging unit type. | *1 GB/Month* |
| AlternateId | Alternate order ID. | *6dc5c039750a* |
| BillableQuantity | Number of licenses or usage hours.  | *0.005001* |
| BillingFrequency | Billing plan. <br> *For one-time payments and unbilled transactions, the billing frequency is left blank.* | *Monthly, Annual*  |
| PricingCurrency | Pricing currency. If the product is sold in multiple currencies, the customer’s local currency will be used. | *USD* |
| PCToBCExchangeRate | Exchange rate applied for pricing currency to billing currency. | *0.846202666* |
| PCToBCExchangeRateDate | Exchange rate calculation date. | *9/30/2020* |
| MeterDescription | Meter description.  | *Tables - LRS Data Stored (GB/Month)* |
| ReservationOrderId | Azure reservation Order ID or Azure Savings plan Order ID. See “Note” for mapping daily charges to monthly costs. | *55eebd03-c6e7-4593-8ba8-0bb7c0b25e02* |
| CreditReasonCode | Azure credit reason (not applicable to refunds). | *Azure Credit Offer* |
| SubscriptionStartDate | Date of purchase or renewal of a subscription. | *5/1/2021* |
| SubscriptionEndDate | Date when the subscription will expire. | *4/30/2022* |
| ReferenceID | Concurrent transactions identifier. | *025d68a6-1bd6-42ab-9636-15e8d776a30e* |
| ProductQualifiers | Purchase type identifier (add-on, a trial, or both). | *["Add-on"]* |
| PromotionID | Promotion identifier. | *CFQ7TTC0LDPB:1:CFQ7TTC0GZQJ* |


## Next steps

- [Billing and taxes](billing.md)
