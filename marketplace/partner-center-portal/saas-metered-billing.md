---
title: Metered billing for SaaS offers in Partner Center
description: Learn about flexible billing models using a metering service for SaaS offers in Partner Center. 
ms.service: marketplace 
ms.subservice: partnercenter-marketplace-publisher
ms.topic: conceptual
ms.date: 03/29/2022
author: mingshen-ms
ms.author: mingshen
---

# Metered billing for SaaS using the commercial marketplace metering service

With the commercial marketplace metering service, you can create software as a service (SaaS) offers that are charged according to non-standard units. Before publishing a SaaS offer to the commercial marketplace, you define the billing dimensions such as bandwidth, tickets, or emails processed. Customers then pay according to their consumption of these dimensions, with your system informing Microsoft via the commercial marketplace metering service API of billable events as they occur.

## Prerequisites for metered billing

For a SaaS offer to use metered billing, it must first:

- Meet all of the offer requirements for a [sell through Microsoft offer](../plan-saas-offer.md#listing-options) as outlined in [Create a SaaS offer in the commercial marketplace](../create-new-saas-offer.md).
- Integrate with the [SaaS Fulfillment APIs](./pc-saas-fulfillment-apis.md) for customers to provision and connect to your offer.
- Be configured for the **flat rate** pricing model when charging customers for your service. Dimensions are an optional extension to the flat rate pricing model.

Then the SaaS offer can integrate with the [commercial marketplace metering service APIs](../marketplace-metering-service-apis.md) to inform Microsoft of billable events.
> [!NOTE]
>Marketplace metering service is available only to the flat rate billing model and does not apply to the per user billing model.

## How metered billing fits in with pricing

Understanding the offer hierarchy is important when it comes to defining the offer along with its pricing models.

- Each SaaS offer is configured to sell either through Microsoft or not. Once an offer is published, this option cannot be changed.
- Each SaaS offer, configured to sell through Microsoft, can have one or more plans. A user subscribes to the SaaS offer, but it is purchased through Microsoft within the context of a plan.
- Each plan has a pricing model associated with it: **flat rate** or **per user**. All plans in an offer must be associated with the same pricing model. For example, there cannot be an offer having plans for a flat-rate pricing model, and another being per-user pricing model.
- Within each plan configured for a flat rate billing model, at least one recurring fee (which can be $0) is included:
    - Recurring **monthly** fee: flat monthly fee that is pre-paid on a monthly recurrence when the user purchases the plan.
    - Recurring **annual** fee: flat annual fee that is pre-paid on an annual recurrence when the user purchases the plan.
- In addition to the recurring fees, a flat rate plan can also include optional custom dimensions used to charge customers for the overage usage not included in the flat rate. Each dimension represents a billable unit that your service will communicate to Microsoft using the [commercial marketplace metering service API](../marketplace-metering-service-apis.md).

> [!IMPORTANT]
> You must keep track of the usage in your code and only send usage events to Microsoft for the usage that is above the base fee.

> [!NOTE]
> Offers will be billed to customers in the customers’ agreement currency, using the local market price that was published at the time the offer was created. The amount that customers pay, and that ISVs are paid, depends on the Foreign Exchange rates at the time the customer transacts the offer. Learn more on ["How we convert currency?"](../marketplace-geo-availability-currencies.md).

## Sample offer

As an example, Contoso is a publisher with a SaaS service called Contoso Notification Services (CNS). CNS lets its customers send notifications either via email or text. Contoso is registered as a publisher in Partner Center for the commercial marketplace program to publish SaaS offers to Azure customers. There are three plans associated with CNS, outlined below:

- Basic plan

   - Send 10000 emails and 1000 texts for $5/month (flat monthly fee)
      - Beyond the 10000 emails, pay $1 for every 100 emails
         - Beyond the 1000 texts, pay $0.05 for every text
                  :::image type="content" source="media/saas-metered-billing/screenshot-2023-08-29-232846.png" alt-text="Screenshot of basic plan pricing." lightbox="media/saas-metered-billing/screenshot-2023-08-29-232846.png":::

          

- Premium plan

   - Send 50000 emails and 1000 texts for $350/year or 120000 emails and 3000 texts for $600/2 years or unlimited emails and 5000 texts for $850/3 years
   - Beyond the included quantity for emails, pay $1 for every 100 emails
   - Beyond the included quantity for texts, pay $0.02 for every text
      :::image type="content" source="media/saas-metered-billing/screenshot-2023-08-29-233910.png" alt-text="Screenshot of premium plan pricing." lightbox="media/saas-metered-billing/screenshot-2023-08-29-233910.png":::

- Enterprise plan

   - Send unlimited number of emails and texts for $50/month
      :::image type="content" source="media/saas-metered-billing/screenshot-2023-08-29-234350.png" alt-text="Screenshot of enterprise plan pricing." lightbox="media/saas-metered-billing/screenshot-2023-08-29-234350.png":::

   Based on the plan selected, an Azure customer purchasing subscription to CNS SaaS offer will be able to send the included quantity of text and emails per subscription term (month or year as appears in subscription details—startDate and endDate). Contoso counts the usage up to the included quantity in base without sending any usage events to Microsoft. When customers consume more than the included quantity, they do not have to change plans or do anything different. Contoso will measure the overage beyond the included quantity and start emitting usage events to Microsoft for charging the overage usage using the [commercial marketplace metering service API](../marketplace-metering-service-apis.md). Microsoft in turn will charge the customer for the overage usage as specified by the publisher in the custom dimensions. The overage billing is done on the next billing cycle (monthly, but can be quarterly or early for some customers). For a monthly flat rate plan, the overage billing will be made for every month where overage has occurred. For a yearly flat rate plan, once the quantity included in base per year is consumed, all additional usage emitted by the custom meter will be billed as overage during each billing cycle (monthly) until the end of the subscription's year term.

   ## Billing dimensions

   Each billing dimension defines a custom unit by which the ISV can emit usage events. Billing dimensions are also used to communicate to the customer about how they will be billed for using the software. They are defined as follows:

   - **ID**: the immutable dimension identifier referenced while emitting usage events.

   - **Display Name**: the display name associated with the dimension, for example "text messages sent".

   - **Unit of Measure**: the description of the billing unit, for example "per text message" or "per 100 emails".

   - **Price per unit in USD**: the price for one unit of the dimension. It can be 0.

   - **1-month quantity included in base**: quantity of dimension included per month for customers paying the recurring monthly fee, must be an integer. It can be 0 or unlimited.

   - **1-year quantity included in base**: quantity of dimension included per each year for customers paying the recurring annual fee, must be an integer. Can be 0 or unlimited.

   - **2-year quantity included in base:** quantity of dimension included for the 2-year term for customers paying the 2-year fee, must be an integer. Can be 0 or unlimited.

   - **3-year quantity included in base:** quantity of dimension included for the 3-year term for customers paying the 3-year fee, must be an integer. Can be 0 or unlimited.

>[!NOTE]
>Accuracy is to two decimal points (one cent), it is not unlimited, and Microsoft will truncate a meter less than $0.01 to zero.

> [!IMPORTANT]
> You must keep track of the usage in your code and only send usage events to Microsoft for the usage that is above the base fee.

   Billing dimensions are shared across all plans for an offer. Some attributes apply to the dimension across all plans, and other attributes are plan-specific.

The attributes, which define the dimension itself, are shared across all plans for an offer. Before you publish the offer, a change made to these attributes from the context of any plan will affect the dimension definition across all plans. Once you publish the offer, these attributes will no longer be editable. These attributes are:

- ID
- Display Name
- Unit of Measure

The other attributes of a dimension are specific to each plan and can have different values from plan to plan. Before you publish the plan, you can edit these values and only this plan will be affected. Once you publish the plan, these attributes will no longer be editable. These attributes are:

- Price per unit in USD

- 1-month quantity included in base

- 1-year quantity included in base

- 2-year quantity included in base

- 3-year quantity included in base

Dimensions also have two special concepts, "enabled" and "Unlimited":

- **Enabled** indicates that this plan participates in this dimension. If you are creating a new plan that does not send usage events based on this dimension, you might want to leave this option unchecked. Also, any new dimensions added after a plan was first published will show up as "not enabled" on the already published plan. A disabled dimension will not show up in any lists of dimensions for a plan seen by customers.
- **Unlimited** represented by the "Unlimited" checkbox against each included quantity, indicates that this plan participates in this dimension, but does not emit usage against this dimension. If you want to indicate to your customers that the functionality represented by this dimension is included in the plan, but with no limit on usage. A dimension with infinite usage will show up in lists of dimensions for a plan seen by customers, with an indication that it will never incur a charge for this plan.

>[!NOTE]
>The following scenarios are explicitly supported: <br> - You can add a new dimension to a new plan. The new dimension will not be enabled for any already published plans. <br> - You can publish a **flat-rate** plan without any dimensions, then add a new plan and configure a new dimension for that plan. The new dimension will not be enabled for already published plans.

   ### Setting dimension price per unit per supported market

   Like flat rate pricing, billing dimension prices can be set per supported country or region. You need to use the pricing data import and export feature in Partner Center, as follows.

   1. Define the desired dimensions and mark which markets are supported. 
1. Export this data into a file.
1. Add the correct prices per country/region and import the file in Partner Center.

   The user interface of the meter will change to reflect that the prices of the dimension can only be seen in the file.

   :::image type="content" source="media/metering-service-dimensions.png" alt-text="Screenshot of commercial marketplace metering service dimensions." lightbox="media/metering-service-dimensions.png":::

   ### Private plan

   Like flat rate plans, a plan with dimensions can be set as private plan, accessible only by the plan's defined audience.

   ## Constraints

   ### Trial behavior

   Metered billing using the commercial marketplace metering service is not compatible with offering a free trial. It is not possible to configure a plan to use both metered billing and a free trial.

   ### Locking behavior

   Because a dimension used with the commercial marketplace metering service represents an understanding of how a customer will be paying for the service, all the details for a dimension are no longer editable after you publish it. It's important that you have your dimensions fully defined for a plan before you publish.

   Once an offer is published with a dimension, the offer-level details for that dimension can no longer be changed:

- ID
- Display Name
- Unit of Measure

Once a plan is published, the plan-level details can no longer be changed:

   - 1-month quantity included in base

   - 1-year quantity included in base

   - 2-year quantity included in base

   - 3-year quantity included in base

   - Whether the dimension is enabled for the plan or not

   ### Upper limits

   The maximum number of dimensions that can be configured for a single offer is 30 unique dimensions.

   ## Get support

   If you have one of the following issues, you can open a support ticket.

  - Technical issues with marketplace metering service API.
- An issue that needs to be escalated because of an error or bug on your side (ex. wrong usage event).
- Any other issues related to metered billing.

   To understand publisher support options and open a support ticket with Microsoft, follow the instructions in [Support for the commercial marketplace program in Partner Center](../support.md).

   ## Next steps

- [Marketplace metered billing APIs](../marketplace-metering-service-apis.md)

**Video tutorials**

- [SaaS Metered Billing Overview](https://go.microsoft.com/fwlink/?linkid=2196314)
- [The SaaS Metered Billing API with REST](https://go.microsoft.com/fwlink/?linkid=2196418)
   

