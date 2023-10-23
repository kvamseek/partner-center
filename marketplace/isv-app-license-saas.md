---
title:       ISV app license management for SaaS offers - Microsoft AppSource and Azure Marketplace
description: Learn about managing ISV app licenses through Microsoft for SaaS offers.
author:      jucoyner1
ms.author:   juliacoyner
ms.service:  marketplace
ms.subservice: partnercenter-marketplace-publisher
ms.topic:    conceptual
ms.date:     04/05/2023
---

# ISV app license management for SaaS offers

If you enabled license management for your SaaS offers (currently available for AppSource only) in Partner Center, then you must integrate with usageRights Graph API to look up licenses of customers. You use usageRights API to determine the licensing state of the customer calling your solution so you can act accordingly.

[!INCLUDE [Important - Azure AD Graph is deprecated](../developer/includes/azure-ad-graph-notice.md)]

## usageRights API

_API_: [usageRight resource type](/graph/api/resources/usageright?view=graph-rest-beta&preserve-view=true)

## How to use usageRights API

You can call usageRights Graph API to determine what is the state of the license for the logged-in user who has purchased the subscription of your offer.
To call the API, follow these steps:

1. Get user On Behalf Of token: see [get access on behalf of a user](/graph/auth-v2-user)
2. Call Graph to get user's object ID: see [use the Microsoft Graph API](/graph/use-the-api)
3. Call usageRights API to determine the user has License to the plan: see [list user usageRights](/graph/api/user-list-usagerights?view=graph-rest-beta&tabs=http&preserve-view=true)

> [!NOTE]
> You need to have minimum User.Read permissions to call usageRights. The usageRights API is currently in beta version. After the version is updated to V1, ISVs should upgrade from beta to V1 version when available.

## Response Codes

Code 200 with response body:

```
{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#users('ea201692-eb91-44e0-b82a-9dd4c78ced32')/usageRights",
    "@odata.nextLink": "https://graph.microsoft.com/beta/users/ea201692-eb91-44e0-b82a-9dd4c78ced32/usageRights?$skiptoken=ZXlKamIzTnRiM05FWWxSdmEyVnVJam9pVzN0Y0ltTnZiWEJ2YzJsMFpWUnZhMlZ1WENJNmUxd2lkRzlyWlc1Y0lqcHVkV3hzTEZ3aWNtRnVaMlZjSWpwN1hDSnRhVzVjSWpwY0lqRkdSa1pHUmtaR1JrWkdSa1pHUmtaR1JrWkdSa1pHUmt.......",
    "value": [
        {
            "id": "635991be-b7a3-4dd4-a48c-f1d39732fe94",
            "catalogId": "ID of the Product",
            "serviceIdentifier": "ISV friendly ID of the product, this is same as planID in partner center",
            "state": "active"
        }
    ]
}
```

## API response explained

- __Odata.nextLink__: If your request has several results and needs to be paged, you'll see Odata.nextLink in the response. You can use this to page the results until there is no more Odata.nextLink, which indicates the end of the response.
- __serviceIdentifier__: The planId of the plan that customer purchased.
- __state__: The state of the license. You can see all possible values of state in the usageRights API documentation. Typically, the user should be able to run your solution if the license state is __active__ or __warning__. Any other state means user's subscription isn't in good condition either because it's expired, or it's suspended for nonpayment, etc.
- Code 200 with empty response: _This is likely because the customer does not have a license assigned._
- Code 400 Bad request: _This is likely because of missing fields while calling the API like Bearer token. Check your API call parameters._
- Code 403 Forbidden: _This is likely because of expired or unauthorized token. Please check you are using the right Azure AD App to authenticate the usageRights Graph API._
- Code 500 Internal server error: _Retry the API call. If the error persists, contact Microsoft Support._

> [!NOTE]
> If the Azure AD app you use for SaaS fulfillment API is also used for usageRights API, then please ensure that the tenant under which the add app is created is either the publishing tenant OR associated tenant in partner center.

Use the following steps to determine the tenant that Azure AD App is created under is part of the partner center setup:

1. Login to [Microsoft Partner Center](https://partner.microsoft.com) with the publisher account that is used to publish the SaaS offer.
1. Under settings link on right top corner, select "Account settings" and then "tenants"
1. You can see all tenants associated in the Microsoft AI Cloud Partner Program account.
1. The tenant that is the owner of the Azure AD App should be on this list.
1. If the tenant is not on the list, you can use the "Associate Azure ID" button to link the tenant.

:::image type="content" source="media/isv-app-license-saas/image.png" alt-text="Screenshot illustrating the Azure AD app list of tenants." lightbox="media/isv-app-license-saas/image.png":::<br>
