---
title: Get earnings export request by ID
description: Gets the status of an existing queued export request.
ms.date: 6/16/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: deeparamani
ms.author: deramani
---

# Get earnings export request by ID

Gets the status of an existing queued export request.

## REST Request

```rest
GET {baseURL}/v{version}/payouts/transactionhistory/{transactionHistoryRequestId}
```

### Request parameters

| Name       | In    | Required | Type    | Description    |
|------------|-------|----------|---------|----------------|
| requestId  | Query | True     | Guid    | Export request ID |

### Request header

| Name                | Required | Type      | Description    |
|---------------------|----------|-----------|----------------|
| Authorization       | Yes      | String    | Authorization Bearer Token. |
| ms-correlationid    | No       | String    | An internal request tracker. Each request generates a new tracker   (GUID).  |
| ms-requestid        | No       | String    | The request idempotency ID. |

### Request body

N/A.

## Response payload

API returns HTTP status 200.

Based on request, API can return other standard status listed in Standard API response statuses:

[!INCLUDE [Standard API response statuses](./includes/standard-api-response-statuses.md)]

The API response payload returns the following attributes:

| Name  | Optional | Description |
|-------|----------|-------------|
| Value | false    | See the following table for possible values and actions. |

**Possible values and actions**

| Value              | Client action|
|--------------------|--------------|
| requestId          | Request ID of the export request.    |
| requestDateTime    | Initiation datetime of the export request. |
| requestPath        | Query path of the export request.    |
| requestQueryString | Filter used as part of the export request.    |
| blobLocation       | Blob resource with token when the export file is ready.   |
| Status             | Export operation status. See the following list of possible values for status. |

**Possible values for status**

- **Queued**: The export operation hasn't started
- **Processing**: The export operation is in progress
- **Failed**: The export operation failed after retries, try queueing a new request
- **Completed**: The export operation completed, and the export file is ready for download.
