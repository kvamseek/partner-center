---
title: Agreement document resources
description: The AgreementDocument resource is a Microsoft agreement document for preview and download. It is supported by Partner Center in the Microsoft public cloud.
ms.date: 06/30/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: JulCsc
ms.author: shishir
---

# Agreement document resources supported by Partner Center in the Microsoft public cloud

**Applies to**: Partner Center

The **AgreementDocument** resource is currently supported by Partner Center only in the Microsoft public cloud.

The **AgreementDocument** resource represents a Microsoft agreement document that is available for preview and download.

## AgreementDocument

An **AgreementDocument** resource includes the following properties:

| Property       | Type   | Description                                                                                               |
|----------------|--------|-----------------------------------------------------------------------------------------------------------|
| country | string | The country/region or market to which this document applies. |
| language | string | The language in which this document is localized. |
| displayUri | string | A link to preview the agreement document in a browser.  |
| downloadUri |string | A link to download the agreement document (in Microsoft Word format). |
| VersionRank | int | Rank for the version of enforcement. |
