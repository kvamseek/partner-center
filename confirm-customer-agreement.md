---
title: How to confirm that your customer has accepted the Microsoft Customer Agreement to the CSP program
description: Cloud Solution Provider (CSP) partners need to confirm customer acceptance of the Microsoft Customer Agreement before ordering Microsoft services for customers.
ms.topic: how-to
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
author: jischulz
ms.author: jischulz
ms.date: 04/28/2023
---

# Confirm customer has accepted the Microsoft Customer Agreement

**Appropriate roles**: Admin agent | Sales agent

Customer acceptance of the *Microsoft Customer Agreement* can be confirmed in two ways:

- **[Partner attestation](#partner-attestation)** - As a partner, you can confirm your customer's acceptance through the Partner Center or Partner Center APIs.
- **[Customer direct acceptance](#customer-direct-acceptance)** - You can invite the customer to review and accept the agreement in the Microsoft 365 Admin Center.

## Partner attestation

Direct-bill partners can confirm new and existing customers' acceptance of the Microsoft Customer Agreement in Partner Center.

> [!NOTE]
> You must have the user role *Admin agent* or *Sales agent* to confirm customer acceptance.

Indirect resellers can't attest on behalf of their customers. Instead, they must work with their indirect provider to complete attestation.

### Attest for new customers

When you create a new customer tenant in Partner Center, use the following steps to confirm the customer's acceptance of the Microsoft Customer Agreement.

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**. 
2. Select **Add customer**.
3. Under **Account info**, enter information about the company and its primary contact.
4. Under **Microsoft agreement**, select the box to attest that the customer has accepted the Microsoft Customer Agreement.
5. Under **Agreement acceptance date**, enter the appropriate date. (You can't set the **Agreement acceptance date** to a future date.)
6. Make sure that the primary user contact information that's displayed is correct. If it's incorrect, select **Update** and enter the accurate information for the person who accepted the agreement.
7. Select **Next** to continue creating the customer tenant.

### Attest for existing customers

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.
2. Select the customer you want, then select **Account**.
3. Under **Microsoft Customer Agreement**, select **Update**.
4. Enter the **First name**, **Last name**, **Email address**, and **Phone number** (optional) of the person who accepted the agreement.
5. Under **Agreement acceptance date**, enter the appropriate date. (You can't set the **Agreement acceptance date** to a future date.)
6. Select **Save** and continue.

### Verify customer acceptance

To get confirmation that an existing customer has accepted the Microsoft Customer Agreement, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.
2. Select the customer whose acceptance you want to verify, then select **Account**.
3. Under **Microsoft customer agreement,** view whether confirmation has been provided by the customer.

### Verify customer acceptance using Partner Center APIs

You can also use Partner Center APIs to confirm customer acceptance of the Microsoft Customer Agreement.

- [Get agreement metadata for the Microsoft Customer Agreement](/partner-center/develop/get-customer-agreement-metadata)
- [Confirm customer acceptance of Microsoft Customer Agreement](/partner-center/develop/confirm-customer-consent-customer-agreement)
- [Get confirmation of customer acceptance of Microsoft Customer Agreement](/partner-center/develop/get-confirmation-of-customer-agreement)
- [Get a download link for the Microsoft Customer Agreement template](/partner-center/develop/download-customer-agreement-template)

### Customer notification of partner attestation

After you attest to new and existing customers' acceptance of the Microsoft Customer Agreement, the primary contact at the customer organization will receive an automated email notice within 30 minutes of attestation. This email is sent by Microsoft as confirmation of the attestation.

- The customer notice won't be sent to customers who were invited to accept the Microsoft Customer Agreement directly via the Microsoft 365 Admin Center (MAC).

- Partners should prepare to address customer questions regarding the notification and agreement as customers will be directed to their partner of record to answer any questions.

- More information can be found in the [Customer Notification for Microsoft Customer Agreement Partner attestation FAQ](https://partner.microsoft.com/resources/detail/customer-notification-for-microsoft-customer-agreement-partner-attestation-faq-pdf).

## Customer direct acceptance

You can use the following methods to invite new and existing customers to review and accept the agreement in the Microsoft 365 Admin Center:

- [Create a new customer and invite the customer to review and accept the agreement](#create-a-new-customer-and-invite-the-customer-to-review-and-accept-the-agreement)
- [Invite a new customer to review and accept the reseller relationship and agreement](#invite-a-new-customer-to-review-and-accept-the-reseller-relationship-and-microsoft-customer-agreement)
- [Invite an existing customer to review and accept the agreement](#invite-an-existing-customer-to-review-and-accept-the-agreement)

### Create a new customer and invite the customer to review and accept the agreement

> [!NOTE]
> New customers can't make a purchase until they accept the Microsoft Customer Agreement.

You can create a new customer in Partner Center and invite that customer to review and accept the Microsoft Customer Agreement within Microsoft 365 Admin Center using the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.\
1. Select **Add Customer** and enter the required information about the new customer, including the customer's company name and primary contact.
1. Under **Customer Agreement**, select **Customer will be asked to accept the Microsoft Customer Agreement in Microsoft 365 Admin Center**, then enter any other required information on the page.
1. Select **Next: Review,** then continue doing the steps to create the customer tenant.
1. When you reach the **Confirmation** screen, be sure to save the customer credentials so you can email them to the customer, as described in the next step.
1. Outside of Partner Center, create and send an email that invites the customer to accept the Microsoft Customer Agreement in Microsoft 365 Admin Center. Include the following items in the email:

   - This URL that the customer can use to sign in the Microsoft 365 Admin Center:
    `https://admin.microsoft.com/AdminPortal/Home?ref=/BillingAccounts/agreement`
   - The customer's sign-in credentials that you saved in Step 5.

When the customer receives the email invitation, they can sign in to [Microsoft 365 Admin Center](https://admin.microsoft.com/AdminPortal/Home?ref=/BillingAccounts/agreement) using the URL and customer credentials you provided. The customer then selects the box to accept the Microsoft Customer Agreement.

### Invite a new customer to review and accept the reseller relationship and Microsoft Customer Agreement

To invite a new customer to review and accept the reseller relationship and the Microsoft Customer Agreement:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.
1. Select **Request a reseller relationship**.
  - An email template is generated that includes text and a parameterized URL that directs the customer to the Microsoft 365 Admin Center.
1. You can customize the automatically generated email template and then select **Copy to clipboard** or **Open in email**.
1. Use this email template to invite the customer to accept the **reseller relationship** request and the **Microsoft Customer Agreement**.
  - In the email invitation, make sure to include the URL that was automatically provided as well as the customer credentials that were recently created.

   :::image type="content" source="media/customers/create-relationship.png" lightbox="media/customers/create-relationship.png" alt-text="Screenshot showing create a relationship screen in Partner Center.":::

Your customer can use the following steps to accept:

1. Select the custom URL to go to Microsoft 365 Admin Center.
1. Sign in to admin center with the credentials you provided.
1. Select the box to accept the **reseller relationship** and **Microsoft Customer Agreement**.
1. If they choose, they can view a consolidated list of the partners they're working with and select a partner to see details.

### Invite an existing customer to review and accept the agreement

To invite an existing customer to review and accept the Microsoft Customer Agreement:

- Create the customer email with the embedded URL, inviting your customer to accept the Microsoft Customer Agreement as described previously.

Your customer can use the following steps to accept:

1. Select the link to Microsoft Admin Center: `https://admin.microsoft.com/AdminPortal/Home?ref=/BillingAccounts/agreement`
1. Enter their credentials and select the box to accept the Microsoft Customer Agreement.
1. If they choose, view a consolidated list of the partners they're working with, and select a partner to see details.

### Troubleshoot customer acceptance issues

Sometimes, customers may not be able to accept the Microsoft Customer Agreement directly, within the Microsoft 365 Admin Center. For example, if an existing customer has purchased any of the following through an existing partner relationship, they may not be able to accept directly:

- Offers
- Software or software subscriptions
- Reserved Instances
- Azure plan

When attempting to make any new purchase (excluding auto-renewal), that customer may receive the message: *Please reach out to your Partner to confirm your acceptance of the Microsoft Customer Agreement.*

To resolve, you must [attest on behalf of the customer](#partner-attestation).

### Confirm that your customer has accepted the agreement

If you try to create a new order for an existing customer who you haven't confirmed before, you'll receive a prompt to complete the confirmation.

To complete the acceptance confirmation, use the following steps:

1. Enter the **First name**, **Last name**, **Email address**, and **Phone number** of the user who accepted the agreement.
1. Under **Agreement acceptance date**, enter the current date. (You can't set the **Agreement acceptance date** to a future date.)
1. Select **Save and continue**.

#### Confirm direct acceptance using APIs

You can use Partner Center APIs to [get the status of a customer's direct signing (direct acceptance) of the Microsoft Customer Agreement](/partner-center/develop/get-direct-sign-status-of-customer-agreement).

## Next steps

- [Verify or update your company profile information](update-your-partner-profile.md)
- [Microsoft Customer Agreements by region and language](agreements.md)
