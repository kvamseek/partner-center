---
title: Manage earnings
description: This section describes the ways that partners enrolled in incentives and ISVs partners active in Azure Marketplace and store programs, can use Partner Center to programmatically consume and reconcile their earnings, underlying details, and payments.
ms.date: 6/14/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: deeparamani
ms.author: deramani
---

# Manage earnings

**Applies to**: Partner Center

This section describes the ways that partners enrolled in incentives and ISVs partners active in Azure Marketplace and store programs, can use Partner Center to programmatically consume and reconcile their earnings, underlying details, and payments. You can download the transactions, earnings, payments data asynchronously using the following API endpoints.

## Earnings
 - [Create earnings export request](create-earnings-export-request.md)
 - [Get earning export request by ID](get-earnings-export-request-by-id.md)
 - [Delete earnings export request by ID](delete-earnings-export-request-by-id.md)

## Payments
- [Create payment export request](create-payments-export-request.md)
- [Get payment export request by ID](get-payment-export-request-by-id.md)
- [Delete payment export request by ID](./delete-payment-export-request-by-id.md)

The following diagram shows the steps needed to download data:
:::image type="content" source="./media/manage-earnings/manage-earnings-workflow.png" alt-text="Diagram shows the API workflow." lightbox="./media/manage-earnings/manage-earnings-workflow.png":::

More resources: [Valet Key pattern - Azure Architecture Center | Microsoft Learn](/azure/architecture/patterns/valet-key)

For more information, see [Scenarios](scenarios.md).
