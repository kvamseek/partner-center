---
title: Cloud Solution Provider security contact
ms.topic: article
ms.service: partner-dashboard
ms.subservice: partnercenter-account
description: Improve security of your account by providing a security contact.
author: vijay-vala
ms.author: vijvala
ms.date: 5/26/2023
---

# Cloud Solution Provider security contact

**Appropriate roles:** Global admin

A *security contact* is an individual or a group of people who are responsible for security-related issues at a partner organization.

When a security-related issue happens on a Cloud Solution Provider (CSP) partner tenant, Microsoft should be able to communicate the issue to a designated security contact in a partner organization and recommend appropriate steps. That security contact then acts with urgency to mitigate and remediate security concerns as soon as possible. Therefore, all partners should keep security contact information for their partner tenant up to date.

Global admins or other roles at Partner Center usually don't have the necessary expertise or reach to act on important, security-related incidents.

Greater privacy safeguards and security are among our top priorities. We know that the best defense is prevention and that we're only as strong as our weakest link. For those reasons, we need everyone in our ecosystem to act and ensure appropriate security protections are in place.

## Affected partners

All direct-bill partners, indirect providers, and indirect resellers should provide a security contact.

## Role of the security contact

The security contact receives email notifications from Microsoft when a security incident affects the CSP partner tenant or the customer tenants that have granted reseller relationship and/or administrative relationship rights to the partner. The email contains clear instructions about any actions that are needed. The security contact is expected to take immediate action to prevent potential or increased damage from the security incident.

## Security contact attributes

| Security contact field   | Description                                                                                      |
|------------------------------|------------------------------------------------------------------------------------------------------|
| First name **\***  | First name of the individual or group accountable for security related issues within the CSP partner organization     |
| Middle name **\***  | Middle name of the individual or group accountable for security related issues within the CSP partner organization (optional)  |
| Last name   | Last name of the individual or group accountable for security related issues within the CSP partner organization  |
| Email       | Email address of the individual or group accountable for security related issues at the CSP partner organization. Microsoft prefers to have a distribution list of a group involved in CSP security. |
| Phone       | Phone number of the individual or group accountable for security related issues within the CSP partner organization. The phone number should be for a phone that's available 24x7. |

  > [!NOTE]
  > **\***  If the security contact is an organization or group in your company, enter the name of that organization or group in both the **First Name** and **Middle Name** fields of the **Security contact** information.
  
## Update security contact information for your CSP partner tenant

You can update the security contact information for your tenant using the following procedure.

You must be a Global admin for your company to perform this task. Other roles might be able to view the **Legal business profile** and security contact information, but they can't update it.

If not already added, you will need to provide security contact information if you want to update your profile.

Security contact information can't be entered using the Partner Center APIs.

> [!IMPORTANT]
> If you update *only* fields on the **Security contact** page, account verification is not required.
>
> However, if you update any of the fields in the **Legal business profile** or **Primary Contact** sections, your account might be required to go through [account verification](verification-responses.md).

To update your security contact for your tenant, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select the **Settings** (gear) icon.
2. Select the **Account settings** workspace, then select **My profile**.
3. Select **Legal Info** in the **Organization Profile** section.
4. In the security contact section, select **Update**.
5. Update the fields in the **Security contact** section and select **Update**.

  :::image type="content" source="./media/security/security-add-contact.png" alt-text="Screenshot showing the Partner Center screen for entering security contact information.":::

## Frequently asked questions

### What is a security contact?

A security contact is a person or group of people responsible for security-related issues within the CSP partner organization. Some examples of security-related issues are spam, Azure fraud, and credential compromise.

### Who can update the security contact?

A CSP *Global administrator* can update the security contact fields in the [Partner Center legal profile](https://partner.microsoft.com/dashboard/account/v3/organization/legalinfo). Persons with other roles might be able to view the Legal business profile and see the security contact information, but they can't update it. Security contact updates can't be performed using an API.

### What type of communications does the security contact receive?

The security contact receives email notifications from Microsoft when there's a security incident that affects either the CSP partner tenant or customer tenants that have granted reseller relationship and administrative relationship rights to the partner.

### What is expected of a security contact?

When there's a security incident, Microsoft notifies the security contact. The notification email has clear instructions about any actions that are needed. The security contact is expected to take immediate action to prevent potential or increased damage from the security incident.

### Will the security contact receive Azure fraud email notifications?

No. The security contact won't receive Azure fraud email notifications. It's recommended that the Admin agent who is responsible for managing the customer Azure subscription enroll to receive Azure fraud email notifications. For details, see [Azure fraud detection and notification](./azure-fraud-notification.md).
