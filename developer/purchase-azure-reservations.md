---
title: Purchase Azure reservations
description: You can purchase Azure reservations for a customer using the Partner Center API through your existing Microsoft Azure subscription (MS-AZR-0145P) or Azure plan.
ms.date: 06/28/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: iragulati1
ms.author: iragulati
---

# Purchase Azure reservations

**Applies to**: Partner Center | Partner Center for Microsoft Cloud for US Government

To purchase an Azure reservation for a customer using the Partner Center API, you must have an existing Microsoft Azure (**MS-AZR-0145P**) subscription or Azure plan for them.

> [!NOTE]
> Azure reservations are not available in the following markets:
>
> | Unavailable markets            | Unavailable markets (continued...) | Unavailable markets (continued...)      |
> |--------------------------------|-----------------------------------|------------------------------------------|
> | Åland Islands                  | Greenland                         | Papua New Guinea                         |
> | American Samoa                 | Grenada                           | Pitcairn Islands                         |
> | Andorra                        | Guadeloupe                        | Reunion                                  |
> | Anguilla                       | Guam                              | Russian Federation                       |
> | Antarctica                     | Guernsey                          | Saba                                     |
> | Antigua and Barbuda            | Guinea                            | Saint Barthélemy                         |
> | Aruba                          | Guinea-Bissau                     | Saint Lucia                              |
> | Benin                          | Guyana                            | Saint Martin                             |
> | Bhutan                         | Haiti                             | Saint Pierre and Miquelon                |
> | Bonaire                        | Heard Island and McDonald Islands | Saint Vincent and the Grenadines         |
> | Bouvet Island                  | Isle of Man                       | Samoa                                    |
> | Brazil                         | Jan Mayen                         | San Marino                               |
> | British Indian Ocean Territory | Jersey                            | São Tomé and Príncipe                    |
> | British Virgin Islands         | Kiribati                          | Seychelles                               |
> | Burkina Faso                   | Kosovo                            | Sierra Leone                             |
> | Burundi                        | Laos                              | Sint Eustatius                           |
> | Cambodia                       | Lesotho                           | Sint Maarten                             |
> | Central African Republic       | Liberia                           | Solomon Islands                          |
> | Chad                           | Madagascar                        | Somalia                                  |
> | China                          | Malawi                            | South Georgia and South Sandwich Islands |
> | Christmas Island               | Maldives                          | South Sudan                              |
> | Cocos (Keeling) Islands        | Mali                              | St Helena, Ascension, Tristan da Cunha   |
> | Comoros                        | Marshall Islands                  | Suriname                                 |
> | Congo                          | Martinique                        | Svalbard                                 |
> | Congo (DRC)                    | Mauritania                        | Swaziland                                |
> | Cook Islands                   | Mayotte                           | Timor-Leste                              |
> | Djibouti                       | Micronesia                        | Togo                                     |
> | Dominica                       | Montserrat                        | Tokelau                                  |
> | Equatorial Guinea              | Mozambique                        | Tonga                                    |
> | Eritrea                        | Myanmar                           | Turks and Caicos Islands                 |
> | Falkland Islands               | Nauru                             | Tuvalu                                   |
> | French Guiana                  | New Caledonia                     | U.S. Outlying Islands                    |
> | French Polynesia               | Niger                             | Vanuatu                                  |
> | French Southern Territories    | Niue                              | Vatican City                             |
> | Gabon                          | Norfolk Island                    | Wallis and Futuna                        |
> | Gambia                         | Northern Mariana Islands          | Yemen                                    |
> | Gibraltar                      | Palau                             | &nbsp;                                   |
>

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with both standalone App and App+User credentials.

- A customer ID (`customer-tenant-id`). If you don't know the customer's ID, you can look it up in [Partner Center](https://partner.microsoft.com/dashboard) by selecting the **Customers** workspace, then the customer from the customer list, then **Account**. On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section. The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).

- A subscription ID for an active CSP Azure subscription or an Azure plan.

## How to purchase Microsoft Azure reservations

Once you have identified the active CSP Azure subscription that you want to add an Azure reservation to, use the following steps to purchase it:

1. [Enablement](#enablement) - Register an active CSP Azure subscription to enable it for purchasing Azure reservations.

2. [Discovery](#discovery) - Find and select the Azure reservation products and Stock Keeping Units (SKUs) you want to purchase and check their availability.

3. [Order submission](#order-submission) - Create a shopping cart with the items in your order and submit it.

4. [Get order details](#get-order-details) - Review the details of an order, all the orders for a customer, or view orders by billing cycle type.

After you have purchased Azure reservations, the following scenarios show you how to manage their lifecycle by getting information about your Azure reservation entitlements, and how to retrieve balance statements, invoices, and invoice summaries.

- [Lifecycle management](#lifecycle-management)
- [Invoice and reconciliation](#invoice-and-reconciliation)

## Enablement

Enablement means associating an existing Microsoft Azure (**MS-AZR-0145P**) subscription to an Azure Reserved VM Instance by registering the subscription so that it is enabled for Azure reservations. Registration is a prerequisite to purchase Azure Reserved VM Instances.

A subscription is required to support the following tasks:

1. To check if the customer is eligible to deploy resources and hence purchase Azure Reserved VM Instances in a region or not.

2. To provide capacity priority for deployments on a subscription. This is applicable only to single scope Azure Reserved VM Instances with the **capacity priority** option selected.

Once you have identified the active subscription that you want to add the Azure reservation to, you must register the subscription so that it is enabled for Azure reservations. To register an existing [Subscription](subscription-resources.md) resource so that it is enabled for ordering Azure reservations, see [Register a subscription](register-a-subscription.md).

After registering your subscription, you should confirm that the registration process is completed by checking the registration status. To do this, see [Get subscription registration status](get-subscription-registration-status.md).

> [!NOTE]
> When purchasing Microsoft Azure reservation for a customer with an Azure plan, you must register the Azure plan first. Similar to a Microsoft Azure (**MS-AZR-0145P**) subscription, an Azure plan is represented by a Partner Center [Subscription](subscription-resources.md) resource. Hence, you can use the same [Register a subscription](register-a-subscription.md) method to register an Azure plan.

## Discovery

Once the subscription is enabled for purchasing Azure reservations, you're ready to select products and SKUs and check their availability using the following Partner Center API models:

- [Product](product-resources.md#product) - A grouping construct for purchasable goods or services. A product by itself isn't a purchasable item.​​

- [SKU](product-resources.md#sku) - A purchasable SKU under a product. These represent the different shapes of the product.​​

- [Availability](product-resources.md#availability) - A configuration in which a SKU is available for purchase (such as country/region, currency, and industry segment).

Before purchasing an Azure reservation, complete the following steps:

1. Identify and retrieve the Product and SKU that you want to purchase. You can do this by listing the products and SKUs first, or If you already know the IDs of the product and SKU, selecting them.

   - [Get a list of products (by country/region)](get-a-list-of-products.md)
   - [Get a product using the product ID](get-a-product-by-id.md)
   - [Get a list of SKUs for a product (by country/region)](get-a-list-of-skus-for-a-product.md)
   - [Get a SKU using the SKU ID](get-a-sku-by-id.md)

2. Check the inventory for a SKU​. This step is only needed for SKUs that are tagged with an **InventoryCheck** prerequisite​.

   - [Check Inventory](check-inventory.md)

3. Retrieve the [availability](product-resources.md#availability) for the [SKU](product-resources.md#sku). You will need the **CatalogItemId** of the availability when placing the order​. To get this value, use one of the following APIs:

   - [Get a list of availabilities for a SKU (by country/region)](get-a-list-of-availabilities-for-a-sku.md)
   - [Get an availability using the availability ID](get-an-availability-by-id.md)

> [!IMPORTANT]
> Each Microsoft Azure reservation product has different availabilities for Microsoft Azure (**MS-AZR-0145P**) subscription and Azure plan. To [Get a list of products (by country/region)](get-a-list-of-products.md), or [Get a list of SKUs for a product (by country/region)](get-a-list-of-skus-for-a-product.md), or [Get a list of availabilities for a SKU (by country/region)](get-a-list-of-availabilities-for-a-sku.md) which are applicable to Azure plan only, specify the "reservationScope=AzurePlan" parameter.

## Order submission

To submit your Azure reservation order, do the following tasks:

1. Create a cart to hold the collection of catalog items that you intend to buy. When you create a [Cart](cart-resources.md), the [cart line items](cart-resources.md#cartlineitem) are automatically grouped based on what can be purchased together in the same [Order](order-resources.md).

   - [Create a shopping cart](create-a-cart.md)​
   - [Update a shopping cart](update-a-cart.md)

2. Check out the cart. Checking out a cart results in the creation of an [Order](order-resources.md).

   - [Checkout the cart](checkout-a-cart.md)

## Get order details

Once you have created your Azure reservation order, you can retrieve the details of an individual order using the order ID, or get a list of orders for a customer. There is a delay of up to 15 minutes between the time an order is submitted and when it will appear in a list of a customer's orders.​

- To get the details of an individual order using the order ID. See, [Get an order by ID](get-an-order-by-id.md).

- To get a list of orders for a customer using the customer ID. See, [Get all of a customer's orders](get-all-of-a-customer-s-orders.md).

- To get a list of orders for a customer by [billing cycle type](product-resources.md#billingcycletype) allowing you to list Azure reservation orders (one-time charges) and annual or monthly billed orders separately. See, [Get a list of orders by customer and billing cycle type](get-a-list-of-orders-by-customer-and-billing-cycle-type.md).

## Lifecycle management

As part of managing the lifecycle of your Azure reservations in Partner Center, you can retrieve information about your Azure reservation [Entitlements](entitlement-resources.md), and get reservation details using the reservation order ID. For examples of how to do this, see [Get entitlements](get-a-collection-of-entitlements.md).   ​

## Invoice and reconciliation

The following scenarios show you how to programmatically view your customer's [invoices](invoice-resources.md), and get your account balances and summaries that include one-time charges for Azure reservations.

### Balance and payment​

To get current account balance in your default currency type that is a balance of ​both recurring and one-time (Azure reservation) charges, see [Get your current account balance](get-the-reseller-s-current-account-balance.md)

### Multi-currency balance and payment

To get your current account balance and a collection of invoice summaries containing an invoice summary with both recurring and one-time charges for each of your customer's currency types, see [Get invoice summaries](get-invoice-summaries.md).

### Invoices​

To get a collection of invoices that show both recurring and one time charges, see [Get a collection of invoices](get-a-collection-of-invoices.md). ​

### Single Invoice​

To retrieve a specific invoice using the invoice ID, see [Get an invoice by ID](get-invoice-by-id.md).  ​

### Reconciliation

To get a collection of invoice line item details (Reconciliation line items) for a specific invoice ID, see [Get invoice line items](get-invoiceline-items.md).  ​

### Download an invoice as a PDF

To retrieve an invoice statement in PDF form using an invoice ID, see [Get an invoice statement](get-invoice-statement.md).
