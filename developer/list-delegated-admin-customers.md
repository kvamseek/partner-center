---
title: List the delegated admin customers of a partner
description: How to list the delegated admin customers of a partner.
ms.date: 5/13/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.custom: has-azure-ad-ps-ref
ms.topic: article
author: Vamseek
ms.author: vijvala
---

# List the delegated admin customers of a partner

**Applies to**: Partner Center

Returns a list of all customers of a partner, also indicating if customers have a DAP / non-DAP relationship.

**Purpose**: Partners are compliant to securely manage the customer tenant and remove inactive DAP relationships that are beyond 90 days using the [Remove a DAP relationship with a customer - Partner Center app developer](remove-dap.md).

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

   Opens an interactive window to sign in. Enter the credentials of the sandbox partner tenant.

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
| GET | `https://traf-pcsvcadmin-prod.trafficmanager.net/CustomerServiceAdminApi/Web/v1/delegatedAdminCustomers`                         |

### URI parameter

No URI parameters required for this API.

### Request headers

| Header | Description | Value
|--------|-------------|------
|Authorization | The authorization token in the form Bearer `<token>`. | String

### Request body

Don't supply a request body for this API.

### Optional query parameters

This method supports the `$select`, `$filter`, `$top` `$count`, `$skip` and `$orderBy` (allowed fields: organizationDisplayName, dapEnabled, startDateTime, lastSignInDateTime) to help customize the response.

`$top` supports up to 300 objects.

### Request example

```json
GET https://traf-pcsvcadmin-prod.trafficmanager.net/CustomerServiceAdminApi/Web/v1/delegatedAdminCustomers 
HTTP/1.1 
Authorization: Bearer \<token\> 
Content-Type: application/json; charset=utf-8 
```

## REST response

If successful, this method returns a collection of delegatedAdminCustomers resources in the response body.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and other debugging information. Use a network trace tool to read this code, error type, and other parameters. For the full list, see [Partner Center REST error codes](error-codes.md).

### delegatedAdminCustomers resource

Represents a delegated admin customer of a partner, and the details about the partner's access to the customer's tenant.

### Properties

|Property |Type |Description
|----------|------|------------
|id        |String|The unique identifier of the customer tenant.
| customerTenantId|String|The unique identifier of the customer tenant.
|OrganizationDisplayName | String | The display name of the customer's organization.
|partnerAgentCount | Int | The count of partners signed into the customer tenant in last one day.
|partnerSignInCount | Int | The number of times the partner(s) has signed into the customer tenant in last one day.
|dapEnabled | Boolean | The value indicates whether the partner has a DAP relationship for the customer.</br> If False: DAP relationship doesn't exist for that customer.</br> If True: DAP relationship exists for that customer
|startDateTime | String | The date time when the DAP relationship was established.
|endDateTime |String | The date time of the DAP relationship was terminated.
|lastSignInDateTime |String | The last date time of partner sign-in to this customer tenant.</br>Null/empty: No sign-ins to customer tenant by partners.

### Response example

```json
{ 

    "@odata.context": "https://traf-pcsvcadmin-prod.trafficmanager.net/CustomerServiceAdminApi/Web/v1/$metadata#delegatedAdminCustomers", 

    "value": [ 

        { 

            "id": "53018d99-ac51-4ec8-b86e-c8a61de43717", 

            "customerTenantId": "53018d99-ac51-4ec8-b86e-c8a61de43717", 

            "organizationDisplayName": "Test_Test_GAA_Partner_Account", 

            "partnerAgentCount": 0, 

            "partnerSignInCount": 0, 

            "globalAdminSignInCount": 0, 

            "dapEnabled": false, 

            "startDateTime": "2021-08-06T21:15:04.3461507Z", 

            "endDateTime": null, 

            "lastSignInDateTime": null 

        }, 

        { 

            "id": "6fc468f5-b399-4e05-a6f1-da8a33da9a6c", 

            "customerTenantId": "6fc468f5-b399-4e05-a6f1-da8a33da9a6c", 

            "organizationDisplayName": "StagingTest", 

            "partnerAgentCount": 0, 

            "partnerSignInCount": 0, 

            "globalAdminSignInCount": 0, 

            "dapEnabled": true, 

            "startDateTime": "2022-04-20T06:11:11.7227953Z", 

            "endDateTime": null, 

            "lastSignInDateTime": "2022-04-20T06:11:11.7227953Z" 

        } 
] 
} 
```
