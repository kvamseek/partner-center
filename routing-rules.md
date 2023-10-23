---
title: Create and manage inbound opportunities routing rules
ms.topic: article
ms.date: 08/24/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-referrals
description: Your company can create rules to decide how an incoming co-sell opportunity from Microsoft sellers is routed.
author: vikramb
ms.author: vikramb
---

# Create and manage inbound opportunities routing rules

**Appropriate roles**:  Referrals admin | Referrals user

> [!NOTE]
> The routing rules page has moved to the Referrals workspace from the Account settings page.

> [!IMPORTANT]
> **Creating routing rules is optional**. It is only recommended for bigger companies with presence across the world or if your company has a complex Microsoft AI Cloud Partner Program (formerly MPN) hierarchy where referral management is to be done at a specific location level based on the customer markets and solutions.

## Introduction

The functionality described in this document will help your company to configure rules, which can help route the Co-sell opportunities sent by Microsoft sellers to the Microsoft AI Cloud Partner Program (formerly MPN) locations of your choice. By default, the referrals from Microsoft seller will be sent to the Microsoft AI Cloud Partner Program (formerly MPN) location associated with the Co-sell solution included in the opportunity. The routing rules if created will help your company override the default routing. Only a **[referral admin](permissions-overview.md#manage-referrals)** with the entire organization scope can create and edit routing rules. Partners with **[referral user](permissions-overview.md#manage-referrals)** role can only view the routing rules to understand how referrals are getting routed within their company.

The rules will not be applied retrospectively. Any referrals created in the past or with an older configuration of the routing rule will not be updated. Any changes made to the rules are applicable instantaneously.

There are three main pivots for any rule.

- **Customer market** - The market where the customer company is located

- **Solution** - solutions published by your company either through the OCP GTM portal or commercial marketplace

- **Microsoft AI Cloud Partner Program (formerly MPN)** **location** - the Microsoft AI Cloud Partner Program (formerly MPN) location to which the referral is to be routed

Each rule can be read like - **For the referrals sent by Microsoft sellers with the solutions from my company, route them to this** **Microsoft AI Cloud Partner Program (formerly MPN)** **location**

> [!NOTE]
> Inbound routing rules are applicable only for Co-sell opportunities sent by Microsoft sellers to your company.

## Navigation

You can create routing rules in the **Referrals** tab under **Account settings** page. To go to the page, select the settings icon next to the user icon on the top-right corner and then select the **Referrals** tab in the left navigation panel.

## Initial setup

**Configuring routing rules is not mandatory**. If your company decides to use the routing rules to take advantage of the routing logic, you can start by importing the default rules that the referral management system uses to route the referrals.

The current logic uses the PartnerID (formerly MPN ID) associated with the solution to route all the inbound referrals from Microsoft sellers irrespective of the customer country/region. They are available for your reference and **can be imported with one click** as routing rules. Once the import action is completed, the rules will be applied for all the new referrals sent by Microsoft sellers. Your company can edit or delete existing rules and create new rules if necessary. Only **[referral admin](permissions-overview.md#manage-referrals)** with the global scope can import the rules. The same permission is required for any subsequent changes to the routing rules.

> [!IMPORTANT]
> **There are changes to the email notification logic**. As soon as the rules have been imported, the emails that were earlier sent to **solution contacts** uploaded in the Co-sell tab in the commercial marketplace will no longer be sent. **Only [referral admins](permissions-overview.md#manage-referrals)** of the Microsoft AI Cloud Partner Program (formerly MPN) location to which the co-sell opportunity is sent will be notified.

## Override rules

You can override two types of rules and override a specific condition of the default rule. In the default rule, you can only change the Microsoft AI Cloud Partner Program (formerly MPN) location to which the referrals are to be routed. The other two rule types that you can override are those with **All markets** and **All solutions** as conditions in the rules.

**All markets override** - Assuming you created a rule that says, for all the customer markets and a given solution A, route the referrals to Microsoft AI Cloud Partner Program (formerly MPN) location M1. You can override such rule with a specific market and the same solution combination. Example override can be "for the referrals containing customers from the market United Kingdom and solution A, route it to Microsoft AI Cloud Partner Program location M2.

**All solutions override** - Assuming you created a rule that says, for all the solutions and a given market MKT1, route the referrals to Microsoft AI Cloud Partner Program (formerly MPN) location M1. You can override such rule with a specific solution and the same market combination. Example override can be "for the referrals containing customers from the market MKT1 and solution B, route it to Microsoft AI Cloud Partner Program location M2.

Below table shows the summary of types of solutions that you can override

| **Type** | **Can you override ?** |
|-------|-------|
|Default| No |
|All markets| Yes|
|All solutions| Yes|
|A specific solutions and specific markets combination| No|

> [!NOTE]
> You can change the Microsoft AI Cloud Partner Program (formerly MPN) location for the default rule even though you cannot change anything else in that rule.

## Rules evaluation

If your company has multiple rules that can be applied for a scenario, below the evaluation criteria used.

- The first check will be for a rule with the specific solution and market combination, which are in the inbound opportunity. A direct match to any such rule will take precedence over all other rules.
- If the first check fails, then we check if there are any rules that contain the solution mentioned in the referral with market condition set as all markets.
- If the second check fails, then we check if there are any rules where all solutions are mentioned as solution criteria for a specific market.
- If the third check also fails, then we use the Default rule.

> [!NOTE]
> You cannot create a rule which conflicts with other rules at a specific location and solution level. The UI will throw an error with the name of the rule which is conflicting with your configuration if you are try to create a conflicting rule.

## Example

Inbound routing rules will be explained with the help of routing rules created for Contoso Corporation. Before understanding how the rules will be applied, let us understand the Microsoft AI Cloud Partner Program (formerly MPN) hierarchy and the user set-up at Contoso Corporation.

### Microsoft AI Cloud Partner Program (formerly MPN) hierarchy of Contoso Corporation

| PartnerID (formerly **PartnerID)**| **Type** | **Address** |
|-------|-------|-------|
|999999| Global| One Contoso way, **Redmond, United States of America**|
|555555| Location| One Contoso way, **London, United Kingdom**|
|666666| Location| One Contoso way, **Singapore, Singapore**|
|777777| Location| One Contoso way, **Bengaluru, India**|

### Sellers from Contoso Corporation

Below are the sellers with their respective referral roles and scope at Contoso Corporation.

| **Name** | **Role** | **Scope** |
|-------|-------|-------|
|Seller One|Referral admin|Entire Organization|
|Seller Two|Referral admin|Bengaluru|
|Seller Three|Referral user|London|
|Seller Four|Referral user|Singapore|

### Inbound routing rules for Contoso Corporation

Assume the following set of rules were created by Seller One for Contoso Corporation. Only **Seller One** can create these rules because [referral admin](permissions-overview.md#manage-referrals) at entire organization scope is required for creating and editing rules.

| **Markets** | **Solutions** | Microsoft AI Cloud Partner Program (formerly MPN) **location** | **Routing rule name** |
|-------|-------|-------|-------|
|All markets|All solutions|Redmond|Default|
|United Kingdom|All solutions|London|UK all solutions|
|All markets|Sol-ABC|Singapore|Sol-ABC all markets|
|India|Sol-PQR|Bengaluru|India-Sol-PQR|

### Summary of routing for various scenarios based on the rules for Contoso Corporation

| **No** | **Scenario** | **Customer Market** | **Solutions included** |**Routing rule applied** |**PartnerID (formerly MPN ID)** **assignment** |**Referrals access** |
|-----|----------|-------|-------|-------|-------|-----------|
| 1|No specific solution and market rule match|United Kingdom|SOL-PQR|Global|999999| Seller One, Seller Two, Seller Three (if added to the team), Seller Four(if added to the team)|
| 2|All solutions and a specific market rule match|United Kingdom|SOL-PQR|UK all solutions|555555| Seller One, Seller Three (if added to the team) |
| 3|Specific solution and all markets rule match|Nigeria|SOL-ABC|SOL-ABC all markets|666666| Seller One, Seller Four(if added to the team) |
| 4|Specific solution and market rule match|India|SOL-PQR|India-Sol-PQR|777777| Seller One, Seller Two|
| 5|Inbound referral with a solution not owned by your company|United States of America|SOL-XYZ|Global|999999| Seller One, Seller Two, Seller Three (if added to the team), Seller Four(if added to the team)|

## Next steps

- [Manage Co-sell Opportunities](manage-co-sell-opportunities.md)

- [Get the co-sell connector for Dynamics 365 CRM](connector-dynamics.md)

- [Get the co-sell connector for Salesforce CRM](connector-salesforce.md)

