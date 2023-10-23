---
title: Software promotions
ms.topic: article
ms.date: 11/17/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-pricing
description: Learn about experiences for discovering and purchasing software promotions.
author: iragulati1
ms.author: iragulati
---

# Software promotions

**Appropriate roles**: Admin agent | Sales agent | Global admin

This article describes software promotions, including how to find promotions, eligibility, pricing, renewals, and reconciliation.

## Verify promotions before being billed

You can see whether promotions were applied to a transaction by:

- Checking the *Order history* and *Activity* logs at Partner Center.
- Calling the Partner Center APIs.
- Checking the estimates file or unbilled open period line items on the Partner Center **Billing** page.
  - `PromotionID` indicates whether or not a promotion was applied.
  - `EffectiveUnitPrice` indicates the discounted price.

The preceding information is updated about six hours after a transaction. However, updates can take as little as one hour or as long as 24 hours due to system latency.

## Discovering promotions

You can discover promotions by browsing the Partner Center catalog.

When you browse for software products, *Promotion Available* appears with products that have discounts available. Selecting this line displays a pop-up with details about the promotion.

You can view promotion details:

- From the review page before submitting a purchase
- From the confirmation after the order is submitted
- On the order history page

The [Get Promotions API](/partner-center/develop/get-promotions) returns promotions for license-based new commerce subscriptions.

## Applying software promotions

Some software promotions require the partner to opt in their customer.

In Partner Center, a dropdown list is available on the **Review Cart** page. Select the software promotion you want to apply from this list.

If you are using the APIs, when [creating a cart](/partner-center/develop/create-a-cart), enter the promotion ID as an optional field of the request.

## Promotional eligibility

Unlike license-based subscriptions, software promotions aren't checked for eligibility constraints and might apply to all customers.

> [!IMPORTANT]
> As a partner, you should verify promotions before you submit a transaction.
>
> If you don't see a promotion on the Partner Center **Review** page, a promotion won't be applied to the transaction, and you will get the non-promotion price.

## Promotions and renewals

Promotional discounts are for the term of a purchase.

- Software subscriptions with applied promotions keep the promotional price if the renewal date is in the promotion duration date range.

- Renewals outside of the promotion duration date range renew at the non-promotion price (from the price list).

You can track renewal status on the subscription details page and on the getSubscription data renewal instructions.

## Pricing and reconciliation for promotions

Price list files don't include promotional pricing or information.

To discover promotions, use the following methods:

- Use the Partner Center catalog.
- Use the [GetPromotions API](/partner-center/develop/get-promotions).

Both Partner Center and the API have information about promotions, such as the percentage discount and how long a promotion is available.

### New commerce reconciliation files line items

You can find the promotions you purchased in the new commerce reconciliation files. The reconciliation line items have information the following information:

|Reconciliation line item  |Meaning  |
|---------|---------|
|`PromotionID`    | Product, SKU, and availability ID for the promotion. Partners can use the [GetPromotionsById API](/partner-center/develop/get-promotion-by-id) to get more details about the promotion.        |
|`PriceAdjustmentDescription`     | Explanation of the price change        |
|`UnitPrice`    | Price per unit for the purchase        |
|`EffectiveUnitPrice`    | Price the partner was charged. Price reflects difference between the `UnitPrice` and the percentage discount for the promotion.        |

Traditional, license-based purchases have different information because the reconciliation files are different.

## Next steps

- [GetPromotionsById API](/partner-center/develop/get-promotion-by-id)
- [Promotions resources](/partner-center/develop/promotion-resources)
