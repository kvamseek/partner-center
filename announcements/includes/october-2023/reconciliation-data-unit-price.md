---
title: include file
ms.topic: include
author: sourishdeb
ms.author: sodeb
ms.date: 10/03/2023
---

## The unit price in the reconciliation data now shows the price based on the usage tiers

*We're excited to announce that our reconciliation data now includes a new feature that shows the unit price based on the usage tiers. This enhancement provides our customers with a more accurate representation of their costs and allows for better financial planning. Reconciliation data plays a pivotal role in helping you understand your consumption and billing. It's the key to ensure you're charged accurately for the resources you use. One important element within this data is the unit price.*

- **Date**: October 3, 2023
- **Workspace**: Billing
- **Impacted audience**: All global partners who have customers with Azure plan subscriptions

The unit price in the reconciliation data shows the price based on the usage tiers. But what exactly are usage tiers, and why do they matter?

Usage tiers are a way of pricing your consumption services based on the amount you consume. They help ensure fairness in billing, while accommodating the varying needs of our diverse customer base.

Here's how it works:

- **Tier structure**: Usage tiers are typically structured into multiple levels. The more you consume, the higher the tier you fall into.
- **Pricing variations**: Each tier has a different unit price. The unit price can increase or decrease as you move into higher tiers.

**Example**:

Let's say you're using “Log Analytics - Pay-as-you-go” product. The first tier might cover up to five units at a lower unit price. If your usage exceeds that initial threshold, you enter the second tier with a slightly higher unit price, and so on, for subsequent tiers.

|ProductID |SKUID |SKU title |Unit of measure |Currency |Unit price |Pricing tier range min |Pricing tier range max |
|---|---|---|---|---|---|---|---|
|DZH318Z0BQD2 |003J |Log analytics - Pay-as-you-go - EU West |1 GB |USD |0 |1 |5 |
|DZH318Z0BQD2 |003J |Log analytics - Pay-as-you-go - EU West |1 GB |USD |2.99 |6 |9223372036854780000 |

##### How does it show in the reconciliation data today?

Let's assume you purchased the “Log analytics - Pay-as-you-go - EU West” product for one of your customers. At the end of the billing period, you used 37 units of this product. In your reconciliation file, you see two lines for it.

- One line shows the usage and cost of the first tier with a price adjustment description of ["15.0% Partner earned credit for services managed", "100.0% Tier 1 Discount"].
- The other line shows the cost and usage for the second tier with the price adjustment description of ["15.0% Partner earned credit for services managed"].

However, in both lines, the unit price is displayed as the base tier or the first-tier unit price, which is **2.99**.

|ProductID |SKUID |AvailabilityID |SkuName |UnitPrice |Quantity |Subtotal |TaxTotal |Total |PriceAdjustmentDescription |SubscriptionID |EffectiveUnitPrice |BillableQuantity |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
|DZH318Z0BQD2 |003J |DZH318Z0B5DK |Log analytics - Pay-as-you-go - EU West |2.99 |1 |0 |0 |0 |["15.0% Partner earned credit for services managed","100.0% Tier 1 Discount"] |92e68872-582e-4783-d1fc-59e6dc43eab0 |0 |5 |
|DZH318Z0BQD2 |003J |DZH318Z0B5DK |Log analytics - Pay-as-you-go - EU West |2.99 |1 |81.33 |0 |81.33 |["15.0% Partner earned credit for services managed"] | 92e68872-582e-4783-d1fc-59e6dc43eab0 |2.5415 |32 |

##### How will it show in the reconciliation data after the change?

However, after the modification, the reconciliation file are more streamlined and will display as follows:

- The **first line** shows the **unit price as zero** based on the tier.
- The **second line** shows the **unit price as 2.99** based on the tier. The descriptions for the price adjustments are also updated since the tier adjustments are applied to the unit price. Therefore, only the adjustments related to partner earned credit are shown.

|ProductID |SKUID |AvailabilityID |SkuName |UnitPrice |Quantity |Subtotal |TaxTotal |Total |PriceAdjustmentDescription |SubscriptionID |EffectiveUnitPrice |BillableQuantity |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
|DZH318Z0BQD2 |003J |DZH318Z0B5DK | Log analytics - Pay-as-you-go - EU West |0 |1 |0 |0 |0 |["15.0% Partner earned credit for services managed"] |92e68872-582e-4783-d1fc-59e6dc43eab0 |0 |5 |
|DZH318Z0BQD2 |003J |DZH318Z0B5DK |Log analytics - Pay-as-you-go - EU West |2.99 |1 |81.33 |0 |81.33 |["15.0% Partner earned credit for services managed"] |92e68872-582e-4783-d1fc-59e6dc43eab0 |2.5415 |32 |

##### How do you interpret your reconciliation data?

When you review your reconciliation data, review the unit price based on usage tiers. Two pointers:

- **Tier level**: Identify which tier your consumption falls into. The unit price for each tier should be clearly indicated in your reconciliation data.
- **Accurate billing**: Ensure that your consumption and the associated unit price align with your expectations. If you have questions or concerns, reach out to our customer support team for clarification.

##### Known limitation

No limitations are known.

##### Benefits

With the addition of the unit price based on different usage tiers, you enjoy the following advantages:

- A complete overview of your expenses and the ability to make well-informed decisions regarding the resource allocation
- The power to optimize their usage and effectively manage costs
- Improved accuracy and reliability of the information provided

We're confident that this enhancement will greatly benefit our partners and contribute to your overall satisfaction with our services.

#### Next steps

This feature is **expected to be introduced in the calendar year 2024**. Currently, we don't have a set timeline, but once it's confirmed, we'll update you 60 days in advance.

However, for now, prioritize the following activities to ensure a smooth change management process:

- **Make any necessary internal adjustments to your reconciliation process** for handling customer invoices.
- **Inform your development and operation teams about the change** and ensure they're aware of the necessary adaptations to the process.

We're dedicated to constantly improving our platform and providing our partners with efficient tools and insights. We **value your feedback and suggestions** to further enhance our services. Don't hesitate to **share your thoughts**.
