---
title: List of sample queries
description: Use the sample queries to programmatically access partner insights analytics data.
ms.topic: reference
ms.service: partner-dashboard
ms.subservice: partnercenter-insights
author: kshitishsahoo
ms.author: ksahoo
ms.date: 07/14/2021
---

# Sample queries for Partner Center insights report

This article provides sample queries for the Partner Insights reports. You can use these queries by calling the Create Report Query API endpoint. If necessary, the [Create Report Query API](insights-programmatic-access-paradigm.md#create-report-query-api) call can be modified to add more columns, adjust the computation period, and add filter conditions.

For details about the column names, attributes, and descriptions, refer to the [Data Definitions](insights-data-definitions.md).

## Customer details

These sample queries apply to the customers details report:

### By geography

List of customers from a specific geography in last month.

```sql
SELECT CustomerName, CustomerTpid, Product
FROM CustomersAndTenants
WHERE CustomerMarket='United States' TIMESPAN LAST_MONTH
```

### By SKU and billed revenue

List of customers using specific SKU and Billed Revenue is more than 20,000 in the last 6 months

```sql
SELECT CustomerName, CustomerTpid, SKU, Month, BilledRevenueUSD
FROM CustomersAndTenants
WHERE SKU='MICROSOFT 365 BUSINESS STANDARD' AND BilledRevenueUSD>20000 TIMESPAN LAST_6_MONTHS
```

### By available seats

Top 10 customers based on Available seats in last month

```sql
SELECT CustomerName, CustomerTpid, Product, AvailableSeats
FROM CustomersAndTenants ORDER BY AvailableSeats DESC LIMIT 10 TIMESPAN LAST_MONTH
```

## Partner Profile

These sample queries apply to the partner profile report:

### By geography

List of partners from a specific geography.

```sql
SELECT MPNId, PartnerName
FROM Profile
WHERE Country='United States'
```

### By Microsoft AI Cloud Partner Program partner

List of partners under same PGA Microsoft AI Cloud Partner Program Partner

```sql
SELECT MPNId, PartnerName, PGAPartnerID
FROM Profile
WHERE PGAMpnID='1001xx'
```

## Reseller Performance

These sample queries apply to the reseller performance report:

### By geography

List of resellers from a specific geography in last month.

```sql
SELECT ResellerMpnId, ResellerName
FROM ResellerPerformance
WHERE ResellerMarket='US' TIMESPAN LAST_MONTH
```

### By reseller

Customer count, subscription count, total available seats, total assigned seats, total revenue for a specific reseller.

```sql
SELECT ResellerMpnId, ResellerName, CustomerCount, SubscriptionCount, TotalAvailableSeats, TotalAssignedSeats, TotalRevenue
FROM ResellerPerformance
WHERE ResellerMpnId='1051xxx'
```

### Top 10 by revenue

Top 10 resellers based on total revenue in last month.

```sql
SELECT ResellerMpnId, ResellerName, TotalRevenue
FROM ResellerPerformance
ORDER BY TotalRevenue
LIMIT 10
TIMESPAN LAST_MONTH
```

## Subscription Details

These sample queries apply to the subscription details report:

### By renewal eligibility

List of subscriptions who are not eligible for auto renewal in last month.

```sql
SELECT SubscriptionId, SubscriptionEndDate, CustomerName, CustomerTpid, Product
FROM SeatsSubscriptionsAndRevenue
WHERE IsAutoRenew='N' TIMESPAN LAST_MONTH
```

### By subscription state

List of subscriptions who are in Disable state in last month.

```sql
SELECT SubscriptionId, SubscriptionEndDate, CustomerName, CustomerTpid, Product
FROM SeatsSubscriptionsAndRevenue
WHERE SubscriptionState='Disabled' TIMESPAN LAST_MONTH
```

### Counts for six months

Subscription count, total sold seats, customer count for a specific partner in last six months.

```sql
SELECT MPNId, SubscriptionCount, TotalSoldSeats, BilledRevenueUSD, CustomerCount
FROM SeatsSubscriptionsAndRevenue
WHERE MPNId=6096xxx TIMESPAN LAST_6_MONTHS
```

## Azure Usage

These sample queries apply to the Azure usage report:

### By meter category

List of Azure usage subscriptions with usage units and ACR for specific meter category in last six months.

```sql
SELECT SubscriptionId, CustomerName, Month, UsageUnits, UsageQuantity, TotalACR
FROM AzureUsage
WHERE MeterCategory='Azure DNS'
TIMESPAN LAST_6_MONTHS
```

### By total ACR

List of Azure usage subscriptions where total ACR is greater than 20,000 in last six months

```sql
SELECT SubscriptionId, ServiceName, CustomerName, Month, UsageUnits, UsageQuantity, TotalACR
FROM AzureUsage
WHERE TotalACR>20000 TIMESPAN LAST_6_MONTHS
```

## Next steps

- [APIs for accessing partner insights analytics data](insights-programmatic-analytics-available-api.md)
