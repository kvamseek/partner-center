---
title: Resource usage record resources
description: You can use the ResourceUsageRecord resource to describe the estimated monetary cost of a subscription's resource level usage in the current billing cycle.
ms.date: 6/29/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: sourishdeb
ms.author: sodeb
---

# Resource usage record resources

You can use the **ResourceUsageRecord** resource to describe the estimated monetary cost of a subscription's resource level usage in the current billing cycle.

## ResourceUsageRecord

| Property          | Type               | Description                                                                                                                                                                                                |
|-------------------|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SubscriptionId    | string             | Gets or sets the subscription identifier. For Microsoft Azure (MS-AZR-0145P) subscriptions, this value is the commerce subscription identifier. For Azure plans, this value is the Azure plan identifier). |
| ResourceUri       | string             | Gets or sets the resource URI."                                                                                                                                                                            |
| ResourceType      | string             | Gets or sets the resource type.                                                                                                                                                                            |
| EntitlementId     | string             | Gets or sets the entitlement identifier (the Azure subscription identifier).                                                                                                                               |
| EntitlementName   | string             | Gets or sets the entitlement name.                                                                                                                                                                         |
| ResourceGroupName | double             | Gets or sets the resource group name.                                                                                                                                                                      |
| Name              | string             | The name of the resource.                                                                                                                                                                                  |
| ResourceName      | string             | Gets or sets the name of the resource.                                                                                                                                                                     |
| TotalCost         | decimal            | Gets or sets the estimated total cost usage.                                                                                                                                                               |
| CurrencyCode      | string             | Gets or sets the currency code.                                                                                                                                                                            |
| USDTotalCost      | decimal            | Gets or sets the estimated total cost in USD.                                                                                                                                                              |
| LastModifiedDate  | string             | The day (in date-time format) that this record was last modified.                                                                                                                                          |
| Attributes        | ResourceAttributes | The metadata attributes corresponding to the resource.                                                                                                                                                     |
