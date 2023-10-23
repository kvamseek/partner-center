---
title: Billing - license-based SaaS transactions
ms.topic: article
ms.date: 11/8/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-billing
description: Learn about common billing scenarios in Partner Center for license-based, software-as-a-service (SaaS) transactions.
author: sodeb
ms.author: sodeb
---

# Common billing scenarios for license-based SaaS transactions in Partner Center

**Appropriate roles**: Admin agent | Billing admin | Helpdesk agent | Sales agent

These example [common billing scenarios](common-billing-scenarios.md) are applicable to license-based software as a service (SaaS) subscriptions in Partner Center.

## Convert a free trial SaaS subscription to a paid subscription

This scenario describes billing for the renewal of a license-based free trial SaaS subscription. The renewal converts the free trial to a paid subscription at the end of the free trial period.

In this example, you purchased a free trial of a license-based SaaS (software as a service) subscription on June 10. This free trial automatically renewed as a paid subscription when the free trial period ends.

The recon files will include the following charges:

| Purchase date | Charge start date | Charge end date | Unit price | Unit quantity | Total amount | Charge type | Subscription description |
| ------------- | ----------------- | --------------- | ---------- | ------------- | ------------ | ----------- | ----------------- |
| 06/10/2019 | 06/10/2019 | 07/09/2019 | $0 | 1 | $0 | New | Free trial |
| 07/10/2019 | 07/10/2019 | 08/09/2019 | $2 | 1 | $2 | Renew | Paid subscription |

## Cancel a free trial SaaS subscription

> [!TIP]
> You can cancel a license-based free trial SaaS subscription any time, even during the free trial period.

In this scenario, you purchased a license-based free trial SaaS subscription on July 1, and then canceled it immediately in Partner Center.

The recon file will include the following charges:

| Purchase date | Charge start date | Charge end date | Unit price | Unit quantity | Total amount | Charge type | Subscription description |
| ------------- | ----------------- | --------------- | ---------- | ------------- | ------------ | ----------- | ----------------- |
| 06/10/2019 | 06/10/2019 | 07/09/2019 | $0 | 11 | $0 | New | Free trial |
| 06/10/2019 | 06/10/2019 | 07/09/2019 | $0 | 11 | $0 | Cancel | Free trial |

## Convert custom meter SaaS subscription to another SKU

This scenario describes how to convert a custom meter SaaS subscription from one stock keeping unit (SKU) to another SKU for the same product, on the same date.

In this scenario, you purchased one SKU (Silver) under a product and converted it to another available SKU (Bronze) under this product on the same date.

The recon file will include the following charges:

| Purchase date | SKU | Charge start date | Charge end date | Unit price | Unit quantity | Total amount | Charge type | Subscription description |
| ------------- | ----------------- | ----------------- | --------------- | ---------- | ------------- | ------------ | ----------- | ----------------- |
| 06/10/2019 | Silver | 06/10/2019 | 06/10/2019 | $20 | 1 | $20 | New | Custom meter SaaS subscription |
| 06/10/2019 | Silver | 06/10/2019 | 06/10/2019 | $20 | 1 | -$20 | Convert | Prorated rebill for custom meter SaaS subscription |
| 06/10/2019 | Bronze | 06/10/2019 | 06/10/2019 | $10 | 1 | $10 | Convert | Custom meter SaaS subscription |

## Purchase and cancel a customer meter SaaS subscription on same date

This scenario describes billing for a customer meter SaaS subscription that you purchased and canceled through the Azure portal on the same date.

In this scenario, you purchased a custom meter SaaS subscription on the Azure portal. Then, you canceled the subscription on the same date.

| Purchase date | SKU | Charge start date | Charge end date | Unit price | Unit quantity | Total amount | Charge type | Subscription description |
| ------------- | ------------- |----------------- | --------------- | ---------- | ------------- | ------------ | ----------- | ----------------- |
| 06/10/2019 | Bronze | 06/10/2019 | 06/10/2019 | $10 | 1 | $10 | New | Custom meter SaaS subscription |
| 06/10/2019 | Bronze | 06/10/2019 | 06/10/2019 | $10 | 1 | -$10 | CancelImmediate | Custom meter SaaS subscription |
