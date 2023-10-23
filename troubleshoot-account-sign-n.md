---
title: Troubleshoot setting up your Partner Center account or Microsoft AI Cloud Partner Program renewal issues
ms.topic: how-to
ms.date: 05/26/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-enroll
description: Troubleshoot problems when trying to enroll in Partner Center. Answers address challenges with payment methods, forgetting passwords, and more.
author: sharath-satish-msft
ms.author: shsatish
---

# Troubleshoot account setup or Microsoft AI Cloud Partner Program renewal issues

**Appropriate roles**: Global admin | MPN Partner Admin

Here are some suggestions for troubleshooting common issues that arise when setting up your Partner Center account.

#### If the IT department has turned off **Sign up for Partner Center**

You see this message because viral users are disabled, or because Viral Sign-up is disabled on the Azure Active Directory (Azure AD) tenant. The Global admin for your Azure AD account can enable required features by running the following PowerShell command:

```powershell
Set-MsolCompanySettings -AllowEmailVerifiedUsers $true -AllowAdHocSubscriptions $true
```

For more information, see [Self-service sign-up](/azure/active-directory/users-groups-roles/directory-self-service-signup).

#### You forgot your password

If you've forgotten your password, on the sign-in page, select **Can't access your account?** You can use this option to reset your password. You can also ask your Global admin to assign new credentials.

#### On the "Tell us about your company" page, you receive a "Something went wrong" error

This error message usually appears if you inadvertently use special characters, spaces, or a country code in your company phone number. The value entered in the **Phone Number** field can have a maximum of 10 characters.

#### When making a credit card purchase, you receive an error message that says "Your order was declined. Verify your information"

To make a successful credit card purchase, you must enter an address that matches the address associated with your credit card (and not the address of your legal entity).

Also, make sure the ZIP code or postal code that you enter is correct and matches the address associated with your credit card.

#### You want to switch from offline payment to online payment method

You must cancel the original order and repurchase using your preferred payment method.

To cancel an order, use the following steps:

1. In [Partner Center](https://partner.microsoft.com/dashboard/home), select **Membership**.

2. Select **Membership offers** and then **Cancel order**.

3. A confirmation window appears. You must confirm to cancel the initial order.

## Next steps

- [Manage your Partner Center account](partner-center-account-setup.md)
- [How to read your bill and recon file](read-your-bill.md)


