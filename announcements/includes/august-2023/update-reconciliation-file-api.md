---
title: include file
ms.topic: include
author: sourishdeb
ms.author: sodeb
ms.date: 08/14/2023
---

## Align reconciliation file column names with API JSON attributes

_Staying organized is critical when dealing with large datasets. We're planning to update the column names in a reconciliation file to match the JSON property or attribute names in the equivalent API._

- **Date**: August 14, 2023
- **Workspace**: Billing
- **Impacted audience**: All partners

We're updating the columns in the Billing Reconciliation file to match the attribute names of the equivalent API. This change should improve efficiency, faster data delivery, and ensure that the data within the reconciliation file can be linked to the API properly without any discrepancies.

This change makes troubleshooting easier, and helps keep the structure of the file organized. It also helps prevent issues with data accuracy or clarity.

We can expedite file delivery by using the same API V2 with an asynchronous approach and compressing the file to reduce the payload. We understand that this change may require some adjustments, but the changes are limited:

- For most columns, the first letter of the column name will be changed from uppercase to lowercase.
- For a few columns, column names are completely changed. For example, the column "PartnerEarnedCreditPercentage" in the daily rated usage file is renamed to "rateOfPartnerEarnedCredit," and its value changes from 15 to 0.15.

Details:

#### Column names that are changed from uppercase to lowercase, while the values remain the same

##### Reconciliation file: Invoice Reconciliation and Estimates

| **Column Name**            | **Expected Column Name**   |
| -------------------------- | -------------------------- |
| PartnerId                  | partnerId                  |
| CustomerId                 | customerId                 |
| CustomerName               | customerName               |
| CustomerDomainName         | customerDomainName         |
| CustomerCountry            | customerCountry            |
| InvoiceNumber              | invoiceNumber              |
| MpnId                      | mpnId                      |
| ResellerMpnId              | resellerMpnId              |
| OrderId                    | orderId                    |
| OrderDate                  | orderDate                  |
| ProductId                  | productId                  |
| SkuId                      | skuId                      |
| AvailabilityId             | availabilityId             |
| SkuName                    | skuName                    |
| ProductName                | productName                |
| ChargeType                 | chargeType                 |
| UnitPrice                  | unitPrice                  |
| Quantity                   | quantity                   |
| Subtotal                   | subtotal                   |
| TaxTotal                   | taxTotal                   |
| Currency                   | currency                   |
| PriceAdjustmentDescription | priceAdjustmentDescription |
| PublisherName              | publisherName              |
| PublisherId                | publisherId                |
| SubscriptionDescription    | subscriptionDescription    |
| SubscriptionId             | subscriptionId             |
| ChargeStartDate            | chargeStartDate            |
| ChargeEndDate              | chargeEndDate              |
| TermAndBillingCycle        | termAndBillingCycle        |
| EffectiveUnitPrice         | effectiveUnitPrice         |
| UnitType                   | unitType                   |
| AlternateId                | alternateId                |
| BillableQuantity           | billableQuantity           |
| BillingFrequency           | billingFrequency           |
| PricingCurrency            | pricingCurrency            |
| PCToBCExchangeRate         | pcToBCExchangeRate         |
| PCToBCExchangeRateDate     | pcToBCExchangeRateDate     |
| MeterDescription           | meterDescription           |
| ReservationOrderId         | reservationOrderId         |
| CreditReasonCode           | creditReasonCode           |
| SubscriptionStartDate      | subscriptionStartDate      |
| SubscriptionEndDate        | subscriptionEndDate        |
| ReferenceId                | referenceId                |
| ProductQualifiers          | productQualifiers          |
| PromotionId                | promotionId                |

##### Reconciliation file: Daily Rated Usage Reconciliation Billed and Unbilled

| **Column Name**         | **Expected Column Name** |
| ----------------------- | ------------------------ |
| PartnerId               | partnerId                |
| PartnerName             | partnerName              |
| CustomerId              | customerId               |
| CustomerName            | customerName             |
| CustomerDomainName      | customerDomainName       |
| CustomerCountry         | customerCountry          |
| MpnId                   | mpnId                    |
| InvoiceNumber           | invoiceNumber            |
| ProductId               | productId                |
| SkuId                   | skuId                    |
| AvailabilityId          | availabilityId           |
| SkuName                 | skuName                  |
| ProductName             | productName              |
| PublisherName           | publisherName            |
| PublisherId             | publisherId              |
| SubscriptionDescription | subscriptionDescription  |
| SubscriptionId          | subscriptionId           |
| ChargeStartDate         | chargeStartDate          |
| ChargeEndDate           | chargeEndDate            |
| UsageDate               | usageDate                |
| MeterType               | meterType                |
| MeterCategory           | meterCategory            |
| MeterId                 | meterId                  |
| MeterSubCategory        | meterSubCategory         |
| MeterName               | meterName                |
| MeterRegion             | meterRegion              |
| ResourceLocation        | resourceLocation         |
| ConsumedService         | consumedService          |
| ResourceGroup           | resourceGroup            |
| ResourceURI             | resourceUri              |
| ChargeType              | chargeType               |
| UnitPrice               | unitPrice                |
| Quantity                | quantity                 |
| UnitType                | unitType                 |
| BillingPreTaxTotal      | billingPreTaxTotal       |
| BillingCurrency         | billingCurrency          |
| PricingPreTaxTotal      | pricingPreTaxTotal       |
| PricingCurrency         | pricingCurrency          |
| ServiceInfo1            | serviceInfo1             |
| ServiceInfo2            | serviceInfo2             |
| Tags                    | tags                     |
| AdditionalInfo          | additionalInfo           |
| EffectiveUnitPrice      | effectiveUnitPrice       |
| PCToBCExchangeRate      | pcToBCExchangeRate       |
| PCToBCExchangeRateDate  | pcToBCExchangeRateDate   |
| EntitlementId           | entitlementId            |
| EntitlementDescription  | entitlementDescription   |
| CreditType              | creditType               |
| BenefitOrderId          | benefitOrderId           |
| BenefitId               | benefitId                |
| BenefitType             | benefitType              |

#### Column names that are changed to a different name, but the values remain the same

##### Reconciliation file: Invoice Reconciliation and Estimates

| **Column Name**            | **Expected Column Name** |
| -------------------------- | ------------------------ |
| Total                      | totalForCustomer         |

##### Reconciliation file: Daily Rated Usage Reconciliation Billed and Unbilled

| **Column Name** | **Expected Column Name** |
| --------------- | ------------------------ |
| Tier2MpnId      | resellerMpnId            |
| Unit            | unitOfMeasure            |

##### Column names that are changed to new names and new values

| **Column Name**               | **Value** | **Expected Column Name**  | **Expected Value** |
| ----------------------------- | --------- | ------------------------- | ------------------ |
| PartnerEarnedCreditPercentage | 15        | rateOfPartnerEarnedCredit | 0.15               |
| CreditPercentage              | 100       | rateOfCredit              | 1.00               |

##### Reconciliation file: Daily Rated Usage Reconciliation Billed and Unbilled 

#### API attribute changes

API attributes remain unchanged. There's no need to make any adjustments to the way you process our API responses.

#### Known limitations

N/A

#### Next steps

To ensure a smooth transition to the new column names:
- Notify users of this change
- Request that developers within your organization update the internal code to ingest and process reconciliation data using the CSV file.

We don't currently have a specific date for this change. When we do announce a date, we'll provide ample time to implement the change. We'd love to hear from you about any concerns you may have.

We appreciate your continued partnership and apologize for any inconvenience.
