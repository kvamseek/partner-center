---
title: Usage dashboard in commercial marketplace analytics | Azure Marketplace
description: Overview of usage dashboard providing insights for raw and metered usage of VM, containers, SAAS and Azure apps offers published on Azure Marketplace.
ms.service: partner-dashboard 
ms.subservice: partnercenter-insights
ms.topic: article
author: saurabhsharmaa
ms.author: saurasharma
ms.date: 06/14/2023
---

# Usage dashboard in commercial marketplace analytics

This article provides information on the Usage dashboard in Partner Center.
The [Usage dashboard](https://go.microsoft.com/fwlink/?linkid=2166106) displays the insights for usage of your Virtual machines (VM), Software as a service (SaaS), Azure apps and container offers.

> [!IMPORTANT]
> The maximum latency between usage event generation and reporting in Partner Center is 48 hours.

## Navigating to pages in Usage dashboard

Usage dashboard consists five different pages to view insights for specific scenarios.

- **Virtual Machine**
  - *VM Normalized usage* - This page shows insights around Normalized usage for your Virtual Machine (VM) offers.
  - *VM Raw usage* - This page shows insights around Raw usage for your Virtual Machine (VM) offers.
- **Custom meters**
  - *Metered usage* - This page shows insights around metered usage for your Containers, Azure apps and Software as a service (SaaS) offers.
  - *Metered usage anomalies* - This page shows insights around anomalies in metered usage.
- **Containers**
  - *Containers Raw usage* - This page shows insights around raw usage for your container offers.

> [!NOTE]
> VM normalized usage is the default page when you land on Usage dashboard.

You can navigate to different pages of usage dashboard by selecting the dropdown at the top of the dashboard.

:::image type="content" source="./media/usage-dashboard/usage-type-picker.png" alt-text="Screenshot of the dropdown picker on the Usage dashboard." lightbox="./media/usage-dashboard/usage-type-picker.png":::

## Public and private offer

You can easily filter the insights based on public or private offers. Each page has three tabs

- **All** - This is the default selection and will show aggregated insights for both Public and Private offers.
- **Public Offers** - Click on this tab to view the insights for usage related to Public offers.
- **Private Offers** - Click on this tab to view the insights for usage related to Private offers.

:::image type="content" source="./media/usage-dashboard/usage-dashboard-tabs.png" alt-text="Screenshot of the three tabs on the Usage dashboard." lightbox="./media/usage-dashboard/usage-dashboard-tabs.png":::

> [!NOTE]
> For detailed definitions of analytics terminology, see [Commercial marketplace analytics terminology and common questions](./analytics-faq.yml).

## Usage details table

> [!IMPORTANT]
> To download the data in CSV, please use the Download data option available on top of page.

The **usage details** table displays a numbered list of the top 500 usage records sorted by usage. Note the following:

- Data in this table is displayed based on the page you've selected.

- Each column in the grid is sortable.

Click on the ellipsis (three dots '...') to copy the widget image or download the image as a pdf for sharing purposes.

:::image type="content" source="./media/usage-dashboard/vm-usage-details.png" alt-text="Screenshot of the Usage details widget." lightbox="./media/usage-dashboard/vm-usage-details.png":::

### Data dictionary

|Column name in<br>user interface|Column name in Download through UI|Definition|Column name in programmatic<br>access reports|
| ------------ | ------------- | ------------- | ------------- |
|Marketplace Subscription ID|Marketplace Subscription ID|The unique identifier associated with the Azure subscription the customer used to purchase your commercial marketplace offer. ID was formerly the Azure Subscription GUID.|MarketplaceSubscriptionId|
|Month Start Date|MonthStartDate|Month Start Date represents the month of purchase.|MonthStartDate|
|Offer Type|Offer Type|This field indicates the type of commercial marketplace offering. It classifies the nature of the product available through the marketplace.|OfferType|
|Sales channel|Azure License Type|The type of licensing agreement used by customers to purchase Azure. Also known as the Channel. The possible values are:<br>-Cloud Solution Provider<br>-Enterprise<br>-Enterprise through Reseller<br>-Pay as You Go|AzureLicenseType|
|Marketplace License Type |Marketplace License Type|The billing method of the commercial marketplace offer. The possible values are:<br>-Billed Through Azure<br>-Bring Your Own License<br>-Free<br>-Microsoft as Reseller|MarketplaceLicenseType|
|Plan|SKU|The plan associated with the offer.|SKU|
|Customer Country|Customer Country|The country/region name provided by the customer. Country/region could be different than the country/region in a customer's Azure subscription.|CustomerCountry|
|Is Preview SKU|Is Preview SKU|The value shows if you've tagged the plan as "preview". Value is "Yes" if the plan has been tagged accordingly, and only Azure subscriptions authorized by you can deploy and use this image. Value is "No" if the plan hasn't been identified as "preview".|IsPreviewSKU|
|SKU Billing Type|SKU Billing Type|The Billing type associated with each plan in the offer. The possible values are:<br>-Free<br>-Paid|SKUBillingType|
|VM Size|VM Size|For VM-based offer types, this entity signifies the size of the VM associated with the plan of the offer.|VMSize|
|Cloud Instance Name|Cloud Instance Name|Microsoft Cloud Instance in which a VM deployment occurred.|CloudInstanceName|
|Offer Name|Offer Name|Name of the commercial marketplace offering.|OfferName|
|Is Private Offer|Is Private Offer|Indicates whether a marketplace offer is a private or a public offer:<br>-0 value indicates false<br>-1 value indicates true|IsPrivateOffer|
|Deployment Method|DeploymentMethod|This field signify|DeploymentMethod|
|Customer name|Customer name|Name of the "billed to" customer|CustomerName|
|Customer Company Name|Customer Company Name|The company name provided by the customer. The name could be different than the name in a customer's Azure subscription.|CustomerCompanyName|
|Usage Date|Usage Date|The date of usage event generation for usage-based assets.|UsageDate|
|IsMultisolution|Is Multisolution|Signifies whether the offer is a Multisolution offer type.|N/A|
|Is New Customer|IsNewCustomer|This field indicates if the customer is new.|IsNewCustomer|
|Core Size|Core Size|Number of cores associated with the VM-based offer.|CoreSize|
|Usage Type|Usage Type|Signifies whether the usage event associated with the offer is one of the following:<br><br>-Normalized usage<br>-Raw usage<br>-Metered usage|N/A|
|Trial End Date|Trial End Date|The date the trial period for this order ends or has ended.|TrialEndDate|
|Customer Currency (CC)|Customer Currency (CC)|The currency used by the customer for the commercial marketplace transaction.|CustomerCurrencyCC|
|Price (CC)|Price (CC)|Unit price of the plan shown in customer currency.|PriceCC|
|Payout Currency (PC)|Payout Currency (PC)|Publisher is paid for the usage events associated with the asset in the currency configured by the publisher.|PayoutCurrencyPC|
|Estimated Price (PC)|Estimated Price (PC)|Unit price of the plan in the currency configured by the publisher.|EstimatedPricePC|
|Usage Reference|Usage Reference|A concatenated GUID that is used to connect the Usage Report (in commercial marketplace analytics) with the Payout transaction report. Usage Reference is connected with OrderId and LineItemId in the Payout transaction report.|UsageReference|
|Usage Unit|Usage Unit|Unit of consumption associated with the plan|UsageUnit|
|Customer ID|Customer ID|The unique identifier assigned to a customer. A customer may have zero or more Azure Marketplace subscriptions.|CustomerId|
|Billing Account ID|Billing Account ID|The identifier of the account on which billing is generated. Map **Billing Account ID** to **customerID** to connect your Payout Transaction Report with the Customer, Order, and Usage Reports.|BillingAccountId|
|Usage Quantity|Usage Quantity|The total usage units consumed by the asset that is deployed by the customer.<br>This is based on Usage type item. For example, if the Usage Type is Normalized usage, then Usage Quantity is for Normalized Usage.|N/A|
|NormalizedUsage|Normalized Usage|The total normalized usage units consumed by the asset that is deployed by the customer.<br>Normalized usage hours are defined as the usage hours normalized to account for the number of VM cores ([number of VM vCPU] x [hours of raw usage]). VMs designated as "SHAREDCORE" use 1/6 (or 0.1666) as the [number of VM vCPU] multiplier.|NormalizedUsage|
|MeteredUsage|Metered Usage|The total usage units consumed by the meters that are configured with the offer that is deployed by the customer.|MeteredUsage|
|RawUsage|Raw Usage|The total raw usage units consumed by the asset that is deployed by the customer.<br>Raw usage hours are defined as the number of time VMs have been running in terms of usage units.|RawUsage|
|Estimated Extended Charge in Customer Currency|Estimated Extended Charge (CC)|Signifies the charges associated with the usage. The column is the product of Price (CC) and Usage Quantity.|EstimatedExtendedChargeCC|
|Estimated Extended Charge in Payout Currency|Estimated Extended Charge (PC)|Signifies the charges associated with the usage. The column is the product of Estimated Price (PC) and Usage Quantity.|EstimatedExtendedChargePC|
|Meter ID|Meter ID|**Applicable for offers with custom meter dimensions.**<br>Signifies the meter ID for the offer.|MeterId|
|Metered Dimension|Metered Dimension|**Applicable for offers with custom meter dimensions.**<br>Metered dimension of the custom meter. For example, user/device - billing unit|MeterDimension|
|Partner Center Detected Anomaly|Partner Center Detected Anomaly|**Applicable for offers with custom meter dimensions**.<br>Signifies whether the publisher reported overage usage for the offer’s custom meter dimension that was flagged as an anomaly by Partner Center. The possible values are: <br> 0 (Not an anomaly) <br> 1 (Anomaly) <br> *If the publisher doesn’t have offers with custom meter dimensions, and exports this column through programmatic access, then the value is null.*|PartnerCenterDetectedAnomaly|
|Publisher Marked Anomaly|Publisher Marked Anomaly|**Applicable for offers with custom meter dimensions**.<br>Signifies whether the publisher acknowledged the overage usage by the customer for the offer’s custom meter dimension as genuine or false. The possible values are:<br><br>-0 (Publisher has marked it as not an anomaly)<br>-1 (Publisher has marked it as an anomaly)*If the publisher doesn’t have offers with custom meter dimensions, and exports this column through programmatic access, then the value is null.*|PublisherMarkedAnomaly|
|New Reported Usage|New Reported Usage|**Applicable for offers with custom meter dimensions**.<br>For overage usage by the customer for the offer’s custom meter dimension identified as anomalous by the publisher. This field specifies the new overage usage reported by the publisher.<br>*If the publisher doesn’t have offers with custom meter dimensions, and exports this column through programmatic access, then the value is null.*|NewReportedUsage|
|Action Taken At|Action Taken At|**Applicable for offers with custom meter dimensions**.<br>Specifies the time when the publisher acknowledged the overage usage by the customer for the offer’s custom meter dimension as genuine or false.<br>*If the publisher doesn’t have offers with custom meter dimensions, and exports this column through programmatic access, then the value is null.* |ActionTakenAt|
|Action Taken By|Action Taken By|**Applicable for offers with custom meter dimensions**.<br>Specifies the person who acknowledged the overage usage by the customer for the offer’s custom meter dimension as genuine or false.<br>*If the publisher doesn’t have offers with custom meter dimensions, and exports this column through programmatic access, then the value is null.* |ActionTakenBy|
|Estimated Financial Impact in USD|Estimated Financial Impact (USD)|**Applicable for offers with custom meter dimensions**.<br>When Partner Center flags an overage usage by the customer for the offer’s custom meter dimension as anomalous, the field specifies the estimated financial impact (in USD) of the anomalous overage usage.<br>*If the publisher doesn’t have offers with custom meter dimensions, and exports this column through programmatic means, then the value is null.* |EstimatedFinancialImpactUSD|
|Asset ID|Asset ID|**Applicable for offers with custom meter dimensions**.<br>The unique identifier of the customer's order subscription for your commercial marketplace service. Virtual machine usage-based offers aren't associated with an order.|N/A|
|PlanId|PlanID|The display name of the plan entered when the offer was created in Partner Center. PlanId was originally a number.|PlanID|
|Reference ID|Reference ID|A key to link transactions of usage-based offers with corresponding transactions in the orders report. For SaaS offers with custom meters, this key represents the AssetId. For VM software reservations, this key can be used for linking orders and usage reports.|ReferenceId|
|List Price in USD|List Price(USD)|The publicly listed price of the offer plan in U.S dollars|ListPriceUSD|
|Discount Price in USD|Discount Price(USD)|The discounted price of the offer plan in U.S dollars|DiscountPriceUSD|
|Is Private Plan|Is Private Plan|Indicates whether an offer plan is private plan:<br>-0 value indicates false<br>-1 value indicates true |IsPrivatePlan|
|Offer ID|Offer ID|ID to identify a marketplace offer|OfferId|
|Private offer ID|Private Offer ID|ID to identify a private marketplace offer|PrivateOfferId|
|Private Offer Name|Private Offer Name|The name provided during private offer creation|PrivateOfferName|
|Billing ID|Billing ID|The Billing ID of the enterprise customer|BillingId|
|Customer Adjustment (USD)|Customer Adjustment (USD)|The price offered by the Channel partner to the billed customer in U.S Dollars. This value will be empty for ISV partners, as only Channel partners can see the final adjusted price for the customer|CustomerAdjustmentUSD|
|MultiParty|MultiParty|Flag indicating whether a private offer transaction involved multi-parties.<br>-1 indicates both an ISV and a channel partner were involved. <br>-0 indicates only an ISV partner was involved. |MultiParty|
|Partner Info|Partner Info|Represents SellerID and name of the partners involved in a Multiparty private offer transaction.|PartnerInfo|
|Sales Notes|Sales Notes|Sales note added by an ISV or a Channel partner during private offer creation. An ISV cannot view Channel Partner’s Sales notes and vice versa.|SalesNotes|
|Plan Type|Plan Type|Type of Azure App deployed. It can be either Managed Application or Solution Templates and it can't be private.|PlanType|
|Customer Access|Customer Access|This column denotes if customer has **Full access** or **Restricted access** for deployment of Azure app.|CustomerAccess|
|Publisher Access|Publisher Access|This column denotes if publisher access is **Enabled** or **Disabled** for deployment of Azure app|PublisherAccess|

## Next steps

- View insights around usage for your Virtual Machine (VM) offers, see [Usage Dashboard for VM in commercial marketplace analytics](./usage-vm-dashboard.md)
- View insights around usage for your Containers offers, see [Usage Dashboard for containers in commercial marketplace analytics](./usage-containers-dashboard.md)
- View insights around metered usage for your offers, see [ Metered Usage Dashboard in commercial marketplace analytics](usage-metered-dashboard.md)
- View insights around metered usage anomalies, see [ Metered Usage anomalies](anomaly-detection.md)
- For frequently asked questions about commercial marketplace analytics and for a comprehensive dictionary of data terms, see [Commercial marketplace analytics terminology and common questions](./analytics-faq.yml)


