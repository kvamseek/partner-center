---
title: Multiparty private offers FAQs
description: FAQs for configuring multiparty private offers in Microsoft Partner Center. 
ms.service: marketplace
ms.subservice: partnercenter-marketplace-publisher
ms.topic: how-to
author: emerb19
ms.author: emerb
ms.date: 09/21/2023
ms.custom: references_regions
---

# Multiparty private offers FAQ

**Appropriate roles**: ISVs and Selling Partners

This article answers frequently asked questions about multiparty private offers for ISVs and selling partners.

## General

### What are private offers and what are multiparty private offers?

Cloud marketplaces are outpacing cloud growth and becoming the centralized go-to-market channel of the future. Private offers empower custom deal making and are the key to unlocking enterprise customers and offer benefits like negotiated pricing, private terms and conditions, and specialized configurations. There are three types of private offers:

- **Private offers for customers**: Offer the ability for ISV partners to create a private offer to sell directly to a customer. If the customer has a cloud consumption commitment with Microsoft, the sale can count towards the customers’ commitment if the offer is Azure IP co-sell incentivized. To learn more, see [ISV to customer private offers](./isv-customer.md).

- **Private offers with margin-sharing**: Offer the ability for ISV partners to extend a margin to motivate partners in the Cloud Solution Provider program (CSPs) to sell their solution. This gives ISVs an advocate for their product while helping ISVs scale to sell in the SMB market. For CSPs, it gives them the opportunity to package ISV solutions with their software and services sales to offer unique customer value. To learn more, see [ISV to CSP partner private offers](./isv-csp-reseller.md) and [Marketplace margins](../csp-commercial-marketplace-margins.md).

- **Multiparty private offers**: Multiparty private offers empower eligible partners to come together, create personalized offers with custom payouts, and sell directly to Microsoft customers with simplified selling through the marketplace. And for customers that have a cloud consumption commitment, every dollar of the sale counts toward their commitment when they purchase solutions that are Azure IP co-sell eligible. It also enables the customer’s preferred partner to work with ISVs on marketplace deals and specify a custom price to that partner for the deal.

| Comparison                                          | **Private offers for customers**                                                                        | **Private offers with CSP margin-sharing**                                                                                                       | **Multiparty private offers**                                                                                                                                                                                                                                                            |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Target audience                           | ISV partners | ISV partners, Partners in the Cloud Solution Provider program (CSPs)  | ISV partners, Selling partners with United States tax profiles for marketplace in Partner Center |
| Availability                              | [Available today](/marketplace/private-offers-in-azure-marketplace)          | [Available today](/azure/marketplace/isv-csp-reseller)                                                                | Available today for customers purchasing in the United States  |
| Customer MACC decrement for eligible apps | Yes                          | No                                                                    | Yes                                                    |
| Selling partner participation             | No participation. ISV sells private offer directly to customer.                                        | [CSP program enrolled partners](../enrolling-in-the-csp-program.md) only. ISV sends a private offer to CSP. | Partners enrolled in the Microsoft AI Cloud Partner Program and enrolled in the [commercial marketplace](/azure/marketplace/create-account) with United States tax profiles for marketplace in Partner Center. ISV partner sends a private offer to the partner. |
| Target customers                          | Enterprise\*                              | SMB/C\*                                                               | Enterprise\*                                            |
| Billing                                   | Microsoft bills to customers (Note: For Indirect EA deals, partners (seller) handle customer billing.) | CSP partners bill to customers                                                                                                                   | Microsoft bills to customers (Note: For Indirect EA deals, the indirect EA partner handles customer billing.)                 |

> [!NOTE]
> There are always exceptions, and the different private offers are viable for all segments, but to prioritize, private offers and multiparty private offers are best suited for the enterprise, and margin sharing private offers are best suited for the SMB/C market.

### What are the key benefits of multiparty private offers to customers and partners?

Benefits vary depending on audience but ultimately the value of multiparty private offers is that the customer can maintain their trusted partner relationships and partners can work together to create customized solutions for customers using their unique cloud services.

- **Customer benefit:** Many customers have preferred partners that they buy their software from. With multiparty private offers, customers can maintain their trusted partner relationships while streamlining the procurement and deployment of the solution(s) through the commercial marketplace. Partners can procure ISV solutions on the customer’s behalf and package that into the offer for the customer—simplifying the process and consolidating transactions. And now with multiparty private offers, customers with a cloud consumption commitment can count their purchase towards their cloud consumption commitment. Microsoft is unique in that 100% of sales count towards a customer’s Microsoft Azure Consumption Commitment automatically when customers buy eligible solutions. Using precommitted cloud spend is one of the main motivators for customers to buy through cloud marketplaces. With multiparty private offers, customers are able to purchase through their preferred partner and still have the sale count towards their cloud consumption commitment. To learn more, see [Azure Services and Marketplace offers that are eligible for MACC](/azure/cost-management-billing/manage/track-consumption-commitment?tabs=portal#azure-services-and-marketplace-offers-that-are-eligible-for-macc). ​​

- **ISV partner benefit:** Many customers utilize partners as trusted advisors for purchasing, implementation, and support decisions. Multiparty private offers unlock deals for ISVs when the partner owns the customer relationship and needs to be included in the transaction.

- **Selling partner benefit:** Multiparty private offers give partners selling software and services the ability to work with ISVs, create personalized offers with customized payouts together, and sell directly to Microsoft customers through the marketplace having the software sale count toward the customers’ cloud consumption commitment. This unlocks new opportunities where partners can proactively collaborate on enterprise deal-making and help manage the customer’s broad technology estate as trusted advisors.

### Which customers can purchase multiparty private offers?

Multiparty private offers are available to customers purchasing in the United States.

Customers can purchase multiparty private offers with an Enterprise Agreement (EA), Microsoft Customer Agreement (MCA), Indirect Enterprise Agreement (Indirect EA), and through web direct motions. Customers need to provide their partner or the ISV with their billing account ID – customers can run the [eligibility check tool](https://aka.ms/poprecheck) and download the report to identify their billing account ID and verify if they're approved to purchase via the marketplace. Alternative ways to find the billing account ID can be found in the [Azure portal](https://aka.ms/posetup). For customers with an Enterprise Agreement (EA) with Microsoft, billing account ID is the same as their EA enrollment number.

### What are the partner qualification criteria to sell through multiparty private offers?

Any partner selling through multiparty private offers will need to be a member of the Microsoft AI Cloud Partner Program and be actively using the Microsoft commercial marketplace as a go-to-market and sales channel.

ISVs or partners that build software or SaaS solutions must have a [transactable offer](/azure/marketplace/marketplace-commercial-transaction-capabilities-and-considerations) with public plan(s) available to participate in multiparty private offers. If the ISV is new to Microsoft or doesn't yet have a transactable offer and needs assistance, the [ISV Success](https://www.microsoft.com/isv/program-benefits) program can help.

Selling partners need to be [enrolled in the commercial marketplace](/azure/marketplace/create-account), have a [US tax profile set up in Partner Center for marketplace](/partner-center/set-up-your-payout-account), and [file their resale certificates](/partner-center/marketplace/multiparty-private-offers-for-selling-partners) with Microsoft to be eligible to sell through multiparty private offers. Sales through multiparty private offers are limited to customers purchasing in the United States.

ISVs across the globe are invited to participate - the only caveat is the selling partner you work with needs to have a US tax profile set up in Partner Center and the customer needs to purchase in the United States.

### What are the key differences between the margin sharing private offers and multiparty private offers? Can partners in the Cloud Solution Provider program participate?

The CSP partner private offer (also known as margin sharing) is a private offer type that is designed to motivate eligible partners to sell an ISV’s solution. ISVs can make private offers and extend a margin to partners in the Cloud Solution Provider program (CSPs). This is intended to help ISVs reach small and medium sized customers by scaling through the Microsoft ecosystem of over 90,000 partners in the Cloud Solution Provider program. With margin sharing, the CSP partner owns the end-to-end customer relationship including the pricing strategy and billing. They bill the customer outside of the marketplace (the deal is done on the CSP’s contracts).

All partners including partners enrolled in the CSP Program can participate in multiparty private offers and work with ISV partners to create custom private offers for customers with an enterprise agreement (EA) or Microsoft Customer Agreement (MCA). The partner still owns the customer relationship but with multiparty private offers, the customer purchases directly through the marketplace and Microsoft bills the customer.

### What should ISVs do to prepare for multiparty private offers?

To prepare for the multiparty private offer opportunity, ISVs should have transactable solutions published to the commercial marketplace. Once they have their offer listed, they should use the current private offer capabilities and build relationships with other partners.

| **Journey stage**     | **Next action**  |**Resources**                          | **Notes**                               |
| ------------------------------------------------------------------------------------------ | ------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ISV who isn't yet a partner                                                               | Become a partner                                              | [Microsoft AI Cloud Partner Program](https://partner.microsoft.com/partnership), [ISV Success Program](https://www.microsoft.com/isv/program-benefits)  | All ISVs must be partners to use multiparty private offers. ISVs can join the Microsoft AI Cloud Partner Program on their own or get guidance with the ISV Success program. |
| ISV partner who isn't listed on the marketplace    | Get published on the commercial marketplace                   | [ISV Success Program](https://www.microsoft.com/isv/program-benefits), [Marketplace Overview and Q&A for partners](https://microsoftcloudpartner.eventbuilder.com/MarketplaceOverviewandQAforPartners)            | [Marketplace Summit presentation](/events/marketplace-summit-2022/microsoft-marketplace-summit-november-2022-the-opportunity-for-isvs-with-microsoft) (The opportunity for ISVs with Microsoft)                     |
| ISV partner who is listed on marketplace, but not transactable                             | Publish a transactable solution on the commercial marketplace | [ISV Success Program](https://www.microsoft.com/isv/program-benefits), [Marketplace Overview and Q&A for partners](https://microsoftcloudpartner.eventbuilder.com/MarketplaceOverviewandQAforPartners) , [ISV Transact & Grow incentive](https://partner.microsoft.com/asset/collection/marketplace-transact-and-grow-incentive-campaign#/) | [Marketplace Summit presentation](/events/marketplace-summit-2022/microsoft-marketplace-summit-november-2022-get-listed-in-the-marketplace-and-jumpstart-your-cloud-go-to-market-strategy) (Get listed in the marketplace to jumpstart your cloud go-to-market)      |
| ISV partner who has transactable offer but isn't Azure IP co-sell incentive               | Become Azure IP co-sell incentivized                          | [Enroll to be MACC-eligible](/azure/marketplace/azure-consumption-commitment-enrollment)                                   | [Marketplace Summit presentation](/events/marketplace-summit-2022/microsoft-marketplace-summit-november-2022-co-sell-with-microsoft-and-land-enterprise-deals-through-the-marketplace) (Co-sell with Microsoft and land enterprise deals) |
| ISV partner who is Azure IP co-sell incentivized and has transactable offer on marketplace | Build relationships with other partners                       | [Partner Finder](https://appsource.microsoft.com/marketplace/partner-dir)  | |

### What should selling partners do to prepare for multiparty private offers?

For partners in the CSP program, start selling ISV solutions via [ISV to CSP margin Sharing private offers](../csp-commercial-marketplace-margins.md) and expand to multiparty private offers.

For partners that aren't in the Cloud Solution Provider program, start building your network of partnerships with ISVs and identify [Azure benefit eligible solutions](/marketplace/azure-consumption-commitment-benefit#determine-which-offers-are-eligible-for-azure-consumption-commitments-maccctc). Additionally, selling partners need to [enroll in the Microsoft commercial marketplace](/azure/marketplace/create-account) on Partner Center, have a completed United States tax profile associated to their marketplace seller ID, and provide their resale certificates to Microsoft in advance to any sales through this offering.

### As a selling partner, if my company has already provided our resale certificates to Microsoft for another program, such as the Cloud Solution Provider (CSP) program or Volume Licensing (VL) program, do we need to resubmit our resale certificates to Microsoft for sales of multiparty private offers?

Yes. **Selling partners must provide your resale certificate(s) to Microsoft at least 5 business days before the sale of any multiparty private offer**. Resale certificate(s) must be provided for each seller ID used to sell multiparty private offers and must be provided even if your company has already provided them for other programs such as the Cloud Solution Provider program. Your certificate(s) must be accurately completed and signed and must include the state where your company is headquartered at a minimum. Your resale certificates must be on file at Microsoft before you sell multiparty private offers, or sales tax may be charged on your purchase as required by various tax laws. To file your tax exemption(s), [request support through Partner Center](https://partner.microsoft.com/dashboard/support/servicerequests/create?stage=2&topicid=96277724-9b43-e131-2ddb-94f18f0a8dde). Provide your marketplace seller ID and supply the appropriate information.

### What are the multiparty private offer terms and conditions?

Multiparty private offers will adhere to the policies and terms included in the Microsoft Publishers Agreement, the Commercial Marketplace Terms of Use, the commercial marketplace certification policies, and the commercial marketplace review policies. View the specific terms for multiparty private offers within the [Microsoft publishers agreement Addendum B](/legal/marketplace/msft-publisher-agreement#addendum-bterms-and-conditions-applicable-to-specific-go-to-market-channels).

## Creating multiparty private offers

### What offer types can be sold through multiparty private offers?

Multiparty private offers can be created for all transactable marketplace offer types: SaaS, Azure Virtual Machines, and Azure Applications. The commercial marketplace [does not support the sale of hardware or professional services](/legal/marketplace/certification-policies), nor does it support offers in Microsoft AppSource.

### What is a customer billing account ID and where can I find it for my customer?

To create a multiparty private offer, you need the billing account ID of your customer. Customers can find the billing account information in the Azure portal either in:

- **Cost Management + Billing > Settings > Properties** or,
- If customer knows the subscription they plan to use for the purchase, select: **Subscriptions** > select the relevant subscription > **Properties** (or Billing Properties). The customer must be an owner or contributor on the billing account to access this information.
  
If a customer doesn't have a billing account, they can create one by signing up on [Azure.com](https://azure.com). See [Billing account scopes in the Azure portal](/azure/cost-management-billing/manage/view-all-accounts).

Applying the multiparty private offer at the Billing Account ID level means that if new subscriptions are added to the customer's Azure plan, the multiparty private offer will automatically apply to those subscriptions also and no edits need to be made to the multiparty private offer.

Billing account information is only available to the customer and can't be accessed by ISV partners or selling partners.

### When should I use Accepted date vs. Specific month for the start date? Or can I use a specific date in the month as the start or end date for the multiparty private offer?

While creating a new multiparty private offer, select **Accepted date** as the start date to make the price available for the customer to transact as soon as the multiparty private offer is accepted. If you want a private price to be available to the customer immediately on acceptance, choose **Accepted date**.

Choose specific month to make the multiparty private price available in a future calendar month. Example: If you create a multiparty private offer on May 15 and want the private price to be available to the customer on June 1, select June. The multiparty private offer starts on the first day of the month and end on the last day. You can't select specific start and end dates. If a customer purchases the public offer/plan prior to June 1, they won't see the multiparty private offer price nor receive the private price for any transactions before June 1.

> [!NOTE]
> If a multiparty private offer is extended to an existing customer of pay-as-you-go (PAYG; consumption-based) products (like Virtual Machines), selecting Accepted date will make the private price applicable for the entire month. For example: if you create a multiparty private offer on May 15 for a Virtual Machine product for an existing customer and select Accepted date, the private price will be applied for the entire month on the month of acceptance.

### How is Accept by date different from End date?

Accept by date is the offer's expiration date. Your customer must accept the multiparty private offer on or before this date or it expires. The End date specifies the date on which the multiparty private price/terms ends.

### What is the difference between Absolute price and Discounted price type in a multiparty private offer?

ISV partners can use discounted price to provide a percentage-based discount on top of a publicly listed plan. This can only be used when the private price is lower than the publicly listed plan price. The absolute price can be used to specify a price point higher, lower, or equal to the publicly listed plan price, and can only be applied at a plan level. Absolute price can be applied to virtual machine software reservation offers but cannot be applied for virtual machine offers or any plans that have a trial enabled.   

### What is Clone?

ISV partners can use Clone to make an editable copy of an existing multiparty private offer and publish as a new one. Clone can be used on any multiparty private offer regardless of its status.

### What is Upgrade? 

This allows ISV partners to upgrade an existing accepted multiparty private offer. Marketplace only supports upgrades at renewal; for example, the upgraded offer Start and End date can’t overlap with the existing multiparty private offer. ISV partners can only edit pricing, dates, terms, and notification contacts for the upgraded multiparty private offer before sending it to the selling partner to finalize and send to the customer for acceptance and purchase. If other changes are needed, such as an additional plan, create a new multiparty private offer.

### My customer accepted a multiparty private offer and is already using it. Can I submit another upgrade to extend the multiparty private offer?

Multiparty private offers can’t be upgraded mid-term. An ISV partner can create an upgrade at any time before sending it to the selling partner to finalize and send to the customer for acceptance, but the upgrade will only take affect at the end of the existing multiparty private offer.  

### Can ISVs and selling partners include their own custom terms and conditions on the multiparty private offer deals?

Yes. ISVs and partners can attach up to five customer terms and conditions that the customer needs to accept as part of the multiparty private offer. Multiparty private offers currently don't support the ability for ISVs and partners to exchange partner-only terms for acceptance that don't get passed to the customer.

### Can a multiparty private offer be withdrawn before the customer purchases?

Yes. Withdrawing a multiparty private offer means your customer will no longer be able to access it.

For ISVs, a multiparty private offer can only be withdrawn by an ISV if the status is **Pending partner action**. A multiparty private offer can't be withdrawn by an ISV if your partner on the deal has already sent it to the customer and the status is **Pending acceptance** or **Accepted** by the customer.  

For selling partners, a multiparty private offer can only be withdrawn by selling partners if the status is **Pending acceptance**. A multiparty private offer can't be withdrawn if the customer has accepted the multiparty private offer and the status is **Accepted** by the customer.

### Is there an API for multiparty private offers?

Yes. ISV partners and selling partners should use the same set of [API calls](/partner-center/marketplace/create-multiparty-private-offer-for-a-customer-api) to create a multiparty private offer for a customer.

## Customer acceptance and purchase

### How do customers purchase multiparty private offers?

Customers purchase multiparty private offers the same why they accept and purchase private offers today through the commercial marketplace. To learn more, see [Purchase a private offer](/marketplace/purchase-a-private-offer).

### Why can’t my customer access the multiparty private offer link I shared?

Any user within the customer’s organization can see the details of the multiparty private offer. To accept a multiparty private offer, the user in the customer organization needs to be an owner, contributor, or admin on the Azure account. Without appropriate permissions, the user can't accept the multiparty private offer. To get access to the billing account, the user should contact the billing account admin or owner. A red notice at the top of the page indicates three people within the customer’s organization who have the appropriate permissions to reach out to.

### Why can’t I make changes to a multiparty private offer after it’s accepted?

Once a multiparty private offer is accepted, it’s a legal agreement between you and the customer and hence it can’t be changed.

### My customer accepted the multiparty private offer. What’s next?

If the multiparty private offer is due to begin on the Accepted date, the customer can go to the Azure portal to subscribe to the offer using any Azure Subscription associated with the billing account. They must use an Azure subscription associated with the configured billing account to get the private price. If the multiparty private offer includes PAYG offers (Virtual Machines) and was extended to an existing customer, the customer will be charged using the private price as soon as the multiparty private offer is accepted.

For a multiparty private offer that includes SaaS, the customer must subscribe to the software as a service (SaaS) product first and then configure the product within 30 days of subscribing to the product.

If the ISV has configured the multiparty private offer to begin at a future date, the customer can accept the multiparty private offer before the Accept by date but shouldn't subscribe to or deploy the product until after the Start date set for the multiparty private offer.

### My customer accepted the multiparty private offer, but the private price is still not reflected in the marketplace products page

Once the customer has accepted the multiparty private offer, it can take up to 15 minutes for the private price to be reflected in the marketplace on the Private products details page. If the customer transacts within these 15 minutes, the marketplace will still charge the customer correctly using the private price. Additionally, if the multiparty private offer was configured to start in a specific month, the customer won't see the multiparty private offer price nor receive the private price until that month.

### My customer accepted the multiparty private offer. When will they be billed?

Accepting a private offer doesn't initiate billing. Before billing begins, the customer must accept the multiparty private offer and then subscribe to the software as a service (SaaS) product or deploy the virtual machine or Azure application product that's contained in the multiparty private offer in the Azure portal.

For a multiparty private offer that includes a SaaS product, the customer must also configure the product within 30 days of subscribing to the product.

### How can I distinguish a SaaS purchase is for multiparty private offer?

The SaaS fulfillment API has been updated to return private offer ID when a subscription is for a multiparty private offer. Follow these steps to verify: 

1. Retrieve the subscription ID and Plan ID as prerequisites. You can get both either through the **Resolve** (when purchase request comes to the landing page) or via the **Get Subscription** calls, both will return the correct Plan ID in the response. 

1. Then call the [SaaS fulfillment subscription APIs](./partner-center-portal/pc-saas-fulfillment-subscription-api.md#list-available-plans), and make sure to pass in the correct Plan ID from the previous step. The response will return the multiparty private offer ID as the external ID if the subscription is for a multiparty private offer. See the following example:

```json
"sourceOffers": [ //sourceOffers is returned when planId is passed as filter parameter (note that this is the plan that customer has purchased). 
        { 
"externalId": "<guid>" //private offer id, returned when purchase is made through private offer. 
        } 
      ] 
```

### What happens when my multiparty private offer ends?

If the customer has autorenew enabled, and you don't create a new multiparty private offer that the customer accepts, the customer will be charged at the list price of the public plan.

### What happens if I publish more than one multiparty private offer and/or customer private offer to the same customer with overlapping products and timeframes?

A multiparty private must be unique and not overlap with another multiparty private offer or another customer private offer for the same customer using the same public plan for the same timeframe regardless of the selling partner. Overlapping multiparty private offers are blocked at submission. To remedy this problem, you have the option to create another similar public plan and configure your multiparty private offer to the same customer with this different plan.

## Payments and reporting

### When will partners receive their payments for sales of multiparty private offers?

Payouts to ISVs and partners follow the commercial marketplace payout schedules and processes. To learn more, see [Payout policy details](../payout-policy-details.md).

### Will there be a marketplace agency fee to ISVs and selling partners for sales of multiparty private offers?

The standard commercial marketplace agency fee applies to ISVs on their partner price they configure to their selling partner. The standard marketplace fee won't be applied to the selling partner’s markup. To learn more, see [Multiparty private offers](/legal/marketplace/msft-publisher-agreement#1multi-party-private-offers-mpo).

### What reporting will be available in Partner Center for multiparty private offers?

Sales of multiparty private offers will be visible in the Partner Center payouts reporting specifically under payments, transaction history, and export data. To learn more, see [Payouts](../payouts-overview.md). Look for the column **isPrivateOffer** to determine if the sale is a private offer sale. Sales will also be visible in marketplace analytics reporting within the revenue, orders, and usage dashboards and exports, and via programmatic access. To learn more, see [Access insights for the commercial marketplace in Partner Center](/azure/marketplace/analytics). To connect the payout reporting to the analytics reporting use **OrderID**. ISVs will have visibility to the customer, the products, and their partner on the deal along with the partner price they configured for their partner. Partners will have visibility to the customer, the products, their ISV on the deal, the partner price they received from their ISV, the customer adjustment they configured, and the customer’s price.


