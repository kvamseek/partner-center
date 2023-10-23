---
title: Purchase Azure savings plans
description: As a Cloud Solution Provider, learn how to use the Azure portal to purchase and manage Azure savings plans for customers.
ms.topic: article
ms.service: partner-dashboard
ms.subservice: partnercenter-pricing
author: migolova
ms.author: migolova
ms.date: 06/15/2023
---

# Purchase Azure savings plans

**Applies to**: Partner Center

This article covers the API experience for purchasing Azure savings plan in Partner Center and provides [request/response examples](#requestresponse-examples) specific to Azure savings plans.

## Prerequisites

Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with App+User credentials.

A customer ID (`customer-tenant-id`). If you don't know the customer's ID, you can look it up in [Partner Center](https://partner.microsoft.com/dashboard) by selecting the **Customers** workspace, then the customer from the customer list, then **Account**. On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section. The Microsoft ID is the same as the customer ID (`customer-tenant-id`).

To purchase an Azure savings plan for a customer using the Partner Center API, you must have an Azure plan for that customer with at least one active Azure subscription. [How to purchase an Azure plan](../purchase-azure-plan.md).

## Discover Azure savings plan

Before purchasing an Azure savings plan, complete the following steps:

1. Identify and retrieve the Product and SKU that you want to purchase. You can do this by listing the products and SKUs first, or if you already know the IDs of the product and SKU, selecting them. To view Azure savings plan values in the below APIs, a customer ID is required in the route for the below APIs, and that customer must have an Azure Plan.
   - [Get a list of products (by country/region)](get-a-list-of-products.md)
   - [Get a list of products (by customer)](get-a-list-of-products-by-customer.md)
   - [Get a product using the product ID](get-a-product-by-id.md)
   - [Get a list of SKUs for a product (by country/region)](get-a-list-of-skus-for-a-product.md)
   - [Get a list of SKUs for a product (by customer)](get-a-list-of-skus-for-a-product-by-customer.md)
   - [Get a SKU using the SKU ID](get-a-sku-by-id.md)

1. Retrieve the [availability](product-resources.md) for the [SKU](product-resources.md). You need the **CatalogItemId** of the availability when placing the order. To get this value, use one of the following APIs:
   - [Get a list of availabilities for a SKU (by country/region)](get-a-list-of-availabilities-for-a-sku.md)
   - [Get a list of availabilities for a SKU (by customer)](get-a-list-of-availabilities-for-a-sku-by-customer.md)
   - [Get an availability using the availability ID](get-an-availability-by-id.md)

For Azure savings plans, the [Get a list of SKUs for a product (by customer)](get-a-list-of-skus-for-a-product-by-customer.md) and [Get a SKU using the SKU ID](get-a-sku-by-id.md) and availability API responses  return a **minimumPurchaseCommitment** for the SKU. This is the minimum commitment that can be made per hour for a given term. This is only applicable to Azure savings plan and doesn't apply to other product families.

## Purchase Azure savings plan

To submit your Azure savings plan order, complete the following steps:

1. Create a cart to hold the collection of catalog items that you intend to buy. When you create a [Cart](cart-resources.md), the [cart line items](cart-resources.md) are automatically grouped based on what can be purchased together in the same [Order](order-resources.md).
   - [Create a shopping cart](create-a-cart.md)
   - [Update a shopping cart](update-a-cart.md)
1. Check out the cart. Checking out a cart results in the creation of an [Order](order-resources.md).
   - [Checkout the cart](checkout-a-cart.md)

In the API requests, partners must specify the following parameters when creating or updating a cart and creating an order.  PurchaseCommitment is a new value for Azure savings plans.

- **Scope**: possible values include single, shared
- **EntitlementId**: Azure subscription ID, required for single scope
- **SubscriptionId**: Azure plan ID, required for shared scope
- **PurchaseCommitment**: The fixed hourly amount committed on compute services for one or three years.

Azure savings plans require a provisioning context, including scope and subscription ID/entitlement ID, and a purchase commitment, including amount, grain, and currency.

## View and manage Azure savings plan

Partners can view Azure savings plans purchased in Partner Center. Like Reservation Instances, partners can continue to use Azure portal for post-purchase management actions. For more information on managing Azure savings plan, see [Manage Azure savings plans - Microsoft Cost Management](/azure/cost-management-billing/savings-plan/manage-savings-plan).

In the [Get a subscription by ID](get-a-subscription-by-id.md) and [Get a customer's subscriptions](get-all-of-a-customer-s-subscriptions.md) APIs, a data model called **SubscriptionLineItem** is returned. Within the subscription response, partners see the following properties for Azure savings plan:

- **unitType:** the value is benefit
- **billingType:** the value is benefit
- **lineItems:** A line item contains the purchase details of a particular Azure savings plan subscription (for example, scope and PurchaseCommitment).
- **productOrderId:** Identifier for a specific product purchase (for example, Reservations or Azure savings plan).

> [!NOTE]
> For Azure savings plan purchased through the Azure portal, the subscription APIs won't return the order ID.

## Invoice and reconciliation for Azure savings plan

Partners can visit [Reconciling and billing of savings plan in CSP](../azure-savings.md) to understand how the savings are reflected in their monthly billing reconciliation files.

## Request/response examples

### Discover API examples

#### Get a product by ID

***Response***:

```http
{  
    "id": "DZH318Z09V6F",  
    "title": "Azure savings plan",  
    "description": "Flexible pricing model offering lower prices compared to On-Demand pricing, in exchange for a specific usage commitment",  
    "productType": {  
        "id": "Azure",  
        "displayName": "Azure",  
        "subType": {  
            "id": "SavingsPlan",  
            "displayName": "SavingsPlan"  
        }  
    },  
    "isMicrosoftProduct": true,  
    "publisherName": "Microsoft Corporation",  
    "links": {  
        "skus": {  
            "uri": "/products/DZH318Z09V6F/skus?country=US",  
            "method": "GET",  
            "headers": []  
        },  
        "self": {  
            "uri": "/products/DZH318Z09V6F?country=US",  
            "method": "GET",  
            "headers": []  
        }  
    }  
}  
```

#### Get a SKU by ID

***Response***:

```http
{  
    "id": "0001",  
    "productId": "DZH318Z09V6F",  
    "title": "Compute savings plan, 1 Year",  
    "description": "Compute savings plan, 1 Year",  
    "minimumQuantity": 1,  
    "maximumQuantity": 1,  
    "minimumPurchaseCommitment": {  
        "grain": "Hourly",  
        "currencyCode": {  
            "code": "USD",  
            "symbol": "$"  
        },  
        "amount": "0.001"  
    },  
    "isTrial": false,  
    "supportedBillingCycles": [  
        "one_time",  
        "monthly"  
    ],  
    "purchasePrerequisites": [  
        "MicrosoftCloudAgreement"  
    ],  
    "inventoryVariables": [],  
    "provisioningVariables": [],  
    "actions": [  
        "Refund"  
    ],  
    "dynamicAttributes": {  
        "isMicrosoftProduct": true,  
        "armSkuName": "Compute_Savings_Plan",  
        "duration": "1year",  
        "termDuration": "P1Y",  
        "internal": false  
    },  
    "links": {  
        "availabilities": {  
            "uri": "/products/DZH318Z09V6F/skus/0001/availabilities?country=US",  
            "method": "GET",  
            "headers": []  
        },  
        "self": {  
            "uri": "/products/DZH318Z09V6F/skus/0001?country=US",  
            "method": "GET",  
            "headers": []  
        }  
    }  
}
```

#### Get availability by ID

***Response***:

```http
{  
    "id": "DZH318Z0BLD3",  
    "productId": "DZH318Z09V6F",  
    "skuId": "0001",  
    "catalogItemId": "DZH318Z09V6F:0001:DZH318Z0BLD3",  
    "defaultCurrency": {  
        "code": "USD",  
        "symbol": "$"  
    },  
    "segment": "commercial",  
    "country": "US",  
    "isPurchasable": true,  
    "isRenewable": false,  
    "renewalInstructions": [],  
    "terms": [  
        {  
            "duration": "P1Y",  
            "description": "1year"  
        }  
    ],  
    "links": {  
        "self": {  
            "uri": "/products/DZH318Z09V6F/skus/0001/availabilities/DZH318Z0BLD3?country=US",  
            "method": "GET",  
            "headers": []  
        }  
    },  
    "product": {  
        "id": "DZH318Z09V6F",  
        "title": "Azure savings plan",  
        "description": "Flexible pricing model offering lower prices compared to On-Demand pricing, in exchange for a specific usage commitment",  
        "productType": {  
            "id": "Azure",  
            "displayName": "Azure",  
            "subType": {  
                "id": "SavingsPlan",  
                "displayName": "SavingsPlan"  
            }  
        },  
        "isMicrosoftProduct": true,  
        "publisherName": "Microsoft Corporation",  
        "links": {  
            "skus": {  
                "uri": "/products/DZH318Z09V6F/skus?country=US",  
                "method": "GET",  
                "headers": []  
            },  
            "self": {  
                "uri": "/products/DZH318Z09V6F?country=US",  
                "method": "GET",  
                "headers": []  
            }  
        }  
    },  
    "sku": {  
        "id": "0001",  
        "productId": "DZH318Z09V6F",  
        "title": "Compute savings plan, 1 Year",  
        "description": "Compute savings plan, 1 Year",  
        "minimumQuantity": 1,  
        "maximumQuantity": 1,  
        "minimumPurchaseCommitment": {  
            "grain": "Hourly",  
            "currencyCode": {  
                "code": "USD",  
                "symbol": "$"  
            },  
            "amount": "0.001"  
        },  
        "isTrial": false,  
        "supportedBillingCycles": [  
            "one_time",  
            "monthly"  
        ],  
        "purchasePrerequisites": [  
            "MicrosoftCloudAgreement"  
        ],  
        "inventoryVariables": [],  
        "provisioningVariables": [],  
        "actions": [  
            "Refund"  
        ],  
        "dynamicAttributes": {  
            "isMicrosoftProduct": true,  
            "armSkuName": "Compute_Savings_Plan",  
            "duration": "1year",  
            "termDuration": "P1Y",  
            "internal": false  
        },  
        "links": {  
            "availabilities": {  
                "uri": "/products/DZH318Z09V6F/skus/0001/availabilities?country=US",  
                "method": "GET",  
                "headers": []  
            },  
            "self": {  
                "uri": "/products/DZH318Z09V6F/skus/0001?country=US",  
                "method": "GET",  
                "headers": []  
            }  
        }  
    }  
} 
```

#### Get a list of SKUs for a product (by customer)

***Response***:

```http
{  
    "totalCount": 2,  
    "items": [  
        {  
            "id": "0001",  
            "productId": "DZH318Z09V6F",  
            "title": "Compute savings plan, 1 Year",  
            "description": "Compute savings plan, 1 Year",  
            "minimumQuantity": 1,  
            "maximumQuantity": 1,  
            "minimumPurchaseCommitment": {  
                "grain": "Hourly",  
                "currencyCode": {  
                    "code": "USD",  
                    "symbol": "$"  
                },  
                "amount": "0.001"  
            },  
            "isTrial": false,  
            "supportedBillingCycles": [  
                "one_time",  
                "monthly"  
            ],  
            "purchasePrerequisites": [  
                "MicrosoftCloudAgreement"  
            ],  
            "inventoryVariables": [],  
            "provisioningVariables": [],  
            "actions": [  
                "Refund"  
            ],  
            "dynamicAttributes": {  
                "isMicrosoftProduct": true,  
                "armSkuName": "Compute_Savings_Plan",  
                "duration": "1year",  
                "termDuration": "P1Y",  
                "internal": false  
            },  
            "links": {  
                "availabilities": {  
                    "uri": "/products/DZH318Z09V6F/skus/0001/availabilities",  
                    "method": "GET",  
                    "headers": []  
                },  
                "self": {  
                    "uri": "/products/DZH318Z09V6F/skus/0001",  
                    "method": "GET",  
                    "headers": []  
                }  
            }  
        },  
        {  
            "id": "0002",  
            "productId": "DZH318Z09V6F",  
            "title": "Compute savings plan, 3 Years",  
            "description": "Compute savings plan, 3 Years",  
            "minimumQuantity": 1,  
            "maximumQuantity": 1,  
            "minimumPurchaseCommitment": {  
                "grain": "Hourly",  
                "currencyCode": {  
                    "code": "USD",  
                    "symbol": "$"  
                },  
                "amount": "0.001"  
            },  
            "isTrial": false,  
            "supportedBillingCycles": [  
                "one_time",  
                "monthly"  
            ],  
            "purchasePrerequisites": [  
                "MicrosoftCloudAgreement"  
            ],  
            "inventoryVariables": [],  
            "provisioningVariables": [],  
            "actions": [  
                "Refund"  
            ],  
            "dynamicAttributes": {  
                "isMicrosoftProduct": true,  
                "armSkuName": "Compute_Savings_Plan",  
                "duration": "3years",  
                "termDuration": "P3Y",  
                "internal": false  
            },  
            "links": {  
                "availabilities": {  
                    "uri": "/products/DZH318Z09V6F/skus/0002/availabilities?country=US",  
                    "method": "GET",  
                    "headers": []  
                },  
                "self": {  
                    "uri": "/products/DZH318Z09V6F/skus/0002?country=US",  
                    "method": "GET",  
                    "headers": []  
                }  
            }  
        }  
    ],  
    "links": {  
        "self": {  
            "uri": "/products/DZH318Z09V6F/skus?country=US",  
            "method": "GET",  
            "headers": []  
        }  
    },  
    "attributes": {  
        "objectType": "Collection"  
    }  
}  
```

#### Get a list of SKUs for a product (by country/region)

***Response***:

```http
{  
    "totalCount": 2,  
    "items": [  
        {  
            "id": "0001",  
            "productId": "DZH318Z09V6F",  
            "title": "Compute savings plan, 1 Year",  
            "description": "Compute savings plan, 1 Year",  
            "minimumQuantity": 1,  
            "maximumQuantity": 1,  
            "minimumPurchaseCommitment": {  
                "grain": "Hourly",  
                "currencyCode": {  
                    "code": "USD",  
                    "symbol": "$"  
                },  
                "amount": "0.001"  
            },  
            "isTrial": false,  
            "supportedBillingCycles": [  
                "one_time",  
                "monthly"  
            ],  
            "purchasePrerequisites": [  
                "MicrosoftCloudAgreement"  
            ],  
            "inventoryVariables": [],  
            "provisioningVariables": [],  
            "actions": [  
                "Refund"  
            ],  
            "dynamicAttributes": {  
                "isMicrosoftProduct": true,  
                "armSkuName": "Compute_Savings_Plan",  
                "duration": "1year",  
                "termDuration": "P1Y",  
                "internal": false  
            },  
            "links": {  
                "availabilities": {  
                    "uri": "/products/DZH318Z09V6F/skus/0001/availabilities?country=US",  
                    "method": "GET",  
                    "headers": []  
                },  
                "self": {  
                    "uri": "/products/DZH318Z09V6F/skus/0001?country=US",  
                    "method": "GET",  
                    "headers": []  
                }  
            }  
        },  
        { 
            "id": "0002",  
            "productId": "DZH318Z09V6F",  
            "title": "Compute savings plan, 3 Years",  
            "description": "Compute savings plan, 3 Years",  
            "minimumQuantity": 1,  
            "maximumQuantity": 1,  
            "minimumPurchaseCommitment": {  
                "grain": "Hourly",  
                "currencyCode": {  
                    "code": "USD",  
                    "symbol": "$"  
                },  
                "amount": "0.001"  
            },  
            "isTrial": false,  
            "supportedBillingCycles": [  
                "one_time",  
                "monthly"  
            ],  
            "purchasePrerequisites": [  
                "MicrosoftCloudAgreement"  
            ],  
            "inventoryVariables": [],  
            "provisioningVariables": [],  
            "actions": [  
                "Refund"  
            ],  
            "dynamicAttributes": {  
                "isMicrosoftProduct": true,  
                "armSkuName": "Compute_Savings_Plan",  
                "duration": "3years",  
                "termDuration": "PY",  
                "internal": false  
            },  
            "links": {  
                "availabilities": {  
                    "uri": "/products/DZH318Z09V6F/skus/0002/availabilities?country=US",  
                    "method": "GET",  
                    "headers": []  
                },  
                "self": {  
                    "uri": "/products/DZH318Z09V6F/skus/0002?country=US",  
                    "method": "GET",  
                    "headers": []  
                }  
            }  
        }  
    ],  
    "links": {  
        "self": {  
            "uri": "/products/DZH318Z09V6F/skus?country=US",  
            "method": "GET",  
            "headers": []  
        }  
    },  
    "attributes": {  
        "objectType": "Collection"  
    }  
}
```

#### Get a list of availabilities by SKU (by customer)

***Response***:

```http
 {  
    "totalCount": 1,  
    "items": [  
        {  
            "id": "DZH318Z0BLD3",  
            "productId": "DZH318Z09V6F",  
            "skuId": "0001",  
            "catalogItemId": "DZH318Z09V6F:0001:DZH318Z0BLD3",  
            "defaultCurrency": {  
                "code": "USD",  
                "symbol": "$"  
            },  
            "segment": "commercial",  
            "country": "US",  
            "isPurchasable": true,  
            "isRenewable": false,  
            "renewalInstructions": [],  
            "terms": [  
                {  
                    "duration": "P1Y",  
                    "description": "1year"  
                }  
            ],  
            "links": {  
                "self": {  
                    "uri": "/products/DZH318Z09V6F/skus/0001/availabilities/DZH318Z0BLD3?country=US",  
                    "method": "GET",  
                    "headers": []  
                }  
            },  
            "product": {  
                "id": "DZH318Z09V6F",  
                "title": "Azure savings plan",  
                "description": "Flexible pricing model offering lower prices compared to On-Demand pricing, in exchange for a specific usage commitment",  
                "productType": {  
                    "id": "Azure",  
                    "displayName": "Azure",  
                    "subType": {  
                        "id": "SavingsPlan",  
                        "displayName": "SavingsPlan"  
                    }  
                },  
                "isMicrosoftProduct": true,  
                "publisherName": "Microsoft Corporation",  
                "links": {  
                    "skus": {  
                        "uri": "/products/DZH318Z09V6F/skus?country=US",  
                        "method": "GET",  
                        "headers": []  
                    }, 
                    "self": {  
                        "uri": "/products/DZH318Z09V6F?country=US",  
                        "method": "GET",  
                        "headers": []  
                    }  
                }  
            },  
            "sku": {  
                "id": "0001",  
                "productId": "DZH318Z09V6F",  
                "title": "Compute savings plan, 1 Year",  
                "description": "Compute savings plan, 1 Year",  
                "minimumQuantity": 1,  
                "maximumQuantity": 1,  
                "minimumPurchaseCommitment": {  
                    "grain": "Hourly",  
                    "currencyCode": {  
                        "code": "USD",  
                        "symbol": "$"  
                    },  
                    "amount": "0.001"  
                },  
                "isTrial": false,  
                "supportedBillingCycles": [  
                    "one_time",  
                    "monthly"  
                ],  
                "purchasePrerequisites": [  
                    "MicrosoftCloudAgreement"  
                ],  
                "inventoryVariables": [],  
                "provisioningVariables": [],  
                "actions": [  
                    "Refund"  
                ],  
                "dynamicAttributes": {  
                    "isMicrosoftProduct": true,  
                    "armSkuName": "Compute_Savings_Plan",  
                    "duration": "1year",  
                    "termDuration": "P1Y",  
                    "internal": false  
                },  
                "links": {  
                    "availabilities": {  
                        "uri": "/products/DZH318Z09V6F/skus/0001/availabilities?country=US",  
                        "method": "GET",  
                        "headers": []  
                    },  
                    "self": {  
                        "uri": "/products/DZH318Z09V6F/skus/0001?country=US",  
                        "method": "GET",  
                        "headers": []  
                    }  
                }  
            }  
        }  
    ],  
    "links": {  
        "self": {  
            "uri": "/products/DZH318Z09V6F/skus/0001/availabilities?country=US",  
            "method": "GET",  
            "headers": []  
        }  
    },  
    "attributes": {  
        "objectType": "Collection"  
    }  
}
```

#### Get a list of availabilities by SKU (by country/region)

***Response***:

```http
{  
    "totalCount": 1,  
    "items": [  
        {  
            "id": "DZH318Z0BLD3",  
            "productId": "DZH318Z09V6F",  
            "skuId": "0001",  
            "catalogItemId": "DZH318Z09V6F:0001:DZH318Z0BLD3",  
            "defaultCurrency": {  
                "code": "USD",  
                "symbol": "$"  
            },  
            "segment": "commercial",  
            "country": "US",  
            "isPurchasable": true,  
            "isRenewable": false,  
            "renewalInstructions": [],  
            "terms": [  
                {  
                    "duration": "P1Y",  
                    "description": "1year"  
                }  
            ],  
            "links": {  
                "self": {  
                    "uri": "/products/DZH318Z09V6F/skus/0001/availabilities/DZH318Z0BLD3?country=US",  
                    "method": "GET",  
                    "headers": []  
                }  
            },  
            "product": {  
                "id": "DZH318Z09V6F",  
                "title": "Azure savings plan",  
                "description": "Flexible pricing model offering lower prices compared to On-Demand pricing, in exchange for a specific usage commitment",  
                "productType": {  
                    "id": "Azure",  
                    "displayName": "Azure",  
                    "subType": {  
                        "id": "SavingsPlan",  
                        "displayName": "SavingsPlan"  
                    }  
                },  
                "isMicrosoftProduct": true,  
                "publisherName": "Microsoft Corporation",  
                "links": {  
                    "skus": {  
                        "uri": "/products/DZH318Z09V6F/skus?country=US",  
                        "method": "GET",  
                        "headers": []  
                    },  
                    "self": {  
                        "uri": "/products/DZH318Z09V6F?country=US",  
                        "method": "GET",  
                        "headers": []  
                    }  
                }  
            },  
            "sku": {  
                "id": "0001",  
                "productId": "DZH318Z09V6F",  
                "title": "Compute savings plan, 1 Year",  
                "description": "Compute savings plan, 1 Year",  
                "minimumQuantity": 1,  
                "maximumQuantity": 1,  
                "minimumPurchaseCommitment": {  
                    "grain": "Hourly",  
                    "currencyCode": {  
                        "code": "USD",  
                        "symbol": "$"  
                    },  
                    "amount": "0.001"  
                },  
                "isTrial": false,  
                "supportedBillingCycles": [  
                    "one_time",  
                    "monthly"  
                ],  
                "purchasePrerequisites": [  
                    "MicrosoftCloudAgreement"  
                ],  
                "inventoryVariables": [],  
                "provisioningVariables": [],  
                "actions": [  
                    "Refund"  
                ],  
                "dynamicAttributes": {  
                    "isMicrosoftProduct": true,  
                    "armSkuName": "Compute_Savings_Plan",  
                    "duration": "1year",  
                    "termDuration": "P1Y",  
                    "internal": false  
                },  
                "links": {  
                    "availabilities": {  
                        "uri": "/products/DZH318Z09V6F/skus/0001/availabilities?country=US",  
                        "method": "GET",  
                        "headers": []  
                    },  
                    "self": {  
                        "uri": "/products/DZH318Z09V6F/skus/0001?country=US",  
                        "method": "GET",  
                        "headers": []  
                    }  
                }  
            }  
        }  
    ],  
    "links": {  
        "self": {  
            "uri": "/products/DZH318Z09V6F/skus/0001/availabilities?country=US",  
            "method": "GET",  
            "headers": []  
        }  
    },  
    "attributes": {  
        "objectType": "Collection"  
    }  
}  
```

### Purchase API examples

#### Create cart

***Request***:

```http
{  
    "lineItems": [  
        {  
            "id": 0,  
            "catalogItemId": "DZH318Z09V6F:0001:DZH318Z0BLD3",  
            "quantity": 1,  
            "billingCycle": "one_time",  
            "termDuration": "P1Y",  
            "provisioningContext": {  
                "scope": “shared", // scope options are shared, single  
                "subscriptionId": "0350d130-4d3d-4005-aca0-cf84f0ab0d4a", // Azure plan ID, this is required for shared scope 
            },  
            "purchaseCommitment": {  
                "amount": 0.05,  
                "grain": "hourly",  
                "currency": "usd"  
            }  
        }  
    ]  
}
```

***Response***:

```http
{  
    "id": "66e3591e-faad-445c-b930-4ccdbf54c43f",  
    "creationTimestamp": "2023-05-18T05:15:16.8466842Z",  
    "lastModifiedTimestamp": "2023-05-18T05:15:16.8467621Z",  
    "expirationTimestamp": "2023-05-25T05:15:23.6893847Z",  
    "lastModifiedUser": "9db12087-fbc3-481c-8965-73d44ff88e27",  
    "status": "Active",  
    "lineItems": [  
        {  
            "id": 0,  
            "catalogItemId": "DZH318Z09V6F:0001:DZH318Z0BLD3",  
            "quantity": 1,  
            "currencyCode": "USD",  
            "billingCycle": "one_time",  
            "termDuration": "P1Y",  
            "provisioningContext": {  
                "scope": "shared",  
                "subscriptionId": "0350d130-4d3d-4005-aca0-cf84f0ab0d4a"  
            },  
            "orderGroup": "0",  
            "purchaseCommitment": {  
                "amount": 0.05,  
                "currency": "usd",  
                "grain": "hourly"  
            }  
        }  
    ],  
    "links": {  
        "self": {  
            "uri": "/customers/6f4ce4d8-f42e-45e0-8661-92ad6ac9d003/carts/66e3591e-faad-445c-b930-4ccdbf54c43f",  
            "method": "GET",  
            "headers": []  
        }  
    },  
    "attributes": {  
        "objectType": "Cart"  
    }  
}
```

#### Get cart

***Response***:

```http
 {  
    "id": "66e3591e-faad-445c-b930-4ccdbf54c43f",  
    "creationTimestamp": "2023-05-18T05:15:16.8466842Z",  
    "lastModifiedTimestamp": "2023-05-18T05:15:16.8467621Z",  
    "expirationTimestamp": "2023-05-25T05:15:23.6893847Z",  
    "lastModifiedUser": "9db12087-fbc3-481c-8965-73d44ff88e27",  
    "status": "Active",  
    "lineItems": [  
        {  
            "id": 0,  
            "catalogItemId": "DZH318Z09V6F:0001:DZH318Z0BLD3",  
            "quantity": 1,  
            "currencyCode": "USD",  
            "billingCycle": "one_time",  
            "termDuration": "P1Y",  
            "provisioningContext": {  
                "scope": "shared",  
                "subscriptionId": "0350d130-4d3d-4005-aca0-cf84f0ab0d4a"  
            },  
            "orderGroup": "0",  
            "purchaseCommitment": {  
                "amount": 0.05,  
                "currency": "usd",  
                "grain": "hourly"  
            }  
        }  
    ],  
    "links": { 
        "self": {  
            "uri": "/customers/6f4ce4d8-f42e-45e0-8661-92ad6ac9d003/carts/66e3591e-faad-445c-b930-4ccdbf54c43f",  
            "method": "GET",  
            "headers": []  
        }  
    },  
    "attributes": {  
        "objectType": "Cart"  
    }  
}  
```

#### Update cart

***Request***:

```http
{  
    "id": "66e3591e-faad-445c-b930-4ccdbf54c43f",  
    "creationTimestamp": "2023-05-18T05:15:16.8466842Z",  
    "lastModifiedTimestamp": "2023-05-18T05:15:16.8467621Z",  
    "expirationTimestamp": "2023-05-25T05:15:23.6893847Z",  
    "lastModifiedUser": "9db12087-fbc3-481c-8965-73d44ff88e27",  
    "status": "Active",  
    "lineItems": [  
        {  
            "id": 0,  
            "catalogItemId": "DZH318Z09V6F:0001:DZH318Z0BLD3",  
            "quantity": 1,  
            "currencyCode": "USD",  
            "billingCycle": "one_time",  
            "termDuration": "P1Y",  
            "provisioningContext": {  
                "scope": “single", // previously was “shared”  
                “entitlementId": "cdd17cc7-14fe-4445-8650-1f52de705851“ // entitlementId equates to subscriptionId key for the scoped Azure subscription 
            },  
            "orderGroup": "0",  
            "purchaseCommitment": {  
                "amount": 0.05,  
                "currency": "usd",  
                "grain": "hourly"  
            }  
        }  
    ],  
    "links": {  
        "self": {  
            "uri": "/customers/6f4ce4d8-f42e-45e0-8661-92ad6ac9d003/carts/66e3591e-faad-445c-b930-4ccdbf54c43f",  
            "method": "GET",  
            "headers": []  
        }  
    },  
    "attributes": {  
        "objectType": "Cart"  
    }  
}
```

***Response***:

```http
{  
    "id": "66e3591e-faad-445c-b930-4ccdbf54c43f",  
    "creationTimestamp": "2023-05-18T05:15:16.8466842Z",  
    "lastModifiedTimestamp": "2023-05-18T05:15:16.8467621Z",  
    "expirationTimestamp": "2023-05-25T05:15:23.6893847Z",  
    "lastModifiedUser": "9db12087-fbc3-481c-8965-73d44ff88e27",  
    "status": "Active",  
    "lineItems": [  
        {  
            "id": 0,  
            "catalogItemId": "DZH318Z09V6F:0001:DZH318Z0BLD3",  
            "quantity": 1,  
            "currencyCode": "USD",  
            "billingCycle": "one_time",  
            "termDuration": "P1Y",  
            "provisioningContext": {  
                "scope": “single",  
                “entitlementId": "cdd17cc7-14fe-4445-8650-1f52de705851“   
            },  
            "orderGroup": "0",  
            "purchaseCommitment": {  
                "amount": 0.05,  
                "currency": "usd",  
                "grain": "hourly"  
            }  
        }  
    ],  
    "links": {  
        "self": {  
            "uri": "/customers/6f4ce4d8-f42e-45e0-8661-92ad6ac9d003/carts/66e3591e-faad-445c-b930-4ccdbf54c43f",  
            "method": "GET",  
            "headers": []  
        }  
    },  
    "attributes": {  
        "objectType": "Cart"  
    }  
}
```

#### Checkout cart

***Response***:

```http
{  
    "orders": [  
        {  
            "id": "2b912b339251",  
            "alternateId": "2b912b339251",  
            "referenceCustomerId": "6f4ce4d8-f42e-45e0-8661-92ad6ac9d003",  
            "billingCycle": "one_time",  
            "currencyCode": "USD",  
            "currencySymbol": "US$",  
            "lineItems": [  
                {  
                    "lineItemNumber": 0,  
                    "provisioningContext": {  
                        "scope": "single",  
                        "entitlementId": "cdd17cc7-14fe-4445-8650-1f52de705851"  
                    },  
                    "offerId": "DZH318Z09V6F:0001:DZH318Z0BLD3",  
                    "termDuration": "P1Y",  
                    "transactionType": "New",  
                    "friendlyName": "Compute savings plan, 1 Year",  
                    "quantity": 1,  
                    "pricing": {  
                        "listPrice": 438.0,  
                        "discountedPrice": 438.0,  
                        "proratedPrice": 438.0,  
                        "price": 438.0,  
                        "extendedPrice": 438.0  
                    },  
                    "purchaseCommitment": {  
                        "amount": 0.05,  
                        "currency": "usd",  
                        "grain": "hourly"  
                    },  
                    "links": {  
                        "product": {  
                            "uri": "/products/DZH318Z09V6F?country=US",  
                            "method": "GET",  
                            "headers": []  
                        },  
                        "sku": {  
                            "uri": "/products/DZH318Z09V6F/skus/0001?country=US",  
                            "method": "GET",  
                            "headers": []  
                        },  
                        "availability": {  
                            "uri": "/products/DZH318Z09V6F/skus/0001/availabilities/DZH318Z0BLD3?country=US",  
                            "method": "GET",  
                            "headers": []  
                        }  
                    }  
                }  
            ],  
            "creationDate": "2023-05-18T05:16:33.1368156Z",  
            "status": "pending",  
            "transactionType": "UserPurchase",  
            "links": {  
                "self": {  
                    "uri": "/customers/6f4ce4d8-f42e-45e0-8661-92ad6ac9d003/orders/2b912b339251",  
                    "method": "GET",  
                    "headers": []  
                },  
                "provisioningStatus": {  
                    "uri": "/customers/6f4ce4d8-f42e-45e0-8661-92ad6ac9d003/orders/2b912b339251/provisioningstatus",  
                    "method": "GET",  
                    "headers": []  
                },  
                "patchOperation": {  
                    "uri": "/customers/6f4ce4d8-f42e-45e0-8661-92ad6ac9d003/orders/2b912b339251",  
                    "method": "PATCH",  
                    "headers": []  
                }  
            },  
            "totalPrice": 438.0,  
            "client": {},  
            "attributes": {  
                "objectType": "Order"  
            }  
        }  
    ],  
    "additionalInformation": [],  
    "attributes": {  
        "objectType": "CartCheckoutResult"  
    }  
}
```

#### Create order

***Request***:

```http
{  
    "BillingCycle": "monthly",  
    "ReferenceCustomerId": "6f4ce4d8-f42e-45e0-8661-92ad6ac9d003",  
    "LineItems": [  
        {  
            "LineItemNumber": 0,  
            "OfferId": "DZH318Z09V6F:0001:DZH318Z0BLD3",  
            "Quantity": 1,  
            "TermDuration": "P1Y",  
            "ProvisioningContext": {  
                "scope": "single",  
                "entitlementId": "cdd17cc7-14fe-4445-8650-1f52de705851"  
            },  
            "PurchaseCommitment": {  
                "amount": 0.05,  
                "currency": "usd",  
                "grain": "hourly"  
            }  
        }  
    ]  
}
```

***Response***:

```http
{  
    "id": "2b912b3392fd",  
    "alternateId": "2b912b3392fd",  
    "referenceCustomerId": "6f4ce4d8-f42e-45e0-8661-92ad6ac9d003",  
    "billingCycle": "monthly",  
    "currencyCode": "USD",  
    "currencySymbol": "US$",  
    "lineItems": [  
        {  
            "lineItemNumber": 0,  
            "provisioningContext": {  
                "scope": "single",  
                "entitlementId": "cdd17cc7-14fe-4445-8650-1f52de705851"  
            },  
            "offerId": "DZH318Z09V6F:0001:DZH318Z0BLD3",  
            "termDuration": "P1Y",  
            "transactionType": "New",  
            "friendlyName": "Compute savings plan, 1 Year",  
            "quantity": 1,  
            "pricing": {  
                "listPrice": 438.0,  
                "discountedPrice": 438.0,  
                "proratedPrice": 438.0,  
                "price": 438.0,  
                "extendedPrice": 438.0  
            },  
            "purchaseCommitment": {  
                "amount": 0.05,  
                "currency": "usd",  
                "grain": "hourly"  
            },  
            "links": {  
                "product": {  
                    "uri": "/products/DZH318Z09V6F?country=US",  
                    "method": "GET",  
                    "headers": []  
                },  
                "sku": {  
                    "uri": "/products/DZH318Z09V6F/skus/0001?country=US",  
                    "method": "GET",  
                    "headers": []  
                },  
                "availability": {  
                    "uri": "/products/DZH318Z09V6F/skus/0001/availabilities/DZH318Z0BLD3?country=US",  
                    "method": "GET",  
                    "headers": []  
                }  
            }  
        }  
    ],  
    "creationDate": "2023-05-18TT21:22:26.7034834Z",  
    "status": "pending",  
    "transactionType": "UserPurchase",  
    "links": {  
        "self": {  
            "uri": "/customers/6f4ce4d8-f42e-45e0-8661-92ad6ac9d003/orders/2b912b3392fd",  
            "method": "GET",  
            "headers": []  
        },  
        "provisioningStatus": {  
            "uri": "/customers/6f4ce4d8-f42e-45e0-8661-92ad6ac9d003/orders/2b912b3392fd/provisioningstatus",  
            "method": "GET",  
            "headers": []  
        },  
        "patchOperation": {  
            "uri": "/customers/6f4ce4d8-f42e-45e0-8661-92ad6ac9d003/orders/2b912b3392fd",  
            "method": "PATCH",  
            "headers": []  
        }  
    },  
    "client": {},  
    "attributes": {  
        "objectType": "Order"  
    }  
}
```

### Order and subscription API examples

#### Get an order by ID

***Response***:

```http
{
    "id": "2b912b3392fd",
    "alternateId": "2b912b3392fd",
    "referenceCustomerId": "6f4ce4d8-f42e-45e0-8661-92ad6ac9d003",
    "billingCycle": "monthly",
    "currencyCode": "USD",
    "currencySymbol": "US$",
    "lineItems": [
        {
            "lineItemNumber": 0,
            "subscriptionId": "005a9b31-3ba0-4ead-b4fe-ad11e072f7e7",
            "provisioningContext": {
                "scope": "single",
                "entitlementId": "cdd17cc7-14fe-4445-8650-1f52de705851"
            },
            "offerId": "DZH318Z09V6F:0001:DZH318Z0BLD3",
            "termDuration": "P1Y",
            "transactionType": "New",
            "friendlyName": "Compute savings plan, 1 Year",
            "quantity": 1,
            "purchaseCommitment": {
                "amount": 0.05,
                "currency": "usd",
                "grain": "hourly"
            },
            "links": {
                "product": {
                    "uri": "/products/DZH318Z09V6F?country=US",
                    "method": "GET",
                    "headers": []
                },
                "sku": {
                    "uri": "/products/DZH318Z09V6F/skus/0001?country=US",
                    "method": "GET",
                    "headers": []
                },
                "availability": {
                    "uri": "/products/DZH318Z09V6F/skus/0001/availabilities/DZH318Z0BLD3?country=US",
                    "method": "GET",
                    "headers": []
                }
            }
        }
    ],
    "creationDate": "2023-05-18TT21:22:26.7034834Z",
    "status": "completed",
    "transactionType": "UserPurchase",
    "links": {
        "self": {
            "uri": "/customers/6f4ce4d8-f42e-45e0-8661-92ad6ac9d003/orders/2b912b3392fd",
            "method": "GET",
            "headers": []
        },
        "provisioningStatus": {
            "uri": "/customers/6f4ce4d8-f42e-45e0-8661-92ad6ac9d003/orders/2b912b3392fd/provisioningstatus",
            "method": "GET",
            "headers": []
        },
        "patchOperation": {
            "uri": "/customers/6f4ce4d8-f42e-45e0-8661-92ad6ac9d003/orders/2b912b3392fd",
            "method": "PATCH",
            "headers": []
        }
    },
    "client": {},
    "attributes": {
        "objectType": "Order"
    }
}
```

#### Get all of a customer’s orders

***Response***:

```http
{
    "totalCount": 1,
    "items": [
        {
            "id": "2b912b3392fd",
            "alternateId": "2b912b3392fd",
            "referenceCustomerId": "6f4ce4d8-f42e-45e0-8661-92ad6ac9d003",
            "billingCycle": "monthly",
            "currencyCode": "USD",
            "currencySymbol": "US$",
            "lineItems": [
                {
                    "lineItemNumber": 0,
                    "subscriptionId": "005a9b31-3ba0-4ead-b4fe-ad11e072f7e7",
                    "provisioningContext": {
                        "scope": "single",
                        "entitlementId": "cdd17cc7-14fe-4445-8650-1f52de705851"
                    },
                    "offerId": "DZH318Z09V6F:0001:DZH318Z0BLD3",
                    "termDuration": "P1Y",
                    "transactionType": "New",
                    "friendlyName": "Compute savings plan, 1 Year",
                    "quantity": 1,
                    "purchaseCommitment": {
                        "amount": 0.05,
                        "currency": "usd",
                        "grain": "hourly"
                    },
                    "links": {
                        "product": {
                            "uri": "/products/DZH318Z09V6F?country=US",
                            "method": "GET",
                            "headers": []
                        },
                        "sku": {
                            "uri": "/products/DZH318Z09V6F/skus/0001?country=US",
                            "method": "GET",
                            "headers": []
                        },
                        "availability": {
                            "uri": "/products/DZH318Z09V6F/skus/0001/availabilities/DZH318Z0BLD3?country=US",
                            "method": "GET",
                            "headers": []
                        }
                    }
                }
            ],
            "creationDate": "2023-05-18TT21:22:26.7034834Z",
            "status": "completed",
            "transactionType": "UserPurchase",
            "links": {
                "self": {
                    "uri": "/customers/6f4ce4d8-f42e-45e0-8661-92ad6ac9d003/orders/2b912b3392fd",
                    "method": "GET",
                    "headers": []
                },
                "provisioningStatus": {
                    "uri": "/customers/6f4ce4d8-f42e-45e0-8661-92ad6ac9d003/orders/2b912b3392fd/provisioningstatus",
                    "method": "GET",
                    "headers": []
                },
                "patchOperation": {
                    "uri": "/customers/6f4ce4d8-f42e-45e0-8661-92ad6ac9d003/orders/2b912b3392fd",
                    "method": "PATCH",
                    "headers": []
                }
            },
            "client": {},
            "attributes": {
                "objectType": "Order"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/6f4ce4d8-f42e-45e0-8661-92ad6ac9d003/orders",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```

#### **Get a subscription by ID**

***Response***:

```http
{
    "id": "a67afaf0-2f79-4c12-8fd1-6005ed24bb28",
    "offerId": "DZH318Z09V6F:0001:DZH318Z0BLD3",
    "offerName": "Compute savings plan, 1 Year",
    "friendlyName": "Compute_Savings_Plan_123",
    "productType": {
        "id": "Azure",
        "displayName": "Azure",
        "subType": {
            "id": "SavingsPlan",
            "displayName": "SavingsPlan"
        }
    },
    "quantity": 1,
    "unitType": "Benefit",
    "hasPurchasableAddons": false,
    "creationDate": "2023-05-18T05:19:22.5478955Z",
    "effectiveStartDate": "2023-05-18T05:19:21.3362111Z",
    "commitmentEndDate": "2024-05-17T00:00:00Z",
    "billingCycleEndDate": "2024-05-17T00:00:00Z",
     "status": "active",
    "autoRenewEnabled": true,
    "isTrial": false,
    "billingType": "benefit",
    "billingCycle": "one_time",
    "termDuration": "P1Y",
    "renewalTermDuration": "",
    "isMicrosoftProduct": true,
    "partnerId": "",
    "attentionNeeded": false,
    "actionTaken": false,
    "contractType": "subscription",
    "links": {
        "product": {
            "uri": "/products/DZH318Z09V6F?country=US",
            "method": "GET",
            "headers": []
        },
"sku": {
            "uri": "/products/DZH318Z09V6F/skus/0001?country=US",
            "method": "GET",
            "headers": []
        },
        "availability": {
            "uri": "/products/DZH318Z09V6F/skus/0001/availabilities/DZH318Z0BLD3?country=US",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/customers/6f4ce4d8-f42e-45e0-8661-92ad6ac9d003/subscriptions/a67afaf0-2f79-4c12-8fd1-6005ed24bb28",
            "method": "GET",
            "headers": []
        }
    },
    "publisherName": "Microsoft Corporation",
    "lineItems": [
        {
            "id": "2131a68b-9796-4557-b628-354539ed66dc",
            "friendlyName": "Compute_Savings_Plan_123",
            "scope": {
                "type": "single",
                "entitlementId": "cdd17cc7-14fe-4445-8650-1f52de705851"
            },
            "autoRenewEnabled": true,
            "status": "active",
            "purchaseCommitment": {
                "amount": 0.05,
                "currency": "usd",
                "grain": "Hourly"
            }
        }
    ],
    "productOrderId": "2131a68b-9796-4557-b628-354539ed66dc",
    "orderId": "2b912b339251",
    "attributes": {
        "objectType": "Subscription"
    }
}
```

#### Get a customer’s subscriptions

***Response***:

```http
{
    "totalCount": 1,
    "items": [
        {
            "id": "a67afaf0-2f79-4c12-8fd1-6005ed24bb28",
            "offerId": "DZH318Z09V6F:0001:DZH318Z0BLD3",
            "offerName": "Compute savings plan, 1 Year",
            "friendlyName": "Compute_Savings_Plan_123",
            "productType": {
                "id": "Azure",
                "displayName": "Azure",
                "subType": {
                    "id": "SavingsPlan",
                    "displayName": "SavingsPlan"
                }
            },
            "quantity": 1,
            "unitType": "Benefit",
            "hasPurchasableAddons": false,
            "creationDate": "2023-05-18T05:19:22.5478955Z",
            "effectiveStartDate": "2023-05-18T05:19:21.3362111Z",
            "commitmentEndDate": "2024-05-17T00:00:00Z",
            "commitmentEndDateTime": "2024-05-17T23:59:59Z",
            "billingCycleEndDate": "2024-05-17T00:00:00Z",
            "billingCycleEndDateTime": "2024-05-17T23:59:59Z",
            "status": "active",
            "autoRenewEnabled": true,
            "isTrial": false,
            "billingType": "benefit",
            "billingCycle": "one_time",
            "termDuration": "P1Y",
            "renewalTermDuration": "",
            "isMicrosoftProduct": true,
            "partnerId": "",
            "attentionNeeded": false,
            "actionTaken": false,
            "contractType": "subscription",
            "links": {
                "product": {
                    "uri": "/products/DZH318Z09V6F?country=US",
                    "method": "GET",
                    "headers": []
                },
                "sku": {
                    "uri": "/products/DZH318Z09V6F/skus/0001?country=US",
                    "method": "GET",
                    "headers": []
                },
                "availability": {
                    "uri": "/products/DZH318Z09V6F/skus/0001/availabilities/DZH318Z0BLD3?country=US",
                    "method": "GET",
                    "headers": []
                },
                "self": {
                    "uri": "/customers/6f4ce4d8-f42e-45e0-8661-92ad6ac9d003/subscriptions/a67afaf0-2f79-4c12-8fd1-6005ed24bb28",
                    "method": "GET",
                    "headers": []
                }
            },
            "publisherName": "Microsoft Corporation",
            "lineItems": [
                {
                    "id": "2131a68b-9796-4557-b628-354539ed66dc",
                    "friendlyName": "Compute_Savings_Plan_123",
                    "scope": {
                        "type": "single",
                        "entitlementId": "cdd17cc7-14fe-4445-8650-1f52de705851"
                    },
                    "autoRenewEnabled": true,
                    "status": "active",
                    "purchaseCommitment": {
                        "amount": 0.05,
                        "currency": "usd",
                        "grain": "Hourly"
                    }
                }
            ],
            "productOrderId": "2131a68b-9796-4557-b628-354539ed66dc",
            "orderId": "2b912b339251",
            "attributes": {
                "objectType": "Subscription"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/6f4ce4d8-f42e-45e0-8661-92ad6ac9d003/subscriptions",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
