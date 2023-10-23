---
title: Manage your customer list
ms.topic: how-to
ms.date: 5/12/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Customer records are among the most important information assets. Learn how to view, search, update, and export information on your Partner Center customer list.
author: jischulz
ms.author: jischulz
---

# Manage your customer list - search, update, or export customer information in Partner Center

**Applies to**: Partner Center | Partner Center for Microsoft Cloud for US Government

**Appropriate roles**: Admin agent

Customer records are among your most important information assets in Partner Center.

This article describes how to:

- Search your database of customer accounts.
- Export a customer database as a comma-separated-values (.csv) file.
- Export a customer's subscription information as a .csv file.

You can also export data about transactions and management actions for customers as *activity logs*. For more information, see [View customer activity logs](activity-logs.md).

In May 2023, we updated the Customer List page to show details in a table view. From the table, you can [create new orders](#create-a-new-order), [manage and assign tags](./manage-customers-with-tags.md), or go to the **Service management** page.

:::image type="content" source="./media/customers/customer-list.png" alt-text="Screenshot of Customer list from Partner Center.":::

## Search for a customer

To search for a customer:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.
   
   A list of your customers appears on the **Customer List**.
   
2. You can narrow the search by using:
   - **Search By** to limit the search to company names, domain names, or Microsoft IDs
   - **Search Customer list** to enter text to search for
   - Dual partners (that is, tier 1 + indirect reseller) see duplicate customers in the list (that is, customers from both their tier 1 status and their status as an indirect reseller).

## Create a new order

You can create a new order for a specific customer from the **Customer list** page. To proceed, select a customer and select **New order** in the command bar.

You can also [manage your customers with tags](./manage-customers-with-tags.md), or see more details through the **Service management** page.

## Filter your customer list

You can filter your customer list to view a subset of your customers.

### Filter by indirect reseller

If you're an indirect provider, you can filter your customer list by an indirect reseller.

To filter by indirect reseller:

1. Select the filter icon.
2. Select the filter icon: **indirect reseller**.
3. Select a reseller.

## Update a customer's company name

You can update a customer's "Bill-to" company name and their company name on the  customer list.

To update a customer's company name:

1. [Search for the customer](#search-for-a-customer).

1. Under the customer's **Bill-to** information, update the company name.

   - When you save the new company name, the change only appears under Bill-to and on the customer list. The company name isn't changed anywhere else.

## Export your customer list

To export your customer list:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Select **Export customers**  in the command bar to download the customer list to the default download folder on your computer as a .csv file.
   
   Data columns in the *Customers.csv* file include:

   - **Microsoft ID**
   - **Company name**
   - **Primary domain name**
   - **Relationship** (the partner's business relationship to the customer, for example *Cloud Reseller*)

## Export customer subscription information

To export customer subscription information, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Select the customer's **Company name**.

   The **Subscriptions** page opens, showing a list of the customer's product subscriptions.

3. Select **Export subscriptions** to silently send the customer subscription data to the default download folder on your computer as a .csv file.
   Data columns include:
   - **Subscription ID**
   - **Subscription**—the product name for the subscription
   - **Quantity**—number of purchased licenses
   - **Status**
   - **Reseller**—the ID of the reseller that owns and manages the subscription

## Next steps

- [Customer subscriptions](customer-subscriptions.md).
