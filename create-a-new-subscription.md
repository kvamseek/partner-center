---
title: Create customer subscriptions in Partner Center
ms.topic: how-to
ms.date: 10/19/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Learn how to sell subscriptions to your customers for products published by Microsoft and for SaaS products published by ISVs.
author: migolova
ms.author: migolova
---

# Manage customer subscriptions

**Applies to**: Partner Center | Partner Center for Microsoft Cloud for US Government

**Appropriate roles**: Admin agent | Billing admin | Global admin | Helpdesk agent | Sales agent

After you've created a record of your customer in Partner Center, you can sell subscriptions to products in the catalog to that customer.

The subscriptions that you can sell are:

- Products published by Microsoft
- Software as a service (SaaS) products published by independent software vendors (ISVs) to the commercial marketplace ([Azure Marketplace](https://azuremarketplace.microsoft.com/marketplace)).

> [!NOTE]
> You can only sell customer subscriptions if you're a *direct-bill partner* or an *indirect provider*. If you're an *indirect reseller*, contact your indirect provider. For more information, see [Which CSP model is best for me?](csp-overview.md).

Some offers are limited to one subscription per customer. To see a list of which offers are restricted, go to the Partner Center **Price lists** page.

As a partner in the Cloud Solution Provider (CSP) program, you can purchase *license-based* or *metered* SaaS subscriptions from ISV publishers within Partner Center. You can purchase any license-based or metered SaaS offer that the ISV publisher has made available to you, including any [exclusive offers](csp-commercial-marketplace-discover.md#exclusive-offers) to which you have access. To purchase or manage other commercial marketplace offers from ISVs (such as usage-based offers that involve Azure applications, containers, or VMs), you must go to the [Azure portal](https://portal.azure.com/).

> [!NOTE]
> All dates and times in Partner Center are given in Coordinated Universal Time (UTC). UTC can differ from your local time by up to 24 hours.

## Create a new subscription

To create a new subscription, use the following steps:

1. From the [Partner Center](https://partner.microsoft.com/dashboard/home), select **Customers** and then select a customer from the customer list.

2. Select **Add subscription**.

3. The **Online Services** tab shows all available marketplace SaaS offers.

   To see only certain types of subscriptions, use the filters:

   | Filter | Setting |
   |-|-|
   | Publisher | Select **Microsoft** to see only offers from Microsoft.<br>Select **Partner** to see commercial marketplace products published by ISVs. |
   | Billing type | Select the type of subscription billing that you want to use: **License** or **Usage**.<br>For information that can help you to decide between the monthly and annual billing, see [Partner Center billing](billing-basics.md). |
   | Category | Select **Enterprise**, **Small business**, or **Trial**.<br>For information about trial subscriptions, see [Offer your customers trials of Microsoft products](offer-your-customers-trials-of-microsoft-products.md). |

4. Select the product subscriptions that you want to purchase for your customer. The products that you see depend on the customer segment (for example, education or government) and the filters you've applied.

   Some marketplace offers might not always be available to particular customers or CSP partners. Possible reasons include:
   - The customer already has a subscription to that product and is allowed only one.
   - The customer's subscription might have been suspended. (In this case, you can reactivate the subscription rather than purchase a new one.)

   For ISV SaaS offers, there might be several reasons why an offer isn't available:

   - The ISV might not support the customer's billing country or region.
   - The ISV might have chosen not to make the offer available through the CSP program.
   - The ISV might have made the offer [exclusive](csp-commercial-marketplace-discover.md#exclusive-offers) to certain CSP partners.
   - The ISV offer might not be transactable through Partner Center (for example, containers or some usage-based offers).

5. For each subscription that you want to add, enter the number of licenses (if needed) and then select **Add to cart**.

6. When you're finished adding subscriptions, select **Review** and review your order.

   > [!IMPORTANT]
   > Partners are required to attest to the following:
   >
   > "I confirm that my organization is acting as an Indirect Partner when choosing a Reseller and as a Direct Partner in the absence of selecting a reseller"

   EU/EFTA laws state that partners transacting in those countries/regions must declare other resellers associated within a transaction. The following rules apply:
   - An initial reseller must be chosen prior to any other resellers.
   - Other resellers won't be entitled to any extra incentives, offers, and so on.
   - Other sellers entered will be validated to ensure that the correct PartnerID has been entered where applicable, and that the reseller has signed the Microsoft Partner Agreement (MPA).
   - A maximum of five other resellers may be entered as part of the transaction.

7. If you're an indirect provider, select the indirect reseller that you want to associate with this customer's subscriptions from the list.

8. Select **Review**.

9. Select **Submit**.

10. To add subscriptions, select **Add Products**.

11. When you're finished adding customer information and have purchased the required subscriptions, select **Done**.

12. When you're ready to purchase these subscriptions, select **Buy**.

   > [!IMPORTANT]
   > Partners should be aware of certain constraints and limits for the number of subscriptions per customer. More information about these limits can be found in the [Azure AD service limits and restrictions documentation](/azure/active-directory/enterprise-users/directory-service-limits-restrictions).

## Offers with unique constraints

### Multi-geo capabilities add-on
The multi-geo capabilities add-on has a unique seat constraint, different from other New Commerce license-based offers. 

To purchase this add-on, the partner must purchase a quantity of Multi-geo licenses equal to or greater than 5% of the base seats the customer owns (across all prerequisite base offers). For example, Customer A has 400 seats across all compatible base subscriptions. The multi-geo capabilities add-on purchase the partner makes on their behalf must be at least 20 seats (5% of 400). 

To learn more about multi-geo capabilities and their benefits, visit [Multi-Geo Capabilities in Microsoft 365](https://microsoft.com/en-us/microsoft-365/business/multi-geo-capabilities). 

### After you buy a subscription

After you buy a subscription for a customer:

- You can review or edit the subscription by selecting the subscription name from that customer's **Subscriptions** page. From there you can select add-on licenses if any are available, change the quantity of licenses, or suspend the subscription.

- *For ISV SaaS (license-based and metered) subscriptions:* You'll receive a link to the ISV publisher's site. This link should help you to complete account setup or the deployment of the customer's subscription.

   > [!NOTE]
   > Neither you nor your customer will receive an email with instructions to complete account setup or provisioning for this type of ISV subscription.

- If your subscription comes with a 30-day free trial, the free trial period is applied automatically. As a partner in the CSP program, you can't waive the free trial period on offers that you purchase for customers.

   After the free trial period ends, the subscription converts to paid status and the subscription term begins. The subscription autorenews according to the same schedule.

## Update subscriptions with add-ons (traditional license-based commerce)

In traditional license-based commerce, to purchase an add-on, the customer must first have an active base subscription; you can't purchase add-ons through the catalog. In New Commerce, add-ons can be purchased through the catalog, and the below steps don't apply. See [New Commerce add-ons](/partner-center/new-commerce-add-ons) for more info.

To update a traditional license-based commerce subscription with an add-on, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Choose a customer from the list.

3. Choose the subscription that you want to manage.

4. Below the **Status** section is a list of available add-ons for the subscription. Update the number of licenses for each required add-on.

5. Select **Submit**.

- Only direct-bill partners and indirect providers can purchase add-ons through Partner Center.
- Only eligible add-ons are displayed, based on the base requirements and regional availability.
- Suspending the base subscription also suspends any associated add-ons.
- Start dates for add-ons align to the base subscription. Charges are calculated from the charge start date and charge end date with prorated charges in the first invoice. For more information, see [Partner Center billing](billing-basics.md).
- For more information about pricing and offers, see the Cloud Reseller Offer Matrix on the Partner Center **Pricing and offers** page.

## Increase or decrease licenses in new commerce license-based subscriptions

The number of licenses on a subscription can be *increased* at any time. Billing adjustments appear on the next invoice and reconciliation file.

The number of licenses on a subscription can be *decreased* only within the first seven days of when the seats were added to the subscription (except where otherwise required by law), whether it was at the initial purchase, on renewal, or at midterm.

To increase or decrease the number of licenses (within the first seven days), use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Choose a customer from the list.

3. Select the subscription that you want to update.

4. On the details page, enter the new total number of licenses that you want in the **Quantity** section.

   If you try to decrease the license count after seven days, you get an error message.

5. Select **Submit**.

> [!NOTE]
> In both cases of license reduction, you'll be refunded the full amount minus the prorated amount for the days that you used the subscription. (Proration is calculated daily.)
>
> If more than seven days have elapsed since the subscription order was placed or more licenses were added, the license count can't be decreased until the next cancellation window at renewal.

> [!NOTE]
> Partners may experience errors when updating a subscription more than 1,200 times. Partners can resolve this by acquiring a second subscription for the given product SKU if necessary. Partners can align the term of a newly acquired subscription to existing subscriptions if needed. Partners needing further assistance can contact partner support.

### View seats available for reduction

You can view the number of seats that can be reduced on a subscription at Partner Center or by using the [Get a Subscription by ID](/partner-center/develop/get-a-subscription-by-id) API.

To view the number of seats that can be reduced on a subscription, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Choose a customer from the list.

3. Select the subscription that you want to check.

4. Select **View licenses to reduce**

- If the number of seats *can* be reduced, you'll see the total quantity listed with a breakdown of the number of licenses and the associated timestamp by when the number of licenses can be reduced.
- If the number of seats *can't* be reduced, you'll see a message that says so.

## Upgrade for new commerce license-based subscriptions

For new commerce, *upgrade* means going from one paid subscription to another paid subscription on a higher tier. (Downgrades aren't supported.) New commerce paid-to-paid upgrades enable a customer to upgrade immediately from the current SKU to a SKU with added services.

You can select the subscription to which you want to upgrade when you're configuring license counts. You can select a new subscription or you can select an existing subscription that's eligible for upgrade.

Upgrades can be of two types: [full upgrades](#full-upgrades) and [partial upgrades](#partial-upgrades).

> [!NOTE]
> Cancellation windows are not applied to upgrades, so changes can't be made after they're submitted.

> [!NOTE]
> You can schedule an upgrade for the end of a term or start an upgrade mid-term.
>
> Starting a midterm upgrade removes any upgrades that may have been scheduled.
>
> You can only start upgrades from active subscriptions.

To upgrade a subscription, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Choose a customer from the list.

3. Select the subscription that you want to upgrade.

   If a subscription is eligible for an upgrade, an **Upgrade now** link is visible. If there isn't an **Upgrade now** link, upgrades aren't available.

4. Select **Upgrade now** and choose an upgrade.

   You can upgrade to a new subscription or select an existing subscription (if available) from the **Destination subscription** dropdown list. You won't be able to select a destination subscription if the subscription is within cancellation window, term durations don't match, or the term end date is before the current term end date.

5. Select the term duration, the billing frequency, and the number of licenses that you want to upgrade.

   The number of licenses that you select determines whether the upgrade is a [full upgrade](#full-upgrades) or a [partial upgrade](#partial-upgrades).

6. Select **Submit**.

> [!NOTE]
> Not every new commerce product SKU can be upgraded. Some expected upgrade paths aren't yet supported. The following table has examples of upgrades that you might expect to be supported but aren't.

### Upgrades that aren't currently supported

| **Upgraded-from SKU** | **Upgrade-to SKU** |
|:-----------   |:-----------   |
| Enterprise Mobility + Security E3 | Enterprise Mobility + Security E5 |
| Enterprise Mobility + Security E5 | Microsoft 365 E5 or Microsoft 365 E5 without Audio Conferencing |
| Universal Print | Microsoft 365 E3, Microsoft 365 E3 - Unattended License, Microsoft 365 E5, or Microsoft 365 E5 without Audio Conferencing |
| Windows 10/11 Enterprise E3 | Microsoft 365 E5 or Microsoft 365 E5 without Audio Conferencing |
| Windows 10/11 Enterprise E3 VDA | Microsoft 365 E5 or Microsoft 365 E5 without Audio Conferencing |
| Windows 10/11 Enterprise E5 | Microsoft 365 E5 or Microsoft 365 E5 without Audio Conferencing |
| Dynamics 365 Human Resources Self Service | Dynamics 365 Team Members |
| Project Online Essentials | Dynamics 365 Team Members |
| Microsoft Defender for Endpoint P1 | Microsoft Defender for Endpoint P2 |

### Remove duplicated licenses after an upgrade

Duplicate (redundant) licenses may be created when purchasing a higher-level SKU in the following cases:

- The upgrade is unsupported
- The online services licenses don't need a prerequisite or a Microsoft base compatible product to purchase the higher SKU

When a customer has redundant licenses after an upgrade, the partner should submit a support ticket requesting that the redundant licenses should be canceled. This support ticket should be requested within the first two billing cycles from when the upgraded license was invoiced.  

### Two-to-one upgrades

If you have two separate standalone SKUs and want to upgrade them both together to one higher value SKU, use this  process:

1. To identify upgrade options, partners should refer to the offers matrix. For each standalone SKU, you'll need to do the following:
   1. Look up the product.
   2. Find its ProductId/SkuId combination.
   3. View the **ProductSkuConversion** column to see available Upgrade options.
2. Upgrade the first subscription (one-to-one) using Partner Center or transition API. This creates a new upgraded subscription.
3. Use the [transition API](./developer/transition-a-new-commerce-subscription.md#post-transition) to transition the second subscription into the already purchased, upgraded subscription.

Once completed, you'll have gone from two separate SKUs to just one higher value SKU.

### Full upgrades

A *full upgrade* is an in-place upgrade, which means that all licenses or additional licenses are being upgraded.

The subscription ID remains the same during a full upgrade, and licenses are assigned automatically.

Licenses must be manually assigned if the customer purchased the destination SKU from another partner or channel. You'll see a warning in Partner Center stating that the licenses need to be manually assigned if that is the case.

During a full upgrade:

- All seats or additional seats are upgraded.
- The subscription ID stays the same.
- All seats or additional seats are transferred to the new subscription.
- If the customer is upgrading to an existing subscription, seats are added only to the existing subscription and keep the term duration and billing frequency.

### Partial upgrades

*Partial upgrades* enable a partner to designate some licenses from one SKU to another.

- Upgrade functionality in traditional license-based subscriptions only enabled every license to be upgraded.

- Upgrade functionality in new commerce subscriptions enables a partner to move some licenses at their convenience. That gives the partner more control over upgrades.

During a partial upgrade:

- An upgrade is defined as partial if the upgrade license count is less than the initial subscription's license count.
- A new subscription that is created during a partial upgrade has the same term end dates as the subscription that the upgrade originated from (that is, the subscriptions are *coterminous* and end at the same time).
- You'll have two subscriptions: an existing one and a new one.

### Seat reassignment

Seat reassignment is always attempted during full upgrades, even if license transfer without reassignment is passed through the API.

Seat reassignment must be completed manually during partial upgrades or if there are multiples of the same SKU.

### Scheduled changes for managing new commerce license-based subscription renewals

> [!NOTE]
> New commerce experiences for license-based services have many new capabilities and are available to all Cloud Solution Provider (CSPs). For more information, see [New commerce experience for license-based services](new-commerce-license-based.md).

You can schedule subscription changes for the end of a term instead of immediately.

Examples of changes that can be scheduled include:

- Subscription upgrades
- License increases or reductions
- Changes to billing term
- Changes to billing frequency
- Changes to coterminous date

You can only schedule changes if:

- A subscription is active
- Auto-renew is on

To schedule a new change to occur at renewal, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Choose a customer from the list.

3. Select the subscription that you want to manage.

4. Select **Manage Renewal**.

5. Make changes to the subscription and select **Okay**.

6. Select **Submit**.

You can access **Manage Renewal** to view, update, or remove an existing scheduled change.

> [!NOTE]
> By default, trial subscriptions convert to the equivalent paid SKU at the end of the trial period.
>
> For scheduled SKU upgrades, if the license quantity doesn't change, user license reassignment is automatic. Otherwise, license reassignment must be done manually.

Saved scheduled changes are deleted if you make any of the following midterm changes:

- Cancel a subscription
- Turn off autorenew
- Change a quantity
- Upgrade a SKU
- Convert a trial

## Switch billing plans

Find out what changes can be made in the middle of your term for each term duration and billing frequency combination (also referred to as billing plan) in the new commerce experience.

### Change only billing frequency (scheduled change)

You can change just the billing frequency at Partner Center if the subscription qualifies. The change isn't immediate: it takes effect in the next billing cycle. This won't reset the billing term.

> [!NOTE]
> Partner Center doesn't support switching to an "upfront" billing plan at midterm, which is **only supported at the time of purchase**. ("Upfront" billing is when the billing term is the same as the billing plan (Examples: annual term and annual billing plan or monthly term and monthly billing plan).)

#### Eligible changes

|**Term duration**|**Billing frequency**|**Billing frequency changes accepted**|
|-----------------|---------------------|--------------------------------------|
|Triennial        |Monthly              |Yes (Monthly to Annual)               |
|Triennial        |Triennial (Upfront)  |None                                  |
|Triennial        |Annual               |Yes (Annual to Monthly)               |
|Annual           |Annual (Upfront)     |None                                  |
|Annual           |Monthly              |None                                  |
|Monthly          |Monthly (Upfront)    |None                                  |

To change billing frequency, use the following steps:

1. Go to the customer's subscription page and select the subscription that you want to change.

2. Select **Manage billing frequency**.

3. A side panel displays the current billing frequency and a dropdown list that has the options for changing the frequency.

4. Select a new billing frequency.

### Change billing frequency along with billing term and other fields (immediate change)

You can move to a higher term mid-term, but changing to a lower term isn't accepted. If you change your term, you can also update the billing frequency. Please note in some cases the Triennial term may not be supported for a particular product and sku and won't show as an available term within the dropdown.

#### Eligible changes

| **Term duration** | **Billing frequency** | **Term duration changes accepted**               | **Billing frequency changes accepted**                                                                                         |
| ----------------- | --------------------- | ------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------ |
| Triennial         | Monthly               | None                                             | None                                                                                                                           |
| Triennial         | Triennial (Upfront)   | None                                             | None                                                                                                                           |
| Triennial         | Annual                | None                                             | None                                                                                                                           |
| Annual            | Annual (Upfront)      | Yes (Annual to Triennial)                        | Yes (Triennial term with Monthly, Triennial, or Annual billing plan)                                                           |
| Annual            | Monthly               | Yes (Annual to Triennial)                        | Yes (Triennial term with Monthly, Triennial, or Annual billing plan)                                                           |
| Monthly           | Monthly (Upfront)     | Yes (Monthly to Annual, or Monthly to Triennial) | Yes (Annual term with Monthly or Annual billing plan), or (Triennial term with Monthly, Triennial or Annual billing plan) |

To change billing term and billing frequency:

1. Go to the customer's subscription page and select the subscription that you want to change.

2. Change the term duration by selecting an option in the dropdown list.

3. In the next dropdown list that opens, select a different billing frequency.

4. Select **Submit**.

> [!NOTE]
> If you change the term or billing plan of a subscription with a promotion, you may lose your promotion if the new billing plan or term are not eligible for that promotion. If the updated subscription is eligible for a different promotion, it will automatically apply.

## Suspend a subscription

You can suspend a subscription and you can resume a subscription.

If there's nonpayment from a customer, you can suspend a subscription to immediately block the customer's access.

You can suspend and resume a subscription without a cancellation as long as the subscription is reactivated by the end the subscription's term.

A customer with a suspended subscription can't sign in or access files and services until the subscription is resumed, but an admin can access data.

All data related to the subscription is deleted if the subscription isn't reactivated by the end of the subscription's term.

The partner continues to be billed during suspension (unlike in legacy), and customer access to services can be restored when payment resumes.

Resuming a subscription immediately restores a customer's access to a subscription's services as long as the suspension is reversed within the subscription's term.

You can reverse a suspension at Partner Center or using the APIs.

> [!NOTE]
> Suspending a new commerce subscription will turn off auto-renew. Partners that remove a suspension should be sure to turn auto-renew back on if desired.

To suspend a subscription at Partner Center, use the following steps:

1. Go to the customer's subscription page and select the subscription that you want to suspend.

2. Select **Suspend**.

3. In the pop-up dialog, select **OK**.

## Cancel a subscription

You can cancel a subscription if a customer requests it.

### Cancel new commerce license-based subscriptions

For new commerce offers, partners can cancel their subscription with a prorated refund within the first *seven days* of any term, except where otherwise required by law.

After the seven day window has closed, cancellation is no longer available. The partner is billed for the full term even if the customer stops paying for or using the subscription (applicable to any billing plan).

When a cancellation is complete:

- The customer immediately loses access to the service.
- The service can't be restored.
- The state for the subscription is unrecoverable.

To cancel a new commerce license-based subscription, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Choose a customer from the list.

3. Find the subscription that you want to cancel.

4. In the **Status** section, select **Cancel Subscription**.

5. Select **Submit**.

If you encounter issues during a transaction, you may submit a support ticket in Partner Center here . Microsoft will respond with further guidance.  Examples of issues you may want to submit:

- Incorrect purchases
- Duplicate orders
- Changes in partner/billing agreements (for example, a customer moving from one CSP to another CSP)
- Technical issues which can be traced back to Microsoft's systems or services
  
> [!IMPORTANT]
> Since October 2021, the refund policy for ISV SaaS offers has changed for both monthly and annual offers. It is now a full refund and not prorated.

### Cancel traditional license-based subscriptions

You can cancel traditional license-based SaaS subscriptions from ISV publishers within the Partner Center [commercial marketplace](csp-commercial-marketplace-overview.md). As long as you cancel within the [cancellation period](/marketplace/refund-policies#software-as-a-service-saas-offers), you'll receive a full refund.

For ISV offers billed *monthly*:

- If you cancel less than 24 hours after you place the order, you'll receive a full credit on the next invoice.

- If you cancel more than 24 hours after you place the order, the cancellation will be scheduled to occur at renewal.

For offers billed *annually*:

- If you cancel less than 14 days after you place the order, you'll receive a full credit on the next invoice.

- If you cancel more than 14 days after you place the order, the cancellation will be scheduled to occur at renewal.

To cancel a traditional license-based subscription, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Choose a customer from the list.

3. Find the subscription that you want to cancel.

4. In the **Status** column, select **Cancel**. Then select **Submit**.

5. If a dialog appears, fill out any relevant details and select **Submit**.

6. To confirm the cancellation, select **Yes, cancel**.

> [!NOTE]
> You can also choose to cancel an Azure Marketplace subscription by using APIs. To do so, see [Cancel an Azure Marketplace subscription](/partner-center/develop/cancel-an-azure-marketplace-subscription).

## Subscription renewals

> [!NOTE]
> The new commerce experiences for license-based services include many new capabilities and are available to all Cloud Solution Provider (CSPs). For more information, see [new commerce experiences overview](new-commerce-license-based.md).

By default, active subscriptions are set to automatically renew when the subscription period expires. For [subscriptions to commercial marketplace products](csp-commercial-marketplace-overview.md), or new commerce subscriptions, you can optionally choose not to automatically renew the subscription.

To stop an active subscription from automatically renewing, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Choose a customer from the list.

3. Select **Subscriptions**.

   Any license-based subscriptions that you've purchased for the customer appear in a list.

4. On the subscription details page, in the **Status** section, clear the **Auto-renew** checkbox.

5. Select **Submit**.

Suspending a new commerce subscription turns off autorenew. Partners that remove a suspension should be sure to turn autorenew back on if desired.

> [!NOTE]
>If a subscription is set to renew, the renewal will be processed the day after the subscription term end date. Renewals start at the end of the term. For example, if the term end date is 2023-03-01T00:00:00Z UTC it is inclusive of the whole day. The renewal will start after the term ends (2023-03-02T00:00:00Z UTC) and may take up to 24 hours. Partners have a seven day window to make changes after renewal completes. The seven day window starts precisely at this datetime of renewal completion.


## Applying changes to new commerce license-based subscriptions 

Some changes to new commerce subscriptions can't be made while the system waits to execute a renewal at the end of the subscription term or a cycle change to apply a billing frequency change in the middle of a term. Each of these events starts at 12:00 AM, the day of the event. Some of the subscription properties may not be updateable until the event (renewal or cycle charge) is completed.

- Cycle charges: The following properties are read-only and can't be changed until the cycle charge is completed: next charge instruction to change billing frequency.
- Renewal event: The renewal is queued and executed. Until the renewal, completed partners will find the following properties are read-only until renewal is completed: Auto renew, scheduled changes next term instructions, and suspend or reactivate.

> [!NOTE]
> Subscriptions may take up to 24 hours to complete their renewal which starts UTC 12:01 AM on the day of the new term. During this window partners can attempt updates to license counts, the subscription's partner of record, the friendly name of the subscription and can also cancel the subscription. If the subscription is still waiting to be processed the partner will get an error response (409: Conflict for API requests). Partners can resubmit the request after waiting for two minutes and the changes should then be accepted.

## Manage trials for new commerce license-based subscriptions

Trials for new commerce license-based subscriptions:

- Come with 25 seats
- Have autorenew turned on by default
- Last for 30 days

   After 30 days, trials autorenew to the paid equivalent subscription, but autorenewal can be turned off.

On conversion to a new subscription, the term duration defaults to **Annual**, and the billing cycle defaults to **Monthly**. You can modify term duration and the billing plan if you decide to convert the trial.

You can convert trials:

- To an equivalent paid subscription
- To a higher-tier subscription or an existing subscription
- At midterm or [schedule trial conversion](#scheduled-trial-conversion)

During a trial, the following actions aren't available:

- Increasing or reducing quantity
- Changing the status of the subscription

> [!NOTE]
> To convert from a trial to an existing subscription, the existing subscription's end date must occur on the same day as or after the trial's end date.
>
> Promotions don't apply when you're converting from a trial to a paid subscription.

### Midterm trial conversion

Trials last for 30 days, but you don't have to wait until the end of the 30 days to convert your trial. You can convert a trial at any time during the trial.

When you convert at midterm, you can't decrease the number of licenses from the default of 25.

Just like in upgrades, you can convert to a new subscription or choose an existing subscription.

If you select a *new* subscription, you can choose the term duration and billing frequency, and choose at least 25 seats to convert with.

If you select an *existing* subscription, the 25 seats are added to the existing subscription and keep the existing term duration and billing frequency.

To convert a trial at midterm, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Choose a customer from the list.

3. Find the trial subscription that you want to convert.

4. Select **Convert trial to paid subscription** in the top banner.

5. Choose an eligible conversion for your subscription.

6. Select the quantity, billing frequency, and term duration, if applicable.

7. Select **Submit**.

### Scheduled trial conversion

If you want to use a trial for its full duration but don't want to convert to the equivalent paid subscription, or if you want to convert with less than the default of 25 seats, you can choose to schedule the conversion.

To schedule a conversion, autorenew must be on.

To schedule a trial to convert at the end of the 30 days, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Choose a customer from the list.

3. Find the trial subscription for which you want to schedule a conversion.

4. Select **Manage Renewal**.

5. Make changes to the subscription and select **Okay**.

6. Select **Submit**.

The trial will convert with the scheduled changes after the 30 days.

## Next steps

- [Purchase commercial marketplace products for your customers](csp-commercial-marketplace-purchase.md)
- [Manage commercial marketplace products for your customers](csp-commercial-marketplace-manage.md)
- [Commercial marketplace overview](csp-commercial-marketplace-overview.md)
