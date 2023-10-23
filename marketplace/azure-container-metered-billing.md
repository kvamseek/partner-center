---
title: Metered billing for Azure Containers using the commercial marketplace metering service
description: Detailed instructions about Azure Containers metered billing
ms.service: marketplace 
ms.subservice: partnercenter-marketplace-publisher
ms.topic: article
author: AarathiN
ms.author: aarathin
ms.reviewer: janeguo-msft
ms.date: 05/04/2023
---

# Metered billing for Azure Containers using the commercial marketplace metering service

With the commercial marketplace metering service, you can create Azure Container offers that are charged according to nonstandard units. Before publishing the offer to the commercial marketplace, you define the billing dimensions such as bandwidth, shards, logfiles, scans, emails processed, etc. Customers then pay according to their consumption of these dimensions, with your application informing Microsoft via the [commercial marketplace metering service API](#azure-container-metered-billing) of billable events as they occur.

## Prerequisites for metered billing

For an Azure Container offer to use metered billing, you must first review the [Licensing options](marketplace-containers.md) outlined in [Plan for Azure Container offer](marketplace-containers.md) and make sure that you have custom billing needs that isn't met by one of the six existing predefined billing models.

Then the Azure Container offer can integrate with the [commercial marketplace metering service APIs](#azure-container-metered-billing) to inform Microsoft of billable events.

> [!IMPORTANT]
> Your application will have to call the commercial marketplace metering service APIs. Currently there isn’t an option to let your hosted service (outside the application) to call metering service API.

> [!NOTE]
> Marketplace metering service is available only to the custom billing model and does not apply to the per user billing model.

## How metered billing fits in with pricing

Understanding the offer hierarchy is important when it comes to defining the offer along with its pricing models.

- Each offer is configured to sell either through Microsoft or not. Once an offer is published, this option can't be changed.
- Each offer, configured to sell through Microsoft, can have one or more plans.
- Each plan has a pricing model associated with it: **Usage-based monthly billed plan** or **Bring your own license (BYOL)**. For the usage-based monthly billing plan, you can either choose free, one of six predefined billing options, or custom.
- The pricing model and price input options can't be updated once published.
- Each plan must have complete pricing plan.
- You can choose to price using custom dimensions to charge your customers to help meet your billing needs. Each dimension represents a billable unit that your service communicates to Microsoft using the [commercial marketplace metering service API](#azure-container-metered-billing).

> [!IMPORTANT]
> You must keep track of the usage in your code and only send usage events to Microsoft for the usage you want the customer invoiced.

> [!NOTE]
> Offers will be billed to customers in the customers’ agreement currency, using the local market price that was published at the time the offer was created. The amount that customers pay, and that ISVs are paid, depends on the Foreign Exchange rates at the time the customer transacts the offer. Learn more on ["How we convert currency?"](marketplace-geo-availability-currencies.md).

## Sample custom pricing options

As an example, Contoso is a publisher whose IP is in their sharding logic for their Kubernetes application. Contoso wants to charge their customers based on the number of shards used. They're also exploring other conveniently and competitively priced billing options. Contoso is registered as a publisher in Partner Center for the commercial marketplace program and wants to publish Container offers to Azure customers. There are four plans associated with Contoso, outlined below:

- Charge per the shards used per hour, for example, $1,000/shard/hour
   
   :::image type="content" source="./media/azure-container-metered-billing/metering-service-dimension-1.png" alt-text="Screenshot depicting charge per the shards used per hour." lightbox="./media/azure-container-metered-billing/metering-service-dimension-1.png":::

- Modeling one-time payment or recurring billing: Let’s say Contoso wants to charge a customer $449/mo for using upto 100 log files from their application. Contoso’s application logic triggers a usage event for the monthly charge and let the application run and use upto 100 log files. It would gracefully notify customer for any overage beyond that. Contoso can model that using dimensions, like so:

   :::image type="content" source="./media/azure-container-metered-billing/metering-service-dimension-2.png" alt-text="Screenshot depicting modeling one-time payment or recurring billing." lightbox="./media/azure-container-metered-billing/metering-service-dimension-2.png":::

- Modeling tiered billing: Let’s say Contoso wants to charge $449/mo for upto 100 shards, and then for any overage they want tiered pricing. Their application logic would keep track of the usage, segment the usage accordingly and report the appropriate billable using the metering APIs. It can be modeled using dimensions like so:

   :::image type="content" source="./media/azure-container-metered-billing/metering-service-dimension-3.png" alt-text="Screenshot depicting modeling tiered billing." lightbox="./media/azure-container-metered-billing/metering-service-dimension-3.png":::

- Multidimensional billing: Contoso can also use custom metering to meet their needs for advanced billing using multiple dimensions

   :::image type="content" source="./media/azure-container-metered-billing/metering-service-dimension-4.png" alt-text="Screenshot depicting multidimensional billing." lightbox="./media/azure-container-metered-billing/metering-service-dimension-4.png":::

Based on the selected plan, an Azure customer getting the Contoso Container offer is charged based on their usage. Contoso counts the usage without sending any usage events to Microsoft. Either when customers consume adequate amount or on a periodic basis, Contoso reports the usage. Customers don't have to change plans or do anything different. Contoso measures the usage and starts emitting usage events to Microsoft for charging the overage usage using the [commercial marketplace metering service API](#azure-container-metered-billing). Microsoft in turn charges the customer for the usage as specified by the publisher in the custom dimensions. The billing is done on the next monthly billing cycle.

## Billing dimensions

Each billing dimension defines a custom unit by which the ISV can emit usage events. Billing dimensions are also used to communicate to the customer about how they'll be billed for using the software. They're defined as follows:

- **ID**: the immutable dimension identifier referenced while emitting usage events.
- **Display Name**: the display name associated with the dimension, for example "text messages sent".
- **Unit of Measure**: the description of the billing unit, for example "per text message" or "per 100 emails".
- **Price per unit in USD**: the price for one unit of dimension. It can be 0.

> [!NOTE]
> Accuracy is to two decimal points (one cent), it is not unlimited, and Microsoft will truncate a meter less than $0.01 to zero.

> [!IMPORTANT]
> You must keep track of the usage in your application code and send usage events to Microsoft based on your billing needs.

Billing dimensions are shared across all plans for an offer. Some attributes apply to the dimension across all plans, and other attributes are plan-specific.

The attributes, which define the dimension itself, are shared across all plans for an offer. Before you publish the offer, a change made to these attributes from the context of any plan affects the dimension definition across all plans. Once you publish the offer, these attributes are no longer editable. These attributes are:

- ID
- Display Name
- Unit of Measure

The other attributes of a dimension are specific to each plan and can have different values from plan to plan. Before you publish the plan, you can edit these values, and only this plan will be affected. Once you publish the plan, these attributes will no longer be editable. These attributes are:

- Price per unit in USD

Dimensions also have a special concept called "enabled":

- **Enabled** indicates that this plan participates in this dimension. If you're creating a new plan that doesn't send usage events based on this dimension, you might want to leave this option unchecked. Also, any new dimensions added after a plan was first published will show up as "not enabled" on the already published plan. A disabled dimension won't show up in any lists of dimensions for a plan seen by customers.

> [!NOTE]
> The following scenarios are explicitly supported:
>
> - You can add a new dimension to a new plan. The new dimension will not be enabled for any already published plans.

### Setting dimension price per unit per supported market

Like other usage-based pricing, billing dimension prices can be set per supported country or region. You need to use the pricing data import and export feature in Partner Center, as follows.

1. Define the desired dimensions and mark which markets are supported.
1. Export this data into a file.
1. Add the correct prices per country/region and import the file in Partner Center.

The user interface of the meter changes to reflect that the prices of the dimension can only be seen in the file.

   :::image type="content" source="./media/azure-container-metered-billing/metering-service-dimension-5.png" alt-text="Screenshot depicting the user interface of the meter." lightbox="./media/azure-container-metered-billing/metering-service-dimension-5.png":::

### Private plan

Like the predefined usage-based billing plans, a plan with custom dimensions can be set as private plan, accessible only by the plan's defined audience.

## Constraints

### Locking behavior

Because a dimension used with the commercial marketplace metering service represents an understanding of how a customer will be paying for the service, all the details for a dimension are no longer editable after you publish it. It's important that you have your dimensions fully defined for a plan before you publish.

Once an offer is published with a dimension, the offer-level details for that dimension can no longer be changed:

- ID
- Display Name
- Unit of Measure

Once a plan is published, this plan-level detail can no longer be changed:

- Whether the dimension is enabled for the plan or not

### Upper limits

The maximum number of dimensions that can be configured for a single offer is 30 unique dimensions.

## Azure Container metered billing

The metered billing APIs should be used when the publisher creates custom metering dimensions for an offer to be published in Partner Center. Integration with the metered billing APIs is required for any purchased offer that has one or more plans with custom dimensions to emit usage events. 

> [!IMPORTANT]
> For more information on creating custom metering dimensions for Kubernetes Apps, see [Create an Azure Container Offer](/partner-center/marketplace/azure-container-offer-setup).

### Enforcing TLS 1.2 note

TLS version 1.2 version is enforced as the minimal version for HTTPS communications. Make sure you use this TLS version in your code. TLS version 1.0 and 1.1 are deprecated and connection attempts are refused.

### Metered billing single usage event

The usage event API should be called by the publisher to emit usage events against an active resource (subscribed) for the plan purchased by the specific customer. The usage event is emitted separately for each custom dimension of the plan defined by the publisher when publishing the offer.

Only one usage event can be emitted for each hour of a calendar day per resource and dimension. If more than one unit is consumed in an hour, then accumulate all the units consumed in the hour and then emit it in a single event. Usage events can only be emitted for the past 24 hours. If you emit a usage event at any time between 8:00 and 8:59:59 (and it's accepted) and send another event for the same day between 8:00 and 8:59:59, it's rejected as a duplicate.

**POST**: `https://marketplaceapi.microsoft.com/api/usageEvent?api-version=<ApiVersion>`

*Query parameters:*

| Parameter | Recommendation          |
| ---------- | ---------------------- |
| `ApiVersion` | Use 2018-08-31. |

*Request headers:*

| Content-type       | Use `application/json`  |
| ------------------ | ---------------------------- |
| `x-ms-requestid`     | Unique string value for tracking the request from the client, preferably a GUID. If this value isn't provided, one is generated and provided in the response headers. |
| `x-ms-correlationid` | Unique string value for operation on the client. This parameter correlates all events from client operation with events on the server side. If this value isn't provided, one is generated and provided in the response headers. |
| `authorization`   | A unique access token that identifies the ISV that is making this API call. The format is `"Bearer <access_token>"` when the token value is retrieved by the publisher, as explained in Kubernetes application in [Authentication strategies](marketplace-metering-service-authentication.md). |

*Request body example:*


```json
{
  "resourceUri": "<ARM resource URI of the Kubernetes app instance>", // unique identifier of the resource against which usage is emitted. 
  "quantity": 5.0, // how many units were consumed for the date and hour specified in effectiveStartTime, must be greater than 0 or a double integer
  "dimension": "dim1", // custom dimension identifier
  "effectiveStartTime": "2018-12-01T08:30:14", // time in UTC when the usage event occurred, from now and until 24 hours back
  "planId": "plan1", // id of the plan purchased for the offer
}
```

>[!NOTE]
> For Kubernetes apps, the `resourceUri` is the ARM resource URI of the Kubernetes App instance. 

#### Responses

Code: 200<br>
OK. The usage emission was accepted and recorded on Microsoft side for further processing and billing.

Response payload example:





```json
{
  "usageEventId": <guid>, // unique identifier associated with the usage event in Microsoft records
  "status": "Accepted" // this is the only value in case of single usage event
  "messageTime": "2020-01-12T13:19:35.3458658Z", // time in UTC this event was accepted
  "resourceUri": "<ARM resource URI of the Kubernetes app instance>", // unique identifier of the resource against which usage is emitted. For SaaS it's the subscriptionId.
  "quantity": 5.0, // amount of emitted units as recorded by Microsoft
  "dimension": "dim1", // custom dimension identifier
  "effectiveStartTime": "2018-12-01T08:30:14", // time in UTC when the usage event occurred, as sent by the ISV
  "planId": "plan1", // id of the plan purchased for the offer
}
```

Code: 400 <br>
Bad request.

* Missing or invalid request data provided.
* `effectiveStartTime` is more than 24 hours in the past. Event has expired.

Response payload example: 

```json
{
  "message": "One or more errors have occurred.",
  "target": "usageEventRequest",
  "details": [
    {
      "message": "The resourceUri is required.",
      "target": "ResourceUri",
      "code": "BadArgument"
    }
  ],
  "code": "BadArgument"
}
```

Code: 400 <br>
Bad request.

* Resource URI is already registered previously, Need to wait for 24 hrs before submitting the usage. 

Response payload example: 

```json
{
  "message": "One or more errors have occurred.",
  "target": "usageEventRequest",
  "details": [
    {
      "message": "Invalid usage state.",
      "target": "ResourceUri",
      "code": "BadArgument"
    }
  ],
  "code": "BadArgument"
}
```

Code: 403<br>

Forbidden. The authorization token isn't provided, is invalid or expired.  

Code: 409<br>
Conflict. A usage event has already been successfully reported for the specified resource ID, effective usage date and hour.

Response payload example: 

```json
{
  "additionalInfo": {
    "acceptedMessage": {
      "usageEventId": "<guid>", //unique identifier associated with the usage event in Microsoft records
      "status": "Duplicate",
      "messageTime": "2020-01-12T13:19:35.3458658Z",
      "resourceUri": "<ARM resource URI of the Kubernetes app instance>", //unique identifier of the resource against which usage is emitted.
      "quantity": 1.0,
      "dimension": "dim1",
      "effectiveStartTime": "2020-01-12T11:03:28.14Z",
      "planId": "plan1"
    }
  },
  "message": "This usage event already exist.",
  "code": "Conflict"
}
```

### Metered billing batch usage event

The batch usage event API allows you to emit usage events for more than one purchased resource at once. It also allows you to emit several usage events for the same resource as long as they are for different calendar hours. The maximal number of events in a single batch is 25.

**POST:** `https://marketplaceapi.microsoft.com/api/batchUsageEvent?api-version=<ApiVersion>`

*Query parameters:*

| Parameter  | Recommendation     |
| ---------- | -------------------- |
| `ApiVersion` | Use 2018-08-31. |

*Request headers:*

| Content-type       | Use `application/json`       |
| ------------------ | ------ |
| `x-ms-requestid`     | Unique string value for tracking the request from the client, preferably a GUID. If this value isn't provided, one is generated, and provided in the response headers. |
| `x-ms-correlationid` | Unique string value for operation on the client. This parameter correlates all events from client operation with events on the server side. If this value isn't provided, is generated, and provided in the response headers. |
| `authorization`      | A unique access token that identifies the ISV that is making this API call. The format is `Bearer <access_token>` when the token value is retrieved by the publisher, as explained in Kubernetes application in [Authentication strategies](./marketplace-metering-service-authentication.md). |

>[!NOTE]
>In the request body, the resource identifier for Kubernetes apps is `resourceUri`. 

*Request body example for Kubernetes apps:*

```json
{
  "request": [ // list of usage events for the same or different resources of the publisher
    { // first event
      "resourceUri": "<ARM resource URI of the Kubernetes app instance>", // Unique identifier of the resource against which usage is emitted. 
      "quantity": 5.0, // how many units were consumed for the date and hour specified in effectiveStartTime, must be greater than 0 or a double integer
      "dimension": "dim1", //Custom dimension identifier
      "effectiveStartTime": "2018-12-01T08:30:14",//Time in UTC when the usage event occurred, from now and until 24 hours back
      "planId": "plan1", // id of the plan purchased for the offer
    },
    { // next event
      "resourceUri": "<ARM resource URI of the Kubernetes app instance>", 
      "quantity": 39.0, 
      "dimension": "email", 
      "effectiveStartTime": "2018-11-01T23:33:10
      "planId": "gold", // id of the plan purchased for the offer
    }
  ]
}
```

#### Responses

Code: 200<br>
OK. The batch usage emission was accepted and recorded on Microsoft side for further processing and billing. The response list is returned with status for each individual event in the batch. You should iterate through the response payload to understand the responses for each individual usage event sent as part of the batch event.

Response payload example: 

```json
{
  "count": 2, // number of records in the response
  "result": [
    { // first response
      "usageEventId": "<guid>", // unique identifier associated with the usage event in Microsoft records
      "status": "Accepted" // see list of possible statuses below,
      "messageTime": "2020-01-12T13:19:35.3458658Z", // Time in UTC this event was accepted by Microsoft,
      "resourceUri": "<ARM resource URI of the Kubernetes app instance>", // unique identifier of the resource against which usage is emitted.
      "quantity": 5.0, // amount of emitted units as recorded by Microsoft 
      "dimension": "dim1", // custom dimension identifier
      "effectiveStartTime": "2018-12-01T08:30:14",// time in UTC when the usage event occurred, as sent by the ISV
      "planId": "plan1", // id of the plan purchased for the offer
    },
    { // second response
      "status": "Duplicate",
      "messageTime": "0001-01-01T00:00:00",
      "error": {
        "additionalInfo": {
          "acceptedMessage": {
            "usageEventId": "<guid>",
            "status": "Duplicate",
            "messageTime": "2020-01-12T13:19:35.3458658Z",
            "resourceUri": "<ARM resource URI of the Kubernetes app instance>",
            "quantity": 1.0,
            "dimension": "email",
            "effectiveStartTime": "2020-01-12T11:03:28.14Z",
            "planId": "gold"
          }
        },
        "message": "This usage event already exist.",
        "code": "Conflict"
      },
      "resourceId": "<guid2>",
      "quantity": 1.0,
      "dimension": "email",
      "effectiveStartTime": "2020-01-12T11:03:28.14Z",
      "planId": "gold"
    }
  ]
}
```

Description of status code referenced in `BatchUsageEvent` API response:

| Status code  | Description |
| ---------- | -------------------- |
| `Accepted` | Accepted. |
| `Expired` | Expired usage. |
| `Duplicate` | Duplicate usage provided. |
| `Error` | Error code. |
| `ResourceNotFound` | The usage resource provided is invalid. |
| `ResourceNotAuthorized` | You aren't authorized to provide usage for this resource. |
| `ResourceNotActive` | The resource is suspended or was never activated. |
| `InvalidDimension` | The dimension for which the usage is passed is invalid for this offer/plan. |
| `InvalidQuantity` | The quantity passed is lower or equal to 0. |
| `BadArgument` | The input is missing or malformed. |

Code: 400<br>
Bad request. The batch contained more than 25 usage events.

Code: 403<br>
Forbidden. The authorization token isn't provided, is invalid or expired.

### Metered billing retrieve usage events

You can call the usage events API to get the list of usage events. ISVs can use this API to see the usage events that have been posted for a certain configurable duration of time and what state these events are at the point of calling the API.

GET: `https://marketplaceapi.microsoft.com/api/usageEvents`

*Query parameters*:

| Parameter | Recommendation |
| ------------ | ------------- |
| ApiVersion | Use 2018-08-31. |
| usageStartDate | DateTime in ISO8601 format. For example, 2020-12-03T15:00 or 2020-12-03 |
| UsageEndDate (optional) | DateTime in ISO8601 format. Default = current date |
| offerId (optional) | Default = all available |
| planId (optional) | Default = all available |
| dimension (optional) | Default = all available |
| azureSubscriptionId (optional) | Default = all available |
| reconStatus (optional) | Default = all available |

*Possible values of reconStatus*:

| ReconStatus | Description |
| ------------ | ------------- |
| Submitted | Not yet processed by PC Analytics |
| Accepted | Matched with PC Analytics |
| Rejected | Rejected in the pipeline. Contact Microsoft support to investigate the cause. |
| Mismatch | MarketplaceAPI and Partner Center Analytics quantities are both nonzero, however not matching |
| TestHeaders | Subscription listed with test headers, and therefore not in PC Analytics |
| DryRun | Submitted with SessionMode=DryRun, and therefore not in PC |

*Request headers*:

| Content type | Use application/json |
| ------------ | ------------- |
| x-ms-requestid | Unique string value (preferably a GUID), for tracking the request from the client. If this value isn't provided, one is generated and provided in the response headers. |
| x-ms-correlationid | Unique string value for operation on the client. This parameter correlates all events from client operation with events on the server side. If this value isn't provided, one is generated and provided in the response headers. |
| authorization | A unique access token that identifies the ISV that is making this API call. The format is `Bearer <access_token>` when the token value is retrieved by the publisher.<br>- Kubernetes application in [Authentication strategies](marketplace-metering-service-authentication.md) |

### Responses

Response payload examples:

*Accepted*





```json
[
  {
    "usageDate": "2020-11-30T00:00:00Z",
    "usageResourceId": "11111111-2222-3333-4444-555555555555",
    "dimension": "tokens",
    "planId": "silver",
    "planName": "Silver",
    "offerId": "mycooloffer",
    "offerName": "My Cool Offer",
    "offerType": "SaaS",
    "azureSubscriptionId": "12345678-9012-3456-7890-123456789012",
    "reconStatus": "Accepted",
    "submittedQuantity": 17.0,
    "processedQuantity": 17.0,
    "submittedCount": 17
  }
]
```

*Submitted*

```json
[
  {
    "usageDate": "2020-11-30T00:00:00Z",
    "usageResourceId": "11111111-2222-3333-4444-555555555555",
    "dimension": "tokens",
    "planId": "silver",
    "planName": "",
    "offerId": "mycooloffer",
    "offerName": "",
    "offerType": "SaaS",
    "azureSubscriptionId": "12345678-9012-3456-7890-123456789012",
    "reconStatus": "Submitted",
    "submittedQuantity": 17.0,
    "processedQuantity": 0.0,
    "submittedCount": 17
  }
]
```

*Mismatch*

```json
[
  {
    "usageDate": "2020-11-30T00:00:00Z",
    "usageResourceId": "11111111-2222-3333-4444-555555555555",
    "dimension": "tokens",
    "planId": "silver",
    "planName": "Silver",
    "offerId": "mycooloffer",
    "offerName": "My Cool Offer",
    "offerType": "SaaS",
    "azureSubscriptionId": "12345678-9012-3456-7890-123456789012",
    "reconStatus": "Mismatch",
    "submittedQuantity": 17.0,
    "processedQuantity": 16.0,
    "submittedCount": 17
  }
]
```

*Rejected*

```json
[
  {
    "usageDate": "2020-11-30T00:00:00Z",
    "usageResourceId": "11111111-2222-3333-4444-555555555555",
    "dimension": "tokens",
    "planId": "silver",
    "planName": "",
    "offerId": "mycooloffer",
    "offerName": "",
    "offerType": "SaaS",
    "azureSubscriptionId": "12345678-9012-3456-7890-123456789012",
    "reconStatus": "Rejected",
    "submittedQuantity": 17.0,
    "processedQuantity": 0.0,
    "submittedCount": 17
  }
]
```

**Status codes**

Code: 403
Forbidden. The authorization token isn't provided, is invalid or expired.

### Development and testing best practices

To test the custom meter emission, implement the integration with metering API, create a plan for your published Kubernetes Apps offer with custom dimensions defined in it with zero price per unit. And publish this offer as preview so only limited users would be able to access and test the integration.

You can also use private plan for an existing live offer to limit the access to this plan during testing to limited audience.

## Next steps

- For more information on metering service APIs, see [Marketplace metering service APIs FAQ](marketplace-metering-service-apis-faq.yml).

## Get support

If you have one of the following issues, you can open a support ticket.

- Technical issues with marketplace metering service API.
- An issue that needs to be escalated because of an error or bug on your side (ex. wrong usage event).
- Any other issues related to metered billing.

To understand publisher support options and open a support ticket with Microsoft, follow the instructions in [Support for the commercial marketplace program in Partner Center](support.md).
