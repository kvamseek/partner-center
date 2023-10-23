---
title: Multiparty private offers (for selling partners)
description: Configure ISV to CSP partner multiparty private offers in Microsoft Partner Center, for selling partners. 
ms.service: marketplace
ms.subservice: partnercenter-marketplace-publisher
ms.topic: how-to
author: emerb19
ms.author: emerb
ms.date: 09/21/2023
ms.custom: references_regions
---

# Multiparty private offers (for Selling partners)

Multiparty private offers empower partners to come together, create personalized offers with custom payouts, and sell directly to Microsoft customers with simplified selling through the marketplace. And for customers that have a Microsoft Azure Consumption Commitment (MACC), every dollar of the sale will count toward their MACC commitment when they purchase solutions that are Azure IP co-sell and MACC eligible.

This allows selling partners to differentiate their offerings. Customers often lean on trusted partners to advise them on their entire cloud estate. Now with multiparty private offers, partners can add ISV solutions to an offer - almost instantly.

This also allows selling partners to maintain their customer relationships and build new relationships with new customers. While any qualified customer can buy through multiparty private offers, this new offering will help you land new customer opportunities that have an Azure consumption commitment.  

Overview of the multiparty private offers experience:

1. The ISV creates an offer and includes the selling partner.
1. The Selling partner extends the offer to the customer.
1. The Customer buys through the commercial marketplace.
1. Microsoft pays the ISV and the selling partner.

## Partner prerequisites to create a multiparty private offer

You must meet these prerequisites to create a multiparty private offer for customers:

- You have [enrolled in the Microsoft AI Cloud Partner Program](../mpn-create-a-partner-center-account.md).
- You have [created a commercial marketplace account in Partner Center](../create-account.md).
- Your account is enrolled in the commercial marketplace program.
- You have [a completed United States tax profile in Partner Center for commercial marketplace](../set-up-your-payout-account.md).
- You have [filed your resale certificates](/partner-center/marketplace/multiparty-private-offers-for-selling-partners) with Microsoft for commercial marketplace.
- An ISV has created a multiparty private offer for you.
- The offer you want to sell privately has been published to the marketplace and is publicly transactable.
- You're creating a multiparty private offer for a customer that is eligible to purchase multiparty private offers. Review the [customer eligibility criteria](./multiparty-private-offers-for-isvs.md#offer-setup).
- You have a marketplace developer, manager, or account owner role associated with your marketplace seller ID.

> [!NOTE]
> For now, the United States is the only supported customer and selling partner market for multiparty private offers. To sell multiparty private offers, you must have a completed United States tax profile in Partner Center for marketplace associated with your seller ID. You can verify this in Partner Center under **Account settings > Payout and tax profiles > Tax profiles** tab. The tax profile country/region associated with your seller ID needs to be the United States. If you don’t see the **Payout and tax profiles** in the left navigational menu, contact your Partner Center global administrator or account administrator within your company for permissions or to complete this step.
## File resale certificates

**Selling partners must provide your resale certificate(s) to Microsoft at least 5 business days before the sale of any multiparty private offer**. Resale certificates must be provided for each seller ID used to sell multiparty private offers and must be provided even if your company has already provided them for other programs such as the [Cloud Solution Provider](../csp-overview.md) program. Your certificate(s) must be accurately completed and signed and must include the state where your company is headquartered at a minimum. Your resale certificate(s) must be on file at Microsoft before you sell multiparty private offers, or sales tax may be charged on your purchase as required by various tax laws. Depending on your location, your local government may govern your resale certificates in addition to or in lieu of your state Department of Revenue (or similar department) and must be managed accordingly. While many locations have blanket certificates that are renewed annually, some locations may renew at two or more years. Verify this and other information by checking your certificate or contacting your local tax authority.

To file your tax exemption(s), request support through [Partner Center](https://partner.microsoft.com/dashboard/support/servicerequests/create?stage=2&topicid=96277724-9b43-e131-2ddb-94f18f0a8dde). You'll need to provide your marketplace seller ID and supply the appropriate information.

> [!NOTE]
> You can locate your seller ID in Partner Center under **Account settings > Identifiers > Publisher** within your organizational profile. Your company must have a completed United States tax profile in Partner Center for marketplace associated to your seller ID. You can verify this in Partner Center under **Account settings > Payout and tax profiles > Tax profiles** tab. The tax profile country/region associated with your seller ID needs to be the United States. If you don’t see the **Payout and tax profiles** in the left navigational menu, contact your Partner Center global administrator or account administrator within your company for permissions or to complete this step.
## Configure your multiparty private offers

Configure your multiparty private offers from the **Private offers** dashboard within the left-nav menu of the Marketplace offers workspace in Partner Center.  

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) using the account associated with the marketplace seller ID you provided to ISVs to add you to the multiparty private offer.
1. Select **Marketplace offers** from the home page.
1. Select **Private offers** from the left-nav menu to open the dashboard.  
1. Select the **Multiparty** tab.
1. Multiparty private offers with the status **Pending partner action** are ready for you to update and send to customers for acceptance. Select the name of the multiparty private offer you are ready to action.

> [!NOTE]
> The ISV that created the multiparty private offer and submitted it to you will be the **originator** of the multiparty private offer.  

### Offer setup

Use this page to verify the customer information, products, pricing, and terms associated to the multiparty private offer are correct. Adjust the pricing and optionally add your terms. If there is an issue with the information included in the multiparty private offer, request the originator to withdraw it, update it, and resubmit it to you. Prior to any sales, provide your resale certificates to Microsoft.

- **Customer terms and conditions**: Optionally, upload a PDF copy of the terms and conditions you want your customer to accept as part of the multiparty private offer. Your terms and conditions will not be visible to your ISV partner, just to your customer. A total of five attachments can be uploaded between you and your ISV partner.

  1. Select **+ Add terms and conditions**.
  1. Attach the PDF copy of the terms and conditions your customer must accept as part of the multiparty private offer.
  1. Type in a unique **Customer-facing document name** for each customer term and condition you upload. This document name will be visible to your customer in Azure portal.

  > [!NOTE]
  >  Your terms and conditions must adhere to Microsoft supported billing models, offer types, and the [Microsoft Publishers Agreement](/legal/marketplace/msft-publisher-agreement).

- **Notification contacts**: Provide up to five email addresses for the people within your company as **Notification contacts** to receive email updates on the status of the multiparty private offer. These emails are sent when your offer status changes to **Pending partner action**, **Pending acceptance**, **Accepted**, or **Expired**.
- **Prepared by contact**: You must also provide a **Prepared by** email address, which will be displayed to the customer in the private offer listing in the Azure portal.
- **Product offers**: Set the price increase to the customer as a percentage. Enter the **Customer adjustment %** with up to 8 decimal digits to achieve more precision. The adjustment % you enter will be used to calculate the estimated price to the customer. The final price to your customer could be affected by other factors that may apply to your customer’s organization.
  
  **Example 1**: This example illustrates how a customer adjustment % can be applied on top of your partner price to calculate the customer price.

  - Partner price: $100.00.
  - Customer adjustment %: you enter **10%**.
  - Customer price: $110.00.
  - Calculation is $100 + ($100 x 10%) = $110.00 plus applicable taxes.
  
  **Example 2**: This example illustrates how the customer adjustment % can be applied to achieve the desired customer price from the partner price you received.  

  - Partner price: $95.00.
  - Desired customer price: $105.00 plus applicable taxes.
  - Customer adjustment %: you enter **10.52631579%**
  - Calculation is ($105.00 - $95.00)/$95.00 = 10.52631579%.
  - Verify this customer adjustment % will generate your desired customer price. Calculate $95.00 + ($95.00 x 10.52631579%) = $105.00 to confirm and edit the customer adjustment % as needed.  

  If your ISV partner configured a discounted partner price to you, the customer price adjustment % you enter cannot exceed the discount your ISV partner provided to you. If you need to configure a customer price adjustment that exceeds the discount your ISV partner provided to you, request your ISV partner withdraw the multiparty private offer and configure an absolute partner price to you to remove this limitation.

- **Sales note**: Optionally include up to 60 characters of text as a sales note. Information entered here will not be visible to your customer or ISV partner and will only appear in your marketplace reporting within the download exports for the orders, usage, and revenue dashboards and through programmatic API access to marketplace analytics. Do not include any personally identifiable information including names or email addresses.  

## Review and submit

On the **Review and submit** page, view the estimated customer price as either a calculated price or a net discount, and edit your customer adjustment % if needed. The final price to your customer could be affected by other factors that may apply to your customer's organization.

Once submitted, the multiparty private offer is locked for edits. You can still withdraw the multiparty private offer while it's **Pending customer acceptance** by the customer. However, your ISV partner will be unable to withdraw the multiparty private offer once you’ve submitted it and it is in a **Pending acceptance** state.

When you’re ready, select **Submit**. You’ll be returned to the dashboard where you can view the offer’s status. Your multiparty private offer will be available within 15 minutes. Once the acceptance link is available, select the multiparty private offer and select **Copy link** in the actions above the dashboard to share it with your customer for acceptance. The notification contacts you specified on the multiparty private offer will be emailed once the offer is ready to be shared with your customer.

> [!NOTE]
> Microsoft will not send an email to your customer. You can copy the private offer link and share it with your customer for acceptance. Your customer will also be able to see the multiparty private offer under the **Private offer management** pane in the Azure portal. To learn more, see [Purchase a private offer](/marketplace/purchase-a-private-offer).

## View private offers status

To view the status of your multiparty private offer:

1. Select **Private offers** from the left-nav menu.
1. Select the **Multiparty** tab.
1. Check the **Status** column.

Private offer status descriptions:

- **Draft**: You've started creating a multiparty private offer but haven't yet submitted it.
- **In Progress**: The multiparty private offer that you submitted is currently being published. This can take up to 15 minutes.
- **Pending partner action**: The multiparty private offer you submitted is now available for your selling partner to update and send to the customer for acceptance.
- **Pending acceptance**: The multiparty private offer is pending customer acceptance and can't be withdrawn by you as the ISV.
- **Accepted**: The multiparty private offer was accepted by your customer. Once accepted, the multiparty private offer can’t be changed.  
- **Expired**: The multiparty private offer expired before the customer accepted it. You can request your selling partner to withdraw the multiparty private offer. Once withdrawn by your selling partner, you'll be able to withdraw the multiparty private offer to make changes and submit it again.
- **Ended**: The multiparty private offer has passed its end date.

## Purchase status

You can track if your customer has subscribed to the products contained within the multiparty private offer after they accept the SaaS offer.

> [!NOTE]
> Currently, this functionality only applies to SaaS offer types.

To see the multiparty private offer purchase status, select the **View status** link under **Purchase status** in the **Private offers** dashboard. The **View status** link only shows for multiparty private offers that have been accepted by the customer or have ended. After selecting the **View status** link, you'll get a view of any subscriptions the customer has set up for the products contained within the multiparty private offer, and the state of those subscriptions. If there are no entries within this view, then either:

- The customer hasn't yet purchased the SaaS product within the multiparty private offer and you should follow up with your selling partner on the deal or with the customer directly to help them purchase and activate the product (assuming the start date has already passed), or,
- The multiparty private offer only contains Azure Application or Virtual Machine offer types.

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

## Withdraw a private offer

Withdrawing a multiparty private offer means your customer will no longer be able to access it. A multiparty private offer can only be withdrawn by a selling partner if the status is **Pending acceptance**. A multiparty private offer can't be withdrawn by an ISV if the status is **Accepted** by the customer.

To withdraw a multiparty private offer:

1. Select **Private offers** from the left-nav menu to open the dashboard.
1. Select the **Multiparty** tab.
1. Select the private offer you want to withdraw, then select **Withdraw**.
1. Select **Request withdraw**.
1. Your offer status is updated to **Pending partner action (Draft)** and can now be edited, if desired. If you also need your ISV partner as the originator of the multiparty private offer to make edits, request your ISV partner to also withdraw the multiparty private offer, update it, and submit it again to you to update and send to your customer for acceptance.

## Cancelling an accepted multiparty private offer

Once the customer accepts the multiparty private offer, selling partners are no longer be able to withdraw or edit the multiparty private offer. In some circumstances, where the multiparty private offer has been created with incorrect details such as incorrect pricing, incorrect public plan, or incorrect terms or dates, the selling partner should work with the customer and their ISV partner to confirm consent, and then submit a marketplace support request to cancel the multiparty private offer.

To do so, selling partners or the ISV can create a support ticket in Partner Center and request the multiparty private offer to be canceled.

You'll need to provide the following information:

- The private offer ID
- The customer billing account ID
- Reason for cancellation  
- Confirm whether refund is needed if the customer has already purchased. More purchase info is required if a refund is needed.
- A screenshot with written confirmation from both the other partner involved in configuring the multiparty private offer and from the customer that they agree to the cancellation.

Upon cancellation, the multiparty private offer will be removed from your multiparty private offer dashboard view in Partner Center and will also be removed from the customer’s Private Offer Management view in the Azure portal. After the cancellation has been processed, the multiparty private offer price will no longer be applied if the customer was to purchase the plan that was contained in the canceled multiparty private offer.

## Payout and reporting on multiparty private offers

The payout amount and agency fee that Microsoft charges is based on the partner price you received and the customer adjustment % you applied to the product prices.
  
- **Payouts**: Sales through multiparty private offers will be in [Payouts reporting](../payouts-overview.md), specifically under Payments, Transaction history, and Export data.
- **Analytics**: Sales through multiparty private offers are available in the [commercial marketplace insights](../analytics.md) dashboards, reports, and through programmatic access.

## Next steps

**Further reading**

- [Frequently Asked Questions](./multiparty-private-offers-faq.md) about configuring multiparty private offers

**Video tutorials (YouTube)**

- [Multiparty private offers: Selling partner configures one for their customer](https://www.youtube.com/watch?v=4VJKzg5LfA8)

- [Multiparty private offers: Customer accepts and purchases a private offer](https://www.youtube.com/watch?v=TANUlgLuVqI)”




