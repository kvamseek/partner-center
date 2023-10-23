---
title: Supported CSP partner relationships
ms.topic: article
ms.date: 1/11/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-enroll
description: Learn about different partner relationships and supported transaction scenarios for partners in the CSP program.
author: JulCsc
ms.author: sabajaj
---

# Learn how partners can work with other partners in the CSP program

**Appropriate roles**: All partners interested in learning more about CSP

This article describes the key types of partner relationships in the Microsoft Cloud Solution Provider (CSP) program. It also describes various use cases, benefits, and supported transaction scenarios for CSP program partners.

Being a partner in the CSP program allows you to go beyond reselling licenses so that you can be more involved in your customers' business. The CSP program puts partners at the center of the relationship with the customer. This leads to deeper engagement with your customers, an insider's view to a customer's business, and the chance to uncover new sales opportunities. It can even help you accelerate your customer's digital transformation.

Being a CSP program partner also means you can harness additional profitability streams. You can do so by integrating Microsoft (first-party) offers and third-party offers with your own, value-added services. This expands your business portfolio and better positions you to meet growing customer demands.

## Types of partner relationships in the CSP program

As a partner in the CSP program, you can decide how you want to interact with Microsoft and with others. The CSP program currently supports three, main types of transactional relationship:

- Indirect providers
- Indirect resellers
- Direct-bill partners

**Indirect providers** (also known as distributors) purchase first-party offers and third-party offers from the Microsoft marketplace. As an indirect provider, you can purchase and integrate these offers into your own, existing commerce or marketplace. This then lets your indirect resellers procure such offers and resell them to their own customers. Being an indirect provider means you have the infrastructure and capabilities to support indirect resellers at scale. It also means you can provide additional services to customers on behalf of your indirect resellers, such as customer support and billing. To learn more about how indirect providers connect with indirect resellers, see [Partner with indirect resellers in the CSP program](indirect-provider-tasks-in-partner-center.md).

**Indirect resellers** are partners in the CSP program who vary in size and business scope, but who don't have a direct billing relationship with Microsoft. As an indirect reseller, you depend on indirect providers to transact in the CSP program. Some indirect resellers may also be able to offer managed services, support, and billing solutions to customers. You can receive several benefits from your partnership with indirect providers. By working with experienced technology providers, you can go to market without having to make a large capital investment. As an indirect reseller, you can also access a broader portfolio of Microsoft and third-party solutions. To learn more about becoming an indirect reseller, see [Indirect reseller tasks in Partner Center](indirect-reseller-tasks-in-partner-center.md).

**Direct-bill partners** are partners with a direct billing relationship with Microsoft. As a direct-bill partner, you can purchase first-party offers and third-party offers directly from the Microsoft marketplace, then sell them to your customers. You need to fulfill certain programmatic requirements for the role of direct-bill partner. This includes the ability to integrate with Microsoft using APIs. You also need to be able to provide billing, support, and managed services to customers on an on-going basis. For more information, see [Enroll as a direct-bill partner](enrolling-in-the-csp-program.md#enroll-as-a-direct-bill-partner).

## CSP program requirements: Signing the Microsoft Partner Agreement (MPA)

As part of the Cloud Solution Provider program's continuous enhancements, we've updated the existing agreements for partners who want to join the CSP program.

The **Microsoft Partner Agreement (MPA)** gives partners a streamlined, digital agreement that supports new business scenarios, a reduced need for multiple partner contracts, and easier compliance with global, legal requirements.

> [!IMPORTANT]
> Starting February 1, 2020, the Microsoft Partner Agreement must be signed by all partners who transact in the CSP program. This includes indirect providers, direct-bill partners, and indirect resellers.

An indirect reseller needs to sign the MPA before the reseller can participate in the following activities:

- Before an indirect provider can associate the indirect reseller's PartnerID to a new CSP subscription
- Before an indirect provider can transact new business with that reseller

In fact, indirect resellers need to do three things before they can transact new business in the Cloud Solution Provider program:

- Onboard into Partner Center
- Enroll as an indirect reseller
- Sign the Microsoft Partner Agreement (MPA)

For more information, see [Microsoft Partner Agreement (MPA) for CSP partners](microsoft-partner-agreement.md).

## Supported partner transactions in the CSP program

Partners in the CSP program are offered many opportunities to work together. The following section describes how a few, sample partner scenarios may or may not be supported in the CSP program.

**Sample scenario 1:** What if a partner wants to sell to the customer, own the end-to-end relationship, and be responsible for billing and customer support?

This scenario is supported by two types of transactional relationship:

- **Relationship 1:** Microsoft sells to the direct-bill partner. The direct-bill partner then sells to the end customer.
- **Relationship 2:** Microsoft sells to the indirect provider. The indirect provider then sells to the indirect reseller. The indirect reseller then sells to the end customer.</br>

**Sample scenario 2:** What if a partner has a customer who needs a specific service or solution offered by another CSP program partner?

The end customer can purchase different services from different partners, based on the customer's business needs. For more information, see [Multi-partner support](multipartner.md).

**Sample scenario 3:** What if a partner is contacted by a customer who wants to hire them to manage and support their subscriptions?

The customer can engage multiple partners to manage their subscriptions. For more information, see [Multi-channel support](multichannel.md).

**Sample scenario 4:** What if a partner in the CSP program (either an indirect provider, indirect reseller, or direct-bill partner) wants to buy Microsoft or third-party offers for their own use (as an end-customer)? Can the partner buy such offers from another CSP program partner?

The partner can buy as a customer from either an indirect reseller or from a direct-bill partner. To do so, however, they must use a different tenant than the one used for CSP.

In this case, services bought by the partner need to be provisioned to a tenant designated as a Customer type (a tenant for internal use only). Such services **cannot** be provisioned to the existing partner's CSP tenant (the tenant used by the partner in the Cloud Solution Provider program).</br>

**Sample scenario 5:** What if a partner in the CSP program wants to sell to themselves as an end-customer?

By contract, partners in the CSP program are not allowed to sell Microsoft or third-party offers to themselves (as end-customers) or to their affiliate organizations (as end-customers).

**Sample scenario 6:** What if an indirect reseller wants to purchase as an end-customer?

Certain indirect resellers may want to purchase licenses for their own use from an indirect provider in the CSP program. For this scenario, the indirect reseller's organization may have already established an indirect provider-indirect reseller relationship. Doing so prevents the partner from establishing any new relationship type as an end-customer with the same indirect provider.

In this case, the indirect reseller can use one of the following options:

- **Option 1:** Partners can set up another Azure AD tenant that is a separate environment for their customers.

- **Option 2:** The indirect reseller can end the relationship with one indirect provider and establish a new CSP relationship with another indirect provider. Doing so allows the indirect reseller to purchase subscriptions for their company's own use from a different CSP direct-bill partner.

   > [!NOTE]
   > To end the relationship between an indirect provider and an indirect reseller, contact [Microsoft Support](support-from-microsoft.md).

- **Option 3:** The reseller can keep their customer relationship with the existing indirect provider and establish another indirect reseller relationship with another indirect provider.

**Sample scenario 7:** What if an indirect reseller wants to sell to a customer who is in a different region?

A partner in the CSP program can only sell to customers from the same region. For more information, see [Cloud Solution Provider program regional markets and currencies](regional-authorization-overview.md).

**Sample scenario 8:** What if an indirect provider wants to establish a relationship with an indirect reseller in a different region?

A partner can only establish a relationship with a partner from the same region.

## Next steps

- [Partner with indirect resellers in the CSP program](indirect-provider-tasks-in-partner-center.md)
- [Indirect reseller tasks in Partner Center](indirect-reseller-tasks-in-partner-center.md)
- [Enroll as a direct-bill partner](enrolling-in-the-csp-program.md#enroll-as-a-direct-bill-partner)
