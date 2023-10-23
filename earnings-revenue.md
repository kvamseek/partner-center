---
title: Earnings – Revenue page in Partner Center
description: Learn about earnings revenue
ms.date: 9/20/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-earnings
ms.topic: article
author: deeparamani
ms.author: deramani
---

# Earnings – Revenue report in Partner Center

**Appropriate roles**: *Incentives*: Incentives admin | Incentives user

The **Revenue** page helps you:

- Understand the eligibility of revenue or usage evaluated for Microsoft Commerce Incentives.
- Get insights into the top 50 customer by eligible and ineligible revenue and usage with ability to search and look up for any customer.
- Get insights into customer, subscription, product level revenue, usage metrics.
- Search for revenue capability at customer or subscription level.
- For ineligible revenue/usage, learn why the earnings are ineligible, and download detailed reports of ineligible revenue/usage.

Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home), and select **Earnings** > **Revenue**.

## Definitions of the revenue page elements

- **Incentives Eligible Revenue – As Of**: Latest earning generation date (also known as the **Calc** date found in the export file) in UTC.
- **Incentives Eligible Revenue - Total**: Sum of distinct transaction amounts in USD for all non-usage based engagements that are assessed as part of Modern Commerce Incentives engagements and are eligible for at least one engagement. Modern work usage won't be part of this total, because it's based on usage.
- **Incentives Ineligible Revenue – As Of**: Latest earning generation date (also known as the **Calc** date found in the export file) in UTC.
- **Incentives ineligible Revenue - Total**: Sum of distinct transaction amounts in USD for all non-usage based transactions that are assessed as part of Modern Commerce Incentives engagements and do not have even a single earning against any engagement. Modern work usage will not be part of this total, because it's based on usage.
- **Revenue and usage summary**: This section shows the top 50 earning customers in two views:
  - **Revenue-based earnings**: This view shows the 50 highest revenue-earning customers. Any earning from engagements that are transaction-based or consumption-based are covered here. Examples: Modern work and business applications transactions or Azure consumption. The default sorting is by highest revenue.
  - **Usage-based earnings**: This view shows the 50 highest-usage customers. Any earning from engagements that are usage-based are covered here. Example: Modern work and business applications usage. The default sorting is by highest usage.

    Search for any customer (not just top 50) in the search box, and the results show as available against both views.

    You can download reports from these views.

- **Incentives eligible and ineligible**
  - **Eligible**: Shows all revenue and usage details that became eligible for incentives against one or many engagements. Sorted by Revenue (USD).
  - **Customer name**: End customer name. Available for all.
  - **Customer Id**: End customer ID. Examples: TPID for Azure consumption, Business Applications usage for PAL or Tenant ID for Modern Work, Business Applications transact. Available for all.
  - **Subscription ID**: Subscription Identity. It's not available for Modern Work usage or Business Applications usage for PAL.
  - **Product**: Product name consistently available for revenue-based engagements. Optionally available for usage-based engagements.
  - **Workload**: Workload name consistently available for usage-based engagements. Optionally available for revenue-based engagements.
  - **Quantity**: Shows units sold for transact-based engagements, none for Azure consumption and monthly active usage (MAU) or monthly active capacity (MAC) for Modern Work and Business Applications usage-based engagements.
  - **RevenueUSD**: Total transaction amount, in USD. Available only for non-usage based engagements.
  - **EarningsUSD**: Total earning amount in USD. Available for all.
- **Incentives eligible and ineligible**
  - **Ineligible**: Shows all revenue and usage details that became ineligible for incentives against one or more engagements. Sorted by Revenue (USD).
  - **Customer name**: End customer name. Available for all.
  - **Customer Id**: End customer ID. Examples: Top Parent ID (TPID) for Azure consumption, BizApps usage for PAL, or tenant ID for Modern Work, Business Applications transact. Available for all.
  - **Subscription Id**: Subscription Identity. It's not available for Modern Work usage or Business Applications usage for PAL.
  - **Product**: Product name consistently available for revenue-based engagements. Optionally available for usage-based engagements.
  - **Workload**: Workload name consistently available for usage-based engagements. Optionally available for revenue-based engagements.
  - **Quantity**: Shows units sold for transact based engagements, none for Azure consumption and monthly active usage (MAU) or monthly active capacity (MAC) for Modern Work and Business Applications usage-based engagements.
  - **Revenue USD** – Total transaction amount USD. Available only for non-usage-based engagements.
  - **Reason**:  Reason for ineligibility. See the [list of reasons for ineligibility](#ineligibility-reason-codes).
- **Downloads available via Revenue page - Ineligible revenue usage details**: This report contains all transactions and usage that became ineligible for Microsoft commerce incentives.       |

## Page filters

Time filter: Has **3 months**, **6 months**, **12 months**, **36 months**, and custom date picker options. If you select 3 months, the report returns data for the three past months from today.
There are multiple page filters. All of them support multi-select options.

| Filter attribute            | Description                              | Applicability                                 |
| --------------------------- | ---------------------------------------- |  --------------------------------------------- |
| **Enrollment ID, Location** | Partner ID with which you are enrolled in the program.     | Applies to the whole page          |
| **Program name**            | Incentive, store or marketplace program name                   | Applies to the whole page          |
| **Solution area**   | High level product categorization. Examples: Azure, Modern Work and Security. | Useful only for Microsoft Commerce Incentives. Applies to all except the Payments, Estimated Payments and Payment summary views |
| **Engagement name**         | Name of the incentive engagement under Microsoft commerce incentive program.                  | Useful only for Microsoft Commerce Incentives. Applies to all except the Payments, Estimated Payments and Payment summary views |
| **Lever**                   | Reflects the calculation rule/policy    | Applies to the whole page          |

## Ineligibility reason codes

Reason code (internal)       | Ineligible reason string                 | Can Partner take action? | How to become eligible again?                |
| -------------------------- | ---------------------------------------- | ------------------------ | -------------------------------------------- |
| **CUSPUBSEC**              | Customer is public sector | Yes, if customer is in United States, Puerto Rico, or India | If you responded to a proof of execution (POE) request and it was rejected, you can't become eligible again. (When a POE is rejected, email is sent explaining why.)<br><br>You can request another POE within 90 days of the transaction or earning date. (Be sure to confirm receipt of the POE email when it arrives.) You can also dispute ineligibility within 90 days by contacting support with the ineligibility reason, subscription and customer information, and reason for dispute. |
| **CUSNOTNEW**              | Customer tenant creation outside valid period   | No    |                |
| **IVDADV**              |  Advanced specialization requirement not fulfilled  | Yes   | [Learn about advanced specializations](./specializations.md)              |
| **IVDCOMP**                | Competency status not met or expired                      | Yes  | View your competency status at **Competencies**. View the required competencies for your engagement at **Incentives Engagements**     |
| **IVDCOSELL**              | Co-sell eligibility not established or expired                | Yes | [See Co-sell with Microsoft sales teams and partners overview](co-sell-overview.md)   |
| **IVDMPA**                 | MPA agreement not signed or expired                      | Yes | [Verify and sign MPA agreement by guidance on The Microsoft Partner Agreement for CSP program partners](microsoft-partner-agreement.md)           |
| **IVDMPN**                 | PartnerID not eligible to participate in engagement           | No | Partner can't become eligible again by policy   |
| **IVDGEO**                 | Partner location ineligible for engagement                   | No | Partner can't become eligible again by policy   |
| **IVDCUST**                | Customer already accounted for in past customer adds earnings | No | A customer that has already generated customer adds incentives won't be eligible for future customer adds incentives for any partner   |
| **CUSEQPTR**               | Partner is customer           | No | Sale to self is not eligible for earning        |
| **CHREVNONCH**             | China revenue shouldn't belong to non-China partner           | No | Partner can't become eligible again by policy   |
| **IVDPTRROLE**             | Invalid partner role                | No | Partner association not eligible per policy to earn                       |
| **IVDPOE**                 | Proof of execution isn't approved   | Yes | Proof-of-execution request is applicable only for public sector or DPOR. Effective October 1, 2021, DPOR is no longer incentivized for Azure, so POE requests aren't sent.<br><br>If you responded to email with the subject _Proof of execution required_ and your response was rejected, you can't become eligible again.                           |
| **INVTNXACO**              | Azure credit offer is active for customer                     | No | Incentives aren't provided when customer is using Azure credit offer.     |
| **PAULWPHWM**              | PAU less than or equal to prior HWM                          | No | Paid available units less than or equal to prior high watermark           |
| **MAULWPHWM**              | MAU less than or equal to Prior HWM                          | No | Monthly active usage less than or equal to prior high watermark           |
| **IVDCLD**                 | Invalid cloud                       | No | Invalid cloud         |
| **MINTHNTMT**              | Min threshold for HWM not met       | No | Minimum threshold for high watermark not met    |
| **MXTMCPMT**               | Met max time cap since claim attach date                      | No | Met maximum threshold to earn since claim attach date                  |

## Ineligible revenue usage download

Detailed ineligible records for the chosen filter criteria can be downloaded from the top of the page through **Download > Ineligible revenue usage details**. The file contains the following attributes:

| Attribute name               | Description                      | Availability                                                  |
| ---------------------------- | -------------------------------- | ----------------------------------------------------------------- |
| **agreementNumber**          | Enterprise agreement number   | Only for any Enterprise Agreement-based engagements  |
| **compensableUnits**<br><br>**compensableUnitsAlt**   | Compensable Units are calculated by subtracting the Prior High Water Mark (HWM) at the start of the month by Tenant/workload from the paid seats at the end of the month by Tenant/workload. For example, Compensable units by tenant and workload = Paid seats – Prior HWM. | Applicable for Microsoft Commerce Incentives – Modern Workplace Usage and Online Advisor      |
| **customerId**               | Identity of the customer associated with a subscription/resource.               | All                          |
| **customerIdType**           | Top Parent ID (TPID) or Tenant ID. TPID is available for Azure consumption engagements and some build intent workshops. The rest have tenant IDs.                                 | All                            |
| **customerName**             | Name of customer                | All                            |
| **earningParticipantId** <br><br>**earningParticipantIdType** <br><br>**earningParticipantName** | Partner identity in the transact relationship                   | For all incentive, store and marketplace programs. Useful when multiple transacting partner IDs are mapped into a single enrollment ID |
| **engagementName**           | Name of the incentives engagement under Microsoft Commerce Incentives                   | Only for transactions dated Oct 1, 2021 and later    |
| **invoiceNumber**            | Invoice number                 | Only for modern partner-led, field-led and customer-led for Azure consumption, all new commerce transactions for other products.       |
| **partnerAssociation**       | Type of relationship partner has to a customer Examples: reseller, PAL.Owner                 | For all incentive, store and marketplace programs    |
| **partnerCountryCode**       | Enrolled Microsoft AI Cloud Partner Program location               | All                          |
| **partnerId**                | PartnerID of the enrolled partner                        | All                          |
| **partnerName**              | Name of the partner                        | All                          |
| **partnerRole**              | Categorization of the kind of engagement. Categories include: **build intent**, **transact**, **deploy** and **use**.   | For Microsoft Commerce Incentives only       |
| **productId**                | Commerce product name. Available for commerce-based transactions    | All                          |
| **productFamily**            | Product family               | All                            |
| **reason**                   | Reason for ineligibility                  | All                          |
| **subscriptionId**           | Subscription ID              | Only for commerce transactions (subscription-based) and Azure consumption                    |
| **transactionAmountUSD**     | Consumption amount in US dollars | All                            |
| **transactionDate**          | Date of consumption or billing                        | All                          |
| **unearnedId**               | Unique identifier that can help you to create a support inquiry       | All                          |
| **quantity**                 | Indicates the active usage or seats                          | Only for BizApps usage-based engagements     |
| **quantityType**             | Elaborates the type of quantity—for example, MAU or seats          | Only for BizApps usage-based engagements     |
| **quantityAlt**              | Alternate quantity value            | Optionally available for incentive programs. Example: Modern Work usage.                                       |
| **quantityAltType**          | Alternate quantity unit For example, Paid available units (PAU)          | Optionally available for incentive programs. Example: For Modern Work usage.                |
| **resourceID**               | Indicates the resource  | Applicable for Business Applications with PAL                                                  |
| **solutionArea**             | High level product categorization. Examples: Azure, Modern Work and Security.               | For Microsoft Commerce Incentives only       |
| **workload**                 | Service name or workload name. Applicable for Azure consumption or monthly active usage based data.    | Only for Azure consumption and BizApps usage   |
