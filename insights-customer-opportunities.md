---
title: Partner Center Insights - CloudAscent propensity reports
description: Learn about the CloudAscent propensity reports in Partner Center. Includes information about a customer's propensity to purchase Microsoft products.
ms.topic: conceptual
ms.service: partner-dashboard
ms.subservice: partnercenter-insights
author: kshitishsahoo
ms.author: ksahoo
ms.date: 8/11/2023
---

# Customer opportunities dashboard - Cloud product performance

**Appropriate roles**: Executive report viewer | Report viewer with Partner Global account access

*Propensity data* shows customers' likelihood to purchase Microsoft products.

Partner Center provides downloadable propensity data from [CloudAscent](https://partner.microsoft.com/solutions/cloudascent).

This article describes propensity data, what it means, and how to use it.

**Summary definitions:**

- **SMC customers**: Number of customers in the propensity downloads. Customers are identified by transacting partner.
- **Expiring agreements**: Number of agreements expiring in the current fiscal year.
- **Open expiring revenue**: Revenue associated with open expiring agreements.

:::image type="content" source="media/insights-customer-opportunities/summary-screen.png" alt-text="Screenshot of Customers Opportunities Summary dashboard.":::

## SMB segment and subsegments

The small to medium business (SMB) segment is divided into three subsegments:

- **Upper Medium business** Org size: 300+ employees or Customers with Azure Consumption revenue (ACR) >$1,000 per month
- **Medium business** subsegment is customers with 25 to 300 employees.

- **Very small business** subsegment is customers with 1 to 25 employees.

:::image type="content" source="media/insights-customer-opportunities/customer-by-smb-type.png" lightbox="media/insights-customer-opportunities/customer-by-smb-type.png" alt-text="Screenshot of customers by SMB type.":::

The **Upper Medium** and **Medium business** subsegments are high-value customers for Microsoft and Microsoft partners. Because of their high value, these subsegments are the primary focus for driving growth in the SMB segment. The key area of opportunity is *customer adds*.

The following diagram shows the three SMB subsegments. CloudAscent prioritizes the profiling, scoring, and modeling of all *Upper Medium*, *Medium*, and *Very Small* business accounts.

:::image type="content" source="media/insights-customer-opportunities/smb-customer-landscape.png" lightbox="media/insights-customer-opportunities/smb-customer-landscape.png" alt-text="Screenshot of SMB subsegments.":::

## CloudAscent machine learning

In the small-to-medium-business segment, we use machine learning to drive sales and marketing customer predictions within the *Upper Medium*, *Medium*, and *Very small business* subsegments.

Customer data is collected and turned into recommendations using the following process:

1. **Collect data**: Web crawlers scan and collect billions of customer signals by pinging company domains and monitoring blog posts, press releases, social streams, and technical forums. In addition to the collected signals, firmographics information is collected from both internal and external sources such as Dunn & Bradstreet, Microsoft internal subscriptions, and transactional data.

2. **Generate predictions**: Data collected in the previous step is fed into a machine learning model that generates a structured data set of sales and marketing predictions for each customer by cloud product and cluster. Each customer is scored using a lookalike model to Microsoft's top SMB that determines the customer's fit, and machine learning algorithms that integrate the customer's online behavior defined as intent. The scoring is merged into clusters that show a customer's propensity to purchase Microsoft cloud products.

3. **Optimize models**: The machine learning system optimizes the models by consuming transaction data monthly and subscription data quarterly. Using the win/loss data, machine learning adjusts the algorithms and validates that the models are working as expected by comparing cluster recommendations to opportunities acted upon in Microsoft Sales Experience (MSX).

:::image type="content" source="media/insights-customer-opportunities/smb-machine-learning.png" lightbox="media/insights-customer-opportunities/smb-machine-learning.png" alt-text="Screenshot of SMB machine learning.":::

## CloudAscent scoring

How are targeting recommendations created?

Using signals collected by web crawlers and data gathered from various sources, we consolidate firmographics data and customers' social media signals. Scoring uses the following signals and data in comparison models for fit and scoring models for intent.

- **Customer account fit**

  - Internal and external data points that define firmographics.

  - Fit scoring compares customers to our best SMB using a lookalike model to see if they're a potential fit for Microsoft cloud products.

  - Fit scoring is updated quarterly.

- **Customer account intent**

   - Buying Signals - Events or changes in an organization that are likely to generate a sales opportunity.
  - Intent scoring is overlaid on top of fit to define the clusters.

  - Intent scoring is updated monthly.

   :::image type="content" source="media/insights-customer-opportunities/predictive-models.png" lightbox="media/insights-customer-opportunities/predictive-models.png" alt-text="Screenshot of CloudAscent SMB predictive models.":::
   
   :::image type="content" source="media/insights-customer-opportunities/buying-signals.png" lightbox="media/insights-customer-opportunities/buying-signals.png" alt-text="Screenshot of CloudAscent Buying Signals: signal collection screen.":::

- **Clustering**

   Signals for fit and intent are consolidated into a clustering score.

   CloudAscent has four clusters:

  - **Act now**: Sales-ready customers
  - **Evaluate**: Marketing-ready customers
  - **Nurture**: Drive awareness campaigns
  - **Educate**: Educate and monitor for intent

   Clustering enables users to target specific customers for sales and marketing initiatives based on segment factors, for example, product, geography, industry, and vertical.

### Propensity and estimated whitespace revenue

   The **Propensity model** tab in the CloudAscent Workbooks displays propensity and estimated whitespace revenue.

  To define the clustering of Fit and Intent, use the following steps:

   1. Using machine learning models, we first calculate the customer fit score and intent score on a scale of 0 to 100.
     Scores vary depending on machine learning models.

        Some example scores are:

         |**Classification**|**Score**|
         |---------|:---------|
         |High|75 - 100|
         |Medium|55 - 74|
         |Low|30 - 54|
         |Very low|0 - 29|

   1. Using the preceding rule, we classify companies as high, medium, low, and very low propensity to buy by both customer fit and intent signals.

   1. We plot customer fit and intent signals on a two-dimensional matrix, with each intersection representing propensity.
     For example, high fit + high intent = A1, the highest propensity.

   1. Finally, these segments group to form clusters. For example, A1, A2, A3, A4 from the *Act Now* cluster.

      :::image type="content" source="media/insights-customer-opportunities/clusters.png" lightbox="media/insights-customer-opportunities/clusters.png" alt-text="Screenshot of CloudAscent models.":::

   We recommend targeting *Act Now* and *Evaluate* customers.

## CloudAscent products and models

The following graphic provides a view of each propensity model within CloudAscent:

:::image type="content" source="media/insights-customer-opportunities/propensity-models.png" lightbox="media/insights-customer-opportunities/propensity-models.png" alt-text="Screenshot of CloudAscent propensity model.":::

- *Whitespace* models are composed of predictions for existing Microsoft customers where they don't have a product and/or are net-new prospect customers.

- *Up-sell* models use transaction data to predict the potential for up-sell in Microsoft 365 SKUs. These customers already have Microsoft 365, and the up-sell model shows that they're likely to purchase more of their existing SKU.

- *Azure Next Logical Workload* model uses existing Azure transaction data to predict potential for next likely workload for this customer to purchase.  These customers already have Azure and are likely to purchase an additional workload when showing high propensity.

- *End of service* (EOS) shows EOS customers for Windows 7, Office 2010, SQL Server, and Windows Server. EOS data is pulled from Microsoft Sales and overlaid with the CloudAscent propensity modeling where available. EOS data lives in the Modern Work and Azure Sales plays.

## Next steps

[Download reports in cloud product performance](./insights-download-reports.md)