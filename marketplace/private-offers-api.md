---
title: Private offers submission API overview
description: This article describes how to submit private offers through the Partner Center API.
ms.subservice: partnercenter-marketplace-publisher
ms.service: marketplace
ms.topic: article
author: migolova 
ms.author: migolova 
ms.date: 07/18/2023
---

# Private offers submission API overview

Private offers allow publishers and customers to transact one or more products in Azure Marketplace by creating time-bound pricing with customized terms. The private offer submission APIs enable publishers to programmatically create and manage private offers for customers and/or CSP partners. This API uses Azure Active Directory (Azure AD) to authenticate the calls from your app or service.

There are three main types of private offers available in Partner Center and supported by the private offer submission API:

- **ISV to customer private offer** – Also termed Customer private offer in Partner Center. This is a custom deal between an ISV and a specific customer with customized terms and pricing for a specific product in Azure Marketplace. Learn more about [ISV to customer private offer](isv-customer.md).
- **ISV to CSP partner private offer** – Also termed CSP Partners private offer in Partner Center. This type of private offer lets ISV specify time-bound margin to create a wholesale price for their CSP partner. Learn more about [ISV to CSP partner private offer](isv-csp-reseller.md).
- **Multiparty private offer** **(MPO)** – A custom deal collaboratively configured by an ISV and a preferred selling partner of a specific customer with customized terms and pricing for specific products in Azure Marketplace. The ISV defines the discounted wholesale price made available to the partner, the selling partner can then add markup on top of the wholesale price to arrive at the final customer price and presents the offer to the customer for acceptance and purchase. Acceptance and purchase of the MPO follows the same flow as ISV to customer private offers.  Learn more about [multiparty private offer](multiparty-private-offers-for-isvs.md).

## Terminology

- **MPO originator** – MPO is a collaboration between ISV and selling partner on the same custom deal for a specific customer, the party who first creates the MPO is designated the “originator” of the offer, typically the ISV of the products included in the MPO. There can only be one originator for any given MPO.
- **MPO seller** – The selling partner that prepares the offer with the final customer price and presents the offer to the customer is the seller of the MPO. There can only be one seller for any given MPO.  
- **Product** – A single unit representing an offer in Azure Marketplace. There's one product per listing page.
- **Plan** – A single version of a particular product. There can be multiple plans for a given product that represent various levels of pricing or terms.
- **Job** – A task created when making a request in this API. When using this API to manage private offers and multiparty private offers, a job is created to complete the request. Once the job is completed, you can get more information about the relevant (multiparty) private offer.

## Supported scenarios

- [Create a private offer for a customer](create-direct-isv-to-customer-private-offer-api.md)
- [Create a private offer for a reseller](create-private-offer-for-a-csp-partner-api.md)
- [Create a multiparty private offer for a customer](create-multiparty-private-offer-for-a-customer-api.md)
- [Delete a private offer](manage-existing-private-offers-via-api.md#delete-an-existing-private-offer)
- [Withdraw a private offer](manage-existing-private-offers-via-api.md#withdraw-an-existing-private-offer)
- [Query for a list of multiparty private offers](#retrieve-private-offers)
- [Query for a list of products and plans](#retrieve-plans-for-a-specific-product)

## Get ready to use this API

Before you write code to call the private offers API, ensure you've completed the following prerequisites.  The same prerequisites apply for all publishing partners.

### Step 1: Complete prerequisites for using the Microsoft Product Ingestion API (one-time)

You or your organization must have an Azure AD directory and global administrator permission. If you already use Microsoft 365 or other business services from Microsoft, you already have Azure AD directory. If not, you can create a new Azure AD in Partner Center for free.

You must [associate an Azure AD](https://aka.ms/PCtoAzureAD) application with your Partner Center account and obtain your tenant ID, client ID, and key. You need these values to obtain the Azure AD access token you'll use in calls to the private offers API.

### Step 2: Obtain an Azure AD access token (every time)

Before you call any of the methods in the Microsoft Store submission API, you need an Azure AD access token to pass to the authorization header of each method in the API. You have 60 minutes to use a token before it expires. After expiration, you can refresh a token so you can continue to use it in further calls to the API.

To obtain the access token, see [Service to Service Calls Using Client Credentials](https://aka.ms/AADAccesstoken) to send an HTTP POST to the [https://login.microsoftonline.com/<tenant_id>/oauth2/token](https://login.microsoftonline.com/<tenant_id>/oauth2/token) endpoint. Here's a sample request:

```JSON
POST https://login.microsoftonline.com/<tenant_id>/oauth2/token HTTP/1.1
Host: login.microsoftonline.com
Content-Type: application/x-www-form-urlencoded; charset=utf-8
grant_type=client_credentials
&client_id=<your_client_id>
&client_secret=<your_client_secret>
&resource=https://graph.microsoft.com/

```

For the tenant_id value in the POST URI and the client_id and client_secret parameters, specify the tenant ID, client ID, and key for your application that you retrieved from Partner Center in the previous section. For the resource parameter, you must specify [https://graph.microsoft.com/](https://graph.microsoft.com/).

## Find product, plan, and private offer IDs

| **ID**         | **Where to find them**                                                                                                                                                   |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| client_id      | See [Associate an Azure AD application with your Partner Center account](https://aka.ms/PCtoAzureAD).                                                                    |
| tenant_id      | See [Associate an Azure AD application with your Partner Center account](https://aka.ms/PCtoAzureAD).                                                                    |
| client_secret  | See [Associate an Azure AD application with your Partner Center account](https://aka.ms/PCtoAzureAD).                                                                    |
| productId      | See [Retrieve products](#retrieve-products) in this article.                                         |
| planId         | See [Retrieve plans for a specific product](#retrieve-plans-for-a-specific-product) in this article. |
| privateofferId | See [Retrieve private offers](#retrieve-private-offers) in this article.                             |

## Retrieve products

A private offer is based on an existing product in your Partner Center account. To see a list of products associated with your Partner Center account, use this API call:

```JSON
GET https://graph.microsoft.com/rp/product-ingestion/product?$version=2022-07-01
```

The response appears in the following sample format:

```JSON
{
  "value": [
    {
      "$schema": "https://schema.mp.microsoft.com/schema/product/2022-07-01",
      "id": "string",
      "identity": {
        "externalId": "string"
      },
      "type": "enum",
      "alias": "string"
    }
  ],
  "@nextLink": "opaque_uri"
}
```

## Retrieve plans for a specific product

For products that contain more than one plan, you may want to create a private offer based on one specific plan. If so, you need that plan's ID. Obtain a list of the plans (such as variants or SKUs) for the product using the following API call:

```JSON
GET https://graph.microsoft.com/rp/product-ingestion/plan?product=<product-id>&$version=2022-07-01
```

The response appears in the following sample format:

```JSON
{
  "value": [
    {
      "$schema": "https://schema.mp.microsoft.com/schema/plan/2022-07-01",
      "product": "string",
      "id": "string",
      "identity": {
        "externalId": "string"
      },
      "alias": "string"
    }
  ]
}
```
## Retrieve private offers

To see a list of all private offers, including multiparty private offers, associated with your account, use the following API call:

```
GET https://graph.microsoft.com/rp/product-ingestion/private-offer/query?$version=2023-07-15
```

## How to use the API

The private offer API lets you create and manage private offers associated with products and plans within your Partner Center account. Here's a summary of the typical calling pattern when using this API.

:::image type="content" source="media/multiparty-private-offers/how-to-use-the-api-flowchart.png" alt-text="Flowchart showing multiparty private offers steps." lightbox="media/multiparty-private-offers/how-to-use-the-api-flowchart.png":::

### Step 1. Make the request

When you make an API call to create, delete, withdraw, or upgrade a private offer, a new job is created to complete the requested task. The API response contains a jobId associated with the job.

### Step 2. Poll for job status

Using the **jobId** from the initial API response, poll to get the job status. The status of the job will either be **Running** or **Completed**. Once the job is completed, the result will either be **Succeeded** or **Failed**. To avoid performance issues, don't poll a job more than once per minute.

| jobStatus | Description                                                                                                                                                                                             |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| NotStarted    | The job hasn't yet started; this is part of the response on the initial request.                                                                                                                            |
| Running       | The job is still running.                                                                                                                                                                                   |
| Completed     | The job has been completed. See **jobResult** for more details.                                                                                                                                                 |
| **jobResult** | **Description** |
| Pending   | The job hasn't yet completed.       |
| Succeeded     | The job has been completed successfully. This job also returns a resourceURI that refers to the private offer related to the job. Use this resourceURI to obtain the full details of a private offer. |
| Failed        | The job has failed. This also returns any relevant errors to help determine the cause of failure.    |

For more information, see [Query the status of an existing job](job-status-and-retrieve-private-offer-detail-api.md#query-the-status-of-an-existing-job).

### Step 3. Obtain information from completed jobs

A successful job returns a resourceUri referencing the relevant private offer. Use this resource Uri to obtain more details about the private offer in the future, such as the privateofferId.

A failed job contains errors that provide detail on why the job failed and how to resolve the issue.

For more information, see [Obtain details of an existing private offer](job-status-and-retrieve-private-offer-detail-api.md#obtain-details-of-an-existing-private-offer).

## How ISV and selling partner should collaboratively use the API for multiparty private offer

Both ISV and selling partner can use the same APIs for creation and management of a given MPO. However, resources in an MPO that can affect the API depend on whether the caller of the API is the ISV (originator) or the selling partner (seller) of the MPO. The same ISV/selling partner publishing flow and business rules governing Partner Center are mirrored in the API. Here's an overview:

| API Operation | ISV (Originator)    | Selling Partner (Seller)     |
| ------------- | ------------------- | ---------------------------- |
| Create        | <ul><li>Intended audience is the **selling** **partner** (seller) when the API call is posted, end customer won't see the private offer until the selling partner submits</li></ul>**Editable resources:**<ul><li>Effective dates</li><li>Intended beneficiary (customer)</li><li>Selling partner to collaborate on the offer, limited to 1 per private offer</li><li>Additional ISV contacts to be notified of the private offer status</li><li>ISV custom terms and conditions</li><li>Products/plans included in the private offer</li><li>Contract duration(s) for each product/plan</li><li>Included quantities for each product (if applicable)</li><li>Nonpricing plan attributes (if applicable)</li><li>Discounted wholesale price available to the selling partner on the included products/plan</li><li>ISV sales notes</li></ul> | <ul><li>Intended audience is the **end-customer** when the API call is posted</li></ul>**Editable resources:**<ul><li>Selling partner custom terms and conditions</li><li>Prepared by</li><li>Customer adjustment (markup percentage) on top of the ISV wholesale price for each product/plan included in the private offer, this determines the final end customer price</li><li>Additional selling partner contacts to be notified of the private offer status</li><li>Selling partner sales notes</li></ul> |
| Delete            | <ul><li> Supported for private offers in draft state </li></ul>         | <ul><li> Not supported </li></ul>      |
| Withdraw          | <ul><li> Supported for private offers published by the ISV but not yet published by the selling partner or if withdrawn by the selling partner </li></ul>  | <ul><li> Supported for private offers published and available to end customers but not accepted yet</li></ul> |

## Next steps

- [Create a private offer for a customer](create-direct-isv-to-customer-private-offer-api.md)
- [Create a private offer for a reseller](create-private-offer-for-a-csp-partner-api.md)
- [Create multiparty private offer for customer API](create-multiparty-private-offer-for-a-customer-api.md)
