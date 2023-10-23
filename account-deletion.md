---
title: Deletion of a partner account or partner location
description: Microsoft partners can request deletion of a Partner Center account or location.  
author: sharath-satish-msft
ms.author: shsatish
ms.service: partner-dashboard
ms.subservice: partnercenter-account
ms.topic: conceptual 
ms.date: 05/04/2023
ms.custom: template-concept
---

# Delete your partner global or local account

**Appropriate roles**: Global administrator

This article explains how to delete a Partner Center account.

>[!IMPORTANT]
>
>- If your partner account does not have any active benefits and the Partner ID is not associated to other program enrollments, then you can delete your partner account from the Identifiers page.
>- If you can't delete your account, submit a support request.

## Delete a Microsoft AI Cloud Partner Program account

Eligibility:

- You have the Global administrator role.
- Your partner account should have **no active benefits**.
- The Partner ID shouldn't be associated to any other program enrollments such as Cloud Solution Provider program, Commercial marketplace program or Surface program.

### Steps to follow

1. Sign into **Partner Center** with global administrator credentials.
1. In the upper right, select **Settings** (gear-icon) and then the **Account settings** workspace.
1. Select the **Identifiers** page from left navigation.
1. In the **Microsoft AI Cloud Partner Program** tab, select the partner account row you want to delete.
1. Select the **Delete account** option as shown in the screenshot.

   :::image type="content" source="media/account-deletion/delete-account.png" lightbox="media/account-deletion/delete-account-lightbox.png" alt-text="Screenshot of delete account option.":::

   > [!NOTE]
   >
   > - Deleting a partner global account also deletes all the locations account added to it.
   > - If you only have one location account with your partner global account, you cannot delete the last remaining location account.

1. From the panel, select the reason for deletion. Select **Next**.
1. From the next panel, enter the Partner ID in the input box and select **Delete account**.

   :::image type="content" source="media/account-deletion/delete-account-confirmation.png" lightbox="media/account-deletion/delete-account-confirmation-lightbox.png" alt-text="Screenshot of delete account confirmation.":::

## Submit a support request

You can request the deletion of a Partner Center account if you can't delete it yourself.

You can create a support request to delete a Partner Center [global account](https://partner.microsoft.com/support/?stage=2&topicid=cff8890b-b8cb-ba22-6e16-c972dc201fde) or [location account](https://partner.microsoft.com/support/?stage=2&topicid=b2aaafc9-0468-ef8d-4e73-bf9669310f4c).

- The support team reviews the potential consequences of deleting the account.
- You receive a brief overview of the potential consequences of deleting the account.
- You provide written notice that you have read the assessment of potential consequences of deleting account and that you agree to proceed with account deletion.  

## Risks and recommendations

The following table describes some of the possible effects of deleting an account and some recommended actions.

> [!IMPORTANT]
> It is strongly recommended that you carefully assess the potential consequences of account deletion and that you perform the recommended actions and any other necessary actions prior to submitting a request to delete an account.

| Affected area | Effect | Recommended actions |
|---|---|---|
| Partner requirements | All data pertaining to customer subscriptions in which the location is listed as the digital partner of record (DPOR), transacting partner, or partner of record are lost. As a result, the partner global account (PGA) might no longer qualify for incentives, competency requirements, and other program requirements in which the organization has enrolled.| Update all customer subscriptions in which the location is listed as the DPOR, transacting partner, or partner of record to a new partner ID. Doing so ensures that the PGA account isn't affected.|
| Incentives | After the location is deleted, all incentives tied to the location immediately cease to accrue. | All customer subscriptions to which the location is tied as the DPOR, transacting partner, or partner of record should be updated to a new location ID. The new location ID should enroll in the incentive programs to receive incentives. |
| Cloud Solution Provider (CSP) | The reseller ID listed in the CSP account is no longer valid, thus affecting terms and agreements. In addition, data pertaining to the CSP transactions is no longer reported to the Microsoft AI Cloud Partner Program/PGA account. | The reseller ID in which the location is listed should be updated to a new reseller ID. |
| Co-sell | All referrals tied to the location are lost. Microsoft can't retrieve referrals after they're deleted. Live solutions should be remapped to a new partner location. | Verify whether there are any live offers. Live offers should be recreated under a new partner ID. The partner should create referrals under the new location account prior to deleting account.|
| Marketplace | Deleting a partner location doesn't delete the seller ID. |  Submit a separate support request to the Marketplace support team to remove the seller ID. <br> Confirm the following items for the seller ID:<br> - There are no active offers. <br> - There are no pending payouts. <br> - Existing offers have been remapped to a new partner location account.

## Next steps

- Learn more about [Partner Center account management](partner-center-account-setup.md)
- [Get help and contact support](report-problems-with-partner-center.md)

