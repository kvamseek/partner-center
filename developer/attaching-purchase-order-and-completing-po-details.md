---
title: Attaching a purchase order and completing purchase order details
description: Request for completing purchase order details.
ms.date: 08/23/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: iragulati1
ms.author: iragulati
---

# Attaching a purchase order and completing purchase order details

**Appropriate roles**: Global admin | Admin agent

Partners may be required to provide Customer Purchase Order and/or Tender or Request for Proposal (RFP) information to complete a transaction within Partner Center. This article describes how partners can use Partner Center to programmatically attach purchase orders.  

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with both standalone App and App+User credentials.

### Request syntax

| Method   | Request URI |
|----------|-------------|
| **POST**  | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customerid}/orders/{orderid}/attachment |

### URI body parameter

Use the following body parameters to return purchase order statuses.

| Name  | Type     | Required | Description  |
|-------|----------|----------|--------------|
| **isPartofTender**  | **Boolean** | N | Is the order part of a customer Tender or Request for Proposal (RFP). | 
| **customerPrice** | Decimal/string| Y|
| **currency**      | String| Y|
| **fxRate**        | Decimal/string |N |
| **tenderLink**    |String |Y/N | If isPartOfTender is true and no tender files are provided, then this is required, otherwise not required.
| **POfiles**          |Files | Y|
| **TenderFiles**      |Files | Y/N|If isPartOfTender is true and no tender link is provided, then this is required otherwise it's not required.

### Request headers

For more information, see [Partner Center REST headers](headers.md).

### Request example

```http
POST https://api.partnercenter.microsoft.com/v1/customers/<customerid>/orders/<orderid>/attachment
Authorization: Bearer <Token>
Content-Type: multipart/form-data; boundary=----WebKitFormBoundaryaLQBO4IgpABK3wdj
Accept: application/json

------WebKitFormBoundaryaLQBO4IgpABK3wdj
Content-Disposition: form-data; name="metadata"
{"isPartofTender":true,"customerPrice":"156.87","currency":"CAD","fxRate":"1.2","tenderLink":https://onedrive.com/ishdruiwiojfdhajhgdfgjhgj}
------WebKitFormBoundaryaLQBO4IgpABK3wdj
Content-Disposition: form-data; name="pofiles"; filename="PO_Part1.pdf"
Content-Type: application/pdf
```

## REST response

If the transaction requires a purchase order upload once a partner completes creating an order or checkout, the following response will be received.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and more debugging information. Use a network trace tool to read this code, error type, and more parameters. For the full list, see [Error Codes](error-codes.md).

### Response example

```http
HTTP/1.1 201 Created
Content-Length: 393

{"totalCount":3,"items":[{"attachmentId":"ed64c99f750115","fileName":"PO_Part1.pdf","sizeInKB":2051,"attachmentType":"POAttachment"},{"attachmentId":"ef8fe74c39e264","fileName":"PO_Part2.pdf","sizeInKB":1313,"attachmentType":"POAttachment"},{"attachmentId":"32a312ca64567a","fileName":"Tender.pdf","sizeInKB":2223,"attachmentType":"TenderAttachment"}],"attributes":{"objectType":"Collection"}}

```
