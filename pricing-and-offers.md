---
title: Pricing and offers
ms.topic: overview
ms.date: 10/18/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-pricing
description: See current price lists for license-based services like Office 365, Microsoft Dynamics CRM, and Enterprise Mobility Suite, and usage-based services like Azure.
author: denysseD
ms.author: DenysseDiaz
---

# Pricing and offers for Office 365, Dynamics CRM, Enterprise Mobility Suite, Azure, and more

**Appropriate roles**: Global admin | User management admin | Admin agent | MPN Partner Admin | Sales agent | Billing admin

To see the latest Cloud Solution Provider (CSP) programs and offers, from the [Partner Center](https://partner.microsoft.com/dashboard/home), go to the [**Pricing** workspace](https://partner.microsoft.com/dashboard/pricing/pricelist).

There you'll find separate price lists for the different types of generally available products and services. Products or services in private preview, used for testing purposes, or available through other sales channels, are not included in CSP price lists. Below you will find an introduction to the categories of pricing for Cloud Solution Provider partners and their update frequency:

- **License-based services** includes pricing information for Office 365, Enterprise Mobility, and Security E3, and Dynamics 365. License-based pricing section includes current and preview pricing and the offer list matrix. Price lists include list price and estimated retail prices (ERP) for offers in all supported currencies. The offer list matrix includes market availability and other important information about the offers. These files are updated on the first day of every month.

   > [!NOTE]
   > List and ERP prices are for monthly billing frequency. For annual billing frequency, multiply the monthly price by 12.

- **Usage-based services** includes pricing information for Microsoft Azure and Visual Studio. You can also use the [Azure Services in CSP Pricing Calculator](https://azure.microsoft.com/pricing/calculator/). The usage-based download includes both the CSP price lists for all supported currencies and the Shared Services pricing files in ERP. These files are updated on the first day of every month.
- **Microsoft Azure Reserved Instances** includes pricing information for all supported currencies for Azure Reserved Instances. The pricing download also includes the Shared Services pricing in ERP. These files are updated on the first day of every month.
- **Software subscriptions** includes pricing for term-based software subscriptions for all supported currencies. The price file includes all supported currencies with list price and estimated retail prices (ERP). These files are updated on the first day of every month.
- **Azure plan pricing** includes pricing information for Azure plan consumption services and Azure plan reservation pricing. Prices are direct prices or ERP and can be retrieved for any given supported market. The data in these files is refreshed every day.
- **Foreign exchange rates** are used to calculate billing charged between USD and the partners local currency for Azure products. The rates are updated daily.
- **Marketplace** includes pricing for independent software vendor (ISV) solutions from Microsoft's commercial marketplace. Prices are retrieved per market. The data in these files is refreshed every day.

> [!NOTE]
> Only CSP partners with the capability to transact can view and download price lists. Indirect resellers should [contact their CSP provider]( https://partner.microsoft.com/cloud-solution-provider/find-a-provider) to request details about pricing

## Price list preview and change frequency

License-based services include a price list preview, provided 30 days in advance of any changes. To see the price list preview, go to **Sell > Pricing and offers**. EndOfSale offers will not be present in current month's price list. There's no price preview for usage-based services since these services are dynamic. The following table explains how to read the price list table.

|**Item**        |**Definition**      |
|:-----------   |:-----------   |
|ADD   |A new item to the price list|
|CHG   |Changes in list price from month to month. Other changes not related to list price may occur, partners should compare price lists between months to determine changes to other properties.|
|DEL   |An item removed from the price list|
|UNC   |List price unchanged from the previous month's price list  |
|DEPR   |Offer is no longer purchasable in legacy commerce. Partner must purchase the new commerce equivalent. More information can be found in the [migration to new commerce topic](migrate-subscriptions-to-new-commerce.md#new-commerce-migration). |
|Effective Start Date   |The day and time a change to product metadata becomes valid    |
|Effective End Date   |The day and time a change to product metadata ceases to be valid   |
|Offer display name   |The customer facing name for the offer   |
|Offer ID   |The internal identifier for the offer   |
|License agreement type   |License agreement types can be either corporate, government, or academic. The agreement type determines which customer types the offer can be sold to.|
|Purchase unit   |The duration of offer being purchased. Purchase units are typically one month.   |
|Secondary license type   |Secondary license types will be either non-specific, add-on, or trial. Add-on indicates that there are prerequisite products the customer must purchase before purchasing the add-on.|
|End customer type   |Relates back to license agreement type: corporate license - cloud reseller corporate, government license - cloud reseller government, or academic license - cloud reseller faculty or cloud reseller student   |
|List price   |The price the partner will pay   |
|ERP price   |The estimated or recommended retail price to the customer   |

## Price changes

Price changes are a common occurrence. Partners can anticipate price changes for license-based offers by looking at the price list preview. On the Partner Center, select the **Pricing** workspace to see the price list preview.

However, Azure usage-based pricing has no preview. Partners can keep up with Azure consumption price changes by using the RateCard API, which returns that day's meter pricing.

|**Type of product**   |**Product examples**  |**Preview available** |**Change details**|
|-----------------------|:-----------------------|:-------------------|------------------|
|License-based|Office, Dynamics, Intune, Windows Enterprise|30-day|List price changes marked CHNG in preview price lists|
|Usage-based|Azure resources|Not available|Change log available in previous month's price list's **Change History** tab|
|Software||Not available|Compare price lists manually from month to month|
|Reservations|Virtual machines, pre-paid|Not available|Compare price lists manually from month to month|

Usage-based prices can change throughout a month. To get 'current' daily pricing for these Azure resources, partners need to call the RateCard API.

> [!NOTE]
> Subscription price changes apply only during a renewal. A partner's monthly charge is determined at the price of purchase, or the price at the time of creating a subscription. If a price increases or decrease after the annual term is acquired, the partner is not charged the changed price until the renewal, which is typically at the 12-month term.

## Pricing and special segments

CSP offers some services to special market segments, for example, education, non-profit and government community cloud. Not all services are available in every channel. No segment defaults to what we call the commercial segment. All license-based pricing is available in the license-based price list on the **Price lists** page. Azure Government pricing is available in the usage-based price list when signed into the Azure Government enabled CSP tenant. Software subscriptions don't yet support these special segments.

|**Segment**   |**who needs to qualify**   |**Partner qualifies customer**|**Enabled product types**|
|-------------------|-----------------------|----------------------------|-----------------------------|
|Education|Customer|No, customer qualification will be performed by Microsoft |License-based only|
|Non-profit|Customer|No, customer qualifies outside of Partner Center|License-based only|
|Government Community Cloud (GCC)|Partner and customer|Once GCC enabled, partner can create GCC customers| License-based only|
|Azure Government|Partner|Once qualified, partner operates in a CSP tenant specific to Azure Government|Azure resources|

Partner margins, the difference between the list price and the estimated retail prices, may vary from segment to segment. Typically, education and non-profit tend to have lower or no margins for CSP partners. Refer to the license-based price list for exact values.

## Add-on offer types

License-based services can be acquired as either base offers or add-ons. Only base offers are discoverable and purchasable via the Partner Center catalog. Partners need to apply add-ons only after purchasing the base offers. The license-based price list **Secondary license type** column includes information about each offer and its type. Base offers have **Non-specific** values in the price list secondary license type column and can be purchased in the catalog. Secondary license type values of **add-on** can't be purchased in the catalog. To purchase these add-ons:

1. Consult the offer list matrix to see the list of offer IDs that need to be purchased before you can purchase an add-on.
2. Purchase the base offer from the catalog
3. Navigate to your customer from the customer list. Select the subscription for the base offer you just purchased. On the manage subscription page, you'll see available add-ons that can be applied to the base offer.

> [!NOTE]
> Some base offers have **Unit type** values of **Add-on licenses**. For a base offer this simply means that you do not assign user licenses after purchasing. If the offer can be purchased in the catalog it is a **Base offer** regardless of the unit type in the user interface.

Add-ons are listed regardless of their segment. So a commercial Add-on could include education base offers. Or education base offers could include commercial base offers. This is by design. Partners should always use the prerequisite lists to understand that at least one of the prerequisites must exist before acquiring the add-on.

## Pricing between Azure and non-Azure

Pricing differs across different types of offers. License-based pricing is typically the amount per license for a given month. Usage-based pricing is determined by use of a given resource, with an associated meter ID. Partners aren't charged for acquiring the Azure subscription. However, partners are charged for resources consumed by different deployments under the Azure subscription. Pricing in the usage-based price list is organized around different resource meter IDs in Azure.

Azure reservations are term-based purchases for the particular resource type - Virtual Machines. Purchasing an Azure reservation enables a partner to pre-pay (one- or three-year terms) and reserve a given virtual machine. Reservations save the partner money and ensuring their virtual machine is always available for the duration of the term. A partner can align the reservation they want against the usage-based resource meter IDs. The meter IDs are consistent across the resource, whether the partner is purchasing a virtual machine or simply deploying the virtual machine as a usage-based resource.

## European regional prices

Partners transact in [regions](regional-authorization-overview.md) that are assigned when they're on-boarded. The European region is unique since this region supports more than one currency. Partners request pricing based on the customer's market but will be billed in their currency, which may be different than the customer market currency. In these cases, a partner will get pricing in all supported currencies for the customer market they request pricing information for.  All European market price lists will include pricing in all supported currencies in the European region. Partners will be billed based on the market price sheet and currency line item aligning with the partner billing currency.

The multi-currency support enables a key scenario which had been blocked for years in traditional license-based and software pricing, enabling a partner to purchase a product SKU for a customer in a different country/region when the product SKU isn't available in the partner's country/region. This scenario is now enabled and no longer blocked in new commerce. Products now available in this scenario include some of the calling plans only available in specific EU markets. Other examples include Business Voice product SKUs, only available in GB, but can now be purchased by non-GB EU partners for GB customers.

### Important details about the European regional price lists

Partners may see some variant prices for markets with different currencies than their own. This is due to some system limitations that will be addressed going forward.  

Slight price differences in same currencies across different markets:

Example:

- Product in UK GBP: 30.25
- Product for DE in GBP: 30.23

Slight price differences for the same term but with different billing frequencies:

- Product in UK GBP annual term with annual billing: 3393.9
- Product in UK GBP annual term with monthly billing: 3393.96

In both of these cases, partners can always rely on being billed the amount reflected in the price list for the customer market and partner billing currency.

## Offers matrix

On the Pricing and offers page, view the Cloud Reseller Offer Matrix, to read about the different SKUs and product bundles available to you to sell. The offers matrix includes which offers are available per locale. If an item is listed on the price list but not on the offer matrix, it means that the products can't be ordered yet. As soon as they're available to order, the offers matrix is updated.

Microsoft also publishes a list of the Azure Services in CSP on the Pricing and offers page.

### Offers matrix and price list questions

If you have questions about the price list or offer matrix, submit a service request through Partner Center.

## Offer limits

Some license-based offers have certain rules and limitations that prohibit multiple purchases for the same customer. These rules apply to most trials and many of the small business offers. **Small business offers** are defined by those offers that have a maximum license count that is less than 300.

These purchasing constraints are defined as part of the offer configuration and can be found by looking in the offer list matrix. Two columns of data work together to define the enforcement: 1. Offer Limit Scope and 2. Offer Limit. The constraints are enforced during a purchase. The catalog in Partner Center will disallow a partner from purchasing more offers than the rules allow. Any attempt to violate the constraints will result in an error.

Offer limit scope is recorded as a column on the offer list matrix and can have values of None, Lifetime or Concurrent.

- Offers with **None** can be purchased without constraints
- **Lifetime** offers can be purchased only once
- **Concurrent** offers can be purchased as many times as is allowed by the **Offer Limit** value for that offer. Most trials have a Lifetime Offer Limit Scope with an Offer Limit of "1". Most small business offers have a Concurrent Offer Limit Scope with an Offer Limit of "2".

> [!IMPORTANT]
> Concurrency limits are enforced even if an offer is canceled. An offer must be completely canceled and then deprovisioned in order to free up an additional space allowing for another purchase.

### Taxes and pricing

All pricing in Partner Center CSP price lists is tax-exclusive. For more information in the Partner Center document [Taxes and tax exemptions](tax-and-tax-exemptions.md).

## Offer attestation

Some offers require the partner to agree before buying. This process is called attestation, and the only offers requiring attestation are Windows 365 Business offers with Windows Hybrid Benefit. Partners will see text on the review screen when purchasing these offers that says, "I understand that each person using Windows 365 Business with Windows Hybrid Benefit also needs to have a valid copy of Windows 10/11 Pro installed on their primary work device." Partners must agree to this before purchasing.

Attestation applies both to the Partner Center and the Partner Center APIs when submitting orders and checking out carts. Partners can determine which offers require attestation by checking the AttestationProperties on the [offer](/partner-center/develop/offer-resources#attestationproperties) or [SKU](/partner-center/develop/product-resources#attestationproperties) objects.

These properties will explain the attestation type and if the attestation is enforced for purchases (enforceAttestation=True). If required, partners simply set the `AttestationAccepted` to **true** on the cart or order [lineitems](/partner-center/develop/cart-resources).

The following offers currently require attestation prior to purchasing

 | **Offer name** |**Offer ID** |
|:------------------------------------------- |:--------------------------------------- |
| Windows 365 Business 1 vCPU, 2 GB, 64 GB (with Windows Hybrid Benefit) | 5f3a7cd2-c76f-4b21-9ddc-f48f09869cf6 |
| Windows 365 Business 2 vCPU, 4 GB, 128 GB (with Windows Hybrid Benefit) | 7612386a-d98d-4110-94b8-554bd612a5ab |
| Windows 365 Business 2 vCPU, 4 GB, 128 GB (with Windows Hybrid Benefit) Trial | ab170880-1254-4534-abb9-fd0bf60cde71 |
| Windows 365 Business 2 vCPU, 4 GB, 256 GB (with Windows Hybrid Benefit) | cc624387-162c-4f31-9d6e-252d39d5324b |
| Windows 365 Business 2 vCPU, 4 GB, 64 GB (with Windows Hybrid Benefit) | f9777f60-19ae-4bd2-b881-6dc674564a2e |
| Windows 365 Business 2 vCPU, 8 GB, 128 GB (with Windows Hybrid Benefit) | 39daa752-18b7-4918-b4eb-cf27cf617ee2 |
| Windows 365 Business 2 vCPU, 8 GB, 128 GB (with Windows Hybrid Benefit) Trial | d5623401-b8e0-429f-86df-29b6efdf4d95 |
| Windows 365 Business 2 vCPU, 8 GB, 256 GB (with Windows Hybrid Benefit) | 8fe4271f-c761-45f8-8261-5ab575195152 |
| Windows 365 Business 4 vCPU, 16 GB, 128 GB (with Windows Hybrid Benefit) | 037cff0f-c231-4cce-a7ef-5324c755ba9a |
| Windows 365 Business 4 vCPU, 16 GB, 128 GB (with Windows Hybrid Benefit) Trial | 46448c4c-8b12-4ea1-9be7-76b35d69bcf5 |
| Windows 365 Business 4 vCPU, 16 GB, 256 GB (with Windows Hybrid Benefit) | 977318cf-57a5-4c3f-a8b6-aa58853dd2e9 |
| Windows 365 Business 4 vCPU, 16 GB, 512 GB (with Windows Hybrid Benefit) | 1a3bdfb8-fb09-4331-8303-2c07e895c6d9 |
| Windows 365 Business 8 vCPU, 32 GB, 128 GB (with Windows Hybrid Benefit) | 1b96db48-9c02-4c95-8c0b-98e4e6aa187c |
| Windows 365 Business 8 vCPU, 32 GB, 256 GB (with Windows Hybrid Benefit) | 3ff72e53-c37f-41d5-b932-793cb39c837b |
| Windows 365 Business 8 vCPU, 32 GB, 512 GB (with Windows Hybrid Benefit) | aca639ae-ae81-4298-a76a-094b6880913b |

## Multi-year term offers

### 36 month offers

There are approximately 50 Dynamics offers that have three-year terms. These are identified by **(36 mo)** in the title of the offers. These offers are similar to the yearly term offers. The only difference is their term. These offers have a three-year term so, the subscriptions renew automatically after three years instead of one.

Here's a summary of how these offers work:

- Terms are 36 months, and subscriptions renew automatically after three years.
- Partners can cancel or change the number of licenses throughout the term of the subscription.
- Annual renewal is at the price of purchase time for the three-year term.
- Billing frequency is still yearly or monthly.

### 72 month offers

Microsoft 365 A1 base offer has a six-year term.  The Office 365 A1 add-ons are available after purchasing this base offer.

|**Offer name**   |**Offer ID**   |**Type**|
|-------------------|-----------------------|----------------------------|
|Microsoft 365 A1|778a4dce-0014-4d53-8647-314ef2b091d2|Base offer|
|Office 365 A1 for faculty (for Device)|0757d14e-7c57-456f-8dab-47d164f2ff1f|Add-on|
|Office 365 A1 for students (for Device)|bae285a9-d56b-4384-b02f-38adc61a6f12|Add-on|

Here's a summary of how these offers work:

- The term is 72 months (six years).
- As subscription isn't renewed and expires after six years.
- Billing frequency on the offer shows as annual, but the partner is billed up-front on their first invoice after acquiring the subscription.
- Subscriptions for A1 72-month offers are locked after purchase and can't be canceled. 
-    License counts can be added to the subscription after initial purchase.
- This subscription is non-cancelable and non-refundable.

## Estimated retail price (ERP)

Most price lists include a list price, the price the partner is billed, and the estimated retail price. Estimated retail price (ERP) is also called Microsoft suggested retail price or MSRP. These two values, ERP and MSRP, represent the estimated market value of the products if a customer were to purchase the products directly from Microsoft.

Here's where to find ERP/MSRP details for each type of product or service:

|**Product or Service**        |**ERP and MSRP price list details**      |
|:-----------   |:-----------   |
|Product or Service  |ERP and MSRP price list details  |
|License-based services  |Listed as ERP in the license-based price lists  |
|Azure usage-based services  |Can be found in the Shared Services equivalent price lists  |
|Azure reservations  |Can be found in the Shared Services equivalent price lists  |
|Azure plan usage based  |Prices are retail, non-discounted in price sheets  |
|Azure plan reservations  |Reference Azure reservations shared services price lists  |
|Software subscriptions  |Listed as ERP in software subscriptions price lists  |
|Marketplace  |Listed as ERP in Marketplace price lists  |

## New commerce license-based pricing

> [!NOTE]
> The new commerce experiences for license-based services include many new capabilities and are available to all Cloud Solution Providers (CSPs). For more information, see [new commerce experiences overview](new-commerce-license-based.md).

Pricing strategy in new commerce Microsoft 365/Dynamics 365 remains the same between traditional and new commerce. In principle, this means each currency will have one price and monthly plan charges for a term will remain constant through the remainder of the term. Partners will continue to be billed in their country/region currency.

### How to access price lists and why

New commerce license-based price lists requests are **by market country/region**.  For example, if a partner wants to get pricing for products sold to a German (DE) customer, they would ask for the German (DE) price list. For European countries/regions (and ONLY for European countries/regions), these market-based price list files include pricing in all six supported European currencies (SEK, NOK, CHF, DKK, GBP, EUR). This is to enable the partner to understand how much they'll be billed in their currency regardless of the customer market. If a partner in Great Britain (GB), for example, wants to purchase a product SKU for a customer in Germany, they would get the DE price sheet and need only the Great Britain Pounds (GBP) pricing because the GBP price point is what the partner will be billed. Supporting pricing by market aligns the product availability to the pricing, enabling partners to get pricing for markets even when the product may not be available to customers their own country/region. This design also can support future scenarios if different markets with the same currency need different pricing.

Pricing data is available to partners both from the Partner Center [dashboard](https://partner.microsoft.com/dashboard/home) and through the pricing sheet API. Partners download the price list by navigating to the **Price lists** page. The new commerce offer price list and offer matrix will be labeled with **New Commerce**.

Price lists include basic information about pricing (how much it costs). The offer matrix includes purchase information about the products (how to buy it). Much of the information included in these download files is also accessible through the various Partner Center APIs (catalog APIs and price sheet APIs). Price lists require the partner to select the market for the pricing they request while the Offer-list matrix is agnostic of market.

Price list and offer-list matrix files default to the current month. To retrieve the previous month's price list, select the month and then download the pricing file for the desired market. Price changes should occur only on a monthly cadence. Partners can use the price list preview to know of price changes coming in the next month. Price changes mid-month rarely occur, usually to correct an error in the data. Any mid-month price changes will be broadly announced and be reflected in the price sheet with a new EffectiveStartDate.

### Market specific discounts

Some markets include geo-specific discounts on top of the CSP margin discounts. Partners may discover pricing for select product SKUs having deeper discounts in some markets depending on the product SKU. Markets they may include a deeper discount are the United Kingdom, India, Australia or Canada. These discounts are very targeted and only impact a very small number of product SKUs. One example:

- Product SKU name: Teams Phone with Calling Plan
- ProductId: CFQ7TTC0HL73
- SkuId: 0001

In this case the CSP price may be discounted in the GB market, so other EU markets will likely see a higher CSP price point, reflect as unit price in the price lists. This is by design for this particular product SKU.

### New commerce pricing versus traditional license-based pricing

There should be general consistency between tradition and new commerce pricing for most product SKUs. However, partners may notice slight differences when comparing legacy traditional license-based pricing to new commerce pricing.

### New commerce terms and billing frequencies

Partners will be billed in their currency based on the currency value in the price list. This billing charge will remain constant for a billing plan that is shorter than the term. Annual term (P1Y) prices reflect the 12 months, partners divide the total by 12 to get the monthly plan charge.

The new commerce price list has three fields that work together to help the partner understand the amount they'll be billed when transacting. TermDuration describes how long the subscription will last. Most subscriptions support Annual or pay for one year (P1Y) and monthly pay for one month (P1M). The **UnitPrice** amount is for the term being purchased. If a partner purchases an annual term with monthly pricing, they'll be billed one-twelfth the total amount each monthly billing period. The amount billed each month for an annual term with monthly billing will be the same each month throughout the term. Price changes during the term don't affect billing plan charges for an existing subscription. Price changes are only relevant for renewals, transitions, and new subscriptions.

> [!NOTE]
> New commerce trials will have a billing plan as "None" since there is no cost for trials.

### Monthly and annual terms

The price list includes **termDuration** data that explains how long the term lasts. Many products support both monthly (P1M) and annual (P1Y). However, not all products support monthly term. A few examples of this include: Microsoft Intune, Microsoft Defender for Cloud, some Phone System and Calling plans, and various Exchange Online stand-alone products. Partners should reference the current price list and filter by **termDuration** to view product SKUs by term.

### New commerce price list

Select the market and then export the price list file. The file is a compressed, comma-delimited text file.

| **Field**                           | **Example**                     | **Description**                      |
|:------------------------------------|:--------------------------------|:-------------------------------------|
| ProductTitle                        | Microsoft 365 Business Basic    | Title of the product                 |
| ProductId                           | CFQ7TTC0LH18                    | ID of the product                    |
| SkuId                               | 1                               | ID of the SKU                        |
| SkuTitle                            | Microsoft 365 Business Basic    | Title of the SKU                     |
| Publisher                           | Microsoft Corporation           | Company publishing the offer         |
| SkuDescription                      | Best for businesses that need professional email, cloud file storage, and... | Description of the offer |
| UnitOfMeasure                       |                                 | Currently only for Azure consumption |
| TermDuration                        | P1Y/P1M                         | Length of the term                   |
| BillingPlan                         | Annual/Monthly                  | How often billing happens            |
| Market                              | US                              | Market for the item                  |
| Currency                            | USD                             | Currency for the item                |
| UnitPrice                           | 48                              | Price per unit (license)             |
| PricingTierRangeMin                 | |If tiered pricing is supported, the minimum range for the price point |
| PricingTierRangeMax                 | |If tiered pricing is supported, the maximum range for the price point |
| EffectiveStartDate                  | 2/1/2023 0:00                   | The day and time a change to product metadata becomes valid. May be an actual date (example: 2023) or placeholder year (example: 1753). |
| EffectiveEndDate                    | 11/30/9999 23:59                | The day and time a change to product metadata ceases to be valid. May be an actual date (example: 2023) or placeholder year (example: 9999).  |
| EndofSaleDate                       | 12/31/2022 23:59                | The last date for the item's sale. This is only present in preview   |
| Tags                                | License; Trial                  | Miscellaneous tags                   |
| ERP Price                           | 60                              | Estimated retail price               |

#### New commerce price list details

The structure of items in the new commerce pricing file differs from the traditional office price list.

|**Category**|**Traditional license-based**|**New commerce license-based**|
|:-----------   |:-----------   |:-----------   |
|Offer ID|This is a GUID identifying the item to be purchased|ProductID/SKUID/AvailabilityID. The Availability ID is only returned in the GetAvailablities API. When purchasing through the Partner Center user interface, it's automatically included.|
|Currencies|Included tabs of all offers for all currencies|Each price sheet contains only the currency for the currently selected market.|

### New commerce offer matrix

The offer matrix contains purchase information and rules for the product SKUs. It's market-agnostic. End of sale offers will still be present in the offer matrix, refer to price list for active offers.

| **Field**                     | **Example**       | **Description**                 |
|:------------------------------|:------------------|:--------------------------------|
| ProductTitle                  | Microsoft 365 Business Basic | Title of the product |
| ProductId                     | CFQ7TTC0LH18       | ID of the product               |
| SkuId                         | 1                  | ID of the SKU                   |
| SkuTitle                      | Microsoft 365 Business Basic | Title of the SKU      |
| ProvisioningId                | 3b555118-da6a-4418-894f-7df1e2096870 | System ID defining the provisioned product |
| ProvisioningString            | O365_BUSINESS_ESSENTIALS    |Friendly key name for provisioned product |
| MinLicenses                   | 1                  | Minimum number of licenses that can be purchased |
| MaxLicenses                   | 300                | Maximum number of licenses that can be purchased |
| AssetOwnershipLimit           | 2 | Limit of assets for the given AssetOwnershipLimitType |
| AssetOwnershipLimitType       | ConcurrentCount    | Type of AssetLimit. Can be lifetime or concurrent |
| ProductSkuPreRequisites       |                    | List of SKUs the add-on supports |
| ProductSkuConversion          | CFQ7TTC0LDPB/0001, CFQ7TTC0LF8Q/0001 | List of SKUs you can convert to |
| Description                   | Best for businesses that need professional... | Description of the SKU |
| AllowedCountries              |AD;AE;AF;AG;AI;AL;AM;AO...                     | List of supported markets, not channel specific |

### Effective dates

Partners will notice two important date time values in the price lists: EffectiveStartDate and EffectiveEndDate. Partners use these values to determine which line items are active and current. Sometimes line items are duplicate in the price list, and when this occurs partners can look to the latest date ranges to identify the current line items and price points. Partners can rely on the latest date range unless the date ranges overlap.

Here's an example of overlap:

| **Product**             | **EffectiveStartDate**      | **EffectiveEndDate**      |
|:----------------------------|:-------------------------------------|:-------------------------------------|
| CFQ7TTC0HD7P | 2021-10-01T00:00:00.0000000Z | 2021-11-03T06:57:30.0682597Z |
| CFQ7TTC0HD7P | 2021-11-01T00:00:00.0000000Z | 9999-11-30T23:59:59.0000000Z |

In the preceding example, a transaction made on November 2 would be related to the top line item. A transaction made on November 4 would be associated with the second line item. Overlap is a condition the Partner Center team is working to resolve because it can cause confusion for price list consumers.

### Price list preview

New commerce supports future pricing. Partners can export and view future pricing for the coming month. Traditional license-based price lists included flags for new offers, deleted offers, changed and unchanged. New commerce pricing files enable partners to track these changes by using the EffectiveStartDate and EffectiveEndDates.

New offers will be identified when they are in the future price file but not in the current price file.

| **Change type**             | **How to identify change type**      |
|:----------------------------|:-------------------------------------|
| New                        | Line items in future pricing not in current monthly pricing |
| Change                     | Line items in both current and future, where future pricing is different, identified by updated EffectiveStartDates |
| Deletes                  | Line item in future with an EffectiveEndDate denoting the end of availability. EndOfSale denotes that partners can no longer purchase new subscriptions for that product/SKU |
| Unchanged                  | Not in the future pricing file |

### Offer limits in new commerce

Existing license-based subscriptions enforced ownership limits, or the number of subscriptions a partner could purchase for a customer. These typically were **small business** SKUs or offers with less than a 300-seat maximum. In traditional license-based subscriptions, partners could see the limits in the offer list matrix for existing seat-based products as **Concurrent** describing the number of subscriptions the partner could have. New commerce implements a seat constraint across the purchased product SKUs. New commerce small business subscriptions with less than a 300 maximum will apply the maximum at the product SKU level. So a partner could have multiple small business subscriptions for a customer as long as the aggregate of the seat counts stays under the declared maximum. The maximum for small business applies regardless of where the customer's product SKU came from, that is, multiple partner or channels.

**Traditional license-based** included a **Concurrent** setting with a limit value, usually of two. These settings mean the customer could have a maximum of two subscriptions for the offer from a given Partner.

Here's an example of the traditional, license-based offer and the concurrency setting:

- Microsoft 365 Business Premium
- Offer ID: 61795cab-2abd-43f6-88e9-c9adae5746e0
- Offer Limit Scope: Concurrent
- Offer Limit: 2

**New commerce** license-based uses a **Max Seat Count** with a value to enforce these small business limits. The product SKUs enforces this limit on any purchased subscriptions for the product SKU. So, a given customer could have four subscriptions from  different partners if the total number of seats from all subscriptions was less than 300. The limit is on the number of aggregate licenses purchased for the product SKU, not on the number of subscriptions. Partners can view these values in the offer matrix for new commerce and get these values in the SKU using the catalog APIs. Here's an example of a new commerce product SKU with the max count value:

- Microsoft 365 Business Premium
- Product ID: CFQ7TTC0LCHC
- SKU ID: 0002
- Max Seat Count: 300

The maximum limits are **pooled** on the customer tenant. A customer could have 100 licenses of a product SKU from one partner, and another 100 from a second partner. But the aggregate limit can't exceed the maximum. A transaction that exceeds the limit returns an error that includes the remaining number of available licenses, helping them to understand how many licenses are left under the maximum available. The error message will look like this: **The requested number of 51 seats exceeds the remaining limit of 50 seats allowed per subscription for the CatalogItemId - CFQ7TTC0LCHC:0002:CFQ7TTC0KFFN**. Partners will also see this information when using the APIs to add a lineItem to the cart that exceeds the limit as an error property **availableQuantity**. More information about the cart lineItem property can be found in the [API documentation cart resource](/partner-center/develop/cart-resources).

Partners can validate these limits and the available quantity functionality in **sandbox** by testing specific product SKUs with lower maximum limits. Partners can reference the offer matrix to find these product SKUs.

| **Product** | **ProductId** |  **SKU** |  **SKUId** |  **Max licenses** |
|:----------------------------|:--------------------|:--------------------|:--------------------|:--------------------|
| Dynamics 365 Business Central External Accountant | CFQ7TTC0LH33 | Dynamics 365 Business Central External Accountant | 0001 | 3 |
| IoT Intelligence | CFQ7TTC0HD4F | Sensor Data Intelligence Additional Machines Add-in for Dynamics 365 Supply Chain Management | 0002 | 10 |
| IoT Intelligence | CFQ7TTC0HD4F | Sensor Data Intelligence Scenario Add-in for Dynamics 365 Supply Chain Management | 0001 | 6 |

### SKUs with no cost

Trials are always free, but other product SKUs may also be free with no cost. Below are some examples of no cost product SKUs. The list of free product SKUs may grow over time, partners should be sure to reference the price list for the current list of free products.

| **Product** | **ProductId** |  **SKUId** |
|:----------------------------|:--------------------|:--------------------|
| Business Apps (free) | CFQ7TTC0LHZ0 | 0001 |
| Dynamics 365 Business Central External Accountant | CFQ7TTC0LH33 | 0001 |
| Dynamics 365 Customer Voice USL | CFQ7TTC0HBSM | 0001 |
| Microsoft Teams Phone Standard - Virtual User | CFQ7TTC0LH0R | 0001 |
| Power Virtual Agent | CFQ7TTC0LH1F | 0001 |

### Pricing and offer matrix APIs

Pricing and offer matrix APIs build on the existing price sheet API infrastructure that was released to support Azure plan. This API is now extended to support license-based new commerce pricing. The [price sheet and offer matrix APIs](/partner/develop/get-a-price-sheet) supports pricing for updated new commerce license-based online services only. It doesn't support traditional office license-based services available for download only from Partner Center pricing and offers page.

## Next steps

- [Azure plan pricing](azure-plan-price-list.md)
- [Azure pricing overview](https://azure.microsoft.com/pricing/)
