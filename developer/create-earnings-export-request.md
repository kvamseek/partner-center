---
title: Create earnings export request
description: Use this API to queue new earnings and underlying transactions/payments data export request with optional filters to slice and dice the earnings and transactions data.
ms.date: 6/16/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: deeparamani
ms.author: deramani
---

# Create earnings export request

Use this API to queue new earnings and underlying transactions/payments data export request with optional filters to slice and dice the earnings and transactions data. It returns a 202 HTTP status and a request ID, which can be used to poll back to check the status of the queued transaction export request.

Submit a POST request to the API endpoint to queue a new export request for transactions/earnings.

## REST request

| Method    | Request URI                                                                                                                |
|-----------|----------------------------------------------------------------------------------------------------------------------------|
| **POST**  | [*{baseURL}*](partner-center-rest-urls.md)/v{version}/payouts/transactionhistory?$filter={$filter}&fileformat=csv1 |

### Request parameters

| Name       | In    | Required | Type    | Description    |
|------------|-------|----------|---------|----------------|
| $filter    | Query |    No    | String  | Even though it's an optional filter, we highly recommend using filters for faster performance and limiting your export data instead of exporting last three years of data. See the following table for a full set of $filter options. |
| fileFormat | Query |    No    | String  | Supported values are .csv/.tsv.  Defaults to .csv if no value is provided. |

The $filter query param is an optional parameter for creating a export operation. However, we highly recommend to use $filters for better performance and faster availability of the export report. The following are some of the key attribute filters that can be used as part of export operation:

| Name                       | Description                                   | Type        | Sample       |
|---|---|---|---|
| `enrollmentParticipantId`    | Enrolled MPN ID of the organization.          | Int         | *{baseUrl}*`/v1.0/payouts/transactionhistory?$filter= enrollmentParticipantId=12345`                                            |
| `EarningForDate`             | Earning period date for the export operation. | DateTime    | *{baseUrl}*`/v1.0/payouts/transactionhistory?$filter=earningForDate ge 2023-03-01 and earningForDate le 2023-04-12`    |
| `transactionAmount`          | Transaction amount.                           | Double      | *{baseUrl}*`/v1.0/payouts/transactionhistory?$filter=?$filter=transactionAmount ge 2000 and transactionAmount le 5000`          |
| `earningAmount`              | Earning amount in transaction currency.       | Double      | *{baseUrl}*`/v1.0/payouts/transactionhistory?$filter=?$filter=earningAmount ge 2000 and earningAmount le 5000`                  |
| `engagementName`             | Applicable for Microsoft Commerce Incentives only. Example values - `'Azure CSP motion incentives - Indirect Provider'`. | String   | *{baseUrl}*`/v1.0/payouts/transactionhistory?$filter=?$filter=engagementName=’Azure CSP motion incentives’`   |
| `payableSubType`             | Filter by the earning type. Example values - `'REBATE'`, `'COOP'`, `'FEE'`, `'SELL'` | String    |     *{baseUrl}*`/v1.0/payouts/transactionhistory?$filter=?$filter=payableSubType=’REBATE’ or payableSubType=’FEE’`    |
| `payoutStatus`               | Filter transactions by the payout status. Example values - `'SENT'`, `'UPCOMING'`, `'IN PROGRESS'`.   |     String    |     *{baseUrl}*`/v1.0/payouts/transactionhistory?$filter=?$filter=payoutStatus=’IN PROGRESS’`    |

Sample transaction history filter with multiple request parameters:

```http
”?$filter=earningForDate ge 2019-01-27T23:16:31.009Z and earningForDate le 2019-09-25T23:16:31.009Z and (enrollmentParticipantId eq 'XXXXXXX') and (programName eq ‘Microsoft Commerce Incentives’) and (payableSubType eq 'REBATE') and (paymentId eq '000000000000') and (engagementName eq 'Azure Enterprise and Self-Service Incentive' or engagementName eq 'Azure CSP motion incentives - Indirect Provider') and (leverCode eq ‘Azure Enterprise and Self-Service Motion’) and (payoutStatus eq 'SENT')”
``` 

### Request header

| Name                | Required | Type      | Description    |
|---------------------|----------|-----------|----------------|
| Authorization       | Yes      | String    | Authorization bearer token. |
| ms-correlationid    | No       | String    | An internal request tracker. Each request generates a new tracker   (GUID).  |
| ms-requestid        | No       | String    | The request idempotency ID. |

To learn more, see [Partner Center REST headers](./headers.md)

### Request body

N/A.

## API response

```rest
HTTP/1.1 202 Accepted
```

The API response payload returns the following attributes:

| Name  | Optional | Description |
|-------|----------|-------------|
| Value | false    | See the following table for possible values and actions. |

**Possible values and actions**

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

### Sample response

```rest
{
    "value": [
        {
            "requestId": "93c2b3cf-c6d8-4e7e-ade1-007768a6eba4",
            "requestDateTime": "2023-05-25T21:20:46.3727561Z",
            "requestPath": "/v1.0/payouts/transactionhistory",
            "requestQueryString": "earningForDate ge 2023-03-01 and earningForDate le 2023-04-12",
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
