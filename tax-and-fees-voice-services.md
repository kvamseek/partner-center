---
title: Regional PSTN service taxes and fees
description: As an Office 365 partner who transacts Microsoft 365 Voice products, you may be subject to regional taxes, fees, or regulatory requirements for PSTN services.
ms.topic: article
ms.date: 11/08/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-billing
author: sourishdeb
ms.author: sodeb
---

# Regional taxes and regulations for Public Switched Telephone Network (PTSN) services

**Appropriate roles**: Global admin | User admin | Admin agent

Public Switched Telephone Network (PSTN) services in some jurisdictions may be subject to special tax and regulatory requirements that may affect partner order and invoicing.

In the United States, including Puerto Rico, PSTN services, which include Audio Conferencing, Calling Plans, and Communication Credits, are subject to special tax and regulatory requirements. In the United States and Puerto Rico, Microsoft prices PSTN services as tax-inclusive. Unique PSTN taxes and regulations will affect Office 365 partners transacting Microsoft 365 Voice products. If a partner marks up the price of a Microsoft PSTN Service, they may be responsible for calculating and remitting PSTN taxes and fees.

## Partner recommendations

Engage your tax and legal counsel to understand your organization's responsibility regarding PSTN services' regulation, taxes and fees, and other potential liabilities.

## Invoice presentation and partner reconciliation file

Cloud Solution Provider (CSP) invoices and CSP reconciliation files in the United States, Puerto Rico, and Canada, which include Skype for Business PSTN and Microsoft 365 Voice services, will provide separate line items for the PSTN and non-PSTN components.

Additionally, CSP invoices will display the following footnote:

* The price displayed is a charge for Audio Conferencing and Calling Plan Services. Any applicable transactional taxes are charged exclusively of the amount shown except for sales made within the United States. In the United States, the price displayed is tax inclusive, as it includes a charge for the Calling Plan and Audio Conferencing Services and a charge for the taxes and fees we are required to charge. Audio Conferencing and Calling Plan Services are serviced by the Microsoft Affiliate authorized to provide them. See Microsoft Volume Licensing for details.

## Reconciliation file example

Office 365 Enterprise E5 presents on reconciliation file as two line items with identical names and identical IDs, but each line item has a unique unit price (example: $28.40 and $2.00). This separates the Skype for Business PSTN Conferencing component of the Office 365 offer, so you can correctly apply taxes.

### Partner reconciliation example #1 (select columns)

|**Durable_offer_ID**|**Offer_Name**|**Subscription_Start_Date**|**Subscription_End_Date**|**Charge_Start_Date**|**Charge_End_Date**|**Charge_Type**|**Unit_Price**|
|:----:|:----:|:----:|:----:|:----:|:----:|:----:|:----:|
|a044b16a-1861-4308-8086-a3a3b506fac2   |Office 365 Enterprise E5   |8/10/2019 0:00   |8/11/2019 0:00   |8/11/2019 0:00|9/10/2019 0:00   |Cycle fee   |28.40   |
|a044b16a-1861-4308-8086-a3a3b506fac2   |Office 365 Enterprise E5   |8/10/2019 0:00   |8/11/2019 0:00   |8/11/2019 0:00   |9/10/2019 0:00   |Cycle fee   |2.00   |

### Partner reconciliation example #2

Microsoft 365 Business Voice available in Canada has additional PSTN taxable components that are consolidated on CSP Invoice (similar to Office 365 E5, two line items are presented, one for PSTN components and the other for non-PSTN components). The CSP Reconciliation file for Microsoft 365 Business Voice will display all PSTN taxable components individually (individual PSTN components will not be consolidated in .CSV or API tool). The summation of order details and billed amounts for customers found in the reconciliation file will match the CSP Invoice.

## Additional resources

For more details, visit the [Microsoft 365 for Partners](https://www.microsoft.com/microsoft-365/partners/) site.
