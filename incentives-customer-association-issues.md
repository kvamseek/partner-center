---
title: Incentives customer association issues
description: Learn how to address issues that come up when working with Claiming Partner of Record (CPOR) customer associations.
ms.topic: how-to
ms.service: partner-dashboard
ms.subservice: partnercenter-incentives
author: DivyaAdam
ms.author: diadam
ms.date: 10/10/2023
---

# Issues with Claiming Partner of Record (CPOR) customer associations

**Appropriate roles**: Billing admin | Global admin | Incentives admin

The following content helps you to solve issues that can come up when you work with customer associations via the Claiming Partner of Record (CPOR) claiming platform. This platform is used for incentives and usage/competency attainment and revenue association. CPOR shouldn't be confused with Cloud Solution Provider (CSP) customer associations.

## Domain-tenant mismatch

In the CPOR association claim flow, you're asked to provide the customer tenant ID and subdomain. If you receive an error stating that they don't match, contact your customer to ensure you have the correct details.

## Subscription errors in the CPOR association claim flow

In the CPOR association claim flow, you might be asked to provide a subscription for a product that you're trying to claim via Business Applications (Dynamics 365). We ask for the subscription because we're dynamically checking that the product and subscription belong to the tenant being claimed for. Post claim, we're also checking that the subscription is in active/grace status so that incentives can be earned.

If you receive an error when entering in a subscription, it could be for several reasons:

- The product selected doesn't exist on the customer's tenant
- The subscription provided isn't for Dynamics
- The subscription provided is for CSP
- The customer hasn't yet activated/provisioned the products for that subscription
- The identifier provided isn't a subscription ID

If you have a question about the accuracy of your subscription, work with your customer to ensure the subscription is correct and that you're using the correct tenant ID.

If this route hasn't resolved your issue, contact [support](https://partner.microsoft.com/dashboard/v2/support/incentives/servicerequests?category=incentives).

## When subscriptions are available to claim

When claiming for a subscription, you receive an error if the subscription hasn't been provisioned yet. There are several steps the customer needs to take for the subscription to become available for the CPOR platform to pick it up and make it available to claim. Once the customer has completed the provisioning on their side, it can take up to seven days to reflect in the CPOR claiming flow. If you're receiving an error when trying to claim a subscription, contact your customer to ensure that it has been provisioned and the subscription you're claiming is correct. If you've taken this route already, contact [support](https://partner.microsoft.com/dashboard/v2/support/incentives/servicerequests?category=incentives).

## Which partner role do I choose?

The CPOR claiming platform allows for CPOR association claims related to Business Applications and Modern Work and Security solution areas. The partner roles that are applicable to each solution area follow. Select the correct partner role based on the descriptions to avoid having to reclaim in the future. Claiming with an incorrect partner role might result in missed eligibility and incentive earnings.

| Solution area | Partner role | Applicable for   |
|---|---|---|
| Business applications    | Build intent - Advisor | Select if you influenced their purchase of an eligible product and want to apply for presale incentives. This option is only applicable if the customer purchased these products via Volume Licensing agreement or Web-Direct.  |
|  | Usage recognition - Non-Incentivized  | Select if you drive their adoption and usage of an eligible workload and want to apply for usage incentives. This option is only applicable if the customer purchased these products via Volume Licensing agreement or Web-Direct.  |
|   | Influenced Revenue recognition - Non-Incentivized  | Select if you influenced their selection of an eligible product as a Business Influencer. This option is for revenue association only, not for incentive payments. This option is only applicable if the customer purchased these products via Volume Licensing agreement or Web-Direct. |
| Modern Work and Security | Use or consume  | Select if you drive their adoption and usage of an eligible workload, and you want to apply for usage incentives and/or usage/competency attainment.    |

## Which Microsoft AI Cloud Partner Program do I choose?

In the CPOR association claim flow, you're asked to choose a company that should be associated to the work you're claiming for at the end customer. Your company might have many Microsoft AI Cloud Partner Programs, some of which might be enrolled in incentive programs, and others associated with a partner type such as FRP FastTrack. The CPOR association claim flow identifies which are enrolled in an incentive program, but it doesn't tell you if it's a specific partner type. It's important to select the correct Microsoft AI Cloud Partner Program to avoid having to reclaim in the future. Claiming with an incorrect Microsoft AI Cloud Partner Program might result in missed eligibility and incentive earnings.

If you don't know which Microsoft AI Cloud Partner Program to use, contact your global admin.

If the Microsoft AI Cloud Partner Program you're wanting to use isn't enrolled, you can manage that in the [Incentives overview tab](https://partner.microsoft.com/dashboard/incentives/enrollment/summary) (Signing in is required).

## Choosing a product vs entering a subscription

When a Dynamics product is being claimed, you might be asked to provide a subscription. You're asked when the customer has numerous subscriptions for the product being claimed, and we need to know which subscription to identify and calculate upon incentive eligibility.  

The subscription ID changes once it expires, and you need to create a new claim with the new subscription ID to continue earning.

## Competing claims

If you're creating a CPOR association claim for a customer, and there are products that are already associated with another partner, your claim goes through arbitration:

-  After you create a new customer association, Microsoft verifies the details of the association and the proof of execution provided to ensure its accuracy.
- If you and another partner claim the same customer and product/workload, Microsoft reviews each partner's proof of execution documentation to determine which partner to approve.
- Additional information might be requested from both partners, which could cause delays in processing your association request.
- Your CPOR association claim will still be reviewed within five business days, although its status might stay as _Under Review_ for a longer period of time. This scenario can happen when Microsoft works with the partner currently owning the product/workload. You're notified within the comments section of your claim if that is the case.

> [!IMPORTANT]
>If we require additional information to verify your CPOR association proof of execution (PoE), we'll contact you via the CPOR association claim comments section.

## Next steps

- [Getting started with incentives](incentives-get-started-intro.md)
