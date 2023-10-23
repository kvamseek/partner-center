---
title: Common legacy monthly billing scenarios
ms.topic: article
ms.date: 11/08/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-billing
description: Common scenarios in Partner Center when you use legacy monthly billing - includes adding new subscriptions, changing license quantity, and suspending subscriptions.
author: sodeb
ms.author: sodeb
---

# Sample legacy monthly billing scenarios for new subscriptions, changing license amounts, or suspensions

**Appropriate roles**: Admin agent | Billing admin | Helpdesk agent | Sales agent

These examples of [common billing scenarios](common-billing-scenarios.md) apply if you use monthly billing in Partner Center.

## New monthly subscription

Your billing date is the 15th of each month. On January 13, you purchase a new subscription with one license for $4/month and select monthly billing. The January 15 license-based reconciliation file will contain the following billing lines:

|Charge Start Date |Charge End Date |Charge Type |Unit Price |Quantity |Amount |
|       :---:      |    :---:       | :---:      |:---:      |:---:    |:---:  |
|1/13/2018         |2/12/2018    |Cycle fee   |4.00       |1        |4.00 |

The February 15 license-based reconciliation file will contain the following billing line:

|Charge Start Date |Charge End Date |Charge Type |Unit Price |Quantity |Amount |
|       :---:      |    :---:       | :---:      |:---:      |:---:    |:---:  |
|2/13/2018         |3/12/2018    |Cycle fee   |4.00       |1        |4.00 |

## Change license quantity

Your billing date is the 15th of each month. On January 13, you purchase a new subscription with one license for $4/month and select monthly billing. The January 15 license-based reconciliation file will contain the following billing lines:

|Charge Start Date |Charge End Date |Charge Type |Unit Price |Quantity |Amount |
|       :---:      |    :---:       | :---:      |:---:      |:---:    |:---:  |
|1/13/2018         |2/12/2018    |Cycle fee   |4.00       |1        |4.00    |

On February 1, you increase your license quantity from one to two. The February 15 license-based reconciliation file will contain the following billing lines:

|Charge Start Date |Charge End Date |Charge Type |Unit Price |Quantity |Amount |
|       :---:      |    :---:       | :---:      |:---:      |:---:    |:---:  |
| 1/13/2018        |2/12/2018    |Cycle Instance Prorate   |-4.00       |1        |-4.00   |
|1/13/2018         |1/31/2018    | Cycle Instance Prorate   |2.45       |1        |2.45    |
|2/1/2018         |2/12/2018    | Cycle Instance Prorate   |1.55       |2        |3.10    |
|2/13/2018         |3/12/2018    | Cycle Instance Prorate   |4.00       |2        |8.00    |

The monthly price is 4.00 and there are 31 days in the service period 1/13/2018 – 2/12/2018, which equates to a daily price of 0.129 (4/31).

There are 19 days in the proration period 1/13/2018 – 1/31/2018.

Proration unit price = 2.451 = 19 x 0.129

There are 12 days in the proration period 2/1/2018 – 2/12/2018.

Proration unit price = 1.54 = 12 x 0.129

## Suspend before 30 days

Your billing date is the 15th of each month. On January 13, you purchase a new subscription with one license for $4/month and select monthly billing. The January 15 license-based reconciliation file will contain the following billing lines:

|Charge Start Date |Charge End Date |Charge Type |Unit Price |Quantity |Amount |
|       :---:      |    :---:       | :---:      |:---:      |:---:    |:---:  |
|1/13/2018         |2/12/2018    |Cycle fee   |4.00       |1        |4.00    |

On February 1, you suspend a subscription. The February 15 license-based reconciliation file will contain the following billing line:

|Charge Start Date |Charge End Date |Charge Type |Unit Price |Quantity |Amount |
|       :---:      |    :---:       | :---:      |:---:      |:---:    |:---:  |
1/13/2018|2/12/2018|Cancel Fee|-4.00|1|-4.00

## Suspend after 30 days

Your billing date is the 15th of each month. On January 13, you purchase a new subscription with one license for $4/month and select monthly billing. The January 15 license-based reconciliation file will contain the following billing lines:

|Charge Start Date |Charge End Date |Charge Type |Unit Price |Quantity |Amount |
|       :---:      |    :---:       | :---:      |:---:      |:---:    |:---:  |
1/13/2018|2/12/2018|Cycle Fee|4.00|1|4.00

The February 15 license-based reconciliation file will contain the following billing line:

|Charge Start Date |Charge End Date |Charge Type |Unit Price |Quantity |Amount |
|       :---:      |    :---:       | :---:      |:---:      |:---:    |:---:  |
2/13/2018|3/12/2018|Cycle Fee|4.00|1|4.00

On March 1, you suspend subscription. The March 15 license-based reconciliation file will contain the following billing line:

|Charge Start Date |Charge End Date |Charge Type |Unit Price |Quantity |Amount |
|       :---:      |    :---:       | :---:      |:---:      |:---:    |:---:  |
3/1/2018|3/12/2018|Cancel Fee|-1.72|1|-1.72

The monthly price is 4.00 and there are 28 days in the service period 2/13/2018 – 3/12/2018, which equates to a daily price of 0.143 (4/28).

Unit price = days in service period x daily price x number of licenses.

There are 12 days in the cancellation period 3/1/2018 – 3/12/2018.

Therefore, the unit price = -1.716 (12 x 0.143 x (-1)).

## Change license quantity and convert from monthly to annual billing

You can change the billing frequency of a subscription from annual to monthly or monthly to annual. To learn the details, see [Billing frequency changes](billing-frequency-changes.md).

In the example that follows, you renew a subscription with monthly billing and then change the billing frequency to annual. (For an example of the reverse scenario, see [Renew with Annual billing, convert to monthly billing](common-billing-scenarios-annual.md#renew-with-annual-billing-convert-to-monthly-billing)).

- Your billing date is the 15th of each month.
- On June 1, you increase the license quantity of this monthly billing subscription from 1 to 2,650.
- On the same day, you convert from monthly to annual billing.
- The June 15 license-based reconciliation file has the following information:

|Sub Start|Sub End|Charge Start|Charge End|Charge Type|Unit Price|Qty|Art|Bill Cycle|
|---|---|---|---|---|---|---|---|---|
|2/26/2021|2/26/2022|5/26/2021|6/25/2021|Cycle fee|21.1|1|211.00|Monthly
|06/01/2021|06/01/2022|06/01/2021|5/31/2022|Prorate fees when convert away from current offering|270.12|2650|7,158,180.00|Annually|
|2/26/2021|2/26/2022|06/01/2021|6/25/2021|Prorate fees when convert to a new offering|-17.01|2650|-450,927.40|Monthly|
|2/26/2021|2/26/2022|5/26/2021|5/31/2021|Convert from instance prorate|4.08|1|40.80|Monthly|
|2/26/2021|2/26/2022|06/01/2021|6/25/2021|Convert from instance prorate|17.01|2650|450,927.40|Monthly|
|2/26/2021|2/26/2022|5/26/2021|6/25/2021|Convert from instance prorate|-21.1|1|-211.00|Monthly|

**Explanation of rows one to six:**

**Row 1**: Charge for the monthly billing period before the license count change and billing frequency change.

**Row 2**: Charge for the annual billing period after billing frequency was changed to annual and with the new license count. The subscription start date corresponds to the date when the billing frequency was changed. As a consequence, the new Charge Start Date aligns with the new subscription anniversary date.

**Row 3**: Prorated credit for monthly charge for the unused portion of the monthly billing period due to billing frequency change with the new license count.

**Rows 4, 5, and 6**: These fees are prorated, deriving from the license count change (the increase from 1 to 2,650 on June 1) with monthly billing.

## Next steps

- [Billing scenarios for one-time and select recurring purchases](common-billing-scenarios-onetime-recurring.md)
