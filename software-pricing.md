---
title: Partner software pricing
description: The Partner Center software price list combines all price lists into one downloadable file and is available using the API.
author: denysseD
ms.author: DenysseDiaz
ms.service: partner-dashboard
ms.subservice: partnercenter-pricing
ms.topic: conceptual
ms.date: 11/04/2022
---
# Software pricing

**Appropriate roles**: Global admin | User management admin | Admin agent | MPN Partner Admin | Sales agent | Billing admin

To find the latest Cloud Solution Provider (CSP) software pricing, from the Partner Center dashboard, go to the Pricing workspace. Software subscription pricing 
includes term-based software subscriptions for all supported currencies and provides the unit price and estimated retail price (ERP). Software pricing is updated on 
the first day of every month. 

## Software price list example

The software price list contains the following data, which varies slightly between perpetual and subscription products. 

| Field                | Example                                                                                                                                                                                                                                                                                    | Description                                                            |
|----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| ProductTitle         | Windows Rights Management Services CAL 2022                                                                                                                                                                                                                                                | Title of the product                                                   |
| ProductId            | DG7GMGF0D5SL                                                                                                                                                                                                                                                                               | Identifier of the product                                                      |
| SkuId                | 7                                                                                                                                                                                                                                                                                          | Identifier of the SKU                                                          |
| SkuTitle             | Rights Management Services (RMS) 2022 CAL-1 Device                                                                                                                                                                                                                                         | Title of the SKU                                                       |
| Publisher            | Microsoft                                                                                                                                                                                                                                                                                  | Company publishing the offer                                           |
| SkuDescription       | A Rights Management Services Client Access License (CAL) and a Windows Server Client Access License (CAL) is required for each user or device that accesses the Rights Management Services software. You'll need a user or device CAL for each user or device that accesses the software.  | Product short description                                              |
| UnitOfMeasure        |                                                                                                                                                                                                                                                                                            | Only applicable for Azure consumption services                                   |
| TermDuration         | OneTime, P1Y, P1M                                                                                                                                                                                                                                                                                            | Length of the term                                                     |
| BillingPlan          | Blank, Annual                                                                                                                                                                                                                                                                                   | How frequently billing occurs                                              |
| Market               | US                                                                                                                                                                                                                                                                                         | Country/region for the item                                                    |
| Currency             | USD                                                                                                                                                                                                                                                                                        | Currency for the item - note: EU/EFTA and UK markets will have pricing in 6 currencies                                                  |
| UnitPrice            |                                                                                                                                                                                                                                                                                            | Price per unit                                                         |
| PricingTierRangeMin  |                                                                                                                                                                                                                                                                                            | If tiered pricing is supported, the minimum range for the price point  |
| PricingTierRangeMax  |                                                                                                                                                                                                                                                                                            | If tiered pricing is supported, the maximum range for the price point  |
| EffectiveStartDate   | (2021-10-01T00:00:00.0000000Z)                                                                                                                                                                                                                                     | Start date for the item's price point                                  |
| EffectiveEndDate     | (9999-11-30T23:59:59.0000000Z)                                                                                                                                                                                                                                                                           | End date for the item's price point. Note: Always refer to the latest EffectiveEndDate to identify the month's active price|
| Tags                 | Software;Perpetual                                                                                                                                                                                                                                                                         | Miscellaneous tags                                                     |
| ERP Price            |                                                                                                                                                                                                                                                                                            | Estimated retail price                                                 |
| Segment              | Commercial, Education, Charity                                                                                                                                                                                                                                                             | Segment                                                                |

## Next steps

- For more information about getting a software price list using the API, see  [Get a price sheet](/partner/develop/get-a-price-sheet).
