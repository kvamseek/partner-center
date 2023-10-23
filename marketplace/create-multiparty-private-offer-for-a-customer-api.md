---
title: Create a multiparty private offer for a customer in Microsoft Partner Center
description: Use this method to create a new multiparty private offer for a customer. 
ms.subservice: partnercenter-marketplace-publisher
ms.service: marketplace
ms.topic: article
author: tortsuk
ms.author: tortsuk
ms.date: 07/18/2023
---

# Create a multiparty private offer for a customer

The ISV (originator) and the collaborating partner (seller) should use the same set of API calls to create a private offer for a customer. Here's the expected flow.

1. ISV creates the offer and submits for selling partner visibility
1. ISV notifies the selling partner (via email or other methods) the offer is now available for selling partner edits
1. Selling partner reviews and completes configuring the private offer and submits for end customer visibility

Here's the method to call for the creation of the offer.

## Request

```
POST https://graph.microsoft.com/rp/product-ingestion/configure?$version=2022-07-01
```

## Request header

| Header        | Type    | Description    |
| ------------- | ------- | -------------- |
| Authorization | String  | Required. The Azure AD access token in the form ```Bearer <token>```. |

Optional: clientID

## Request parameters

**$version** - required. This is the version of the schema that is being used in the request.

## Request body

The following options mirror the options in Partner Center when creating a multiparty private offer for a customer. These options are defined by the following **offerPricingType** values:

| offerPricingType value  | Partner Center private offer creation option equivalent           |
| ----------------------- | ----------------------------------------------------------------- |
| editExistingOfferPricingOnly | **Customize pricing for existing public offer and plans** - Use this option to create a private offer for all transactable offer types: SaaS, Azure Virtual Machines, and Azure Applications. You can customize your partner pricing via absolute pricing or percentage discounts.           |
| saasNewCustomizedPlans       | **Customize pricing, meter quantities, and user limits for SaaS offer** - Use this option to create a private offer for a SaaS plan by customizing your absolute partner price, metering dimension quantities, and user limits.                                                              |
| vmSoftwareReservations       | **Customize pricing and specific quantities for VM software reservation offers** - Use this option to create a multiparty private offer to sell VM software reservations (1-year or 3-year) and customize the absolute partner price, vCPU size, quantities, duration, and payment schedule. |

For the previous three pricing type options, plan-specific resources requirements can vary. For details, see the following table:

| Resource name  | editExistingOfferPricingOnly  | saasNewCustomizedPlans  | vmSoftwareReservations  |
| -------------- | ----------------------------- |------------------------ | ----------------------- |
| pricing.Plan                       | Set this to the plan ID of the public plan to be configured in the request body | Not applicable                                                                                      | Not applicable                                                                                                        |
| pricing.basePlan                   | Not applicable                                                                  | Set this to the plan ID of the public plan to be configured in the request body                     | Set this to the plan ID of the public plan to be configured in the request body                                       |
| pricing.newPlanDetails.name        | Not applicable                                                                  | Set this to the name of the new plan that will be shown to the customer in the request body         | Not applicable to the request body, will be system generated and available in the response of the job when completed. |
| pricing.newPlanDetails.description | Not applicable                                                                  | Set this to the description that will be shown to the customer for the new plan in the request body | Not applicable to the request body, will be system generated and available in the response of the job when complete.  |

The request body varies depending on the caller role. Use **privateOfferType** to distinguish ISV caller from selling partner caller.

| Caller role          | privateOfferType value        |
| -------------------- | ----------------------------- |
| ISV (Originator)         | multipartyPromotionOriginator     |
| Selling Partner (Seller) | multipartyPromotionChannelPartner |

### Request body samples

#### Sample request body by ISV to create the offer using discount pricing to customize pricing for existing public plan only

The ISV (originator) is required to provide all the foundational details of the offer. This must include a name.

```JSON
{
 "$schema": "https://schema.mp.microsoft.com/schema/configure/2022-07-01",
  "resources": [ 
    {
       "$schema": "https://schema.mp.microsoft.com/schema/private-offer/2023-07-15", 
"resourceName": "privateOffer",
       "name": "privateOffercustomer1705",
       "state": "live",
       "privateOfferType": "multipartyPromotionOriginator",
       "offerPricingType": "editExistingOfferPricingOnly",
       "variableStartDate": true,
       "end": "2022-01-31",
       "acceptBy": "2022-02-28",
"termsAndConditionsDocs": [
                {
                    "sasUrl": "https://promotionpmeprod.blob.core.windows.net/promotionsblobdata/44c2b38a-fa64-4861-806c-6c486ec19b6d-769f3960-45af-42db-ab3b-6391841683d6",
                    "fileName": "Test1.pdf",
                    "customerFacingDocumentName": "Test1 T&C"
                }            ],
       "notificationContacts": [ "amy@contoso.com" ],
       "beneficiaries": [ 
          { "id": "xxxxxx-2163-5eea-ae4e-d6e88627c26b:6ea018a9-da9d-4eae-8610-22b51ebe260b_2019-05-31", "description": "Top First Customer"}
       ], 
"partners": [
                {
                    "id": "12345678",
                    "partnerName": "Market Place Test",
                    "location": "United States"
                }
            ],
       "pricing": [ 
          { "product": "product/34771906-9711-4196-9f60-4af380fd5042", "plan":"plan/123456","discountType": "percentage", "discountPercentage": 5 }
       ],
"notes": "ISV 123"
    }
  ]
}
```

#### Sample request body using absolute pricing to customize pricing for existing public plan only

If you're using absolute pricing instead of percentage-based discounting, you can create a new resource above the multiparty private offer resource that defines the absolute pricing, then include that newly created resource as another object in the resources list of the configure schema.

Use this method to obtain the pricing resource for your existing public plan, edit the prices, and then use the edited resource for your offer.

```
GET https://graph.microsoft.com/rp/product-ingestion/price-and-availability-private-offer-plan/{productId}?plan={planId}&$version=2023-07-15
```

#### Sample absolute pricing resource

```JSON
{
    "$schema": "https://schema.mp.microsoft.com/schema/price-and-availability-private-offer-plan/2023-07-15",
    "resourceName": "newSimpleAbsolutePricing",
    "product": "product/7ba807c8-386a-4efe-80f1-b97bf8a554f8",
    "plan": "plan/987654",
    "offerPricingType": "editExistingOfferPricingOnly",
    "pricing": {
        "recurrentPrice": {
            "priceInputOption": "usd",
            "prices": [
                {
                    "pricePerPaymentInUsd": 1,
                    "billingTerm": {
                        "type": "month",
                        "value": 1
                    }
                },
                {
                    "pricePerPaymentInUsd": 2,
                    "paymentOption": {
                        "type": "month",
                        "value": 1
                    },
                    "billingTerm": {
                        "type": "year",
                        "value": 1
                    }
                }
            ]
        },
        "customMeters": {
            "priceInputOption": "usd",
            "meters": {
                "meter1": {
                    "pricePerPaymentInUsd": 1
                }
            }
        }
    }
}

```

#### Include that resource as an object in the pricing module

```JSON
[
    {
        "product": "product/34771906-9711-4196-9f60-4af380fd5042",
        "plan": "plan/123456",
        "discountType": "percentage",
        "discountPercentage": 5
    },
    {
        "product": "product/7ba807c8-386a-4efe-80f1-b97bf8a554f8",
        "plan": "plan/987654",
        "discountType": "absolute",
        "priceDetails": {
            "resourceName": "newSimpleAbsolutePricing"
        }
    }
]
```

#### Sample request body using absolute pricing to customize pricing, metering quantities, and user limits for SaaS offer

Use the following method to create an absolute price and availability resource for the private offer.

```
GET https://graph.microsoft.com/rp/product-ingestion/price-and-availability-private-offer-plan/{productId}?plan={planId}&$version=2023-07-15
```

#### Sample absolute pricing resource for a flat rate SaaS offer that customizes price and meter quantities

```JSON
{
    "$schema": "https://schema.mp.microsoft.com/schema/price-and-availability-private-offer-plan/2023-07-15",
    "product": "product/7ba807c8-386a-4efe-80f1-b97bf8a554f8",
    "resourceName": "newSaaSPlanAbsolutePricing",
    "plan": "plan/123456”,
    "offerPricingType": "saasNewCustomizedPlans",
    "pricing": {
        "recurrentPrice": {
            "recurrentPriceMode": "flatRate",
            "priceInputOption": "usd",
            "prices": [
                {
                    "billingTerm": {
                        "type": "month",
                        "value": 1
                    },
                    "paymentOption": {
                        "type": "month",
                        "value": 1
                    },
                    "pricePerPaymentInUsd": 0.1
                },
                {
                    "billingTerm": {
                        "type": "year",
                        "value": 1
                    },
                    "paymentOption": {
                        "type": "month",
                        "value": 1
                    },
                    "pricePerPaymentInUsd": 0.12
                }
            ]
        },
        "customMeters": {
            "priceInputOption": "usd",
            "meters": {
                "meter1": {
                    "includedQuantities": [
                        {
                            "billingTerm": {
                                "type": "month",
                                "value": 1
                            },
               "quantity": 10.0,
                            "isInfinite": false
                        },
                        {
                            "billingTerm": {
                                "type": "year",
                                "value": 1
                            },
               "quantity": 15.0,
                            "isInfinite": false
                        }
                    ]
                },
                "meter2": {
                    "includedQuantities": [
                        {
                            "billingTerm": {
                                "type": "month",
                                "value": 1
                            },
                            "isInfinite": true
                        },
                        {
                            "billingTerm": {
                                "type": "year",
                                "value": 1
                            },
                            "isInfinite": true
                        }
                    ]
                }
            }
        }
    }
}
```

#### Sample absolute pricing resource for a per user SaaS offer that customizes price and user limits

```JSON
{
    "$schema": "https://schema.mp.microsoft.com/schema/price-and-availability-private-offer-plan/2023-07-15",
    "resourceName": "newSaaSPlanAbsolutePricing",
    "product": "product/7ba807c8-386a-4efe-80f1-b97bf8a554f8",
    "plan": "plan/123456",
    "offerPricingType": "saasNewCustomizedPlans",
    "pricing": {
        "recurrentPrice": {
            "recurrentPriceMode": "perUser",
            "priceInputOption": "usd",
            "userLimits": {
                "min": 20,
                "max": 100
            },
            "prices": [
                {
                    "billingTerm": {
                        "type": "month",
                        "value": 1
                    },
                    "paymentOption": {
                        "type": "month",
                        "value": 1
                    },
                    "pricePerPaymentInUsd": 0.01
                },
                {
                    "billingTerm": {
                        "type": "year",
                        "value": 1
                    },
                    "paymentOption": {
                        "type": "year",
                        "value": 1
                    },
                    "pricePerPaymentInUsd": 0.02
                }
            ]
        }
    }
}
```

#### Include that resource as an object in the pricing module

```JSON

{
 "$schema": "https://schema.mp.microsoft.com/schema/configure/2022-07-01",
  "resources": [ 
    {
       "$schema": "https://schema.mp.microsoft.com/schema/private-offer/2023-07-15", 
       "name": "privateOffercustomer1705",
       "state": "live",
       "privateOfferType": "multipartyPromotionOriginator",
       "offerPricingType": "newSimpleAbsolutePricing",
       "variableStartDate": true,
       "end": "2022-01-31",
       "acceptBy": "2022-02-28",
       "partners": [
         {
            "id": "12345678",
            "partnerName": "Market Place Test",
            "location": "United States"
         }
        ],
       "termsAndConditionsDocs": [
        {
             "sasUrl": "https://promotionpmeprod.blob.core.windows.net/promotionsblobdata/44c2b38a-fa64-4861-806c-6c486ec19b6d-769f3960-45af-42db-ab3b-6391841683d6",
             "fileName": "Test1.pdf",
             "customerFacingDocumentName": "Test1 T&C"
        }            ],
       "notificationContacts": [ "amy@contoso.com" ],
       "beneficiaries": [ 
          { "id": "xxxxxx-2163-5eea-ae4e-d6e88627c26b:6ea018a9-da9d-4eae-8610-22b51ebe260b_2019-05-31", "description": "Top First Customer"}
       ], 
       "pricing": [ 
          {
           "product": "product/7ba807c8-386a-4efe-80f1-b97bf8a554f8",
           "discountType": "absolute",
           "priceDetails": {
              "resourceName": "newSaaSPlanAbsolutePricing"
             }
           "basePlan": "plan/123456",
                "newPlanDetails": {
                "name": "newPlanName",
                "description": "newPlanDescription"
             }
        ],
 "notes": "ISV 123"
     }
  ]
}
```

#### Sample request body using absolute pricing to customize pricing and specific quantities for VM software reservation offers

Use the following method to create an absolute price and availability resource for the offer.

```
GET https://graph.microsoft.com/rp/product-ingestion/price-and-availability-private-offer-plan/{productId}?plan={planId}&$version=2023-07-15
```

#### Sample absolute pricing resource for a VM offer that customizes price and quantities

```JSON
{
    "$schema": "https://schema.mp.microsoft.com/schema/price-and-availability-private-offer-plan/2023-07-15",
    "resourceName": "newVMSRAbsolutePricing",
    "product": "product/7ba807c8-386a-4efe-80f1-b97bf8a554f8",
    "offerPricingType": "vmSoftwareReservations",
    "plan": "plan/987654",
    "softwareReservation": {
        "reservationDuration": {
            "type": "year",
            "value": 1
         },
        "paymentSchedule": {
            "type": "year",
            "value": 1
         },
        "vmPrices": {
            "36Core": {
                "quantity": 4.0,
                "unitPricePerPaymentPeriodInUsd": 0.04
            }
        }
    }       
}
```

#### Include that resource as an object in the pricing module

```JSON
{
 "$schema": "https://schema.mp.microsoft.com/schema/configure/2022-07-01",
  "resources": [ 
    {
       "$schema": "https://schema.mp.microsoft.com/schema/private-offer/2023-07-15", 
       "name": "privateOffercustomer1705",
       "state": "live",
       "privateOfferType": "multipartyPromotionOriginator",
       "offerPricingType": "vmSoftwareReservations",
       "variableStartDate": true,
       "end": "2022-01-31",
       "acceptBy": "2022-02-28",
       "partners": [
         {
            "id": "12345678",
            "partnerName": "Market Place Test",
            "location": "United States"
         }
        ],
       "termsAndConditionsDocs": [
        {
             "sasUrl": "https://promotionpmeprod.blob.core.windows.net/promotionsblobdata/44c2b38a-fa64-4861-806c-6c486ec19b6d-769f3960-45af-42db-ab3b-6391841683d6",
             "fileName": "Test1.pdf",
             "customerFacingDocumentName": "Test1 T&C"
        }            ],
       "notificationContacts": [ "amy@contoso.com" ],
       "beneficiaries": [ 
          { "id": "xxxxxx-2163-5eea-ae4e-d6e88627c26b:6ea018a9-da9d-4eae-8610-22b51ebe260b_2019-05-31", "description": "Top First Customer"}
       ], 
       "pricing": [ 
          {
           "product": "product/7ba807c8-386a-4efe-80f1-b97bf8a554f8",
           "discountType": "absolute",
           "priceDetails": {
              "resourceName": "newVMSRAbsolutePricing"
             }
           "basePlan": "plan/987654"
        ],
 "notes": "ISV 123"
     }
  ]
}
```

#### Sample request by the partner to complete the creation of the offer

The selling partner should use the multiparty private offer ID provided by the ISV to configure the customer adjustment % (markup), selling partner custom agreements, prepared by, and selling partner contacts.

The following example is based on the response body returned when retrieving the offer details using the offer ID.

```JSON
{
 "$schema": "https://schema.mp.microsoft.com/schema/configure/2022-07-01",
  "resources": [ 
    {
       "$schema": "https://schema.mp.microsoft.com/schema/private-offer/2023-07-15", 
"resourceName": "privateOffer",
       "name": "privateOffercustomer1705",
       "state": "live",
       "privateOfferType": "multipartyPromotionChannelPartner",
       "offerPricingType": "editExistingOfferPricingOnly",
       "variableStartDate": true,
       "end": "2022-01-31",
       "acceptBy": "2022-02-28",
       "preparedBy": "tester@microsoft.com",
"originatorTermsAndConditionsDocs": [
                {
                    "sasUrl": "https://promotionpmeprod.blob.core.windows.net/promotionsblobdata/44c2b38a-fa64-4861-806c-6c486ec19b6d-769f3960-45af-42db-ab3b-6391841683d6",
                    "fileName": "Test1.pdf",
                    "customerFacingDocumentName": "Test1 T&C"
                }            ],
"termsAndConditionsDocs": [
                {
                    "sasUrl": "https://promotionpmeprod.blob.core.windows.net/promotionsblobdata/44c2b38a-fa64-4861-806c-6c486ec19b6d-769f3960-45af-42db-ab3b-6391841683d6",
                    "fileName": "Test1.pdf",
                    "customerFacingDocumentName": "Test1 T&C"
                }            ],

       "notificationContacts": [ "amy@contoso.com" ],
       "beneficiaries": [ 
          { "id": "xxxxxx-2163-5eea-ae4e-d6e88627c26b:6ea018a9-da9d-4eae-8610-22b51ebe260b_2019-05-31", "description": "Top First Customer"}
       ], 
"partners": [
                {
                    "id": "12345678",
                    "partnerName": "Market Place Test",
                    "location": "United States"
                }
            ],
       "originatorPricing": [ 
          { 
        "product": "product/34771906-9711-4196-9f60-4af380fd5042",
        "plan":"plan/123456",
        "discountType": "percentage", 
        "discountPercentage": 5 
        "markupPercentage": 1.0
        }
     ],
    "lastModified": "2023-01-19",
        "eTag": "\"7f020249-0000-0800-0000-63c9b4ca0000\"",
    }
  ]
}
```

#### Key call-outs in the previous example

- Selling partner must provide the **preparedBy** attribute.
- ISV custom terms and conditions are viewable but can't be edited by the selling partner, they're captured in the resource **originatorTermsAndConditionsDocs**.
- Selling partner can upload their own custom term and condition in the **termsAndConditionsDocs** resource.
- Selling partner can add their own contacts to be notified of the offer in the **notificationContacts** resource.
- Beneficiary and Partners attributes are viewable but can't be edited by the selling partner.
- Pricing resource is displayed as **originatorPricing**, **markupPercentage** is required and must be provided by the selling partner when submitting, all other attributes in the pricing resource are read-only.

## Response

The response contains the **jobId** you can use later to poll the status:

```JSON
{
    "$schema": "https://schema.mp.microsoft.com/schema/configure-status/2022-07-01",
    "jobId": "c32dd7e8-8619-462d-a96b-0ac1974bace5",
    "jobStatus": "notStarted",
    "jobResult": "pending",
    "jobStart": "2021-12-21T21:29:54.9702903Z",
    "jobEnd": "0001-01-01",
    "errors": []
}
```

### Error codes

| HTTP status code | Description              |
| ---------------- | ------------------------ |
| 401              | Authentication Error: Ensure you're using a valid Azure AD access token. |
| 400              | Schema Validation. Ensure your request body is following the correct schema and includes all required fields. |

## Next steps

- [Manage existing private offers](manage-existing-private-offers-via-api.md)
- [Job status and retrieve private offer detail API](job-status-and-retrieve-private-offer-detail-api.md)
- [Troubleshooting and additional resources](private-offer-api-troubleshooting.md)
