---
title: Earnings and payout reconciliation FAQ
ms.topic: faq
ms.date: 06/26/2023
description: Reconciliation frequently asked questions.
ms.service: partner-dashboard
ms.subservice: partnercenter-payouts
author: deeparamani
ms.author: deramani
---

# Earnings and payout reconciliation FAQ

**Appropriate roles**: Global Admin | Incentive Admin | Incentive User

This article answers frequently asked questions about reconciliation in the Microsoft Commerce Incentive program.

## Incentives

**Appropriate roles**: Account admin | Global Admin | Incentive admin | Incentive User

## What is the difference between Microsoft Commerce Incentives and other incentive programs?

Traditionally, every time there's a new incentive offer, it was set up as a separate program or as a lever in one of the existing programs. However, since October 1, 2021, any commercial incentive offers that are new or undergo rule changes are launched as engagements under Microsoft Commerce Incentives or as new levers under existing engagements (think of engagements as containers).

> [!NOTE]
> This does not apply to OEM (original equipment manufacturers) or any of the devices-based incentive programs yet.

Any transactions on new commerce will only be incentivized through a Microsoft Commerce Incentive engagement.

:::image type="content" source="media/reconciliation/existing-new.png" lightbox="media/reconciliation/existing-new.png" alt-text="Screenshot that shows existing programs versus new programs.":::

> [!NOTE]
>
> - Engagement names are unique and could change over time as they align around program refresh periods.
> - Lever names could be the same across engagements and could change.

## What are the different Partner Center pages that I need in order to access Microsoft Commerce Incentives?

| Access | Page |
|:-------|:-----|
| Make sure payout and tax profiles are up to date to continue receiving payments. Doing so keeps you in an enrolled state for Microsoft Commerce Incentives. | [Payout and tax profiles in Partner Center](incentives-create-and-manage-your-payout-and-tax-profiles.md)
| View all available engagements under Microsoft Commerce Incentives and your eligibility status to qualify for the engagement. | [MCI engagements overview and eligibility](mci-engagements.md)
| Understand the revenue/usage eligibility/ineligibility for Microsoft Commerce Incentives. | [Revenue summary in the Partner Center](revenue-summary.md)
| View aggregates and download earnings, payments and reconciliation details. | [Transaction history and Payments](transaction-history.md)
| View upcoming or sent payment orders and download details. | [Transaction history and Payments](transaction-history.md)

## How can I use the transaction history effectively to view and export Microsoft Commerce Incentives data?

Narrow the dataset within Microsoft Commerce Incentives by using the highlighted attributes to get a manageable sized export.

:::image type="content" source="media/reconciliation/mci-data-set.png" lightbox="media/reconciliation/mci-data-set.png" alt-text="Screenshot that shows Microsoft Commerce Incentive data set.":::

## How do I learn about the new incentive offers and understand my eligibility to participate?

Learn about existing and new incentive offers [at Partner Incentives](https://partner.microsoft.com/membership/partner-incentives).

For Microsoft Commerce Incentives, view all of the available engagements and your eligibility to participate by navigating to the Incentives workspace > Engagements Overview.

:::image type="content" source="media/reconciliation/mci-engagements.png" lightbox="media/reconciliation/mci-engagements.png" alt-text="Screenshot that shows Microsoft Commerce Incentive engagements.":::

You can check the Microsoft Commerce Incentives specific revenue eligibility using the Revenue Summary page in the Payouts workspace.

## I'm transacting on new commerce now. In which program can I expect to earn my incentives?

Any incentives for new commerce experiences will be available as engagements under Modern Commerce Incentives. When you meet the eligibility criteria, you'll start earning incentives.

> [!NOTE]
> Local/global campaigns are an exception to this rule.

## How do I understand why I'm not eligible for any of the engagements-based Microsoft Commerce Incentives?

1. Check if you're eligible for engagement by looking it up in the below screen. Green tick mark means you're eligible. If it's empty, then you aren't.

   :::image type="content" source="./media/payouts/faq-eligible.png" alt-text="Screenshot showing list of MCI engagements." lightbox="./media/payouts/faq-eligible.png":::

   > [!NOTE]
   > For some engagements, partner eligibility is custom controlled and if it does not show up on your screen, then it means you are not eligible.

2. In the event you're eligible for engagement, check the Revenue summary page for specific customer or transaction level ineligibility. [Revenue summary](./revenue-summary.md) outlines the possible ineligible reason codes the system generates today and next steps (if any).

   > [!NOTE]
   > Expanding the list of reason codes on the Revenue summary page will be an ongoing exercise.

3. Product eligibility for incentives isn't shown in the above pages. Refer to the product eligibility list in the product addendum section of each engagement by navigating through this guide <https://aka.ms/incentivesguide>

## Why do I see the same transaction marked as ineligible multiple times in the Revenue summary page? Why do I see ineligibility reason code for the same transaction in the Revenue Summary page when there's a valid earning for the same in the Transaction history download?

1. One usage or transaction record could be evaluated against multiple engagements and it's possible for various outcomes per engagement. We provide you ineligibility reasons at engagement level.

2. If usage or transaction record is ineligible for one or more engagement(s), you'll find entries in the Ineligible revenue download report. If usage or transaction record is eligible for one or more engagement(s), you'll find them in Transaction history download report.

| Sample                            | Engagement                                   | Eligibility outcome possibilities     | Outcome    | Outcome    | Outcome    |
|-----------------------------------|----------------------------------------------|---------------------------------------|------------|------------|------------|
| Transaction 1 for invoice G…..345 | Microsoft 365 new commerce CSP direct bill            | Eligible                              | Eligible   | Ineligible | Ineligible |
|                                   | Microsoft 365 Cust Add New Commerce CSP – Direct Bill | Eligible                              | Ineligible | Ineligible | Eligible   |

:::image type="content" source="./media/payouts/faq-transaction-flow.png" alt-text="Flowchart showing how to establish earnings and eligibility.":::

> [!IMPORTANT]
> The above numbers are used just for demonstration. Does not represent real incentive calculation.

## The basics of earning Azure consumption incentives

| **Partner associations**                                           | **Program**                   | **Role eligibility for Incentive** |
|--------------------------------------------------------------------|-------------------------------|------------------------------------|
|  Partner A as PAL.Owner. No other partners                         | Microsoft Commerce Incentives | Yes                                |
|                                                                    | Enterprise                    | No                                 |
|  Partner A as PAL.Contributor. No other partners                   | Microsoft Commerce Incentives | Yes                                |
|                                                                    | Enterprise                    | No                                 |
|  Partner A as PAL.Reader. No other partners                        | Microsoft Commerce Incentives | No                                 |
|                                                                    | Enterprise                    | No                                 |
| Partner A as Transacting partner of record (TPOR). No PAL partners | Microsoft Commerce Incentives | No                                 |
|                                                                    | Enterprise                    | Yes                                |
| Partner A as PAL. Owner or PAL. Contributor and Partner A as TPOR    | Microsoft Commerce Incentives | Yes                                |
|                                                                    | Enterprise                    | No                                 |
| Partner A as PAL. Owner or PAL. Contributor and Partner B as TPOR    | Microsoft Commerce Incentives | Yes (Partner A), No (Partner B)    |
|                                                                    | Enterprise                    | No (Partner A), Yes (Partner B)     |

For more, see [Learn how to associate as PAL](/azure/cost-management-billing/manage/link-partner-id).

## What is the fastest way to figure out if I have the right PAL role that will make me eligible for MCI consumption-based engagements?

Visit [Download reports](https://partner.microsoft.com/dashboard/insights/analytics/reports/export). This report provides daily Azure consumption insight within a week of associating your partner ID in the PAL link. The Azure usage report refreshes with daily Azure consumption within four days. Choose to download only the following columns in Azure Usage report to manage download size.

| **Azure Usage report**   | **What is it called in the incentive earnings download report** |
|--------------------------|-----------------------------------------------------------------|
| Month                    | transactionDate                                                 |
| SubscriptionId           | subscriptionId                                                  |
| PartnerID                | participantId                                                   |
| PartnerAttributionType   | -                                                               |
| AdminType                | -                                                               |
| ServiceLevel2            | workload                                                        |
| CustomerTpid             | customerId                                                      |
| CustomerTenantId         |                                                                 |
| CustomerName             | customerName                                                    |
| ACR_USD                  | transactionAmountUSD                                            |
| IsACRDuplicateAtMPNLevel | Not applicable                                                  |

For the subscription in question, if PartnerAttributionType reads "Partner Admin Link" and if the AdminType reads "Owner" or "Contributor" then your role is considered for consumption-based engagements in Microsoft Commerce incentives. To get the accurate Azure consumption revenue (ACR) value set IsACRDuplicateAtMPNLevel as 0. Set SubscriptionID, PartnerID and PartnerAttributionType="Partner Admin Link" as filters, AdminType as columns, Month as rows and ACR_USD as values.

:::image type="content" source="./media/reconciliation/scenario.png" alt-text="Screenshot of scenario as described":::

If the AdminType is **Reader**, you aren't eligible for incentives. If you provide managed services at subscription or resource level, reach out to your customer to ensure they have given you the right level of permission on resources. If the AdminType is "Owner" or "Contributor" and you have \>0 ACR_USD then it means you recognized, and the role is eligible for incentives. Incentives are also subject to more checks like partner, transaction and customer eligibility and if you've met everything you'll eventually earn incentives.

## I'm certain I associated myself as PAL but don't find the subscription in the Azure Usage report in Insights workspace?

If you've followed the steps outlined for the previous question and still don't find the subscriptionID, it's highly likely that there's no active Azure consumption happening for that subscription.

## How do I reconcile Azure consumption revenue (ACR) from the Azure Usage report with incentive earnings for Azure engagements?

1. Download the Azure usage report based on criteria specified in one of the above FAQs from the Insights workspace.

2. For Azure Growth engagements – Download the earning, transaction and payment details (Growth Levers) from the Payouts – Export page or Transaction history page. `totalTransactionAmountUSD` is the actual Azure consumption revenue. Single consumption records could become eligible to earn against multiple levers across different engagements, identify distinct amounts as recommended in the following figure. The figure demonstrates the pivots of key attributes from Usage and Earning, transaction and payment status details (Growth lever) reports using dummy data.

   :::image type="content" source="./media/reconciliation/pivot.png" lightbox="./media/reconciliation/pivot.png" alt-text="Screenshot of growth levers pivot data.":::

3. For other Azure consumption based engagements - Download the earnings, payments and transaction details from the Payouts – Export page. Since the same ACR could contribute to incentives against multiple engagements, identify distinct values as demonstrated in the following figure.

   :::image type="content" source="./media/reconciliation/distinct.png" lightbox="./media/reconciliation/distinct.png" alt-text="Screenshot of growth levers distinct function against data.":::

4. If the ACR value in the Transaction history report is still low, look for ineligibility reasons on the Payouts workspace Revenue summary page.

## How do I reconcile ACR incentive earnings for Azure growth engagements?

Azure growth engagement incentivizes the growth percentage on Azure consumption revenue. If the difference between the current quarter and the previous quarter Azure consumption revenue is positive, it's considered growth.

The following are three scenarios related to Azure growth engagements. See the corresponding experience summary for more information related to these scenarios.

| Scenario                                                                                                                                       | Experience                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Azure consumption for current quarter is greater than previous consumption for the lever, and other eligibility requirements are met           | Incentive earnings without consumption (also known as transactional details like customer, subscription) available in **Earnings, transaction, payment status details**. Download available from [Partner Center (microsoft.com)](https://partner.microsoft.com/dashboard/payouts/reports/incentiveexport?category=TransactionHistory).  Consumption (also known as transactional details) is available in **Earnings, transaction, payment status details (Growth levers)** along with earning information redundantly printed in each associated Azure consumption record. Download available from [Partner Center (microsoft.com)](https://partner.microsoft.com/dashboard/payouts/reports/incentiveexport?category=TransactionHistory)  |
| Azure consumption for current quarter is greater than previous all up for the lever, and at least one other eligibility requirement isn't met | No earnings will be generated; for missed eligibility, see the [Revenue summary page in Partner Center](https://partner.microsoft.com/dashboard/payouts/reports/incentiverevenue) to understand ineligibility reason. </br></br>Note: Earnings generated could be positive or negative at a subscription and/or agreement level depending whether there was growth or not. |
| Azure consumption for current quarter is same or less than previous all up for the lever                                                       | No earnings will be generated and won't cause negative payments/claw back                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |

To effectively reconcile growth engagements, download the **Earnings, transaction, payment status details** and the **Earnings, transaction, payment status details (Growth levers)** from [Partner Center (microsoft.com)](https://partner.microsoft.com/dashboard/payouts/reports/incentiveexport?category=TransactionHistory).

The reports can be co-related using the `earningID` field, which is available in both reports. To learn more about the export process, see the [Payouts export data page](payouts-enhanced-exports.md).

:::image type="content" source="./media/reconciliation/acr-reconciliation.png" lightbox="./media/reconciliation/acr-reconciliation.png" alt-text="Screenshot of ACR reconciliation.":::

1. **Earning, transaction, payment status details** download will have the following characteristics for growth engagements, and this is different from other programs/core engagement levers

    a. One unique earning per lever. This earning is derived from multiple Azure consumption records from the current and previous quarter (also known as transactions).

    b. Because earnings are derived from many transactions, this file won't contain information about customer, subscription, agreement number etc. They can be obtained by combining this report with the **Earning, transaction, payment status details(Growth levers**) by using Earning ID

    c. The following attributes can be used to derive the unique earnings, verify how they were computed and track payment status.
  
    :::image type="content" source="./media/reconciliation/sample-data.png" lightbox="./media/reconciliation/sample-data.png" alt-text="Screenshot of sample data export.":::

    d.  Attribute definitions

      - The **transactionAmount / transactionAmountUSD** attribute provides the growth amount (Total Current quarter consumption – Total Previous quarter consumption).

      - **earningAmount** / **earningAmountUSD** is the incentive amount calculated by multiplying growth amount with earning rate. **earningRate** is another column present in this report.

      - **baseline** is the total Azure consumption of the previous quarter. This column has been added to the end of the report in January 2023.

      - Current quarter consumption can be calculated by adding the baseline amount and growth amount.

1. **Earning, transaction, payment status details (Growth levers)** download will have the following characteristics for growth engagements and this file isn't required for other programs / core engagement levers.

    1. Every unique Azure consumption record that contributed to growth lever is available with customer, subscription, agreement number. Earning information (EarningID, EarningAmount and earningAmountUSD, paymentID, paymentStatus) is duplicated on every associated Azure consumption record as demonstrated below.

    :::image type="content" source="./media/reconciliation/growth-levers-export.png" lightbox="./media/reconciliation/growth-levers-export.png" alt-text="Screenshot of sample growth levers data export.":::

1. **Understand distinct earnings at customer level per lever**:
   1. Copy the following data, and paste it into a separate Microsoft Excel workbook: enrollmentParticipantID, customerName, customerID(optional), SubscriptionID, engagementname, levername, earningID, earningDate, earningAmountUSD.
   1. In Excel, select all of the data copied into the new sheet, then select **Data > Remove Duplicates**. This step ensures that only unique combinations of earnings per customer and subscription ID remain.
   1. Build a pivot table to view earnings by lever, customer, subscription (rows) organized by earning date (column).
 
1. **Understand distinct ACR per customer per month**
   1. Copy the following data, and paste it into a separate Microsoft Excel workbook: enrollmentParticipantID, customerName, customerID(optional), Subscription ID, transactionMonth, totalTransactionAmount.
  1. In Excel, select all data copied into the new sheet, then select **Data > Remove Duplicates**. This step ensures that only unique combinations of ACR per customer and subscription ID.
  1. Build a pivot table to view ACR by customer, subscription (rows) organized by transactionMonth (column)

## Marketplace

**Appropriate roles**: Account owner | Financial Contributor

### Roles and permissions

This table provides information on pages you can access for Marketplace:

| Reports/Pages | Account owner | Manager | Developer | Business contributor | Finance contributor | Marketer |
| --- | --- | --- | --- | --- | --- | --- |
| Acquisition report (including near real-time data) | Can view | Can view | No access | No access | Can view | No access |
| Feedback report/responses | Can view and send feedback | Can view and send feedback | Can view and send feedback | No access | No access | Can view and send feedback |
| Health report (including near real-time data) | Can view | Can view | Can view | Can view | No access | No access |
| Usage report | Can view | Can view | Can view | Can view | No access | No access |
| Payout account | Can update | No access | No access | No access | Can update | No access |
| Tax profile | Can update | No access | No access | No access | Can update | No access |
| Payout summary | Can view | No access | No access | No access | Can view | No access |

## Next steps

- [Payout and tax profiles in Partner Center](incentives-create-and-manage-your-payout-and-tax-profiles.md)
- [MCI engagements overview and eligibility](mci-engagements.md)
- [Revenue summary in the Partner Center](revenue-summary.md)
- [Transaction history and Payments](transaction-history.md)
- [Payouts export data page - Partner Center](payouts-enhanced-exports.md)
