---
title: Get subscription analytics by search query
description: How to get subscription analytics information filtered by a search query.
ms.date: 05/10/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
ms.author: kiranban
author: kbangalore
---

# Get subscription analytics information filtered by a search query

**Applies to**: Partner Center | Partner Center operated by 21Vianet |  Partner Center for Microsoft Cloud for US Government

How to get subscription analytics information for your customers filtered by a search query.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with User credentials only.

## REST request

### Request syntax

| Method | Request URI |
|--------|-------------|
| **GET** | [*\{baseURL\}*](partner-center-rest-urls.md)/partner/v1/analytics/subscriptions?filter={filter_string} |

### URI parameters

Use the following required path parameter to identify your organization and filter the search.

| Name | Type | Required | Description |
|------|------|----------|-------------|
| filter_string | string | Yes | The filter to apply to the subscription analytics. See the Filter syntax and Filter fields sections for the syntax, fields, and operators to use in this parameter. |

### Filter syntax

The filter parameter must be composed as a series of field, value, and operator combinations. Multiple combinations can be combined using **`and`** or **`or`** operators.

An unencoded example looks like this:

- String: `?filter=Field operator 'Value'`
- Boolean: `?filter=Field operator Value`
- Contains `?filter=contains(field,'value')`

### Filter fields

The filter parameter of the request contains one or more statements that filter the rows in the response. Each statement contains a field and value that are associated with the **`eq`** or **`ne`** operators. Some fields also support the **`contains`**, **`gt`**, **`lt`**, **`ge`**, and **`le`** operators. Statements can be combined using **`and`** or **`or`** operators.

The following are examples of filter strings:

```http
autoRenewEnabled eq true

autoRenewEnabled eq true and customerMarket eq 'US'
```

The following table shows a list of the supported fields and support operators for the filter parameter. String values must be surrounded by single quotes.

| Parameter | Supported operators | Description |
|-----------|---------------------|-------------|
| autoRenewEnabled | `eq`, `ne` | A value indicating whether the subscription is renewed automatically. |
| commitmentEndDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le`  | The date the subscription ends. |
| creationDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le`  | The date the subscription was created. |
| currentStateEndDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le` | The date that the current status of the subscription will change. |
| customerMarket | `eq`, `ne` | The country/region that the customer does business in. |
| customerName | `contains` | The name of the customer. |
| customerTenantId | `eq`, `ne` | A GUID-formatted string that identifies the customer tenant. |
| deprovisionedDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le` | The date that the subscription was deprovisioned. The default value is null. |
| effectiveStartDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le` | The date the subscription starts. |
| friendlyName | `contains` | The name of the subscription. |
| id | `eq`, `ne` | A GUID-formatted string that identifies the subscription. |
| lastRenewalDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le` | The date that the subscription was last renewed. The default value is null. |
| lastUsageDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le` | The date that the subscription was last used. The default value is null. |
| partnerId | `eq`, `ne` | The PartnerID. For a direct reseller, this value will be the PartnerID of the partner. For an indirect reseller, this value will be the PartnerID of the indirect reseller. |
| partnerName | string | Name of the partner for whom the subscription was purchased |
| productName | `contains`, `eq`, `ne` | The name of the product. |
| providerName | string | When subscription transaction is for the indirect reseller, provider name is the indirect provider who bought the subscription.|
| status | `eq`, `ne` | The subscription status. Supported values are: "ACTIVE", "SUSPENDED", or "DEPROVISIONED". |
| subscriptionType | `eq`, `ne` | The subscription type. **Note**: This field is case-sensitive. Supported values are: "Office", "Azure", "Microsoft365", "Dynamics", "EMS". |
| trialStartDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le` | The date that the trial period for the subscription started. The default value is null. |
| trialToPaidConversionDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le`  | The date that the subscription converts from trial to paid. The default value is null. |

### Request headers

For more information, see [Partner Center REST headers](headers.md).

### Request body

None.

### Request example

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/subscriptions?filter=autoRenewEnabled eq true
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105123
Content-Type: application/json
Content-Length: 0
```

## REST response

If successful, the response body contains a collection of [Subscription](partner-center-analytics-resources.md#subscription-resource) resources that meet the filter criteria.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Error Codes](error-codes.md).

### Response example

```http
HTTP/1.1 200 OK
Content-Length: 177
Content-Type: application/json; charset=utf-8
MS-CorrelationId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-RequestId: ec8f62e5-1d92-47e9-8d5d-1924af105123

{
    "customerTenantId": "735920EB-A564-4C72-9FE5-52632562712C",
    "customerName": "SURFACE TEST2",
    "customerMarket": "US",
    "id": "B76412DA-D382-4688-A6A4-711A207C1C2E",
    "status": "ACTIVE",
    "productName": "UNKNOWN",
    "subscriptionType": "Azure",
    "autoRenewEnabled": true,
    "partnerId": "3B33E682-00C3-41EE-9DD2-A548ADF56438",
    "friendlyName": "MICROSOFT AZURE",
    "creationDate": "2017-06-02T23:11:58.747",
    "effectiveStartDate": "2017-06-02T00:00:00",
    "commitmentEndDate": null,
    "currentStateEndDate": null,
    "trialToPaidConversionDate": null,
    "trialStartDate": null,
    "trialEndDate": null,
    "lastUsageDate": null,
    "deprovisionedDate": null,
    "lastRenewalDate": null,
    "licenseCount": 0
}
```

## See also

- [Partner Center Analytics - Resources](partner-center-analytics-resources.md)
