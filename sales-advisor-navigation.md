---
title: Navigate Sales Advisor opportunities
description: Learn how to navigate the Sales Advisor landing page to find high-value opportunities.
ms.date: 07/17/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-insights
ms.topic: article
author: JulCsc
ms.author: juliacawthra
ms.reviewer: sharonchoi
---

# Navigating Sales Advisor

**Appropriate roles**: Executive report viewer | Report viewer

The Sales Advisor landing page contains summary about overview of the highest value opportunities within partner's Microsoft 365 install-base. It contains summary of the number of customers with opportunities, number of opportunities, and a graph of the number of opportunities by opportunity type.

## Filtering by Enrollment ID

User can select to filter the opportunities by Enrollment ID (also known as MPN ID or Partner ID) if the partner organization has multiple Enrollment IDs. Filter button is located in the top right. Select **>** to expand the list of Enrollment IDs. From there, select and unselect the Enrollment IDs using the checkbox. Select this filter to only show opportunities where the customer is associated with the selected Enrollment ID.

:::image type="content" source="./media/sales-advisor-navigation/filter-button.png" alt-text="Screenshot showing the Filter button.":::

## Prioritized opportunities

Table view available in the landing page that contains the number of total customers, number of high propensity opportunities, and number of medium propensity opportunities by opportunity type. 

:::image type="content" source="./media/sales-advisor-navigation/prioritized-opportunities.png" alt-text="Screenshot showing the filtered list of opportunities.":::

Select **View customers** to view the list of recommendations and customers filtered by each opportunity type. For example, Select **View customers** under **Customer acquisition** to see the Customer acquisition opportunities tab and recommendations.

## All opportunities

From the landing page, select **View all opportunities** to navigate to the table view of all opportunities. Each opportunity shows up as a separate row.

:::image type="content" source="./media/sales-advisor-navigation/opportunities-list.png" alt-text="Screenshot showing the full list of opportunities.":::

### Table columns

The table contains the following columns:

- **Customer**: Name of customer  
- **Recommendation**: Recommended action for this opportunity  
- **Opportunity type**: Type of opportunity that belongs to one of the opportunity categories
  - **Trial**: Shows trial subscriptions in the customer tenant.
  - **Engagement**: Shows scenarios where the customer needs to be engaged to drive product adoption because of low or declining usage in critical workloads, or where the customer tenant needs to take action to secure their organization
  - **Retention**: Shows customer tenants at risk of churn
  - **Upsell**: Shows opportunities to move customers to more premium products or purchase new products
  - **SMB Expansion**: Shows opportunities to add seats to a customer tenant's existing subscriptions
- **Propensity status**: The probability that the prediction is correct, with possible values of "high" or "low"
- **Product**: Product associated with the opportunity (not visible for Customer retention opportunities)
- **Seats**: Number of paid licenses in the customer tenant  
- **Date added**: Date the opportunity was first created for the customer. Recommendations are refreshed regularly to capture the most recent customer signals; therefore, an opportunity continues to show up if there's no change in the customer signals, regardless of when it was first created.

By default, the table is sorted alphabetically based on customer name.

## Provide feedback

You can provide feedback directly within the tool including on the quality of specific recommendation or feature. Your feedback allows us to improve our ability offer more relevant, accurate opportunities.

User can submit feedback selecting any of the 'Thumbs Up' and 'Thumbs Down' icon present in Sales Advisor. 'Thumbs Up' and 'Thumbs Down' can be found under most graphs, charts, and for each recommendation. Select 'Thumbs Up' to indicate a positive experience and 'Thumbs Down' to indicate a negative experience along with opportunity to improve.

:::image type="content" source="./media/sales-advisor-navigation/feedback-1.png" alt-text="Screenshot showing providing feedback on a specific recommendation.":::

:::image type="content" source="./media/sales-advisor-navigation/feedback-2.png" alt-text="Screenshot showing providing feedback on opportunity overview chart.":::

Once the 'Thumbs Up' or 'Thumbs Down' icon is selected, a form to collect your feedback with comments is displayed.

:::image type="content" source="./media/sales-advisor-navigation/feedback-3.png" alt-text="Screenshot showing providing feedback with comment form.":::

## Table Filtering

The filter is located on the top right of the opportunity table. You can select specific recommendations to populate based on the filtering criteria. You can filter by recommendation, propensity status, product, or opportunity type.

Select **+** to expand the options to choose a specific recommendation, propensity status, product, or opportunity type to filter against. 

:::image type="content" source="./media/sales-advisor-navigation/filtered-recommendations.png" alt-text="Screenshot showing the filtering options for recommendations.":::

## Search bar

Using the search bar located on the top right of the opportunity table, user can search for recommendations that contains the keyword input (for example, searching for a recommendation based on a specific customer name).

## View opportunity by category (tabs)

Select the tabs located above the opportunity table to view opportunities by each opportunity category. In addition to the opportunity table, this view displays graph of the total customers, total seats, and pie chart of opportunity category by propensity.

:::image type="content" source="./media/sales-advisor-navigation/insights.png" alt-text="Screenshot the opportunities list by opportunity category.":::

## Recommendation flyout view

Select the **Recommendation** (blue text) in the table to learn more about the opportunity and display a flyout that contains a **Recommendation**, **Subscription**, and **Usage** tab.

:::image type="content" source="./media/sales-advisor-navigation/recommendation-example.png" alt-text="Screenshot an example of a Sales Advisor recommendation.":::

### Recommendation

- Customer insights: characteristics about the selected customer based on historical data and correlation, explains why we're suggesting the specific recommendation.
- Suggested actions: specific suggestions to enforce the recommendation (such as running a workshop).
- Related Resources: marketing materials such as playbook, demo, cheat sheets, email templates to help prepare partners for the conversation with the customer regarding the opportunity.

### Subscription

Contains subscription information about the products purchased by the customer from the partner's organization or from Microsoft directly.

- Product name
- Purchase quantity
- Subscription status: Active/Inactive

## Usage

Shows how users are using Microsoft 365 services for all products owned by the customer.

- Usage per user graph (can be filtered by workload)
- Table View
  - Workload: Exchange Online, OneDrive for Business, Azure Active Directory, etc.
  - Assigned users: number of seats containing the workload assigned to user
  - Active users: number of users actively using the workload
  - Trend: the trend in monthly active usage over the previous three months. Average, Positive, or Negative

:::image type="content" source="./media/sales-advisor-navigation/recommendation-details.png" alt-text="Screenshot showing the recommendation details.":::

## Export

:::image type="content" source="./media/sales-advisor-navigation/opportunities-export.png" alt-text="Screenshot showing the export screen for opportunities.":::

The export button located on the top left of opportunity table exports the data into a CSV file. Export data out of Sales Advisor to consume data in a different format, integrate into your internal tools, and create reports. The downloaded CSV file contains the following data:

- Customer ID
- TPID
- Customer Name
- Opportunity Type
- Recommendation
- Growth Propensity
- Recommended Product
- Date Added
- Link (a unique URL for each opportunity)
- Feedback

> [!NOTE]
> Exported Excel file will be automatically downloaded to the device that is accessing Sales Advisor.

## Next steps

- [Sales Advisor troubleshooting](./sales-advisor-troubleshoot.md)
