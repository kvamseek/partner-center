---
title: Azure plan billing - invoice & recon files
ms.topic: article
ms.date: 7/18/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-billing
description: Learn how to access and understand the invoice and reconciliation file structure related to billing for the Azure plan.
author: sodeb
ms.author: sodeb
---

# New commerce experience in CSP—Azure billing

**Appropriate roles**: Admin agent | Billing admin | Global admin

This article explains the invoice and reconciliation file structure for Azure plan billing, and how to access and understand it.

Azure plan billing is simple, with a single billing date and calendar-month billing periods.

## Access your invoices and reconciliation files

The Global admin or Billing admin for your company receives an email when an invoice is ready to view.

To access the invoice and reconciliation file, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Billing**.

2. Select the tab **Recurring and one-time purchases** for the currency you're interested in.

   :::image type="content" source="media/azure-plan-billing/billing-history.png" alt-text="Screenshot showing billing history at Partner Center.":::

3. Select **Invoices** or **Reconciliation**.

   To view historical invoices and reconciliation files, see **Billing history** at the bottom of the page.

## About usage data

- Azure plan is the root or top-level container for usage. All usage is tied back to a single Azure plan.

- Within a plan, there will be one or more Azure subscriptions. These subscriptions are containers used for resource management and deployment.

- Within a subscription, resource groups add resources to a group, and every resource is deployed to one resource group.

- Examples of resources include virtual machines and storage accounts.

- Resource emit meters: Meters are measurements of consumption of a resource, and one resource may emit usage for multiple meters. Meters are identified by a ProductId, SKUId, and AvailabilityId.

### Hierarchy of subscription resource groups and metering

**Azure account (tenant):**

- Subscription A
  - ResourceGroup 1
    - Virtual machine (resource)
      - Compute meter
    - Virtual network (resource)
      - No billing meter

  - ResourceGroup 2
    - Virtual machine (resource)
      - Computer meter
    - Premium SSD-managed disk (resource)
      - Storage capacity meter
      - Storage operations meter

- Subscription B
  - ResourceGroup 1
    - Azure SQL (resource)
      - DTU meter
    - VPN Gateway (resource)
      - VPN gateway meter

  - ResourceGroup 2
    - Virtual Network Interface (resource)
      - No billing meter

## About your invoice

See the following numbers in the image.

1. Invoice is available by the eighth of each month.

2. Partners have 60 days to remit payment.

3. The billing period is a calendar month, for example June 1 to 30.

4. Charges are net of adjustments (amount is net of "Partner Earned Credit").

5. Review the invoice reconciliation file and daily rated usage file for more billing details.

   :::image type="content" source="media/azure-plan-billing/invoice.png" lightbox="media/azure-plan-billing/invoice.png" alt-text="Microsoft invoice example.":::

## About your invoice reconciliation file

- The reconciliation file would have one billing line if the meter received a discount or credit (like a tiered discount or partner credit for services managed) during the month. The column `PriceAdjusmentDescription` refers to the discount or earned credit, and the effective unit price will show the discounted price.

- If no resources for a meter qualify for a discount or partner-earned credit, the effective unit price is the retail price (the unit price).


## Read the daily usage file

- Subscription meters under an Azure plan are rated and cumulated on a daily basis.

- **Partner earned credit for services managed** is determined and applied on a daily basis.

- Every subscription meter has a row for every day of the month in which there was consumption.

- In the following image:

  - Meter qualified for **Partner earned credit for services managed** from 7/1 - 7/3 (Note the effective unit price is the retail price less partner earned credit.

  - Meter didn't qualify for **Partner earned credit for services managed** from 7/4 - 7/7 (Note the effective unit price is the retail price).

  - Meter qualified for **Partner earned credit for services managed** from 7/8 - 7/31 (Note the effective unit price is the retail price less partner earned credit).

   :::image type="content" source="media/azure-plan-billing/partner-earned-credit-final.png" lightbox="media/azure-plan-billing/partner-earned-credit-final.png" alt-text="Reconciliation file example.":::

## Azure reservations

If purchasing [Azure reservations](azure-reservations.md) through an Azure plan, you can choose either one-time or monthly billing.

## Azure savings plans

If purchasing [Azure savings plans](azure-savings-plan.md) through an Azure plan, you can choose either one-time or monthly billing. Learn more about how [billing and reconciliation](azure-savings.md) work for Azure savings plans.

## How do you calculate the costs of a product with both subscription and pay-as-you-go charges?

Read this to learn more about how [costs are calculated](common-billing-scenarios-onetime-recurring.md#how-do-you-calculate-the-costs-of-a-product-with-both-subscription-and-pay-as-you-go-charges) for a product with a subscription fee for a fixed unit and pay-as-you-go charges for the overage.

## Effective unit price calculation for Azure plan pay-as-you-go

The effective unit price is calculated at the meter level (as opposed to the resource level), and is adjusted daily according to meter usage.

We calculate the effective unit price using the following three factors:

- Consumption, which is monitored daily throughout the billing cycle
- Billable cost for the meter
- Tiering (if applicable)

The effective unit price may fluctuate because we monitor consumption daily throughout the open billing period. The final price for that billing period will be available after we close the billing period.

### Find out whether your meter uses tiered pricing

If you don't know whether your meter uses tiered pricing, use the procedure below to find out.

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Pricing**.

2. Select **Azure plan pricing**.

3. Locate your meter by ID, and then download your pricing data.

### Sample calculation

The table below gives an example of how we calculate the effective unit price during the open period.

In the table, the following values apply:

- **UP** = Unit price of the resource/hour = 0.868

- **BCU** = Billable consumption unit for the meter

- **BC** = Billable cost for the meter = BCU \* UP \* 0.85, which reflects an adjustment for the 15% PEC discount. We then use the lower limit of the function to limit the value to two digits after the decimal point, in order to charge the minimum amount.

- **Effective unit price** = BCU/BC

> [!NOTE]
> The meter in this example does not have tiers in pricing or other discounts—the Effective Unit Price factors in discount percentages and other adjustments.

| Date | BCU (Billable consumption unit) | BC (Billable cost) | Effective unit price |
| ------ | ----------- | ----------- | ----------- |
| 3-Aug | 29 | 21.39 | 0.737586206896552 |
| 10-Aug | 210.950039 | 155.63 | 0.737757626107858 |
| 25-Aug | 555.950039 | 410.17 | 0.737782122900436 |

## Next steps

- [Purchasing the Azure plan](purchase-azure-plan.md).
- [Price list for the new commerce experience in CSP](azure-plan-price-list.md).
