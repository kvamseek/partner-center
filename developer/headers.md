---
title: Partner Center REST headers
description: Learn about the HTTP REST request headers and REST response headers supported by the Partner Center REST API.
ms.date: 6/7/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: vijay-vala
ms.author: vijvala
---

# Partner Center REST and response headers supported by the Partner Center REST API 

**Applies to**: Partner Center | Partner Center operated by 21Vianet |  Partner Center for Microsoft Cloud for US Government

The following HTTP request and response headers are supported by the Partner Center REST API. Not all API calls accept all headers.

## REST request headers

The following HTTP request headers are supported by the Partner Center
REST API.

| Header                       | Description                                                                                                                                                                                                                                                                            | Value Type |
|------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|
| Authorization:               | Required. The authorization token in the form Bearer &lt;token&gt;.                                                                                                                                                                                                                    | string     |
| Accept:                      | Specifies the request and response type, "application/json".                                                                                                                                                                                                                           | string     |
| MS-RequestId:                | A unique identifier for the call, used to ensure id-potency. If there's a timeout, the retry call should include the same value. Upon receiving a response (success or business failure), the value should be reset for the next call.                                            | GUID       |
| MS-CorrelationId:            | A unique identifier for the call, useful in logs and network traces for troubleshooting errors. The value should be reset for every call. All operations should include this header. For more information, see the Correlation ID information in [Test and debug](test-and-debug.md). | GUID       |
| MS-Contract-Version:         | Required. Specifies the version of the API requested; generally api-version: v1 unless otherwise specified in the [Scenarios](scenarios.md) section.                                                                                                                                  | string     |
| If-Match:                    | Used for concurrency control. Some API calls require passing the ETag via the If-Match header. The ETag is usually on the resource and therefore, requires GET-ting the latest. For more information, see the ETag information in [Test and debug](test-and-debug.md).                | string     |
| MS-PartnerCenter-Application | Optional. Specifies the name of the application that is using the Partner Center REST API.                                                                                                                                                                                             | string     |
| X-Locale:                    | Optional. Specifies the language in which the rates are returned. Default is "en-US". For a list of supported values, see [Partner Center supported languages and locales](partner-center-supported-languages-and-locales.md).                                                                                                                                                                                                  | string     |

## REST response headers

The following HTTP response headers may be returned by the Partner
Center REST API.

| Header            | Description                                                                                                                                                                                                                                 | Value Type |
|-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|
| Accept:           | Specifies the request and response type, "application/json".                                                                                                                                                                                | string     |
| MS-RequestId:     | A unique identifier for the call, used to ensure id-potency. If there's a timeout, the retry call should include the same value. Upon receiving a response (success or business failure), the value should be reset for the next call. | GUID       |
| MS-CorrelationId: | A unique identifier for the call. This value is useful for troubleshooting logs and network traces to find the error. The value should be reset for every call. All operations should include this header.                                                       | GUID       |
