---
title: Customers page for MCI engagements
description: Use the Customers page within the Microsoft Commerce Incentive (MCI) program Engagements section to manage customers.
author: Karthic83
ms.author: kashanum
ms.service: partner-dashboard
ms.subservice: partnercenter-incentives
ms.topic: how-to
ms.date: 10/01/2023
ms.custom: template-how-to
---

# Customers page for MCI engagements

**Appropriate roles**: Incentives admin | Incentives user

The **Customers** page shows customer associations that have applicable partner activity for build intent engagements.

Each engagement's **Customers** page displays all the customers who have provided consent to you for any previous engagement claim.

Engagements are sorted as:

- **Eligible**: Customers who are eligible for the engagement.
- **Ineligible**: Customers who are ineligible for the engagement. 
  
  Customers may be ineligible for engagements because:
  - They don't meet the eligibility criteria for the engagement, or
  - They have met the allowed limit on the number of active/allowed claims a given customer may have.

  The **Ineligible** tab doesn't show detail for partner activity type engagements that only allow customers to be nominated using their Microsoft Sales Experience (MSX) opportunity ID.

- **Complete**: Shows details about all customer claims that are in a terminal state and have no further action pending. These could be customer claims that have been completed, expired, cancelled or final rejected. To see details of completed claims, select the claim number in the **claim ID** column.

For any engagement, you must either [add a customer](#add-a-customer) or [claim a customer](#claim-a-customer), but not both.

## Add a customer

1. Select **Add customer** from the **Customers** page of the relevant engagement using the **Eligible** tab.
1. Provide a friendly name to the claim.
1. Select a Microsoft AI Cloud Partner Program location ID for the engagement, and then select **Next**.

   Only Microsoft AI Cloud Partner Program location IDs that are enrolled in the MCI program are eligible for MCI engagements. To select a location, your Partner Center user profile must have either **Incentives user** or **Incentives admin** permissions.

1. Select the customer ID type that you want to use to add the customer. You can then go on to provide the value for the ID type selected, then select **Next**.

   ID type options include: **domain name**, **tenant ID**, **TPID** (Top Parent ID), **Azure subscription ID**, or **MSX opportunity ID** (Microsoft Sales Experience opportunity ID).

   - For **fixed pay engagements**, you can nominate the customer by using the **domain name**, **tenant ID**, **TPID**, or **Azure subscription ID** based on the customer eligibility rules of the engagement. Each engagement may allow customers to be nominated using a subset of these IDs.

     If the customer is only eligible via their **TPID**, or only eligible via a **tenant ID** that isn't associated with their email domain, you must provide their eligible TPID or tenant ID.

   - For **variable pay engagements**, you can only nominate the customer by using the **MSX opportunity ID**.

   >[!NOTE]
   > **Eligibility checks**:
   > - If you provide a **domain name**, the system derives the tenant ID from the customer domain. It then runs a customer eligibility check.
   > - If you provide a **tenant ID**, **TPID**, **Azure subscription ID** or **MSX opportunity ID**, then customer eligibility checks are performed on the ID value provided in this step. The eligibility status of any given ID doesn't automatically cascade to any other IDs owned by that same customer.
   > - If you provide a **tenant ID**, the system checks whether it matches the customer's email domain. If a mismatch is found, the system asks you to provide a reason.

1. Choose the engagements for which you'd like to add the customer.

   The **Eligible** tab lists only engagements that can be selected for which both you and your customer are eligible. The **Ineligible** tab lists ineligible engagements along with reasons for ineligibility.

   For **variable pay engagements**, you may only select a single engagement in the flow. You must provide the number of hours that you would need to complete the engagement with the customer. The number of hours can't be updated after the **Add customer** flow has been completed.

   Select **Next**.

1. Provide the customer's email and contact information, along with contact information for your own company. Select **Next**.

1. Review the information.

   For **variable pay engagements**, review the proposed payout amount for conducting the engagement with the customer. This amount is based on the MSX opportunity ID, the number of hours provided, and the rules of the variable pay engagement.

1. After reviewing, select **Add customer**.

   After the customer has been added, you'll get confirmation, and the customer will appear on the respective **Customers** pages for the engagements selected in step 3.

## Claim a customer

The **Eligible** tab on the **Customers** page displays a list of customers who are known to you (the partner) through other active or completed engagements. You can initiate an engagement with any of those customers.

To claim a customer, use the following steps:

1. Select **Claim customer** from the **Action** column.

1. Provide a friendly name to the claim.

1. Choose a Microsoft AI Cloud Partner Program location ID for the engagement.

   Only the Microsoft AI Cloud Partner Program location IDs that are enrolled in the MCI program and that are eligible for this engagement will appear.
   Select **Next**.

1. Choose the engagements you'd like to add, then select **Next**.

1. Provide the customer's email and contact information, along with contact information for your own company, and then select **Next**.

1. Review the information and select **Add customer**.

   You'll get confirmation that the customer has been claimed.

## Ask for customer consent

If you want to conduct an engagement with a customer, you must ask the customer for consent, which is their agreement to participate in the engagement.

You'll have a defined number of days to obtain consent after adding or claiming the customer, based on the specific engagement.

To ask for customer consent:

1. Select **Send customer consent email** from the **Action** column.
2. Review and update, if necessary, the already provided customer's email and contact information, along with contact information for your own company,and then select **Next**.
3. Review the details and select **Send for consent**.

   Email is sent to the customer so they can accept or decline the engagement.
   - If you haven't received consent, you can send a reminder by selecting **Re-send email for customer consent** under the **Action** column.
   - If a customer was newly added but declines participation in the engagement or doesn't respond within the required time, they'll no longer appear on the **Customers** page for that engagement.

   After a customer provides consent, you must submit your claim [within the timeline defined per engagement type](mci-engagements-workshop.md#claim-expiration-timelines).

## Next steps

[Submit a workshop claim](./mci-engagements-workshop.md)

[MCI engagements overview and eligibility](./mci-engagements.md)

[Use these resources to help you get started with incentives](./incentives-get-started-intro.md)

[Determine your incentives program eligibility](./incentives-determined-your-program-eligibility.md)

[Enrollment and user management in the incentives program](./incentives-enroll.md)
