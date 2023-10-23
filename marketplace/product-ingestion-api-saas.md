---
title: Product Ingestion API for SaaS
description: Learn how the Product Ingestion API, which is a modernized API for the commercial marketplace that unifies all existing APIs, can be used for SaaS.
ms.service: marketplace
ms.subservice: partnercenter-marketplace-publisher
ms.topic: how-to
author: varsha-sarah
ms.author: vavargh
ms.reviewer: karrao
ms.date: 05/10/2023
---
# Product Ingestion API for SaaS

The Product Ingestion API is a modernized API that unifies all existing submission APIs across all commercial marketplace products. Refer to Product Ingestion API for details on how to get started.

This article provides guidance on how to use the APIs specifically for SaaS offer type.

## Retrieve existing resource configurations

Before updating existing resources, it’s important to first retrieve them to ensure that you have their latest configuration. There are several ways to retrieve resources via a GET call. See Method 1, detailed below, to retrieve all resources within a specific product in a single API call.

### Method 1: Resource-tree

`GET resource-tree/<product-durableID>?$version=<schema-version>`

You can retrieve all resource configurations within a specific product by using the "resource-tree" resource type along with the product’s durable ID. The schema version you provide will be used as the max supported version for each of the applicable resources of the requested product.

> [!NOTE]
>If you don’t know the product’s durable ID, you can retrieve the product resource first by using the product’s external ID instead and running `GET product?externalID=<product-externalID>&$version=<product-schema-version>`. This request leverages a query string parameter, which is detailed in Method 3. The response will include the product’s durable ID, which you can use for future requests.

By default, when you run a GET call using the "resource-tree", you get back the draft version of your resources. However, by passing the "targetType" query parameter, you can specify the desired target to retrieve the "preview" or "live" data. In the following example, the GET call returns the configuration of the preview environment for all resources under the product "12345678-abcd-efgh-1234-12345678901".

***Sample GET call***:

`GET https://graph.microsoft.com/rp/product-ingestion/resource-tree/product/12345678-abcd-efgh-1234-12345678901?targetType="preview"&$version=2022-03-01-preview5`

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
        "type": "softwareAsAService",
        "alias": "product_example"
        },
        { 
        "$schema": "https://product-ingestion.azureedge.net/schema/commercial-marketplace-setup/2022-03-01-preview2",
        "id": "commercial-marketplace-setup/12345678-abcd-efgh-1234-12345678901",
        "product": "product/12345678-abcd-efgh-1234-12345678901",
        "sellThroughMicrosoft": true,
        "useMicrosoftLicenseManagementService": false
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

## Resource lifecycle states

There are different actions you can take that map to a resource’s lifecycle state. Not all resources have a lifecycle state and not all lifecycle states are supported by all resources. To discover if a resource has a lifecycle state and which values are supported, you can check the resource schema for the existence of the property "lifecycleState". Following are some examples to set the Resource lifecycle state for SaaS offer type.

### Deprecated

Deprecation removes the resource from the commercial marketplace. To deprecate, set the "lifecycleState" property to "deprecated" on the resources that support it. Various levels of deprecation are supported depending on the product type. For example, in the case of SaaS products, you can deprecate plans, or the entire product. When deprecating plans the "lifecycleState" must be changed and the changes must then be published to preview then live for the deprecation to take effect. This is different from a product level deprecation in which setting this automatically kicks off the deprecation in the live environment. To later restore a deprecated resource, refer to the "generallyAvailable" lifecycle state.

***Plan deprecation sample request***:

In the following example, a plan within a SaaS product is set to deprecate. Remember that to apply this change, you can later publish using the submission resource.

`POST https://graph.microsoft.com/rp/product-ingestion/configure?$version=2022-03-01-preview2`

```json
    {
        "$schema": "https://product-ingestion.azureedge.net/schema/configure/2022-03-01-preview2"
        "resources": [
        {
        "$schema": "https://product-ingestion.azureedge.net/schema/plan/2022-03-01-preview2",
        "id": "plan/9f8af57f-ab07-461b-8404-50e10e5e80fb/7e70b11f-809e-4c45-ae2f-1fb3ceaca33b",
        "product": "product/9f8af57f-ab07-461b-8404-50e10e5e80fb",
        "identity": { "externalID": "basic" },
        "alias": "basic plan"
        "lifecycleState": "deprecated"
        }
        ]
    }
```

***Product deprecation sample request***:

In the following example, the live submission of the product is set to deprecate, once this change is applied it is automatically published to live to take effect.

`POST https://graph.microsoft.com/rp/product-ingestion/configure?$version=2022-03-01-preview2`

```json
    {
        "$schema": "https://product-ingestion.azureedge.net/schema/configure/2022-03-01-preview2"
        "resources": [
        {
        "$schema": "https://product-ingestion.azureedge.net/schema/submission/2022-03-01-preview2 ",
        "id": "submission/9f8af57f-ab07-461b-8404-50e10e5e80fb/1152921515689848683",
        "product": "product/9f8af57f-ab07-461b-8404-50e10e5e80fb",
        "target": {
            "targetType": "live"
            },
        "lifecycleState": "deprecated"
        }
        ]
    }
```

### Generally available

"generallyAvailable" is the default lifecycle state for all resources. Once a resource is deprecated, you can restore it by changing the "lifecycleState" property back to "generallyAvailable". To restore a deprecated product, you must publish the product once more to preview and then to live.

***Plan restore sample request***:

In the following example, a plan is intended to be restored. To apply this change, you later need to publish all the way to live using the submission resource.

`POST https://graph.microsoft.com/rp/product-ingestion/configure?$version=2022-03-01-preview2`

```json
    {
        "$schema": "https://product-ingestion.azureedge.net/schema/configure/2022-03-01-preview2"
        "resources": [
        {
        "$schema": "https://product-ingestion.azureedge.net/schema/plan/2022-03-01-preview2",
        "id": "plan/9f8af57f-ab07-461b-8404-50e10e5e80fb/7e70b11f-809e-4c45-ae2f-1fb3ceaca33b",
        "product": "product/9f8af57f-ab07-461b-8404-50e10e5e80fb",
        "identity": { "externalID": "basic" },
        "alias": "basic plan"
        "lifecycleState": "generallyAvailable"
        }
        ]
    }
```

## Next steps

- [Product ingestion API for Saas](product-ingestion-api-saas.md)
- [Product ingestion API for transactable containers](product-ingestion-api-transactable-containers.md)
