---
title: Azure usage report
description: Learn how to use Partner Center Azure usage report.
ms.service: partner-dashboard
ms.subservice: partnercenter-insights
author: kshitishsahoo
ms.author: ksahoo
ms.topic: how-to
ms.date: 8/17/2023
---

# How to use the Azure usage report

**Appropriate roles**: Global admin | Admin agent | Report viewer | Executive report viewer

## Overview

Azure consumption revenue (ACR) is the monetary value of Azure services consumed by a customer.

> ACR = quantity of a metered resource * price-per-unit-payed by the the customer

*Price-per-unit-payed by the customer* can be:

- Retail, pay-as-you-go rate for a direct customer

  **\- or -**

- Discounted rate for an enterprise customer

ACR aggregated for all metered resources consumed within an Azure subscription is the *ACR for the subscription*.

ACR aggregated across all subscriptions that belong to an enrollment is the *ACR for the enrollment*.

## Data Definitions

The following table lists data terms and their respective definitions.

| Data term | Description | Classification | How to use |
|:---|:---|:---:|:---:|
| PGAPartnerID | Identifier of the partner global account | ID | NA |
| SubscriptionId | GUID of the subscription | ID | NA |
| SubscriptionStartDate | The date of the start of the subscription | Measure | Time range for subscriptions |
| SubscriptionEndDate | The date of the end of the subscription | Measure | Time range for subscriptions |
| FirstUseDate | Date when Azure services were used first | Measure | Time-sensitive considerations |
| SubscriptionState | Current State of the subscription (Open, Closed Active or In Grace Period) | Dimension | Filtering for a particular subscription type |
| Month | Date aggregated by month | Measure | Filtering for a particular month |
| ServiceLevel1 | Service Level 1 – Corresponds to Service Pillar such as Containers, Databases, Networking, and so on. | Dimension | Filtering on the Product/offering type |
| ServiceLevel2 | Service Level 2 – Corresponds to the Workload for the Service Pillar | Dimension | Filtering on the Product/offering type |
| ServiceLevel3 | Service name used by Azure.Microsoft.Com to white listing Azure offerings | Dimension | Filtering on the Product/offering type |
| ServiceLevel4 | Logical groupings of high-level feature set differentiations within the service. Such as General-Purpose Virtual Machines, Memory Optimized Virtual Machines, Single SQL Database, Elastic SQL Database, and so on. | Dimension | Filtering on the Product/offering type |
| ServiceGroup2 | Field Revenue Accountability (FRA) areas such as AI, App Dev, IoT, and so on | Dimension | Filtering on the Product/offering type |
| ServiceGroup3 | More detail for FRA such as IoT Hub, Maps for IoT FRA | Dimension | Filtering on the product/offering type |
| ServiceInfluencer | PaaS services that drive consumption of infra resources, such as Service Fabric, Azure Databricks, AKS, and so on. | Dimension | Filtering on the influencers |
| ComputeOS | Operating System for the Compute | Dimension | Filtering on the computing OS |
| ComputeCoreSoftware | Compute Core Software | Dimension | Filtering on the core software |
| UsageUnits | The number of units that are used during the billing cycle | Dimension | Filtering on a particular Unit |
| UsageQuantity | Quantity of usage of resource | Measure | Counting the usage units to monitor usage |
| CustomerName | Name of the customer | ID | NA |
| CustomerTenantId | Tenant ID of customer | ID | NA |
| CustomerTpid | Customer top parent ID | ID | NA |
| CustomerSegment | Segment of the customer | Dimension | Filtering on the customer segment |
| CustomerMarket | Geographical market of the customer | Dimension | Filtering on the customer market |
| PartnerID | PartnerID of the customer | ID | NA |
| PartnerName | Name of the partner | ID | NA |
| PartnerLocationID | Geographical country/region location of the partner | Dimension | Filtering on a particular country/region |
| PartnerAttributionType | Attribution type of the partner | Dimension | Filtering on partner attribution type for various partners |
| SalesChannel | Channel of the sales (Direct/CSP, Indirect/CSP, Direct, and so on) | Dimension | Filtering on sales channel |
| EnrollmentNumber | Enrollment number of the subscription | ID | NA |
| IsACRDuplicateAtPGALevel | For multiple partner attributions under single PGA, this value will be set to 0 for only one PartnerID. If the value is set to 1, then it indicates a duplicate row | Flag | Essential flag to use when you're aggregating at the PGA level |
| IsACRDuplicateAtPGAAttachTypeLevel | For multiple partner attributions under single PGA and AttachType combination, this value will be set to 0 for only one PGA PartnerID and AttachType combination. If the value is set to 1, then it indicates a duplicate row | Flag | Essential flag to be used when you're aggregating at the PGA & AttachType granularity |
| IsACRDuplicateAtMPNLevel | For multiple partner attributions under single PartnerID, this value will be set to 0 for only one of the AttachTypes under the PartnerID. If the value is set to 1, then it indicates a duplicate row | Flag | Essential flag to be used when you're aggregating at the PartnerID level |
| ResellerID | ID of reseller | ID | NA |
| ResellerName | Reseller name | ID | NA |
| IndustryName | Type of industry the customer belongs | Dimension | Filtering on a particular industry type |
| VerticalName | Business Vertical within the Industry of the Customer | Dimension | Filtering on a particular vertical type |
| EOU | Enterprise Organizational Unit, for example, SMB-Commercial, Healthcare, Manufacturing | Dimension | Filtering on a particular EOU type |
| AdminType | When the Partner Attribution Type is "Partner Admin Link (PAL)," this column indicates the assigned role in the customer's subscription. | Dimension | Filtering on a particular admin type |
| AssociationType | Type of Association | Dimension | Filtering on a particular association type |
| MonthlySubscriptionLevelACR | Monthly subscription level ACR | Measure | Direct sum, pivot table on the association types |
| ACR_USD | Azure consumed revenue (ACR) in US dollars | Measure | Direct sum, pivot table on the association types, |

## Aggregate functions

The following table lists aggregate functions that can be used with each classification.

| Classification | Possible aggregate functions |
|:---|:---:|
| ID | Count, Distinct Count, Filter |
| Dimension | Count, Distinct Count, Filter |
| Measure | Sum, Avg., Min, Max, Count |

## Available partner attribution types

The following table lists available partner attribution types.

| Partner attribution type | Notes | External links |
|:---:|:---|:---|
| Partner admin link | "PAL" customer provisions partner with admin access to subscription. | [Link PartnerID](/azure/cost-management-billing/manage/link-partner-id) |
| Partner of record | "DPOR" or "POR". Associate's servicing partners to a customer subscription. Requires partner PartnerID tagging. | [Link a PartnerID](https://support.microsoft.com/topic/link-a-partner-id-for-azure-performance-pal-or-dpor-a8eed43b-82a8-f017-3b1a-f9c8aa385d32) |
| CSP Tier 1 | Cloud Solution Provider Distinguishes between direct (T1) and indirect (T2) partners. CSP Tier 1 - Partners who buy from MSFT and sells to end-customer. The Partner or Reseller manages everything: the relationship, support, and billing. Reflects **direct** CSP partner for customer subscription. Any changes in ownership of subscription will retroactively restate full ACR history. | [Azure offers](https://azure.microsoft.com/offers/ms-azr-0145p/) |
| CSP Tier 2 | Cloud Solution Provider Distinguishes between direct (T1) and indirect (T2) partners. Tier 2 – Are partners of Indirect Resellers, they acquire new customers and manage the relationship. Reflects **indirect** CSP partner for customer subscription. Any changes in ownership of subscription will retroactively restate full ACR history. | [Azure offers](https://azure.microsoft.com/offers/ms-azr-0145p/) |
| Transacting partner of record | Associates a transacting partner as listed in MS Sales to customer revenue, licenses, usage, and consumption. Various types of transacting partners exist, such as Distributor, Reseller, Software Advisor and can all be associated to a given customer record at the same time. | |
| Partner as end-customer | Microsoft Partner consuming against their own subscription. | |
| Deal registration | Customer promise to consume based on partner co-sell solution. Amounts reflect % of deal amount, not actual consumption. All amounts land one month in arrears. | |

## Available flags and usage guide

### IsDuplicateAtPGALevel

| Attach type | Priority *|
|------------|:---------:|
|Partner admin link | 0
|Transacting partner of record | 1
| Partner of record | 2
| CSP Tier 1 | 3
| CSP Tier 2 | 4
| Partner as end-customer | 5

**\*** A lower priority number means a higher priority.

This filter is to be used when aggregating/analyzing revenues that are attributed to multiple PartnerIDs under a single PGA PartnerID.

You can use it only when the report is being viewed/downloaded at PGA PartnerID level, when you want to know the total revenue attributed to the PGA PartnerID across all Partner AttachTypes.

This field isn't required when analyzing a report at a PLA PartnerID level.

For example, when there are two PartnerIDs under a PGA PartnerID that has two different partners attach types for the same ACR row, only one of the rows is marked with IsDuplicateAtPGALevel=0. The duplicate row is marked with IsDuplicateAtPGALevel=1.

The PLA PartnerID within PGA PartnerID that has a higher priority AttachType is marked with 0, and the other is marked with 1 (duplicate). An illustration is shown below. Whenever the report is downloaded at PGA level and total revenue under the PGA PartnerID needs to be calculated, filter and use only IsDuplicateAtPGALevel=0.

:::image type="content" source="media/pga.png" alt-text="Screenshot of PGA.":::

### IsDuplicateAtPGAAttachTypeLevel

This filter is to be used when a report is being viewed/downloaded at PGA PartnerID when you want to know how much revenue was attributed to each attach type under a PGA PartnerID.

This filter is to be used when aggregating/analyzing revenues that are attributed to multiple PartnerIDs under a single PGA PartnerID.

This field isn't required when analyzing the report at a PLA PartnerID level.

For example, when there are two PartnerIDs within a PGA PartnerID that have PAL attributions for an ACR row, only one of the rows is marked with IsDuplicateAtPGAAttachTypeLevel=0. The duplicate row is marked with IsDuplicateAtPGAAttachTypeLevel=1.

The PLA PartnerID within PGA PartnerID that has a higher priority role (Owner > Contributor) is marked with 0, and the other is marked with 1 (duplicate).

An illustration is shown below.

Whenever a report is downloaded at PGA level and you need to calculate total revenue for each AttachType under the PGA PartnerID, filter and use only IsDuplicateAtPGAAttachTypeLevel=0.

:::image type="content" source="media/pga-attach.png" alt-text="Screenshot of PGA attach.":::

### IsDuplicateAtMPNLevel

The following table shows the priority in which ACR attribution is done based on attach types.

| Attach type | Priority *|
|------------|:---------:|
|Partner admin link | 0|
|Transacting partner of record | 1|
| Partner of record | 2|
| CSP Tier 1 | 3|
| CSP Tier 2 | 4|
| Partner as end-customer | 5|

**\*** A lower number means a higher priority.

Use this flag when viewing/downloading a report using the PartnerID column when you want to know the total revenue attributed to the single PartnerID across all Partner AttachTypes. (This column can contain PGA or PLA PartnerIDs.)

This field isn't required when analyzing the report at a PGA PartnerID level.

For example, when a single PartnerIDs has two different partners attach types for the same ACR row, only one of the rows is marked with IsDuplicateAtMPNLevel=0. The duplicate row is marked with IsDuplicateAtMPNLevel=1.

The row that has a higher priority AttachType is marked with 0 and the other is marked with 1 (duplicate).

An illustration is shown below.

Whenever you need to calculate the total revenue under a single PartnerID (Using PartnerID), filter and use only IsDuplicateAtMPNLevel=0.

:::image type="content" source="media/mpn-100.png" alt-text="Screenshot of Microsoft AI Cloud Partner Program 100 and attributes.":::

## Scenario-based report usage

### Advanced specializations

The following columns are relevant to this report:

- PartnerCustomer
- Tenant related Tables
- Service Level 1, Service Level 2, Service Level 3, Service Level 4
- Service Group 2, Service Group 3
- Service Influencer
- Compute OS
- Compute Core Software
- ACR

The following table lists the filters for advanced specialization.

| Advanced specialization | Filters to be used |
|---|---|
| Data Warehouse migration to Microsoft Azure | *Azure Synapse Analytics ACR: Service Level 2 = Azure Synapse Analytics* |
| Kubernetes on Microsoft Azure | *Azure Kubernetes Service (AKS) ACR: Service Influencer = AKS, AKS-EngineAzure RedHat OpenShift ACR: Service Group 3 = ARO, Service Level 2 = All except "Unknown"* |
| Microsoft Windows virtual desktop | Windows Virtual Desktop ACR: Service Influencer = NATIVE WVD |
| Modernization of web applications to Microsoft Azure | Azure App Service ACR: Service Level 1 = Compute and Service Level 2 = Azure App Service</br>Azure Spring Cloud ACR:</br>ACR Adjustment Type = N/A</br>Service Group 2 = App Dev</br>Service Group 3 = Spring Cloud</br>Service Level 2 = All except "Unknown" |
| Analytics on Microsoft Azure |Azure Synapse Analytics ACR: Service Level 2 = Azure Synapse Analytics</br>Data Lake ACR: Service Group 3 = Azure Data Lake</br>Databricks ACR: Service Group3 = Databricks</br>Azure Data Factory ACR: Service Level 2 = Azure Data Factory, Azure Data Factory v2 |
| Hybrid cloud infrastructure with Microsoft Azure Stack HCI | Azure Stack HCI ACR: Service Level 2 = Azure Stack HCI |
| Microsoft Azure VMware solution | Azure VMware Solutions(AVS) ACR: Service Level 4 = Azure VMware Solution, Azure VMware Solution by CloudSimple, Azure VMware Solution by Virtustream, Specialized Compute Azure VMware Solution |
| Build and modernize AI apps with Microsoft Azure| ServiceLevel1: (Compute), ServiceLevel2: (Azure App Service), ServiceGroup2: (App Dev), ServiceGroup3: (Spring Cloud) |
| AI and machine learning in Microsoft Azure | AI ACR: Service Group 2 = AI |
| Infra and database migration to Microsoft Azure (Windows)| Windows ACR:ACR Adjustment Type = N/A, Compute Core SW = Core,Compute OS = WINDOWS THEN Compute OS Attribute = WINDOWS, UNKNOWN or Compute OS = LINUX THEN Compute OS Attribute = WINDOWS-AHUBService Level 2 = Cloud Services, Container Instances, Container Registry, Specialized Compute, Virtual Machines, Virtual Machines LicensesSQL Database (DB) ACR: Service Group 3 = SQLDBSQL Azure SQL Managed Instance ACR: Service Group 3 = SQL DB MISQL VM ACR: Service Group 3 = SQL on IaaS, SQL on IaaS VM |
| Infra and database migration to Microsoft Azure (Linux) | Linux Virtual Machines (VM)ACR:Option 1:ACR Adjustment Type= N/A, Service Level 2 = Virtual Machines, Compute OS= Linux, Compute OS Attribute = Non-Windows, UNKNOWN, WindowsService Level 4 = All EXCEPT Cloud Services MS Series, Virtual Machines MS Series, Virtual Machines MS Series Windows, Virtual Machines MSv2 Series, Virtual Machines MSv2 Series Windows, MS Series Dedicated Host, MSv2 Series Dedicated HostOption 2: only require filters on Service Level 4, other fields like Compute OS/Compute OS Attributes aren't requiredService Level 4 = Red Hat Enterprise Linux, Red Hat Enterprise Linux with HA, SUSE Linux Enterprise Server Basic, SUSE Linux Enterprise Server for HPC Priority, SUSE Linux Enterprise Server for HPC Standard, SUSE Linux Enterprise Server Priority, SUSE Linux Enterprise Server StandardAzure Database (DB) for MariaDB ACR: Service Level 1 = Databases and Service Level 2 = Azure Database for MariaDBAzure DB for MySql ACR: Service Level 1 = Databases and Service Level 2 = Azure Database for MySQL and MySQL Database on AzureAzure DB for PostgreSQL ACR: Service Level 1 = Databases and Service Level 2 = PostgreSQLAzure COSMOS DB ACR: Service Level 1 = Databases and Service Level 2 = Cosmos DB |
| Threat protection | Microsoft Sentinel ACR: Service Level 4 = Sentinel |
| Cloud Security | Hybrid Environment XDR and Network Security ACR: Service Level 4 = Microsoft Defender for SQL, Microsoft Defender for container registries, Microsoft Defender for Kubernetes, Microsoft Defender for Storage, Application Gateway WAF v2, WAF Application Gateway, Azure Active Directory B2C, Azure Active Directory Domain Services, Azure Active Directory for External Identities, Azure Bastion, Azure DDOS Protection, Azure Firewall, Azure Firewall Manager, Azure Front Door Service, Microsoft Defender for IoT, Azure Dedicated HSM, Key Vault, Network Watcher, Microsoft Defender for App Service, Microsoft Defender for servers, Sentinel |
| SAP on Microsoft Azure | SAP Workloads ACR: Service Level 4 = Cloud Services MS Series, Virtual Machines MS Series, Virtual Machines MS Series Windows, Virtual Machines MSv2 Series, Virtual Machines MSv2 Series Windows, MS Series Dedicated Host, MSv2 Series Dedicated Host, SAP HANA on Azure Large Instances,SAP Cloud Platform Alert Notification, SAP Cloud Platform Extension Factory - Kyma Runtime,SAP Cloud Platform Integration Suite - Additional Messages, SAP Cloud Platform Integration Suite - Standard Edition, SAP Cloud Platform Transport Management, SAP Edge Services, SAP Embrace API Management,SAP Embrace Application Logging, SAP Embrace Application Runtime, SAP Embrace Bandwidth, SAP Embrace Business Application Studio, SAP Embrace Business Rules, SAP Embrace Cloud Integration, SAP Embrace Credential Store, SAP Embrace Custom Domain, SAP Embrace Data Intelligence, SAP Embrace Enterprise Messaging, SAP Embrace Extension Factory, serverless runtime, SAP Embrace Hana Cloud, SAP Embrace Identity Authentication, SAP Embrace Job Scheduler, SAP Embrace MACC, SAP Embrace Mobile Services,SAP Embrace Object Store Service, SAP Embrace Open Connectors, SAP Embrace Portal, SAP Embrace Process Visibility, SAP Embrace Web Analytics, SAP Embrace Workflow, SAP HANA Service, SAP Web IDE, BareMetal Infrastructure, Virtual Machines MdSv2 Series, Virtual Machines MdSv2 Series Windows |

### Revenue (monthly, quarterly, annually)

This table lists columns and filters for revenue reporting.

| Use | Columns to select | Filters to be used |
|--|---|---|
|For viewing ACR at PGA PartnerID level | PGAPartnerID, Month, IsACRDuplicateAtPGALevel, ACR_USD  | IsDuplicateAtPGALevel=0 |
| For viewing ACR at PartnerID level |PGAPartnerID, PartnerID, Month, IsDuplicateAtMPNLevel, ACR_USD  | IsDuplicateAtMPNLevel=0 |

### Revenue by attach types (monthly, quarterly, annually)

The following table lists columns and filters for revenue reporting.

| Use | Columns to select | Filters to be used |
|---|---|--|
| For PGA PartnerID level along with Partner attribution type | PGAPartnerID, Month, PartnerAttributionType, IsDuplicateAtPgaAttributionTypeLevel, ACR_USD  | IsDuplicateAtPGAAttachTypeLevel=0 |

### Usage

The following table lists columns and filters for usage.

| Use | Columns to select | Filters to be used |
|---|---|----|
| For viewing usage PGA PartnerID level | PGA PartnerID, Month/Datekey, ResourceGuid, ServiceLevel1, ServiceLevel2, ServiceLevel3, ServiceLevel4, ServiceLevel5, UsageUnits, UsageQuantity | IsDuplicateAtPGALevel=0 |
| For viewing usage PartnerID level | PartnerID, Month/Datekey, ResourceGuid, ServiceLevel1, ServiceLevel2, ServiceLevel3, ServiceLevel4, ServiceLevel5, UsageUnits, UsageQuantity  | IsDuplicateAtMPNLevel=0 |

## Data granularity in reports

You can view a report at various levels of granularity:

- Partner – Global
- Partner – Local
- Customer
- Tenant
- Subscriptions

## Time ranges and data availability

You can download the data for any time range—daily, weekly, monthly, quarterly, half-yearly, or annually.

Suggested  time for downloading: For previous-month data, we recommend downloading the report after the fifth date in the current data.

Reports are updated daily, but it can take from 48 to 72 hours for data from the transaction system to become available.

| Time Range | Considerations |
|---|---|
| Fiscal month | Because it takes time to update transactional data, to be safe, wait to pull data for reporting at month + two days. |

### Considerations

Be careful when considering the following partner attach types because the ACR number attribution isn't proper.

- Partner as an end-customer
- Deal registration

## FAQ

### Is ACR the same as billed revenue?

**ACR doesn't always equal billed revenue**. There are several scenarios of prepayment by an Azure customer—such as EA monetary commitment, buying a bundled SKU (also known as suite), or buying a Reserved Instance—for which billed revenue is what the customer prepays, but consumed revenue is based on actual usage of Azure services.

If a customer doesn't use everything that they prepaid for, ACR is less than billed revenue.

In the case of EA monetary commitment, if an EA customer doesn't use their entire commitment amount and forfeits the remaining balance at the end of the term, ACR includes only the consumed amount, not the forfeited amount.

ACR captures usage at the individual subscription and resource (also known as billing meter) level per calendar month, across the various "channels" that Azure is sold in—for example, direct and EA, as well as specialized ones: Azure in Open (AiO), CSP (Cloud Solution Provider), and Suites (also known as Plan SKUs or Hybrid SKUs).​

### How can ACR for historical months change? Aren't historical months "frozen" with ACR published?

ACR for historical months can change.

- Restatements typically happen for EA in the event of subscription/enrollment transfers.
- Another common scenario for change is backdated ACO or contractual credits.

Enterprise customers might have more than one enrollment, each with its own set of subscriptions.

If one enrollment's price sheet is more favorable to the customer than the other enrollment's, the customer can request that the Azure support team transfer subscriptions from other enrollment(s) to the enrollment with more favorable pricing terms. The customer could request backdating the transfer, which means they could request that the enrollment transfer become effective as of a date in the past. When support complies with the request and transfers the subscriptions, all the customer's consumption, including even historical months, is "rerated" using the destination enrollment's price sheet. Rerating results in ACR being recomputed for prior months and appearing as having changed.

In the case of an enrollment renewal, a customer can consume in overage on their expiring enrollment "A" while working on their agreement renewal discussions with their account team. When they have the new enrollment "B" in place, they could be consuming from the old enrollment for weeks or months before they place a request for transfer. That would move all existing subscriptions and their usage from the expired enrollment "A" to the renewed enrollment "B," effective from the expiration date of enrollment. As a result, all overage from the expired enrollment would move to the new enrollment "B." Again, any variation in pricing terms between enrollments "A" and "B" causes historical ACR to appear to have changed.​

ACO and other contractual credits are sometimes backdated. That triggers recalculation and reduction of ACR in prior months.

### Why am I seeing unknowns in my data and Subscriptions as 000 ?

For partner attribution types (such as Deal Registration), you'll find many columns with the value UNKNOWN, NULL or blank, and with the Subscription value  ‘00000000-0000-0000-0000-000000000000’. This value is expected because Deal Registration data is partner reported. It can’t have data for subscription details like the data we store for normal Azure subscriptions.

The major goal of having Deal Registration partner attribution type data is to have a reference to Azure Consumed Revenue, which is needed to track the co-sell eligibility of partners. The ACR is tracked via the total ACR deal volume in a given time period.

You can learn more about co-sell opportunities at [Manage co-sell opportunities](manage-co-sell-opportunities.md).

### Why CustomerName and CustomerTenantName are different in some cases ?

In some cases, you may notice that the CustomerName and CustomerTenantName differ from each other. This occurs due to a heuristic mapping used CustomerID and CustomerName for internal purposes. It's important to understand that this mapping is not intended for ensuring correctness but serves internal needs.

For all reporting purposes, we strongly recommend utilizing the data at the Tenant level, specifically the Tenant ID and CustomerTenantName. Since a customer can have multiple tenants, it can be challenging. However, in most cases, using the CustomerID should correctly group the tenants together, although it's important to note that CustomerID still relies on a heuristic mapping and does not guarantee perfect accuracy.

During the report preparation, if you encounter instances where the mapping of CustomerID and CustomerTenatantName does not align, we advise making a note of those particular CustomerIDs as exceptions. After the report is generated, manual intervention will be required to map the tenants correctly. It's important to keep in mind that while there may be a few cases where manual mapping is necessary, the majority of the mappings should be accurate without the need for intervention.

## Next steps

- [Purchase the Azure plan for customers and access the latest Azure services at pay-as-you-go rates](purchase-azure-plan.md)




