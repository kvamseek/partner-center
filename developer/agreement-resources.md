---
title: Agreement resources
description: The Agreement resource represents a Microsoft cloud customer agreement with details of certification provided by the partner.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
ms.author: kiranban
author: kbangalore
---

# Agreement resources representing a Microsoft cloud customer agreement

**Applies to**: Partner Center

**Does not apply to**: Partner Center operated by 21Vianet |  Partner Center for Microsoft Cloud for US Government

The **Agreement** resource is currently supported by Partner Center only in the Microsoft public cloud.

The **Agreement** resource represents a Microsoft cloud customer agreement.

## Agreement

The **Agreement** resource represents the details of certification provided by the partner.

| Property       | Type   | Description                                                                                               |
|----------------|--------|-----------------------------------------------------------------------------------------------------------|
| userId         | string                         | Object identifier of the logged-in user in the partner tenant who is providing confirmation on behalf of the partner organization. When using App+User authentication to create an Agreement resource, Partner Center automatically derives the **userId** attribute value from the App+User token.                                                                             |
| primaryContact | [Contact](./utility-resources.md#contact) | Information about the user from the customer organization that accepted the agreement, including:  **firstName**, **lastName**, **email**, and **phoneNumber** (optional). |
| dateAgreed     | string in UTC date time format | The date when the customer accepted the agreement.                                 |
| templateId     |string                          | Unique identifier of the agreement that the customer accepted. |
| type           |string                          | Agreement type. Currently, supported values include **MicrosoftCloudAgreement** and **MicrosoftCustomerAgreement**.|
| agreementLink  | string                         | URL for the agreement template.                                                    |
