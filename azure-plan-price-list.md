---
title: Azure plan price list for CSP partners
ms.topic: how-to
ms.service: partner-dashboard
ms.subservice: partnercenter-pricing
description: Learn how CSP program partners can use Partner Center to see the price list for subscriptions under the Azure plan.
author: denysseD
ms.author: DenysseDiaz
ms.date: 06/05/2023
---

# Price list for the new commerce experience in CSP for Azure

**Appropriate roles**: Admin agent | Billing admin | Global admin | Helpdesk agent | Sales agent | User management admin

The real-time prices for the new Azure commerce experience in CSP are dynamically delivered in real time in Partner Center.

> [!NOTE]
> Prices are shown in USD only.

Partners are billed in the partner-location currency regardless of the location of the customer to whom they sold the products. For more information, see [Azure plan - billing](azure-plan-billing.md).

As part of the new commerce experience for Azure in CSP, we've introduced a [new Azure offer](./azure-plan-lp.md). For important dates related to the previous Azure offer (MS-AZR-0145p), refer to the [offer document](https://go.microsoft.com/fwlink/p/?linkid=2164140).

If you enrolled *before* July 21, 2021:

- You'll continue to see the previous Azure offer in the price list.

If you enrolled *on or after* July 21, 2021:

- You *won't* see the previous Azure offer in the price list.

> [!IMPORTANT]
> If a customer has not been transitioned to an Azure plan (such as Modern Azure, 17G offer), then the price list to be used for Azure reservations is the one highlighted in the red box (see the following image).
>
> Azure reserved instances (RIs) purchased via legacy Azure are priced in the customer's local currency (local currencies are visible in the price list) and billed in partner's local currency. Azure RI purchases are always found on Modern "G" invoices.
>
> If a customer is using an Azure plan, then the price list to be used for Azure reservations is the one highlighted in the green box (see the following image).
>
> Azure RIs purchased via Azure plan are priced in USD and billed in partner's local currency. Azure RI purchases are always found on Modern "G" invoices.
>
> :::image type="content" source="media/software-pricing/azure-RI-pricelist.png" lightbox="media/software-pricing/azure-RI-pricelist.png" alt-text="Screenshot of Azure pricelist option on the Price lists page in Partner Center.":::

## See pricing for subscriptions under the Azure plan pricing

To get Azure plan subscription pricing, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Pricing**.

2. For new commerce Azure pricing, under **Azure plan consumption pricing** and **Azure plan reservations pricing**, select the country/region, then the download link.

   - For **Foreign exchange rates**, select the download link under the section.

   > [!NOTE]
   > FX rates are not country/region-specific.

   > [!NOTE]
   > You can export two different price lists: Azure plan pricing and Marketplace third-party pricing.

## Azure price list specifics

- Azure plan pricing is available from the **Pricing** workspace in Partner Center.

- Exports are available for:
  - New commerce Azure plan consumption
  - New commerce Azure reservations
  - Azure reserved instances

  Foreign exchange rates to apply to Azure pricing if needed

- Options for export include:

  - **Current pricing**: This option includes all meters and pricing from the first of the month to the current date of the month, such as new prices, changed prices, or removed prices. All prices  have effective start and end dates to explain whether they're new or removed.

  - **Previous month's pricing**: Downloads of each type of resource are by month. For pricing files, the download includes all meters that were available during that month. If a new meter appeared in the middle of the month, it appears as a meter with an effective date reflecting its availability. Downloads are similar for prices that are no longer supported, appearing with an effective end date describing when they're no longer available.

  - **FX Rates**: FX rates are available for download and are updated daily.

- Prices in the price lists are direct prices. Some partners might be eligible for partner earned credits. For information about how partner earned credit is calculated, see [How the partner earned credit is calculated and paid](partner-earned-credit-explanation.md).

- **Eligible services**: Partner earned credit is applicable to services listed in the **Azure plan consumption pricing** that partners can export from the [Azure plan pricing](https://partner.microsoft.com/dashboard/pricing/pricelist) page.
   > [!NOTE]
   > There are exceptions, including, but not limited to, third-party products identified as "Third Party" in the **Tags** column of the Azure plan consumption price list and Azure plan reservations.

## Price list data

|**Field**   |**Description**   |
|:--------------------------|:---------------------------|
|ProductTitle  |Title or  name of the product|
|ProductID   |ID of the product|
|SKuId|ID of SKU|
|SkuTitle|Title or name of SKU|
|Publisher|Microsoft by default, as a first-party seller or when reselling third-party products with ThirdParty tag present|
|SkuDescription|Description of the SKU|
|UnitOfMeasure|The units that will be charged or billed|
|TermDuration|For term-based products, the length of the term, applicable to reservations|
|Market|Market of the pricing|
|Currency|Currency of the pricing|
|UnitPrice|Price per unit|
|PricingTierRangeMin|For tiered pricing, the minimum price applies|
|PricingTierRangeMax|For tiered pricing, the maximum price applies|
|EffectiveStartDate|Start date of pricing|
|EffectiveEndDate|End date of the pricing|
|MeterIds|Meter ID of the product SKU|
|MeterType|Type of meter|
|Tags|Properties for the item. For Azure plan pricing, possible values are Azure, Consumption, Reservation and ThirdParty.|

Price lists for Azure plan can be exported from the [Pricing and offers page](https://partner.microsoft.com/dashboard/sell/pricingandoffers) in Partner Center.

## Tiered pricing

Some Azure plan consumption services support tiered pricing.

Partners can find these products and SKUs in the Azure plan price list.

Items that have values in the pricing tier range columns enable partners to understand the price based on usage.

In the following example, using sample data, we have one product SKU with three pricing tiers.

|**ProductId**   |**SkuId**   |**UnitPrice**   |**PricingTierRangeMin**   |**PricingTierRangeMax**   |
|:---------------|:-----------|:---------------|:-------------------------|:-------------------------|
|DDD123456ABC|01AB|0.50|100001|9223372036854780000|
|DDD123456ABC|01AB|0.80|101|100000|
|DDD123456ABC|01AB|1|1|100|

In the preceding example, if 101 units are used, the charge would be 100.80. The first 100 units are one each and the next unit is charged at 0.80.

## Pricing API for Azure plan

You can use the [pricing API](/partner/develop/pricing) to retrieve Azure plan pricing for consumption and reservations programmatically. You can also retrieve foreign exchange (FX) rates.

The pricing API is on a different endpoint than the other Partner Center APIs. The pricing information includes meter pricing in USD for Azure plan resources and reservations pricing applied to Azure plan subscriptions.

The pricing API also enables partners to retrieve monthly exchange rates because Azure plan pricing is in USD only. You can use the APIs to retrieve both pricing and foreign exchange rates for the current month or previous months.

> [!NOTE]
> The pricing API is specific to Azure plan pricing. You should still use the existing RateCard API and price lists posted to the Partner Center **Pricing and offers** page for Azure resources or reservations deployed to non-Azure plan subscriptions. The Azure plan pricing API doesn't support software, marketplace, or license-based pricing, such as Microsoft 365 or Dynamics 365.

For more information about Azure plan pricing and foreign exchange rate APIs, see the full [pricing API documentation](/partner/develop/pricing).

## Next steps

- [Manage subscriptions and resources under the Azure plan](azure-plan-manage.md)
