---
title: Revenue dashboard in commercial marketplace analytics | Azure Marketplace
description: The Revenue dashboard shows the summary of your billed sales of all offer purchases and consumption through the Microsoft commercial marketplace. 
ms.service: partner-dashboard 
ms.subservice: partnercenter-insights
ms.topic: article
author: saurabhsharmaa
ms.author: saurasharma
ms.date: 03/08/2023
---

# Revenue dashboard in commercial marketplace analytics

This article provides information on the _Revenue dashboard_ in Microsoft Partner Center. The Revenue dashboard shows the summary of _billed sales_ of all offer purchases and consumption through the commercial marketplace. It enables you to reconcile billed sales, payouts, and analytic reports in the commercial marketplace.

Use this report to understand your revenue information across customers, billing models, offer plans, and so on. It provides a unified view across entities and helps answer queries, such as:

- How much revenue was invoiced to customers and when can I expect payouts?
- Which customer transacted the offer and where are they located?
- Which offer was purchased?
- When was the offer purchased or consumed?
- What are the billing models and sales channels used?

This article explains how to access the revenue report, understand the purpose of the various widgets on the page, and how to download the exported revenue reports. To learn about your earnings and payouts, see [Getting paid in Partner Center](marketplace-get-paid.md).

## Revenue Dashboard

The [Revenue dashboard](https://partner.microsoft.com/dashboard/commercial-marketplace/analytics/revenue) displays the estimated revenue for all your order purchases and offer consumption. You can view graphical representations of the following items:

- Estimated revenue
- Transactions
- Estimated revenue timeline
- Customer leader board
- Geographical spread
- Details

### Revenue dashboard filters

The page has different dashboard-level filters you can use to filter the Revenue data:

- Offer type
- Offer listing
- Billing model
- Payout status
- Offer name
- Payment instrument family
- Sales channel

To select the filters, in the top-right of the page, select **Filters**.

:::image type="content" source="./media/revenue-dashboard/filters.png" alt-text="Screenshot of the filters on a revenue dashboard widget." lightbox="./media/revenue-dashboard/filters.png":::

Each filter is expandable with multiple options that you can select. Filter options are dynamic and based on the selected date range.

:::image type="content" source="./media/revenue-dashboard/filters-panel.png" alt-text="Screenshot of the Filters side panel." lightbox="./media/revenue-dashboard/filters-panel.png":::

> [!NOTE]
> The dashboard-level filters have no impact on the data shown in the _Estimated revenue timeline_ widget.

### Estimated revenue

In this section, you find the _estimated revenue_ information that shows the overall billed sales of a partner for the selected date range and page filters.

The _Total revenue_ represents the billed sales of payouts or earnings mapped to different payout statuses: _sent_, _upcoming_, and _unprocessed_.

The _Others revenue_ represents billed sales of earnings with status as rejected, reprocessed, not eligible, uncollected from the customers, or not reconcilable with transaction amounts in the earnings report.

The growth rate denotes the percentage change of billed sales between the end and the start of the selected month range.

> [!NOTE]
> There are no earnings entries in the transaction history report for estimated revenue figures with the rejected, reprocessed, not eligible, or not reconcilable status. This screenshot shows an example of billed sales of not only sent, upcoming, and unprocessed earnings, but also uncollected payments from customers.

Select the ellipsis (three dots) to copy the widget image and download the image as a .PDF for sharing purposes.

:::image type="content" source="./media/revenue-dashboard/estimated-revenue-ellipsis.png" alt-text="Screenshot of the ellipsis menu of the estimated revenue widget." lightbox="./media/revenue-dashboard/estimated-revenue-ellipsis.png":::

### Transactions

In this section, you find the _transactions information_ that shows the overall count of the order purchases or offer consumption for a partner for the selected date range and page filters.

Each transaction represents a unique combination of purchase record ID and line-item ID in the revenue report. Transaction information is further categorized based on orders (subscriptions) and consumption (usage) based billing models.

The growth rate denotes the percentage change of transactions between the end and the start of the selected month range.

Select the ellipsis (three dots) to copy the widget image and download the image as a .PDF.

:::image type="content" source="./media/revenue-dashboard/transactions-widget-ellipsis.png" alt-text="Screenshot of the ellipsis menu of the transactions widget." lightbox="./media/revenue-dashboard/transactions-widget-ellipsis.png":::

### Estimated revenue timeline

In this section, you find the _estimated revenue timeline_ information that displays the billed sales of the last payout amount, date, and the revenue figures of upcoming payments and their associated timelines. The upcoming revenue values shown are figures based on the current system date.

Select the ellipsis (three dots) to copy the widget image, download aggregated widget data as a .CSV file, and download the image as a .PDF.

:::image type="content" source="./media/revenue-dashboard/estimated-revenue-timeline-ellipsis.png" alt-text="Screenshot of the Estimated revenue timeline section of the Revenue dashboard." lightbox="./media/revenue-dashboard/estimated-revenue-timeline-ellipsis.png":::

### Customers leader board

In this section, you find the information for top customers who contribute the most to estimated revenue. The “All” row denotes billed sales of all your customers. This table can have upto 500 records. All figures are reported in the partner preferred currency and can be sorted on different columns. You can select each row of the table and see the corresponding revenue split across different statuses, and the revenue trend for the selected month range. The dotted line in the revenue trend represents revenue figures for the open month.

Select the ellipsis (three dots) to copy the widget image and download the image as a .PDF.

:::image type="content" source="./media/revenue-dashboard/customers-leaderboard.png" alt-text="Screenshot of the Customers leader board section of the Revenue dashboard." lightbox="./media/revenue-dashboard/customers-leaderboard.png":::

### Geographical spread

In this section, you find the geographic spread the total estimated revenue, estimated revenue for sent, upcoming, and unprocessed payout statuses. You can sort the table on different statuses. Total estimated revenue includes revenue for other statuses as well.

Select the ellipsis (three dots) to copy the widget image and download the image as a .PDF.

:::image type="content" source="./media/revenue-dashboard/revenue-geographical-spread.png" alt-text="Screenshot of the geographical spread section of the Revenue dashboard." lightbox="./media/revenue-dashboard/revenue-geographical-spread.png":::

### Details

> [!IMPORTANT]
> To download the data in CSV, please use the Download data option available on top of page.

The _Revenue details_ table displays a numbered list of the 1,000 top orders sorted by transaction month.

- Each column in the grid is sortable.
- Use the expand and collapse widget icon at the rightmost side of each record to view billed sales revenue split across different statuses for a given _purchase order ID_ and _line item ID_.
- Apply filters to the revenue details table to display only the data you're interested in. You can filter by order type, offer name, billing model, sales channel, payment instrument type, payout status, and estimated payout instrument.

:::image type="content" source="./media/revenue-dashboard/details-widget.png" alt-text="Screenshot of the Revenue details section of the Revenue dashboard." lightbox="./media/revenue-dashboard/details-widget.png":::

Details widget with expandable and collapsible view.

:::image type="content" source="./media/revenue-dashboard/details-table.png" alt-text="Screenshot of the expandable view of the Revenue details section of the Revenue dashboard." lightbox="./media/revenue-dashboard/details-table.png":::

Note the following:

- The revenue is an estimate since it factors the exchange currency rates. It's displayed in transaction currency, US dollar, or partner preferred currency. Values are displayed as per the selected date range and page filters.
- Estimated revenue is tagged with different statuses as explained in the [data dictionary table](#data-dictionary-table).
- Each row in the Details section has estimated revenue that is an aggregate of all revenue figures for a unique combination of purchase record ID and line-item ID.
- Columns for customer attributes may contain empty values.

## Data dictionary table

| Column name in user interface | Definition |
|----|---------|
| Billed revenue | Represents billed sales of a partner for customer’s offer purchases and consumption through the commercial marketplace. This is in transaction currency and will always be present in download reports. |
| Estimated revenue (USD) | Estimated revenue reported in US dollars. This column will always be present in download reports. |
| Estimated revenue (PC) | Estimated revenue reported in partner preferred currency. This column will always be present in download reports. |
| Status - Sent | The overall revenue for which earnings were sent to the Partner. |
| Status - Unprocessed | The overall revenue for which earnings are yet to be processed. This revenue may be shown across months due to payment schedules and processes. It can occur for multiple reasons:<br><br>- Customer has made payment but the earnings to partner is not yet posted<br>-Manual payment cancellations or failed payment submissions, and so on. |
| Status - Upcoming | The overall revenue for which earnings are upcoming or pending. This revenue may be shown across months due to payment schedules and processes. |
| Status - Rejected | The overall revenue for which payments or safe approval were rejected. |
| Status - Not eligible | The overall revenue for which a partner isn't eligible to receive payouts. [Learn more](/partner-center/transaction-history) about eligibility. |
| Status - Reprocessed | The overall revenue under-reprocessing due to various reasons. For example, invoice cancellation or safe approval cancelation, and so on. |
| Status - Unreconciled | The overall revenue for which successful reconciliation with earnings couldn't happen. This can occur for multiple reasons:<ul><li>Estimated revenue is generated but earnings aren't yet posted</li><li>Some issues with software systems</li></ul> |
| Status - Uncollected | The overall revenue for which an end customer hasn't yet paid or has defaulted. [Learn more](payout-policy-details.md#process-for-customer-nonpayment) about write-offs. For enterprise agreement (EA) customers, there may be entries and for non-EA customers there will be no entries in the transaction history report. |
| Transactions | An order purchase or an offer usage event for which a purchase order ID and line-item ID are generated in the customer invoice. |
| Purchase record ID | Relates to a customer's invoice. Same as `order id` in the transaction history report. |
| Line-item ID | Individual line in a customer's invoice. Same as  `lineItemId` in the transaction history report. |
| Customer name | Name of the customer |
| Customer company name | Name of the customer’s company |
| Customer ID | The unique identifier assigned to a customer. A customer may have zero or more Azure Marketplace subscriptions. Same as `customer id` in the customers report. |
| Billing account ID | Identifier for the billing account of the customer. Same as `customer id` in the transaction history report. |
| Asset ID | An identifier for the software assets. Same as the `order id` in the orders report in Partner Center. |
| Offer type | Type of offer, such as SaaS, VM, and so on. |
| Offer name | Display name of the offer |
| Is Private Offer | Indicates whether a marketplace offer is a private or a public offer.<br><br>-0 value indicates false<br>-1 value indicates true|
| Offer plan | Specific offer plan, also referred to as SKU |
| Trial deployment | Denotes whether the offer was in trial deployment at the time of billing |
| Service Start Date | The start date of the order subscription term |
| Service End Date | The end date of the order subscription term |
| Billed month | The month for which the billing was done and `Purchase record id` and `Line-item id` were generated |
| Transaction amount | Transaction amount in the original transaction currency. Refers to the transaction amount column in the transaction history report |
| Earnings amount CC | Earnings amount in the original transaction currency |
| Transaction currency | The customer currency used for a transaction |
| Transaction amount (USD) | Transaction amount in US dollars. Refers to the transaction currency USD column in the transaction history report |
| Earnings amount USD | Earnings amount in USD |
| Transaction exchange rate (USD) | The exchange rate used to convert transaction amount and transaction amount in USD |
| Transaction amount (PC) | Transaction amount in Partner preferred currency. Refers to the transaction currency USD column in the transaction history report |
| Earnings amount (PC) | Earnings amount in partner preferred payout currency |
| Exchange rate date | The date used to calculate exchange rates for currency conversions |
| Estimated pay out month | The month for receiving your estimated earnings |
| Sales channel | Represents the sales channel for the customer. It's the same as `Azure<br>-Enterprise through Reseller<br>-Pay as You Go<br>->Go to market (GTM) |
| PlanId | The display name of the plan entered when the offer was created in Partner Center. Note: PlanId was originally a numeric number. |
| Billing model | Subscription or consumption-based billing model used for calculation of estimated revenue. It can have one of these two values:<br><br>-UsageBased<br>-SubscriptionBased |
| Customer postal code | The postal code name provided by the bill-to customer |
| Customer city | The city name provided by the bill-to customer |
| Customer state | The state name provided by the bill-to customer |
| Customer country | The country or region name provided by the customer. The country/region could be different than the country/region in a customer's Azure subscription. |
| Customer company | The company name provided by the customer |
| Customer email | The e-mail address provided by the end customer. This address could be different than the e-mail address in a customer's Azure subscription. |
| Payout currency | The partner preferred currency to receive payout. It's same as the _lastpaymentcurrency_ column in the transaction history report. |
| Payment sent date | The date on which payment was sent to the partner |
| Quantity | Indicates billed quantity for transactions. This can represent the seats and site purchase count for subscription-based offers, and usage units for consumption-based offers. |
| Units | The unit quantity. Represents count of purchased seat/site SaaS orders and core hours for VM-based offers. Units will be displayed as NA for offers with custom meters. |
| Customer Adjustment (USD)  | The price offered by the Channel partner to the billed customer in U.S Dollars. This value will be empty for ISV partners, as only Channel partners can see the final adjusted price for the customer |
| MultiParty | Flag indicating whether a private offer transaction involved multi-parties. <br><br>-1 indicates both an ISV and a channel partner were involved.<br><br>-0 indicates only an ISV partner was involved.  |
| Partner Info | Represents SellerID and name of the partners involved in a Multiparty private offer transaction. |
| Sales Notes | Sales note added by an ISV or a Channel partner during private offer creation. An ISV cannot view Channel Partner’s Sales notes and vice versa. |


## Next steps

- For common questions about the revenue dashboard or commercial marketplace analytics, and for a comprehensive dictionary of data terms, see [Commercial marketplace analytics Frequently Asked Questions](analytics-faq.yml).
- For information on payout statements, see [Payout statements](/partner-center/transaction-history).
- For information on Payout schedules, see [Payout schedules and processes](payout-policy-details.md).
- For Virtual Machine (VM) offers usage and metered billing metrics, see [Usage dashboard in commercial marketplace analytics](usage-dashboard.md).
- For information about your orders in a graphical and downloadable format, see [Orders dashboard in commercial marketplace analytics](orders-dashboard.md).
- For a list of your download requests over the last 30 days, see [Downloads dashboard in commercial marketplace analytics](downloads-dashboard.md).
- For an overview of analytics reports available in the commercial marketplace, see [Access analytic reports for the commercial marketplace in Partner Center](analytics.md).
