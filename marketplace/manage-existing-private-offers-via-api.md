---
title: Manage existing private offers via API in Microsoft Partner Center
description: You can use APIs to delete or withdraw existing private offers. 
ms.subservice: partnercenter-marketplace-publisher
ms.service: marketplace
ms.topic: article
author: tortsuk
ms.author: tortsuk
ms.date: 07/18/2023
---

# Manage existing private offers via API

You can use APIs to delete or withdraw existing private offers.

## Delete an existing private offer

Use this method to delete an existing private offer while it's still in draft state. You must use the private offer ID to specify which private offer to delete.  For multipart private offers, only the MPO originator can delete the private offer.

### Request

```
POST https://graph.microsoft.com/rp/product-ingestion/configure?$version=2022-07-01
```

### Request header

| Header        | Type    | Description    |
| ------------- | ------- | -------------- |
| Authorization | String  | Required. The Azure AD access token in the form ```Bearer <token>```. |

### Request parameters

**$version** - required. This is the version of the schema that is being used in the request.

### Request body

```JSON
{
    "$schema": "https://schema.mp.microsoft.com/schema/configure/2022-07-01"
     "resources": [
        {
        "$schema": "https://schema.mp.microsoft.com/schema/private-offer/2023-07-15",
        "id": "private-offer/456e-a345-c457-1234",
        "name": "privateOffercustomer1705",
        "privateOfferType": "multipartyPromotionOriginator",
        "state": "deleted"
        }
    ]
}
```

### Response

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

### Error codes

| HTTP status code | Description              |
| ---------------- | ------------------------ |
| 401                  | Authentication Error: Ensure you're using a valid Azure AD access token.                                      |
| 400                  | Schema Validation. Ensure your request body is following the correct schema and includes all required fields. |

## Withdraw an existing private offer

Use this method to withdraw an existing private offer. Withdrawing an offer means your customer will no longer be able to access it.

> [!NOTE]
> For multiparty private offers, the ISV can withdraw a submitted private offer if the selling partner has not published and made it available to the end customer yet.  The selling partner can only withdraw a published private offer if the customer hasn't accepted it. If the private offer has already been made available for customer to accept and ISV needs to make changes to it, the selling partner must first withdraw the private offer so that the ISV can then withdraw and revert the private offer back to a draft state to make edits.

You must use the private offer ID to specify which private offer you want to withdraw.

### Request

```
POST https://graph.microsoft.com/rp/product-ingestion/configure?$version=2022-07-01
```

### Request Header

| Header        | Type    | Description    |
| ------------- | ------- | -------------- |
| Authorization | String  | Required. The Azure AD access token in the form ```Bearer <token>```. |

### Request parameters

**$version** - required. This is the version of the schema that is being used in the request.

### Request body (for ISV)

```JSON
{
    "$schema": "https://schema.mp.microsoft.com/schema/configure/2022-07-01"
     "resources": [
         {
        "$schema": "https://schema.mp.microsoft.com/schema/private-offer/ 2023-07-15",
        "id": "private-offer/456e-a345-c457-1234",
        "name": "privateOffercustomer1705", 
        "privateOfferType": "multipartyPromotionOriginator",
        "state": "withdrawn"
        }
    ]
}
```

### Request body (for Selling partner)

```JSON
{
    "$schema": "https://schema.mp.microsoft.com/schema/configure/2022-07-01"
     "resources": [
         {
        $schema": "https://schema.mp.microsoft.com/schema/private-offer/ 2023-07-15",
        "id": "private-offer/456e-a345-c457-1234",
        "name": "privateOffercustomer1705", 
        "privateOfferType": "multiPartyPromotionChannelPartner",
        "state": "withdrawn"
        }
    ]
}
```

### Response

The response contains the jobId you can later use to poll the status.

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

### Error codes

| HTTP status code | Description              |
| ---------------- | ------------------------ |
| 401              | Authentication Error: Ensure you're using a valid Azure AD access token. |
| 400              | Schema Validation. Ensure your request body is following the correct schema and includes all required fields. |

## Next steps

- [Job status and retrieve private offer detail API](job-status-and-retrieve-private-offer-detail-api.md)
- [Troubleshooting and additional resources](private-offer-api-troubleshooting.md)
