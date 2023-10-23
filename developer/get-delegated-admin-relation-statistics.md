---
title: Get delegated admin relationship statistics
description: How to get delegated admin relationship statistics.
ms.date: 5/13/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.custom: has-azure-ad-ps-ref
ms.topic: article
author: Vamseek
ms.author: vijvala
---

# Get delegated admin relationship statistics

**Applies to**: Partner Center

Returns information on the count of Delegated Admin (DAP) relationships established or active that are associated to a partner across all of their customers.

**Purpose**: Partners are compliant to securely manage the customer tenant and remove inactive DAP relationships that are beyond 90 days using the [Remove a DAP relationship with a customer - Partner Center app developer](remove-dap.md).

This API helps track the statistics of active DAPs so partners can transition active DAPs to [Granular delegated admin privileges (GDAP)](../gdap-introduction.md).

> [!NOTE]
> This API is short lived and will be supported during the DAP deprecation phase. Post the DAP Deprecation program, this API will be retired.

## Prerequisites

### Credentials

This scenario supports authentication with App+User credentials only.

### Token exchange to receive access token

For more information, see [Configure an app to access a web API](/azure/active-directory/develop/quickstart-configure-app-access-web-apis).

Create a service principal for the Partner Customer Delegated Administration API app in the partner tenant by executing the following commands from a PowerShell console.

1. Connect to Azure Active Directory.

   `Connect-AzureAD`

   This opens an interactive window to sign in. Enter the credentials of the sandbox partner tenant.

2. Next, create a new service principal:
   `New-AzureADServicePrincipal -AppId 2832473f-ec63-45fb-976f-5d45a7d4bb91`

   | ObjectId |  AppId |  DisplayName |
   |----------|--------|--------------|
   | c1bf31da-09e5-4985-ab50-3232d4ae4f5a | 2832473f-ec63-45fb-976f-5d45a7d4bb91 | Partner Customer Delegated Administration |

3. Next, you create an app in the tenant by going to the [Azure portal](https://portal.azure.com), then **App registrations**, then either **Create a public client app** or **Use an existing app**.

4. Select **View API permissions** > **Add a permission** > **APIs my organization uses**

5. Select **Partner Customer Delegated Administration** > **Delegated permissions** > **Add permissions**

6. Grant admin consent for this new permission.

You can now use an App+User token (with resource `https://api.partnercustomeradministration.microsoft.com`) using this app (with a logged-in tenant admin) to call the GDAP APIs.

`POST https://login.microsoftonline.com/<partner_tenant_id>/oauth2/token grant_type=client_credentials&scope:https://api.partnercustomeradministration.microsoft.com&client_id:<client_id>&client_secret:<client_secret>`

## REST request

### Request syntax

| Method    | Request URI                                                                                                                |
|-----------|----------------------------------------------------------------------------------------------------------------------------|
| GET | `https://traf-pcsvcadmin-prod.trafficmanager.net/CustomerServiceAdminApi/Web/v1/delegatedAdminStatistics`                        |

### URI parameter

No URI parameters required for this API.

### Request headers

| Header | Description | Value
|--------|-------------|------
| Authorization | The authorization token in the form Bearer `<token>`. | String

### Request body

Don't supply a request body for this API.

### Request example

```json
GET https://traf-pcsvcadmin-prod.trafficmanager.net/CustomerServiceAdminApi/Web/v1/ delegatedAdminStatistics  
HTTP/1.1 
Authorization: Bearer \<token\> 
Content-Type: application/json; charset=utf-8 
```

## REST response

If successful, this method returns a collection of delegatedAdminStatistics resources in the response body.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and other debugging information. Use a network trace tool to read this code, error type, and other parameters. For the full list, see [Partner Center REST error codes](error-codes.md).

### delegatedAdminStatistics resource

Represents the object containing statistics of the usage of Delegated Admin Privilege (DAP) relationships.

### Properties

| Property | Type | Description
|----------|------|-------------
|id        |String|The unique identifier of the partner tenant.
| partnerTenantId|String|The unique identifier of the partner tenant.
|totalDapCustomerCount | Int | The total number of customers with DAP access.
|establishedDapCount | delegatedAdminAccessCount collection  | The number of DAPs established(created) and Date of creation. Example: If 10 DAPs created on 6/18/2021, the response would include “count” as 10 and “date” as "6/18/2021."
|inactiveDapCount | delegatedAdminAccessCount collection | The count of customers who have had sign-ins with the last date of sign-in. Example: If partner(s) signed in to 10 customers tenant on 6/18/2021, the response would include “count” as 10 and “date” as "6/18/2021."

### delegatedAdminAccessCount resource

Represents the count of delegated admin per day.

|Property |Type |Description
|----------|------|------------
| Date | String | The date of the action [established or signed in].
| Count | Int | The count of customers.

### Response example

```json
{ 

  "@odata.context": "https://traf-pcsvcadmin-prod.trafficmanager.net/CustomerServiceAdminApi/Web/v1/$metadata#delegatedAdminStatistics/$entity", 

  "id": "8984fecd-00a2-4686-ba43-b5c20866944a", 

  "partnerTenantId": "8984fecd-00a2-4686-ba43-b5c20866944a", 

  "totalDapCustomerCount": 200, 

  "establishedDapCount": [ 

    { 

      "date": "6/18/2021", 

      "count": 1 

    }, 

    { 

      "date": "2/18/2022", 

      "count": 1 

    } 

  ], 

  "inactiveDapCount": [ 

    { 

      "date": "2/18/2022", 

      "count": 1  

    }, 

    { 

      "date": "2/24/2022", 

      "count": 1 

    } 

  ] 

}  
```
