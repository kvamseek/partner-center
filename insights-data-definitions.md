---
title: Partner insights reports and data definitions
ms.topic: article
ms.service: partner-dashboard
ms.subservice: partnercenter-insights
description: The document lists various reports and their data definitions, which you can download from the Insights Download report page.
author: kshitishsahoo
ms.author: ksahoo
ms.date: 08/11/2023
---

# Cloud product performance reports – Data definitions

**Appropriate roles**: Report viewer | Executive report viewer

By using the **Download Reports** hub on the **Insights** dashboard, you can export the raw datasets.

The various reports, which you can download along with their data definitions, are listed in the following tables:

## **Partner profile report**

| Column name | Data description |
| :--------- | :--------- |
| :::no-loc text="MPNId"::: | Microsoft AI Cloud Partner Program ID |
| :::no-loc text="PartnerName"::: | Name of the partner |
| :::no-loc text="PGA_MPNID"::: | Identifier of the partner global account |
| :::no-loc text="PGA_PartnerName"::: | Partner global account name |
| :::no-loc text="City"::: | City location of the partner |
| :::no-loc text="Country"::: | Country/region location of the partner |
| :::no-loc text="HierarchyLevel"::: | Indicates whether it's a Global ID or Location ID |

## Customers and revenue

| Column name | Data description |
| :--------- | :--------- |
| :::no-loc text="PGAMpnID"::: |Identifier of the partner global account|
| :::no-loc text="CustomerName"::: |Name of the customer|
| :::no-loc text="CustomerTenantId"::: |Identifier of the customer tenant|
| :::no-loc text="CustomerTpid"::: |Identifier of the customer top parent|
| :::no-loc text="DUNSNumber"::: |Global Data Universal Number System Identifier of customer|
| :::no-loc text="CustomerSegment"::: |Customer segment|
| :::no-loc text="TopSegment"::: | Higher-level segment classification of customer|
| :::no-loc text="CustomerMarket"::: |Geographical market of the customer|
| :::no-loc text="CustomerStatus"::: | Customer Status (Active or Inactive)|
| :::no-loc text="CustomerTenantName"::: | Name of customer tenant|
| :::no-loc text="CustomerTenantCountry"::: |Country/region of customer tenant|
| :::no-loc text="TenantDomainName"::: |Domain name of customer tenant|
| :::no-loc text="Product"::: |The product sold to the customer by the partner: Microsoft 365, Dynamics 365, Enterprise Mobility + Security, Power BI, or Microsoft Azure.|
| :::no-loc text="RawProductName"::: |Detailed product name sold to the customer|
| :::no-loc text="SKU"::: |Product SKU|
| :::no-loc text="Month"::: |Month for which usage and revenue are reported|
| :::no-loc text="MPNId"::: |Identifier of Microsoft AI Cloud Partner Program (formerly MPN)|
| :::no-loc text="PartnerName"::: |Name of the partner|
| :::no-loc text="PartnerLocation"::: |Geographical location of partner|
| :::no-loc text="PartnerAttributionType"::: |Attribution type of the partner|
| :::no-loc text="SalesChannel"::: |Sales Channel|
| :::no-loc text="IndustryName"::: |Type of Industry the customer belongs|
| :::no-loc text="VerticalName"::: |Business Vertical within the Industry of the Customer |
| :::no-loc text="EOU"::: | Enterprise Organizational Unit, Focus areas for Subsidiary levels. For example, SMC Commercial, USA – Northeast, JPN - Kansai|
| :::no-loc text="IsDuplicateRowForPGA"::: |For multiple partner attributions under single PGA, this value is set to 0 for only one MPNId. If the value is set to 1, then it indicates a duplicate row|
| :::no-loc text="AvailableSeats"::: |Available seats|
| :::no-loc text="BilledRevenueUSD"::: |Billed revenue in US dollar|
| :::no-loc text="AzureConsumedRevenueUSD"::: |Azure Consumed Revenue in USD|
| :::no-loc text="CPORRevenue"::: |Revenue from the CPOR Partner attaches type|
| :::no-loc text="CPORPaidSeats"::: | Paid seats with CPOR Partner attach type|
| :::no-loc text="CPORActiveUsers"::: | Active users with CPOR Partner attach type|

## **Reseller performance report**

> [!NOTE]
> Revenue and Azure consumed revenue (ACR) data are available only to users who are Executive report viewers.

| Column name | Data description |
| :--------- | :--------- |
| :::no-loc text="PGAMpnID"::: | Identifier of the partner global account |
| :::no-loc text="ResellerMpnID"::: | Reseller Microsoft AI Cloud Partner Program identifier |
| :::no-loc text="ResellerName"::: | Reseller name |
| :::no-loc text="ResellerMarket"::: | Reseller country/region of market |
| :::no-loc text="IndirectProviderMpnID"::: | Identifier of the indirect provider Microsoft AI Cloud Partner Program |
| :::no-loc text="IndirectProviderName"::: | Indirect provider name |
| :::no-loc text="Month"::: | Month for which usage and revenue is reported |
| :::no-loc text="Product"::: | Product name |
| :::no-loc text="SubscriptionID"::: | Identifier of the subscription |
| :::no-loc text="AvailableSeats"::: | Number of seats available |
| :::no-loc text="AssignedSeats"::: | Number of assigned seats |
| :::no-loc text="BilledRevenueUSD"::: | Billed revenue in US dollars |
| :::no-loc text="CustomerName"::: | Name of the customer |
| :::no-loc text="CustomerTPid"::: | Identifier of the customer top parent |
| :::no-loc text="CustomerSegment"::: | Customer segment |
| :::no-loc text="CustomerMarket"::: | Geographical market of the customer |
| :::no-loc text="ResellerStatus"::: | Reseller status |
| :::no-loc text="IndustryName"::: |Type of Industry the customer belongs|
| :::no-loc text="VerticalName"::: |Business Vertical within the Industry of the Customer |
| :::no-loc text="EOU"::: | Enterprise Organizational Unit, Focus areas for Subsidiary levels. For example, SMC Commercial, USA – Northeast, JPN - Kansai|

## **Subscription details report**

> [!NOTE]
>Revenue and ACR data are available only to users who are Executive report viewers.

| Column name | Data description |
| :--------- | :--------- |
| :::no-loc text="PGAMpnID"::: | Identifier of the partner global account |
| :::no-loc text="SubscriptionId"::: | GUID of the subscription|
| :::no-loc text="SubscriptionStartDate"::: | Start date of the subscription|
| :::no-loc text="SubscriptionEndDate"::: | End date of the subscription|
| :::no-loc text="SubscriptionState"::: | State of the subscription (Active or Churned)|
| :::no-loc text="Month"::: | Month for which usage and revenue are reported|
| :::no-loc text="IsAutoRenew"::: | Indicates whether the subscription is autorenewed (Yes or No)|
| :::no-loc text="CustomerName"::: | Name of the customer|
| :::no-loc text="CustomerTenantId"::: | GUID of the customer|
| :::no-loc text="CustomerTpid"::: | Customer top parent identifier|
| :::no-loc text="DUNSNumber"::: | Global Data Universal Number System Identifier of customer|
| :::no-loc text="CustomerSegment"::: | Market segment of the customer|
| :::no-loc text="TopSegment"::: | Higher-level segment classification of customer|
| :::no-loc text="CustomerMarket"::: | Geographical market of the customer|
| :::no-loc text="ReportingProductName"::: | Granular product name|
| :::no-loc text="Product"::: | Product sold to the customer by the partner|
| :::no-loc text="RawProductName"::: | Detailed product name sold to the customer|
| :::no-loc text="ProductPartNumber"::: | Part number of the product|
| :::no-loc text="SKU"::: | SKU of the product|
| :::no-loc text="RevSumDivisionName"::: | Revenue reporting product hierarchy name|
| :::no-loc text="SolutionArea"::: | Business application classification of the product|
| :::no-loc text="MPNID"::: | Microsoft AI Cloud Partner Program ID|
| :::no-loc text="PartnerName"::: | Name of the partner|
| :::no-loc text="PartnerLocation"::: | Geographical location of the partner|
| :::no-loc text="PartnerAttributionType"::: | Attribution type for the subscription|
| :::no-loc text="SalesChannel"::: | Channel of the sales - Direct, CSP (Cloud Solution Provider), and so on|
| :::no-loc text="IndustryName"::: |Type of Industry the customer belongs|
| :::no-loc text="VerticalName"::: |Business Vertical within the Industry of the Customer |
| :::no-loc text="EOU"::: | Enterprise Organizational Unit, Focus areas for Subsidiary levels. For example, SMC Commercial, USA – Northeast, JPN - Kansai|
| :::no-loc text="PricingLevel"::: | Price point of the sale|
| :::no-loc text="EnrollmentNumber"::: | Enrollment number of the subscription|
| :::no-loc text="IsDuplicateRowForPGA"::: | For multiple partner attributions under single PGA, this value is set to 0 for only one PartnerID. If the value is set to 1, then it indicates a duplicate row|
| :::no-loc text="SubscriptionStartMonth"::: | Start month of the subscription|
| :::no-loc text="ResellerID"::: | ID of reseller|
| :::no-loc text="ResellerName"::: | Reseller name|
| :::no-loc text="AvailableSeatsEOP"::: | Overall Available seats until End of Period|
| :::no-loc text="AvailableSeats"::: | Available seat difference Month on month|
| :::no-loc text="BilledRevenueUSD"::: | Revenue in USD|
| :::no-loc text="AzureConsumedRevenueUSD"::: | Azure Consumed Revenue in USD|
| :::no-loc text="CPORRevenue"::: |Revenue from the CPOR Partner attaches type|
| :::no-loc text="CPORPaidSeats"::: | Paid seats with CPOR Partner attach type|
| :::no-loc text="CPORActiveUsers"::: | Active users with CPOR Partner attach type|

## CSP Direct Partner eligibility

| Column name | Data description |
|---------|----------|
| :::no-loc text="PGAMpnID"::: | Identifier of the partner global account
| :::no-loc text="PartnerName"::: |Name of the partner
| :::no-loc text="MPNID"::: |Microsoft AI Cloud Partner Program ID
| :::no-loc text="MPNType"::: |Type of the Partner account: Global or Local account
| :::no-loc text="CustomerName"::: |Name of the customer
| :::no-loc text="CustomerID"::: |Identifier of the customer
| :::no-loc text="CustomerTenantId"::: |Identifier of the customer tenant
| :::no-loc text="MonthKey"::: |Month for which usage is reported
| :::no-loc text="SubscriptionId"::: |GUID of the subscription
| :::no-loc text="ReportingPricingLevel"::: | Serves as a specific grouping used for budgeting and forecasting purposes. A Reporting Pricing Level is the established level for Budget/Forecast to Actual revenue comparisons possible.
| :::no-loc text="DetailPricingLevelName"::: |A Detail Pricing Level is assigned to actual revenue based on rules defined and approved by the business. The fields Purchase Type and Detail User Type are determined by the Detail Pricing Level assigned to the transaction.
| :::no-loc text="SummaryPricingLevel"::: |Serves as a grouping of Detail Pricing Levels. A Summary Pricing Level has been assigned to each Detail Pricing Level.
| :::no-loc text="PartnerAttributionType"::: |Attribution type of the partner
| :::no-loc text="ProductPartNumber"::: |Part number of the product
| :::no-loc text="Product"::: |Product name
| :::no-loc text="IsDuplicateRowForPGA"::: |For multiple partner attributions under single PGA, this value is set to 0 for only one MPNId. If the value is set to 1, then it indicates a duplicate row.
| :::no-loc text="BilledRevenueUSD"::: |Billed revenue in US dollars

## **Azure usage report**

| Column name | Data description |
| :--------- | :--------- |
| :::no-loc text="PGAMpnID"::: | Identifier of the partner global account|
| :::no-loc text="SubscriptionId"::: | GUID of the subscription|
| :::no-loc text="SubscriptionStartDate"::: | The date of the start of the subscription|
| :::no-loc text="SubscriptionEndDate"::: | The date of the end of the subscription|
| :::no-loc text="FirstUseDate"::: | Date when Azure services were used first|
| :::no-loc text="SubscriptionState"::: | Current State of the subscription (Open, Closed Active or In Grace Period)|
| :::no-loc text="Month"::: | Date aggregated by month|
| :::no-loc text="ServiceLevel1"::: | Service Level 1 – Corresponds to Service Pillar such as Containers, Databases, Networking, and so on.|
| :::no-loc text="ServiceLevel2"::: | Service Level 2 – Corresponds to the Workload for the Service Pillar|
| :::no-loc text="ServiceLevel3"::: | Service name used by Azure.Microsoft.Com to white listing Azure offerings|
| :::no-loc text="ServiceLevel4"::: | Logical groupings of high-level feature set differentiations within the service. Such as General Purpose Virtual Machines, Memory Optimized Virtual Machines, Single SQL Database, Elastic SQL Database, and so on. |
| :::no-loc text="ServiceGroup2"::: | Field Revenue Accountability (FRA) areas such as AI, App Dev, IoT, and so on |
| :::no-loc text="ServiceGroup3"::: | More Detail for FRA  such as IoT Hub, Maps for IoT FRA|
| :::no-loc text="ServiceInfluencer"::: | PaaS services that drive consumption of infra resources, such as Service Fabric, Azure Databricks, AKS, and so on.|
| :::no-loc text="ComputeOS"::: | Operating System for the Compute|
| :::no-loc text="ComputeCoreSoftware"::: | Compute Core Software|
| :::no-loc text="UsageUnits"::: | The number of units that are used during the billing cycle|
| :::no-loc text="UsageQuantity"::: | Quantity of usage of resource|
| :::no-loc text="CustomerName"::: | Name of the customer|
| :::no-loc text="CustomerTenantId"::: | Tenant ID of customer|
| :::no-loc text="CustomerTpid"::: | Customer top parent ID|
| :::no-loc text="CustomerSegment"::: | Segment of the customer|
| :::no-loc text="CustomerMarket"::: | Geographical market of the customer|
| :::no-loc text="MPNID"::: | PartnerID of the customer|
| :::no-loc text="PartnerName"::: | Name of the partner|
| :::no-loc text="PartnerLocation"::: | Geographical country/region location of the partner|
| :::no-loc text="PartnerAttributionType"::: | Attribution type of the partner|
| :::no-loc text="SalesChannel"::: | Channel of the sales (Direct/CSP, Indirect/CSP, Direct, and so on)  |
| :::no-loc text="EnrollmentNumber"::: | Enrollment number of the subscription |
| :::no-loc text="IsACRDuplicateAtPGALevel"::: | For multiple partner attributions under single PGA, this value is set to 0 for only one MPNId. If the value is set to 1, then it indicates a duplicate row|
| :::no-loc text="ResellerID"::: | ID of reseller|
| :::no-loc text="ResellerName"::: | Reseller name|
| :::no-loc text="IndustryName"::: |Type of Industry the customer belongs|
| :::no-loc text="VerticalName"::: |Business Vertical within the Industry of the Customer |
| :::no-loc text="EOU"::: | Enterprise Organizational Unit, Focus areas for Subsidiary levels. For example, SMC Commercial, USA – Northeast, JPN - Kansai|
| :::no-loc text="AdminType"::: | When the Partner Attribution Type is "Partner Admin Link (PAL)," this column indicates the assigned role in the customer's subscription.|
| :::no-loc text="AssociationType"::: | Type of Association|
| :::no-loc text="ACR_USD"::: | Azure consumed revenue (ACR) in US dollars|

## **Office 365 license usage report**

| Column name | Data description |
| :--------- | :--------- |
| :::no-loc text="PGAPartnerID"::: | Identifier of the partner global account |
| :::no-loc text="CustomerTenantId"::: | Tenant ID of the customer |
| :::no-loc text="CustomerTpid"::: | Customer top parent ID |
| :::no-loc text="WorkloadName"::: | Skype for Business, Teams, Exchange Online |
| :::no-loc text="Month"::: | Month for which usage is reported |
| :::no-loc text="PaidAvailableUnits"::: | Number of paid available units |
| :::no-loc text="MonthlyActiveUsers"::: | Number of monthly active users |
| :::no-loc text="CustomerName"::: | Name of the customer |
| :::no-loc text="CustomerMarket"::: | Geographical country/region location of the customer's market |
| :::no-loc text="CustomerSegment"::: | Customer segment |
| :::no-loc text="IndustryName"::: |Type of Industry the customer belongs|
| :::no-loc text="VerticalName"::: |Business Vertical within the Industry of the Customer |
| :::no-loc text="EOU"::: | Enterprise Organizational Unit, Focus areas for Subsidiary levels. For example, SMC Commercial, USA – Northeast, JPN - Kansai|
| :::no-loc text="PartnerID"::: | Identifier of Microsoft AI Cloud Partner Program |
| :::no-loc text="PartnerName"::: | Name of the partner |
| :::no-loc text="PartnerLocation"::: | Geographical location of the partner |
| :::no-loc text="PartnerAttributionType"::: | Attribution type of the partner |
| :::no-loc text="IsDuplicateRowForPGA"::: | For multiple partner attributions under single PGA, this value is set to 0 for only one PartnerID. If the value is set to 1, then it indicates a duplicate row|

## **Enterprise Mobility license usage report**

| Column name | Data description |
| :--------- | :--------- |
| :::no-loc text="PGAMpnID"::: | Identifier of the partner global account|
| :::no-loc text="SubscriptionId"::: | GUID of the Subscription|
| :::no-loc text="SubscriptionStartDate"::: | The date of the start of the subscription|
| :::no-loc text="SubscriptionEndDate"::: | The date when the subscription ends|
| :::no-loc text="SubscriptionStatus"::: | Current state of the subscription (Open, Closed, Active or In Grace Period)|
| :::no-loc text="Month"::: | Date aggregated by month|
| :::no-loc text="SKU"::: | Product SKU|
| :::no-loc text="SKUId"::: | SKU ID of the product|
| :::no-loc text="FreeVsPaidSKU"::: | Indicates Free or Paid SKU|
| :::no-loc text="SalesModel"::: | Sales channel used for selling the subscription|
| :::no-loc text="DetailedSalesModel"::: | Detailed sales model for the subscription|
| :::no-loc text="CustomerName"::: | Name of the customer|
| :::no-loc text="CustomerTenantId"::: | Tenant ID of customer|
| :::no-loc text="CustomerTpid"::: | Customer top parent ID|
| :::no-loc text="CustomerSegment"::: | Customer segment|
| :::no-loc text="CustomerMarket"::: | Geographical country/region location of the market of customer|
| :::no-loc text="IndustryName"::: |Type of Industry the customer belongs|
| :::no-loc text="VerticalName"::: |Business Vertical within the Industry of the Customer |
| :::no-loc text="EOU"::: | Enterprise Organizational Unit, Focus areas for Subsidiary levels. For example, SMC Commercial, USA – Northeast, JPN - Kansai|
| :::no-loc text="MPNID"::: | PartnerID|
| :::no-loc text="PartnerName"::: | Name of the partner|
| :::no-loc text="PartnerLocation"::: | Geographical location of partner|
| :::no-loc text="PartnerAttributionType"::: | Attribution type of partner|
| :::no-loc text="PartnerHierarchy"::: | Hierarchy of partner (HeadQuarters or Location)|
| :::no-loc text="PaidAvailableUnits"::: | Number of paid available units|
| :::no-loc text="MonthlyActiveUsers"::: | Number of monthly active users|
| :::no-loc text="AATPActiveUsage"::: | Azure Advanced Threat Protection (AATP) active usage|
| :::no-loc text="MCASActiveUsage"::: | Microsoft 365 Defender for Cloud Apps active usage|
| :::no-loc text="AADPPaidAvailableUnits"::: | Number of paid available units for Azure Active Directory Premium (AADP)|
| :::no-loc text="IntunePaidAvailableUnits"::: | Number of paid available units for Intune|
| :::no-loc text="AzipPaidAvailableUnits"::: | Number of paid available units for Azure Information Protection|
| :::no-loc text="AADPMonthlyActiveUsers"::: | Number of monthly active users for Azure Active Directory Premium (AADP)|
| :::no-loc text="IntuneMonthlyActiveUsers"::: | Number of monthly active users for Intune|
| :::no-loc text="AzipMonthlyActiveUsers"::: | Number of monthly active users for Azure Information Protection. It's a workload reported under EMS. It has recently been renamed to Microsoft Purview Information Protection.)|
| :::no-loc text="MDM"::: | Mobile Device Management|
| :::no-loc text="MAM"::: | Mobile Application Management|
| :::no-loc text="SSPR"::: | Self-Service Password Reset|

## **Dynamics 365 license usage report**

| Column name | Data description |
| :--------- | :--------- |
| :::no-loc text="PGAMpnID"::: | Identifier of the partner global account |
| :::no-loc text="SubscriptionId"::: | GUID of the subscription |
| :::no-loc text="SubscriptionStartDate"::: | Start date of the subscription |
| :::no-loc text="SubscriptionEndDate"::: | End date of the subscription |
| :::no-loc text="SubscriptionStatus"::: | State of the subscription |
| :::no-loc text="Month"::: | Month for which usage is reported |
| :::no-loc text="RevSumDivisionName"::: | Name of the rev sum division |
| :::no-loc text="RevSumCategoryName"::: | Name of the rev sum category |
| :::no-loc text="SKU"::: | SKU of the product |
| :::no-loc text="SKUId"::: | SKU ID of the product |
| :::no-loc text="FreeVsPaidSKU"::: | Indicates whether it's a free or paid SKU |
| :::no-loc text="SalesModel"::: | Sales channel that's used for selling the subscription |
| :::no-loc text="DetailedSalesModel"::: | Detailed sales model for the subscription |
| :::no-loc text="CustomerName"::: | Name of the customer |
| :::no-loc text="CustomerTenantId"::: | GUID of the customer tenant |
| :::no-loc text="CustomerTpid"::: | Customer top parent identifier |
| :::no-loc text="CustomerSegment"::: | Market segment of the customer |
| :::no-loc text="CustomerMarket"::: | Geographical market of the customer |
| :::no-loc text="IndustryName"::: |Type of Industry the customer belongs|
| :::no-loc text="VerticalName"::: |Business Vertical within the Industry of the Customer |
| :::no-loc text="EOU"::: | Enterprise Organizational Unit, Focus areas for Subsidiary levels. For example, SMC Commercial, USA – Northeast, JPN - Kansai|
| :::no-loc text="MPNID"::: | Identifier of Microsoft AI Cloud Partner Program |
| :::no-loc text="PartnerName"::: | Name of the partner |
| :::no-loc text="PartnerLocation"::: | Geographical country/region location of the partner |
| :::no-loc text="PartnerAttachType"::: | Attribution type for the subscription |
| :::no-loc text="AvailableSeats"::: |Current paid available seats|
| :::no-loc text="AssignedSeats"::: |Current assigned seats|
| :::no-loc text="ActiveSeats"::: |Current active seats|
| :::no-loc text="DeploymentOpportunity"::: |Deployment opportunity is the number of seats that aren't assigned|
| :::no-loc text="ActiveUsagePercent"::: |Current active usage as a percentage of available seats |

## Power BI license usage report

| Column name | Data description |
| :--------- | :--------- |
| :::no-loc text="PGAMpnID"::: | Identifier of the partner global account |
| :::no-loc text="SubscriptionId"::: | GUID of the subscription |
| :::no-loc text="SubscriptionStartDate"::: | Start date of the subscription |
| :::no-loc text="SubscriptionEndDate"::: | End date of the subscription |
| :::no-loc text="SubscriptionStatus"::: | State of the subscription (Active, Inactive, or In Grace Period) |
| :::no-loc text="Month"::: | Date aggregated by month |
| :::no-loc text="SKU"::: | SKU of the product |
| :::no-loc text="SKUId"::: | SKU ID of the product |
| :::no-loc text="FreeVsPaidSKU"::: | Free or paid SKU differentiator |
| :::no-loc text="SalesModel"::: | Sales model that's used to sell the subscription |
| :::no-loc text="DetailedSalesModel"::: | Detailed sales model for the subscription |
| :::no-loc text="CustomerName"::: | Name of the customer |
| :::no-loc text="CustomerTenantId"::: | GUID of the customer tenant |
| :::no-loc text="CustomerTpid"::: | Identifier of the customer top parent |
| :::no-loc text="CustomerSegment"::: | Market segment of the customer |
| :::no-loc text="CustomerMarket"::: | Geographical market of the customer |
| :::no-loc text="IndustryName"::: |Type of Industry the customer belongs|
| :::no-loc text="VerticalName"::: |Business Vertical within the Industry of the Customer |
| :::no-loc text="EOU"::: | Enterprise Organizational Unit, Focus areas for Subsidiary levels. For example, SMC Commercial, USA – Northeast, JPN - Kansai|
| :::no-loc text="MPNId"::: | Identifier of Microsoft AI Cloud Partner Program |
| :::no-loc text="PartnerName"::: | Name of the partner |
| :::no-loc text="PartnerLocation"::: | Geographical country/region location of the partner |
| :::no-loc text="PartnerAttachType"::: | Attribution type for the subscription |
| :::no-loc text="PartnerHierarchy"::: |Hierarchy of partner (HeadQuarters or Location)|
| :::no-loc text="AvailableSeats"::: | Current paid available seats|
| :::no-loc text="AssignedSeats"::: |Current assigned seats|
| :::no-loc text="ActiveSeats"::: |Current active seats|
| :::no-loc text="DeploymentOpportunity"::: |Deployment opportunity is the number of seats that aren't assigned|
| :::no-loc text="ActiveUsagePercent"::: |Current active usage as a percentage of available seats|

## Business applications revenue

| Column name | Data description |
| :--------- | :--------- |
| :::no-loc text="FiscalMonthName"::: | Month and year information regarding the data|
| :::no-loc text="GlobalPartnerID"::: | Global partner ID of the partner|
| :::no-loc text="PartnerName"::: | Name of the partner|
| :::no-loc text="PartnerAssociationType"::: | Partner association type, for example, CSP T1, DPOR, PAL|
| :::no-loc text="CustomerID"::: | Unique identifier for a customer in Microsoft record|
| :::no-loc text="CustomerName"::: | Name of the customer|
| :::no-loc text="CustomerTenantID"::: | Tenant ID of the customer|
| :::no-loc text="CustomerTenantName"::: | Name of the customer at the tenant level|
| :::no-loc text="SubscriptionId"::: | Identifier for the subscription|
| :::no-loc text="SubscriptionStartDate"::: | Start date of the subscription|
| :::no-loc text="Country"::: | Country/region of the customer|
| :::no-loc text="WorkloadCategory"::: | Category of the workload|
| :::no-loc text="Workloads"::: | Appropriate workload for the subscription, such as AI Builder, Business Central, CE Bundle, Commerce, Customer Insights, Customer Service, F&O Bundle, Field Service, Finance|
| :::no-loc text="AdjustedRevenueAmtCD"::: | Revenue details for the subscription|

## Business applications usage

| Column name | Data description |
| :--------- | :--------- |
| :::no-loc text="FiscalMonthName"::: |Month and year information regarding the data|
| :::no-loc text="GlobalPartnerID"::: |Global partner ID of the partner|
| :::no-loc text="PartnerName"::: |Name of the partner|
| :::no-loc text="PartnerAssociationType"::: |Partner association type, for example, CSP T1, DPOR, PAL|
| :::no-loc text="CustomerID"::: |Unique identifier for a customer in Microsoft record|
| :::no-loc text="CustomerName"::: |Name of the customer|
| :::no-loc text="CustomerTenantID"::: |Tenant ID of the customer|
| :::no-loc text="CustomerTenantName"::: |Name of the customer at the tenant level|
| :::no-loc text="SubscriptionID"::: |Identifier for the subscription|
| :::no-loc text="SubscriptionStartDate"::: |Start date of the subscription|
| :::no-loc text="MetricType"::: |Type of the subscription paid or trial|
| :::no-loc text="WorkloadCategory"::: |Category of the workload|
| :::no-loc text="Workload"::: |Appropriate workload for the subscription, such as AI Builder, Business Central, CE Bundle, Commerce, Customer Insights, Customer Service, F&O Bundle, Field Service, Finance|
| :::no-loc text="SkuGroup"::: |Group to which the SKU belongs|
| :::no-loc text="PAMAU"::: |Partner attached monthly active users|
| :::no-loc text="MAC"::: |Monthly active capacity|
| :::no-loc text="MAU"::: |Monthly active users|

## Teams meetings and calls report

| Column name | Data description |
| :--------- | :--------- |
| :::no-loc text="PGAMpnID"::: | Identifier of the partner global account |
| :::no-loc text="CustomerId"::: | Identifier of the customer top parent |
| :::no-loc text="CustomerTenantId"::: | Tenant ID of the customer |
| :::no-loc text="CustomerName"::: |Customer name |
| :::no-loc text="CustomerCountryCode"::: | Country Code of the customer|
| :::no-loc text="CustomerCountry"::: |Customer country/region |
| :::no-loc text="CustomerSegment"::: | Type of Customer segment, for example Major Commercial, Major Public Sector, Small, Medium & Corporate Commercial, and so on.|
| :::no-loc text="IndustryName"::: |Type of Industry the customer belongs|
| :::no-loc text="VerticalName"::: |Business Vertical within the Industry of the Customer |
| :::no-loc text="EOU"::: | Enterprise Organizational Unit, Focus areas for Subsidiary levels. For example, SMC Commercial, USA – Northeast, JPN - Kansai|
| :::no-loc text="DateKey"::: |Date for which usage is reported
| :::no-loc text="Subworkload"::: | Subworkload for which usage is reported (meetings, calls, or phone systems) |
| :::no-loc text="Meeting count"::: | Number of meetings |
| :::no-loc text="Meeting duration"::: | Total meeting duration in hours |

## Teams monthly usage report

| Column name | Data description |
| :--------- | :--------- |
| :::no-loc text="PGAMpnID"::: |Identifier of the partner global account |
| :::no-loc text="CustomerId"::: |Identifier of the customer top parent|
| :::no-loc text="CustomerTenantId"::: |Tenant ID of the customer|
| :::no-loc text="CustomerName"::: |Customer name |
| :::no-loc text="CustomerCountryCode"::: | Country Code of the customer|
| :::no-loc text="CustomerCountry"::: |Customer country/region |
| :::no-loc text="CustomerSegment"::: | Type of Customer segment, for example Major Commercial, Major Public Sector, Small, Medium & Corporate Commercial, and so on.|
| :::no-loc text="MonthKey"::: |Month for which usage is reported|
| :::no-loc text="SubWorkload"::: |Subworkload for which usage is reported (Meetings, calls or phone systems)|
| :::no-loc text="DesktopUsers"::: |Number of users who use Teams on desktop|
| :::no-loc text="WebUsers"::: |Number of users who use Teams on the web|
| :::no-loc text="MobileUsers"::: |Number of users who use Teams on mobile|
| :::no-loc text="AllUpParticipants"::: |Number of unique users of Teams for the month|
| :::no-loc text="IndustryName"::: |Type of Industry the customer belongs|
| :::no-loc text="VerticalName"::: |Business Vertical within the Industry of the Customer |
| :::no-loc text="EOU"::: | Enterprise Organizational Unit, Focus areas for Subsidiary levels. For example, SMC Commercial, USA – Northeast, JPN - Kansai|

## Teams usage 3P apps report

| Column name | Data description |
| :--------- | :--------- |
| :::no-loc text="PGAMpnID"::: | Identifier of the partner global account |
| :::no-loc text="CustomerId"::: |Customer top parent ID |
| :::no-loc text="CustomerTenantId"::: |Tenant ID of the customer |
| :::no-loc text="CustomerName"::: |Customer name |
| :::no-loc text="CustomerCountryCode"::: | Country Code of the customer|
| :::no-loc text="CustomerCountry"::: |Customer country/region |
| :::no-loc text="CustomerSegment"::: | Type of Customer segment, for example Major Commercial, Major Public Sector, Small, Medium & Corporate Commercial, and so on.|
| :::no-loc text="IndustryName"::: |Type of Industry the customer belongs|
| :::no-loc text="VerticalName"::: |Business Vertical within the Industry of the Customer |
| :::no-loc text="EOU"::: | Enterprise Organizational Unit, Focus areas for Subsidiary levels. For example, SMC Commercial, USA – Northeast, JPN - Kansai|
| :::no-loc text="DateKey"::: |Date for which usage is reported |
| :::no-loc text="AppName"::: |Name of the Teams app |
| :::no-loc text="Usercount"::: |Number of users for the app |

## Trainings, exams and certifications

| Column name | Data description |
| :--------- | :--------- |
| :::no-loc text="PGAMpnId"::: | Identifier of the partner global account |
| :::no-loc text="TrainingActivityId"::: | Identifier of the training |
| :::no-loc text="TrainingTitle"::: | Title of the training |
| :::no-loc text="TrainingType"::: | Type of training (certification or exam) |
| :::no-loc text="IndividualFirstName"::: | First name of the customer |
| :::no-loc text="IndividualLastName"::: | Last name of the customer |
| :::no-loc text="Email"::: | Personal email ID of the customer |
| :::no-loc text="CorpEmail"::: | Office email ID of the customer |
| :::no-loc text="TrainingCompletionDate"::: | Completion date of the training |
| :::no-loc text="ExpirationDate"::: |Expiration Date of the Certification|
| :::no-loc text="ActivationStatus"::: |Status of the Certification|
| :::no-loc text="Month"::: | Month for which the data is reported |
| :::no-loc text="IcMCP"::: | Indicates whether the user is a Microsoft Certified Professional (MCP) |
| :::no-loc text="MCPID"::: | MCP ID of the user |
| :::no-loc text="MpnId"::: | Identifier of Microsoft AI Cloud Partner Program |
| :::no-loc text="PartnerName"::: | Name of the partner |
| :::no-loc text="PartnerCityLocation"::: | Geographical city location of the partner |
| :::no-loc text="PartnerCountryLocation"::: | Geographical country/region location of the partner |

## Microsoft Learn report

| Column name | Data description |
| :--------- | :--------- |
| :::no-loc text="PGAMpnId"::: | Identifier of the partner global account |
| :::no-loc text="UserName"::: | Name of the user |
| :::no-loc text="UserId"::: | GUID of the user |
| :::no-loc text="TrainingName"::: | Name of the training |
| :::no-loc text="TrainingType"::: | Type of training  (module or learning path) |
| :::no-loc text="Products"::: | Product for which the learning module is applicable |
| :::no-loc text="Roles"::: | Applicable roles of the training |
| :::no-loc text="CompletionDate"::: | Date of completion of the training |
| :::no-loc text="MPNId"::: | Identifier of Microsoft AI Cloud Partner Program |
| :::no-loc text="PartnerName"::: | Name of the partner |
| :::no-loc text="Country"::: | Geographical country/region location of the partner |

## Cloud Ascent - Microsoft 365 propensity report

| Column name   | Data description|
|-------------|-------------------|
| :::no-loc text="MPNID"::: | Microsoft AI Cloud Partner Program ID               |
| :::no-loc text="PartnerName"::: | Name of the partner                              |
| :::no-loc text="CustomerID"::: | Customer identifier number as defined by Microsoft                            |
| :::no-loc text="DUNSNumber"::: | The Dun & Bradstreet number of the customer who's being scored for propensity              |
| :::no-loc text="AccountName"::: | Name of the Customer                             |
| :::no-loc text="Domain"::: | Domain of the Customer                           |
| :::no-loc text="OrgSize"::: | Size of the organization                         |
| :::no-loc text="Industry"::: | Industry that the organization belongs           |
| :::no-loc text="Vertical"::: | The vertical of the customer who's being scored for propensity, as identified by Microsoft, D&B, and other industry standards                        |
| :::no-loc text="Area"::: | Geographical area of the Customer                |
| :::no-loc text="Subsidiary"::: | The subsidiary of the customer who's being scored for propensity              |
| :::no-loc text="SalesTerritory"::: | The sales territory of the customer who's being scored for propensity         |
| :::no-loc text="City"::: | Geographical city location of the customer       |
| :::no-loc text="State"::: | Geographical state location of the customer      |
| :::no-loc text="PostalCode"::: | Postal code of the organization of the customer  |
| :::no-loc text="Country"::: | Geographical country/region location of the customer    |
| :::no-loc text="Segment"::: | Market segment as defined by Microsoft           |
| :::no-loc text="SubSegment"::: | Market subsegments as defined by Microsoft       |
| :::no-loc text="SMCTypeSummary"::: | The categorization of a customer as defined by Microsoft: Corporate Scale Businesses meet at least one of the following criteria - High Revenue (\$100 K+), High Growth (20%+), High Potential (\$100 K+), Org Size 500+, ACR Web Direct \> $1000+ per month; Medium businesses are customers with 25 - 300 employees, small are customers with 1-24 employees                        |
| :::no-loc text="IsNonprofit"::: | Indicates whether the organization is nonprofit and approved by Microsoft or not: "Nonprofit" defines customers with an industry of nonprofit but they aren't approved by Microsoft. "Approved - Paid" defines the customers that are approved nonprofits and are paying some amount, "Approved - Free Only" defines the customers that are approved as a nonprofit by Microsoft but are only using a free SKU and aren't using products, "Approved - Inactive" defines customers who are approved but aren't using products, "No" defines the customers who aren't a nonprofit |
| :::no-loc text="MW_On Prem Acq_Office 2016_2019"::: | Target customers with On Prem Office 2016 or Office 2019 for conversion to Cloud |
| :::no-loc text="MW_On Prem Acq Office_Prod Server 2007_2010"::: | Target customers with On Prem Office/Prod Server 2007 or 2010 for conversion to Cloud |
| :::no-loc text="MW_On Prem Acq Office 2021 Office_Prod Server 2019"::: | Target customers with On Prem Office 2021 or Office/Prod Server 2019 for conversion to Cloud |
| :::no-loc text="MW_On Prem Acq Office_Prod Server 2013_Office 2019 for Mac"::: | Target customers with On Prem Office/Prod Server 2013 or Office 2019 for Mac for conversion to Cloud |
| :::no-loc text="MW_Transition Customer - Compete (Endpoint Security) with M365"::: | Target Customers with Endpoint Security and M365 for conversion to MW Cloud Suite SKU with security |
| :::no-loc text="MW_Transition Customer - Compete (Endpoint Security) without M365"::: | Target Customers with Endpoint Security but without M365 for conversion to MW Cloud Suite SKU with security |
| :::no-loc text="MW_Transition Customer - Compete (Zoom) with M365"::: | Target Customers with Zoom and M365 for conversion to teams |
| :::no-loc text="MW_Transition Customer - Compete (Zoom) without M365"::: | Target Customers with Zoom and without M365 for conversion to M365/teams |
| :::no-loc text="MW_Transition Customer - Compete Google Workspace"::: | Target Customers with Google Workspace for conversion to M365 |
| :::no-loc text="MW_Upsell Existing Cloud Customer - EMS Suites_Standalones"::: | Upsell existing EMS Suites/standalone customers to ME3 for sub-300 employee businesses or ME5 for >300 employee businesses |
| :::no-loc text="MW_Upsell Existing Cloud Customer - ME3_OE5 to ME5"::: | Upsell existing ME3 or OE5 customers to ME5 |
| :::no-loc text="MW_Upsell Existing Cloud Customer - MW Standalones_EXO_SPO_etc"::: | Upsell existing modern work standalone customers to ME3 for sub-300 employee businesses or ME5 for >300 employee businesses |
| :::no-loc text="MW_Upsell Existing Cloud Customer - No MBP_ME3_ME5"::: | Upsell existing O365 Core Products, M365 BS, O365 E3/E4 for conversion to ME3, ME5, or MBP |
| :::no-loc text="MW_Upsell Existing Cloud Customer - O365 A1"::: | Upsell existing O365 active A1 Customers to M365  |
| :::no-loc text="MW_Upsell Existing Cloud Customer - O365 A3_A5_M365 A1_A3"::: | Upsell existing O365 A3, A5, M365 A1 or A3 customers to ME5  |
| :::no-loc text="MW_Upsell Existing Cloud Customer - Underpenetrated MBP_ME3_ME5"::: | Upsell existing Customers with underpenetrated MBP, ME3, and/or ME5 to full penetration of the SKU in their business  |
| :::no-loc text="MW_Upsell Existing Cloud Customer - Teams Essentials"::: | Upsell existing teams essentials customers without O365/M365 Suites or Standalones to Microsoft Teams Phone System |
| :::no-loc text="MW_Business Premium_E SKU Attach >50"::: | Target customers with 50 or more O365 Core or M365 BP seats to purchase surface |
| :::no-loc text="MW_EDU for Surface"::: | Target EDU customers with at least 25 licenses of surface for upsell |
| :::no-loc text="MW_Surface Devices >25 Purchased in the Last 3 Years"::: |  |
| :::no-loc text="FY24 Offers"::: | Promos for FY24, Customers who are eligible for a promo  |
| :::no-loc text="M365Cluster"::: | Identifies a customer's propensity to purchase Microsoft 365. Target Act Now and Evaluate clusters because they produce higher yield. Target Nurture and Educate customers only if there's still capacity after Act Now and Evaluate customers are targeted                        |
| :::no-loc text="M365Fit"::: | Internal and external data points that define firmographics. Fit scoring uses a lookalike model to our best small or mid-sized businesses (SMBs) to compare customers and see whether they're a potential fit for Microsoft cloud products. Fit scoring is updated quarterly.         |
| :::no-loc text="M365Intent"::: | Signals related to social media and a customer's online behavior define Intent. Intent scoring is overlaid on Fit to define the clusters. Intent scoring is updated monthly.      |
| :::no-loc text="SurfaceCluster"::: | Identifies a customer's propensity to purchase Surface by consolidating the Fit and Intent recommendations into a cluster. Target Act Now and Evaluate clusters because they produce higher yield. Target Nurture and Educate customers only if there's still capacity after Act Now and Evaluate customers are targeted.    |
| :::no-loc text="SurfaceFit"::: | Internal and external data points that define firmographics. Fit scoring uses a lookalike model to our best SMBs to compare customers and see whether they're a potential fit for Microsoft cloud products. Fit scoring is updated quarterly.            |
| :::no-loc text="Surface Intent"::: | Signals related to social media and a customer's online behavior define Intent. Intent scoring is overlaid on Fit to define the clusters. Intent scoring is updated monthly.      |
| :::no-loc text="M365UpsellCustomer"::: | Identifies whether the existing customer shows upsell propensity for Microsoft 365         |
| :::no-loc text="Has Azure"::: | Identifies Active Azure Customer
| :::no-loc text="Has D365"::: | Identifies Active D365 Customer
| :::no-loc text="Has M365"::: | Identifies Active M365 Customer
| :::no-loc text="HasGoogle"::: | Identifies whether the customer shows competitive signals for owning Google products       |
| :::no-loc text="HasAWS"::: | Identifies whether the customer shows competitive signals for owning AWS products          |
| :::no-loc text="HasEA"::: | Identifies whether a renewal is an EA or an EA subscription                   |
| :::no-loc text="HasOpen"::: | Identifies whether a renewal is an Open or Open Value agreement               |
| :::no-loc text="Transactedinthelast36months"::: | Identifies if the customer has purchased in the trailing 36 month period      |

## Cloud Ascent - Dynamics 365 propensity report

| Column name    | Data description|
|-------------------|--------------|
| :::no-loc text="MPNID"::: | Microsoft AI Cloud Partner Program ID          |
| :::no-loc text="PartnerName"::: | Name of the partner                         |
| :::no-loc text="CustomerID"::: | Customer identifier number as defined by Microsoft                       |
| :::no-loc text="DUNSNumber"::: | The Dun & Bradstreet number of the customer who's being scored for propensity         |
| :::no-loc text="AccountName"::: | Name of the Customer                        |
| :::no-loc text="Domain"::: | Domain of the Customer                      |
| :::no-loc text="OrgSize"::: | Size of the organization                    |
| :::no-loc text="Industry"::: | Industry that the organization belongs      |
| :::no-loc text="Vertical"::: | The vertical of the customer who's being scored for propensity, as identified by Microsoft, D&B, and other industry standards                   |
| :::no-loc text="Area"::: | Geographical area of the Customer           |
| :::no-loc text="Subsidiary"::: | The subsidiary of the customer who's being scored for propensity         |
| :::no-loc text="SalesTerritory"::: | The sales territory of the customer who's being scored for propensity                 |
| :::no-loc text="City"::: | Geographical city location of the customer  |
| :::no-loc text="State"::: | Geographical state location of the customer |
| :::no-loc text="PostalCode"::: | Postal code of the organization of the customer                          |
| :::no-loc text="Country"::: | Geographical country/region location of the customer                            |
| :::no-loc text="Segment"::: | Market segment as defined by Microsoft      |
| :::no-loc text="SubSegment"::: | Market subsegments as defined by Microsoft  |
| :::no-loc text="SMCTypeSummary"::: | The categorization of a customer as defined by Microsoft: Corporate Scale Businesses meet at least one of the following criteria - High Revenue (\$100 K+), High Growth (20%+), High Potential (\$100 K+), Org Size 500+, ACR Web Direct \> \$1000+ per month; Medium businesses are customers with 25 - 300 employees, small are customers with 1-24 employees                   |
| :::no-loc text="IsNonprofit"::: | Indicates whether the organization is nonprofit and approved by Microsoft or not: "Nonprofit" defines customers with an industry of nonprofit but they aren't approved by Microsoft. "Approved - Paid" defines the customers that are approved nonprofits and are paying some amount, "Approved - Free Only" defines the customers that are approved as a nonprofit by Microsoft but are only using a free sku and aren't a paying customer, "Approved - Inactive" defines customers who are approved but aren't using products, "No" defines the customers who aren't a nonprofit |
| :::no-loc text="D365_BC Customers with no D365 SalesPro or Sales Enterprise"::: | Upsell Customers without Business Central but have SalesPro/Enterprise for Business Central |
| :::no-loc text="D365_CRM On Prem Customers with No D365 SalesPro Or Sales Enterprise"::: | Target customers with existing Dynamics On Prem CRM systems but don't have D365 Sales Pro or Enterprise for D365 Sales |
| :::no-loc text="D365_M365 Customers with >300 Employees with No D365 SalesPro Or Sales Enterprise"::: | Upsell existing MW customers with at least 300 employees to target for D365 Sales |
| :::no-loc text="D365_M365 Customers with <300 Employees with No D365 SalesPro or Sales Enterprise"::: | Upsell existing MW customers with fewer than 300 employees to SalesPro or Sales Enterprise |
| :::no-loc text="D365_Azure Customers with No Power Platform"::: | Upsell existing Azure customers with no D365 SalesPro, Sales Enterprise or Power Platforms and target for power platforms |
| :::no-loc text="D365_BC or D365 SalesPro Or Sales Enterprise Customers with No Power Platform"::: | Upsell existing D365 SalesPro Or Sales Enterprise Customers with No Power Platform to use Power Platform |
| :::no-loc text="D365_M365 BP_E1_E3_E5 Customer with No Power Platform"::: | Upsell existing MW customers with BP, E1, E3, or E5 to use Power Platforms |
| :::no-loc text="D365_AX Customer, No BC/Finance"::: | Target Legacy Customers with AX install base to apply D365 BC |
| :::no-loc text="D365_D365 SalesPro or Sales Enterprise Customers with No BC"::: | Upsell existing SalesPro or Sales Enterprise customers to Business Central |
| :::no-loc text="D365_GP Customer, No BC/Finance"::: | Target Legacy Customers with GP install base to use D365 BC |
| :::no-loc text="D365_M365 Customer with No BC with <300 Employees"::: | Upsell existing MW Cloud Customers with fewer than 300 employees to use Business Central |
| :::no-loc text="D365_M365 Customer with No BC No Finance No Supply Chain"::: | Upsell existing MW Cloud Customers with at least 300 employees to Business Central |
| :::no-loc text="D365_NAV Customers, No BC_Finance"::: | Target Legacy Customers with NAV install base to use D365 BC |
| :::no-loc text="D365_Quickbooks Customers with No BC"::: | Target Compete Customers with Quickbooks for Business Central |
| :::no-loc text="FY24 Offers"::: | Promos for FY24, Customers who are eligible for a promo  |
| :::no-loc text="D365BCCluster"::: | Identifies the customer's propensity to purchase Dynamics 365 Business Central. Customers who show a propensity for Business Central are in the Medium and Small categories. Target Act Now and Evaluate clusters, because they produce higher yield. Target Nurture and Educate customers only if there's still capacity after your target Act Now and Evaluate customers.    |
| :::no-loc text="D365BCFit"::: | Internal and external data points that define firmographics. Fit scoring uses a lookalike model to our best SMB to compare customers and see whether they're a potential fit for Microsoft cloud products. Fit scoring is updated quarterly.        |
| :::no-loc text="D365BCIntent"::: | Signals related to social media and a customer's online behavior define Intent. Intent scoring is overlaid on Fit to define the clusters. Intent scoring is updated monthly.              |
| :::no-loc text="D365FOCluster"::: | Identifies the customer's propensity to purchase Dynamics 365 Finance and Operations. Customers who show a propensity for Finance + Operations are in the top un-managed categories. Target Act Now and Evaluate clusters because they produce higher yield. Target Nurture and Educate customers only if there's still capacity after your target Act Now and Evaluate customers.           |
| :::no-loc text="D365FOFit"::: | Internal and external data points that define firmographics. Fit scoring uses a lookalike model to our best SMB to compare customers and see whether they're a potential fit for Microsoft cloud products. Fit scoring is updated quarterly.        |
| :::no-loc text="D365FOIntent"::: | Signals related to social media and a customer's online behavior define Intent. Intent scoring is overlaid on Fit to define the clusters. Intent scoring is updated monthly.              |
| :::no-loc text="D365CECluster"::: | Identifies the customer's propensity to purchase Dynamics 365 Customer Engagement. Customers who show a propensity for Customer Engagement are in the Medium and Small categories. Target Act Now and Evaluate clusters because they produce higher yield. Target Nurture and Educate customers only if there's still capacity after your target Act Now and Evaluate customers.            |
| :::no-loc text="D365CEFit"::: | Indicates Fit for Dynamics 365 Customer Engagement                       |
| :::no-loc text="D365CEIntent"::: | Indicates Intent for Dynamics 365 Customer Engagement                    |
| :::no-loc text="PowerAppsCluster"::: | Identifies the customer's propensity to purchase Power Apps. Target Act Now and Evaluate clusters because they produce higher yield. Target Nurture and Educate customers only if there's still capacity after your target Act Now and Evaluate customers.                     |
| :::no-loc text="PowerAppsFit"::: | Internal and external data points that define firmographics. Fit scoring uses a lookalike model to our best SMB to compare customers and see whether they're a potential fit for Microsoft cloud products. Fit scoring is updated quarterly.        |
| :::no-loc text="PowerAppsIntent"::: | Signals related to social media and a customer's online behavior define Intent. Intent scoring is overlaid on Fit to define the clusters. Intent scoring is updated monthly.              |
| :::no-loc text="DynamicsOnPremAXorCRM_HasOpenRenewal"::: | Identifies whether the customer has an open renewal for Dynamics on-premises AX or CRM                             |
| :::no-loc text="M365UpsellCustomer"::: | Identifies whether the existing customer shows upsell propensity for Microsoft 365    |
| :::no-loc text="Has Azure"::: | Identifies Active Azure Customer
| :::no-loc text="HasD365"::: | Identifies Active D365 Customer
| :::no-loc text="HasM365"::: | Identifies Active M365 Customer
| :::no-loc text="HasGoogle"::: | Identifies whether the customer shows competitive signals for owning Google products                               |
| :::no-loc text="HasAWS"::: | Identifies whether the customer shows competitive signals for owning AWS products     |
| :::no-loc text="HasEA"::: | Identifies whether a renewal is an EA or an EA subscription              |
| :::no-loc text="HasOpen"::: | Identifies whether a renewal is an Open or Open Value agreement          |
| :::no-loc text="Transactedinthelast36months"::: | Identifies if the customer has purchased in the trailing 36 month period              |

## Cloud Ascent - Azure propensity report

| Column name         | Data description|
|-------------------|--------------|
| :::no-loc text="MPNID"::: | Microsoft AI Cloud Partner Program ID          |
| :::no-loc text="PartnerName"::: | Name of the partner                         |
| :::no-loc text="CustomerID"::: | Customer identifier number as defined by Microsoft                       |
| :::no-loc text="DUNSNumber"::: | The Dun & Bradstreet number of the customer who's being scored for propensity         |
| :::no-loc text="AccountName"::: | Name of the Customer                        |
| :::no-loc text="Domain"::: | Domain of the Customer                      |
| :::no-loc text="OrgSize"::: | Size of the organization                    |
| :::no-loc text="Industry"::: | Industry that the organization belongs      |
| :::no-loc text="Vertical"::: | The vertical of the customer who's being scored for propensity, as identified by Microsoft, D&B, and other industry standards                   |
| :::no-loc text="Area"::: | Geographical area of the Customer           |
| :::no-loc text="Subsidiary"::: | The subsidiary of the customer who's being scored for propensity         |
| :::no-loc text="SalesTerritory"::: | The sales territory of the customer who's being scored for propensity                 |
| :::no-loc text="City"::: | Geographical city location of the customer  |
| :::no-loc text="State"::: | Geographical state location of the customer |
| :::no-loc text="PostalCode"::: | Postal code of the organization of the customer                          |
| :::no-loc text="Country"::: | Geographical country/region location of the customer                            |
| :::no-loc text="Segment"::: | Market segment as defined by Microsoft      |
| :::no-loc text="SubSegment"::: | Market subsegments as defined by Microsoft  |
| :::no-loc text="SMCTypeSummary"::: | The categorization of a customer as defined by Microsoft: Corporate Scale Businesses meet at least one of the following criteria - High Revenue (\$100 K+), High Growth (20%+), High Potential (\$100 K+), Org Size 500+, ACR Web Direct \>\$1000+ per month; Medium businesses are customers with 25 - 300 employees, small are customers with 1-24 employees                   |
| :::no-loc text="IsNonprofit"::: | Indicates whether the organization is nonprofit and approved by Microsoft or not: "Nonprofit" defines customers with an industry of nonprofit but they aren't approved by Microsoft. "Approved - Paid" defines the customers that are approved nonprofits and are paying some amount, "Approved - Free Only" defines the customers that are approved as a nonprofit by Microsoft but are only using a free sku and aren't a paying customer, "Approved - Inactive" defines customers who are approved but aren't using products, "No" defines the customers who aren't a nonprofit |
| :::no-loc text="Azure_Migrate and Modernize Apps with Azure Managed Databases"::: | Target Azure high propensity customers with competitor products for conversion Azure Managed Database |
| :::no-loc text="Azure_Innovate with AI_Build Intelligent Cloud Native Apps on Azure Managed Databases"::: | Target customers with Power BI or DB's for conversion to Azure Managed Database |
| :::no-loc text="Azure_Extend Edge Inferencing with Cloud-Based Model Training using Azure AI Infrastructure"::: | Target customers with Microsoft Edge products for conversion to Azure AI Infrastructure |
| :::no-loc text="Azure_Extend to AVD Workloads Requiring GPU Rendering"::: | Target customers with WVD for AVD workloads |
| :::no-loc text="Azure_Modernize HPC Workloads with Azure HPC + AI"::: | Target customers with existing HPC products for conversion to Azure HPC + AI |
| :::no-loc text="Azure_Azure Backup and ASR to Every Production Workload"::: | Target VM customers with no backup for Azure backup and Azure Site Recovery |
| :::no-loc text="Azure_Backup On Prem Data and SaaS Data"::: | Target Azure High propensity customers with win/SQL Server but no backup for backup |
| :::no-loc text="Azure_Migrate and Modernize VMware to Azure"::: | Target existing VMware customers with High propensity for Azure for conversion to Azure Virtual desktop |
| :::no-loc text="Azure_Modernize VDI to AVD"::: | Target existing VDI customers with High propensity for Azure for conversion to Azure Virtual desktop |
| :::no-loc text="Azure_Modernize VDI to AVD: Citrix IB"::: | Target existing Citrix customers with High propensity for Azure for conversion to Azure Virtual desktop |
| :::no-loc text="Azure_Modernize VDI to AVD: Cross-sell MW to Azure AVD"::: | Target existing MW customers with High propensity for Azure for conversion to Azure Virtual desktop |
| :::no-loc text="Azure_Modernize VDI to AVD: RDS IB"::: | Target existing RDS customers with High propensity for Azure for conversion to Azure Virtual desktop |
| :::no-loc text="Azure_Modernize VDI to AVD: VMWare IB"::: | Target existing VMware Horizon Cloud customers with High propensity for Azure for conversion to Azure Virtual desktop |
| :::no-loc text="Azure_Secure Migration_MDC_Network Security_and Monitor: Defender"::: | Target customers with Azure who don't have Defender for Defender attach motion |
| :::no-loc text="Azure_Secure Migration_MDC_Network Security_and Monitor: Network Security"::: | Target Customers with Azure who don't have security to add a security workload or specialization |
| :::no-loc text="Azure_Secure Migration_MDC_Network Security_and Monitor: Well Architected Security Go Back"::: | Target Customers with Azure consumption of greater than 1k for security |
| :::no-loc text="Azure_Windows Server OR SQL Server: Active Annuity"::: | Target Win Server and SQL server customers with Active Annuity for conversion to Azure |
| :::no-loc text="Azure_Windows Server OR SQL Server: Active Non-Annuity"::: | Target Win Server and SQL server customers with Non-Active Annuity for conversion to Azure |
| :::no-loc text="Azure_Windows Server OR SQL Server: EOS Prior 2012"::: | Target Win Server and SQL server customers with End of Service license prior to 2012 for conversion to Azure |
| :::no-loc text="Azure_Windows Server OR SQL Server: EOS 2012"::: | Target Win Server and SQL server customers with End of Service 2012 for conversion to Azure |
| :::no-loc text="Azure_Windows Server OR SQL Server: Inactive Annuity"::: | Target Win Server and SQL server customers with Inactive Annuity for conversion to Azure |
| :::no-loc text="Azure_Windows Server OR SQL Server: Inactive Non-Annuity"::: | Target Win Server and SQL server customers with Inactive Non-annuity for conversion to Azure |
| :::no-loc text="Azure_Migrate Linux Estate - Migrate and Modernize Linux_OSS DB to Azure"::: | Target Azure high propensity customers with Linux/OSS DB compete products for conversion to Azure |
| :::no-loc text="Azure_Migrate Oracle DBs to Oracle on Azure"::: | Target Azure high propensity customers with Linux/OSS DB compete products for conversion to Azure |
| :::no-loc text="Azure_Extend and Innovate SAP with Microsoft Cloud Services"::: | Target Azure high propensity customers with SAP for Microsoft Cloud Services |
| :::no-loc text="Azure_Migrate and Modernize to S_4HANA via RISE with SAP"::: | Target Azure high propensity customers with SAP HANA for Microsoft Cloud Services |
| :::no-loc text="Azure_SQL DW to Azure"::: | Target customers with SQL Data Warehouse for Azure |
| :::no-loc text="Azure_Modernize Enterprise Applications - Move On Prem .NET apps to Azure App Services"::: | Target Azure high propensity customers with competitor .NET apps for Azure App Services |
| :::no-loc text="Azure_Power Business Decision with Cloud Scale Analytics - Win New Analytics Scenarios"::: | Target Azure high propensity customers with compete in business intelligence for Azure Analytics |
| :::no-loc text="FY24 Offers"::: | Promos for FY24, Customers who are eligible for a promo         |
| :::no-loc text="AzureFit"::: | Internal and external data points that define firmographics. Fit scoring uses a lookalike model to our best SMB to compare customers and see whether they're a potential fit for Microsoft cloud products. Fit scoring is updated quarterly.        |
| :::no-loc text="AzureIntent"::: | Signals related to social media and a customer's online behavior define Intent. Intent scoring is overlaid on Fit to define the clusters. Intent scoring is updated monthly.              |
| :::no-loc text="AzureCluster"::: | Identifies the customer's propensity to purchase Azure by consolidating the Fit and Intent recommendations into a cluster. Target Act Now and Evaluate clusters, because they produce higher yield. Target Nurture and Educate customers only if there's still capacity after your target Act Now and Evaluate customers.                             |
| :::no-loc text="WindowsServerDataCenter_HasOpenRenewal"::: | Identifies whether the customer has an open renewal for Windows Server Datacenter     |
| :::no-loc text="WindowsServerStandard_HasOpenRenewal"::: | Identifies whether the customer has an open renewal for Windows Server Standard       |
| :::no-loc text="Has Azure"::: | Identifies Active Azure Customer    |
| :::no-loc text="Has D365"::: | Identifies Active D365 Customer    |
| :::no-loc text="Has M365"::: | Identifies Active M365 Customer    |
| :::no-loc text="HasGoogle"::: | Identifies whether the customer shows competitive signals for owning Google products                               |
| :::no-loc text="HasAWS"::: | Identifies whether the customer shows competitive signals for owning AWS products     |
| :::no-loc text="HasEA"::: | Identifies whether a renewal is an EA or an EA subscription              |
| :::no-loc text="HasOpen"::: | Identifies whether a renewal is an Open or Open Value agreement          |
| :::no-loc text="NumberofExistingWorkloads"::: | The number of existing Azure workloads that the customer has             |
| :::no-loc text="Existing Workloads"::: | The existing Azure workloads that the customer has purchased             |
| :::no-loc text="NumberofRecommendedWorkloads"::: | The number of recommended Azure workloads that the customer could be targeted for based on their past purchase history and the propensity recommendations                    |
| :::no-loc text="RecommendedWorkloads"::: | The recommended Azure workloads that the customer could be targeted for based on their past purchase history and the propensity recommendations |
| :::no-loc text="Transactedinthelast36months"::: | Identifies if the customer has purchased in the trailing 36 month period              |

## Cloud Ascent - agreement renewal propensity report

| Column name                  | Data description |
|----------------------------------|--------------|
| :::no-loc text="MPNID"::: | Microsoft AI Cloud Partner Program ID          |
| :::no-loc text="PartnerName"::: | Name of the partner                         |
| :::no-loc text="CustomerID"::: | Customer identifier number as defined by Microsoft                       |
| :::no-loc text="DUNSNumber"::: | The Dun & Bradstreet number of the customer who's being scored for propensity         |
| :::no-loc text="AccountName"::: | Name of the Customer                        |
| :::no-loc text="Domain"::: | Domain of the Customer                      |
| :::no-loc text="OrgSize"::: | Size of the organization                    |
| :::no-loc text="Industry"::: | Industry that the organization belongs      |
| :::no-loc text="Vertical"::: | The vertical of the customer who's being scored for propensity, as identified by Microsoft, D&B, and other industry standards                   |
| :::no-loc text="Area"::: | Geographical area of the Customer           |
| :::no-loc text="Subsidiary"::: | The subsidiary of the customer who's being scored for propensity         |
| :::no-loc text="SalesTerritory"::: | The sales territory of the customer who's being scored for propensity                 |
| :::no-loc text="City"::: | Geographical city location of the customer  |
| :::no-loc text="State"::: | Geographical state location of the customer |
| :::no-loc text="PostalCode"::: | Postal code of the organization of the customer                          |
| :::no-loc text="Country"::: | Geographical country/region location of the customer                            |
| :::no-loc text="Segment"::: | Market segment as defined by Microsoft      |
| :::no-loc text="SubSegment"::: | Market subsegments as defined by Microsoft  |
| :::no-loc text="SMCTypeSummary"::: | The categorization of a customer as defined by Microsoft: Corporate Scale Businesses meet at least one of the following criteria - High Revenue (\$100 K+), High Growth (20%+), High Potential (\$100 K+), Org Size 500+, ACR Web Direct \> \$1000+ per month; Medium businesses are customers with 25 - 300 employees, small are customers with 1-24 employees                   |
| :::no-loc text="IsNonprofit"::: | Indicates whether the organization is nonprofit and approved by Microsoft or not: "Nonprofit" defines customers with an industry of nonprofit but they aren't approved by Microsoft. "Approved - Paid" defines the customers that are approved nonprofits and are paying some amount, "Approved - Free Only" defines the customers that are approved as a nonprofit by Microsoft but are only using a free sku and aren't a paying customer, "Approved - Inactive" defines customers who are approved but aren't using products, "No" defines the customers who aren't a nonprofit |
| :::no-loc text="FY24 Offers"::: | Promos for FY24, Customers who are eligible for a promo
| :::no-loc text="HasGoogle"::: | Identifies whether the customer shows competitive signals for owning Google products                               |
| :::no-loc text="HasAWS"::: | Identifies whether the customer shows competitive signals for owning AWS products     |
| :::no-loc text="AzureCluster"::: | Identifies the customer's propensity to purchase Azure by consolidating the Fit and Intent recommendations into a cluster. Target Act Now and Evaluate clusters, because they produce higher yield. Target Nurture and Educate customers only if there's still capacity after you target Act Now and Evaluate customers.
| :::no-loc text="D365FOCluster"::: | Identifies the customer's propensity to purchase Dynamics 365 Finance and Operations. Customers who show a propensity for Finance + Operations are in the top un-managed categories. Target Act Now and Evaluate clusters, because they produce higher yield. Target Nurture and Educate customers only if there's still capacity after you target Act Now and Evaluate customers.
| :::no-loc text="D365CECluster"::: | Identifies the customer's propensity to purchase Dynamics 365 Customer Engagement. Customers who show a propensity for Customer Engagement are in the Medium and Small categories. Target Act Now and Evaluate clusters, because they produce higher yield. Target Nurture and Educate customers only if there's still capacity after you target Act Now and Evaluate customers.
| :::no-loc text="D365BCCluster"::: | Identifies the customer's propensity to purchase Dynamics 365 Business Central. Customers who show a propensity for Business Central are in the Medium and Small categories. Target Act Now and Evaluate clusters, because they produce higher yield. Target Nurture and Educate customers only if there's still capacity after you target Act Now and Evaluate customers.
| :::no-loc text="PowerAppsCluster"::: | Identifies the customer's propensity to purchase Power Apps. Target Act Now and Evaluate clusters, because they produce higher yield. Target Nurture and Educate customers only if there's still capacity after you target Act Now and Evaluate customers.
| :::no-loc text="M365Cluster"::: | Identifies a customer's propensity to purchase Microsoft 365. Target Act Now and Evaluate clusters because they produce higher yield. Target Nurture and Educate customers only if there's still capacity after Act Now and Evaluate customers are targeted  
| :::no-loc text="License Program"::: | Identifies the license program type for the renewal                      |
| :::no-loc text="Agreement ID"::: | Identifier of the agreement as defined by Microsoft                      |
| :::no-loc text="Agreement End Date"::: | End date of the agreement                   |
| :::no-loc text="Expiration Type"::: | Type of expiration                          |
| :::no-loc text="Expiring Revenue"::: | Revenue associated with expiring subscriptions                           |
| :::no-loc text="Has EA"::: | Identifies whether a renewal is an EA or an EA subscription              |
| :::no-loc text="Has Open"::: | Identifies whether a renewal is an Open or Open Value agreement          |
| :::no-loc text="Microsoft365UpsellCustomer"::: | Identifies whether the existing customer shows upsell propensity for Microsoft 365    |
| :::no-loc text="RevSumDivisionName"::: | Identifies the product that's up for renewal                             |
| :::no-loc text="TransactedInTheLast36months"::: | Identifies if the customer has purchased in the trailing 36 month period              |

## Cloud Ascent - Surface propensity report

| Column name    | Data description                    |
|-------------|--------------|
| :::no-loc text="MPN ID"::: | Microsoft AI Cloud Partner Program ID          |
| :::no-loc text="PartnerName"::: | Name of the partner                         |
| :::no-loc text="CustomerID"::: | Customer identifier number as defined by Microsoft                       |
| :::no-loc text="DUNSNumber"::: | The Dun & Bradstreet number of the customer who's being scored for propensity         |
| :::no-loc text="AccountName"::: | Name of the Customer                        |
| :::no-loc text="Domain"::: | Domain of the Customer                      |
| :::no-loc text="OrgSize"::: | Size of the organization                    |
| :::no-loc text="Industry"::: | Industry that the organization belongs      |
| :::no-loc text="Vertical"::: | The vertical of the customer who's being scored for propensity, as identified by Microsoft, D&B, and other industry standards                   |
| :::no-loc text="Area"::: | Geographical area of the Customer           |
| :::no-loc text="Subsidiary"::: | The subsidiary of the customer who's being scored for propensity         |
| :::no-loc text="SalesTerritory"::: | The sales territory of the customer who's being scored for propensity                 |
| :::no-loc text="City"::: | Geographical city location of the customer  |
| :::no-loc text="State"::: | Geographical state location of the customer |
| :::no-loc text="PostalCode"::: | Postal code of the organization of the customer                          |
| :::no-loc text="Country"::: | Geographical country/region location of the customer                            |
| :::no-loc text="Segment"::: | Market segment as defined by Microsoft      |
| :::no-loc text="SubSegment"::: | Market subsegments as defined by Microsoft  |
| :::no-loc text="SMCTypeSummary"::: | The categorization of a customer as defined by Microsoft: Corporate Scale Businesses meet at least one of the following criteria - High Revenue (\$100 K+), High Growth (20%+), High Potential (\$100 K+), Org Size 500+, ACR Web Direct \> \$1000+ per month; Medium businesses are customers with 25 - 300 employees, small are customers with 1-24 employees                   |
| :::no-loc text="IsNonprofit"::: | Indicates whether the organization is nonprofit and approved by Microsoft or not: "Nonprofit" defines customers with an industry of nonprofit but they aren't approved by Microsoft. "Approved - Paid" defines the customers that are approved nonprofits and are paying some amount, "Approved - Free Only" defines the customers that are approved as a nonprofit by Microsoft but are only using a free sku and aren't a paying customer, "Approved - Inactive" defines customers who are approved but aren't using products, "No" defines the customers who aren't a nonprofit |
| :::no-loc text="MW_On Prem Acq_Office 2016_2019"::: | Target customers with On Prem Office 2016 or Office 2019 for conversion to Cloud |
| :::no-loc text="MW_On Prem Acq Office_Prod Server 2007_2010"::: | Target customers with On Prem Office/Prod Server 2007 or 2010 for conversion to Cloud |
| :::no-loc text="MW_On Prem Acq Office 2021 Office_Prod Server 2019"::: | Target customers with On Prem Office 2021 or Office/Prod Server 2019 for conversion to Cloud |
| :::no-loc text="MW_On Prem Acq Office_Prod Server 2013_Office 2019 for Mac"::: | Target customers with On Prem Office/Prod Server 2013 or Office 2019 for Mac for conversion to Cloud |
| :::no-loc text="MW_Transition Customer - Compete (Endpoint Security) with M365"::: | Target Customers with Endpoint Security and M365 for conversion to MW Cloud Suite SKU with security |
| :::no-loc text="MW_Transition Customer - Compete (Endpoint Security) without M365"::: | Target Customers with Endpoint Security but without M365 for conversion to MW Cloud Suite SKU with security |
| :::no-loc text="MW_Transition Customer - Compete (Zoom) with M365"::: | Target Customers with Zoom and M365 for conversion to teams |
| :::no-loc text="MW_Transition Customer - Compete (Zoom) without M365"::: | Target Customers with Zoom and without M365 for conversion to M365/teams |
| :::no-loc text="MW_Transition Customer - Compete Google Workspace"::: | Target Customers with Google Workspace for conversion to M365 |
| :::no-loc text="MW_Upsell Existing Cloud Customer - EMS Suites_Standalones"::: | Upsell existing EMS Suites/standalone customers to ME3 for sub-300 employee businesses or ME5 for >300 employee businesses |
| :::no-loc text="MW_Upsell Existing Cloud Customer - ME3_OE5 to ME5"::: | Upsell existing ME3 or OE5 customers to ME5 |
| :::no-loc text="MW_Upsell Existing Cloud Customer - MW Standalones_EXO_SPO_etc"::: | Upsell existing modern work standalone customers to ME3 for sub-300 employee businesses or ME5 for >300 employee businesses |
| :::no-loc text="MW_Upsell Existing Cloud Customer - No MBP_ME3_ME5"::: | Upsell existing O365 Core Products, M365 BS, O365 E3/E4 for conversion to ME3, ME5, or MBP |
| :::no-loc text="MW_Upsell Existing Cloud Customer - O365 A1"::: | Upsell existing O365 active A1 Customers to M365  |
| :::no-loc text="MW_Upsell Existing Cloud Customer - O365 A3_A5_M365 A1_A3"::: | Upsell existing O365 A3, A5, M365 A1 or A3 customers to ME5  |
| :::no-loc text="MW_Upsell Existing Cloud Customer - Under-penetrated MBP_ME3_ME5"::: | Upsell existing Customers with under-penetrated MBP, ME3, and/or ME5 to full penetration of the SKU in their business  |
| :::no-loc text="MW_Upsell Existing Cloud Customer - Teams Essentials"::: | Upsell existing teams essentials customers without O365/M365 Suites or Standalones to Microsoft Teams Phone System |
| :::no-loc text="MW_Business Premium_E SKU Attach >50"::: | Target customers with 50 or more O365 Core or M365 BP seats to purchase surface |
| :::no-loc text="MW_EDU for Surface"::: | Target EDU customers with at least 25 licenses of surface for upsell |
| :::no-loc text="MW_Surface Devices >25 Purchased in the Last 3 Years"::: |  |
| :::no-loc text="FY24 Offers"::: | Promos for FY24, Customers who are eligible for a promo  |
| :::no-loc text="M365Cluster"::: | Identifies a customer's propensity to purchase Microsoft 365. Target Act Now and Evaluate clusters because they produce higher yield. Target Nurture and Educate customers only if there's still capacity after Act Now and Evaluate customers are targeted                   |
| :::no-loc text="M365Fit"::: | Internal and external data points that define firmographics. Fit scoring uses a lookalike model to our best small or mid-sized businesses (SMBs) to compare customers and see whether they're a potential fit for Microsoft cloud products. Fit scoring is updated quarterly.    |
| :::no-loc text="M365Intent"::: | Signals related to social media and a customer's online behavior define Intent. Intent scoring is overlaid on Fit to define the clusters. Intent scoring is updated monthly.              |
| :::no-loc text="SurfaceCluster"::: | Identifies a customer's propensity to purchase Surface by consolidating the Fit and Intent recommendations into a cluster. Target Act Now and Evaluate clusters because they produce higher yield. Target Nurture and Educate customers only if there's still capacity after Act Now and Evaluate customers are targeted.                            |
| :::no-loc text="SurfaceFit"::: | Internal and external data points that define firmographics. Fit scoring uses a lookalike model to our best SMBs to compare customers and see whether they're a potential fit for Microsoft cloud products. Fit scoring is updated quarterly.       |
| :::no-loc text="SurfaceIntent"::: | Signals related to social media and a customer's online behavior define Intent. Intent scoring is overlaid on Fit to define the clusters. Intent scoring is updated monthly.              |
| :::no-loc text="M365UpsellCustomer"::: | Identifies whether the existing customer shows upsell propensity for Microsoft 365    |
| :::no-loc text="Has Azure"::: | Identifies Active Azure Customer    |
| :::no-loc text="Has D365"::: | Identifies Active Dynamics 365 Customer    |
| :::no-loc text="Has M365"::: | Identifies Active Microsoft 365 Customer    |
| :::no-loc text="HasGoogle"::: | Identifies whether the customer shows competitive signals for owning Google products                               |
| :::no-loc text="HasAWS"::: | Identifies whether the customer shows competitive signals for owning AWS products     |
| :::no-loc text="HasEA"::: | Identifies whether a renewal is an EA or an EA subscription              |
| :::no-loc text="HasOpen"::: | Identifies whether a renewal is an Open or Open Value agreement          |
| :::no-loc text="Transacted in the last 36 months"::: | Identifies if the customer has purchased in the trailing 36 month period              |
| :::no-loc text="SurfaceFit"::: | Internal and external data points that define firmographics. Fit scoring uses a lookalike model to our best SMBs to compare customers and see whether they're a potential fit for Microsoft cloud products. Fit scoring is updated quarterly.       |
| :::no-loc text="SurfaceIntent"::: | Signals related to social media and a customer's online behavior define Intent. Intent scoring is overlaid on Fit to define the clusters. Intent scoring is updated monthly.              |
| :::no-loc text="M365UpsellCustomer"::: | Identifies whether the existing customer shows upsell propensity for Microsoft 365    |
| :::no-loc text="HasGoogle"::: | Identifies whether the customer shows competitive signals for owning Google products                               |
| :::no-loc text="HasAWS"::: | Identifies whether the customer shows competitive signals for owning AWS products     |
| :::no-loc text="HasEA"::: | Identifies whether a renewal is an EA or an EA subscription              |
| :::no-loc text="HasOpen"::: | Identifies whether a renewal is an Open or Open Value agreement          |
| :::no-loc text="Transacted in the last 36 months"::: | Identifies if the customer has purchased in the trailing 36 month period

## CPOR-M365 usage report

| Column name | Data description |
| :--------- | :--------- |
| :::no-loc text="CustomerTenantId"::: | Tenant ID of the customer |
| :::no-loc text="CustomerName"::: | Name of the customer |
| :::no-loc text="WorkloadName"::: | Name of the workload |
| :::no-loc text="MonthlyActiveUsers"::: | MAU (monthly active users) |
| :::no-loc text="PaidAvailableUnits"::: | PAU (paid available units) |
| :::no-loc text="ClaimId"::: | Claim ID of the workload |
| :::no-loc text="MpnId"::: | Microsoft AI Cloud Partner Program ID |
| :::no-loc text="DateAssociated"::: | Associated date of the workload with the partner |
| :::no-loc text="PartnerAttributionType"::: | Partner Attribution Type (CPOR) |
| :::no-loc text="Date"::: | Date (first of month and year) for which the data is exported |

## Next steps

- [Download reports](insights-download-reports.md)
