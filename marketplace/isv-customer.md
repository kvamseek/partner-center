---
title: ISV to customer private offers
description: Configure ISV to customer private offers in Microsoft Partner Center for Azure Marketplace. 
ms.service: marketplace
ms.subservice: partnercenter-marketplace-publisher
ms.topic: how-to
author: emerb19
ms.author: emerb
ms.date: 07/12/2023
---

# ISV to customer private offers

Private offers allow publishers and customers to transact one or more products in Azure Marketplace by creating time-bound pricing with customized terms. This article explains the requirements and steps for a publisher to create a private offer for a customer in Azure Marketplace. Private offers aren't yet available in Microsoft AppSource.

This is what the private offer experience looks like from the publisher's perspective:

:::image type="content" source="media/isv-customer/isv-private-offer-experience.png" alt-text="Shows the progression of the ISV private offer experience with customers.":::

This is what the private offer experience looks like from the customer's perspective:

:::image type="content" source="media/isv-customer/customer-private-offer-experience.png" alt-text="Shows the progression of the customer's private offer experience with ISVs.":::

## Benefits of private offers

Private offers provide new deal-making capabilities to the marketplace that can't be achieved with private plans.

- **Time-bound discount**: Specify a start/end date for the discounted price. When the private offer ends, customers fall back to the publicly listed price.
- **Custom terms and contract upload**: Extend unique terms to each customer privately. By accepting your offer, the customer is accepting your terms. Attaching a PDF of your contract to the private offer is easy; no more plain text or amending the Microsoft Standard Contract.
- **Send by email**: Rather than coaching customers on where to find their offer in the Azure portal, email customers a link directly to their private offer. Save time by sending this email to anyone in the customer's company responsible for accepting the offer.
- **Deals expire**: Add urgency to the sales process by specifying the date by which the customer must accept the offer or it expires.
- **Faster arrival**: Private offers are available for purchase within 15 minutes (private plans take up to 48 hours to arrive).
- **Bundle discounts**: Select multiple products/plans to receive a discount; customers can accept the private offer for all of them at once.
- **Target a company**: Private offers are sent to an organization, not a tenant.

## Private offer prerequisites

Creating a private offer for a customer has these prerequisites:

- You've created a [commercial marketplace account](create-account.md) in Partner Center.
- Your account is enrolled in the commercial marketplace program.
- The offer you want to sell privately has been published to the marketplace and is publicly transactable.

## Supported offer types

Private offers can be created for all transactable marketplace offer types: SaaS, Azure Virtual Machines, and Azure Applications.

> [!NOTE]
> Discounts are applied on all custom meter dimensions your offer may use. They're only applied on the software charges set by you, not on the associated Azure infrastructure hardware charges.

## Private offers dashboard

Create and manage private offers from the **Private offers** dashboard in Partner Center's left-nav menu. This dashboard has two tabs:

- **Customers**: Create a private offer for a customer in Azure Marketplace. This opens the Customers private offer dashboard, which lets you:
  - Create new private offers
  - View the status of all your private offers
  - Clone existing private offers
  - Withdraw private offers
  - Delete private offers
  - View the purchase status of the products in a private offer
- **CSP Partners**: Create a private offer for a CSP partner. See [ISV to CSP partner private offers](isv-csp-reseller.md).
- The **Customers** tab looks like this:

:::image type="content" source="media/isv-customer/private-offers-in-partner-center.png" lightbox="media/isv-customer/private-offers-in-partner-center.png" alt-text="Screenshot that shows the private offers customer tab in Partner Center.":::

## Create a private offer for a customer

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/commercial-marketplace/overview), and select the **Marketplace offers** workspace.
1. Select **Private offers** from the left-nav menu.
1. Select the **Customers** tab.
1. Select **+ New private offer**.
1. Enter a private offer name. This is a descriptive name for use within Partner Center and is visible to your customer in the Azure portal.
1. Select the type of private offer you wish to submit based on the private offer attributes that you want to customize for your customer, including pricing (can be absolute or percentage discounts), meter quantities, and user limits for transactable marketplace offer types (including SaaS and VM reservation). Choose one of the below options:

   1. **Customize pricing for existing public offers and plans**: This existing option allows you to create a private offer for all transactable Marketplace offer types: SaaS, Azure Virtual Machines, and Azure Applications. You can customize the pricing via Absolute pricing or percentage discounts.

   2. **Customize pricing, metering quantities, and user limits for SaaS offers**: This new option allows you to create a private offer for a SaaS plan by customizing the absolute price, metering dimension quantities, and user limits.

   3. **Customize pricing and specific quantities for VM software reservation offers**: Use this option to create a private offer to sell VM software reservations (1-year or 3-year) and customize the absolute price, vCPU size, quantities, duration, and payment schedule.

       :::image type="content" source="media/isv-customer/new-private-offer.png" lightbox="media/isv-customer/new-private-offer.png" alt-text="Screenshot that shows the new private offers fields in Partner Center.":::

### Offer setup

Use this page to define private offer terms, notification contacts, and pricing for your customer.

- **Customer Information**: Specify the billing account for the customer receiving this private offer. This is only available to the configured customer billing account and the customer need to be an owner, contributor, or signatory to the billing account to accept the offer.

  > [!NOTE]
  > Customers can find their billing account ID in three ways:
  >
  >- The customer can scan their account using the [private offer precheck functionality](/marketplace/private-offers-pre-check), and export the report with billing account ID included.
  >- In the **[Azure portal](https://aka.ms/PrivateOfferAzurePortal)** under **Cost Management + Billing** > **Properties** > **ID**. A user in the customer organization should have access to the billing account to see the ID in Azure Portal.
  >- If the customer knows the subscription they plan to use for the purchase, select **Subscriptions**, select the relevant subscription > **Properties** (or Billing Properties) > **Billing Account ID**. See **[Billing account scopes in the Azure portal](/azure/cost-management-billing/manage/view-all-accounts)**.

   :::image type="content" source="media/isv-customer/customer-properties.png" lightbox="media/isv-customer/customer-properties.png" alt-text="Shows the offer Properties tab in Partner Center.":::

   :::image type="content" source="media/isv-customer/subscription-name-properties.png" lightbox="media/isv-customer/subscription-name-properties.png" alt-text="Screenshot showing subscription name properties.":::

- **Private offer terms**: Specify the duration, accept-by date, and terms:
  - **Start date**: Choose **Accepted date** if you want the private offer to start as soon as the customer accepts it. If a private offer is extended to an existing customer of a Pay-as-you-go product, this makes the private price applicable for the entire month. To have your private offer start in an upcoming month, select **Specific month** and choose one. The start date for this option is always the first day of the selected month.
  - **End date**: Choose the month for your private offer's **End date**. This is always the last day of the selected month.
  - **Accept by**: Choose the expiration date for your private offer. Your customer must accept the private offer prior to this date.
  - **Terms and conditions**: Optionally, upload a PDF with terms and conditions your customer must accept as part of the private offer.

  > [!NOTE]
  > Your terms and conditions must adhere to Microsoft supported billing models, offer types, and the [Microsoft Publisher Agreement](/legal/marketplace/msft-publisher-agreement).

- **Notification Contacts**: Provide up to five emails in your organization as **Notification Contacts** to receive email updates on the status of your private offer. These emails are sent when your offer status changes to **Pending acceptance**, **Accepted**, or **Expired**. You must also provide a **Prepared by** email address, which is displayed to the customer in the private offer listing in the Azure portal.
- **Pricing**:
  - If you selected ***option a*** under *step 6* in [Create a private offer for a customer](#create-a-private-offer-for-a-customer)): Configure the percentage-based discount or absolute price for up to 10 offers/plans in a private offer. For a percentage-based discount, the customer receives this discount off your plan's list price in the marketplace.
    - Select **+ Add Offers/plans** to choose the offers or plans you want to provide a private offer for.
    - Choose to provide a custom price or discount at either an offer level (all current and future plans under that offer have a discount associated to it) or at a plan level (only the plan you selected has a private price associated with it).
    - Choose up to 10 offers/plans and select **Add**.
    - Enter the discount percentage or configure the absolute price for each item in the pricing table.
    - Absolute pricing lets you input a specific price for the private offer. You can only customize the price based on the same pricing model, billing term, and dimensions of the public offer. You can't change to a new pricing model or billing term or add dimensions.
    - Absolute pricing is supported for SaaS and Azure Applications but not for Virtual Machine offers. You can't use absolute pricing for plans that have a trial enabled. Create a new public plan without a trial enabled or use discounted pricing.

   > [!NOTE]
   > Only public offers/plans that are transactable in Microsoft Azure Marketplace appear in the selection menu.

  - If you selected ***option b*** under *step 6* in [Create a private offer for a customer](#create-a-private-offer-for-a-customer)):
    - Select + Create new plan to choose the offers/plans you want to provide a private offer for by configuring absolute pricing, quantities on metering dimensions, and user limits.
    - Enter a plan name and select an existing plan as a template for the new plan to provide customized pricing, quantities on metering dimensions, or specific user limits.
    - Choose up to 10 offers/plans and select **Add**.
    - Configure the absolute price and other attributes for each item in the pricing table.
      - Each plan should have a name and description.
      - Pricing model:
        - Flat rate model:
          - Configure the billing term/s and price per payment for each billing term.
          - You can also modify the quantity included in the base for defined dimensions of your plan for each billing term.

          :::image type="content" source="media/isv-customer/flat-rate-model.png" lightbox="media/isv-customer/flat-rate-model.png" alt-text="Screenshot that shows the marketplace metering services dimensions.":::

        - Per User model:
          - Configure the minimum and maximum user limits for your plan, and the price per payment per user for each billing term.

          :::image type="content" source="media/isv-customer/pricing-model.png" lightbox="media/isv-customer/pricing-model.png" alt-text="Screenshot that shows the pricing model screen.":::

  - If you selected ***option c*** under *step 6* in [Create a private offer for a customer](#create-a-private-offer-for-a-customer)):
    - Select **+ Add offers/plan** to choose the offers/plans you want to provide a private offer for VM software reservations.
    - Choose up to 10 plans and select **Add**. You'll only see the VM plans that are public and have reservation pricing enabled (one year or three years).
    - Configure the absolute price for each item in the pricing table.
    - Absolute pricing lets you configure the following:
      - **Reservation duration**: Configure the duration of the reservations you would like to extend to the customer. You'll only see the options that are enabled on the public VM plan.
      - **Payment schedule**: You can choose “Upfront” or “Monthly” payment schedule for the reservations.
      - **Add reservation**: Add all the reservations that you want to extend as part of this private offer. Configure the vCPU size, Quantity of reservations, and the Unit price (USD). vCPU size is disabled if the VM plan is configured with a Flat rate pricing model. In the case of Monthly payment schedule, the Subtotal is calculated as “Monthly unit price **x** number of months **x** Quantity” and in the case of Upfront payment schedule, it's calculated as “Unit price **x** Quantity”.
      - To view the prices in all the enabled markets, use the “Export pricing data” after selecting **Save**.

### Review and submit

Use this page to review the information you've provided. Once submitted, a private offer is locked for edits. You can still withdraw a private offer while it's pending acceptance by the customer.

When you're ready, select **Submit**. You're returned to the dashboard where you can view the offer's status. The notification contacts are emailed once the offer is ready to be shared with your customer.

> [!NOTE]
> Microsoft will not send an email to your customer. You can copy the private offer link and share it with your customer for acceptance. Your customer will also be able to see the private offer under the **Private Offer Management** blade in the Azure portal.

## Private offer purchase status

ISVs can now track if their customers have subscribed to the products contained in private offers that have been accepted by the customers.

> [!NOTE]
> Currently this functionality only applies to SaaS offer types.

To see the private offer purchase status, select the **View status** link under Purchase status in the Private offers dashboard. The **View status**  link will only show for private offers that have been accepted by customers or have ended.
Selecting the **View status** link brings up a view of any subscriptions the customer has set up for the products contained in the private offer, and the state of those subscriptions, such as PendingFulfillmentStart, Subscribed, and so on.

If there are no entries in this view, then either 1) the customer hasn't purchased the SaaS product in your private offer yet and ISVs should follow up with the customer to tell them to purchase and activate the product (assuming start date has passed) or 2) The private offer only contains Azure Application or Virtual Machine offer types.
Purchase status can be:

- **Subscribed** – this means the customer has subscribed to the product, configured the SaaS service and the ISV has activated the subscription. No further action is required by ISV or the customer.
- **PendingFulfillmentStart** – this means either:
  - The customer has subscribed to the product but has yet to configure the SaaS service. ISVs should follow up with the customer and ask them to complete the step to configure the SaaS service.
  - The customer has subscribed and completed the configuration step but the ISV has yet to activate the subscription. The ISV should activate the subscription so that billing can occur.
- **Suspended** - this means the subscription has been suspended as a customer’s payment wasn't received. Microsoft gives the customer a 30-day grace period before automatically canceling the subscription.
- **Unsubscribed** – this means either:  
  - ISV didn't activate the subscription by the 30-day deadline since the customer purchased and configured the SaaS service. ISVs need to advise their customers to subscribe to the product again and ISV should activate it within the 30-day deadline.
  - The subscription has been canceled either because a customer has requested to cancel the subscription, or the subscription was canceled because of nonpayment.
  - The subscription has expired.

## Clone a private offer

You can clone an existing offer and update its customer information to send it to different customers, so you don't have to start from scratch. Or, update the offer/plan pricing to send extra discounts to the same customer.

1. Select **Private offers** from the left-nav menu.
1. Select the **Customers** tab.
1. Check the box of the private offer to clone.
1. Select **Clone**.
1. Enter a new private offer name.
1. Select **Clone**.
1. Edit the details on the **Offer setup** page as needed.
1. **Submit** the new private offer.

## Withdraw a private offer

Withdrawing a private offer means your customer will no longer be able to access it. A private offer can only be withdrawn if your customer hasn't accepted it.

To withdraw a private offer:

1. Select **Private offers** from the left-nav menu.
1. Select the **Customers** tab.
1. Check the box of the private offer to withdraw.
1. Select **Withdraw**.
1. Select **Request withdraw**.
1. Your offer status is updated to **Draft** and can now be edited, if desired.

Once you withdraw a private offer, your customer will no longer be able to access it in the commercial marketplace.

## Delete a private offer

Delete can be used when a private offer is in **Draft** status. To delete a private offer in **Draft** status:

1. Select **Private offers** from the left-nav menu.
1. Select the **Customers** tab.
1. Check the box of the private offer to delete.
1. Select **Delete**.
1. Select **Confirm**.

This action will permanently delete your private offer. You can only delete private offers in **Draft** status.

## Cancelling an accepted private offer

Once a private offer has been accepted by the customer, ISVs will no longer be able to withdraw or edit the private offer. In some circumstances, where the private offer has been created with incorrect details, that is, incorrect pricing, incorrect public plan used, incorrect terms or dates, the ISV (with the customer’s agreement) can request marketplace support team to cancel the private offer.

To do so, ISVs can create a support ticket in Partner Center and request the private offer to be canceled.

The ISV needs to provide:

- The Private Offer ID
- Customer Billing Account ID  
- Reason for cancellation  
- Screenshot with written confirmation from the customer that they agree to the cancellation.

Upon cancellation, the private offer is removed from the ISV’s customer private offer dashboard view in Partner Center and will also be removed from the customer’s Private Offer Management view in the Azure portal. After the cancellation has been processed, the private offer price will no longer be applied if the customer was to purchase the plan that was contained in the canceled private offer.  

> [!NOTE]
> If a private offer is canceled containing a virtual machine offer type that has been deployed, the discount will not be applied to consumption charges in the month of cancellation.

## View private offer status

To view the status of a private offer:

1. Select **Private offers** from the left-nav menu.
1. Select the **Customer** tab.
1. Check the **Status** column.

The status of the private offer will be one of the following:

- **Draft** – You've started the process of creating a private offer but haven't submitted it yet.
- **In Progress** – A private offer you submitted is currently being published; this can take up to 15 minutes.
- **Pending acceptance** – Your private offer is pending customer acceptance. Ensure you've sent the private offer link to your customer.
- **Accepted** – Your private offer was accepted by your customer. Once accepted, the private offer can't be changed.
- **Expired** – Your private offer expired before the customer accepted it. You can withdraw the private offer to make changes and submit it again.
- **Ended** – Your private offer has passed its end date.

## Reporting on private offers

The payout amount and agency fee that Microsoft charges is based on the private price after the percentage-based discount or absolute price was applied to the products in your private offer.

## Next steps

**Further reading**

- [Frequently asked questions](isv-customer-faq.yml) about configuring ISV to customer private offers

**Video tutorials (YouTube)**

- [Private Offer Overview of ISV to Customer Offers](https://www.youtube.com/watch?v=SNfEMKNmstY)
- [ISV to Customer Private Offer Creation](https://www.youtube.com/watch?v=WPSM2_v4JuE)
- [ISV to Customer Private Offer Acceptance](https://www.youtube.com/watch?v=HWpLOOtfWZs)
- [ISV to Customer Private Offer Purchase Experience](https://www.youtube.com/watch?v=mPX7gqdHqBk)