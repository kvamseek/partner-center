---
title: Create payments export request
description: Use this API to create payments export request
ms.date: 6/16/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: deeparamani
ms.author: deramani
---

# Create payments export request

Submit a POST request to the API endpoint to queue a new export request for payments.

## REST request

| Method    | Request URI                                                                                                                |
|-----------|----------------------------------------------------------------------------------------------------------------------------|
| **POST**  | [*{baseURL}*](partner-center-rest-urls.md)/v{version}/payouts/payments?$filter={$filter}&fileformat=csv|


### Request parameters
| Name       | In    | Required | Type    | Description    |
|------------|-------|----------|---------|----------------|
| $filter    | Query |    No    | String  | Even though it's an optional filter, we highly recommend using filters for faster performance and limiting your export data instead of exporting last three years of data. See the following table for a full set of $filter options. |
| fileFormat | Query |    No    | String  | Supported values are .csv/.tsv.  Defaults to .csv if no value is provided. |

| Name | Description | Type | Format |
|-|-|-|-|
| programName |Filter by one or more programs you're enrolled in. Example values - 'CSP Indirect Provider', 'CSP 2T Indirect Provider', 'CSP Direct Bill Partner', 'CSP 1T Direct Partner', 'CSP Indirect Reseller', 'CSP 2T Indirect Reseller' | String | *{baseUrl}*`/v1.0/payouts/payments?$filter=?$filter=programName=’CSP Indirect Provider’` |

Sample payments filter with multiple request parameters

```rest
“?$filter=payoutStatusUpdateTS le 2019-09-25T23:11:55.647Z and (enrollmentParticipantId eq 'XXXXXXX') and (programName eq 'CSP Direct Bill Partner') and (payoutOrderType eq 'REBATE') and (paymentId eq '000000000000')”
```

### Request header

| Name                | Required | Type      | Description    |
|---------------------|----------|-----------|----------------|
| Authorization       | Yes      | String    | Authorization Bearer Token. |
| ms-correlationid    | No       | String    | An internal request tracker. Each request generates a new tracker   (GUID).  |
| ms-requestid        | No       | String    | The request idempotency ID. |

To learn more, see [Partner Center REST headers](./headers.md).

### Request body

N/A

## API response

```rest
HTTP/1.1 202 Accepted
```


The API response payload returns the following attributes:

| Name  | Optional | Description |
|-------|----------|-------------|
| Value | false    | See the following table for possible values and actions. |

| Value              | Client action|
|--------------------|--------------|
| requestId          | Request ID of the export request     |
| requestDateTime    | Initiation datetime of the export request |
| requestPath        | Query path of the export request.    |
| requestQueryString | Filter used as part of the export request.    |
| blobLocation       | Blob resource with token when the export file is ready    |
| Status             | Export operation status. See the following list of possible values for status. |

**Possible values for status**

- **Queued**: The export operation hasn't started
- **Processing**: The export operation is in progress
- **Failed**: The export operation failed after retries, try queueing a new request
- **Completed**: The export operation completed, and the export file is ready for download.

### Sample response:

```http
{
    "value": [
        {
            "requestId": "93c2b3cf-c6d8-4e7e-ade1-007768a6eba4",
            "requestDateTime": "2023-05-25T21:20:46.3727561Z",
            "requestPath": "/v1.0/payouts/payments",
            "requestQueryString": "paymentDate ge 2023-03-01 and paymentDate le 2023-04-12",
            "blobLocation": "",
            "status": "Queued"
        }
    ],
    "nextLink": null,
    "totalCount": 1
}
```

API returns HTTP status 202.

| Name         | Description       |
|--------------|-------------------|
| 202 Accepted | The request has been accepted. Query the GET request URL for the request status. |

Depending on the request, the API can return other standard statuses:

[!INCLUDE [Standard API response statuses](./includes/standard-api-response-statuses.md)]
