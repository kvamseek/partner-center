---
title: Use promotions to attract customers
ms.topic: article
ms.date: 02/01/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-pricing
description: Discover how Microsoft partners in the Cloud Solution Provider program can buy subscriptions at promotion pricing and pass savings on to their customers.
author: iragulati1
ms.author: iragulati
---

# Use promotions to attract new customers and pass the savings on to them

**Appropriate roles**: Admin agent | MPN Partner Admin | Billing admin | Sales agent

Microsoft occasionally offers promotions on license-based subscriptions, allowing you to pass the savings on to customers and grow your business.

> [!NOTE]
> This article describes how promotions work for traditional license-based subscriptions. Information about how promotions work for new commerce license-based subscriptions can be found in the [new commerce promotions topic](new-commerce-promotions.md).
>

Microsoft offers two kinds of promotions: Those available to all eligible partners in the Cloud Solution Provider (CSP) program, and those available only to partners in a particular geographic region.

Promotion pricing is automatically applied to your net price when you purchase new subscriptions at the promotion price. In addition, any licenses you add to a subscription purchased with promotion pricing are added at the promotion price.

Take a moment to review these important facts about promotions:

- A subscription's promotion price applies only for the duration of the subscription. When a subscription you purchased with promotional pricing expires, the renewal subscription's price reverts to the price in the price list. This means that any subscriptions set up for automatic renewal will renew at the prevailing price. You can find the price list on the **Pricing and offers** page.

- If a subscription is eligible for multiple promotions, the promotion with the highest percentage off is automatically applied.

- Cancellations of promotion-priced subscriptions follow the same process and policy as regularly priced subscriptions.

## See available promotions

As a partner, you can access the list of all CSP promotions in the [Global Promo Readiness Guide](https://partner.microsoft.com/resources/detail/operations-promo-guide-pdf). You'll need to sign-in to access the guide.

You can also see which traditional license-based promotions you're eligible for, if any, on your **Promotions** page. Select **Promotions** from your **Partner Center** menu to see a list of current promotions, along with the discount, promotion type, and start and end dates for the subscription. If no promotions are available, you'll see a message indicating this.

> [!NOTE]
> You can also see promotions when making a purchase. When you select a subscription, the promotion pricing appears on the **Review** page.

## Purchase subscriptions at promotion prices

1. On your **Partner Center** menu, select **Customers** and then select the customer who's buying the subscription.

2. Select **Add subscription**.

3. On the **New subscription** page, select the subscription the promotion applies to.

4. Enter the number of licenses the customer needs.

5. Review the order. You'll see the promotion pricing that will be applied in the **Discount** column.

6. Select **Submit** to purchase. Your customer will see the promotion price on their next bill.

> [!NOTE]
> The new commerce experiences for license-based services include many new capabilities and are available to all Cloud Solution Provider (CSPs). For more information, see [new commerce experiences overview](new-commerce-license-based.md).

New commerce promotions can be found while purchasing in the catalog. Catalog product SKUs that include promotions will have **Promotion available** in the SKU description. More information can be found in the [new commerce promotions article](new-commerce-promotions.md).

## NCE vs. Legacy promotions in the reconciliation file

The NCE reconciliation file has a specific attribute, "PromotionID" for identifying the promotion and looking up additional information about it. Furthermore, the file includes attributes for distinguishing between the pre-and post-promotion prices and descriptions. The legacy reconciliation file provides the "TotalOtherDiscount" attribute containing the total discount amount to track promotions.

Unlike legacy, NCE promotions are not separated by billing plans. In legacy, only the monthly billing plan is eligible for promotions. However, regardless of your billing plan, you'll receive a discount from NCE.

## How to identify promotions in the NCE recon file?

The Partner Center reconciliation file has an identifier called "PromotionID" to help you determine whether a product was sold as a promotion at the time of purchase. You can use this identifier to look up additional information about the promotion, such as its name, validity, and discount percentage. Using this information, you can generate customer invoices and pass the benefit on to them.

In addition to the "PromotionID," you must pay attention to other attributes to verify the prices and discount description. The "UnitPrice" column shows the pre-promotion price, and the "EffectiveUnitPrice" column shows the post-promotion price. Furthermore, the "PriceAdjustmentDescription" column describes that the specific transaction has a discounted price.

More information about how promotions work for new commerce license-based subscriptions can be found in the [new commerce promotions topic](new-commerce-promotions.md).

## Next steps

- [Sell to specialized audiences](sell-to-education-customers.md)
