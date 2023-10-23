---
title: Gets a list of pending purchase order uploads
description: Gets a list of pending purchase order uploads.
ms.date: 08/23/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: iragulati1
ms.author: iragulati
---

# Get pending purchase order uploads

**Appropriate roles**: Global admin | Admin agent

Partners may be required to provide Customer Purchase Order and/or Tender or Request for Proposal (RFP) information to complete a transaction within Partner Center. This article describes how partners can use Partner Center to programmatically manage purchase orders.  

To test in the Sandbox environment, the purchase of the following offers will trigger the PO Upload flow for their respective orders:
- Access LTSC 2021 (Perpetual Software, Product ID DG7GMGF0D7FV)
- Excel LTSC 2021 (Perpetual Software, Product ID DG7GMGF0D7FT)

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with both standalone App and App+User credentials.

## REST response

If the transaction requires a purchase order upload once a partner completes creating an order or checkout, the following response will be received.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and more debugging information. Use a network trace tool to read this code, error type, and more parameters. For the full list, see [Error Codes](error-codes.md).

### Response example

```http
 {
    "id": "8ae0e679fb36",
    "alternateId": "8ae0e679fb36",
    "referenceCustomerId": "71b277b9-9cc1-4fef-a0df-7355006cb52e",
    "billingCycle": "annual",
    "currencyCode": "USD",
    "currencySymbol": "$",
    "lineItems": [
        {
            …
        }
    ],
    "creationDate": "2022-03-10T18:21:22.5246613Z",
    "status": "pending_po_upload",
    "transactionType": "UserPurchase",
    …
 }
```
