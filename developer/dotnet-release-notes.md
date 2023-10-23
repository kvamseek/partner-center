---
title: Partner Center .NET SDK release notes
description: Release notes for the latest version of the Partner Center .NET SDK.
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: denysseD
ms.author: denyssediaz 
ms.date: 05/24/2023
---

# .NET SDK release notes

The following release notes are available for new versions of [Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter). You can find [.NET SDK samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) on GitHub. You can find the [Partner Center .NET API reference](/dotnet/api/?view=partnercenter-dotnet-latest&preserve-view=true) in the .NET API Browser.

> [!IMPORTANT]
> As of June 2023, the latest Partner Center .NET SDK release 3.4.0 is now archived. You can [download the SDK release from GitHub](https://github.com/microsoft/partner-center-sdk-for-dotNET), along with a [readme file](https://github.com/microsoft/partner-center-sdk-for-dotNET#readme) that contains useful information.
>
> Partners are encouraged to continue to use the [Partner Center REST APIs](partner-center-rest-api-reference.md).

## Version 3.4.0

[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter) v3.4.0 is now available. Updated [GitHub samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) are also available.

The following changes are included in this version:

### Transact and manage

The following APIs are updated to provide term end date time properties:

- [`GetSubscriptionById`](get-a-subscription-by-id.md)
- [`GetAllSubscriptions`](subscription-resources.md)

`Pricing object` is now present in below API response:

- [`OrderLineItem`](checkout-a-cart.md)

### Promotions

Expose constraints:  

- [`GetPromoByID`](get-promotion-by-id.md)

## Version 3.3.0

[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter) v3.3.0 is now available. Updated GitHub samples are also available.

The following changes are included in this version:

### Transact and manage

The following APIs are updated to enable Azure subscription cancellations if a customer is compromised (fraud):

- [Azure plan - Manage subscriptions & resources](/partner-center/azure-plan-manage#cancel-an-azure-subscription)
- [Cancel an Azure subscription - Partner Center app developer](/partner-center/develop/cancel-an-azure-subscription)
- [Azure spending - Cancel an Azure entitlement - REST API (Partner Center Rest)](/rest/api/partner-center/azure-spending/cancel-an-azure-entitlement)
- [Get an Azure entitlement for a subscription - Partner Center app developer](/partner-center/develop/get-an-Azure-entitlement-for-a-subscription)
- [Azure spending - Get an Azure entitlement for a subscription - REST API (Partner Center Rest)](/rest/api/partner-center/azure-spending/get-an-azure-entitlement-for-a-subscription)

‘*OperationId*’ is now present in the below API responses:

- [Transition a new commerce subscription - Partner app developer](/partner-center/developer/transition-a-new-commerce-subscription)
- [Gets transition history for a previously transitioned new commerce subscription - Partner app developer](/partner-center/developer/get-transitions)

New GDAP error messages:

- [Transition a subscription - Partner app developer](/partner-center/developer/transition-a-subscription)
- [Transition a new commerce subscription - Partner app developer](/partner-center/developer/transition-a-new-commerce-subscription#get-transition-eligibilities)
- [Get subscription provisioning status - Partner app developer](/partner-center/developer/get-subscription-provisioning-status)

**Audit**

New resource type ‘*AzureEntitlement*’ and ‘*IndirectProviderIndirectResellerDap*’ was added for the following:

- [Auditing resources](/partner-center/developer/auditing-resources)
- [Dotnet Latest](/dotnet/api/microsoft.store.partnercenter.models.auditing.resourcetype?view=partnercenter-dotnet-latest&preserve-view=true)


## Version 3.2.0

[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter) v3.2.0 is now general availability. Updated GitHub samples are also available.

The following changes are included in this version:

To leverage .NET SDK v 3.2.0, partners will need to have [Newtonsoft.Json 13.0.1](https://www.nuget.org/packages/Newtonsoft.Json/13.0.1) and higher. As the versions prior to v13.0.1 have high vulnerable bugs.

*New APIs Contracts* 

The following API are introduced to support NCE migration schedule:

- [Schedule a new commerce migration](schedule-a-new-commerce-migration.md)
- [Cancel a new commerce migration](cancel-a-new-commerce-migration-schedule.md)
- [Update a new commerce migration](update-a-new-commerce-migration-schedule.md)
- [Get a new commerce migration](get-a-new-commerce-migration-schedule.md)

*Updates to the API contract*

- Qualifications API - Updated public contract with three additional fields, “EducationSegment”, “Website”, “ValidationCode”
    [Update a customer's qualifications](update-customer-qualification-asynchronous.md#request-body)

- Validation status -The “lastUpdateDatetime” is changed from DateTime to String
    [Retrieve validation status of a customer](retrieve-validation-status.md#response-fields)

- Self Serve Policy - New value “AzureSavingsPlan” supported for Resource under Permission object [Create a self-serve policy](create-a-self-serve-policy.md#c)

- Migration - Introduced “customTermEndDate” field [Create a new commerce migration](create-migration.md)

- Subscription resource -New "BillingCycleEndDate" attribute added
    [Subscription resources](subscription-resources.md)

- Added new error type “NoPromotionsAvailableEligibilityError” and added
    “AvailableSeats” property to the “SeatCountPromotionEligibilityError” [Verify a promotion eligibility](verify-promotion-eligibility.md)

## Version 3.1.2

[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/3.1.2) v3.1.2 is now general availability. Updated GitHub samples are also available. The following changes are included in this version:

_Updates to the public contract_

Added the `AddOnMigrations` field to the `NewCommerceEligibility` object    
[Validate a subscription for migration](validate-subscription-for-migration.md)

## Version 3.1.1

> [!IMPORTANT]
> Version 3.1.0 is deprecated. Do not download .NET SDK v.3.1.0

[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/3.1.1) v3.1.1 is now general availability. Updated [GitHub samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) are also available. The following changes are included in this version:

### Transact and manage

_New field in public contract_

Add promotion ID to scheduled change  
[Manage scheduled changes for new commerce subscriptions](create-scheduled-changes.md)

* `Patch {baseURL}/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}`

New SDK support for subscription status value ‘disabled’.

* [Subscription resource](subscription-resources.md)
* [Subscription lifecycle states](../subscription-lifecycle.md)

Partner Center APIs will start returning new ‘disabled’ states after 90 days from the v3.1.1 SDK release. Partners have 90 days before the API returns ‘disabled’ state to give them time to update their SDKs and comply with change management principles.

_New API Updates_

[Query migrated subscriptions](query-migrated-subscriptions.md) is the API where partners can query all migrated subs for a given input criteria.

* `GET {baseURL}/v1/migrations/newcommerce`

[Get New Commerce migration events](get-migration-events.md) API is used for fetching the details of migration events based on the current subscription ID or migration ID.

* `GET {baseURL}/v1/customers/{customer-tenant-id}/migrations/newcommerce/events`

## Version 3.0.1

[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/3.0.1) v3.0.1 is now general availability. Updated [GitHub samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) are also available. The following changes are included in this version:

### Transact and manage

_New field in public contract_
* `POST {baseURL}/v1/customers/{customer_id}/subscriptions/{subscription_id}/transition` 
* `GET {baseUrl}/v1/customers/{customer_id}/subscriptions/{subscription_id}/transitions`
* `GET/PATCH {baseUrl}/v1/customers/{customer_id}/subscriptions/{subscription_id}`
  * Added `RefundableQuantity` property to the `Subscription` model
  * Added `CustomTermEndDate` property to the `ScheduledNextTermInstructions` model
  * Added `MigratedFromSubscriptionId` property to the `Subscription` model
* `POST {baseUrl}/v1/customers/{customer_tenant_id}/migrations/newcommerce/validate`
  * Added `AddOnMigrations` property to the `NewCommerceMigration` model
* `POST {baseUrl}/v1/customers/{customer_tenant_id}/migrations/newcommerce`
  * Added `AddOnMigrations` property to the `NewCommerceMigration` model
* `GET {baseUrl}/v1/customers/{customer_tenant_id}/migrations/newcommerce/{migration_id}`
  * Added `AddOnMigrations` property to the `NewCommerceMigration` model
* `POST {baseURL}/v1/customers/{customer_id}/carts`
  * Added new `CartErrorCode` enum values 
  * Added new `AdditionalInformation` model to `CartError` model 
  * Added `CustomTermEndDate` property to the `CartLineItem` model
* `GET/PUT {baseURL}/v1/customers/{customer_id}/carts/{cart_id}`
  * Added new `CartErrorCode` enum values
  * Added new `AdditionalInformation` model to `CartError` model
  * Added `CustomTermEndDate` property to the `CartLineItem` model
* `GET/POST {baseURL}/v1/customers/{customer_id}/orders`
  * Added `CustomTermEndDate` property to the `OrderLineItem` model
* `GET/PATCH {baseURL}/v1/customers/{customer_id}/orders/{order_id}` 
  * Added `CustomTermEndDate` property to the `OrderLineItem` model 

### NCE Batch Migration Tool

To facilitate partner needs of efficiently migrating large quantities of subscriptions, we've enabled a Batch Migration (BAM) tool. The BAM tool allows partners to migrate subscriptions into NCE using the following approach: 

- Streamlined open source .NET SDK sample app experience 
- Uses Excel to manage migration edits 
- Simple tool supporting high quality, repeatable, and customizable migration scenarios in batches

You can find detailed instructions on using [the tool here](https://github.com/microsoft/Partner-Center-DotNet-Samples/tree/master/nce-bulk-migration-tool#readme).

### Security  
_New API_ 
- Patch {[baseURL](./partner-center-rest-urls.md)}/v1/customers/{customer-tenant-id}
  - Remove DAP API – To remove DAP set `AllowDelegatedAccess` property to false 

### Audit and webhook
Audit Updated - Added new operation types for “Manage Overage”, “DAP Admin Relationship Terminated By Microsoft” and “Azure Fraud Event Detected”.  

[Auditing resources](./auditing-resources.md)

## Version 3.0.0

[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/3.0.0) v3.0.0 is now general availability. Updated [GitHub samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) are also available. The following changes are included in this version: 

### Common Updates 
Upgrade System.ComponentModel.Annotations to latest 5.0 version to resolve existing compatibility issues. 

### Transact and manage 

_New API_
* `POST {baseUrl}/v1/customers/{customer_tenant_id}/migrations/newcommerce/validate`
* `POST {baseUrl}/v1/customers/{customer_tenant_id}/migrations/newcommerce` 
* `GET {baseUrl}/v1/customers/{customer_tenant_id}/migrations/newcommerce/{migration-id}` 
* `GET  {baseURL}/customers/{customerId}/subscriptions/overage` 

_New field in public contract_ 
* `PATCH {baseURL}/v1/customers/{customer_id}/subscriptions/{subscription_id}` 
* `POST {baseURL}/v1/customers/{customer_id}/subscriptions/{subscription_id}/transition` 
* `GET {baseUrl}/v1/customers/{customer_id}/subscriptions/{subscription_id}/transitions` 
* `POST/PUT {baseURL}/v1/customers/{customer-tenant-id}/cart` 
* `POST {baseURL}/v1/customers/{customer-tenant-id}/orders` 
* `PUT {baseURL}/v1/customers/{customer-id}/carts/{cart-id}` 

### Catalog/Price/Promotion 

_New API_ 
* `POST {baseURL}/v1/customers/{customerId}/promotionEligibilities` 
* `GET {baseURL}/v1/productpromotions/{promotion-id}?country={country-code}` 
* `GET {baseURL}/v1/productpromotions?country={country-code}&segment={segment}` 

_New field in public contract_ 

* `GET {baseURL}/v1/offers/{offer-id}?country={country-code}` 
* `GET {baseURL}/v1/products/{product-id}/skus?country={country-code}&targetSegment={target-segment}` 
* `GET {baseURL}/v1/products/{product-id}/skus/{sku-id}?country={country-code}` 
* `GET {baseURL}/v1/products?country={country}&targetView={targetView}&targetSegment={targetSegment}`   
* `POST {baseURL}/v1/customers/{customer-tenant-id}/products?targetView={targetView}` 
* `GET {baseURL}/v1/products/{product-id}?country={country}` 
* `POST {baseURL}/v1/customers/{customer-tenant-id}/products/{product-id}/skus` 
* `GET {baseURL}/v1/products/{product-id}/skus?country={country-code}&targetSegment={target-segment}` 
* `GET {baseURL}/v1/products/{product-id}/skus/{sku-id}?country={country-code}` 
* `GET {baseURL}/v1/products/{product-id}/skus/{sku-id}/availabilities?country={country-code}&targetSegment={target-segment}` 
* `POST {baseURL}/v1/customers/{customer-tenant-id}/products/{product-id}/skus/{sku-id}` 
* `GET {baseURL}/v1/products/{product-id}/skus/{sku-id}/availabilities/{availability-id}?country={country-code}` 

### Customer 

_New API_ 

* `GET	{baseURL}/v1/customers/{customer-id}/validationStatus?type=account` 

### Audit and webhook  

Audit Updated - Added new operation types for Add SoftwareAttestation  and Add Device and Policy Updates 

[Auditing resources - Partner Center app developer | Microsoft Docs](./auditing-resources.md)

* `GET {baseURL}/v1/products/{product-id}/skus?country={country-code}&targetSegment={target-segment}` 
* `GET {baseURL}/v1/products/{product-id}/skus/{sku-id}?country={country-code}` 
* `GET {baseURL}/v1/products?country={country}&targetView={targetView}&targetSegment={targetSegment}`   
* `POST {baseURL}/v1/customers/{customer-tenant-id}/products?targetView={targetView}` 
* `GET {baseURL}/v1/products/{product-id}?country={country}` 
* `POST {baseURL}/v1/customers/{customer-tenant-id}/products/{product-id}/skus` 
* `GET {baseURL}/v1/products/{product-id}/skus?country={country-code}&targetSegment={target-segment}` 
* `GET {baseURL}/v1/products/{product-id}/skus/{sku-id}?country={country-code}` 
* `GET {baseURL}/v1/products/{product-id}/skus/{sku-id}/availabilities?country={country-code}&targetSegment={target-segment}` 
* `POST {baseURL}/v1/customers/{customer-tenant-id}/products/{product-id}/skus/{sku-id}` 
* `GET {baseURL}/v1/products/{product-id}/skus/{sku-id}/availabilities/{availability-id}?country={country-code}` 
* `PUT  {baseURL}/customers/{customerId}/subscriptions/overage` 
* `GET  {baseURL}/customers/{customerId}/subscriptions/overage` 

## Version 2.0.1

[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/2.0.1) v2.0.1 is now general availability. Updated [GitHub samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) are also available. The following changes are included in this version:

> [!NOTE]
> Some of changes introduced as part of New Commerce Experiences (“NCE”) which are currently available based on invitation only to partners who are part of the M365/D365 new commerce experience technical preview. Partners who are not part of New commerce private preview should not notice impacts and should be backward compatible.

### Common
* Change on the reference to authentication library – The reference is changed from Azure Active Directory Authentication Library ([ADAL](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet)) to Microsoft Authentication Library ([MSAL](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet))

  Following changes should be made to ensure MSAL runs correctly on your application or .NET sample:

  * Add `https://login.microsoftonline.com/common/oauth2/nativeclient` as RedirectUrl for Mobile and desktop applications
  * Add **Domain** into UserAuthentication section in your application configuration file. 

    Domain is the Azure Active Directory domain or tenant ID where the Azure AD application was created

* [Error codes](error-codes.md) – New error code added 
  * 408: Request timeout
  * 504: Gateway timeout 

### Manage billing

* [Invoice line-items](get-invoiceline-items.md) - new attributes added to following APIs:
  * `GET /invoices/{invoice-id}/lineitems?provider={provider}&invoicelineitemtype=billinglineitems`
  * `GET /invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=billinglineitems`

  New attributes: 
  * productQualifiers
  * subscriptionStartDate
  * subscriptionEndDate
  * referenceId
  * creditReasonCode  (Only applicable to NCE)
  * promotionId 


* [Daily rated usage Line-items](get-invoice-billed-consumption-lineitems.md) – new attributes added to following API: 
  * `GET /invoices/{invoice-id}/lineitems?provider=onetime&invoicelineitemtype=usagelineitems`
  
  New attributes: 
  * hasPartnerEarnedCredit (Only applicable to NCE)
  * creditType (Only applicable to NCE)
  * rateOfCredit (Only applicable to NCE)


### Manage orders

* [Subscription Resources](subscription-resources.md) – New property added. 
  * CancellationAllowedUntilDate  - (Only applicable to NCE)

* Transition Resources (Only applicable to NCE) – New property added 
  * FromSubscriptionId

### Manage customer accounts

* [Validate an address](validate-an-address.md) – Response is changed from a Boolean to a new model for API:
  * `POST /validations/address`
  
  New response model: 
  * AddressValidationResponse

* Customer’s qualification synchronous API is deprecated.  


## Version 1.17.0

[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.17.0) v1.17.0 is now general availability. Updated [GitHub samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) are also available. The following changes are included in this version:

* Audit Updated - Added new operation types for knowing when the customer approved and terminated DAP
  * [DapAdminRelationshipApproved](auditing-resources.md)
  * [DapAdminRelationshipTerminated](auditing-resources.md)

* Audit Updated – Added new resource and operation types for supporting the customer directory role scenario
  * Resource type "[CustomerDirectoryRole](auditing-resources.md)"
  * Operation types "[AddUserMember](auditing-resources.md)" and "[RemoveUserMember](auditing-resources.md)"

* SDK Updates to Customers Account - Support for following APIs
  * GET /customers/{customer-tenant-id}/directSignedMicrosoftCustomerAgreementStatus
  * GET /customers/{customer-tenant-id}/qualifications 
  * POST /customers/{customer_id}/qualifications?code={validationCode}

* **Following changes introduced as part of New Commerce which are currently available based on invitation only to partners who are part of the M365/D365 new commerce experience technical preview.** Partners who aren't part of New commerce private preview shouldn't notice impacts and should be backward compatible.
  * Catalog Changes:
    * GET /products/{product-id}/skus/{sku-id}
  * Purchase and Manage:
    * GET /customers/{customerId}/subscriptions
    * GET /customers/{customerId}/subscriptions/{subscriptionId}
    * PATCH /customers/{customerId}/subscriptions/{subscriptionId}
    * GET /customers/{customerId}/subscriptions/{subscriptionId}/transitioneligibilities
    * GET /customers/{customerId}/subscriptions/{subscriptionId}/transitions
    * POST /customers/{customerId}/subscriptions/{subscriptionId}/transitions


## Version 1.16.3

[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.16.3) v1.16.3 is now general availability. Updated [GitHub samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) are also available. The following changes are included in this version:

* SelfServePolicies - new functionality added
  * [GetSelfServePolicies](get-a-self-serve-policy-by-id.md)
  * [GetListOfSelfServicePolicies](get-a-list-of-self-serve-policies.md)
  * [CreateSelfServePolicies](create-a-self-serve-policy.md)
  * [UpdateSelfServePolicies](update-a-self-serve-policy.md)
  * [DeleteSelfServePolicies](delete-a-self-serve-policy.md)

* Customers Company Profile
  * Added [OrganizationRegistrationNumber](create-a-customer.md)

* CustomerBillingProfile.DefaultAddress
  * Added MiddleName

## Version 1.16.2

[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.16.2) v1.16.2 is now general availability. Updated [GitHub samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) are also available. The following changes are included in this version:

* Update supported operation types for Audit Record. The newly added ones are:
  * CreateSelfServePolicy
  * UpdateSelfServePolicy
  * DeleteSelfServePolicy
  * RemovePartnerRelationship
  * DeleteTipCustomer
  * CreateRelatedReferral
  * UpdateRelatedReferral

* Service request creation is now deprecated
* Support topics are now deprecated


## Version 1.16.1

[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.16.1) v1.16.1 is now general availability. Updated [GitHub samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) are also available. The following changes are included in this version:

We've migrated the existing Microsoft Partner Center SDK from .NET Framework to .NET Standard 2.0 platform. This will make the SDK compatible with existing applications using .NET Framework 4.6.1 and above. The SDK will support .NET Core 2.0 and above. Check [.NET implementation support](/dotnet/standard/net-standard) before porting it to existing applications.   


## Version 1.15.3
[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.15.3) v1.15.3 is now general availability. Updated REST APIs and [GitHub samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) are also available. The following changes are included in this version:

* Partner Agreement
  * Added the ability for indirect providers to [verify Microsoft Partner Agreement status of indirect resellers](verify-indirect-reseller-mpa-status.md).
* Products
  * The following two interfaces were incorrectly placed under the Microsoft.Store.PartnerCenter.Products namespace. Now, they're located under the Microsoft.Store.PartnerCenter.Customers.Products namespace.
    * ICustomerProductByReservationScope
    * ICustomerSkuByReservationScope
