---
title: Verify your account information
ms.topic: article
ms.date: 05/26/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-enroll
description: Follow the status of your account verification when trying to enroll in a new Partner Center program. Learn how to supply additional information, if necessary.
author: sharath-satish-msft
ms.author: shsatish
---

# Verify your account information when you enroll in a new Partner Center program

**Appropriate roles**: Global admin | MPN Partner Admin | Account admin | Manager | Owner

When you enroll in a new program in Partner Center or change legal details in your profile, Microsoft verifies the information that you provide, such as your company name, company address, and primary contact details. During this process, Microsoft may send email to your primary contact to request more verification documentation.

You can go to [Legal info](https://partner.microsoft.com/dashboard/account/v3/organization/legalinfo#mpn) in Partner Center to monitor verification status for the:

- [Microsoft AI Cloud Partner Program](https://partner.microsoft.com/dashboard/account/v3/organization/legalinfo#mpn).
- [Cloud Solution Provider (CSP) program](https://partner.microsoft.com/dashboard/account/v3/organization/legalinfo#csp).
- [Developer program(s)](https://partner.microsoft.com/dashboard/account/v3/organization/legalinfo#developer) (Commercial Marketplace, Windows and Xbox, Office Store, and so on).

When account verification is complete, you can perform activities such as purchasing new offers, renewing existing offers in the Microsoft AI Cloud Partner Program, or publishing offers to Commercial Marketplace.

> [!NOTE]
> Verification usually takes 3-5 business days. If more than five days have passed, you can contact support for assistance.

## What is verified and how to respond

| **Type of verification**   | **What's verified**   | **Suggestions**                                                                                        |
|----------------------------|:-----------------------------------|:-----------------------------------------------------------------------------------------------------|
| Email ownership            | Email ownership verifies that the primary contact (primary email) address is valid. The primary contact email address must be a work account that is monitored and can send/receive email. **Do not use** a personal email address not associated with the company domain and **avoid using** a tenant user credential not associated with email. (For example, jsmith@testcompany.onmicrosoft.com). | If you don't receive the email ownership verification email message within one business day, you can ask us to send the email again. Go to your profile page for [MPN](https://partner.microsoft.com/dashboard/account/v3/organization/legalinfo#mpn), [CSP](https://partner.microsoft.com/dashboard/account/v3/organization/legalinfo#csp), or [Developer](https://partner.microsoft.com/dashboard/account/v3/organization/legalinfo#developer), and select **Resend verification email**. Be sure to flag email from Microsoft.com as a "safe" domain, and check junk email folders. For further assistance, [create a support ticket](https://go.microsoft.com/fwlink/?linkid=2167384).|
| Identity verification (Applicable for Microsoft AI Cloud Partner Program only) | Identity verification confirms the identity of at least one user on the account. The identity is verified by trusted third party ID verification vendors (IDVs). You can learn more about these vendors and verification process. All users should ensure that their first, last name and other details they provide match those on the supporting ID document. | Identity verification can either be in **Passed**, **Rejected**, or **Challenged** state. If identity verification is **Rejected** and you don't see a **Fix now** button, there's no further action required and the account will be suspended. If it's **Challenged**, at least one user on the account needs to present [verifiable credentials](get-verifiable-credentials.md) to prove their identity. Ensure that the user details on the account match the deails on a supporting government-issued ID document provided to obtain the verifiable credentials. If there's a mismatch, either update the first and last name in the tenant or use a government-issued ID document with matching details. If there are issues with obtaining the Verifiable Credentials, refer to the help provided in the **Learn more** link on the page. |
| Employment | Employment verification confirms your primary contact is an employee of the enrolling company and that the company owns the domain of the email address provided.| If employment verification is rejected, the primary contact (normally your Global or Account Admin) must provide documentation confirming the contact's email domain is under the ownership of their employer. For further assistance, go to your profile page for [MPN](https://partner.microsoft.com/dashboard/account/v3/organization/legalinfo#mpn), [CSP](https://partner.microsoft.com/dashboard/account/v3/organization/legalinfo#csp), or [Developer](https://partner.microsoft.com/dashboard/account/v3/organization/legalinfo#developer) to upload more proofs through the [interactive account verification experience](#checking-your-verification-status). |
| Business   | Business verification confirms that the enrolling company is a legitimate business entity and at the stated address. | Confirm that the company name and address in your [Legal business profile](https://aka.ms/accountexp/legalInfo) have no spelling errors or abbreviations. They must match your formal company business registration records exactly. If appropriate, select the match found in external data sources (external company databases, such as Dun & Bradstreet (DUNS ID) or state registry).<br /><br />Microsoft asks the primary contact (normally your Global or Account admin) to provide official documentation. Documentation could be a business registration, tax registration certificate, or a receipt from the company's home country/region, municipality, or questionnaires to be completed. Microsoft uses this documentation to verify that the company is authorized to do business under that name, and that it's located at the address provided. For further assistance, go to your profile page for [MPN](https://partner.microsoft.com/dashboard/account/v3/organization/legalinfo#mpn), [CSP](https://partner.microsoft.com/dashboard/account/v3/organization/legalinfo#csp), or [Developer](https://partner.microsoft.com/dashboard/account/v3/organization/legalinfo#developer) to upload more proofs through the [interactive account verification experience](#checking-your-verification-status).|
| Additional due diligence | Additional Due Diligence confirms the trustworthiness of the enrolling company in the Microsoft partner ecosystem. | Microsoft runs on trust. In order to ensure trustworthiness in its partner ecosystem, Microsoft might conduct additional background checks on your organization. If your organization is selected for additional due diligence, your profile page will display the status accordingly. If any concerns arise during additional due diligence, you might be asked to complete a questionnaire, respond to any concerns identified, or take certain mitigating measures. |

> [!NOTE]
> Learn how to update your [Legal Business Profile (address)](update-your-partner-profile.md).

## Checking your verification status

You can check verification status at Partner Center in **[Account settings | Legal Info](https://partner.microsoft.com/dashboard/account/v3/organization/legalinfo#mpn)**, where you can see:

- One or more tabs (**Partner**, **Developer**, or **Reseller**, depending on the programs in which your organization is enrolled).
- Your verification status: **Pending**, **Accepted**, or **Rejected**, with a status icon.
- The **Legal business profile** progress bar with an information icon you can select to get more information.

:::image type="content" source="media/verification-responses/verification-status.png" alt-text="Screenshot of the Account settings | Legal Info window in Partner Center, with the Partner tab and verification status highlighted.":::

In the image, one of the three possible tabs (the **Partner** tab) and the **Pending** verification status are highlighted.

### Verification status

There are three possible results when you check your verification status:

- **Accepted**: The information you submitted was verified, and you're notified of your acceptance into the program. No further action is required.
- **Pending**: The verification process has started but isn't complete. No action is required. You can monitor verification status at [Account settings | Legal Info](https://partner.microsoft.com/dashboard/account/v3/organization/legalinfo#mpn). (Verification usually takes 3-5 business days.)
- **Rejected**: The information you submitted couldn't be verified. The reason and instructions for [how to appeal](#appealing-a-rejected-application) appear in the **Account Verification** pane.

### Appealing a rejected application

To appeal a rejected application, use the following steps:

1. At **[Account settings | Legal Info](https://partner.microsoft.com/dashboard/account/v3/organization/legalinfo#mpn)**, select **Fix now**.
1. In **Account Verification**, from **Select document type to upload**, select the type of document that you want to upload for verification.
1. In **Enter your comment**, you can add additional information about your appeal.
1. Select **Upload**.

The amount of time required to review an appeal varies. You can return to **[Account settings | Legal Info](https://partner.microsoft.com/dashboard/account/v3/organization/legalinfo#mpn)** to check verification status at any time. Verification status is **Pending** during the review.

:::image type="content" source="media/verification-responses/fix-rejection.png" alt-text="Screenshot of the Account settings | Legal Info window in Partner Center, with the Fix now and Account verification highlighted.":::

## Next steps

[Get verifiable credentials](get-verifiable-credentials.md)
