---
title: CSP regional authorization tenant consolidation
ms.topic: how-to
ms.date: 10/18/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-membership
description: Use these instructions to consolidate tenants for different country/regions. This article includes steps to migrate customer accounts and customer subscriptions.
author: brentserbus
ms.author: brserbus
robots: noindex,nofollow
---

# Instructions for CSP regional authorization tenant consolidation

**Applies to**: Partner Center | Partner Center for Microsoft Cloud for US Government

**Appropriate roles**: Global admin | Admin agent

> [!NOTE]
> Some information in this article relates to pre-released product, which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.

You can consolidate tenants for your business. Use these instructions to consolidate tenants for different country/regions.

> [!NOTE]
> You must be aware of all of the provisioned subscriptions and license counts for each of your customers in the account you are transitioning from. You will be re-provisioning those same exact subscriptions with the same license counts under the new central CSP account as part of the migration process. Use the export list feature to help create a list of customers to move over to the centralized tenant.  Once consolidation is complete, you can't revert to the previous tenant state. Customer action may also be required.

> [!IMPORTANT]
> There is a limit of 300 subscriptions per tenant.

## Prepare for migration

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) with the **transitioning** account (the one you'll transition to the new account), and review of all customers and all of the services provisioned for those customers.

2. Sign out of this account.

## Migrate customer accounts

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) with the **new** account (the one you're transitioning customers into) and select **Customers**.

2. Select **Request a reseller relationship**. You're presented with a default email message to send to your customers. This message contains a URL with the org ID unique to your new Partner Center account.

3. **Customer Action:** Ensure that each of the active customers you want to migrate visits this URL. When they open the URL, customers are prompted to sign in to the Office 365 portal. The customer signs in using the same Org ID that they use to access the Azure and Office 365 admin portals.

4. After they sign in, the Global Admin for the **customer account** is prompted to submit an agreement that gives delegated admin privileges to the new CSP account. If they agree, the customer selects the checkbox, and agrees to authorize the relationship.

The customers will appear in the partner's customer list after they've submitted the agreement, one by one.

## Migrating Office 365 and non-Azure usage-based subscriptions

1. Once your customer has signed the agreement, you can recreate their subscriptions under your Centralized Partner Tenant.

2. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

3. Open the company name for the customer you want to migrate.

4. Select **Add subscription**.

5. Add the correct subscriptions and license counts from the catalog. Verify with the information provided in the **Transitioning From** partner accounts.

   :::image type="content" source="media/regionalcustomer2.png" lightbox="media/regionalcustomer2.png" alt-text="customer list.":::

6. Select **Submit.**

   The services are now provided to the customer from the **transitioning to** partner account.

7. Repeat these steps to migrate subscriptions for all remaining customers.

Before proceeding to the next section, ensure all customer subscriptions existing under the **Transitioning From** partner accounts are reprovisioned under the **Transitioning To** partner account.

> [!NOTE]
> Partners must suspend subscriptions on the **transitioning from** Partner Tenant account in Partner Center the same day that those subscriptions are transitioned and set up under the **Transitioning To** Partner Tenant account in the Partner Center to ensure double billing does not occur. Support requests will be denied for credits due to any overlap in billing that occurs from not correctly disabling the **Transitioning From** subscriptions.

## Disabling the Office 365 subscriptions under the Transitioning From partner account

Disabling the CSP subscription under the **Transitioning From** partner accounts stops any future billing. You don't have to manually disable Azure subscriptions, because Azure subscriptions are automatically disabled during the migration process.

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) with the **transitioning from** CSP account and go to the customer list.

2. Open the customer with subscriptions to disable, and then select the first offer to disable.

3. Set the subscription to **suspended**, and then select **submit**.

   > [!NOTE]
   > Suspending the subscription ensures double billing does not occur.

   The subscription shows **suspended** on the subscriptions list.

4. Repeat these steps for all subscriptions under the customer. Verify all show **suspended.**

5. Select the next customer on the list and repeat the process of disabling all subscriptions.

## Migrating Azure usage-based subscriptions

Unlike the Office 365 CSP subscriptions, Azure, usage-based CSP subscriptions don't need to be migrated manually. Microsoft Azure Support will migrate the Azure subscriptions and all deployed services or resources from the **Transitioning From** CSP reseller accounts to the **transitioning to** CSP reseller account. There will be no disruption of service to the customer during this transition.

1. Ensure that the customer accounts that will have Azure subscriptions migrated have accepted the agreement to be associated with the new **transitioning to** CSP account.

2. You'll notify Microsoft of which customer accounts are ready to migrate, and provide those customer's company names.

3. Microsoft migrates the Azure usage-based subscriptions and notifies you when the migration is complete.

4. You need to confirm that the Azure subscription under the **transitioning from** CSP reseller account now is marked **suspended** in Partner Center under the customer subscriptions section.

5. Confirm that the Azure subscription under the **transitioning to** CSP reseller account now shows a status of **active** in Partner Center under the customer subscriptions section.

   > [!NOTE]
   > Disabling the subscriptions under the customer does not change the appearance of the customer in the Customers list. There is currently no option to remove customers from the list. Partners should avoid adding subscriptions back to these customers from their **transitioning from** account in the future.

6. Repeat these steps for all subscriptions under all of your customers to stop future charges on the **Transitioning From** accounts. The partner receives a final invoice. It has a credit unused days between the day of cancellation and the last day of the billing period. No future invoices will generate after that final billing period.

### Additional information

- Disabling the subscription from the **transitioning from** CSP account doesn't affect the end customer's service as long as the service was provisioned from the **Transitioning To** CSP account prior to disabling the subscription.

- Subscriptions can't be used by the customer and don't generate charges when suspended or canceled.

- There's currently no way to remove a customer completely from the **Customers** list.

  > [!NOTE]
  > Partners must suspend subscriptions on the **transitioning from** partner tenant account in Partner Center the same day those subscriptions are transitioned to and set up under the **transitioning to** account to ensure double billing does not occur. Microsoft will not support requests for credits due to any overlap in billing that occurs from not correctly setting the **transitioning from** subscriptions to suspended.

### Simplify migration using Export

Using the **Export Function**, you can capture the subscriptions you need to use in your new consolidated structure:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Select the customer name.

3. On the **Subscriptions** page, select **Export Subscriptions** to export details of subscriptions to an Excel file.

4. Use this list to recreate the subscriptions in your new consolidated tenant.

### API registration

For more information about API registration, see [Set up API access in Partner Center](/partner-center/develop/set-up-api-access-in-partner-center).

## Next steps

- [Regional markets and currencies where you can sell CSP offers](regional-authorization-overview.md)
