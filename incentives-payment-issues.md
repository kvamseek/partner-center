---
title: Troubleshooting payments and earnings issues
ms.topic: article
ms.date: 9/16/2022
description: Learn how to solve issues such as missing or incorrect earnings, eligibility problems, and how to reconcile your incentives earnings.
ms.service: partner-dashboard
ms.subservice: partnercenter-incentives
author: Karthic83
ms.author: kashanum
---

# Troubleshooting missing payments, incorrect earnings, and other issues

**Appropriate roles**: Incentives admin

This article can help you to resolve any earnings or payment issues in your incentives program. Subjects covered include timing of payments, checking your earnings eligibility, and the importance of setting up your payout and tax profiles properly.

## Who can create or update payout and tax profiles for my organization?

Users who have the *Incentives admin* role in Partner Center for the relevant incentive program and Microsoft AI Cloud Partner Program location can update and see the payout and tax profiles for the organization. For more information about roles in the Incentives workspace, see [Manage incentives](permissions-overview.md#manage-incentives).

## How long does it take for Microsoft to approve my pending payout and/or tax profiles?

Validation can take up to 48 hours. During this time, your profile status on the **Overview** page will appear as **Validating enrollment**. After the process is complete, the status will appear as either **Enrolled** if successful, or **Action Required – Update Payment and/or tax details** if necessary.

## How do I know if I've completed my payout and tax profile correctly?

The status of your enrollment is displayed on the **Overview** page. When you've finished creating your profiles, your status is **Validating enrollment**. After we've validated your information, your status changes to **Enrolled**. This status indicates that your payout and tax profile and your enrollment have been successfully completed.

## Why do I need to update my tax profile to use it with a new incentive program?

We pay out incentives from different locations depending on the incentive type. These differing locations may require more tax information, based on the incentive program rules, to process correctly.

## How can I delete a payment and/or tax profile?

Microsoft doesn't support deleting existing payout and tax profiles.

## My payment is missing or incorrect

Missing or incorrect payments often occur for the following reasons:

- **You may not be eligible.**  Earnings are available only if you meet Operational Eligibility Requirements, that is, enrolled to the respective program earning period.
- **You may not have met the requirements.**  Check to see whether you've met the eligibility and eligible revenue rules for the incentive you're looking for.

  To check your eligibility, use the following steps:

  1. Sign in to [Partner incentives](https://partner.microsoft.com/membership/partner-incentives).

  2. Scroll down to the documents for your program.

  3. Select the document link you want and then review the sections **Partner eligibility** and **Eligible revenue rules**.

- **Your payment profile may be incomplete.** Your incentive earnings start date is the first day of the month in which you've completed all of the eligibility requirements, including onboarding with payout and tax details. Earnings aren't available for the months prior to payout and tax completion. For example, if you complete all of the requirements during the month of April 2020, your earnings start date is April 1, 2020.

- **You may have an outstanding action**.  It could be that your incentives aren't being processed because there's an outstanding action pending from you.

  To view your outstanding actions, use the following steps:

  1. Sign in to [Partner incentives](https://partner.microsoft.com/membership/partner-incentives).

  2. Open the **Transaction history** page and look for any outstanding actions to be completed, such as **Pending Tax profile**, **Pending payment profile**, or **Pending tax invoice submission**.

If the preceding actions don't help and your payments are still missing or incorrect, contact [support](https://partner.microsoft.com/dashboard/v2/support/incentives/servicerequests?category=incentives).

## How can I reconcile my adjustments?

You can locate and reconcile your adjustments by downloading your earning and transaction details.

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Payouts**.

2. Select **Transaction history**, then apply the appropriate filters. (See the note below.)

3. After you've filtered your data, select **Start download** and then select **Export data**. Your data will open in a CSV file.

4. In the CSV file, go to Column P, **Earning type**.

5. Filter this column for **Adjustment-Rebate**. You can see the month of each adjustment in Column S.

    > [!IMPORTANT]
    > Adjustments applied to prior earnings periods will not be visible in the earnings for the month in which the adjustment was applied. Adjustments will always reflect in the earnings report for the month that the adjustment was applied to.
    >
    > For example, an adjustment for January 2019 earnings that was processed in September 2019 will not reflect in the earnings amount for September 2019. However, when the payment for September 2019 is received, it will include the adjustment for January 2019 that was applied in September. In this scenario, you would need to download the transaction details for January 2019 to see the adjustment that was applied.
    >
    > Keep this in mind when you set your date filters. As mentioned above, adjustments for previous periods will only be visible in the month the adjustment was applied to. Double check that the date range selected corresponds with the month of the adjustment you're attempting to locate. You may need to select **Clear all** to remove your filters, and then apply new ones.

## Why are my co-op claim payments made in two different currencies?

When co-op funds are earned from different Microsoft entities, payments are made in the local currency of each respective entity.

## Why was I paid in a currency other than my co-op claim currency?

Every incentive program has a bank profile that was created during setup. The currency specified in that profile is the currency in which you're paid.

## I don't see earnings for a certain period

If you don't see earnings for a period in which they're expected, it's usually for one of the following issues:

- **You may not be eligible.**  Earnings are available only if you meet Operational Eligibility Requirements, that is, enrolled in the respective program earning period.

- **Your payment profile may be incomplete.**  Your incentive earnings start date is the first day of the month in which you've completed all of the eligibility requirements, including onboarding with payout and tax details. Earnings aren't available for the months prior to payout and tax completion. For example, if you complete all of the requirements during the month of April 2020, your earnings start date is April 1, 2020.

If you have completed eligibility requirements on time, including onboarding with payout and tax details, and earnings are still missing, contact [support](https://partner.microsoft.com/dashboard/v2/support/incentives/servicerequests?category=incentives).

## My earnings are missing or incorrect

Missing or incorrect earnings may be caused by one of the following issues:

- **You may not have met the requirements.**  Check to see whether you've met the [eligibility](#my-payment-is-missing-or-incorrect) and eligible revenue rules for the incentive you're looking for.

- **There may be a discrepancy.**  If you meet both [program eligibility](incentives-determined-your-program-eligibility.md) and [earnings eligibility](incentives-confirm-your-earnings-eligibility.md) requirements and your earnings still appear to be incorrect, the following information may help you retrieve your data.

  - Earnings are displayed on both the **Transaction history** page and the **Payments** page. You can access both pages by selecting the **Payouts** workspace in the [Partner Center](https://partner.microsoft.com/dashboard/home).

  - Monthly earning amounts in the **Transaction history** view may not align with the payment amount received for a particular month. This is due to recalculations and adjustments for prior earning periods that are applied to future payments.

    For example, an adjustment for January 2019 earnings that was processed in September 2019 isn't reflected in the earnings amount for September 2019. However, when the payment for September 2019 is received, it includes the adjustment for January 2019 that was applied in September.

    In this scenario, you would need to download the transaction details to get a complete view of all earnings included in your payment. You can also go to the **Payments** view to download transactions for each payment.

### Transaction history

The **Transaction history** view shows earning and payment trends by month, earnings by status, and transaction details, along with the payment status for each transaction. Data is only visible for the programs and PartnerIDs for which you're an incentive user or admin.

### Payments

You can view payments for all programs and PartnerIDs using this view. Data is visible only for the programs and PartnerIDs for which you're an incentive user or admin. From this view, you can download remittance or view transaction details by payment.

|If you want to:|Do this:|
| ------ | :----------- |
| View your payment information by line, including earning and payment amounts in local currency  | See the **List of Payments** field   |
| Download a remittance letter   |  Select **Payment remittance**  |
| View transaction level details for a specific payment |  Select **View**  |
| Export transaction details to Excel  |  Select **Start download**, and then select **Export data**. All selected filters are applied to the exported data. After the status changes to Completed, select **Download** and follow the prompts to export the detailed transactions report. Refresh the page if the status isn't updated within five minutes.  |

### Missing or incorrect earnings and payments

If you can't find a payment or transaction details, check to see whether you've applied the correct filters. Because some program names have changed (for example, *CSP 1T Direct Partner* is now *CSP Direct Bill Partner*), you may need to use multiple selections.

If you still can't find your earnings or believe the earnings shown are incorrect, contact [Support](https://partner.microsoft.com/dashboard/v2/support/incentives/servicerequests?category=incentives).

## How do I reconcile my earnings?

If there's a discrepancy in your earnings, complete the following steps:

1. **Verify that you're eligible for earnings.**  Earnings are available only if you meet both [program eligibility](incentives-determined-your-program-eligibility.md) and [earnings eligibility](incentives-confirm-your-earnings-eligibility.md).

2. **Verify that your payment profile is complete.**  Your incentive earnings start date is the first day of the month in which you completed all of the eligibility requirements, including onboarding with payout and tax details. Earnings aren't available for the months prior to payout and tax completion. For example, if you complete all of the requirements during the month of April 2020, your earnings start date is April 1, 2020.

3. **Verify that you've met the requirements.**  Check to see whether you've met the [eligibility](#my-payment-is-missing-or-incorrect) and eligible revenue rules for your incentive program.

If these actions don't help and your earnings are still not reconciled, contact [Support](https://partner.microsoft.com/dashboard/v2/support/incentives/servicerequests?category=incentives).

## Where can I find my rates?

1. Sign in to [Partner incentives](https://partner.microsoft.com/membership/partner-incentives).

2. Scroll down to access the documents for your program.

3. Select the document link for the respective program.

4. In the document, refer to the section **Program structure and rates**.

## Next steps

- [Manage co-op claims](incentives-managing-co-op-claims.md)
