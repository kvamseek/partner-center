---
title: Multiparty private offers (for ISVs)
description: Configure ISV to CSP partner multiparty private offers in Microsoft Partner Center. 
ms.service: marketplace
ms.subservice: partnercenter-marketplace-publisher
ms.topic: how-to
author: emerb19
ms.author: alisonb
ms.date: 09/21/2023
ms.custom: references_regions
---

# Multiparty private offers (for ISVs)

Multiparty private offers empower partners to come together, create personalized offers with custom payouts, and sell directly to Microsoft customers with simplified selling through the marketplace. And for customers that have a Microsoft Azure Consumption Commitment (MACC), every dollar of the sale will count toward their MACC commitment when they purchase solutions that are Azure IP co-sell and MACC eligible.

This allows ISVs to scale and unlock a completely new, repeatable revenue channel. The Microsoft partner ecosystem has over 400,000 partners - many of whom are looking to resell solutions like yours. Multiparty private offers help you activate partners to become your extended sales force.

This also allows ISVs to achieve the flexibility needed to make and close deals quickly. Multiparty private offers are the newest offer type in the private offers collection. You can create new offers within minutes and customize the pricing and terms to build the partnerships you need.

Overview of the multiparty private offers experience:

1. The ISV creates an offer and includes the selling partner.
1. The Selling partner extends the offer to the customer.
1. The Customer buys through the commercial marketplace.
1. Microsoft pays the ISV and the selling partner.

## ISV prerequisites to create a multiparty private offer

As the ISV, you must meet these prerequisites to create a multiparty private offer for partners:

- You have [enrolled in the Microsoft AI Cloud Partner Program](../mpn-create-a-partner-center-account.md).
- You have [created a commercial marketplace account in Partner Center](../create-account.md).
- Your account is enrolled in the commercial marketplace program.
- The offer you want to sell privately has been published to the marketplace and [is publicly transactable](./marketplace-commercial-transaction-capabilities-and-considerations.md).
- You're creating a multiparty private offer for a partner that is eligible to sell multiparty private offers to customers. Review the [partner eligibility criteria](./multiparty-private-offers-for-selling-partners.md#partner-prerequisites-to-create-a-multiparty-private-offer).
- You're creating a multiparty private offer for a customer that is eligible to purchase multiparty private offers. Review the [customer eligibility criteria](#offer-setup).
- You have a marketplace developer, manager, or account owner role associated with your marketplace seller ID.  

### Supported offer types

Multiparty private offers can be created for the following transactable marketplace offer types: SaaS, Azure Virtual Machines, and Azure Applications.

> [!NOTE]
> Your selling partner can adjust the price on all custom meter dimensions your offer may use. Price adjustments are only applied on the software charges set by you, not on the associated Azure infrastructure charges.  

## Private offers dashboard

Create and manage private offers from the **Private offers** dashboard in Partner Center’s left-nav menu of the Marketplace offers workspace in Partner Center. This dashboard has three tabs:

- **Customers**: Create a private offer for a customer to buy direct from the Azure portal. See [ISV to customer private offers](./isv-customer.md).
- **CSP partners**: Create a private offer for a CSP partner. See [ISV to CSP partner private offers](./isv-csp-reseller.md).
- **Multiparty**: Create a private offer that includes a selling partner and is transacted through Azure Marketplace.

## Create a multiparty private offer

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home).
1. Select **Marketplace offers** from the home page.
1. Select **Private offers** from the left-nav menu to open the dashboard.  
1. Select the **Multiparty** tab.
1. Select **+ New private** offer.
1. Enter a **multiparty private offer name**. This name is a descriptive name that you use to refer to your multiparty private offer within Partner Center. The name entered is visible to your selling partner within Partner Center and to your customer within the Azure portal.
1. Select the type of multiparty private offer you wish to create based on the attributes you want to customize. Attributes include pricing (either absolute or percentage discounts), meter quantities, and user limits for transactable marketplace offer types (including SaaS and VM reservation). Choose one of the options:
   - **Customize pricing for existing offers**: Use this option to create a multiparty private offer for all transactable offer types: SaaS, Azure Virtual Machines, and Azure Applications. You can customize your partner pricing via absolute pricing or percentage discounts.
   - **Customize pricing, metering quantities, and user limits for SaaS offers**: Use this option to create a multiparty private offer for a SaaS plan by customizing your absolute partner price, metering dimension quantities, and user limits.
   - **Customize pricing and specific quantities for VM software reservation offers**: Use this option to create a multiparty private offer to sell VM software reservations (1-year or 3-year) and customize the absolute partner price, vCPU size, quantities, duration, and payment schedule.

> [!NOTE]
> As the ISV, you'll create the multiparty private offer and submit it to your selling partner. Therefore, you'll be the originator of the multiparty private offer.

### Offer setup

Use this page to configure your multiparty private offer with the customer and term details and add the selling partner you’ll be working with.

- **Customer information**: Specify the billing account for the customer receiving this multiparty private offer. The multiparty private offer will only be available to the configured customer billing account and the customer will need to be an owner or contributor or signatory on the billing account to accept the offer. For now, the United States is the only supported customer and selling partner market for multiparty private offers. Your customer must have a United States billing account to purchase your products through a multiparty private offer.

  Customers can find their billing account ID in three ways:

  1. Customers can run the [eligibility check tool](https://aka.ms/poprecheck) and download the report to identify their billing account ID to verify if they're approved to purchase via the marketplace.
  1. In the [Azure portal](https://aka.ms/PrivateOfferAzurePortal) under **Cost Management + Billing > Properties > ID**. A user in the customer organization should have access to the billing account to see the ID in Azure portal.
  1. If the customer knows the subscription they plan to use for the purchase, select **Subscriptions**, select the relevant subscription > **Properties** (or **Billing Properties**) > **Billing Account ID**. See [Billing account scopes in the Azure portal](/azure/cost-management-billing/manage/view-all-accounts).

- **Description**: Optionally enter a description of the multiparty private offer for your reference. The description entered is visible to your selling partner in Partner Center, but won't be visible to the customer and not included in your marketplace reporting.
- **Partner information**: Add the selling partner you authorize to sell your products through this multiparty private offer. Only one selling partner can be added to the multiparty private offer.

  1. Select + **Add partner**.
  1. Enter the marketplace seller ID of your partner. Your partner can locate this information in Partner Center under **Account settings > Identifiers > Publisher** within their organizational profile.
  1. Select **Add partner**.
  
  > [!NOTE]
  > For now, the United States is the only supported customer and selling partner market for multiparty private offers. Your selling partner must have a completed United States tax profile in Partner Center for marketplace associated with their seller ID. Your selling partner can verify this in Partner Center under **Account settings > Payout and tax profiles > Tax profiles** tab. The tax profile country/region associated with their seller ID needs to be the United States.

- **Customer terms**: The customer start and end date determine how long the multiparty private offer prices apply to customer purchases during that time. This is different from the offer subscription start and end date.
  - **Customer start date**:
    - Choose **Customer accept by date** if you want the multiparty private offer to start as soon as the customer accepts it. This will make the multiparty private offer immediately visible to the customer within Azure portal in Marketplace under Private Products. If a multiparty private offer is extended to an existing customer of a Pay-as-you-go product, this makes the private price applicable for the entire month.
    - To have your multiparty private offer start in an upcoming month, select **Specific month** and choose one. The start date for this option is always the first day of the selected month. The selected month and the multiparty private offer won't be visible to the customer within the Azure portal in Marketplace under Private Products until that month.
  - **Customer end date**: Choose the expiration date for your multiparty private offer. Your customer must purchase prior to the end date otherwise the multiparty private offer price will end after this date.
  - **Customer accept by date**: Choose the expiration date by which your customer must accept your multiparty private offer. Your customer must accept the multiparty private offer prior to this date.
  - **Customer terms and conditions**: Optionally, upload a PDF copy of the terms and conditions you want your customer to accept as part of the multiparty private offer. A total of five attachments can be uploaded between you and your selling partner.
  
    1. Select **+ Add terms and conditions**.
    1. Attach the PDF copy of the terms and conditions your customer must accept as part of the multiparty private offer.
    1. Type in a unique **Customer-facing document name** for each customer term and condition you upload. This document name is visible to your selling partner in Partner Center and to your customer in Azure portal.

       > [!NOTE]
       > Your terms and conditions must adhere to Microsoft supported billing models, offer types, and the [Microsoft Publishers Agreement](/legal/marketplace/msft-publisher-agreement).  

- **Notification contacts**: Optionally provide up to five email addresses for the people within your company as **Notification contacts** to receive email updates on the status of the multiparty private offer. These emails are sent when your offer status changes to **Pending partner action**, **Pending acceptance**, **Accepted**, or **Expired**.
- **Product offers**: Add the offers or plans you authorize your partner to sell. Configure the price to your partner, and your selling partner will be able to adjust the customer price separately. A total of 10 products can be added to the multiparty private offer.

  1. Select **+ Add offer**.
  1. Choose to configure a custom **Absolute price** or a **Discounted price** to your selling partner for your products.

     Configuring an absolute price to your selling partner lets you override the price for a specific plan within a product offer. You can only customize the price based on the same pricing model, billing term, and dimensions of the public offer. You can’t change to a new pricing model or billing term or add dimensions.
  
  Absolute pricing is supported for SaaS and Azure Applications but not for Virtual Machine offers. You can't use absolute pricing for plans that have a trial enabled. Create a new public plan without trial enabled or use discounted pricing.

     Configuring a discounted price to your selling partner lets you configure a discount percentage for a specific plan within a product offer. Your partner receives this discount off your plan’s list price in the marketplace.

  1. Choose up to 10 offers or plans and select **Add**.
  1. Enter your **Partner price** as an absolute price or as a discount percentage for each product in the product pricing table. Select **Configure price** to configure an absolute partner price. Enter the discount percentage in the product pricing table to configure a discounted partner price.

     > [!NOTE]
     > Only public offers and plans that are transactable in Azure Marketplace appear in the selection menu.

- If you're creating a multiparty private offer with absolute pricing, quantities on metering dimensions and user limits for SaaS offers:

  - Select **+ Create new plan** to choose the offers/plans you want to include in the multiparty private offer by configuring absolute pricing, quantities on metering dimensions, and user limits.
  - Enter a plan name and select an existing plan as a template for the new plan to provide customized pricing, quantities on metering dimensions, or specific user limits.
  - Choose up to 10 offers/plans and select **Add**.
  - Configure the absolute price to your partner and other attributes for each item in the pricing table.
  - Each plan should have a name and description.

    To use a flat-rate pricing model:
    - Configure the billing term/s and price per payment for each billing term.
    - You can also modify the quantity included in the base for defined dimensions of your plan for each billing term.

    To use a per-user pricing model:
    - Configure the minimum and maximum user limits for your plan, and the price per payment per user for each billing term.

- If you're creating a multiparty private offer for VM software reservations:
  - Select + **Add offers/plan** to choose the offers/plans you want to include in the multiparty private offer for VM software reservations.
  - Choose up to 10 plans and select **Add**. You'll only see the VM plans that are public and have reservation pricing enabled (1-year or 3-years).
  - Configure the absolute price to your partner for each item in the pricing table.
  - Absolute pricing lets you make these configurations:

    - **Reservation duration**: Configure the duration of the reservations you would like to extend to the partner. You'll only see the options that are enabled on the public VM plan.
    - **Payment schedule**: You can choose an **Upfront** or **Monthly** payment schedule for the reservations.
    - **Add reservation**: Add all the reservations that you want to extend as part of this multiparty private offer. Configure the **vCPU size**, **Quantity of reservations**, and the **Unit price (USD)**. The vCPU size will be disabled if the VM plan is configured with a Flat rate pricing model.

      For the Upfront payment schedule, the subtotal is calculated as: _Unit price x Quantity_.

      For the Monthly payment schedule, the subtotal is calculated as: _Monthly unit price x number of months x Quantity_.

    - To view the prices in all the enabled markets, select **Save**, then select **Export pricing data**.

- **Sales note**: Optionally include up to 60 characters of text as a sales note. Information entered here isn't visible to your partner or to your customer and only appears in your marketplace reporting within the download exports for the orders, usage, and revenue dashboards and through programmatic API access to marketplace analytics. Don't include any personal data including names or email addresses.  

### Review and submit

Use this page to review the information you’ve provided. Once submitted, the multiparty private offer is locked for edits. You can still withdraw the multiparty private offer while it's pending partner action by your selling partner.

When you’re ready, select **Submit**. The offer will be available to your selling partner within 15 minutes. Be sure to send your selling partner an email to inform them the multiparty private offer is available for them to access. You’ll be returned to the dashboard where you can view the offer’s status. The notification contacts you specified on the multiparty private offer will be emailed once the offer is ready to be shared with your customer.

> [!NOTE]
> Microsoft will not send an email to your selling partner or customer. Your selling partner will be able to copy the multiparty private offer link and share it with your customer for acceptance. Your customer will also be able to see the multiparty private offer under the Private offer management blade in the Azure portal.  

## View private offers status

To view the status of your multiparty private offer:

1. Select **Private offers** from the left-nav menu.
1. Select the **Multiparty** tab.
1. Check the **Status** column.

Private offer status descriptions:

- **Draft**: You have started creating a multiparty private offer but haven't yet submitted it.
- **In Progress**: The multiparty private offer that you submitted is currently being published. This can take up to 15 minutes.
- **Pending partner action**: The multiparty private offer you submitted is now available for your selling partner to update and send to the customer for acceptance.
- **Pending acceptance**: The multiparty private offer is pending customer acceptance. While the offer is in this state, the ISV can't withdraw the offer with the selling partner, unless the selling partner withdraws the multiparty private offer from the customer first.
- **Accepted**: The customer accepted the multiparty private offer. Once accepted, the multiparty private offer can’t be changed.  
- **Expired**: The multiparty private offer expired before the customer accepted it. You can request your selling partner to withdraw the multiparty private offer. Once withdrawn by your selling partner, you'll be able to withdraw the multiparty private offer to make changes and submit it again.
- **Ended**: The multiparty private offer has passed its end date.

## Purchase status

You can track if your customer has subscribed to the products contained within the multiparty private offer after they accept the offer.

> [!NOTE]
> Currently this functionality only applies to SaaS offer types.

To see the multiparty private offer purchase status, select the **View status** link under **Purchase status** in the **Private offers** dashboard. The **View status** link only shows for multiparty private offers that have been accepted by the customer or have ended. After selecting the **View status** link, you'll get a view of any subscriptions the customer has set up for the products contained within the multiparty private offer, and the state of those subscriptions. If there are no entries within this view, then either:

1. The customer hasn't yet purchased the SaaS product within the multiparty private offer and you should follow up with your selling partner on the deal or with the customer directly to help them purchase and activate the product (assuming the start date has already passed), or,
1. The multiparty private offer only contains Azure Application or Virtual Machine offer types.

Purchase status can be:

- **Subscribed**: The customer has subscribed to the product, configured the SaaS service and you have activated the subscription. No further action is required by you or the customer.
- **PendingFulfillmentStart**: Possible reasons:

  - The customer has subscribed to the product but has yet to configure the SaaS service. You should follow up with your selling partner on the deal or with the customer directly and ask them to complete the step to configure the SaaS service.
  - Or, the customer has subscribed and completed the configuration step, but you as the ISV haven’t activated the subscription yet. You should activate the subscription so that billing can occur.

- **Suspended**: The subscription has been suspended because a customer’s payment wasn't received. Microsoft gives the customer a 30-day grace period before automatically canceling the subscription.

- **Unsubscribed**: Possible reasons:

  - You as the ISV didn't activate the subscription by the 30-day deadline since the customer purchased and configured the SaaS service. You need to advise your selling partner or the customer directly to subscribe to the product again. You should activate it within the 30-day deadline.
  - The subscription has been canceled either because a customer has requested to cancel the subscription, or the subscription was canceled because of nonpayment.
  - The subscription has expired.

## Clone a private offer

You can clone an existing multiparty private offer so that you don’t have to start from scratch. Update its customer and selling partner information to send it to different customers and selling partners. Or, update the product offer or plan pricing to send another multiparty private offer to the same customer and selling partner.

To clone a multiparty private offer:  

1. Select **Private offers** from the left-nav menu.
1. Select the **Multiparty** tab.
1. Select the private offer you want to clone, then select **Clone**.
1. Enter a new private offer name, then select **Clone**.
1. Edit the details on the **Offer Setup** page as needed.
1. **Submit** the new multiparty private offer.

## Withdraw a private offer

Withdrawing a multiparty private offer means your selling partner and your customer will no longer be able to access it. A multiparty private offer can only be withdrawn by an ISV if the status is **Pending partner action**. A multiparty private offer can't be withdrawn by an ISV if the status is **Pending acceptance** or **Accepted by the customer**.

To withdraw a multiparty private offer:

1. Select **Private offers** from the left-nav menu to open the dashboard.
1. Select the **Multiparty** tab.
1. Select the private offer you want to withdraw, then select **Withdraw**.
1. Select **Request withdraw**.
1. Your offer status is updated to **Draft** and can now be edited, if desired.  

## Delete a multiparty private offer

Delete can only be used when a multiparty private offer is in **Draft** status. To delete:

1. Select **Private offers** from the left-nav menu to open the dashboard.
1. Select the **Multiparty** tab.
1. Check the box of the multiparty private offer you want to delete.
1. Select **Delete**.
1. Select **Confirm**.

This action permanently deletes your multiparty private offer.

## Cancelling an accepted multiparty private offer

Once the customer accepts the multiparty private offer, ISVs are no longer be able to withdraw or edit the multiparty private offer. In some circumstances, where the multiparty private offer has been created with incorrect details such as incorrect pricing, incorrect public plan, or incorrect terms or dates, the ISV should work with the selling partner to inform the customer to confirm consent, and then submit a marketplace support request to cancel the multiparty private offer.

To do so, ISV partners, or the selling partner, can create a support ticket in Partner Center and request the multiparty private offer to be canceled.

Provide the following information:

- The private offer ID
- The customer billing account ID
- Reason for cancellation  
- Confirm whether refund is needed if the customer has already purchased. More purchase info is required if a refund is needed.
- A screenshot with written confirmation from both the other partner involved in configuring the multiparty private offer and from the customer that they agree to the cancellation.

Upon cancellation, the multiparty private offer will be removed from your multiparty private offer dashboard view in Partner Center and will also be removed from the customer’s Private Offer Management view in the Azure portal. After the cancellation has been processed, the multiparty private offer price will no longer be applied if the customer was to purchase the plan that was contained in the canceled multiparty private offer.  

## Payout and reporting on multiparty private offers

The payout amount and agency fee that Microsoft charges is based on the partner price you set after your percentage-based discount or absolute price was applied to the products in your multiparty private offer.

- **Payouts**: Sales through multiparty private offers will be in [Payouts reporting](../payouts-overview.md), specifically under Payments, Transaction history, and Export data.
- **Analytics**: Sales through multiparty private offers are available in the [commercial marketplace insights](../analytics.md) dashboards, reports, and through programmatic access.

## Next steps

**Further reading**

- [Frequently asked questions](./multiparty-private-offers-faq.md) about configuring multiparty private offers

- Reference the [multiparty private offer eligible selling partner list](https://partner.microsoft.com/resources/detail/multiparty-private-offer-eligible-selling-partner-list-pdf) to quickly validate a selling partner’s eligibility. You’ll need to authenticate with your Microsoft partner credentials to access it.

**Video tutorials (YouTube)**

- [Multiparty private offers: ISV partner creates one for their selling partner](https://www.youtube.com/watch?v=6AmdYEvSxso)

- [Multiparty private offers: Customer accepts and purchases a private offer](https://www.youtube.com/watch?v=6AmdYEvSxso)


