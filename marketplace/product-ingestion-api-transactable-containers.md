---
title: Product Ingestion API for transactable containers
description: Learn how the Product Ingestion API, which is a modernized API for the commercial marketplace that unifies all existing APIs, can be used for transactable containers.
ms.service: marketplace
ms.subservice: partnercenter-marketplace-publisher
ms.topic: how-to
author: AarathiN
ms.author: aarathin
ms.reviewer: vavargh
ms.date: 05/10/2023
---
# Product Ingestion API for transactable containers

The Product Ingestion API is a modernized API that unifies all existing submission APIs across all commercial marketplace products. Refer to [Product Ingestion API](product-ingestion-api.md) for details on how to get started.

This article provides guidance on how to use the APIs specifically for containers.

## Retrieve existing resource configurations

Retrieve all resources within a specific product in a single API call.

`GET resource-tree/<product-durableID>?$version=<schema-version>`

You can retrieve all resource configurations within a specific product by using the “resource-tree” resource type along with the product’s durable ID. The schema version you provide is used as the max supported version for each of the applicable resources of the requested product.

> [!NOTE]
> If you don’t know the product’s durable ID, you can retrieve the product resource first by using the product’s external ID instead and running. [Learn more](product-ingestion-api.md#method-1-resource-tree).

***Sample GET call***:

GET <https://graph.microsoft.com/rp/product-ingestion/resource-tree/product/12345678-abcd-efgh-1234-12345678901?targetType="preview"&$version=2022-03-01-preview5>

***Sample response***:

```json
{
  "$schema": "https://product-ingestion.azureedge.net/schema/resource-tree/2022-03-01-preview2",
  "root": "product/12345678-abcd-efgh-1234-12345678901",
  "target": {
    "targetType": "preview"
  },
  "resources": [
  { 
    "$schema": "https://product-ingestion.azureedge.net/schema/product/2022-03-01-preview3",
    "id": "product/12345678-abcd-efgh-1234-12345678901",
    "identity": {
      "externalID": "product_external_id_example"
    },
    "type": "azureContainer",
    "alias": "product_example"
  },
  { 
    "$schema": "https://product-ingestion.azureedge.net/schema/commercial-marketplace-setup/2022-03-01-preview2",
    "id": "commercial-marketplace-setup/12345678-abcd-efgh-1234-12345678901",
    "product": "product/12345678-abcd-efgh-1234-12345678901",
    "sellThroughMicrosoft": true
  },
  {
    "$schema": "https://product-ingestion.azureedge.net/schema/plan/2022-03-01-preview2",
    "id": "plan/12345678-abcd-efgh-1234-12345678901/98756328-04e9-55ae-9403-52b6c971a956
  ...
  }, 
     // The response would include all existing resources within this product.
  {
     ...
  }]
}
```

## Sync private audiences

Updates to private audiences in the draft, preview, and live environments can be performed at the same time without requiring a publish. This can be done by utilizing the “price-and-availability-update-private-audiences” resource and specifying which audiences you want to add or remove from a specific plan. You don't need to provide the submission resource when syncing the private audience.

> [!IMPORTANT]
> If your product supports more than one type of identifier to configure the private audience (for example, both tenant IDs and subscription IDs), you must perform a full publish if providing a new identifier type for the first time. You cannot sync the private audience in this case.

***Sample request to sync the private audience configuration***:

`POST https://graph.microsoft.com/rp/product-ingestion/configure?$version=2022-03-01-preview2`

```json
{
  "$schema": "https://product-ingestion.azureedge.net/schema/configure/2022-03-01-preview2"
  "resources": [
  {
    "$schema": "https://product-ingestion.azureedge.net/schema/price-and-availability-update-private-audiences/2022-03-01-preview3",
    "product": "product/12345678-abcd-efgh-1234-12345678901", // product durable ID
    "plan": "plan/12345678-abcd-efgh-1234-12345678901/7e70b11f-809e-4c45-ae2f-1fb3ceaca33b", //plan durable ID 
    "privateAudiences":
    {
      "add ":
      [
         {
   "type": "tenant",
           "id": " c0cab000-5c00-2ae9-acbe-f5f0bb264498 ",
           "label": "test 1"
         }
      ],
      "remove ":
      [
        {
    "type": "tenant",
           "id": " d1cab000-6c06-4ae9-acbe-b5f0bb264498 ",
           "label": "test 2"
        }
      ]
    }
  }
 ]
}
```

### Configure transactability and Listing options of a container product

Choose whether you want to sell this product through Microsoft. Doing so may improve customer discovery and acquisition. If you set this to true, a set of prerequisite technical configuration is required in your service. If you set this to false, your product is still available in the marketplace as a listing only. This choice can't be changed once your product is published. [Learn more](create-new-saas-offer.md).

***Sample request setting product to transactable***:

`POST https://graph.microsoft.com/rp/product-ingestion/configure?$version=2022-03-01-preview2`

```json
{
  "$schema": "https://product-ingestion.azureedge.net/schema/configure/2022-03-01-preview2"
  "resources": [
   {
      "$schema": "https://product-ingestion.azureedge.net/schema/commercial-marketplace-setup/2022-03-01-preview2",
      "id": "commercial-marketplace-setup/a0c6484f-b4fb-4129-ac6b-35f2b5628089",
      "product": "product/a0c6484f-b4fb-4129-ac6b-35f2b5628089",
      "sellThroughMicrosoft": true
    }
  ]
}
```

***Sample request setting listing option**:

`POST https://graph.microsoft.com/rp/product-ingestion/configure?$version=2022-03-01-preview2`

```json
{
  "$schema": "https://product-ingestion.azureedge.net/schema/configure/2022-03-01-preview2"
  "resources": [
   {
      "$schema": "https://product-ingestion.azureedge.net/schema/commercial-marketplace-setup/2022-03-01-preview2",
      "id": "commercial-marketplace-setup/a0c6484f-b4fb-4129-ac6b-35f2b5628089",
      "product": "product/a0c6484f-b4fb-4129-ac6b-35f2b5628089",
      "sellThroughMicrosoft": false
    }
  ]
}
```

### Configure Properties

Define the categories and industries applicable to your container product, your app version, and legal contracts. Be sure to provide complete and accurate details about your product in the Properties resource, so that it's displayed appropriately and offered to the right set of customers. [Learn more](categories.md#microsoft-appsource-categories-and-subcategories).

***Sample request body configuring properties***:

`POST https://graph.microsoft.com/rp/product-ingestion/configure?$version=2022-03-01-preview2`

```json
{
  "$schema": "https://product-ingestion.azureedge.net/schema/configure/2022-03-01-preview2"
  "resources": [
    {
      "$schema": "https://schema.mp.microsoft.com/schema/property/2022-03-01-preview5",
      "id": "property/a8b48be1-a630-41b5-b5a5-c2a9f7789922/public/main",
      "product": "product/a8b48be1-a630-41b5-b5a5-c2a9f7789922",
      "kind": "azureContainer",
      "termsConditions": "standardMicrosoft",
      "categories": {
        "containers": [
          "container-apps",
   "container-images"
        ]
      }
    }
 ]
}
```

### Configure listing

The information you provide through listing resources is displayed in the Microsoft commercial marketplace online stores. This includes the descriptions of your product, screenshots, and your marketing assets.

***Sample request body configuring listing***:

`POST https://graph.microsoft.com/rp/product-ingestion/configure?$version=2022-03-01-preview2`

```json
{
  "$schema": "https://product-ingestion.azureedge.net/schema/configure/2022-03-01-preview2"
  "resources": [
    {
      "$schema": "https://schema.mp.microsoft.com/schema/listing/2022-03-01-preview5",
      "id": "listing/6d50c7bd-eb19-4d4c-b2f0-beb14aee084b/public/main/default/en-us",
      "product": "product/6d50c7bd-eb19-4d4c-b2f0-beb14aee084b",
      "kind": "azureContainer",
      "title": "ContainerCM0815",
      "description": "<div>This offer is in the early stages of development and not for general public consumption. Use is restricted to a limited audience, and has no commercial purpose beyond the testing for which it is intended.</div>",
      "searchResultSummary": "Container product",
      "shortDescription": "This offer is in the early stages of development and not for general public consumption",
      "privacyPolicyLink": "https://www.company.com/privacy",
      "generalLinks": [
 {
   "displayText": "Product link",
   "link": "https://www.company.com/mkt",
 }
      ],
      "globalSupportWebsite": "https://testprivacyurl.com",
      "governmentSupportWebsite": "https://testprivacyurl.com",
      "supportContact": {
        "name": "Support",
        "email": "support@company.com",
        "phone": "4255555555"
      },
      "engineeringContact": {
        "name": "Engineering",
        "email": "john@company.com",
        "phone": "4255555555"
      },
      "cloudSolutionProviderContact": {
        "name": "CSP",
        "email": "csp@company.com",
        "phone": "4255555555"
      },
      "languageID": "en-us"
    },
    {
      "$schema": "https://schema.mp.microsoft.com/schema/listing-asset/2022-03-01-preview5",
      "product": "product/6d50c7bd-eb19-4d4c-b2f0-beb14aee084b",
      "kind": "azure",
      "listing": "listing/6d50c7bd-eb19-4d4c-b2f0-beb14aee084b/public/main/default/en-us",
      "type": "azureLogoScreenshot",
      "languageID": "en-us",
      "description": "Image caption",
      "displayOrder": 0,
      "fileName": "test.png",
      "friendlyName": "test.png",
      "url": "https://company.com/12345/test.png"
    },
    {
      "$schema":  "https://schema.mp.microsoft.com/schema/listing-asset/2022-03-01-preview5",
      "product": "product/6d50c7bd-eb19-4d4c-b2f0-beb14aee084b",
      "kind": "azure",
      "listing": "listing/6d50c7bd-eb19-4d4c-b2f0-beb14aee084b/public/main/default/en-us",
      "type": "azureLogoLarge",
      "languageID": "en-us",
      "description": "",
      "displayOrder": 0,
      "fileName": "216x216.png",
      "friendlyName": "216x216.png",
      "url": "https://company.com/12345/216x216.png"
    },
    {
      "$schema": "https://schema.mp.microsoft.com/schema/listing-trailer/2022-03-01-preview5",
      "product": "product/6d50c7bd-eb19-4d4c-b2f0-beb14aee084b",
      "kind": "azure",
      "listing": "listing/6d50c7bd-eb19-4d4c-b2f0-beb14aee084b/public/main/default/en-us",
      "streamingUrl": "https://www.youtube.com/watch?v=123",
      "assets": {
        "en-us": {
          "title": "Video",
          "imageList": [
            {
              "url": "https://company.com/12345/trailer.png"
            }
          ]
        }
      }
    }
  ]
}
```

### Configure preview audience

If your container product sells through the Microsoft marketplace, you need to define a preview audience, via subscription IDs, who can review your product listing before it goes live.

***Sample request body configuring preview audience***:

`POST https://graph.microsoft.com/rp/product-ingestion/configure?$version=2022-03-01-preview2`

```json
{
  "$schema": "https://product-ingestion.azureedge.net/schema/configure/2022-03-01-preview2"
  "resources": [
    {
      "$schema": "https://product-ingestion.azureedge.net/schema/price-and-availability-offer/2022-03-01-preview3",
     "id": "price-and-availability-offer/a8b48be1-a630-41b5-b5a5-c2a9f7789922",
     "product": "product/a8b48be1-a630-41b5-b5a5-c2a9f7789922",
     "previewAudiences": [
       {
        "type": "subscription",
        "id": "c2d12fa0-c012-33b0-b0a0-c0a0a0011222",
        "label": "Test Subscription"
       }
     ]
    }
  ]
}
```

### Configure a plan

If you’re creating a listing-only container, when you create a plan you can configure the Azure regions in which your plan should be available. All plans for container offers are automatically made available in the Azure Global region. You may also make your plan available to customers in the Azure Government region. [Learn more](azure-container-plan-setup.md).

> [!NOTE]
> Transactable containers only support the Azure Global region.

***Sample request body configuring listing-only plan with government region***:

`POST https://graph.microsoft.com/rp/product-ingestion/configure?$version=2022-03-01-preview2`

```json
{
    "$schema": "https://product-ingestion.azureedge.net/schema/plan/2022-03-01-preview2", 
    "alias": "my new plan",
    "identity": {"externalID": "myPlanName123"},
    "azureGovernmentCertifications": [
        {
          "name": "Documentation",
          "link": "https://www.company.com/gov"
        }
      ],
      "azureRegions": [
        "azureGovernment",
        "azureGlobal"
      ],
     "product": "product/a8b48be1-a630-41b5-b5a5-c2a9f7789922",
}
```

#### Configure a plan - technical configuration

If you’re creating a listing-only container, provide reference information for your container image repository inside the [Azure Container Registry](/azure/container-registry/container-registry-intro). [Learn more](azure-container-technical-assets.md).

***Sample request body configuring listing-only technical configuration***:

`POST https://graph.microsoft.com/rp/product-ingestion/configure?$version=2022-03-01-preview2`

```json
{
  "$schema": "https://product-ingestion.azureedge.net/schema/configure/2022-03-01-preview2"
  "resources": [
   {
      "$schema": "https://product-ingestion.azureedge.net/schema/container-plan-technical-configuration/2022-03-01-preview3",
      "id": "container-plan-technical-configuration/a8b48be1-a630-41b5-b5a5-c2a9f7789922",
      "product": "product/a8b48be1-a630-41b5-b5a5-c2a9f7789922",
      "plan": "plan/a8b48be1-a630-41b5-b5a5-c2a9f7789922/4db792e6-8e10-439d-9db2-a0e98fa7e174",
      "payloadType": "image",
      "imageRepositoryDetails": {
        "subscriptionID": "537d2130-be25-451e-b3ff-c5b469a13e2d",
        "resourceGroupName": "TestResources",
        "registryName": "testregistry",
        "userName": "testuser",
        "password": "your-password",
        "repositoryName": "listonlycontainerrepo"
      },
      "imageTags": [
        "latest"
      ]
    },
  ]
}
```

If you’re creating a transactable container, provide a cluster extension type name in the format of 'PublisherName.ApplicationName'. The name should be unique across all your offers and plans. You can't modify this value once the plan is published to Preview. [Learn more](azure-container-plan-technical-configuration-kubernetes.md#setting-cluster-extension-type-name).

***Sample request body configuring transactable technical configuration***:

`POST https://graph.microsoft.com/rp/product-ingestion/configure?$version=2022-03-01-preview2`

```json
{
  "$schema": "https://product-ingestion.azureedge.net/schema/configure/2022-03-01-preview2"
  "resources": [
   {
      "$schema": "https://product-ingestion.azureedge.net/schema/container-plan-technical-configuration/2022-03-01-preview3",
      "id": "container-plan-technical-configuration/a8b48be1-a630-41b5-b5a5-c2a9f7789922",
      "product": "product/a8b48be1-a630-41b5-b5a5-c2a9f7789922",
      "plan": "plan/a8b48be1-a630-41b5-b5a5-c2a9f7789922/4db792e6-8e10-439d-9db2-a0e98fa7e174",
      "payloadType": " cnab",
      "clusterExtensionType": " unique.extension.type",
      "cnabReferences": [
 {
          "tenantID": "421c00000-ac12-451e-b3ff-c5b469a13e2d",
          "subscriptionID": "537d2130-be25-451e-b3ff-c5b469a13e2d",
          "resourceGroupName": "TestResources",
          "registryName": "testregistry",
          "repositoryName": "containerrepo",
   "tag": "1.0.4",
          "digest": "sha256:000193bfefde1e9"
        },
      ]
    },
  ]
}
```

#### Configure a plan - price and availability

Configuration for a plan price and availability can differ depending on if the product is set as listing only or configured to sell through Microsoft.

For listing-only containers, you can only determine whether the plan is visible in the marketplace or hidden.

***Sample request body configuring a hidden plan***:

`POST https://graph.microsoft.com/rp/product-ingestion/configure?$version=2022-03-01-preview2`

```json
{
  "$schema": "https://product-ingestion.azureedge.net/schema/configure/2022-03-01-preview2"
  "resources": [
  {
      "$schema": "https://schema.mp.microsoft.com/schema/price-and-availability-plan/2022-03-01-preview4",
      "product": "product/a8b48be1-a630-41b5-b5a5-c2a9f7789922",
      "plan": "plan/a8b48be1-a630-41b5-b5a5-c2a9f7789922/0abbe45b-c405-4c08-bb14-ec485002084e",
      "visibility": "hidden",
      "audience": "public"
    }
  ]
}
```

Transactable container offers support various billing options. To learn more about the supported billing models, see [Licensing options](marketplace-containers.md#licensing-options).

## Next steps

- [Product ingestion API](product-ingestion-api.md)
- [Product ingestion API for Saas](product-ingestion-api-saas.md)
