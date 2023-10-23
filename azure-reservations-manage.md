---
title: Manage Azure reservations for customers
description: Learn how to manage Azure reservations for a customer, including how to cancel a reservation, exchange a reservation, or request a refund.
ms.topic: how-to
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
author: migolova
ms.author: migolova
ms.date: 07/31/2023
---

# Manage, cancel, exchange, or refund Azure reservations for customers

**Appropriate roles**: Admin agent | Global admin | Helpdesk agent | Sales agent | User management admin

This article explains how to manage Azure reservations for a customer, which includes canceling or exchanging a reservation, or requesting a refund.

> [!NOTE]
> This article applies only to partners in the Cloud Solution Provider (CSP) program.
>
> Customers using other types of subscriptions—such as pay-as-you-go (PAYG), individual, Microsoft Customer Agreement, or Enterprise Agreement subscriptions)—should see [Azure reservations](/azure/cost-management-billing/reservations) instead.

To manage your customers' Azure reservations post-purchase, select the customer and reservation that you want to manage in Partner Center, and then make changes to the reservation in the Azure portal. For information about Admin agent privilege and guest access, see [View Azure reservations as a Cloud Solution Provider (CSP)](/azure/cost-management-billing/reservations/how-to-view-csp-reservations).

To manage your customers' Azure reservations post-purchase, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.
1. Select the customer you want to manage.
1. On the customer's detail page, select **Azure reservations** and then select the reservation that you want to manage.
1. Under **Actions**, select **Manage** to go to the customer's reservation record in the Azure portal.
1. On the reservation detail page, do the following steps to complete tasks.

    | **Select**   | **To**    |
    |:-----------------------------|:-----------------|
    | **Overview**   | View details of a customer's reservation, including expiration date, scope, and utilization data. <br> Select **Refund** to create a support request for a prorated refund. <br> Select **Exchange** to create a support request to exchange the unused portion of your reservation term.
    | **Access Control (IAM)**   | Manage access to the customer's reservation information.|
    | **Configuration**   | Change the reservation's scope and/or the Azure subscription the reservation is associated with.    |
    | **Properties**   | View the reservation's properties and copy to the clipboard the reservation ID and reservation order ID. <br>**NOTE**: Support might ask you for the reservation ID and reservation order ID when you request support on behalf of a customer.    |
    | **New support request**    | Request help from Microsoft Support.   |

## Cancel or exchange a reservation

If a customer's business needs change, they might want to cancel a reservation, and get a refund or exchange a reservation's prorated refund amount to be used toward the price of a new reservation.

For more information, see [Self-service exchanges and refunds for Azure Reservations](/azure/cost-management-billing/reservations/exchange-and-refund-azure-reservations).

### How exchanges work

If a customer wants to buy a different reservation than the one they originally bought from you, they can request an exchange. Exchanging a reservation can be an attractive alternative to canceling a reservation because it allows the customer to use the prorated refund amount toward the price of the new reservation.

The prorated refund amount is credited to your account so that you can offer the customer an exchange.

> [!NOTE]
> Exchanging reservations is allowed only on reservations of the **same type**, not cross-types. For **cross-type reservations**, customers must **cancel and repurchase** the new reservation.

## Request a refund or exchange on behalf of a customer

To file a support request for a refund or exchange on behalf of a customer, select the customer and reservation in Partner Center and then create the support request in the Azure portal.

> [!NOTE]
> Microsoft Support agents might ask you to provide the reservation ID and reservation order ID. You can find this information on the reservation's **Properties** page in the Azure portal.

To request a refund or exchange on behalf of a customer, use the following steps:

1. In Partner Center, select **Customers** and then select the customer who wants a refund.
1. On the customer's detail page, select **Azure reservations** and then select the reservation for which the customer wants a refund.
1. Under **Actions**, select **Refund** to go to the customer's reservation record in the Azure portal and initiate a support request.
1. On the **New support request** page, do the following steps to request a refund.

   |**Step**                    |**Selections**    |
   |:---------------------------|:-----------------|
   |**1. Basics**                |**Issue type**: Billing.  |
   |**2. Problem**               |**Problem type**: Reservation management. <br> **Category**: Exchanges and refunds. |
   |**3. Contact information**   |Select your preferences and enter the required information.

1. Select **Create** when done.

## Azure reservations resources

|**For information about**:  |**Read this**:   |
|:-----------------------------|:-----------------|
|Azure reservations in CSP overview  | [Sell Microsoft Azure Reserved Instances](azure-reservations.md) |
|Purchasing Azure reservations for your customers in Partner Center   | [Buy Azure reservations](azure-reservations-buying.md) |
|Determining the correct VM size and verifying customer VM usage   | [VM sizing for maximum Azure reservation usage](azure-usage.md)   |
|Purchasing Azure reservations using the Partner Center API | [Purchase Azure Reserved VM Instances](/partner-center/develop/purchase-azure-reservations) in the Partner Center developer documentation   |
|Giving customers permission to buy their own Azure reservations from a subscription you purchased for them | [Give customers permission to buy their own Azure reservations](give-customers-permission.md)   |
