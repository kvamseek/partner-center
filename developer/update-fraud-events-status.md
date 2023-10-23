---
title: Azure fraud notification - Update fraud event status
description: Update the fraud event status to resolve the fraud alert.
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
ms.date: 09/11/2023
author: vijay-vala
ms.author: vijvala
---

# Azure fraud notification - Update fraud event status

**Applies to**: Partner Center API

After you investigated the fraud activities for each reported Azure resource and determined the behavior as fraudulent or legitimated, you can use this API to update the fraud event status with the appropriate reason.

> [!NOTE]
>This API will only update the event status, it will not resolve the fraud activity on behalf of CSP partners.

As of May 2023, pilot partners can use this API with the [**New Events Model**](#rest-request-with-the-x-neweventsmodel-header). With the new model, you can update new types of alerts as they're added to the system, for example, anomalous compute usage, crypto mining, Azure Machine Learning usage and service health advisory notifications.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with App+User credentials.

## REST request

### Request syntax

| Method  | Request URI                                                               |
|---------|---------------------------------------------------------------------------|
| **POST** | [*{baseURL}*](partner-center-rest-urls.md)/v1/fraudEvents/subscription/{subscriptionId}/status |

### Request headers

- For more information, see [Partner Center REST headers](headers.md).

### Request body

None.

### Request example

```http
POST https://api.partnercenter.microsoft.com/v1/fraudEvents/subscription/{subscriptionId}/status} HTTP/1.1
Authorization: Bearer <token>
Host: api.partnercenter.microsoft.com
Content-Type: application/json
{​

    "EventIds": ["2a7064fb-1e33-4007-974e-352cb3f2c805_2edeb5b1-766f-4209-9271-3ddf27755afa"],
    "EventStatus" : "Resolved",​
    "ResolvedReason": "Fraud"
}
```

### URI parameter

Use the following optional query parameters when creating the request.

| Name      | Type   | Required | Description                                                                                                                                                                                                                |
|-----------|--------|----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SubscriptionId   | string   | Yes       | The Azure subscription ID, which has the Crypro-mining activities |

### Request body

| Property              | Type             | Required        | Description                                                                                               |
|-----------------------|------------------|-----------------|-----------------------------------------------------------------------------------------------------------|
| eventIds                    | string[]           | No              | Keep eventIds as empty if you'd like to update the status for all fraud events under the given subscription ID|
| eventStatus | string         | No        | The fraud alert status. It can be either **Active**, **Resolved**, or **Investigating**. |
| resolvedReason | string         | Yes        | When fraud event is resolved, set an appropriate reason code, the accepted reason codes are **Fraud** or **Ignore** |

## REST response

If successful, this method returns a collection of Fraud events in the response body.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and more debugging information. Use a network trace tool to read this code, error type, and more parameters. For the full list, see [Error Codes](error-codes.md).

### Response example

``` http
HTTP/1.1 200 OK
Content-Length: 313
Content-Type: application/json
MS-CorrelationId: 4cb80cbe-566b-4d8b-8b8f-af1454b73089
MS-RequestId: 566330a7-1e4b-4848-9c23-f135c70fd810
Date: Thu, 21 May 2020 22:29:17 GMT
[
    {
        "eventTime": "2021-12-08T00:25:45.69",
        "eventId": "2a7064fb-1e33-4007-974e-352cb3f2c805_2edeb5b1-766f-4209-9271-3ddf27755afa",
        "partnerTenantId": "348e932d-ef58-4347-8351-be51e4ec148c",
        "partnerFriendlyName": "test partner",
        "customerTenantId": "a248da34-6840-4c67-82d7-7f55ccd50d03",
        "customerFriendlyName": "test customer",
        "subscriptionId": "2a7064fb-1e33-4007-974e-352cb3f2c805",
        "subscriptionType": "modern",
        "entityId": "2edeb5b1-766f-4209-9271-3ddf27755afa",
        "entityName": "sampleentity",
        "entityUrl": "\\sample\\entity\\url",
        "hitCount": "10",
        "catalogOfferId": "ms-azr-17g",
        "eventStatus": "Resolved",
        "serviceName": "sampleservice",
        "resourceName": "sampleresource",
        "resourceGroupName": "sampleresourcegroup",
        "firstOccurrence": "2021-12-08T00:25:45.69",
        "lastOccurrence": "2021-12-08T00:25:45.69",
        "resolvedReason": "Fraud",
        "resolvedOn": "2021-12-08T11:25:45.69",
        "resolvedBy": "adminagent@test.com"
    }
]
```

## REST request with the X-NewEventsModel header

### Request syntax

| MethodRequest |  URI |
|---------------|------|
| **POST** | [*{baseURL}*](partner-center-rest-urls.md)/v1/fraudEvents/subscription/{subscriptionId}/status |

### Request headers

- X-NewEventsModel: true
- For more information, see [Partner Center REST headers](headers.md).

### Request body

```html

{
    "EventIds": ["string"],
    "EventStatus": "Resolved",
    "ResolvedReason": "Fraud"
}
```

### Request example

```http
POST https://api.partnercenter.microsoft.com/v1/fraudEvents/subscription/{subscriptionId}/status} HTTP/1.1
Authorization: Bearer <token>
Host: api.partnercenter.microsoft.com
Content-Type: application/json
X-NewEventsModel: true
{
    "EventIds": ["2a7064fb-1e33-4007-974e-352cb3f2c805_2edeb5b1-766f-4209-9271-3ddf27755afa"],
    "EventStatus" : "Resolved",
    "ResolvedReason": "Fraud"
}
```

### URI parameter

Use the following optional query parameters when creating the request.

| Name           | Type   |Required  |Description   |
|----------------|--------|----------|--------------|
|SubscriptionId  |string  |Yes       |The Azure subscription ID, which has the Crypro-mining activities|

### Request body

| Property       |Type    |Required  |Description   |
|----------------|--------|----------|--------------|
|eventIds        |string[]|No        | Keep **eventIds** as empty if you'd like to update the status for all fraud events under the given subscription ID|
|eventStatus     |string  |Yes       | Set it to **Resolve** to resolve the fraud event or set it to **Investigating** to investigate a fraud event.|
|resolvedReason  |string  |Yes       | When fraud event is resolved, set an appropriate reason code, the accepted reason codes are **Fraud** or **Ignore**|

### REST response

If successful, this method returns a collection of Fraud events with extended attributes in the response body.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and more debugging information. Use a network trace tool to read this code, error type, and more parameters. For the full list, see Error Codes.

### Response example

```HTTP
HTTP/1.1 200 OK
Content-Length: 313
Content-Type: application/json
MS-CorrelationId: 4cb80cbe-566b-4d8b-8b8f-af1454b73089
MS-RequestId: 566330a7-1e4b-4848-9c23-f135c70fd810
Date: Thu, 21 May 2020 22:29:17 GMT
[
    {
        "eventTime": "2021-12-08T00:25:45.69",
        "eventId": "2a7064fb-1e33-4007-974e-352cb3f2c805_2edeb5b1-766f-4209-9271-3ddf27755afa",
        "partnerTenantId": "348e932d-ef58-4347-8351-be51e4ec148c",
        "partnerFriendlyName": "test partner",
        "customerTenantId": "a248da34-6840-4c67-82d7-7f55ccd50d03",
        "customerFriendlyName": "test customer",
        "subscriptionId": "2a7064fb-1e33-4007-974e-352cb3f2c805",
        "subscriptionType": "modern",
        "entityId": "2edeb5b1-766f-4209-9271-3ddf27755afa",
        "entityName": "sampleentity",
        "entityUrl": "\\sample\\entity\\url",
        "hitCount": "10",
        "catalogOfferId": "ms-azr-17g",
        "eventStatus": "Resolved",
        "serviceName": "sampleservice",
        "resourceName": "sampleresource",
        "resourceGroupName": "sampleresourcegroup",
        "firstOccurrence": "2021-12-08T00:25:45.69",
        "lastOccurrence": "2021-12-08T00:25:45.69",
        "resolvedReason": "Fraud",
        "resolvedOn": "2021-12-08T11:25:45.69", 
        "resolvedBy": "adminagent@test.com",
        "eventType": "NetworkConnectionsToCryptoMiningPools",
        "severity": "Medium",
        "confidenceLevel": "high",
        "displayName": "sample display name",
        "description": "sample description.",
        "country": "US",
        "valueAddedResellerTenantId": "897e68c5-fdf8-430e-bb54-3b386e0906b0",
        "valueAddedResellerFriendlyName": "Sample Reseller Name",
        "subscriptionName": "sample Subscription Name",
        "affectedResources": [
            {
                "azureResourceId": "\\sample\\resource\\url ",
                "type": "sample resource type"
            }
        ],
        "additionalDetails": {
            "resourceid": "\\sample\\resource\\id ",
            "resourcetype": "sample resource type",
            "vM_IP": "[\r\n \"13.89.185.189\"\r\n]",
            "miningPool_IP": "[\r\n \"104.243.33.118\"\r\n]",
            "connectionCount": "31",
            "cryptoCurrencyMiningPoolDomainName": "sample pool domain name"
            },
              "IsTest": "false",
                "activityLogs": "[
                {
                    "statusFrom": "Active",
                    "statusTo": "Investigating",
                    "updatedBy": "admin@testtestcsp022.ccsctp.net",
                    "dateTime": "2023-07-10T12:34:27.8016635+05:30"
            },
            {
                    "statusFrom": "Investigating",
                    "statusTo": "Resolved",
                    "updatedBy": "admin@testtestcsp022.ccsctp.net",
                    "dateTime": "2023-07-10T12:38:26.693182+05:30"
            }
          ]"

        }
    }
]
```

|Property             |Type    |Description|
|---------------------|--------|-----------|
|eventTime            |datetime|The time when the alert was detected|
|eventId              |string  |The unique identifier for the alert|
|partnerTenantId      |string  |The tenant ID of the partner associated with the alert|
|partnerFriendlyName  |string  |A friendly name for the partner tenant|
|customerTenantId     |string  |The tenant ID of the customer associated with the alert|
|customerFriendlyName |string  |A friendly name for the customer tenant|
|subscriptionId       |string  |The subscription ID of the customer tenant|
|subscriptionType     |string  |The subscription type of the customer tenant|
|entityId             |string  |The unique identifier for the alert|
|entityName           |string  |The name of the entity compromised|
|entityUrl            |string  |The entity Url of the resource|
|hitCount             |string  |The number of connections detected between firstObserved and lastObserved|
|catalogOfferId       |string  |The modern offer category ID of the subscription|
|eventStatus          |string  |The status of the alert: **Active**, **Investigating** or **Resolved**|
|serviceName          |string  |The name of the Azure service associated with the alert|
|resourceName         |string  |The name of the Azure resource associated with the alert|
|resourceGroupName    |string  |The name of the Azure resource group associated with the alert|
|firstOccurrence      |datetime|The impact start time of the alert (the time of the first event or activity included in the alert).|
|lastOccurrence       |datetime|The impact end time of the alert (the time of the last event or activity included in the alert).|
|resolvedReason       |string  |The reason provided by the partner for addressing the alert status|
|resolvedOn           |datetime|The time when the alert was resolved|
|resolvedBy           |string  |The user who resolved the alert|
|firstObserved        |datetime|The impact start time of the alert (the time of the first event or activity included in the alert).|
|lastObserved         |datetime|The impact end time of the alert (the time of the last event or activity included in the alert).|
|eventType            |string  |The type of alert: **ServiceHealthSecurityAdvisory**, **UsageAnomalyDetection**, **MultiRegionVirtualMachineScaleSetDeploymentAnomaly**, **NetworkConnectionsToCryptoMiningPools**, **VirtualMachineDeploymentAnomaly**, **MultiRegionMachineLearningUsageAnomaly**|
|severity             |string  |The severity of the alert. Values: Low, Medium, High|
|confidenceLevel      |string  |The confidence level of the alert, Values- Low, Medium, High|
|displayName          |string  |A user-friendly display name for the alert depending on the alert type.|
|description          |string  |A description of the alert|
|country              |string  |The country code for the partner tenant|
|valueAddedResellerTenantId |string  |The tenant ID of the value added reseller associated with the partner tenant and customer tenant|
|valueAddedResellerFriendlyName |string  |A friendly name for the value added reseller|
|subscriptionName     |string  |The subscription name of the customer tenant|
|affectedResources    |json Array  |The list of resources affected. Affected resources might be Empty for different alert types. If so, the partner needs to check the usage and consumption at the subscription level.|
|additionalDetails    |Json Object |A dictionary of other details key-values pairs required for identifying and managing the security alert.|
isTest                |string  |If an alert is generated for test, it will be set to **true** or else **false**.|
activityLogs          |string  |Activity logs for alert.
