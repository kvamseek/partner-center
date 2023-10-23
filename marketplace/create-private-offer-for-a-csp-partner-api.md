---
title: Create a private offer for a CSP partner in Microsoft Partner Center
description: Use this method to create a new private offer for a customer. 
ms.subservice: partnercenter-marketplace-publisher
ms.service: marketplace
ms.topic: article
author: tortsuk
ms.author: tortsuk
ms.date: 07/18/2023
---

# Create a private offer for a CSP partner

Use this method to create a new private offer for a customer.

## Request

```
POST https://graph.microsoft.com/rp/product-ingestion/configure?$version=2022-07-01
```

## Request header

| Header        | Type    | Description    |
| ------------- | ------- | -------------- |
| Authorization | String  | Required. The Azure AD access token in the form ```Bearer <token>```. |

## Request parameters

**$version** - required. This is the version of the schema that is being used in the request.

## Request body

Provide the details of the private offer using the **ISV to reseller margin private offer** schema. You must include a name.

```JSON
{
 "$schema": "https://schema.mp.microsoft.com/schema/configure/2022-07-01", 
  "resources": [ 
    { 
       "$schema": "https://schema.mp.microsoft.com/schema/private-offer/2023-07-15", 
       "privateOfferType": "cspPromotion",
       "name": "privateOffercsp1034",
       "state": "live",
       "variableStartDate": false,
       "start": "2022-01-31",
       "end": "2022-02-28",
       "preparedBy": "amy@contoso.com",
       "notificationContacts": [ "amy@contoso.com" ],
       "beneficiaries": [ 
          { "id": "xxxxxxx-0a32-4b44-b904-39dd964dd790", "description": "Top First CSP"}
       ], 
       "pricing": [ 
          { "product": "product/34771906-9711-4196-9f60-4af380fd5042", "plan":"plan/123456","discountType": "percentage","discountPercentage": 5 }
       ]
    }
  ]
}
```

### Request body samples

#### Sample request for a reseller offer restricted to a specified beneficiary

If you're creating a margin for a reseller that applies to a specific customer, add that information as an object in the beneficiaryRecipients parameter array under beneficiaries.

The request body will look like the following sample:

```JSON
[
    {
        "id": "xxxxxxx-0a32-4b44-b904-39dd964dd790",
        "description": "Top First CSP",
        "beneficiaryRecipients": [
            {
                "id": "xxxxxxx-48b4-af80-66333cd9c609",
                "recipientType": "cspCustomer"
            }
        ]
    }
],
```

## Response

The response contains the jobId you can use later to poll the status.

```JSON
{
    "$schema": "https://schema.mp.microsoft.com/schema/configure-status/2022-07-01",
    "jobId": "c32dd7e8-8619-462d-a96b-0ac1974bace5",
    "jobStatus": "notStarted",
    "jobResult": "pending",
    "jobStart": "2021-12-21T21:29:54.9702903Z",
    "jobEnd": "0001-01-01",
    "errors": []
}
```

## Error codes

| HTTP status code | Description              |
| ---------------- | ------------------------ |
| 401              | Authentication Error: Ensure you're using a valid Azure AD access token. |
| 400              | Schema Validation. Ensure your request body is following the correct schema and includes all required fields. |

## Next steps

- [Manage existing private offers](manage-existing-private-offers-via-api.md)
- [Job status and retrieve private offer detail API](job-status-and-retrieve-private-offer-detail-api.md)
- [Troubleshooting and additional resources](private-offer-api-troubleshooting.md)
