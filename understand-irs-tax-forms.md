---
title: Understand IRS tax forms issued by Microsoft
description: Learn about the tax forms issued by Microsoft, including who will receive them and when they're made available.
ms.topic: article
author: deeparamani
ms.author: deramani
ms.reviewer: leannlu
ms.service: partner-dashboard
ms.subservice: partnercenter-payouts
ms.date: 01/05/2022
---
# Understand IRS tax forms issued by Microsoft

**Appropriate roles**: Global admin

You might receive one or more tax forms from Microsoft each year, depending on your sales, your location, and the number of payments you receive. Microsoft is required to issue these forms and file them with the Internal Revenue Service (IRS).

This article will help you to understand these tax forms, including who receives them and when they're available.

## Types of tax forms

| IRS tax form | Description | Availability |
|--------------|-------------|--------------|
|1099-MISC, 1099-K | Related to sales activity and/or payments made to you for participation in Microsoft marketplaces | Printed forms are postmarked on or before **January 31**, and .pdf copies are available in the Partner Center [Payout and tax profiles](https://partner.microsoft.com/dashboard/payee/profiles/partner/manage). |
|1042-S | Related to payments made to you that are subject to United States withholding tax | Printed forms are postmarked on or before **March 15**, and .pdf copies are available in Partner Center (in **Partner Center Developer Settings** under **Payout and tax > Payout and tax profiles**) at the same time.  |

> [!NOTE]
> Tax forms are sent to the address you entered in your tax profile when you [set up your payout account and tax forms](set-up-your-payout-account.md). If your address has changed, be sure to update the address in your **Tax profile**.

The tax forms are sent to you from the following addresses:

**US Person (under US tax law):**

| Business Group         | Legal Entity          | Address                                          |
|------------------------|-----------------------|--------------------------------------------------|
| Windows, Office, Azure, Minecraft, MS Flight Simulator | Microsoft Corporation | One Microsoft Way<br>Redmond, WA 98052 USA       |
| Advertising            | Microsoft Online, Inc. | 6880 Sierra Center Parkway<br>Reno, NV 98511 USA |

**Foreign Person (under US tax law):**

| Business Group         | Legal Entity          | Address                                          |
|------------------------|-----------------------|--------------------------------------------------|
| Windows, Office, Azure | Microsoft Ireland Operations Limited (Payment is made by Microsoft Corporation via Microsoft Ireland acting as qualified intermediary for Microsoft Corporation.) | One Microsoft Place<br>South County Business Park<br>Leopardstown, Dublin 18, D18 P521, Ireland|
| Advertising          | Microsoft Ireland Operations Limited (Payment is made by Microsoft Online, Inc. via Microsoft Ireland acting as payout agent for Microsoft Online, Inc.) | One Microsoft Place<br>South County & Business Park<br>Leopardstown, Dublin 18, D18 P521, Ireland |
| Advertising            | Microsoft Online, Inc. | 6880 Sierra Center Parkway<br>Reno, NV 98511 USA |

*Citizens of the following countries/regions earning advertising revenue are paid through Microsoft Ireland Operations Limited:*

Austria, Belgium, Bulgaria, Croatia, Cyprus, Czechia, Denmark, Estonia, Finland, France, Germany, Greece, Hungary, Ireland, Isle of Man, Italy, Latvia, Liechtenstein, Lithuania, Luxembourg, Malta, Monaco, Netherlands, Norway, Poland, Portugal, Romania, Slovakia, Slovenia, South Africa, Spain, Sweden, Switzerland, United Kingdom

## For developers who are US Persons (under US tax law)

| If I'm a United States developer selling paid apps and...   | I should receive this form: |
|------------------------|-----------------------|
| I had **greater than 200 app sales** with a total purchase amount of these sales **greater than USD20,000** in the applicable tax year (**not** counting sales made in Brazil and China through the Microsoft Store on Windows 10.)| **1099-K:**<br/>Filer: Microsoft Corporation<br/>EIN: \*\*\*\*\*4442<br/><br/>**Important:** Form 1099-K contains **gross purchase** amounts, not payments made to you. <br/><br/> **How do I the reconcile 1099-K tax form with payout statements?**<br/> <br>- Starting in tax year 2021, any unpaid orders and any transactions that aren't eligible for partner earnings are excluded from gross revenue.<br/><br>- All paid earnings accrued from January 1 to December 31, 2021 are included, except for adjustments, Commercial Marketplace program earnings from the country Brazil, and Microsoft Store program earnings from Brazil and China.|
| I received **at least USD10 in payments** for (i) app sales made in Brazil or China through the Microsoft Store on Windows 10 or (ii) sales in the Minecraft Marketplace or MS Flight Simulator Marketplace.<br/><br/>**OR**<br/><br/>I received at least USD600 in payments not related to app sales from Microsoft in the applicable tax year (for example, incentive payments or payments from a contest or promotion).| **1099-MISC:**<br/>Payer: Microsoft Corporation<br/>EIN: \*\*\*\*\*4442<br/><br/>**Important:** Certain business entities won't receive 1099-MISC forms regardless of the payment amounts received from Microsoft. For more information, see your tax professional.|
| None of the preceding apply.| None |
| <br/><br/>**If I'm a United States developer selling ads in apps and...** |<br/><br/>**I should receive this form:** |
|I received **at least USD600 in payments** from ads in apps in the applicable tax year. | **1099-MISC:**<br/>Payer: Microsoft Online, Inc<br/>EIN: \*\*\*\*\*0505<br/><br/>**Important:** Certain business entities won't receive 1099-MISC forms regardless of the payment amounts received from Microsoft.  Consult your tax professional for more information. |
| I received **less than USD600 in payments** from ads in apps in the applicable tax year. | None |

## For developers who are Foreign Persons (under US tax law)

| **Question** | **Answer** |
|---|---|
| **I received a form 1042-S from Microsoft. What is it for?** | Microsoft has provided you with a 1042-S form or forms because we paid you revenue that is considered reportable to the United States tax authorities and was subject to withholding tax.  Form 1042-S is used for this reporting requirement. |
| **What should I do with the forms?** | Generally, no action is required on your part. Form 1042-S might be useful to you if you want to apply to your local tax authorities for any form of tax credit.  Consult with your own tax advisors to get more information on this subject. |
| **Why was tax withheld on my payments when I completed a W8 form?** | Taxes are withheld if either:<br/>- You didn't complete the tax treaty section of the W8 correctly, or <br/>- You're a resident in a country that doesn't have a tax treaty with the United States.<br/><br/>You can visit Partner Center at any time to submit an updated W8 form.<br/><br/> **Note:** Not all income is subject to tax withholding. |
| **I submitted an updated W8 form with valid treaty information. Can Microsoft refund me the tax that was withheld?** | After tax has been withheld, it can't be refunded. Contact your tax advisors to discuss whether you can claim a local credit for these taxes, or whether you can seek a refund from the IRS. |
| **What sales are reported on form 1042-S?** | Only sales made **to buyers located in the United States that were classified as subject to tax withholding** are reportable.  All other sales aren't considered reportable. |
| **Why did I get three copies of the same form 1042-S in one envelope?** | IRS regulations require three copies of the form to be provided:<br/>- One for the recipient's records<br/>- One for filing with a United States Federal tax return (if applicable)<br/>- One for filing with a United States state tax return (if applicable) |

> [!NOTE]
> If you have additional questions or concerns related to **IRS tax forms**, go to [Help + support](https://partner.microsoft.com/dashboard/v2/support/) in the Partner Center. Microsoft cannot answer questions related to your specific tax circumstances. For those questions, seek advice from your tax professional.

For more information about whether you're a US Person or Foreign Person under US tax law, see [Classification of Taxpayers for U.S. Tax Purposes](https://www.irs.gov/individuals/international-taxpayers/classification-of-taxpayers-for-us-tax-purposes).

## Next steps

- [Getting paid in the commercial marketplace](marketplace-get-paid.md)
