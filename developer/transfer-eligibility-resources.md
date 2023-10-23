---
title: TransferEligibility resources
description: A partner can create a transfer when a customer requests their subscription with the partner to be transferred to another partner.
ms.date: 7/31/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: brentserbus
ms.author: brserbus
---

# TransferEligibility resources

A partner can create a transfer when a customer requests their subscription with the partner to be transferred to another partner. Use TransferEligibility to check whether a subscription is eligible to be transferred.

## TransferEligibility

Describes a transferEligibility.

| Property              | Type             | Description                                                                              |
|-----------------------|------------------|------------------------------------------------------------------------------------------|
| id                    | string           | The customer's subscription identifier.                                                  |
| isEligible            | bool             | Indicates whether the subscription is eligible for the transfer.                         |
| Reason                | string           | The reason property explains why the subscription isn't eligible for transfer. |
