---
title: include file
description: Reminder - Changes to license assignment - Impact on partners announcement from April 4, 2023
ms.topic: include
ms.service: partner-dashboard
ms.subservice: partnercenter-announcements
ms.custom: has-azure-ad-ps-ref
author: JulCsc
ms.author: juliacawthra
ms.reviewer: satinder.bajaj
ms.date: 05/01/2023
---

## Reminder - Changes to license assignment - Impact on partners

*Microsoft previously [announced](https://techcommunity.microsoft.com/t5/microsoft-entra-azure-ad-blog/migrate-your-apps-to-access-the-license-managements-apis-from/ba-p/2464366) that on March 31, 2023, the MSOnline and Azure Active Directory Graph license assignment APIs will be retired to enable the transition to Microsoft Cloud Licensing. This specifically impacts User license assignment in CSP (via both Partner center UX and API) in two conditions. First is **where the customer has a Conditional Access policy**: Partners will need to work with the customer to identify and exclude the Partner Tenant from the Conditional Access policy (see [GDAP FAQs](../../../gdap-faq.md#what-is-the-recommended-next-step-if-the-conditional-access-policy-set-by-the-customer-blocks-all-external-access-including-csps-access-aobo-to-the-customers-tenant)). Second is **where the partner is using [Partner token](/rest/api/partner-center/authentication/generate-access-token)**: Partners will need to move to Partner Access Token (see [Enable secure application model](../../../developer/enable-secure-app-model.md#get-access-token)).*

- **Date**: May 1, 2023
- **Workspace**: Customers
- **Impacted audience**: Partners trying to assign licenses and upgrade subscriptions for their end customers

From May 1, partners will see the below error messages (when using [AssignUserLicensesAsync](../../../developer/assign-licenses-to-a-user.md), [UpgradeSubscription](../../../developer/transition-a-subscription.md) with license transfer) if customer tenant has Conditional Access policy and partner tenant is not added in the exclusion list of the same:

- **API**:

  |HTTP status|HTTP error code|Error code|Description|
  |----|----|----|----|
  |Forbidden|403|900309|Access has been blocked by Conditional Access policies. The access policy does not allow token issuance. Learn more at Users and groups in [Conditional Access policy - Microsoft Entra](/azure/active-directory/conditional-access/concept-conditional-access-users-groups)|
  |Bad Request|400 |900316 | Partner token is not allowed in license management calls. Please call with Partner Access Token - [Enable secure application model](../../../developer/enable-secure-app-model.md#get-access-token)|
  |

- **UX error**:

   :::image type="content" source="../../../media/announcements/2023-april/ux-error.png" lightbox="../../../media/announcements/2023-april/ux-error.png" alt-text="Screenshot of conditional access error.":::

#### Next steps

Partners need to work with the affected customers to identify and exclude the partner tenant from the Conditional Access policy.

When creating a Conditional Access policy:

1. Select **Exclude**.
1. Check the **Guest or external users** box.
    - This selection provides several choices that can be used to target Conditional Access policies to specific guest or external user types and specific tenants containing those types of users.
    - There are several different types of guest or external users that can be selected, and multiple selections can be made, such as Service provider users (for example, a Cloud Solution Provider).
    - One or more tenants can be specified for the selected user type(s), or you can specify all tenants.

For more on how to exclude a partner tenant from the Conditional Access policy, see the [GDAP FAQs](../../../gdap-faq.md#what-is-the-recommended-next-step-if-the-conditional-access-policy-set-by-the-customer-blocks-all-external-access-including-csps-access-aobo-to-the-customers-tenant).

Where the partner is using [Partner token](/rest/api/partner-center/authentication/generate-access-token) - API Error code 900316 Partner token isn't allowed in license management calls. Call with Partner Access Token.

**Solution**: Update APIs to use Partner Access Token per [Enable secure application model](../../../developer/enable-secure-app-model.md#get-access-token).

### Get support

If you need help with the Conditional Access policy, create a service request with Azure Support using the following parameters:

- **Summary**: Conditional access
- **Issue type**: Technical
- **Service type**: Azure Active Directory sign-in and multi-factor authentication
- **Problem type**: Conditional access
- **Problem subtype**: Grant or block access
