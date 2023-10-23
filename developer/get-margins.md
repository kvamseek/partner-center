---
title: Get margins
description: Gets a list of margins for a given partner.
ms.date: 10/03/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: migolova
ms.author: migolova
---

# Get margins

**Applies to**: Partner Center

**Appropriate roles**: Global admin | Admin agent

As a partner in the CSP program, you can call the GetMargins API to get a list of private offer margins extended to you by ISV publishers.

## Prerequisites

Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with both standalone App and App+User credentials.

## REST request

[GET] /v1/margins

### Request syntax

| Method   | Request URI         |
|----------|---------------------|
| **GET**  | [*{baseURL}*](partner-center-rest-urls.md)/v1/margins HTTP/1.1 |

### Request headers

For more information, see [Partner Center REST headers](headers.md).

### Request body

None

### Request example

```http
GET https://api.partnercenter.microsoft.com/v1/margins HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
X-Locale: en-US
```

## REST response

If successful, this request returns a list of private offer margins. The ISV publisher can configure the private offer margin either as a fixed percentage discount, which is applied to the original price of the offer, or as a custom price that overrides the original price of the offer. Both margin types are returned in GetMargins API response.

Each line item in the response contains start and end dates. The private offer margin will only be applied on purchases that are made within those two dates. Purchases made outside of that time frame won't get the benefit of the private offer margin.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and more debugging information. Use a network trace tool to read this code, error type, and more parameters. For the full list, see [Error Codes](error-codes.md).

### Response examples

#### Percentage-based private offer margin

In this example, the ISV publisher configured the private offer margin as a fixed percentage discount from the original price of the offer. The discount is shown in the "percentageMargin" property. Because this private offer is extended for a specific SKU, SKU information such as SKU name and SKU ID is specified. If the ISV publisher chose to extend the private offer for all SKUs, this information wouldn't be specified.

#### Response

```html
HTTP/1.1 200 OK
Content-Type: application/json
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
{
"pageSize": 1,
"totalSize": 1,
"results": [
{
      "id": "1aa125798b04_01a14813-f6d1-494a-ace1-b84525cf3db4",
      "type": "Percentage",
      "productId": "DZH318Z0HJ49",
      "publisherName": "Test Publisher Name",
      "productTitle": "Test Offer Beta",
      "skuTitle": "Test Offer Beta SKU 1",
      "skuId": "0001",
      "productType": "SaaS",
      "marginPercentage": 10.0,
      "startDate": "2022-02-24T18:38:02.8104364Z",
      "endDate": "2022-04-30T23:59:59Z",
      "status": "live",
      "statusDate": "2022-02-24T18:38:02.8104364Z"
}
]
}
```

#### Custom price private offer margin

In this example, the ISV publisher configured the private offer margin as a custom price that overrides the original price of their SaaS solution with custom meters. Instead of a marginPercentage property as in the previous example, this line item contains a priceConfiguration property that contains the details of the custom pricing.

The pricingModel in this example is listed as a "flat rate" model, meaning that you pay a set amount per term. If the ISV is charging a set amount per user, then the pricingModel would say "per user."

The "purchase" array contains the pricing details for each term duration. The ISV in this example has only configured a "Monthly" term duration, but the "purchase" array could also contain an "Annual" term duration. Within the purchase configuration for a given term, includedMeterQuantities states the amounts for each custom meter that are included in the price. Because the ISV publisher can configure different price points for different customer markets, the marketSetPrices array contains the custom price for each market and currency that the private offer is available in. In this example, the flat rate of 448.75262 GPB for a customer in the GB (United Kingdom) market includes 20 devices and 30,000 emails per month.

The "consumption" array contains the overage pricing information for each custom meter. If the ISV's product doesn't have custom meters, then this array will be empty. You'll notice that the consumption array contains a line item for each custom meter that is listed in the "includedMeterQuantities". In this example, if you consume more than 20 devices per month, you would pay an additional 0.44729 GBP per 1 additional device per month. If you consume more than 30,000 emails, you would pay 0.38765 GBP per 100 additional emails per month.

#### Response

```html
HTTP/1.1 200 OK
Content-Type: application/json
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
{
"pageSize": 1,
"totalSize": 1,
"results": [
{
      "id": "15680381dbad_fe3f0bc2-6372-48af-bbec-2df83918dbf2",
      "type": "CustomPrice",
      "productId": "DZH318Z0BDGN",
      "publisherName": "Test Publisher Name",
      "productTitle": "Test Offer Gamma",
      "skuTitle": "Test Offer Gamma SKU 1",
      "skuId": "0001",
      "productType": "SaaS",
      "priceConfiguration": {
        "pricingModel": "Flat rate",
        "purchase": [
          {
            "termDuration": "Monthly",
            "includedMeterQuantities": [
              "20 device",
              "30000 email"
            ],
            "startDate": "2022-01-31T17:49:25.1346812Z",
            "endDate": "2028-08-31T23:59:59Z",
            "marketSetPrices": [
              {
                "markets": [
                  "GB"
                ],
                "currency": "GBP",
                "customPrice": 447.29387
              },
              {
                "markets": [
                  "BG",
                  "FI",
                  "IT",
                  "RO"
                ],
                "currency": "GBP",
                "customPrice": 448.75262
              }
            ]
          }
        ],
        "consumption": [
          {
            "meterType": "device",
            "unitofMeasure": "per 1 device",
            "startDate": "2022-01-01T00:00:00Z",
            "endDate": "2028-08-31T23:59:59Z",
            "marketSetPrices": [
              {
                "markets": [
                  "GB"
                ],
                "currency": "GBP",
                "customPrice": 0.44729
              },
              {
                "markets": [
                  "BG",
                  "FI",
                  "IT",
                  "RO"
                ],
                "currency": "GBP",
                "customPrice": 0.44875
              }
            ]
          },
          {
            "meterType": "email",
            "unitofMeasure": "per 100 emails",
            "startDate": "2022-01-01T00:00:00Z",
            "endDate": "2028-08-31T23:59:59Z",
            "marketSetPrices": [
              {
                "markets": [
                  "GB"
                ],
                "currency": "GBP",
                "customPrice": 0.38765
              },
              {
                "markets": [
                  "BG",
                  "FI",
                  "IT",
                  "RO"
                ],
                "currency": "GBP",
                "customPrice": 0.38892
              }
            ]
          }
        ]
      },
      "startDate": "2022-01-31T17:49:25.1346812Z",
      "endDate": "2028-08-31T23:59:59Z",
      "status": "live",
      "statusDate": "2022-01-31T17:49:25.1346812Z"
    }
  ]
}
```

The above example should result in the following.

:::image type="content" source="./media/get-margins-pricing.png" alt-text="Screenshot showing a custom pricing page for a sample ISV offer.":::
