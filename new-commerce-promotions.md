---
title: New commerce promotions
ms.topic: article
ms.date: 03/21/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-pricing
description: Learn about new commerce experiences for discovering and purchasing promotions.
author: iragulati1
ms.author: iragulati
---

# New commerce promotions

**Appropriate roles**: Admin agent | Sales agent | Global admin

> [!NOTE]
> The new commerce experiences for license-based services include many new capabilities and are available to all Cloud Solution Provider (CSPs). For more information, see [new commerce experiences overview](new-commerce-license-based.md).

Microsoft supports promotions in new commerce. These promotions have varying discount amounts and durations.

### Verify promotions before being billed

You can check the estimates file or unbilled open-period line items by:

- Going to the Partner Center billing page
- Calling the Partner Center APIs to see if promotions were applied to a transaction

The `PromotionID` indicates whether or not the promotion was applied. The `EffectiveUnitPrice` indicates the discounted price. On average, these details are updated 6 hours after the transaction. However, they can take as little as one hour or as long as 24 hours due to system latency.

You can also verify the promotion was applied int the Partner Center order history and activity logs. More information about billing and reconciliation files can be found in the [New Commerce Operations Guide](https://partner.microsoft.com/resources/detail/operating-guide-new-commerce-experience-for-csp-seat-based-offers-pdf).

## Discovering promotions

You can discover promotions by visiting the promotions backlog or by calling the `getPromotions` API. The promotions backlog is a Microsoft list of available promotions that you need to know about. The list is editorially maintained and updated monthly.

As a partner, you can access the list of all CSP promotions in the [Global Promo Readiness Guide](https://partner.microsoft.com/resources/detail/operations-promo-guide-pdf). You need to sign-in to access the guide.

## Get promotions list

You can get a [list of active new commerce promotions](/partner-center/develop/get-promotions) for a given market (country/region) and segment.

The API returns this list of promotions and important information to help you understand which promotions are available for customers in different countries/regions.

The `getPromotions` API includes the following data for a given promotion:

- Duration of the promotion
- The percentage discount for the promotion. The discount is applied to the partner price (not estimated retail price or ERP).
- The products and SKUs the promotion is available for

Promotions are applied by the Partner Center when you purchase the product SKU that the promotion is available for. Partner promotions are available in the Partner Center catalog in product SKU details. You can select **View promotion details** to get more information about the promotion.

You can view the promotion details from the catalog page view SKU details, the review page before submitting the purchase, the confirmation after the order is submitted and the order history page.

## Verify eligibility

You can view whether a customer purchase is eligible for a promotion by seeing the information in the review page in Partner Center before purchasing the product. You can also call the [verifyPromotionEligibility API](/partner-center/develop/verify-promotion-eligibility), passing the `customer tenant ID` and the `promotion ID`. The call returns true if the customer is eligible.

If the customer isn't eligible, the API returns the conditions that weren't met for the promotion to be applied.

You can call verify eligibility and get results back. Eligibility errors can be based on seat counts, incompatible terms, or limits on how many times a promotion can be applied to a customer's product SKU.

For a list of important articles about new commerce promotions APIs, see [Next steps](#next-steps) at the end of this article.

> [!IMPORTANT]
> As a partner, you should:
>
> - Verify promotions before you submit a transaction. In the Partner Center *review page* if you don't see a promotion, it isn't be applied on the transaction and you receive the non-promotion price.
> - Look at the cart line item API to see if the promotion is present before submitting a transaction.
> - Call verify promotions API before submitting transactions to verify your customer product sku combination is eligible for the promotion and, if not, the reasons for ineligibility.

There are various reasons a customer isn't eligible for a promotion. These ineligible types are returned in the validate promotion API in the cases where the customer isn't eligible.

| **ErrorCode** | **Description** |
|------------------|----------------------------|
| InvalidCatalogItemId | Incorrect product SKU availability ID is passed to the eligibility check. |
| InvalidPromotion | Incorrect product SKU availability ID is passed to the eligibility check. |
| PrerequisiteProductOwnership | Customer doesn't have a prerequisite that is required. This scenario is most common when purchasing promotions available for add-ons. |
| RedemptionLimit | Attempting to purchase a promotion that has exceeded the number of redemptions. |
| SeatCount | Attempting to purchase a promotion with a seat limit. Results include remaining licenses that can be purchased.  |
| OfferPurchasedPreviously | Returned for promotions that have one time purchase constraints configured. These can only be purchased one time.  |
| Term | Incorrect product SKU availability ID is passed to the eligibility check. |

Below are some examples of constraints and validation scenarios.

### Seat Count

Seat limits for promotions are enforced across partners. In a case where a promotion has a maximum seat count limit of 1,000 and a seat count minimum of 1, if one partner purchases a promotion of 900 seats, a second partner who purchases 200 seats for the same customer would get the subscription price at the non-promotional price.

Promotion eligibly is enforced at the promotion ID's product SKU when the partner is transacting. A promotion ID has a **product:SKU:availability** structure. The partner transacts the product SKU and availability from the catalog APIs and the `promotionID` is applied to the transaction.

Limits, like seat count, are evaluated against the promotionID's product SKU, but not the availability. For an example of a promotion ID of **39NFJQT1PGVJ:0045:39NFJQT1Q684** applied to a catalog item product SKU of **CFQ7TTC0LFLX:0001**, the limit is enforced against **39NFJQT1PGVJ:0045**. Different catalog item product SKUs have different promotion IDs, so a partner could get promotional pricing for the maximum seat limit of Microsoft 365 E3 (given that promotion has a seat count maximum) and promotional pricing for a different product SKU, such as Microsoft 365 E5.

If a promotion has a seat count maximum and a partner wants more licenses than the maximum seats, the partner needs to purchase one subscription up to the limit at the promotional price and a second subscription at the non-promotional price.

You should always rely on the [verify eligibility API](/partner-center/develop/verify-promotion-eligibility) to understand whether a promotion is applied before purchasing. The API returns the minimum, maximum, and the **remaining available licenses** if the seat limits aren't met.

For example, if a single customer has two partners and a single promotion with a seat constraint maximum of 1,000:

- Partner 1 purchases 600 seats for a customer.
- Partner 2 sees the promotion and wants to purchase 500 seats for the same customer even though there are only 400 seats available.

In this case, verify eligibility returns a seat count error. The error includes the minimum, maximum and, in this case, the 400 available seats.

If a partner tries to increase a subscription's seats beyond the promotional limits, they'll see an error: `This subscription has a discount applied and the desired quantity is not within minimum and maximum allowed quantity`.

Promotions sometimes change the availability ID under the promotion's product SKU. Depending on the promotion, the limits may include term and billing plan for the same Product SKU.

### Term

Promotions have different discounts defined based on the term. If a partner submits a transaction and the term doesn't match the promotion, the transaction is at the non-promotional price. Examples of terms are *annual* or *monthly*.

Partners may change the term duration of a subscription with a promotion midterm (to supported options available on Partner Center). If a promotion is available for the specific term and billing cycle that the subscription has following the change, the promotion is automatically applied. Midterm changes take effect immediately. When making a midterm update, ensure there are no scheduled changes for the subscription before adjusting term length.

### Scheduled changes and promotions

Partners can schedule changes to apply to their subscription for the next term. Partners can see if a current promotion is applied and the promotion the scheduled changes are enabled for the next term in the right pane for the scheduled change. Partners also see if the scheduled changes result in no promotion. Like all promotions, the scheduled change promotions apply to the next term's duration. Partners should take notice of whether a scheduled change includes a promotion before scheduling the change.

Partners using the **APIs** can include an optional promotion ID when [scheduling changes](/partner-center/develop/create-scheduled-changes) long as the promotion is eligible. Partners should verify the promotion's eligibility before including a promotion ID. Scheduled changes submitted to the API return an eligible promotion ID if one exists. This promotion is applied to the subscription term as long as the scheduled change is not removed. Scheduled changes displaying no promotion ID indicate the next subscription term will not have a promotion.

> [!NOTE]
> The ability for a promotion to be applied to a scheduled change is a new feature. Any scheduled changes saved prior to June 16, 2022 need to be resubmitted in order for a promotion to apply. This feature does not retroactively apply promotions to scheduled changes saved prior to this date.

### Offer Previously Purchased

Some promotions enforce something called **FirstPurchase**. Both the Dynamics AX Migration and SMB OnPrem Transition evaluate and enforce the new customer limitation. Partner Center enforces a check to only enable the promotion to be applied if the customer has no existing product SKU the promotion is for. This check either includes both previous seat-based purchases (legacy) and new commerce product SKUs or only new commerce product SKUs. Please refer to the  [Global Promo Readiness Guide](https://partner.microsoft.com/resources/detail/operations-promo-guide-pdf) for details on a specific promotions eligibility. The new customer limitation ensures that the product SKU hasn't previously been purchased in the platforms specified at promo configuration.

You're encouraged to always check the Partner Center **review** screen when making a purchase to see if the expected promotion is applied. Partners who use the APIs should use the [VerifyPromotionEligibilities](/partner-center/develop/verify-promotion-eligibility) API to evaluate whether the customer is eligible for a given promotion.

### Redemption Limit

Some promotions can only be purchased once. A partner sees an eligibility of **false** using the validate eligibility API with the error type of *RedemptionLimit*. A partner can still purchase the given product SKU but the subscription will be at the non-promotional price. The limitation is per customer, not per partner. Once a customer has a promotion with this rule, they can't get a second promotion applied by a second partner.

### Checking eligibility for promotion IDs that change

Promotion IDs include three distinct pieces of information, delimited by a colon. An example is: **39NFJQT1W0JL:0003:39NFJQT1Q5KW**. This is represented as **Product:SKU:Availability** of the promotion. Availability IDs may change frequently just as availabilities often change for product SKUs in the catalog. Partners can still call the eligibility API with the original promotion ID if the availability ID has changed. You can also pass the new current promotion's availability ID, both producing the same eligibility check and results. This is helpful for partners who have promotions enforcing the 2,400 seat cap limits.

Eligibility checks won't honor expired or end-dated promotion Ids. If you have an existing subscription, you'll have to rely on the subscription update's generic errors to know whether the applied change was accepted.

### Opting in to promotions

Nearly all promotions in New Commerce are auto-applicable, and no action is needed for the promotions to apply on eligible offers. The Bridge to the Cloud 2 Promotion (BTTC2) is an exception. BTTC2 is intended for customers who are moving from Dynamics on-premises products to Dynamics cloud products; for customers to qualify for this promotion, their partner must attest they meet the eligibility criteria and apply the promotion at checkout. Within the Partner Center UI, a dropdown appears on the Review page for Dynamics products that qualify for the BTTC2 promo, and a partner can select the discount from the dropdown if they have confirmed their customers meet the eligibility criteria.

For a detailed FAQ regarding the Bridge to the Cloud 2 promotion and customer eligibility, visit [Bridge to the Cloud FAQ](https://dynamicspartners.transform.microsoft.com/migration?tab=tab-custom4). You'll need to sign-in to access the available resources.

## Promotions and renewals

Promotional discounts are for the term of the purchase. Subscriptions with applied promotions keep the promotional price if the renewal date is in the promotion duration date range. Renewals outside of the promotion duration date range renew at the non-promotion price (from the price list). You can track the renewal status in the subscription details page and on the getSubscription data renewal instructions.

## Promotions and manage scenarios

New commerce promotions are applicable for new subscription purchases, renewals (when a subscription's applied promotion has an enrollment window inclusive of the renewal dates), migrations from legacy to new commerce, scheduled changes to new SKUs or terms, and mid-term changes to a longer term.

Throughout the duration of the promotion window, additional licenses can be added to the promotional offer (up to seat maximums).

Mid-term upgrades support promotions. Upgrading mid-term to an existing destination subscription without a promotion won't apply a promotion to the existing subscription if one isn't already present. Scheduled upgrades apply promotions, given a promotion is active during the scheduled change date and the customer is eligible.

Partner Center permits upgrades from both non-promo and promo base offers to existing promo offers, given that the destination subscription is 1) not within it’s cancellation window, 2) not of shorter term length than the base subscription, and 3) not ending at an earlier date than the base subscription. If you're using the Partner Center APIs, you'll see a promotion ID returned after posting the transition. This promotion ID tells you that the promotion was applied to the transition.

If you're using the Partner Center APIs, you'll see a promotion ID returned after posting the transition. This promotion ID tells you that the promotion was applied to the transition.

Promotion IDs can also be found in the unbilled line items in the new commerce recon file. Promotions are reflected in the subscription details page, where they show whether the current subscription promotion renews at the promotional price or the non-promotional price.

## Promotions and eligibility exceptions

If a partner purchases an offer with a promotion that has the First Purchase constraint, the partner doesn't receive the promotional pricing on any purchases other than the initial transaction. 

The following cases invalidate promotional eligibility with the First Purchase constraint:

- Partner purchases a subscription with a promo and later cancels the subscription. Future purchases of the offer won't receive promotional pricing.
- Trial subscriptions count against the First Purchase constraint. Promotional pricing is not applied when auto-renewing from a trial to paid subscription.

Additionally, if a promotion has a maximum seat count limit, canceled seats count against this limit.

## Promotions that overlap in traditional license-based commerce

Traditional license-based offers included some promotions whose terms overlap with the new commerce promotions. Below are some examples:

- Dynamics AX Migration 40% three-year term
- SMB OnPrem Transition 60% annual term

In cases where a term overlaps, only the deeper discounted promotion is applied. For example, the annual SMB OnPrem promotion takes precedence over the new commerce annual 5% launch promotions. You can reference the promotions guide for more details.

## Promotions and migrations

You can migrate your customer's subscriptions from traditional Microsoft 365/Dynamics 365 to the new commerce versions of their subscriptions. The migrations are available both from the Partner Center or from calling the migration APIs.

When you migrate from a traditional subscription to new commerce, the product SKU you move must match the promotion definition in order to get the promotion. Partners can locate the NCE product SKU that a legacy subscription will be migrated to by referencing [Validate a new commerce migration](/partner-center/develop/validate-subscription-for-migration).

You can call the [verifyPromotionEligibility API](./developer/verify-promotion-eligibility.md) to ensure the target product SKU is applied to the promotional price before migration.

Migrating to a subscription with the promotion applies the promotional price for the rest of the migrated subscription's term. When migrating a subscription to new commerce, you can select to either start a new term or align to the traditional office subscription's term. The promotional price applies to whichever term you choose.

The promotion is reapplied when the renewal date is in the promotion's start and end date range if the new commerce subscription has only a few months before its term ends. For more information about how to choose a new term upon migration, see [Create a new commerce migration](/partner-center/develop/create-migration).

## Pricing and reconciliation for promotions

Price list files don't include promotional pricing or information. You should use the [GetPromotions API](/partner-center/develop/get-promotions) or discover promotions in the Partner Center catalog purchase experiences. The API and Partner Center include details about the promotions, such as the percentage of discount and how long the promotion is available for.

You can find the promotions you purchased in the new commerce reconciliation files. The reconciliation line item has information in the following fields:

- `PromotionID` includes the product, SKU and availability ID for the promotion. Partners can use the [GetPromotionsById API](/partner-center/develop/get-promotion-by-id) to get more details about the promotion.
- `PriceAdjustmentDescription` includes an explanation about the price change.
- `UnitPrice` is the price per unit for the purchase.
- `EffectiveUnitPrice` is the price the partner was charged. It reflects the difference between the UnitPrice and the percentage discount for the promotion.

Traditional license-based purchases include different details as reconciliation files are different.

## Cross-channel considerations

Cloud Solution Provider (CSP) promotion limits aren't enforced across channels, such as enterprise agreement (EA). You can acquire a new commerce promotion with a 2,400-promotion limit even when the customer may have 3,000 seats from EA.

## Next steps

- [GetPromotions API](/partner-center/develop/get-promotions)
- [GetPromotionsById API](/partner-center/develop/get-promotion-by-id)
- [VerifyPromotionEligibilities](/partner-center/develop/verify-promotion-eligibility)
- [Promotions resources](/partner-center/develop/promotion-resources)
