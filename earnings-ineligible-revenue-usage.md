---
title: Earnings - Ineligible revenue usage page in Partner Center
description: Find out information about commerce incentives that are ineligible for Earnings in Partner Center
ms.date: 9/20/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-earnings
ms.topic: article
author: deeparamani
ms.author: deramani
---

# Earnings – Ineligible revenue usage report in Partner Center

**Appropriate roles**: *Incentives*: Incentives admin | Incentives user

To see commerce incentives that are ineligible for Earnings in Partner Center:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Earnings** > **Reports**.
1. Select **Download > Ineligible revenue usage details**. The report that downloads contains the following attributes:

| Attribute name | Description | Availability |
| --- | ---| ---|
| **agreementNumber**  | Enterprise agreement number | Only for any Enterprise Agreement-based engagements  |
| **compensableUnits**<br><br>**compensableUnitsAlt** | Compensable Units are calculated by subtracting the Prior High Water Mark (HWM) at the start of the month by Tenant/workload from the paid seats at the end of the month by Tenant/workload. For example, Compensable units by tenant and workload = Paid seats – Prior HWM. | Applicable for Microsoft Commerce Incentives – Modern Workplace Usage and Online Advisor  |
| **customerId** | Identity of the customer associated with a subscription/resource. | All  |
| **customerIdType** | Top Parent ID (TPID) or Tenant ID. TPID is available for Azure consumption engagements and some build intent workshops. The rest have tenant IDs. | All  |
| **customerName** | Name of customer  | All  |
| **earningParticipantId** <br><br>**earningParticipantIdType** <br><br>**earningParticipantName** | Partner identity in the transact relationship | For all incentive, store and marketplace programs. Useful when multiple transacting partner IDs are mapped into a single enrollment ID |
| **engagementName** | Name of the incentives engagement under Microsoft Commerce Incentives | Only for transactions dated Oct 1, 2021 and later  |
| **invoiceNumber**  | Invoice number | Only for modern partner-led, field-led and customer-led for Azure consumption, all new commerce transactions for other products. |
| **partnerAssociation** | Type of relationship partner has to a customer. Examples: reseller, PAL.Owner | For all incentive, store and marketplace programs  |
| **partnerCountryCode** | Enrolled Microsoft AI Cloud Partner Program location | All  |
| **partnerId**  | PartnerID of the enrolled partner  | All  |
| **partnerName**  | Name of the partner  | All  |
| **partnerRole**  | Categorization of the kind of engagement. Categories include: **build intent**, **transact**, **deploy** and **use**. | For Microsoft Commerce Incentives only |
| **productId**  | Commerce product name. Available for commerce-based transactions  | All  |
| **productFamily**  | Product family | All  |
| **reason** | Reason for ineligibility  | All  |
| **subscriptionId** | Subscription ID  | Only for commerce transactions (subscription-based) and Azure consumption  |
| **transactionAmountUSD** | Consumption amount in US dollars | All  |
| **transactionDate**  | Date of consumption or billing  | All  |
| **unearnedId** | Unique identifier that can help you to create a support inquiry | All  |
| **quantity** | Indicates the active usage or seats  | Only for BizApps usage-based engagements |
| **quantityType** | Elaborates the type of quantity—for example, MAU or seats  | Only for BizApps usage-based engagements |
| **quantityAlt**  | Alternate quantity value  | Optionally available for incentive programs. Example: Modern Work usage. |
| **quantityAltType**  | Alternate quantity unit For example, Paid available units (PAU)  | Optionally available for incentive programs. Example: For Modern Work usage.  |
| **resourceID** | Indicates the resource  | Applicable for Business Applications with PAL  |
| **solutionArea** | High level product categorization. Examples: Azure, Modern Work and Security. | For Microsoft Commerce Incentives only |
| **workload** | Service name or workload name. Applicable for Azure consumption or monthly active usage based data.  | Only for Azure consumption and BizApps usage |

## Next steps

- [Earnings - Default](./earnings-default.md)
