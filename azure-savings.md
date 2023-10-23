---
title: Azure savings plan billing
ms.topic: article
ms.date: 10/11/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-billing
description: Learn how to reconcile Azure savings plan.
author: sodeb
ms.author: sodeb
---

# Azure savings plan billing

Microsoft has introduced an [*Azure savings plan*](azure-savings-plan.md) for compute services. This plan enables customers to save money by committing to an hourly spend on Azure compute services for either one or three years. Upon receiving Microsoft’s invoices and reconciliation data, you can confirm that the consumption and costs align with the savings plan purchased. To enhance and simplify the reconciliation process, new attributes have been added to the daily rated usage data model:

| File  | New column | Description                                                         |
|-------|------------|-------------------------------------------------------------------------|
| Daily Rated Usage Reconciliation (closed and open periods) | BenefitID      | A unique identifier for each Azure Savings Plan.   |
|                                                            | BenefitOrderID | A unique identifier, which is similar to the Azure reservation order ID. You can match this with the `ReservationOrderID` on the invoice reconciliation to link the monthly cost to the daily charges. |
|       | BenefitType    | It has the value **“SavingsPlan”** to make it easy to find Azure Savings Plan transactions.                                 |

| API | New attribute | Description                                                                                    |
|-----|---------------|------------------------------------------------------------------------------------------------|
| Get invoice billed and unbilled commercial consumption line items | benefitId         | A unique identifier for each Azure Savings Plan.                |
|                                                                   | benefitOrderId    | A unique identifier, which is similar to the Azure reservation order ID. You can match this with the `ReservationOrderID` on the invoice reconciliation to link the monthly cost to the daily charges. |
|                                                                   | benefitType       | It has the value **“SavingsPlan”** to make it easy to find Azure Savings Plan transactions.     |

You can find the Azure Savings Plan charges by filtering the `BenefitType` attribute with the value “SavingsPlan.” The `BillingPreTaxTotal` attribute confirms that these transactions have zero charges. To compare the daily usage and charges with the costs of a savings plan, refer to the `BenefitOrderId` in the daily rated usage data and the `ReservationOrderId` in the invoice reconciliation data. On the other hand, pay-as-you-go charges are calculated at a standard rate, just like other Azure resources.

> [!NOTE]
> Only use the attributes listed here when comparing daily and monthly costs for a savings plan. Using other attributes may result in incorrect reconciliation.

> [!IMPORTANT]
> When savings plan discounts are in effect, Partner Earned Credits (PEC) are not given for the same transaction.

## Frequently asked questions

The following frequently asked questions provide more information about the reconciliation process.

### How do you check the savings plan usage in the Azure portal?

After buying an Azure Savings Plan, you can track how it is used daily in the Azure portal.

1. Check your customer view for the savings plan you bought them.
2. When you click on the name of the savings plan, you can see how it has been used in the last seven days, one month, three months, or a custom range of dates.

### How do you reconcile the charges with the utilization percentage?

Maximizing your savings and staying on top of your resource usage is essential when using Microsoft Azure. With the “Utilization over time” feature in the Azure portal, you can compare charges and make sure your plan to save money is working. Here’s how you can check your charges with Utilization Percentage:

1. Find the `BenefitOrderID` or `BenefitID` of savings plans that are less than 100% used. This will help you identify which plans you should be focusing on.
2. Look at `ResourceURI` in the daily rated usage data to find the virtual machines supported by the savings plans. Remember, an Azure plan’s benefit scope can be a resource, resource group, subscription, or shared across subscriptions.
3. Sort the transactions by UsageDate in the daily rated usage data. Transactions with the **“SavingsPlan”** `BenefitType` are covered by the savings plan and not charged for daily consumption. If there are no transactions with the **“Charge”** `BenefitType,` the virtual machines have no pay-as-you-go charges. 
4. Repeat steps 2 and 3 to ensure that plans with over commitments have pay-as-you-go charges.

By following these simple steps, you can easily reconcile your charges and make sure that you are getting the most out of your savings plan. 

### How do you verify the effective rate of a savings plan?

The effective rate of a savings plan is not shown in the daily rated usage file in the Partner Center. You can, however, find out in one of two ways:

1. Use amortized data from the Azure portal.
2. Calculate using the logic provided [below](#how-are-the-savings-plan-charges-calculated).

### How do you verify effective rate, unused utilization, and amortized data?

The amortized data shows the used and unused hours of a subscription, a resource group, or a specific resource in a savings plan.

You can download the amortized data for the savings plan at [Export cost data with an Azure Storage account SAS key](/azure/cost-management-billing/costs/export-cost-data-storage-account-sas-key).

1. Find the `resourceId` of the savings plan once you have the data. The attributes in this file are different from those in the Partner Center daily rated usage data. The attribute mapping is shown in [attribute mapping table](#amortized-and-daily-rated-usage-data-attribute-mapping).
2. After that, sort the transactions by the `date`, which you can make even easier by filtering on a specific date. You’ll see charges for the virtual machines, which you can easily confirm by making sure there are no transactions with the “SavingsPlan” value in the `pricingModel` attribute.
3. Check the `effectivePrice` and `costInBillingCurrency` attributes to find out the effective rate and charges.
4. You can also check to see if any of the savings plans are underutilized by taking the following steps:
    1. Use the `productOrderId` attribute to filter by the order ID of the Azure savings plan.
    2. Then look for the “UnusedBenefits” value in the `chargeType` attribute.
    3. Any number higher than zero in the `quantity` attribute is the number of unused hours for that day.

### How are the savings plan charges calculated?

Let’s look at a simple example to understand how savings plan costs are calculated. Say you bought a USD 1/hour savings plan and a USD 4/hour pay-as-you-go virtual machine for your customer Contoso.

**Consider the following scenario:** 

- When you sign up for a savings plan, you get a 50% discount on the pay-as-you-go rate (the exact discount may vary). This means that you will only pay USD 2 per hour instead of USD 4.
- If the VM runs for one hour, the savings plan will only cover **1 (A) / 2 (C) = 0.5 (S)** hours. 
- The remaining **(1 - S) = 0.5 (P)** hours will be charged at the pay-as-you-go rate, adding up to a total charge of **USD 3 (K)** for that hour. To break it down, the savings plan commitment is **USD 1 (H),** and the pay-as-you-go costs are **USD 0.5 (P) \* 4 (B) = USD 2 (J).**
- If the VM runs for 24 hours, the daily charge for the VM will be **USD 72 (L),** calculated as **24 (E) \* 3 (K).**

Note that the savings plan charges are billed monthly or upfront, depending on your billing plan. This way, you can always track how much you spend on your savings plan.

This table shows various conditions and how they were used to extrapolate the charges for one day.

| Committed \$\$ / hour (A)        | PAYG rate / hour (B)                   | Savings plan rate / hour (C)       | Savings plan discount % (D) | Total hours per day (E) | Hours covered by the pay-as-you-go charges per day (F) | Hours covered by the savings plan per day (G) |
|--------------------------------------|--------------------------------------------|----------------------------------------|---------------------------------|-----------------------------|------------------------------------------------------------|---------------------------------------------------|
| 1 **(A)**                            | 4 **(B)**                                  | 2 **(C)**                              | 0.50 **(D)**                    | 24 **(E)**                  | 12 **(E - G)**                                             | 12 **(E \* S)**                                   |
| Let's say the VM is used for 1 hour. | | | | Extrapolate it for the whole day—24 hours. | | |  
|                                      | **Savings Plan**                           | **Pay-As-You-Go**                      | **Total**                       |                             |                                                            |                                                   |
| Quantity                             | 0.5 **(A / C) ==\> S**                     | 0.5 **(1 - S) ==\> P**                 | 1                               | 96 **(B \* E ==\> M)**      |                                                            |                                                   |
| Effective cost with savings plan     | 1 **(H)**                                  | 2  **[B \* [1 - (A / C)]]** **==\> J** | 3 **(H + J)** **==\> K**       | 72  **(K \* E) ==\> L**     | 48 **(B \* F) ==\> Q**                                            | **0**                                             |
| Savings                              | 1                                          | 0                                      | 1                               | 24 **(M - L) ==\> N**       |                                                            |                                                   |
| Savings %                            |                                            |                                        |                                 | 25%  **(N / M)**            |                                                            |                                                   |

Look at a real-life example to get a better idea of how much your savings plan is going to cost you:

- Let’s say your savings plan commitment is **USD 0.01/hour,** and the pay-as-you-go rate for the virtual machine (VM) is **USD 0.3264/hour.**
- Sign up for a one-year savings plan and enjoy a **31.43% discount,** reducing your hourly rate to **USD 0.22381248**.
- If the VM runs for one hour, the savings plan will cover **0.04468026 (S) hours**, calculated as **0.01 (A) / 0.22381248 (C)**.
- The remaining **0.95531973 (P) hours** will be charged at the pay-as-you-go rate and will cost **USD 0.31181636 (J)**, calculated as **0.95531973 (P) \* 0.3264 (B)**.
- So, the total cost for an hour will be **USD 0.32181636 (K). To break it down,** the savings plan commitment is **USD 0.01 (H), plus** the pay-as-you-go cost is **USD 0.31181636 (J).**
- If the VM runs for 24 hours, the daily charge will be **USD 7.72359270 (L)**, calculated as **24 (E) \* 0.32181636 (K)**.

> [!IMPORTANT]
> The daily rated usage data displays your pay-as-you-go charges for each day that your virtual machine runs. For the above example, if your virtual machine runs 24 hours a day, the daily rated usage data will show a usage quantity of 22.9276737383009 and a cost of 7.48359270818142.

By using this data, you can learn more about how you use things and find places where you might be able to cut costs. Whether running a single virtual machine or managing a large-scale deployment, having access to this information is essential for staying on top of your usage and managing your costs effectively.

This table shows various conditions and how they were used to extrapolate the charges for one day.

| Committed \$\$ / hour (A)        | Pay-As-You-Go rate / hour (B)           | Savings plan rate / hour (C) | Savings plan discount % (D) | Total hours per day (E)  | Hours covered by the pay-as-you-go charges per day (F) | Hours covered by the savings plan per day (G) |
|--------------------------------------|---------------------------------------------|----------------------------------|---------------------------------|------------------------------|------------------------------------------------------------|---------------------------------------------------|
| 0.01 **(A)**                         | 0.3264 **(B)**                              | 0.22381248 **(C)**               | 0.3143 **(D)**                  | 24 **(E)**                   | 22.92767373 **(E - G) ==\> F**                                | 1.07232626 **(E \* S) ==\> G**                       |
| Let's say the VM is used for 1 hour. | | | | Extrapolate it for the whole day—24 hours. | | |
|                                      | **Savings Plan**                            | **Pay-As-You-Go**                | **Total**                       |                              |                                                            |                                                   |
| Quantity                             | 0.04468026 **(A / C) ==\> S**                  | 0.95531973  **(1 - S) ==\> P**      | 1                               | 7.8336  **(B \* E ==\> M)**     |                                                            |                                                   |
| Effective cost with a savings plan   | 0.01 **(H)**                                | 0.31181636  **(B \* P) ==\> J**     | 0.32181636  **(H + J)** **==\> K** | 7.72359270  **(K \* E) ==\> L** | 7.48359270  **(B \* F) ==\> Q**                               | 0                                                 |
| Savings                              |                                             |                                  |                                 | 0.11000729  **(M - L) ==\> N**  |                                                            |                                                   |
| Savings %                            |                                             |                                  |                                 | 1.40%  **(N / M)**           |                                                            |                                                   |

### Amortized and daily rated usage data attribute mapping

In the table below, you can see how the amortized data and daily usage data match up. Some of the information may not match, but you can still use it to check and confirm the charges and usage for the savings plan.

| Amortized data attribute | Partner Center daily rated data attribute |
|------------------------------|-----------------------------------------------|
| invoiceId                    | InvoiceNumber                                 |
| previousInvoiceId            | N/A                                           |
| billingAccountId             | N/A                                           |
| billingAccountName           | N/A                                           |
| billingProfileId             | N/A                                           |
| billingProfileName           | N/A                                           |
| invoiceSectionId             | N/A                                           |
| invoiceSectionName           | N/A                                           |
| partnerTenantId              | PartnerId                                     |
| partnerName                  | PartnerName                                   |
| resellerName                 | N/A                                           |
| resellerMpnId                | N/A                                           |
| customerTenantId             | CustomerId                                    |
| customerName                 | CustomerName                                  |
| costCenter                   | N/A                                           |
| billingPeriodEndDate         | N/A                                           |
| billingPeriodStartDate       | N/A                                           |
| servicePeriodEndDate         | ChargeStartDate                               |
| servicePeriodStartDate       | ChargeEndDate                                 |
| date                         | UsageDate                                     |
| serviceFamily                | N/A                                           |
| productOrderId               | BenefitOrderId                                |
| productOrderName             | N/A                                           |
| consumedService              | ConsumedService                               |
| meterId                      | MeterId                                       |
| meterName                    | MeterName                                     |
| meterCategory                | MeterCategory                                 |
| meterSubCategory             | MeterSubCategory                              |
| meterRegion                  | MeterRegion                                   |
| ProductId                    | ProductId + SkuId                             |
| ProductName                  | ProductName                                   |
| SubscriptionId               | EntitlementId                                 |
| subscriptionName             | EntitlementDescription                        |
| publisherType                | N/A                                           |
| publisherId                  | PublisherId                                   |
| publisherName                | PublisherName                                 |
| resourceGroupName            | ResourceGroup                                 |
| ResourceId                   | ResourceURI                                   |
| resourceLocation             | ResourceLocation                              |
| location                     |                                               |
| effectivePrice               | EffectiveUnitPrice                            |
| quantity                     | Quantity                                      |
| unitOfMeasure                | UnitType                                      |
| chargeType                   | N/A                                           |
| billingCurrency              | BillingCurrency                               |
| pricingCurrency              | PricingCurrency                               |
| costInBillingCurrency        | PricingPreTaxTotal                            |
| costInPricingCurrency        | PricingCurrency                               |
| costInUsd                    | N/A                                           |
| paygCostInBillingCurrency    | N/A                                           |
| paygCostInUsd                | N/A                                           |
| exchangeRatePricingToBilling | PCToBCExchangeRate                            |
| exchangeRateDate             | PCToBCExchangeRateDate                        |
| isAzureCreditEligible        | N/A                                           |
| serviceInfo1                 | ServiceInfo1                                  |
| serviceInfo2                 | ServiceInfo2                                  |
| additionalInfo               | AdditionalInfo                                |
| tags                         | Tags                                          |
| partnerEarnedCreditRate      | PartnerEarnedCreditPercentage                 |
| partnerEarnedCreditApplied   | N/A                                           |
| PayGPrice                    | N/A                                           |
| frequency                    | N/A                                           |
| term                         | N/A                                           |
| reservationId                | N/A                                           |
| reservationName              | N/A                                           |
| pricingModel                 | BenefitType                                   |
| unitPrice                    | UnitPrice                                     |
| benefitId                    | BenefitId                                     |
| benefitName                  | N/A                                           |
| provider                     | N/A                                           |

## Next steps

- Learn about [purchasing the Azure plan](purchase-azure-plan.md)
- See the [price list for the new commerce experience in CSP](azure-plan-price-list.md)
