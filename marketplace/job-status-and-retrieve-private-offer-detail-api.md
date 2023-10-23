---
title: Job status and retrieve private offer detail via API in Microsoft Partner Center
description: This article includes methods to check status and to retrieve private offer details through the Partner Center API.
ms.subservice: partnercenter-marketplace-publisher
ms.service: marketplace
ms.topic: article
author: tortsuk
ms.author: tortsuk
ms.date: 07/18/2023
---

# Job status and retrieve private offer detail via API

This article includes methods to check status and retrieve private offer details through the Partner Center API.

## Query the status of an existing job

Use this method to query the status of an existing job. You can poll the status of an existing job with a polling interval with a maximum frequency of one request per minute.

### Request

```
GET https://graph.microsoft.com/rp/product-ingestion/configure/<jobId>/status?$version=2022-07-01
```

### Request header

| Header        | Type    | Description    |
| ------------- | ------- | -------------- |
| Authorization | String  | Required. The Azure AD access token in the form ```Bearer <token>```. |

### Request parameters

- **jobId** – required. This is the ID of the job you want to query the status of. It's available in the response data generated during a previous request to either create, delete, withdraw, or upgrade a private offer.
- **$version** - required. This is the version of the schema that is being used in the request.

### Request body

No request body is available for this method.

### Response

There are three possible responses for a completed job:

| jobResult | Description|
| --------- | ---------- |
| Running   | The job hasn't yet completed.  |
| Succeeded | The job completed successfully. This also returns a resourceURI that refers to the offer related to the job. Use this resourceURI to obtain the full details of an offer. |
| Failed    | The job failed. This will also return any relevant errors to help determine the cause of failure. |

### Sample outputs

#### Running

```JSON
JSON
{
    "$schema": "https://schema.mp.microsoft.com/schema/configure-status/2022-07-01",
    "jobId": "c32dd7e8-8619-462d-a96b-0ac1974bace5",
    "jobStatus": "running",
    "jobResult": "pending",
    "jobStart": "2021-12-21T21:29:54.9702903Z",
    "jobEnd": "2021-12-21T21:30:10.3649551Z",
    "errors": []
}
```

#### Succeeded

```JSON
{
    "$schema": " https://schema.mp.microsoft.com/schema/configure-status/2022-07-01",
    "jobId": "b3f49dff-381f-480d-a10e-17f4ce49b65f",
    "jobStatus": "completed",
    "jobResult": "succeeded",
    "jobStart": "2021-12-21T21:29:54.9702903Z",
    "jobEnd": "2021-12-21T21:30:10.3649551Z",
    "resourceUri": "https://product-ingestion.mp.microsoft.com/configure/b3f49dff-381f-480d-a10e-17f4ce49b65f",
    "errors": []
}
```

> [!NOTE]
> If the job was created by a request to delete a private offer, then there will be no resourceURI in the response.

#### Failure

```JSON
{
    "$schema": " https://schema.mp.microsoft.com/schema/configure-status/2022-07-01",
    "jobId": "c32dd7e8-8619-462d-a96b-0ac1974bace5",
    "jobStatus": "completed",
    "jobResult": "failed",
    "jobStart": "2021-12-21T21:29:54.9702903Z",
    "jobEnd": "2021-12-21T21:30:10.3649551Z",
    "errors": [
        {
            "code": "Conflict",
            "message": "The start date should be defined"
        }
    ]
}
```

#### Error codes

| Error code | Description |
| ---------- | ----------- |
| 401        | Authentication Error: ensure you're using a valid Azure AD access token. |

## Obtain details of an existing private offer

There are two methods to do this depending whether you have the resourceURI or the private offer ID.

### Request

```
GET https://graph.microsoft.com/rp/product-ingestion/private-offer/<id>?$ version=2023-07-15
```

or

```
GET https://graph.microsoft.com/rp/product-ingestion/configure/<jobId>?$version=2023-07-15  
```

### Request header

| Header        | Type    | Description    |
| ------------- | ------- | -------------- |
| Authorization | String  | Required. The Azure AD access token in the form ```Bearer <token>```. |

### Request parameters

- **ID** - required. This is the ID of the private offer you want the full details of. This ID is available in the response data generated during a previous request to obtain the details of an existing multiparty private offer using the jobId.

- **jobId** - required. This is the ID of the job you want the full details of. This ID is available in the response data generated during a previous request to either create, delete, withdraw, or upgrade a private offer.
- **$version** - required. This is the version of the schema that is being used in the request

### Request body

Don't provide a request body for this method.

### Response

You'll receive the full details of the private offer. Here's an example for a selling partner caller when querying for a multiparty private offer.

```JSON
{
    "id": "private-offer/30b90a6a-df19-43cc-a107-b0c62057da6d",
    "name": "mpo_api_test",
    "privateOfferType": "multiPartyPromotionChannelPartner",
    "offerPricingType": "editExistingOfferPricingOnly",
    "variableStartDate": true,
    "end": "2023-01-31",
    "acceptBy": "2023-01-21",
    "notificationContacts": [],
    "state": "draft",
    "originatorTermsAndConditionsDocs": [
        {
            "sasUrl": "https://promotionpmeprod.blob.core.windows.net/promotionsblobdata/44c2b38a-fa64-4861-806c-6c486ec19b6d-769f3960-45af-42db-ab3b-6391841683d6",
            "fileName": "test.pdf",
            "customerFacingDocumentName": "test1"}],
    "termsAndConditionsDocs": [],
    "beneficiaries": [
        {
            "id": "ac357579-e860-54a6-80b3-66958aea67fe:7471d04e-f696-4d20-af34-fa78d51e419c_2019-05-31",
            "description": "beneficiary Id"}],
    "partners": [
        {
            "id": "12345678",
            "partnerName": "Market Place Test",
            "location": "United States" }],
    "originatorPricing": [
        {
            "product": "product/11775d67-fb2b-46bf-ad0f-0e1d5e74ba03",
            "productName": "mpo_test_saas_site_1",
            "plan": "plan/11775d67-fb2b-46bf-ad0f-0e1d5e74ba03/570ebda0-467b-4ac3-a0d8-069131afd7ee",
            "planName": "MPO Site 1 - LTS 2",
            "discountType": "absolute",
            "priceDetails": "price-and-availability-private-offer-plan/11775d67-fb2b-46bf-ad0f-0e1d5e74ba03/2152924500014081860"},
        {
            "product": "product/6c73a19b-ba11-496c-b38b-1d4a3cc64d91",
            "productName": "mpo_test_vmsr",
            "plan": "plan/6c73a19b-ba11-496c-b38b-1d4a3cc64d91/24f34f12-df93-4a7b-93d7-d9336e02d44e",
            "planName": "MPO VMSR 4",
            "discountType": "percentage",
            "discountPercentage": 2.0 }],
    "lastModified": "2023-01-19",
    "eTag": "\"7d02cb1b-0000-0800-0000-63c9aee80000\"",
    "$schema": "https://schema.mp.microsoft.com/schema/private-offer/2023-07-15"
}
```

### Error codes

| HTTP status code | Description              |
| ---------------- | ------------------------ |
| 401              | Authentication Error: Ensure you're using a valid Azure AD access token. |
| 404              | Resource not found. Ensure you're using the correct ID in the request.   |

## Next steps

- [Manage existing private offers](manage-existing-private-offers-via-api.md)
- [Troubleshooting and additional resources](private-offer-api-troubleshooting.md)
