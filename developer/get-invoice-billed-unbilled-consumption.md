---
title: Invoicing and reconciliation API v2 (beta)
description: Invoicing and reconciliation API v2 beta for accessing billing and reconciliation data.
ms.date: 10/18/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: sourishdeb
ms.author: sodeb
---

# Invoicing and reconciliation v2 API (beta)

**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud for US Government

You can use these APIs to retrieve billed and unbilled daily rated usage data asynchronously.

> [!NOTE]
> Daily-rated usage normally takes 24 hours to appear in Partner Center or to be accessed through the API.

The asynchronous API is a novel method for quickly accessing billing and reconciliation data in manageable chunks. It eliminates the need to maintain an open connection for hours and loop through millions of transactions iteratively.

We’ve used [valet key](/azure/architecture/patterns/valet-key) and [asynchronous request-reply](/azure/architecture/patterns/async-request-reply) patterns to optimize our invoicing and reconciliation APIs to deliver the results asynchronously. API responses will provide a token to access the reconciliation data with all the attributes or a subset.

> [!NOTE]
>
> - This functionality is in beta and may be changed in future releases.
> - New APIs are not hosted under Partner Center API host.  APIs are available under host `https://ep-billingreconservice-prod-d5bfczcnfvbqbdhx.z01.azurefd.net`. Refer to examples below for full URL.

## API overview

You can download the usage data asynchronously using three new steps (API endpoints). To learn more, read the following:

### Usage line-item endpoint

Use this API to access billed or unbilled consumption line items. It will return a 202 HTTP status and a location header with the URL, which you must poll at regular intervals until you receive a success status with a manifest URL.

### Operation status endpoint

Until you receive the success status, keep polling this API at a regular interval. If the requested data is unavailable, the API response will include a *Retry-After* header indicating how long you should wait before sending another request.

### Manifest endpoint

This endpoint provides a storage folder from which actual billing data can be downloaded. The response splits or partitions the files to optimize throughput and I/O parallelism.

## Sequence diagram

The diagram below depicts the steps needed to download reconciliation data.

:::image type="content" source="./media/billing/diagram-1.png" alt-text="Diagram that shows the steps needed to download reconciliation data.":::

## User action sequence

Follow the steps below to retrieve reconciliation data.

## Step 1: Submit request

Submit a POST request to the API endpoint.

### Get unbilled usage line items

Get unbilled usage line items for the current or last calendar month.

### API request

`POST https://ep-billingreconservice-prod-d5bfczcnfvbqbdhx.z01.azurefd.net/v1/unbilledusage?fragment={fragment}&period={period}?currencyCode={currencyCode}`

### Request parameters

| **Name**     | **In** | **Required** | **Type** | **Description**                                                                                                                                                             |
|--------------|--------|--------------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| fragment     | Query  | False        | String   | Choose "full" for a complete response or "basic" for a subset of attributes. The default value is “full.” (List of attributes is available [here](#usage-data-attributes). |
| period       | Query  | True         | String   | Use “current” or “last” to get usage for the current or last calendar month. The value “last” is the same as “previous” in existing V1 APIs.                                |
| currencyCode | Query  | True         | String   | Partner billing currency code.                                                                                                                                              |

### Deprecated request parameters

The newer API version doesn't require the following URI parameters:

| **Name**               | **Description**                                                                                |
|------------------------|------------------------------------------------------------------------------------------------|
| Provider               | N/A. (It returns all Azure plan usage and is equivalent to the “onetime” of existing V1 APIs.) |
| hasPartnerEarnedCredit | N/A. (returns all data, regardless of PEC.)                                                    |
| Size                   | N/A.                                                                                           |
| Offset                 | N/A.                                                                                           |
| seekOperation          | N/A.                                                                                           |

### Request header

Request headers for the API are listed [here](#standard-api-request-headers).

### Request body

N/A.

### API response

`HTTP/1.1 202 Accepted  
Operation-Location: https://ep-billingreconservice-prod-d5bfczcnfvbqbdhx.z01.azurefd.net/v1/billingoperations/811bb8f0-8aca-4807-897c-c15ce50820d6`

API returns HTTP status 202. Based on request, API can return other standard status listed [here](#standard-api-response-statuses).

| **Name**     | **Description**                                                                                |
|--------------|------------------------------------------------------------------------------------------------|
| 202 Accepted | The request has been accepted. Query the operation-location header URL for the request status. |

### Get billed usage line items

Get billed rated usage line items for the closed billing period.

### API request

`POST https://ep-billingreconservice-prod-d5bfczcnfvbqbdhx.z01.azurefd.net/v1/billedusage/invoices/{invoiceId}?fragment={fragment}`

### Request parameters

| **Name**  | **In** | **Required** | **Type** | **Description**                                                                                                                                            |
|-----------|--------|--------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| invoiceId | Path   | True         | String   | The Partner Center invoice number.                                                                                                                         |
| Fragment  | Query  | False        | String   | Choose "full" for a complete response or "basic" for a subset of attributes. The default value is “full.” (The list of attributes is [available here](#usage-data-attributes)). |

### Deprecated request parameters
  
The newer API version doesn't require the following URI parameters:

| **Name**               | **Description**                                                                                |
|------------------------|------------------------------------------------------------------------------------------------|
| Provider               | N/A. (It returns all Azure plan usage and is equivalent to the “onetime” of existing V1 APIs.) |
| hasPartnerEarnedCredit | N/A. (returns all data, regardless of PEC.)                                                    |
| Size                   | N/A.                                                                                           |
| Offset                 | N/A.                                                                                           |
| seekOperation          | N/A.                                                                                           |

### Request header

Request headers for the API are [listed here](#standard-api-request-headers).

### Request body

N/A.

### API response

`HTTP/1.1 202 Accepted  
Operation-Location:  https://ep-billingreconservice-prod-d5bfczcnfvbqbdhx.z01.azurefd.net/v1/billingoperations/06d01983-07bf-4448-83b4-1e83ab1d4640`

API returns “HTTP 202 Accepted”. Based on request API can return other standard status listed [here](#standard-api-response-statuses).

| **Name**     | **Description**                                                                                       |
|--------------|-------------------------------------------------------------------------------------------------------|
| 202 Accepted | The request has been accepted. Check the request status by polling the operation-location header URL. |

## Step 2: Check request status

Wait for an HTTP 200 with a terminal status of succeeded or failed. The manifest URL will be "resourceLocation" in the success status.

### Get operation status

Gets the status of a reconciliation data request.

### API request

`GET https://ep-billingreconservice-prod-d5bfczcnfvbqbdhx.z01.azurefd.net/v1/billingoperations/06d01983-07bf-4448-83b4-1e63ab1d3640`

### Request parameters

| **Name**    | **In** | **Required** | **Type** | **Description**   |
|-------------|--------|--------------|----------|-------------------|
| operationId | Path   | True         | String   | The operation ID. |

### Request header

Request headers for the API are [listed here](#standard-api-request-headers).

### Request body

N/A.

### Response status

In addition to the standard HTTP status listed [here](#standard-api-response-statuses). API can return below HTTP status:

| **Name** | **Description**                                                                                                                                   |
|----------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| 410 Gone | Each operation link is active for a specified amount of server-controlled time. After the time has elapsed, the client must submit a new request. |

### Response payload

The API response payload returns the following attributes:

| Name        | Optional | Description |
|--------------------|---------------------|----------------------|
|createdDateTime| false | Request time.|
|lastActionDateTime |false | Status change time.|
| resourceLocation | true | The manifest payload URI.|
| status     | false              | Possible values and actions.|

|  Value | Client action |
|--------|---------------|
| notstarted | Make another call to check the status after waiting for the time specified in the “Retry-After” header. |
| running    | Make another call to check the status after waiting for the time specified in the “Retry-After” header.
| succeeded  | The final state of operation, which indicates that data is ready. Retrieve the manifest payload using the URI specified in **resourceLocation**. |  
| failed     | Terminal state, which indicates permanent failure. Restart the operation.|

For error attribute:

| Name        | Optional | Description |
|--------------------|---------------------|----------------------|
|error|true| Error details provided in json format if the status of operation is failed.

| Name | Optional | Description                           |
|----------|--------------|-------------------------------------------|
| message  | false        | Describes the error in detail             |
| code     | false        | Indicates the kind of error that occurred |

### API request

`GET https://ep-billingreconservice-prod-d5bfczcnfvbqbdhx.z01.azurefd.net/v1/billingoperations/06d01983-07bf-4447-83b4-1e83ab1d3640`

### API response

The response suggests waiting 10 seconds before retrying when processing data.

```json
HTTP/1.1 200 OK  
Retry-After: 10  
{  
"createdDateTime": "2022-06-1T10-01-03.4Z",  
“lastActionDateTime”:” 2022-06-1T10-01-05Z”,  
"status": "running"  
}
```

### API request

(10 seconds after the earlier request)

`GET https://ep-billingreconservice-prod-d5bfczcnfvbqbdhx.z01.azurefd.net/v1/billingoperations/06d01983-07bf-4447-83b4-1e83ab1d3640`

### API response

The API returns the "succeeded" status and the "resourceLocation" URI.

```json
HTTP/1.1 200 OK  
Content-Type: application/json  
{  
"createdDateTime": "2022-06-1T10-01-03.4Z",  
"lastActionDateTime": "2022-06-1T10-01-13Z",  
"status": "succeeded",  
"resourceLocation": “https://ep-billingreconservice-prod-d5bfczcnfvbqbdhx.z01.azurefd.net/v1/billingmanifests/e03e1882-ff59-4c09-882f-74e60b4d7743”  
}
```

## Step 3: Get manifest payload

The caller makes a GET request to the manifest URL to learn more about where the reconciliation data is stored in Azure blobs.

### Getting the manifest

Retrieves the manifest having information about the Azure storage location of the reconciliation data.

### API request

`GET https://ep-billingreconservice-prod-d5bfczcnfvbqbdhx.z01.azurefd.net/v1/billingmanifests/{manifestId}`

### Request parameters

| **Name**   | **In** | **Required** | **Type** | **Description**  |
|------------|--------|--------------|----------|------------------|
| manifestId | Path   | True         | String   | The manifest ID. |

### Request header

Request headers for the API are [available here](#standard-api-request-headers).

### Request body

N/A.

### Response status

In addition to the standard HTTP status listed [here](#standard-api-response-statuses). API can return below HTTP status:

| **Name** | **Description**                                                                                                                                  |
|----------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| 410 Gone | Each manifest link is active for a specified amount of server-controlled time. After the time has elapsed, the client must submit a new request. |

### Response payload

The API response returns the following attributes:

| **Name**           | **Description**                                                                                                                                                                                                                                                                                                                               |
|--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Version            | The manifest schema version.                                                                                                                                                                                                                                                                                                                  |
| dataFormat         | The billing data file format.  Possible values compressedJSONLines: each blob is a compressed file and data in the file is in [JSON lines](https://jsonlines.org/) format. Decompress the file to access the data.                                                                                                                            |
| utcCreatedDateTime | Manifest file creation time.                                                                                                                                                                                                                                                                                                                  |
| eTag               | Manifest data version. A change in billing information generates a new eTag value.                                                                                                                                                                                                                                                            |
| partnerTenantId    | Partner Tenant ID.                                                                                                                                                                                                                                                                                                                            |
| rootFolder         | The file’s root directory.                                                                                                                                                                                                                                                                                                                    |
| rootFolderSAS      | The SAS token for accessing the file.                                                                                                                                                                                                                                                                                                         |
| partitionType      | This property divides the data. If a given partition has more than the supported number, the data will be split into multiple files corresponding to the “partitionValue.”  Data is partitioned by the number of line items in the file by default. Don't set a fixed number of line items or file size in your code since these may change. |
| blobCount          | Total file count for this Partner Tenant ID.                                                                                                                                                                                                                                                                                                  |
| sizeInBytes        | Total bytes in all the files.                                                                                                                                                                                                                                                                                                                 |
| blobs              | A JSON array of "blob" objects having the details of all the files for the partner tenant ID.                                                                                                                                                                                                                                                 |
| Blob object        |                                                                                                                                                                                                                                                                                                                                               |
| Name               | Blob’s name.                                                                                                                                                                                                                                                                                                                                  |
| sizeInBytes        | Blob size in bytes.                                                                                                                                                                                                                                                                                                                           |
| partitionValue     | The partition that contains the file. A large partition will be split into multiple files, each with the same “partitionValue.”                                                                                                                                                                                                               |

### Sample manifest payload

```json
{
"version": "1",
"dataFormat": "compressedJSONLines",
"utcCretedDateTime": "2022-04-29T22:40:57.1853571Z",
"eTag": "0x5B168C7B6E589D2",
"partnerTenantId": "14f593ad-1edc-474d-aaa0-83abbf9638da",
"rootFolder": "https://{billing.blob.core.windows.net}/{folder_path}",
"rootFolderSAS": "\*\*\*",
"partitionType": "ItemCount",
"blobCount": 3,
"sizeInBytes": 2000,
"blobs": [
  {
  "name": "{blobName1.json.gz}",
  "sizeinBytes": 500,
  "partitionValue": "1"
  },
  {
  "name": "{blobName2.json.gz}",
  "sizeinBytes": 1000,
  "partitionValue": "2"
  },
  {
  "name": "{blobName3.json.gz}",
  "sizeinBytes": 500,
  "partitionValue": "3"
  }
  ]
}
```

## Step 4: Download usage reconciliation data from storage location

Download the reconciliation data from Azure blob storage using the SAS token in the manifest payload. Use the Microsoft Azure Storage SDK/tool to download blobs and uncompress or unzip the blob file before reading its data. The data is in [JSON](https://jsonlines.org/) lines format.

### Standard API request headers

All APIs accept the following headers:

| **Name**         | **Required** | **Type** | **Description**                                                           |
|------------------|--------------|----------|---------------------------------------------------------------------------|
| Authorization    | True         | String   | Authorization Bearer Token.                                               |
| ms-correlationid | False        | String   | An internal request tracker. Each request generates a new tracker (GUID). |
| ms-cv            | False        | String   | An internal request tracker.                                              |
| ms-requestid     | False        | String   | The request idempotency ID.                                               |

### Standard API response statuses

The following are the HTTP statuses from the API response:

| **Name**                  | **Description**                                                                                                  |
|---------------------------|------------------------------------------------------------------------------------------------------------------|
| 400 Bad Request           | There was missing or incorrect data. The error details are included in the response body.                        |
| 401 Unauthorized          | The caller isn't authenticated and must authenticate with the partner API service before making the first call. |
| 403 Forbidden             | The caller isn't authorized to make the request.                                                                |
| 500 Internal Server Error | The API or one of its dependencies is unable to fulfill the request. Please try again later.                     |
| 404 Not Found             | Resource not available with input parameters.                                                                    |
| 410 Gone                  | The manifest link has timed out or elapsed. Submit a new request.                                                |

### Usage data attributes

The billed or unbilled usage API response with the "full" or "basic" request parameter returns the following attributes:

| **Attribute**                 |  **“full”** |  **“basic”** |
|-------------------------------|-------------|--------------|
| PartnerId                     | yes         | yes          |
| PartnerName                   | yes         | yes          |
| CustomerId                    | yes         | yes          |
| CustomerName                  | yes         | Yes          |
| CustomerDomainName            | yes         | no           |
| CustomerCountry               | yes         | no           |
| MpnId                         | yes         | no           |
| Tier2MpnId                    | yes         | no           |
| InvoiceNumber                 | yes         | yes          |
| ProductId                     | yes         | yes          |
| SkuId                         | yes         | yes          |
| AvailabilityId                | yes         | no           |
| SkuName                       | yes         | yes          |
| ProductName                   | yes         | no           |
| PublisherName                 | yes         | yes          |
| PublisherId                   | yes         | no           |
| SubscriptionDescription       | yes         | no           |
| SubscriptionId                | yes         | yes          |
| ChargeStartDate               | yes         | yes          |
| ChargeEndDate                 | yes         | yes          |
| UsageDate                     | yes         | yes          |
| MeterType                     | yes         | no           |
| MeterCategory                 | yes         | no           |
| MeterId                       | yes         | no           |
| MeterSubCategory              | yes         | no           |
| MeterName                     | yes         | no           |
| MeterRegion                   | yes         | no           |
| Unit                          | yes         | yes          |
| ResourceLocation              | yes         | no           |
| ConsumedService               | yes         | no           |
| ResourceGroup                 | yes         | no           |
| ResourceURI                   | yes         | yes          |
| ChargeType                    | yes         | yes          |
| UnitPrice                     | yes         | yes          |
| Quantity                      | yes         | yes          |
| UnitType                      | yes         | no           |
| BillingPreTaxTotal            | yes         | yes          |
| BillingCurrency               | yes         | yes          |
| PricingPreTaxTotal            | yes         | yes          |
| PricingCurrency               | yes         | yes          |
| ServiceInfo1                  | yes         | no           |
| ServiceInfo2                  | yes         | no           |
| Tags                          | yes         | no           |
| AdditionalInfo                | yes         | no           |
| EffectiveUnitPrice            | yes         | yes          |
| PCToBCExchangeRate            | yes         | yes          |
| EntitlementId                 | yes         | yes          |
| EntitlementDescription        | yes         | no           |
| PartnerEarnedCreditPercentage | yes         | no           |
| CreditPercentage              | yes         | yes          |
| CreditType                    | yes         | yes          |
| BenefitOrderID                | yes         | yes          |
| BenefitID                     | yes         | no           |
| BenefitType                   | yes         | yes          |
