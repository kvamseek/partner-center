---
title: Legacy annual billing - common scenarios
ms.topic: article
ms.date: 11/8/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-billing
description: Partner Center legacy annual billing - when you add new subscriptions, add licenses before billing date, change license quantity, or suspend/reactivate subscriptions.
author: sodeb
ms.author: sodeb
---

# Common legacy annual billing scenarios in Partner Center

**Appropriate roles**: Admin agent | Billing admin | Helpdesk agent | Sales agent

These example [common billing scenarios](common-billing-scenarios.md) are applicable if you use annual billing in Partner Center.

## New annual subscription

Your billing date is the 15th of each month. On January 13, you buy a new subscription with one license for $4 a month and select annual billing. The January 15 license-based reconciliation file will contain the following billing line:

|Charge Start Date |Charge End Date |Charge Type |Unit Price |Quantity |Amount |
|       :---:      |    :---:       | :---:      |:---:      |:---:    |:---:  |
January 13, 2018|January 12, 2019|Prorate fees when purchase|48.00|1|48.00

## Add license after subscription anniversary date but before billing date

You buy a new subscription on February 11, 2017 with one license for $211.20 a year. Your subscription anniversary is set as the 11th of each month. The Microsoft billing system creates the following billing lines:

- $211.20 charge for period February 11, 2017 – February 10, 2018.

On February 12, 2017, you buy a second license. Your billing date is February 14, 2017. An invoice and reconciliation file are generated. The reconciliation file will contain the following billing lines:

|Charge Start Date  |Charge End Date  |Charge Type  |Unit Price |Quantity | Amount |
|      :---:   |      :---:   |      :---:   |      :---:   |:---:   |:---:   |
|February 11, 2017 |February 10, 2018 |Prorate Fees When Purchase |211.20 |1 | 211.20 |

On your subscription anniversary, March 11, 2017, the Microsoft billing system creates the following billing lines for the license increase on February 12, 2017:

- $211.20 credit for period February 11, 2017 to February 10, 2018.
- $0.58 prorated charge per license for one license for period February 11, 2017 to February 11, 2017.
- $15.62 prorated charge per license for two licenses for period February 12, 2017 to March 10.
- $195.00 prorated charge per license for two licenses for period March 11, 2017 to February 10, 2018.

On February 11, 2017, you buy a subscription. On February 12, 2017, you add a license. Your billing date is February 14, 2017. On February 11, 2018 your subscription renews.

Your next billing date is March 14, 2017, and an invoice and reconciliation file are generated. The reconciliation file will contain the following billing lines:

|Charge Start Date  |Charge End Date  |Charge Type  |Unit Price |Quantity | Amount |
|      :---:   |      :---:   |      :---:   |      :---:   |:---:   |:---:   |
|February 11, 2017 |February 10, 2018 |Cycle Instance Prorate |-211.20 |1 |-211.20 |
|February 11, 2017 |February 11, 2017 |Cycle Instance Prorate |0.58 |1 |0.58 |
|February 12, 2017 |March 10, 2017 |Cycle Instance Prorate |15.62 |2 |31.25 |
|March 11, 2017 |February 10, 2018 |Cycle Instance Prorate |195.00 |2 |390.00 |

On February 11, 2018 the subscription renews for another 12-month term.

## Change license quantity

Your billing date is the 15th of each month. On January 13, you buy a new subscription with one license for $4 a month and select annual billing. The January 15 license-based reconciliation file will contain the following billing line:

|Charge Start Date |Charge End Date |Charge Type |Unit Price |Quantity |Amount |
|       :---:      |    :---:       | :---:      |:---:      |:---:    |:---:  |
January 13, 2018|January 12, 2019|Prorate fees when buy|48.00|1|48.00

On February 1, you increase your license quantity from one to two. The February 15 license-based reconciliation file will contain the following billing lines:

|Charge Start Date |Charge End Date |Charge Type |Unit Price |Quantity |Amount |
|       :---:      |    :---:       | :---:      |:---:      |:---:    |:---:  |
January 13, 2018|January 12, 2019|Cycle Instance Prorate|-48.00|1|-48.00
January 13, 2018|January 31, 2018|Cycle Instance Prorate|2.47|1|2.47
February 1, 2018|January 12, 2019|Cycle Instance Prorate|44.98|2|89.96

The annual price is $48.00, which equates to daily price of $0.13 ($48.00 / 365).

Unit price = days in the service period x daily price x number of licenses.

There are 19 days in service period of January 13, 2018 to January 31, 2018.

So the unit price is $2.47 (19 x 0.13 x 1)

There are 346 days in service period February 1, 2018 to January 12, 2019.

So the unit price is $44.98 (346 x 0.13 x 2)

## Suspend before 30 days

Your billing date is the 15th of each month. On January 13, you buy a new subscription with one license for $4 a month, and select annual billing. The January 15 license-based reconciliation file will contain the following billing line:

|Charge Start Date |Charge End Date |Charge Type |Unit Price |Quantity |Amount |
|       :---:      |    :---:       | :---:      |:---:      |:---:    |:---:  |
January 13, 2018|January 12, 2019|Prorate fees when purchase|48.00|1|48.00

On February 1, you suspend your subscription. The February 15 license-based reconciliation file will contain the following billing line:

|Charge Start Date |Charge End Date |Charge Type |Unit Price |Quantity |Amount |
|       :---:      |    :---:       | :---:      |:---:      |:---:    |:---:  |
January 13, 2018|January 12, 2019|Cancel Fee|-48.00|1|-48.00

## Suspend after 30 days

Your billing date is the 15th of each month. On January 13, you buy a new subscription with one license for $4/month and select annual billing. The January 15 license-based reconciliation file will contain the following billing line:

|Charge Start Date |Charge End Date |Charge Type |Unit Price |Quantity |Amount |
|       :---:      |    :---:       | :---:      |:---:      |:---:    |:---:  |
January 13, 2018|January 12, 2019|Prorate fees when buy|48.00|1|48.00

The February 15 license-based reconciliation file will not contain any billing lines for this subscription.
On March 1, you suspend your subscription. The March 15 license-based reconciliation file will contain the following billing line:

|Charge Start Date |Charge End Date |Charge Type |Unit Price |Quantity |Amount |
|       :---:      |    :---:       | :---:      |:---:      |:---:    |:---:  |
March 1, 2018|January 12, 2019|Cancel Fee|-41.34|1|-41.34

The annual price is $48.00, which equates to daily price of 0.13 (48.00 / 365).

Unit price = days in service period x daily price x number of licenses.

There are 318 days in service period March 1, 2018 to January 12, 2019.

So the unit price is $41.34 (318 x 0.13 x 1). Because this is a credit, the unit price is -$41.34.

## Suspend and reactivate

Your billing date is the 15th of each month. On January 13, you buy a new subscription with one license for $4 a month and select annual billing. The January 15 license-based reconciliation file will contain the following billing line:

|Charge Start Date |Charge End Date |Charge Type |Unit Price |Quantity |Amount |
|       :---:      |    :---:       | :---:      |:---:      |:---:    |:---:  |
January 13, 2018|January 12, 2019|Prorate fees when purchase|48.00|1|48.00

On February 1, you suspend your subscription. The February 15 license-based reconciliation file will contain the following billing line:

|Charge Start Date |Charge End Date |Charge Type |Unit Price |Quantity |Amount |
|       :---:      |    :---:       | :---:      |:---:      |:---:    |:---:  |
January 13, 2018|January 12, 2019|Cancel Fee|-48.00|1|-48.00

On March 1, you reactivate your subscription. The March 15 license-based reconciliation file will contain the following billing line:

|Charge Start Date |Charge End Date |Charge Type |Unit Price |Quantity |Amount |
|       :---:      |    :---:       | :---:      |:---:      |:---:    |:---:  |
March 1, 2018|January 12, 2019|Prorate fees when purchase|41.34|1|41.34

Annual price is 48.00, which equates to daily price of 0.13 (48.00/365).

Unit price = days in service period x daily price x number of licenses.

There are 318 days in service period March 1, 2018 – January 12, 2019.

So the unit price is $41.34 (318 x 0.13 x 1).

## Multiyear offers with annual billing

For multiyear offers with annual billing, charges start on the date of purchase and continue for one year.

(In the [example of multiyear billing](#example-of-multiyear-billing) that follows, in the first year charges start on March 20, 2020, and end a year later on March 19, 2021.)

Charges for the second year start one month earlier than the charge end date of the first year.

(In the example, charges for the second year start on February 20, 2021, one month before first year's charge end date of March 19, 2021.)

This annual billing process has a one-month difference between the subscription end date and charge end date for the third year. However, the subscription remains active until the subscription end date.

(In the example, the subscription end date of March 19, 2023 in the third year is one month after the charge end date of February 19, 2023.)

### Example of multiyear billing

For a 36-month offer purchased on March 20, 2020 shown in the tables that follow, the reconciliation file would be:

#### First year

|Subscription start date  |Subscription end date  |Charge start date  |Charge end date  |Charge type  |
|:-:|:-:|:-:|:-:|:-:|
|March 20, 2020|March 19, 2023|March 20, 2020|March 19, 2021|Prorate fees when purchased|

#### Second year

|Subscription start date  |Subscription end date  |Charge start date  |Charge end date  |Charge type  |
|:-:|:-:|:-:|:-:|:-:|
|March 20, 2020|March 19, 2023|February 20, 2021|February 19, 2022|Cycle Fee|

#### Third year

|Subscription start date  |Subscription end date  |Charge start date  |Charge end date  |Charge type  |
|:-:|:-:|:-:|:-:|:-:|
|March 20, 2020|March 19, 2023|February 20, 2022|February 19, 2023|Cycle fee|

## Renew with annual billing, convert to monthly billing

You can change the billing frequency of a subscription from annual to monthly or monthly to annual. To learn the details, see [Billing frequency changes](billing-frequency-changes.md).

In the following example, you renew a subscription with annual billing and then change the billing frequency to monthly. (To see an example of the reverse scenario, see [Change license quantity and convert from monthly to annual billing](common-billing-scenarios-monthly.md#change-license-quantity-and-convert-from-monthly-to-annual-billing))

- The billing date is the 15th of each month.

- On October 1, an existing subscription with annual billing renewed.

- On October 2, you converted from annual billing to monthly billing.

- The October 15 license-based reconciliation file has the following information:

|Sub Start|Sub End|Charge Start|Charge End|Charge Type|Unit Price|Qty|Amt|Bill Cycle|
|---|---|---|---|---|---|---|---|---|
|10/01/2020|10/01/2021|10/01/2020|9/30/2021|Prorate fee when renew|48.6|150|72,900.00|Annually|
|10/02/2020|10/02/2021|10/02/2020|11/01/2020|Prorate fees when convert away from current offering|4.05|150|6,075.00|Monthly|
|10/01/2020|10/01/2021|10/02/2020|9/30/2021|Prorate fees when convert to a new offering|-48.46|150|-72,700.30|Annually|

The subscription term resets and the new subscription start date corresponds to the date when the billing frequency was changed. As a consequence, the new **Charge Start Date** aligns with the new subscription anniversary date.
