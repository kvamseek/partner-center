---
title: Agreement metadata resources
description: The AgreementMetadata resource collection describes agreement types that partners can use to provide confirmation of customer acceptance.
ms.date: 06/30/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: JulCsc
ms.author: shishir
---

# Agreement metadata resources

**Applies to**: Partner Center

**Does not apply to**: Partner Center operated by 21Vianet |  Partner Center for Microsoft Cloud for US Government

The **AgreementMetaData** resource is currently supported by Partner Center only in the Microsoft public cloud. 

The **AgreementMetaData** collection provides metadata about all the agreement types. Partners can use this collection to provide confirmation of customer acceptance of agreements. The **AgreementMetaData** collection returns metadata for both agreement types (**Microsoft Cloud Agreement** and **Microsoft Customer Agreement**).

## AgreementMetaData

Agreement metadata returned includes the following properties:

| Property      | Type               | Description                                                                       |
|---------------|--------------------|-----------------------------------------------------------------------------------|
| templateId    | string             | Unique identifier of an agreement template.                                       |
| type          | string             | Agreement type. Currently, supported values include **MicrosoftCloudAgreement** and **MicrosoftCustomerAgreement** (preview). |
| agreementLink | string             | URL for the agreement template.
| VersionRank | int | Rank for the version for enforcement. |