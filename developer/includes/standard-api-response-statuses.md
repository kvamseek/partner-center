---
title: include file
ms.topic: include
title: Standard API response statuses, as used by the Manage Earnings API
ms.date: 6/16/2023
ms.service: partner-dashboard
ms.subservice:  partnercenter-api
author: deeparamani
ms.author: deepapriya.ramani
---

| Name                      |Description|
|---------------------------|-----------|
| 400 Bad Request           | There was missing or incorrect data.  |
| 401 Unauthorized          | The caller isn't authenticated and must authenticate with the partner API service before making the first call. |
| 403 Forbidden             | The caller isn't authorized to make the request. |
| 500 Internal Server Error | The API or one of its dependencies is unable to fulfill the request. Try again later. |
| 404 Not Found             | Resource not available with input parameters. |
| 429 Rate limiting         | Too many requests of the same type. Try after sometime. |
