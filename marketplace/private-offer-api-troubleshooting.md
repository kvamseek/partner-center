---
title: Private offers submission API troubleshooting and resources in Microsoft Partner Center
description: This article provides troubleshooting tips and resources for using the Partner Center API.
ms.subservice: partnercenter-marketplace-publisher
ms.service: marketplace
ms.topic: article
author: migolova 
ms.author: migolova 
ms.date: 07/18/2023
---

# Private offers submission API troubleshooting and resources

This article provides a sample text, which helps parse response text from the Private offers API in Partner Center.

## How to parse error messages in the response body

**Public API Response Error schema**

```
Core Library Class Name: Microsoft.ProductIngestion.Models.ResponseError 
```

In case of failure (for example: notFound, schema validation error,...) we return a response of this schema: 

```JSON
"$schema": "https://json-schema.org/draft/2020-12/schema",
"$id": "https://product-ingestion.azureedge.net/schema/response-error/2022-03-01", "$comment": "In case of any failure. For example not found of in invalid schema", 
"type": "object",
"properties": {
    "error": { "$ref": "https://product-ingestion.azureedge.net/schema/error/2022-03-01"},
"required": ["error"],
"additionalProperties": false
```

## Schemas

Private offer: [https://schema.mp.microsoft.com/schema/private-offer/2023-07-15](https://schema.mp.microsoft.com/schema/private-offer/2023-07-15)

Multiparty private offer for ISV originator: [https://schema.mp.microsoft.com/schema/private-offer-mpo-originator/2023-07-15](https://schema.mp.microsoft.com/schema/private-offer-mpo-originator/2023-07-15)

Multiparty private offer for selling partner: [https://schema.mp.microsoft.com/schema/private-offer-mpo-channel-partner/2023-07-15](https://schema.mp.microsoft.com/schema/private-offer-mpo-channel-partner/2023-07-15)

## Next steps

- [Manage existing private offer API](manage-existing-private-offers-via-api.md)
- [Job status and retrieve private offer detail API](job-status-and-retrieve-private-offer-detail-api.md)
