---
title: Partner Center REST API change log
description: This page lists changes in the Partner Center REST APIs
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: JulCsc
ms.author: raormeni
ms.date: 10/13/2022
---

# Recent changes to Partner Center REST APIs

This article summarizes changes made to the Partner Center REST APIs.

## November 2022

|Feature area                     |Change type                    |API/objects                                                       |
|:--------------------------------|:------------------------------|:-----------------------------------------------------------------|
| NCE Migration                   | Partners can now schedule migrations using the API’s, UX and BAM tool. For more see [November announcements](../announcements/2022-november.md#18). | [Schedule a new commerce migration](schedule-a-new-commerce-migration.md)</br></br> [Cancel a new commerce migration](cancel-a-new-commerce-migration-schedule.md)</br></br> [Update a new commerce migration](update-a-new-commerce-migration-schedule.md)</br></br> [Get a new commerce migration](get-a-new-commerce-migration-schedule.md)</br></br> [New commerce experience batch migration tool](/samples/microsoft/partner-center-dotnet-samples/new-commerce-experience-batch-migration-tool-bam/) |


## October 2022

API changes support new capabilities and add fields benefitOrderId, benefitId, and benefitType to billed and unbilled daily rated usage data.

|Feature area                     |Change type                    |API/objects                                                       |
|:--------------------------------|:------------------------------|:-----------------------------------------------------------------|
| Self-serve policy enhancement   | New self-serve policy support for Azure savings plan. | [Create self-serve policy](create-a-self-serve-policy.md) [Get list of self-serve poliies](get-a-list-of-self-serve-policies.md) [Get a self-serve policy](get-a-self-serve-policy-by-id.md) [Self-serve policy resource](self-serve-policy-resources.md) [Update a self-serve policy](update-a-self-serve-policy.md) |
| Billed Daily Rated Usage Data   | Add fields benefitOrderId, benefitId, and benefitType to billed daily rated usage API. | [Get invoice billed commercial consumption line items](get-invoice-billed-consumption-lineitems.md) |
| Unbilled Daily Rated Usage Data | Add fields benefitOrderId, benefitId, and benefitType to unbilled daily rated usage API. | [Get invoice unbilled commercial consumption line items](get-invoice-unbilled-consumption-lineitems.md) |


## September 2022

PI changes to add fields firstObserved and lastObserved to Fraud events.

|Feature area|Change type|API/objects|
|:--------------------------------|:------------------------------|:-----------------------------------------------------------------|
| NCE Migration            | CustomTermEndDate is added to the Migration API | [Create a new commerce migration](create-migration.md) |
| Azure fraud notification | Add firstObserved and lastObserved fields to fraud events | [Get fraud events](get-fraud-events.md)|

## July 2022

API changes support new capabilities.

|Feature area|Change type|API/objects|
|:--------------------------------|:------------------------------|:-----------------------------------------------------------------|
| Scheduled changes with promotion | Expose promotion ID if scheduled change aligns to available promotion. | [Create scheduled changes](create-scheduled-changes.md)|

## June 2022

API changes support partners with NCE Migration.

|Feature area|Change type|API/objects|
|:--------------------------------|:------------------------------|:-----------------------------------------------------------------|
| Validate Migration | New API to validate a subscription for migration to New Commerce Experience | [Validate a subscription for migration](validate-subscription-for-migration.md)|
| Create a new migration | New API to create a migration of a subscription to New Commerce Experience | [Create a new commerce migration](create-migration.md) |
| Get a new commerce subscription migration | New API to get a migration of a subscription to New Commerce Experience in order to check migration status | [Get a new commerce subscription migration](get-new-commerce-migration.md)

## May 2022

API changes support partners to monitor DAP and remove inactive DAPs.

|Feature area|Change type|API/objects|
|:--------------------------------|:------------------------------|:-----------------------------------------------------------------|
| DAP removal | Remove a delegated admin (DAP) relationship with a customer that you no longer need to manage.| [Remove a DAP relationship with a customer](remove-dap.md)
| List Delegated Admin Relationships | New API to return a list of all customers of a partner, also indicating if customers have a DAP / non-DAP relationship | [List Delegated Admin customers](list-delegated-admin-customers.md)
| Get Delegated Admin statistics | Returns information on the count of delegated admin (DAP) relationships established or active that are associated to a partner across all their customers. | [Get Delegated Admin statistics](get-delegated-admin-relation-statistics.md)


## March 2022

March changes include enhancements to support [New commerce license-based](/partner-center/develop/purchase-new-commerce-license-based) features.

|Feature area|Change type|API/objects|
|:--------------------------------|:------------------------------|:-----------------------------------------------------------------|
| DAP removal | Remove a delegated admin (DAP) relationship with a customer that you no longer need to manage. | [Remove a DAP relationship with a customer](/partner-center/develop/remove-dap) |
|New commerce cart | Added availableQuantity for CartLineItem response |[Promotions resource](/partner-center/develop/cart-resources#additionalinformation)|
|New commerce transition | Added promotionId to transition response |[Transitions resource](/partner-center/develop/transition-resources#transition)|

## December 2021

December changes include enhancements to support [New commerce license-based](/partner-center/develop/purchase-new-commerce-license-based) features.

|Feature area|Change type|API/objects|
|:--------------------------------|:------------------------------|:-----------------------------------------------------------------|
|New commerce promotions|Added availableSeats to seatcounts |[Promotions resource](/partner-center/develop/promotion-resources)|
|New commerce promotions|Added availableSeats to seatcounts |[POST {baseURL}/v1/customers/{customerId}/promotionEligibilities](/partner-center/develop/verify-promotion-eligibility)|
|Azure fraud notification|  New API | [Get fraud events](get-fraud-events.md)
|Azure fraud notification|  New API | [Update fraud events status](update-fraud-events-status.md)
|New commerce subscriptions| Added refundableQuantity to Get Subscription by ID API | [GET Subscription By ID](get-a-subscription-by-id.md)

## October 2021

Changes for October are to support [New commerce license-based](/partner-center/develop/purchase-new-commerce-license-based) features and the new [ISV margin discounts for CSPs](../csp-commercial-marketplace-margins.md).

|Feature area|Change type|API/objects|
|:--------------------------------|:------------------------------|:-----------------------------------------------------------------|
|New commerce subscription management|New field in public contract|[PATCH {baseURL}/v1/customers/{customer_id}/subscriptions/{subscription_id}](/partner-center/develop/get-a-subscription-by-id)|
|New commerce upgrades and trial conversions|New field in public contract|[POST {baseURL}/v1/customers/{customer_id}/subscriptions/{subscription_id}/transition](/partner-center/develop/transition-a-subscription)|
|New commerce transitions|New field in public contract|[GET {baseUrl}/v1/customers/{customer_id}/subscriptions/{subscription_id}/transitions](/partner-center/develop/transition-a-subscription)|
|Migrating to new commerce|New API|[POST {baseUrl}/v1/customers/{customer_tenant_id}/migrations/newcommerce/validate](/partner-center/develop/validate-subscription-for-migration)|
|Migrating to new commerce|New API|[POST {baseUrl}/v1/customers/{customer_tenant_id}/migrations/newcommerce](/partner-center/develop/create-migration)|
|Migrating to new commerce|New API|[GET {baseUrl}/v1/customers/{customer_tenant_id}/migrations/newcommerce/{migration-id}](/partner-center/develop/get-new-commerce-migration)|
|Purchasing new commerce|New field in public contract|[POST {baseURL}/v1/customers/{customer-id}/orders"](/partner-center/develop/create-an-order-for-a-customer-of-an-indirect-reseller)|
|Purchasing new commerce|New field in public contract|[POST{baseURL}/v1/customers/{customer-id}/carts ](/partner-center/develop/create-a-cart)|
|Purchasing new commerce|New field in public contract|[PUT{baseURL}/v1/customers/{customer-id}/carts/{cart-id}](/partner-center/develop/update-a-cart)|
|New commerce promotions|New API|[POST {baseURL}/v1/customers/{customerId}/promotionEligibilities](/partner-center/develop/verify-promotion-eligibility)|
|New commerce promotions|New API|[GET {baseURL}/v1/productpromotions/{promotion-id}?country={country-code}](/partner-center/develop/get-promotion-by-id)|
|New commerce promotions|New API|[GET {baseURL}/v1/productpromotions?country={country-code}&segment={segment}](/partner-center/develop/get-promotions)|
|New commerce promotions|New resource|[Promotions resource](/partner-center/develop/promotion-resources)|
|Catalog updates for new commerce|New field in public contract|[GET {baseURL}/v1/products?country={country}&targetView={targetView}&targetSegment={targetSegment}  ](/partner-center/develop/get-a-list-of-products)|
|Catalog updates for new commerce|New field in public contract|[POST {baseURL}/v1/customers/{customer-tenant-id}/products?targetView={targetView}](/partner-center/develop/get-a-list-of-products-by-customer)|
|Catalog updates for new commerce|New field in public contract|[GET {baseURL}/v1/products/{product-id}?country={country}](/partner-center/develop/get-a-list-of-products)|
|Catalog updates for new commerce|New field in public contract|[POST {baseURL}/v1/customers/{customer-tenant-id}/products/{product-id}/skus](/partner-center/develop/get-a-list-of-skus-for-a-product-by-customer)|
|Catalog updates for new commerce|New field in public contract|[GET {baseURL}/v1/products/{product-id}/skus?country={country-code}&targetSegment={target-segment}](/partner-center/develop/get-a-list-of-skus-for-a-product)|
|Catalog updates for new commerce|New field in public contract|[GET {baseURL}/v1/products/{product-id}/skus/{sku-id}?country={country-code}](/partner-center/develop/get-a-sku-by-id)|
|Catalog updates for new commerce|New field in public contract|[GET {baseURL}/v1/products/{product-id}/skus/{sku-id}/availabilities?country={country-code}&targetSegment={target-segment}](/partner-center/develop/get-a-list-of-availabilities-for-a-sku)|
|Catalog updates for new commerce|New field in public contract|[POST {baseURL}/v1/customers/{customer-tenant-id}/products/{product-id}/skus/{sku-id}](/partner-center/develop/get-a-list-of-skus-for-a-product-by-customer)|
|Catalog updates for new commerce|New field in public contract|[GET {baseURL}/v1/products/{product-id}/skus/{sku-id}/availabilities/{availability-id}?country={country-code}](/partner-center/develop/get-a-list-of-availabilities-for-a-sku)|
|Catalog updates for new commerce|New field in public contract|[Product resources](/partner-center/develop/product-resources)|
|ISV margin discounts for CSPs|New resource|[Margin resource](/partner-center/develop/margin-resources)|
|ISV margin discounts for CSPs|New API|[GET {baseURL}/v1/margins](/partner-center/develop/get-margins)|
|ISV margin discounts for CSPs|New API|[GET {baseURL}/v1/margins/download](/partner-center/develop/download-margins)|
|Telco pay-as-you-go in new commerce|New API|[PUT  {baseURL}/customers/{customerId}/subscriptions/overage](/partner-center/develop/update-subscription-overage)|
|Telco pay-as-you-go in new commerce|New API|[GET  {baseURL}/customers/{customerId}/subscriptions/overage ](/partner-center/develop/get-subscription-overage)|
|Telco pay-as-you-go in new commerce|New field in public contract|[Add ConsumptionType to Sku model](/partner-center/develop/product-resources#sku)|

## July 2021

Changes for July were to support [Windows 365 attestation](../pricing-and-offers.md#offer-attestation) required for some Windows 365 SKUs only.

|Feature area             |Change type|API/objects|
|:------------------------|:------------------------------|:---------------------------------------------------------------------------------------------------------|
|Windows 365 Attestation  |New field in public contract   |[Sku resource](/partner-center/develop/product-resources#sku)|
|Windows 365 Attestation  |New field in public contract   |[Offer resource](/partner-center/develop/offer-resources)|
|Windows 365 Attestation  |New field in public contract   |[Cart line item resource](/partner-center/develop/cart-resources#cartlineitem)|
|Windows 365 Attestation  |New field in public contract   |[GET {baseURL}/v1/products/{product-id}/skus?country={country-code}&targetSegment={target-segment}](/partner-center/develop/get-a-list-of-skus-for-a-product)|
|Windows 365 Attestation  |New field in public contract   |[GET {baseURL}/v1/products/{product-id}/skus/{sku-id}?country={country-code}](/partner-center/develop/get-a-list-of-skus-for-a-product)|
|Windows 365 Attestation  |New field in public contract   |[PUT {baseURL}/v1/customers/{customer-id}/carts/{cart-id} HTTP/1.1](/partner-center/develop/create-a-cart)|

## December 2020

Two new GET and POST Qualifications APIs introduced. The new APIs will be using Qualifications, not Qualification. The APIs will be available for testing in FY21 Q2.

| Feature area | Change type | API/objects |
|:------------------------|:------------------|:-----------------------------------------------------------------|
| Customer qualification | New API | [GET {baseURL}/v1/customers/{customer-tenant-id}/qualifications](/partner-center/develop/get-customer-qualification-asynchronous) |
| Customer qualification | New API | [POST {baseURL}/v1/customers/{customer_id}/qualifications?code={validationCode}](/partner-center/develop/update-customer-qualification-asynchronous) |


### What has changed?

Currently, the Partner Center API has GET and PUT qualifications to verify Education customers’ eligibility. There will be no changes to the GET Qualification API. However, we’ve added a return case to the PUT Qualification API.

- GET - doesn't change.
- PUT - return case will be added.

These APIs will be retired at the end of February 2021, to be replaced by new APIs as described below.

### Scenarios impacted:

Customer eligibility for education pricing on select SKUs

### Detail descriptions

Two new GET and POST Qualifications APIs will be introduced. The new APIs will be using **Qualifications**, not **Qualification**. The APIs will be available for testing in FY21 Q2.

#### GET Qualifications

```http
GET {customer_id}/qualifications
```

#### Response example:

```json
{
  "Qualification": "Education",
  "VettingStatus": "Denied",
  "VettingReason": "Not an education customer",
  "VettingCreatedDate": "07/09/2020: 00:00:00" //UTC
}
```

#### Response fields: 

- VettingStatus values: Approved, Denied, InReview, etc.

- VettingReason values:
   - Not an Education Customer
   - No longer an Education Customer
   - Not an Education Customer - After Review
   - Restricted being an Education Customer
   - Not an Academic Domain
   - Not an eligible Library
   - Not an eligible Museum
 
#### POST Qualifications

```http
POST {customer_id}/qualifications
    [
            "Qualification": "Education"
    ]
```

#### Response example:

```JSON
{
  "Qualification": "Education",
  "VettingStatus": "InReview",
  "VettingCreatedDate": "07/09/2020: 00:00:00" //UTC
}
```

## Next steps

[Partner Center REST API reference](partner-center-rest-api-reference.md)