---
ms.topic: include
author: JulCsc
ms.author: Satinder.Bajaj
ms.reviewer: Satinder.Bajaj
ms.date: 05/16/2023
---
## Request contract change for Update Customer Qualifications API

*The Update Customer Qualifications API has recently been updated to adopt a new request contract that allows greater flexibility when working with Customer Qualifications. This new contract will be mandatory and enforced starting **May 17th, 2023**.*


- **Date**: May 16, 2023
- **Workspace**: APIs
- **Impacted audience**: CSP direct-bill and indirect providers in the Cloud Solution Provider (CSP) program

The updated request contract has three new fields: `EducationSegment`, `Website`, and `ValidationCode`. Partners can start the migration to the new contract immediately.

Partners who only consume the [Partner Center SDK v3.2.0](../../../developer/dotnet-release-notes.md#version-320) and above aren't affected by this change.

The API will continue to accept the old contract until **May 17th, 2023**.

More details on the API contract can be found at [Update a customer's qualifications](../../../developer/update-customer-qualification-asynchronous.md).

### Next steps

[Review the information](../../../developer/update-customer-qualification-asynchronous.md) on this article and share with the appropriate stakeholders in your organization.

