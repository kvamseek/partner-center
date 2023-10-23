---
title: Create an Azure plan
description: Developers can purchase, create, and manage Azure plans programmatically using Partner Center APIs.
ms.date: 12/09/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: iragulati1
ms.author: iragulati
---

# Create an Azure plan

You can purchase, create, and manage an Azure plan using the Partner Center APIs. The process is similar to creating a Microsoft Azure ([MS-AZR-0145P](https://go.microsoft.com/fwlink/p/?linkid=2164140)) subscription. You must [get the catalog item for the Azure plan](#get-the-catalog-item-for-azure-plan), then [create and submit an order](#create-and-submit-an-order).

## Prerequisites

* [Partner Center authentication](partner-center-authentication.md) credentials. This scenario supports authentication with both standalone App and App+User credentials.
* The customer identifier. If you don't have a customer's identifier, follow the steps in [Get a list of customers](get-a-list-of-customers.md). Alternatively, sign in to Partner Center, choose the customer from the list of customers, select **Account**, then save their **Microsoft ID**.
* [Confirmation of the customer's acceptance of the Microsoft Customer Agreement](../confirm-customer-agreement.md).

## Get the catalog item for Azure plan

Before you can create an Azure plan for a customer, you need to retrieve the corresponding catalog item. You can retrieve the catalog item using the existing Partner Center catalog APIs with the following resource models.

* **[Product](product-resources.md#product)**: A grouping construct for purchasable goods or services. A product itself isn't a purchasable item.
* **[SKU](product-resources.md#sku)**: A purchasable Stock Keeping Unit (SKU) under a product. SKUs represent the different shapes of the product.
* **[Availability](product-resources.md#availability)**: A configuration in which a SKU is available for purchase (such as country/region, currency, or industry segment).

To obtain the catalog item for an Azure plan, complete the following steps:

1. Identify and retrieve the *product* identifier for the Azure plan. Follow the steps in [Get a list of products](get-a-list-of-products.md) and specify the **targetView** as **MicrosoftAzure**. (If you already know the *product* identifier for the Azure plan, you can follow the steps in [Get a product using the product ID](get-a-product-by-id.md) instead.)

2. Retrieve the **SKU** from the product for the Azure plan. Follow the steps in [Get a list of SKUs for a product](get-a-list-of-skus-for-a-product.md). If you already know the SKU identifier for the Azure plan, you can follow the steps in [Get a SKU using the SKU ID](get-a-sku-by-id.md) instead.

3. Retrieve the **availability** from the SKU for the Azure plan. Follow the steps in [Get a list of availabilities for a SKU](get-a-list-of-availabilities-for-a-sku.md). If you already know the identifier for the availability you need, you can follow the steps in [Get an availability using the availability ID](get-an-availability-by-id.md) instead. *Be sure to note the value of the **CatalogItemId** property of the availability for the Azure plan. You will need this value to create an order.*

## Create and submit an order

To submit your order for an Azure plan, follow these steps:

1. [Create a cart](create-a-cart.md) to hold the collection of catalog items that you intend to buy. When you create a [cart](cart-resources.md#cart), the [cart line items](cart-resources.md#cartlineitem) are automatically grouped based on what can be purchased together in the same [order](order-resources.md#order). (You can also [update a cart](update-a-cart.md).)

2. [Check out the cart](checkout-a-cart.md), which results in the creation of an [order](order-resources.md#order).

## Get order details

You can [retrieve the details of an individual order using the order ID](get-an-order-by-id.md). You can also [retrieve a list of all orders for a specific customer](get-all-of-a-customer-s-orders.md).

> [!NOTE]
>After an order is submitted, there is a delay of up to 15 minutes before the order appears in that customer's order list.

## Manage Azure plans

After the order is successfully processed, a Partner Center **Subscription** resource will be created for the Azure plan. You can use the following methods for managing Partner Center **Subscription** resources to manage the Azure plan:

* [Get a customer's subscriptions](get-all-of-a-customer-s-subscriptions.md)
* [Get a list of subscriptions by order](get-a-list-of-subscriptions-by-order.md)

When an Azure plan is created in Partner Center, a corresponding Azure usage subscription is also created in Azure. You can also create additional Azure usage subscriptions under the same Azure plan using Azure portal and Azure APIs. You can obtain the identifiers of all the Azure usage subscriptions associated with an Azure plan by following the steps in [Get a list of Azure entitlements for Partner Center subscription](get-a-list-of-azure-entitlements-for-subscription.md)

## Lifecycle management

You can suspend an existing Azure plan by following the steps in [Suspend a subscription](suspend-a-subscription.md).

*You can only suspend an existing Azure plan if it no longer has any active usage assets associated with it, including Azure usage subscriptions and Azure reservations.*

For details on how to disable Azure usage subscriptions, see [Azure API on subscription lifecycle management](/rest/api/resources/subscriptions).

To remove existing Azure reservations, you must [cancel the reservations](../azure-reservations-manage.md#cancel-or-exchange-a-reservation).
After you suspend an Azure plan, you can reactivate it.

For details on how to reactivate an Azure plan, see [Reactivate a suspended subscription](reactivate-a-suspended-a-subscription.md)

## Transition existing CSP offers to Azure plan

You can't create an Azure plan for an existing customer with a Microsoft Azure (MS-AZR-0145P) subscription. However, you can [transition a customer from their existing CSP Azure offers to Azure services under the Azure plan](../azure-plan-transition.md) in the new commerce experience in the CSP program from within Partner Center. To transition an existing customer, use the product upgrade APIs to follow these steps:

* [Check whether the customer is eligible for a transition to Azure plan](get-eligibility-for-product-upgrade.md)
* [Initiate a product upgrade for the customer](create-product-upgrade-entity.md)
* [Check the status of a product upgrade](get-product-upgrade-status.md)

## Azure spending

You can track [Azure spending](azure-spending.md) by querying for usage summary and detailed usage records using the following methods:

* [Get partner usage summary](get-a-partner-usage-summary.md)
* [Get all customer usage records for a partner](get-a-customer-s-usage-records.md)
* [Get customer usage summary](get-a-customer-usage-summary.md)
* [Get all subscription usage records for a customer](get-a-customer-subscription-s-usage-records.md)
* [Get subscription usage summary](get-a-customer-subscription-usage-summary.md)
* [Get usage data for subscription by resource](get-a-customer-subscription-resource-usage-records.md)
* [Get usage data for subscription by meter](get-a-customer-subscription-meter-usage-records.md)
* [Get meter usage record resources](meter-usage-resources.md)
* [Get resource usage record resources](resource-usage-resources.md)

You can also set and manage customer usage budget using the following methods:

* [Get customer usage budget](get-a-customer-s-usage-spending-budget.md)
* [Update customer usage budget](update-a-customer-s-usage-spending-budget.md)

## Invoice and reconciliation

You can manage invoices and reconciliation data using the following methods:

* [Get a collection of invoices](get-a-collection-of-invoices.md)
* [Get invoice estimate links](get-invoice-estimate-links.md)
* [Get invoice by ID](get-invoice-by-id.md)
* [Get invoice statement](get-invoice-statement.md)
* [Get invoice summaries](get-invoice-summaries.md)
* [Get invoice billed consumption line items](get-invoice-billed-consumption-lineitems.md)
* [Get invoice unbilled consumption line items](get-invoice-unbilled-consumption-lineitems.md)
* [Get invoice billed recon line items](get-invoiceline-items.md)
* [Get invoice unbilled recon line items](get-invoice-unbilled-recon-lineitems.md)