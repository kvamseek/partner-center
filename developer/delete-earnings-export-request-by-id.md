---
title: Delete earnings export request by ID
description: Use this API to delete earnings export request by ID
ms.date: 6/14/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: deeparamani
ms.author: deramani
---

# Delete earnings export request by ID

This article explains how to delete a earnings export request.

## API request

```rest
DELETE {baseURL}/v{version}/payouts/transactionhistory/{transactionHistoryRequestId}
```

## API response body

API returns HTTP status 200.

| Name         | Description       |
|--------------|-------------------|
| 200 Accepted | The request has been deleted successfully. |

Request can't be deleted. – If the export request is in “Processing” state.

Depending on the request, the API can return other standard statuses:

[!INCLUDE [Standard API response statuses](./includes/standard-api-response-statuses.md)]
