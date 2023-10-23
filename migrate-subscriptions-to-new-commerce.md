---
title: Migrate subscriptions to new commerce
ms.topic: article
ms.date: 10/13/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Learn about new commerce experiences for migrating subscriptions.
author: brentserbus
ms.author: brserbus
ms.custom: intro-migration
---

# Migrate subscriptions to new commerce

**Appropriate roles**: Admin agent | Sales agent | Global admin

> [!NOTE]
> The new commerce experiences for license-based services include many new capabilities and are available to all Cloud Solution Provider (CSPs). For more information, see [new commerce experiences overview](new-commerce-license-based.md).

## New commerce migration

New commerce license-based product SKUs were made generally available on January 10th, 2022. Since then, various migration capabilities have been enabled to enable partners to make the transition more easily from tradition license-based (legacy) to new commerce product skus.

Since March 2022, most **Commercial** license-based product SKUs are *only* available in new commerce. In March 2022 many of these traditional license-based offers were deprecated, meaning they were no longer purchasable in the old system and only available via **New commerce**.

Partners can see these deprecated legacy offers in the old price lists flagged as DEPR, meaning they are only in new commerce. Partners with DEPR legacy offers cannot purchase new subscriptions, but their existing subscriptions continue to function and renew. Partners can verify the renewal date for the subscription to find out when it renews. Partners can see all price lists, both for legacy and new commerce license-based services, in the pricing and offers page in partner center. Partners need to be logged into the partner center to get these pricing files.

Migration APIs and Partner Center migration capabilities have been available since March 2022. Partners can find the mapping between traditional (legacy) and new commerce product SKUs in the legacy offer matrix **NCE Mapping** tab.

> [!NOTE]
> Since March 2022, all new commercial product SKUs are only made available via new commerce. Special segments such as education, nonprofit, and government offers are still only available in the traditional or legacy price list. There are not yet release dates for these special segments in new commerce. Partners that need these special segments can continue to transact by using the traditional or legacy offers.

## Mapping legacy offers to new commerce experience

Partners can get details about which legacy offers map to the new commerce product skus by reviewing the **NCE Mapping** tab in the new commerce offer matrix. This data in this tab looks similar to the core offer matrix data except there is an extra column Q, which includes the new commerce product sku ID that relates to the legacy offer. Partners can use this data to understand what the product skus that are available in new commerce. Partners can migrate their legacy subscriptions for **Migration enabled** offers using the migration capabilities in Partner Center's user interface or APIs. Other product skus can be acquired manually if they do not yet support migration. Partners should always consult the price lists to ensure the product sku they are purchasing is what they expect before transacting any offer or product sku in Partner Center.

To view a mapping matrix of legacy to new commerce experience offers and determine the correct migration mapping for a specific legacy offer, complete the following steps.

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select [**Pricing | Price lists**](https://partner.microsoft.com/dashboard/pricing/pricelist).
2. Download the legacy price sheet **License-based pricing**.
3. Download the legacy OLM file **Cloud Reseller offer matrix**, which has the mapping between legacy and new commerce in the first section for **License-based services** cloud reseller offer matrix.
4. Download the legacy price list through the Partner Center interface.
5. In the offer matrix file, select the **NCE Mapping** tab.
6. Map the Offer ID from the legacy price list to the Durable offer ID in the legacy offer matrix file in the NCE Mapping tab to determine the **Modern ProductID/SkuID** in column Q. Partners use the **Migration enabled** column to determine if the offer can be migrated using the Partner Center user experiences or APIs.

Not all offers can be migrated to NCE (such as legacy Azure Information Protection Premium P1 that does not have an equivalent corresponding offer in NCE).

## Manual migrations

Partners should use the Partner Center portal or APIs for migrations. However, partners can also manually purchase the new commerce version of the offer, ensure licenses are appropriately assigned and then cancel the legacy offer. This manual approach may be appropriate for some offers that have not yet been enabled for the migration paths. Partners should consult the price lists to verify pricing before any purchases.

Some legacy offers, although enabled for migration, need to be manually migrated. Here are some examples of popular offers that migration does not yet support.

| Legacy Offer Name | Legacy Offer ID | New commerce sku name | New commerce productId/skuId |
| ---- | ---- | ---- |---- |
| Azure Active Directory Premium P1 | 16c9f982-a827-4003-a88e-e75df1927f27 | Azure Active Directory Premium P1 | CFQ7TTC0LFLS/0002 |
| Intune | 51e95709-dc35-4780-9040-22278cb7c0e1 | Intune | CFQ7TTC0LCH4/0009 |
| Azure Information Protection Premium P1 | 648bf77b-1f0a-4911-8066-caf37d67dc72 | Azure Information Protection Premium P1 | CFQ7TTC0LH9J/0001 |
| Microsoft Intune | 73b45f83-fb4f-4cdc-a0d6-3d8792708f80 | Microsoft Intune | CFQ7TTC0LCH4/0009 |
| Intune per-device for Enterprise | 871e82d5-a046-4803-9825-69ba2f640c16 | Intune per-device for Enterprise | CFQ7TTC0LCH4/0004 |
| Intune Extra Storage | ced5f693-2d40-40ae-8848-9809ab1b0ee9 | Intune Extra Storage | CFQ7TTC0LCH4/0006 |
| Microsoft Teams Domestic Calling Plan for US and Canada | 60d2919e-427a-46c9-bd03-89cbad27d53f | Microsoft Teams Domestic Calling Plan Zone 1 | CFQ7TTC0LHXJ/0017 |

## Ineligible subscriptions

Not all subscriptions are eligible for migration at this time. The following categories of subscriptions are currently ineligible:

- Subscriptions within the first month of service since purchase (this check is only in Production; it isn't applied in Sandbox to aid effective testing).

- Subscriptions within the last 24 hours will only be blocked if **purchaseFullTerm** is false. 

- Migrations are allowed in the last 24 hours if **purchaseFullTerm** is true.

- Inactive subscriptions (no changes in service occur if a subscription is inactive)

- Trial subscriptions (no monetary benefit or implications; trials run their course in legacy)

- Subscriptions with active promotions (promotions in New commerce Experience (NCE) are independent of those promotions in legacy) and subscriptions that had promotions at initial purchase

- Subscriptions for Gov, Edu, or Nonprofit audiences (the mapping of qualified offers from legacy to NCE isn't supported)

- Subscriptions without a corresponding offer available in New commerce; check the New Commerce mapping sheet in the legacy offer list matrix file.

Migrations of the aforementioned mentioned subscriptions cannot be migrated. Subscriptions in the processing state cannot be migrated (such as migration for that subscription having already been initiated). Migration requests fail if the request includes an unsupported term and billing combo, an incomplete Partner Profile, or if the subscription has an invalid PartnerID on record.

## Suspending a legacy subscription during migration

Intended migration behavior is for the legacy subscription to only be suspended once a successful path to New commerce is provisioned for the subscription. This action  prevents loss of service if there are any blockers following a Partner initiating migration of a subscription. Additionally, no double billing occurs for both the legacy and New commerce subscription. Once migration has been initiated, billing for the legacy subscription stops to prevent any overlap with billing for the NCE subscription.

## Updating term length, term duration, billing frequency, and seat count upon migration

Migrated traditional license-based subscriptions preserve the remaining term, overall term length, billing frequency, and license counts unless the partner specifies otherwise. The capability to update these values during migration is available both in the Partner Center UX and via the **CreateMigration** API.

Partners can choose to change subscription attributes when migrating. Partners can change term duration, billing cycle, quantities or whether to continue their existing term or start a new one. Partners can also define a customer term end date, [aligning the end dates of their subscription to existing subscriptions](align-subscription-end-dates.md). Quantities for migrated subscriptions can be more, less or stay the same as the source subscription.
 
## Configuring term and billing frequency

Partners can change terms and billing frequencies when migrating.

Migrate with the same term length and end date from legacy (default)

- An annual legacy subscription migrated at month seven have five remaining months of the new commerce term left.

Begin a new term upon migration; can specify new term length (for example, three years, one year, one month)

- An annual legacy subscription migrated at month seven have the full new commerce term.

Switch term length (for example, annual to monthly) without beginning a new term upon migration

- Partner starts with an annual legacy subscription with an end term of February 10, 2022. The partner migrates to a monthly term on November 17, 2021. The migrated new commerce monthly subscription has an end term date of December 10, 2021. 

Billing frequency for the subscription may also be configured to other New commerce supported options, such as switching from annual to monthly billing.

## Cancelling subscriptions or decreasing licenses

Newly migrated subscriptions follow the same cancellation policy as new purchases in New commerce Experience.

## Scheduling migrations to new commerce

CSP partners can now schedule a migration for each legacy subscription in their sandbox and production environments.

Partners can use the new Partner Center API/BAM tool to schedule a migration upfront in their sandbox and in production environments.

Partners can also schedule a migration and [align the end dates](align-subscription-end-dates.md) with their existing NCE subscriptions to simplify asset management and billing.

API documents for the NCE migration scheduling feature are:

* [Cancel a new commerce migration](/partner-center/developer/cancel-a-new-commerce-migration-schedule)

* [Update a new commerce migration](/partner-center/developer/update-a-new-commerce-migration-schedule)

* [Get a new commerce migration](/partner-center/developer/get-a-new-commerce-migration-schedule)

* [Schedule a new commerce migration](/partner-center/developer/schedule-a-new-commerce-migration)

Partners can also use the BAM tool to schedule migration. Details of the schedule migration can be found at [New Commerce Experience Batch Migration Tool (BAM)](/samples/microsoft/partner-center-dotnet-samples/new-commerce-experience-batch-migration-tool-bam/).

## Migrating subscriptions with add-ons

As of March 2022, migration of subscriptions with add-ons has been enabled via the Partner Center APIs and UX.

A base subscription and all of its active add-ons must migrate to New commerce together, as a bundle. For a subscription with add-ons to be eligible for migration, the subscription and all its add-ons must have corresponding offers in New commerce. If a subscription has multiple add-ons, and one add-on is ineligible to migrate, the subscription and all add-ons cannot migrate. Post-migration, the migrated add-ons display as independent add-ons in NCE.

A partner can elect to make changes to the subscription terms, seat counts and billing frequency of the base subscription and the add-ons. Edited values are independent of each subscription (base subscription or add-on subscription) in the bundle being migrated. Migrations to new commerce without specified changes to quantity, billing frequency, term duration, and term end dates carry forward the legacy subscriptions’ properties.

Because both the base subscription and add-on subscription(s) are being migrated together as a bundle, the purchase of a new add-on subscription results in migration ineligibility for the next 30 days (post add-on purchase) of the whole bundle, even if the base subscription is greater than 30 days old. Each subscription in the bundle being migrated is validated for eligibility individually, and this includes the 30 day purchase check on each subscription. If one subscription is ineligible for migration, the entire bundle cannot migrate.

Partners can migrate add-ons independently (without the base subscription) to New commerce using the Partner Center UX or migration APIs.

## Promotions on migrated subscriptions

Migration doesn't affect an offer's eligibility to qualify for an available promotion. If the remaining term of the traditional license-based subscription isn't updated upon migration, and the New commerce Experience subscription is eligible for a promotion, the promotion is applied to the remainder of the NCE subscription's term.

For more information on promotions and identifying promotional eligibility, see [new commerce experience promotions](new-commerce-promotions.md).

## Expected migration timelines

The time a migration request takes to complete varies depending on factors such as attributes edited within the request and the quantity of requests being submitted at a time through Partner Center. Migration usually takes from zero to six hours, but in some cases migrations take up to 72 hours.

Partners can view the migration status in the Partner Center via the customer's Subscriptions page or by calling the [Get a new commerce subscription migration API](/partner-center/developer/get-new-commerce-migration).

When a migration request is submitted, the legacy subscription is set to a suspended state when the migration begins. A suspended legacy subscription with no corresponding NCE offer is visible on the subscription list. Additionally, the [Get a new commerce subscription migration API](/partner-center/developer/get-new-commerce-migration) request returns a migration status of "Failed" for migrations affected by this error. A partner's next steps are determined by the status of the legacy subscription:

- Legacy subscription still "Active": Legacy subscriptions that are still active in a failed migration state is allowed to be retried.  
- Legacy subscriptions that are "Suspended". Migration status of "Failed" where the legacy subscription is suspended are still being processed by the system, partners should let the migration as Microsoft diagnoses and correct the issue if needed during the 72 hour window. Microsoft corrects this issue within 72 hours of the initial migration request.

Migrations with "Failed" status with the legacy subscription in a suspended legacy subscription with no NCE subscription creation may take up to 72 hours from the time of the initial migration request for Microsoft to address the issue. Microsoft either corrects the error and completes migration (successfully creating the migration's corresponding NCE subscription) or reverts the migration after the 72 hours. If the migration is successfully completed by Microsoft within 72 hours, no further action is required by the partner. If the migration is reverted, the legacy subscription is set back to active again and partners can retry migration in this scenario.

During the period where the legacy subscription is suspended without a corresponding NCE offer created, no service loss occurs. The start of billing for the NCE subscription aligns with the date the New commerce subscription was created if Microsoft successfully completes migration. The created New commerce subscription retains the pricing and promotion specified at the time the migration request was created.

If the legacy subscription is reverted to a premigration state (effectively rolling back the migration request), billing of the legacy subscription resumes when the legacy subscription active again; no charges are made for the period where the legacy subscription was suspended without a corresponding NCE subscription created.

## Migration of SMB SKUs

Customers who have SMB SKUs are subject to a 300-seat limit when migrating their subscription from legacy to seat-based offers for new commerce.  

A partner can migrate a customer's SMB subscription with 200-seats successfully. But if the customer has another 200-seats on the same SMB SKU they want to migrate, the system blocks the migration because the transaction exceeds the 300-seat limit. In this case, the partner can adjust the seat count of the second SKU they would like to migrate from 200 to 100 (or lower to fall within the SMB seat limits) successfully.

If a partner submits a migration request at the same time for two SMB SKUs with 200 seats, one migration request goes through, and the other request fails. In this case, the partner would adjust the second SKU they would like to migrate from 200 to 100 (or lower to fall within the SMB seat limits) successfully.

## Migration history

Some migration details, such as start and completion time of migration, can be accessed using the new [Get a new commerce subscription migration API](/partner-center/developer/get-new-commerce-migration) and MigrationID field in the APIs. At Partner Center, the Subscription ID from which the new NCE subscription migrated from is visible at the top of the details page, which can be accessed when selecting the subscription on the customer's "Subscriptions" page.

Additionally, when clicking upon the migrated New commerce subscription in Partner Center (from the customer's subscriptions list), Partners are able to view a detailed log of migration events under the Migration Activity header that may include the status of the following migration activities:

- MigrationStarted: time migration request was submitted
- NewCommerceSubscriptionCreated: subscription created subscription ID
- NewCommerceSubscriptionProvisioned: NCE subscription's service has been provisioned
- MigrationCompleted: indicates migration was successful and NCE subscription can now be managed
- MigrationFailed: migration was unsuccessful; service access is retained with documented migration failure timelines are applicable

These migration events are also accessible via the [GetMigrationEvents API](/partner-center/developer/get-migration-events).

> [!NOTE]
> The ability  to see migration activity and events is a new feature. Any subscriptions migrated prior to June 22, 2022 won't have migration events recorded. This feature does not retroactively record migration events for subscriptions migrated prior to this date.
>

## Bulk migration

In the case where a Partner is trying to migrate a customer's eligible subscriptions to NCE, the outlined steps may be taken:

1. Select a customer to migrate the subscriptions.
1. Call the [Get a list of subscriptions](/partner-center/developer/get-a-list-of-subscriptions-by-order) API to receive a collection of the customer's subscriptions by customer-tenant-id. Query parameter for Order ID [is optional](/partner-center/developer/get-a-list-of-subscriptions-by-order).
1. Call the [Validate a subscription for migration API](/partner-center/developer/validate-subscription-for-migration) to check the migration eligibility.
1. Go through the collection of subscriptions and call the [Create a New commerce migration](/partner-center/developer/create-migration) API with each subscription-id. This action checks for migration eligibility and migrate the subscription if eligible.
1. To check for the migration eligibility call the [Get a New commerce subscription migration API](/partner-center/developer/get-new-commerce-migration) after going through the Subscription collection. Subscriptions that have been successfully migrated is populated with migratedFromSubscriptionID [attribute](/partner-center/developer/get-new-commerce-migration). The migrationId provided by the CreateMigration response facilitates tracking the progress of the migrations when used in the [Get a New commerce subscription migration API](/partner-center/developer/get-new-commerce-migration) API request. The unit of migration is a single subscription, but can be scaled to meet requirements of bulk migration scenarios.

## Mapping matrix of legacy offers to new commerce experience

To view a mapping matrix of legacy to new commerce experience offers and determine the correct migration mapping for a specific legacy offer, complete the steps below.

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Pricing**.
2. Download the legacy Price Sheet "License-based pricing".
3. Download the legacy OLM file "Cloud Reseller offer matrix," which has the mapping between legacy and new commerce in the first section for "License-based services" Cloud Reseller offer matrix.
4. Download the legacy Price List through the API or the Partner Center UX.
5. In the offer matrix file, select the tab that is named NCE Mapping.
6. Map the Offer ID from the legacy price list to the Durable offer ID in the legacy offer matrix file in the NCE Mapping tab to determine the Modern Product / SKU ID to find the "Modern Product ID / SKU ID" in column Q.

Not all offers are migratable to NCE (for example, offers such as legacy Azure Information Protection Premium P1 do not have an equivalent corresponding offer in NCE that can be migrated to).

## Migration Webhooks

Partner Center has made available webhooks to help API enabled partners to easily automate and track status of migrations. These migration webhooks are documented in the [webhooks documentation topic](/partner-center/developer/partner-center-webhooks).

- New Commerce Migration Completed 
- New Commerce Migration Created
- New Commerce Migration Failed
- New Commerce Migration Schedule Failed

## Migration, transition, conversion, and upgrade

In Partner Center, migration into New commerce refers to the moving of subscriptions from the traditional licensed-based commerce into the New commerce Experience. This may be confused with other action terms in Partner Center, such as transition, conversion, and upgrade.

Upgrades and conversions are considered types of subscription transitions.

[Transitions](create-a-new-subscription.md) are used to upgrade a customer's new commerce subscription to a target subscription or convert an NCE trial to a paid subscription. The key difference between transitions and migrations is that migrating a subscription moves it from traditional commerce to the equivalent offer in New commerce Experience. Unlike transitions, migration can't be utilized to change between unequal subscriptions (such as an upgrade or conversion action).

## Previous new commerce milestones

Effective March 10, 2022, legacy CSP commercial seat-based offers with equivalent new commerce offers are no longer be available for new orders on the legacy platform.

The price list contains a new value within the A, C, D, and U column, flagging the offers with "DEPR" for retired or no-longer-supported offers. As of March 1, 2022, the offer matrix (OLM) contains the list of offers that are retired in a new sheet entitled "Legacy Deprecated." On April 1, 2022, the price list includes offers that have been blocked for new purchases marked with "DEPR," and pricing continues to show up for these offers. Offers that are no longer available for purchase in legacy CSP won't be discoverable via the Partner Center catalog and won't be removed from the monthly CSP price lists.

Existing legacy subscriptions still have the options for the partner to add or remove seats, purchase add-ons, upgrade the subscription through the subscription term, and convert from trial to paid, regardless of the blocking of new commerce purchases from March 10, 2022.

Additionally, the error messaging of Create Order, Create Cart, and Update Cart APIs reflect available New commerce offers when a partner tries to purchase a blocked legacy offer. If an equivalent NCE offer is available for the blocked legacy offer that was attempted for purchase, the NCE offer's product ID, SKU ID, and availability ID is provided to the partner through the API message. Partners should realize that availabilities may expire, and the provided availability ID may no longer be valid if there's a wait time between the partner receiving the error message and attempting to purchase in New commerce.
