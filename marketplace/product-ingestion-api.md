---
title: Product Ingestion API for the commercial marketplace
description: The Product Ingestion API is a modernized API for the commercial marketplace that unifies all existing APIs.
ms.service: marketplace
ms.subservice: partnercenter-marketplace-publisher
ms.topic: how-to
author: varsha-sarah
ms.author: vavargh
ms.reviewer: karrao
ms.date: 05/10/2023
---
# Product Ingestion API for the commercial marketplace

The Product Ingestion API is a modernized API that unifies all existing submission APIs across all commercial marketplace products. The API lets you create, publish and manage resources associated with products and plans within your Partner Center account. It uses a declarative pattern to submit requests, in which the desired state is indicated as opposed to specifying the individual steps to reach the desired state.

This article provides guidance on how to get started with the APIs for any commercial marketplace offer type. The Product Ingestion API is currently supported for [SaaS](product-ingestion-api-saas.md), [VMs](product-ingestion-api-vm.md), [Private offers](private-offers-api.md), and [container offer types](product-ingestion-api-transactable-containers.md) and is in preview. For guidance specific to your offer, review [API guidance per offer type](#api-guidance-per-product-type).

[!INCLUDE [Important - Azure AD Graph is deprecated](../developer/includes/azure-ad-graph-notice.md)]

## Getting started

The Product Ingestion API can be accessed using the [MSGraph API](/graph/overview) under the workload name *"product-ingestion*". The base URL is `https://graph.microsoft.com/rp/product-ingestion`.

To use the Product Ingestion API, you need to first acquire the following prerequisites:

- An Azure Active Directory (Azure AD) and ensure that you have Global administrator permissions for the directory
- An Azure AD application
- An Azure AD access token

Follow these [onboarding instructions](submission-api-onboard.md) to get started. After this has been set up once, you can obtain an Azure AD access token to call the APIs with the Authorization header for each API method.

## Concepts

Before you get started, you need to understand some basic concepts.

### Resources

The API is structured around resource types, where each type is described using a dedicated schema definition as referenced by the "*$schema*" property. The schema consists of the configuration properties of that resource. Resources are fundamental in creating and updating the configuration of various aspects of a given product. For a full list of resource types and their schemas, see the [Resource API reference](#resource-api-reference).

### Durable ID

A *durable ID* is a system generated global identifier used to uniquely identify any resource. Every resource has an associated "*ID*" property, which when combined with the resource type name, makes up a resource's durable ID. The durable ID is used when referencing resources to either retrieve or modify.

***Format***:

`\<resource-type>/\<id>`

***Example***:

```json
        { 
            "$schema": "https://product-ingestion.azureedge.net/schema/product/2022-03-01-preview3",
            "id": "product/12345678-abcd-efgh-1234-12345678901", // durable ID
            "identity": {
              "externalID": "ds-contoso-image-resize-demo"
            },
            "type": "softwareAsAService", // Product types that can be specified include azureContainer, azureVirtualMachine, softwareAsAService 
            "alias": "Contoso Image Resizing Service"
        }
```

### External ID

An *external ID* is another unique identifier that can be used to reference specific products or plans. This is an alternative way to reference these resources instead of using the durable ID. The external ID of a product translates to its "*offerID*" and the external ID of a plan translates to its "*planID*", as defined upon creation under the "*identity*" property.

Example:

```json
            { 
                "$schema": "https://product-ingestion.azureedge.net/schema/plan/2022-03-01-preview2",
                "id": "plan/12345678-abcd-efgh-1234-12345678901/4e0bfefa-b993-4b79-a426-871c3bf236a5",
                "identity": {
                  "externalID": "gold-annual"
                },
                "azureRegions": [
                    "azureGlobal"
                  ],
                "alias": "Gold - Annual payment",
                "product": "product/12345678-abcd-efgh-1234-12345678901",
            }
```

### API Methods

There are four management APIs that can be used to perform different actions, such as querying existing resources, making configuration updates, and checking the status of a request.

> [!NOTE]
> All requests require you to set the schema version ($version [query parameter](#querying-your-submissions)) you desire as part of the response.

| **API type** | **Description** | **HTTP method and path** |
|---|---|---|
| [**Query**](#retrieve-existing-resource-configurations) | Retrieves existing resources by:<br>-Method 1: "*resource-tree*" resource type<br>-Method 2: the durable-id<br>-Method 3: query string parameters | -Method 1: `GET resource-tree/<product-durableID>`<br>-Method 2: `GET <resource-durableID>`<br>-Method 3: `GET <resourceType>?<query parameters>` |
| [**Configure submit**](#configuration-requests) | Submits requests to create or update one or more resources. Upon successful processing, a jobID is returned, which can be used to retrieve the status of the request. This API type can be used to update the draft state and publish changes, sync private audiences, and modify the resource lifecycle state. | `POST configure` |
| [**Configure status**](#status-of-a-pending-request) | Retrieves the status of a pending request via the jobID. | `GET configure/<jobID>/status` |
| [**Configure status details**](#summary-of-a-completed-request) | Retrieves a detailed summary of a completed request, including the updated resources, via the jobID. | `GET configure/<jobID>` |
| [**Cancel Configure**](#cancel-a-configuration-request) | Cancels the specified Configure job. | `POST configure/<jobID>/cancel`|

## A typical workflow

To update an existing resource, a typical workflow would be to:

1. Retrieve an existing resource configuration (API type: [*Query  via resource-tree*](#retrieve-existing-resource-configurations))*
1. Make any necessary updates and then submit a configuration request (API type: [*Configure submit*](#configuration-requests))
1. Check the status of the request (API type: [*Configure status*](#status-of-a-pending-request) and [*Configure status details*](#summary-of-a-completed-request))

`*` This same workflow can be applied when creating new resources, but instead of retrieving resources (Step 1), use the [Resource API reference](#resource-api-reference) table to ensure that you're using the current schema for the resource type that you're creating.

To summarize, this image shows the typical calling pattern used to submit a configuration request, regardless of whether you're creating a new or modifying an existing resource.

:::image type="content" source="./media/product-ingestion-api/product-ingestion-api-workflow.png" alt-text="Screenshot illustrating the typical calling pattern used to submit a configuration request.":::

> [!NOTE]
> Be sure to review any additional prerequisites specific to the offer type you're managing by referring to the [**API guidance per offer type**](#api-guidance-per-product-type) section.

## Retrieve existing resource configurations

Before updating existing resources, it's important to first retrieve them to ensure that you have their latest configuration. There are several ways to retrieve resources via a GET call. See Method 1, detailed below, to retrieve all resources within a specific product in a single API call.

### Method 1: Resource-tree

`Schema: https://product-ingestion.azureedge.net/schema/resource-tree/2022-03-01-preview2`

`GET resource-tree/<product-durableID>?$version=<schema-version>`

You can retrieve all resource configurations within a specific product by using the "*resource-tree*" resource type along with the product's durable ID.

The latest schema version available can be different for each resource. When performing a resource-tree request, the schema version specified dictates which version is returned for each resource in the product. The version specified serves as a "max" version limit in that it returns the latest schema version available for all resources of equal or lower version.  For example, if the latest plan listing version available is "2022-03-01-preview3", the response will surface this version if you were to specify "2022-03-01-preview5" in the resource-tree GET request. However, if requesting "2022-03-01-preview2" as the resource-tree version, this will return the "2022-03-01-preview2" plan listing resource even though the latest version available is "2022-03-01-preview3". It's recommended to use the latest available version of each resource to ensure you're using updated schema with newly supported features.

> [!NOTE]
> If you don't know the product's durable ID, you can use  the product's [external ID](#external-id) to retrieve the product resource by running  `GET product?externalID=<product-externalID>&$version=<product-schema-version>`. This request leverages a query string parameter, which is detailed in method 3 below. The response will include the product's durable ID, which you can use for future requests.

By default, when you run a GET call using the "*resource-tree*", you get back the draft version of your resources. However, by passing the "*targetType*" query parameter, you can specify the desired target to retrieve the "*preview*" or "*live*" data. In the following example, the GET call returns the configuration of the preview environment for all resources under the product "12345678-abcd-efgh-1234-12345678901".

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
              "externalID": "ds-contoso-image-resize-demo"
            },
            "type": "softwareAsAService",
            "alias": "Contoso Image Resizing Service"
          },
          { 
            "$schema": "https://product-ingestion.azureedge.net/schema/property/2022-03-01-preview3",
            "id": "property/12345678-abcd-efgh-1234-12345678901/public/main",
            "product": "product/12345678-abcd-efgh-1234-12345678901",
            "kind": "azureSaaS",
            "termsConditions": "false",
            "categories": {
          "developer-tools-saas": [
            "devService"
          ]
            }
          },
          {
            "$schema": "https://product-ingestion.azureedge.net/schema/plan/2022-03-01-preview2",
            "id": "plan/12345678-abcd-efgh-1234-12345678901/4e0bfefa-b993-4b79-a426-871c3bf236a5",
            "product": "product/071b135e-9faf-4ff7-b113-a3f25bb0f468",
          ...
          }, 
              // The response would include all existing resources within this product.
          {
              ...
          }]
        }
```

### Method 2: Durable ID

`GET <resource-durableID>?$version=<schema-version>`

Retrieve a specific resource by using its [durable ID](#durable-id). Once a resource is created, the durable ID always remains the same and can be used to retrieve the latest draft changes of that resource by calling the GET method. For example, the following request will return the draft configuration of this specific product using the "2022-03-01-preview3" schema version.

`GET product/12345678-abcd-efgh-1234-12345678901?$version=2022-03-01-preview3`

> [!IMPORTANT]
> This method is only used for retrieving the draft configuration. If you would like to retrieve preview or live data, use the "*resource-tree*" method, as detailed above.

To find the durable ID for your resources, you can either:

- Use the ["resource-tree" method](#method-1-resource-tree) to fetch all resources within the product along with each of their respective durable IDs, or
- Retrieve the [details of a completed resource configuration request](#summary-of-a-completed-request), which includes the durable IDs for all resources created or updated as a part of the request.

Remember, the "*ID*" property is the durable-id for the respective resource.

### Method 3: Query string parameters

`GET <resourceType>?<query parameters>&$version=<schema-version>`

This method is used to query certain resource types associated with a specific account. For example, you can retrieve all your products of a specific product type with a single GET call. Query string parameters are used to query details pertaining to your products, plans, or submissions.

This table shows the supported query parameters for each of the supported resource types. Not all resource types support each of the query parameters. Reference this table for the full list of currently supported query strings.

| **Resource type** | **Parameters** | **Query string examples** |
|---|---|---|
| **plan** | product`*`<br>externalID<br>$maxpagesize<br>continuationToken$version`*` | `GET plan?product=<product-durableID>&$version=<schema-version>`<br>`GET plan?product=<product-durableID>&externalID=<plan-externalID>&$version=<schema-version>`<br>`GET plan?product=<product-durableID>&$maxpagesize=<#>&$version=<schema-version>`<br>`GET plan?product=<product-durableID>&continuationToken=<token>&$version=<schema-version>` |
| **product** | externalID<br>type<br>$maxpagesize<br>continuationToken$version`*` | `GET product?externalID=<product-externalID>&$version=<schema-version>`<br>`GET product?type=<product-type>&$version=<schema-version>`<br>`GET product?$maxpagesize=<#>&$version=<schema-version>`<br>`GET product?continuationToken=<token>&$version=<schema-version>` |
| **submission** | targetType<br>$maxpagesize<br>continuationToken$version`*` | `GET submission/<product-durableID>?targetType=<environment>&$version=<schema-version>`<br>`GET submission/<product-id>?$maxpagesize=<#>&continuationToken=<token>&$version=<schema-version>` |
| **resource-tree** | targetType$version`*` | `GET resource-tree/<product-durableID>?targetType=<environment>&$version=<schema-version>` |

`*` The product and $version parameters are always required.

Functionality of each of the supported query parameters:

- *product* – When passing the "*product*" parameter in context of the "*plan*" resource type, it returns all plans within that specific product.
- *externalID* – When passing the "*externalID*" parameter in the context of a product or plan, it returns the configuration of that respective product or plan. Unlike the "*resource-tree*" method, this query string parameter will only return the details of that resource, not all resources within it.
- *type* – When passing the "*type*" parameter in context of the "*product*" resource type, it returns all products of that type associated to your account. For example, by specifying "*type=softwareAsAService*", all of your SaaS products will be returned.
- *targetType* – This returns the data of a specific environment in the context of the resource type that is used. The supported "*targetType*" values are "*draft*", "*preview*", or "*live*".
- *$maxpagesize* – By specifying the maximum page size, in the form of a positive whole number, this parameter is used to limit the results of your search when querying your previous submissions.
- *continuationToken* – This parameter can be used with the "*$maxpagesize*" parameter to query another set of results available in your search. The "*continuationToken*" value is provided in the response of the previous page.
- *$version* – **This is a required parameter for all calls**, it specifies what schema version you want for the response from the request you made. The latest schema version available can be different for each resource and the version specified serves as a "max" version limit. The system returns either the exact schema version if available or the closest version that is older than the requested version. This can help maintain your code working even if there are newer schema changes, but in order to utilize the latest features, it's recommended to use the latest available version of each schema.

#### Querying your submissions

You can retrieve your existing product submissions by doing `GET submission/<product-durableID>`. By default, you get back all your active submissions including the draft reference, but you can additionally query a specific environment using the "*targetType*" query parameter: (`GET submission/<product-durableID>?targetType=<environment>&$version=<version>`).

> [!IMPORTANT]
>Once a "*Preview*" submission is pushed to "*Live*", it replaces any the previous "*Live*" submission. When this happens, the data now represents both "*Preview*" and "*Live*" environments until a new submission is published to "*Preview*".

***Sample request***:

`GET https://graph.microsoft.com/rp/product-ingestion/submission/12345678-abcd-efgh-1234-12345678901?$version=2022-03-01-preview2`

***Sample response***:

This example shows a GET request for the active submissions associated to *product ID* "*12345678-abcd-efgh-1234-12345678901*". The active "*Live*" submission (*submission/12345678-abcd-efgh-1234-12345678901/1152921515689847470*) was published to preview first and then later to live. When this submission was pushed to live on January 25, 2022, it represented both preview and live until a new preview submission (*submission/12345678-abcd-efgh-1234-12345678901/1152921515689848683*) was created on February 4, 2022.

```json
            {
              "value": [
                {
                  "$schema": "https://product-ingestion.azureedge.net/schema/submission/2022-03-01-preview2",
                  "id": "submission/12345678-abcd-efgh-1234-12345688901/0",
                  "product": "product/12345678-abcd-efgh-1234-12345678901",
                  "target": {
                    "targetType": "draft"
                  }
                },
                {
                  "$schema": "https://product-ingestion.azureedge.net/schema/submission/2022-03-01-preview2",
                  "id": "submission/12345678-abcd-efgh-1234-12345678901/1152921515689847470",
                  "product": "product/12345678-abcd-efgh-1234-12345678901",
                  "target": {
                    "targetType": "live"
                  },
                  "status": "completed",
                  "result": "succeeded",
                  "created": "2022-01-25T07:13:06.4408032Z"
                },
                {
                  "$schema": "https://product-ingestion.azureedge.net/schema/submission/2022-03-01-preview2",
                  "id": "submission/12345678-abcd-efgh-1234-12345678901/1152921515689848683",
                  "product": "product/12345678-abcd-efgh-1234-12345678901",
                  "target": {
                    "targetType": "preview"
                  },
                  "status": "completed",
                  "result": "succeeded",
                  "created": "2022-02-04T20:07:22.4220588Z"
                }
              ]
            }
```

## Create new products and resources

You can create new resources, including new products, as part of a single configuration request. By using the [Resource API reference](#resource-api-reference) table, you can retrieve the schema for the resource type you want to create. This ensures that you're using the latest schema and therefore configuring all necessary properties to create the resource.

If you're creating a new product, requirements vary by product type. Therefore, you need to provide different resources. You can reference the corresponding commercial marketplace documentation for the respective product type to ensure that you're configuring the basic requirements in your request. Alternatively, you can make a [configuration request](#configuration-requests) using just the product resource. After creating the product, then call the [configure status details](#status-of-a-pending-request) API to retrieve the created product resource and find its durable ID to call the [resource-tree Query API](#method-1-resource-tree). The response returns the applicable supported resources for the product type you created.

Similarly, to create a new resource within an existing product, you also need to retrieve the latest schema of that specific resource type. Ensure that you provide the dependent resources as part of the configuration request by reviewing the [resource dependencies](#resource-references-and-dependencies).

After constructing your resources using the schemas, learn how to make a [configuration request](#configuration-requests).

## Modify existing products and resources

You can submit updates by using the configure payload. This payload consists of one or more resource types and the "*$schema*" property indicates the resource type being referenced.

> [!TIP]
>We recommend that you first retrieve existing resources before publishing updates to ensure that you are leveraging the latest configuration.

After modifying your resources, learn how to make a [configuration request](#configuration-requests).

## Configuration requests

You can edit and publish in the same payload. To submit a configuration request, use the HTTP POST method of the configure API. The configure payload consists of an array of resources that indicate the desired changes. All edits affect only the draft version until you explicitly submit a submission resource to publish your draft changes. When publishing to preview or live, include the [submission resource](#submission-resource) and specify the target environment. Before submitting a request, you need to know how to reference resources and understand their dependencies.

`Schema:`<https://product-ingestion.azureedge.net/schema/configure/2022-03-01-preview2>

Upon submitting your configuration request, you get back a configure-status object with the jobID that you can use to [track the progress](#status-of-a-pending-request) and [results](#summary-of-a-completed-request) of your request.

`Schema: <https://product-ingestion.azureedge.net/schema/configure-status/2022-03-01-preview2>`

### Resource references and dependencies

#### References

To reference an existing resource in a configure request, provide the resource's "*$schema*" type along with the resource's durable ID. In the case of products and plans, you can also reference these resources via their external ID.

The durable ID can be found in the "*ID*" property, for example if this is the product resource we want to reference in another resource:

```json
            { 
                "$schema": "https://product-ingestion.azureedge.net/schema/product/2022-03-01-preview3",
                "id": "product/12345678-abcd-efgh-1234-12345678901",
                "identity": {
                  "externalID": "ds-contoso-image-resize-demo"
                },
                "type": "softwareAsAService",
                "alias": "Contoso Image Resizing Service"
            }
```

The durable ID would be "**product/071b135e-9faf-4ff7-b113-a3f25bb0f468**".

The durable ID can then be used in the listing resource example below by setting it in the "product" resource schema property like this:

```json
            {
                "$schema": "https://schema.mp.microsoft.com/schema/listing/2022-03-01-preview5", 
                "product": "product/071b135e-9faf-4ff7-b113-a3f25bb0f468", // product durable ID
                  ...
              }
```

The external ID of product and plan resources is defined within the "*identity*" property.

```json
            {
                "$schema": "https://product-ingestion.azureedge.net/schema/plan/2022-03-01-preview2", 
                "alias": "Gold - Annual payment",
                "identity": {"externalID": "gold-annual"},
                "product": "product/071b135e-9faf-4ff7-b113-a3f25bb0f468",
                  ...
              }
```

The plan external ID "gold-annual" can then be referenced by other subsequent resources in the following format:

```json
              {
                "$schema": "https://schema.mp.microsoft.com/schema/plan-listing/2022-03-01-preview5", 
                "product": "product/071b135e-9faf-4ff7-b113-a3f25bb0f468"}
                "plan": {"externalID": "gold-annual"}
                  ...
              }
```

***Sample request***:

In this example, the configure payload is used to create a new SaaS product with an external ID of "***ds-contoso-image-resize-demo***". Upon creation of this product, you can later reference this product using its durable ID or external ID.

`POST https://graph.microsoft.com/rp/product-ingestion/configure?$version=2022-03-01-preview2`

```json
            {
              "$schema": "https://product-ingestion.azureedge.net/schema/configure/2022-03-01-preview2"
              "resources": [
                { 
                "$schema": "https://product-ingestion.azureedge.net/schema/product/2022-03-01-preview3",
                "identity": {
                  "externalID": "ds-contoso-image-resize-demo"
                },
                "type": "softwareAsAService",
                "alias": " Contoso Image Resizing Service"
              }
              ]
            }
```

***Sample response***:

```json
            {
  "$schema": "https://product-ingestion.azureedge.net/schema/configure-status/2022-03-01-preview2",
  "jobID": "071b135e-9faf-4ff7-b113-a3f25bb0f468",
  "jobStatus": "running",
  "jobResult": "pending",
  "jobStart": "2022-08-18T16:35:56.5917185Z",
  "jobEnd": "0001-01-01T00:00:00",
  "errors": []
}
```

You can then use the jobID via the Configure Status API to check the status of your request.

#### Dependencies

Certain resources have dependencies on the creation of another resource as a prerequisite. In this circumstance, we're using the "*resourceName*" property within the same payload to denote the dependency of the product resource in the plan resource as we're creating both in the same request.

The "resourceName" is only used to identify each resource as part of the configure request you're doing. The value won't be part of the resources' data, it isn't stored, nor is it exposed to customers. Additionally if there are any errors as part of the configure request, the "resourceName" will be used to call out the resource to which the error belongs.

***Sample request***:

In this example, the product must be created prior to the plan and therefore, the "*resourceName*" property is used. The product being created, "myNewProduct," will be the value used for "resourceName" and referenced within the dependent plan resource.

`POST https://graph.microsoft.com/rp/product-ingestion/configure?$version=2022-03-01-preview2`

```json
            {
              "$schema": "https://product-ingestion.azureedge.net/schema/configure/2022-03-01-preview2"
              "resources": [
              {
                "$schema": "https://product-ingestion.azureedge.net/schema/product/2022-03-01-preview3", 
                "resourceName": "myNewProduct", 
                "alias": "Contoso Image Resizing Service",
                ...
              }, 
              {
                "$schema": "https://product-ingestion.azureedge.net/schema/plan/2022-03-01-preview2", 
                "alias": " Gold - Annual payment",
                "product": {"resourceName": "myNewProduct"}
                  ...
              }, 
              }]
            }
```

### Submission resource

If publishing to "*preview*" or "*live*", include the submission resource in your request, which contains:

- The "*product*" property, denoting the product being updated as referenced by either its durable ID or external ID
- The "*targetType*" property, denoting the target environment

When publishing to live specifically, the "*ID*" of the preview submission you're looking to publish:

```json
              {
                "$schema": "https://product-ingestion.azureedge.net/schema/submission/2022-03-01-preview2",
                "id": "submission/12345678-abcd-efgh-1234-12345678901/11521167929065",    
                "product": "product/12345678-abcd-efgh-1234-12345678901", 
                "target": { "targetType": "live" }
              }
```

> [!NOTE]
> If you don't include the submission resource, the changes will only be made to the draft state.

### Publishing to preview

Commercial product types support a preview environment, and each update must be first published to preview before going live. You can't publish directly to live.

> [!IMPORTANT]
> The exception to this is when making changes to the private audience of your plans. When [syncing updates to the private audience](#sync-private-audiences) specifically, these changes will propagate to both preview and live at the same time.

There are two ways you can publish your resources to the preview environment. If any changes need to be made to the preview submission, do another GET request, make the necessary changes, and push the changes again. You don't need to first go live with your initial changes.

#### Method 1: Publish all draft resources

If you want to publish every draft change you have made, you can send a configure request with a submission resource that sets the preview environment as the "targetType". As shown in the example below, you don't need to explicitly provide every resource that requires an update as this method publishes all changes to the target environment, which in this case is preview. You only need to provide the configure API endpoint and the submission resource.

***Sample request***:

`POST https://graph.microsoft.com/rp/product-ingestion/configure?$version=2022-03-01-preview2`

```json
            {
              "$schema": "https://product-ingestion.azureedge.net/schema/configure/2022-03-01-preview2"
              "resources": [
              {
            // Below is the submission resource to publish to preview
                "$schema": "https://product-ingestion.azureedge.net/schema/submission/2022-03-01-preview2",
                "product": "product/12345678-abcd-efgh-1234-12345678901", // This is the product durable ID
                "target": { "targetType": "preview" }
              }
              ]
            }
```

#### Method 2: Publish specific draft resources (also known as modular publish)

Alternatively, if you aren't prepared to publish all draft changes across various resources, just provide the resources you want to publish along with the submission resource to trigger a modular publish. You can also use this approach to make changes to resources and publish them at the same time instead of as part of a bulk update, as is done through Method 1. For a modular publish, all resources are required except for the product level details (for example, listing, availability, packages, reseller) as applicable to your product type.

***Sample request***:

In this example, resources in the product are explicitly provided as part of the modular publish followed by the submission resource.

`POST https://graph.microsoft.com/rp/product-ingestion/configure?$version=2022-03-01-preview2`

```json
            {
              "$schema": "https://product-ingestion.azureedge.net/schema/configure/2022-03-01-preview2"
              "resources": [
              {
                "$schema": "https://product-ingestion.azureedge.net/schema/product/2022-03-01-preview2", 
                "id": "product/12345678-abcd-efgh-1234-12345678901",
                ...
              },
              {
                "$schema": "https://product-ingestion.azureedge.net/schema/plan/2022-03-01-preview2", 
                  ...
              }, 
              // additional resources
              {
                  ...
              },
              // Below is the submission resource to publish to preview
              {
                "$schema": "https://product-ingestion.azureedge.net/schema/submission/2022-03-01-preview2",
                "product": "product/12345678-abcd-efgh-1234-12345678901", // This is the product durable ID
                "target": { "targetType": "preview" }
              }
              ]
            }
```

### Publishing to live

Once your changes in preview have been tested and verified, you can push your changes to live by sending a configure request with the "*ID*" of your preview submission and the "*targetType*" set to "*live*". To find the "*ID*" of your preview submission to incorporate within your configure request, see [Querying your submissions](#querying-your-submissions).

> [!IMPORTANT]
> Unlike when publishing to preview, there is no option to perform a modular publish when publishing to live. Therefore, it is important to ensure that you have verified your preview submission before going live with your changes.

***Sample request***:

`POST https://graph.microsoft.com/rp/product-ingestion/configure?$version=2022-03-01-preview2`

```json
            {
              "$schema": "https://product-ingestion.azureedge.net/schema/configure/2022-03-01-preview2"
              "resources": [
              // Below is the submission resource, including the preview submission id, to publish to live.
              {
                "$schema": "https://product-ingestion.azureedge.net/schema/submission/2022-03-01-preview2",
                "id": "submission/12345678-abcd-efgh-1234-12345678901/11521167929065",    
                "product": "product/12345678-abcd-efgh-1234-12345678901", // This is the product durable ID
                "target": { "targetType": "live" }
              }
              ]
            }
```

## Check the status of a request

Regardless of the resources included in your configure request or the changes you're making, you'll get a ***configure-status*** object back in the response shortly after submitting a request once it's successfully processed. The "*jobID*" is important as it can later be used to check the status of the request.

`Schema: <https://product-ingestion.azureedge.net/schema/configure-status/2022-03-01-preview2>`

***Sample response to a submitted request***:

```json
            {
                "$schema": "https://product-ingestion.azureedge.net/schema/configure-status/2022-03-01-preview2",
                "jobID": "d4261631-c583-4949-a612-5150882632e9",
                "jobStatus": "notStarted",
                "jobResult": "pending",
                "jobStart": "2022-03-01T13:32:43.123456Z",
                "jobEnd": "0001-01-01T00:00:00",
                "errors": []
            }
```

### Status of a pending request

You can retrieve the status until the job finishes using the following call and inputting the "*jobID*" of the request. The object may also contain a list of errors if there were any issues with your request.

`GET https://graph.microsoft.com/rp/product-ingestion/configure/<jobID>/status?$version=2022-03-01-preview2`

Keep in mind that the time to complete may vary depending on the complexity of your request,

### Summary of a completed request

Once a configure request job is complete, either successfully or with a failure, you can get the list of resources created or updated using the "*jobID*".

> [!NOTE]
> If you make this call before the job is completed, it will fail. Additionally it will only return the resources which were completed successfully, or in the case of a cancellation only the ones completed before the cancellation.

`Schema: <https://product-ingestion.azureedge.net/schema/configure-detail/2022-03-01-preview2>`

`GET https://graph.microsoft.com/rp/product-ingestion/configure/<jobID>?$version=2022-03-01-preview2`

***Sample request***:

In the below example, a GET request is used to retrieve the summary details of the configure request used in the earlier example that created a new SaaS product. The response is the configure-detail object with the resources array containing the product resource that was created along with its durable ID.

`GET https://graph.microsoft.com/rp/product-ingestion/configure/071b135e-9faf-4ff7-b113-a3f25bb0f468?$version=2022-03-01-preview2`

***Sample response***:

```json
            {
"$schema": "https://product-ingestion.azureedge.net/schema/configure-detail/2022-03-01-preview2",
"resources": [
{ 
                "$schema": "https://product-ingestion.azureedge.net/schema/product/2022-03-01-preview2",
                "id": "product/12345678-abcd-efgh-1234-12345678901",
                "identity": {
                  "externalID": "ds-contoso-image-resize-demo "
                },
                "type": "softwareAsAService",
                "alias": "Contoso Image Resizing Service"
              }
]
}             
```

## Cancel a configuration request

Before a job is completed, you may attempt to cancel it if needed. For long running requests, like publishing to "*preview*" or "*live*," the cancel request may be rejected if the job is far enough along in being fully processed.

In order to cancel a job, make a POST call to the cancel endpoint and provide the job ID of the request you want to cancel.

`POST https://graph.microsoft.com/rp/product-ingestion/configure<jobID>/cancel?$version=2022-03-01-preview2`

***Sample request***:

`POST <https://graph.microsoft.com/rp/product-ingestion/configure/d4261631-c583-4949-a612-5150882632e9/cancel?$version=2022-03-01-preview2>`

***Sample response of a successful cancellation request***:

```json
            {
                "$schema": "https://product-ingestion.azureedge.net/schema/configure-status/2022-03-01-preview2",
                "jobID": "d4261631-c583-4949-a612-5150882632e9",
                "jobStatus": "completed",
                "jobResult": "cancelled",
                "jobStart": "2022-03-01-T13:32:43.123456Z",
                "jobEnd": "2022-03-01T17:34:21.5225132Z",
                "errors": []
            }
```

***Sample response in case cancellation is not allowed:
`HTTP Status code: 400`***

Content:

```json
            {
              "error": {
                "code": "badRequest",
                "message": "Cannot cancel job, job has already completed.",
                "details": []
              }
}
```

> [!IMPORTANT]
> Keep in mind the cancellation only applies to resources that have not yet been processed. Some resources may have already completed processing and will reflect the latest configuration updates, despite cancellation of the request.

You can fetch the [summary of the configure request](#check-the-status-of-a-request) after cancellation to verify which resources (if any) had already been processed prior to the cancellation.

## Sync private audiences

Updates to private audiences in the draft, preview, and live environments can be performed at the same time without requiring a publish. This can be done by utilizing the "*price-and-availability-update-private-audiences*" resource and specifying which audiences you want to add or remove from a specific plan. You don't need to provide the submission resource when syncing the private audience.

> [!IMPORTANT]
> The supported audience types are "subscription", "ea", "msdn" and "tenant" but support for these varies by product type. If your product supports more than one type of identifier to configure the private audience (for example, both tenant IDs and subscription IDs), you must perform a full publish if providing a new identifier type for the first time. You cannot sync the private audience in this case.

***Sample request to sync the private audience configuration***:

`POST https://graph.microsoft.com/rp/product-ingestion/configure?$version=2022-03-01-preview2`

```json
        {
          "$schema": "https://product-ingestion.azureedge.net/schema/configure/2022-03-01-preview2"
          "resources": [
          {
            "$schema": "https://product-ingestion.azureedge.net/schema/price-and-availability-update-private-audiences/2022-03-01-preview2",
            "product": "product/12345678-abcd-efgh-1234-12345678901", // product durable ID
            "plan": "plan/12345678-abcd-efgh-1234-12345678901/7e70b11f-809e-4c45-ae2f-1fb3ceaca33b", //plan durable ID 
            "privateAudiences":
            {
              "add ":
              [
                  {
            "type": "tenant",
                    "id": "4c2bdcdc-f10e-468d-8a2a-0832e089215b",
                    "label": "test 1"
                  }
              ],
              "remove ":
              [
                {
            "type": "subscription",
                    "id": "412c45bf-c99a-4e96-b683-77b0aa2dd09e",
                    "label": "test 2"
                }
              ]
            }
          }
          ]
        }
```

## Configure lead management

Connect your customer relationship management (CRM) system with your commercial marketplace product so you can receive customer contact information when a customer expresses interest or deploys your product. You can modify this connection at any time during or after product creation. [Learn more](partner-center-portal/commercial-marketplace-get-customer-leads.md).

***Sample request to configure lead management***:

`POST https://graph.microsoft.com/rp/product-ingestion/configure?$version=2022-03-01-preview2`

```json
        {
          "$schema": "https://product-ingestion.azureedge.net/schema/configure/2022-03-01-preview2"
          "resources": [
            {
            "$schema": "https://product-ingestion.azureedge.net/schema/customer-leads/2022-03-01-preview3",
            "id": "customer-leads/a0c6484f-b4fb-4129-ac6b-35f2b5628089",
            "product": "product/a0c6484f-b4fb-4129-ac6b-35f2b5628089",
            "leadDestination": "httpsEndpoint",
            "httpsEndpointLeadConfiguration": {
              "httpsEndpointUrl": "https://www.your-crm.com/triggers/invoke"
            }
          }  
          ]
        }
```

## Resource lifecycle states

There are different actions you can take that map to a resource's lifecycle state. Not all resources have a lifecycle state and not all lifecycle states are supported by all resources. To discover if a resource has a lifecycle state and which values are supported, you can check the resource schema for the existence of the property "*lifecycleState*". Various supported lifecycle states are detailed below.

### Deleted

You can delete specific resources by updating the "*lifecycleState*" property to "*deleted*". You can only delete draft resources that haven't been published before. This action can't be undone.

***Sample request***:

In the example below, the "*basic*" draft plan is deleted.

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
            "lifecycleState": "deleted"
            }
          ]
        }
```

### Deprecated

Deprecation removes the resource from the commercial marketplace. To deprecate, set the "*lifecycleState*" property to "*deprecated*" on the resources that support it. There are various levels of deprecation. All product types support deprecating the entire product and individual plans within it. To later restore a deprecated resource, refer to the ["generallyAvailable" lifecycle state](#generally-available).

***Sample request of a product deprecation***:

In the example below, the live submission of the product is set to deprecate. Once this change is applied, it's automatically published to live to take effect.

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

When deprecating plans, the *"lifecycleState"* property must be changed to "*deprecated*" and the changes must then be published to "*preview*" then "*live*" for the deprecation to take effect. This is different from a product level deprecation in which the deprecation will automatically be configured in the live environment.

***Sample request of a plan deprecation***:

In the example below, a plan within a SaaS product is set to deprecate. Remember that to apply this change, you can later publish using the submission resource.

`POST https://graph.microsoft.com/rp/product-ingestion/configure?$version=2022-03-01-preview2`

```json
            {
              "$schema": "https://product-ingestion.azureedge.net/schema/configure/2022-03-01-preview2"
              "resources": [
                {
                "$schema": "https://product-ingestion.azureedge.net/schema/plan/2022-03-01-preview2 ",
                "id": "plan/9f8af57f-ab07-461b-8404-50e10e5e80fb/7e70b11f-809e-4c45-ae2f-1fb3ceaca33b",
                "product": "product/9f8af57f-ab07-461b-8404-50e10e5e80fb",
                "identity": { "externalID": "basic" },
                "alias": "basic plan"
                "lifecycleState": "deprecated"
                }
              ]
            }
```

There are other forms of deprecation that vary depending on the product type. [Learn more](#api-guidance-per-product-type) about deprecation of SaaS, virtual machines, and containers.

### Generally available

`generallyAvailable` is the default lifecycle state for all resources. Once a resource is deprecated, you can restore it by changing the "lifecycleState" property back to "generallyAvailable". To restore a deprecated product, you must publish the product to preview then live. You can find examples for SaaS, VMs and containers in their respective articles.

***Sample request of a plan restoration***:

In the example below, a plan is intended to be restored. To apply this change, you later need to publish all the way to live using the submission resource.

`POST https://graph.microsoft.com/rp/product-ingestion/configure?$version=2022-03-01-preview2`

```json
            {
              "$schema": "https://product-ingestion.azureedge.net/schema/configure/2022-03-01-preview2"
              "resources": [
                {
                "$schema": "https://product-ingestion.azureedge.net/schema/plan/2022-03-01-preview2 ",
                "id": "plan/9f8af57f-ab07-461b-8404-50e10e5e80fb/7e70b11f-809e-4c45-ae2f-1fb3ceaca33b",
                "product": "product/9f8af57f-ab07-461b-8404-50e10e5e80fb",
                "identity": { "externalID": "basic" },
                "alias": "basic plan"
                "lifecycleState": "generallyAvailable"
                }
              ]
            }     
```

## Resource API reference

The below schema versions are applicable for preview only and will change once the API becomes generally available.

> [!NOTE]
> You can view the existing available resources and their versions here: [resources-index](https://schema.mp.microsoft.com/schema/resources-index/2022-07-01)

| **Resource type**  | **Description** | **Schema** |
|---|---|---|
| **azure-test-drive-technical-configuration** | Technical details that help the Microsoft commercial marketplace connect to your test drive solution. | <https://product-ingestion.azureedge.net/schema/azure-test-drive-technical-configuration/2022-03-01-preview3> |
| **commercial-marketplace-setup** | Describes the transactable configuration of products in the commercial marketplace. | <https://product-ingestion.azureedge.net/schema/commercial-marketplace-setup/2022-03-01-preview2> |
| **customer-leads** | Allows connecting to a CRM system to receive customer leads. | <https://product-ingestion.azureedge.net/schema/customer-leads/2022-03-01-preview3> |
| **listing** | This includes the descriptions of your product, which will be displayed in Microsoft commercial marketplace storefronts. | <https://schema.mp.microsoft.com/schema/listing/2022-03-01-preview5> |
| **listing-asset** | Screenshots and your marketing assets linked to the listing resource. | <https://schema.mp.microsoft.com/schema/listing-asset/2022-03-01-preview5> |
| **listing-trailer** | Video assets linked to the listing resource. | <https://schema.mp.microsoft.com/schema/listing-trailer/2022-03-01-preview5> |
| **microsoft365-integration** | Microsoft 365 enablement and type selection. | <https://product-ingestion.azureedge.net/schema/microsoft365-integration/2022-03-01-preview2> |
| **plan** | To create plans, which will then be referenced by the plan level resources you configure, like plan-listing. | <https://product-ingestion.azureedge.net/schema/plan/2022-03-01-preview2> |
| **plan-listing** | Define the plan name and description as you want them to appear in the commercial marketplace. | <https://schema.mp.microsoft.com/schema/plan-listing/2022-03-01-preview5> |
| **price-and-availability-custom-meter** | Define the custom-meters shared across your plans. | <https://product-ingestion.azureedge.net/schema/price-and-availability-custom-meter/2022-03-01-preview3> |
| **price-and-availability-offer** | Define a limited audience who can review your product before you publish it live. | <https://product-ingestion.azureedge.net/schema/price-and-availability-offer/2022-03-01-preview3> |
| **price-and-availability-plan** | Configure the markets this plan is available in, the desired monetization model, price, and billing terms. | <https://schema.mp.microsoft.com/schema/price-and-availability-plan/2022-03-01-preview4> |
| **price-and-availability-update-private-audiences** | Updates to private audiences in the draft, preview, and live environments can be performed at the same time without requiring a publish. | <https://product-ingestion.azureedge.net/schema/price-and-availability-update-private-audiences/2022-03-01-preview3> |
| **private-and-availability-private-offer-plan** | Used to configure the absolute pricing details of a product/plan pricing used within a private offer | <https://schema.mp.microsoft.com/schema/price-and-availability-private-offer-plan/2022-07-01> |
| **private-offer** | Defines the name and type of private offer, with the offer terms and details, along with the products/plan included and their pricings | <https://schema.mp.microsoft.com/schema/private-offer/2022-07-01> |
| **product** | This is the main resource, defines the name and type of the product, all resources reference this. | <https://product-ingestion.azureedge.net/schema/product/2022-03-01-preview3> |
| **property** | Define the categories and industries applicable to your offer, your app version, and legal contracts. | <https://schema.mp.microsoft.com/schema/property/2022-03-01-preview5> |
| **reseller** | Configure the partners in the Cloud Solution Providers (CSP) program you want to make your product available to. | <https://product-ingestion.azureedge.net/schema/reseller/2022-03-01-preview2> |
| **resource-tree** | Describes the  product a list of resources for that product in the current state for the target environment specified. | <https://product-ingestion.azureedge.net/schema/resource-tree/2022-03-01-preview2> |
| **software-as-a-service-technical-configuration** | Technical details that help the Microsoft commercial marketplace connect to your solution. | <https://product-ingestion.azureedge.net/schema/software-as-a-service-technical-configuration/2022-03-01-preview3> |
| **submission** | Can be used to trigger different actions on your product and indicate the publish state of your product indifferent environments (draft, preview, and live). | <https://product-ingestion.azureedge.net/schema/submission/2022-03-01-preview2> |
| **test-drive** | Define whether you want to let your customers try out the product for free for a limited time. | <https://product-ingestion.azureedge.net/schema/test-drive/2022-03-01-preview2> |
| **test-drive-listing** | Define the details regarding how customers can try out your product. | <https://product-ingestion.azureedge.net/schema/test-drive-listing/2022-03-01-preview3> |
| **virtual-machine-plan-technical-configuration** | Technical details describing the virtual machine and the image location. | <https://product-ingestion.azureedge.net/schema/virtual-machine-plan-technical-configuration/2022-03-01-preview3> |
| **virtual-machine-test-drive-technical-configuration** | Technical details that help the Microsoft commercial marketplace connect to your test drive solution. | <https://product-ingestion.azureedge.net/schema/virtual-machine-test-drive-technical-configuration/2022-03-01-preview2> |
| **container-plan-technical-configuration** | Technical details describing the container image properties. | <https://product-ingestion.azureedge.net/schema/container-plan-technical-configuration/2022-03-01-preview3> |

## API guidance per product type

The Product Ingestion API will be made available to other product types in the future. As more product types are supported, more guidance specific to each product type will be made available.

| **Product type** | **Product type-specific resources** |
|---|---|
| **Private offers** | [Create and manage private offers via Product Ingestion API](private-offers-api.md) |
| **SaaS** | [Create and manage SaaS offers via Product Ingestion API](https://microsoft.sharepoint.com/:w:/t/CMP2/Eam9Qhdob0pGi463sGsUdkYBDvISglSPW6hq6KqUJ73ivQ?e=hgqccY) |
| **Virtual machines** | [Create and manage virtual machine offers via Product Ingestion API](product-ingestion-api-vm.md) |
| **Containers** | [Create and manage container offers via Product Ingestion API](https://microsoft.sharepoint.com/:w:/t/CMP2/ETqOHvMYhLZKqz3ZXgJBO48BZFh0WFZ59DxAjAiLzts7kw?e=FzefJw) |

## API versions and updates

| **Update** | **What has changed?** |
|---|---|
| **12-2022** | A new schema version 2022-03-01-preview3 of the PC Ingestion API for customer leads is now available that accepts clientID and clientSecret while configuring customer leads and stops capturing the serverID and contact email fields. Switch to the new version and provide the clientID and clientSecret to continue configuring Marketo connector for marketplace offers. New schema URL: `https://product-ingestion.azureedge.net/schema/customer-leads/2022-03-01-preview3` |
| **09-2022** | Container preview support is released as version 2022-03-01-preview4 |
| **08-2022** | Software as a service preview support is released as version 2022-03-01-preview3 |
| **08-2022** | Private offer public release as version 2022-07-01 |
| **05-2022** | Virtual machine preview support is released as version 2022-03-01-preview2 |

## Next steps

- [Product ingestion API for Saas](product-ingestion-api-saas.md)
- [Product ingestion API for transactable containers](product-ingestion-api-transactable-containers.md)
