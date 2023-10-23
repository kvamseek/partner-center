---
title: Get purchase order upload complete status.
description: Get purchase order upload complete statuses.
ms.date: 08/23/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: iragulati1
ms.author: iragulati
---

# Get purchase order upload complete status

**Appropriate roles**: Global admin | Admin agent

Partners may be required to provide Customer Purchase Order and/or Tender or Request for Proposal (RFP) information to complete a transaction within Partner Center. This article describes how partners can use Partner Center to programmatically get purchase orders statuses.  

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with both standalone App and App+User credentials.

## REST response

Once a Partner has uploaded the Customer Purchase order and/or Tender document, Get Order details can be called to see the status change to `po_upload_complete`.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and more debugging information. Use a network trace tool to read this code, error type, and more parameters. For the full list, see [Error Codes](error-codes.md).

### Response example

```http
"id": "54be297b70ad",
    "alternateId": "54be297b70ad",
    "referenceCustomerId": "71b277b9-9cc1-4fef-a0df-7355006cb52e",
    "billingCycle": "annual",
    "currencyCode": "USD",
    "currencySymbol": "$",
    "lineItems": [
        {
            …
        }
    ],
    "creationDate": "2022-03-08T17:38:57.5217119Z",
    "status": "po_upload_complete",
    "transactionType": "UserPurchase",
    "links": {
        "self": {
            "uri": "/customers/71b277b9-9cc1-4fef-a0df-7355006cb52e/orders/54be297b70ad",
            "method": "GET",
            "headers": []
        },
        "provisioningStatus": {
            "uri": "/customers/71b277b9-9cc1-4fef-a0df-7355006cb52e/orders/54be297b70ad/provisioningstatus",
            "method": "GET",
            "headers": []
        },
        "patchOperation": {
            "uri": "/customers/71b277b9-9cc1-4fef-a0df-7355006cb52e/orders/54be297b70ad",
            "method": "PATCH",
            "headers": []
        }
    },
    "client": {},
    "attributes": {
        "objectType": "Order"
    }
}

```
