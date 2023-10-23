---
title: include file
description: New subscription date time attributes available via partner center APIs May 10, 2023.
ms.topic: include
ms.service: partner-dashboard
ms.subservice: partnercenter-announcements
author: Brentserbus
ms.author: brserbus
ms.reviewer: brserbus
ms.date: 04/10/2023
---

## New date time attributes available for CSP new commerce subscriptions

*From May 10, CSP partners who use the partner center APIs will have more specific information about when subscriptions end.*

- **Date**: April 10, 2023
- **Workspace**: Customers
- **Impacted audience**: Cloud Solution Provider (CSP) partners who use the partner center APIs

The Partner Center team is adding two new properties to the subscriptions resource available via the Partner Center APIs. These new properties are intended to provide partners with more accuracy and details for a subscription's exact UTC end times for billingCycles and terms. 

Example of subscription current properties:

```current
"commitmentEndDate": "2023-03-13T00:00:00Z",
"billingCycleEndDate": "2023-03-13T00:00:00Z"
```

The above property values are always zeros, intended to mean for the entire day. In reality, the end **times** for these two properties are the end of the data. To provide more clarity, we're adding two new **time** inclusive values to the subscription API result, commitmentEndDateTime and billingCycleEndDateTime.

Example of subscription properties after May 10, 2023:

```new
"commitmentEndDate": "2023-03-13T00:00:00Z",
"billingCycleEndDate": "2023-03-13T00:00:00Z"
"commitmentEndDateTime": "2023-03-13T23:59:59Z",
"billingCycleEndDateTime": "2023-03-13T23:59:59" 
```

The **DateTime** new properties are new and additive, partners don't need to consume them. These attributes are being added to give partners more granular details to determine the end time of term and billing cycles.

#### Next steps

- Review the [subscription API how to topic](/partner-center/developer/get-a-subscription-by-id).
- Review the [subscription resource topic](/partner-center/developer/subscription-resources).

#### Questions?

Contact [Support](https://partner.microsoft.com/dashboard/v2/support/servicerequests) if you have questions or need more information.
