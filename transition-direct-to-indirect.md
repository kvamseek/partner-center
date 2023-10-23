---
title: Switch direct-bill partner to indirect reseller
ms.topic: how-to
ms.date: 10/07/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-enroll
description: Learn how a Cloud Solution Provider (CSP) program partner can use Partner Center to transition from direct-bill partner to indirect reseller.
author: Brentserbus
ms.author: brserbus
---

# Transition from Cloud Solution Provider direct-bill partner to indirect reseller

**Appropriate roles**: Global admin

Direct-bill partners have a [revenue requirement](direct-partner-new-requirements.md#verify-minimum-requirements) of at least 300,000 USD.

This article is intended for direct-bill partners who have decided to transition to being **indirect resellers** instead.

You can enroll in the [indirect reseller program](csp-overview.md#indirect-model) using your existing direct-bill tenant.

Your indirect reseller business will use the same Microsoft Azure Active Directory (Azure AD) tenant you use for your direct business.

> [!IMPORTANT]
> After you enroll as an indirect reseller, you can reapply to be a direct-bill partner after meeting the requirements using a new tenant. You can move your current customers from your indirect CSP tenant to the new direct-bill tenant.
> Make sure that you fully evaluate your business needs before enrolling as an indirect reseller.

## Get started

To transition from being a direct-bill partner to an indirect reseller, use the following steps:

1. Make sure that your partner profiles in Partner Center and your PartnerID are current.

2. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) as a Global admin for the direct-bill tenant you're transitioning to being an indirect reseller.

3. Review your partner details on the enrollment form:

   :::image type="content" source="media/direct/direct2a.png" lightbox="media/direct/direct2a.png" alt-text="Screenshot showing at enrollment form and the 'Enroll now' button.":::

4. Select **Enroll now**.

5. When your enrollment is approved, sign in to Partner Center again.

6. On your **[Overview](https://aka.ms/accountexp/agreements)** page, you'll see the indirect reseller agreement. Select **Accept and continue**. Doing so enables indirect reseller capabilities.

> [!NOTE]
> Although approval is usually immediate, it can take up to five business days.
> Once approved, you will receive a notification at the primary contact email address you specified in the enrollment form. 
> You can also check your enrollment status at **Settings** > **Account settings** > **Partner Profile** > **Program info**.

When you've accepted the indirect reseller agreement, notice that your Partner profile identifies you as **both** a direct-bill and indirect reseller.

:::image type="content" source="media/direct/direct4.png" alt-text="Screenshot of 'Program info' that shows both direct-bill and indirect reseller.":::

## While you transition from direct to indirect reseller

During the transition from direct-bill partner to indirect reseller, you'll continue to manage your direct customers' subscription needs, including the billing process.

You can also begin accepting customers from your indirect provider and operating as an indirect reseller.

> [!NOTE]
> Sandbox and [Partner Center API/SDK](/partner-center/develop/manage-customers) capabilities are available only to direct-bill partners. After the transition from direct-bill to indirect reseller, you lose access to the sandbox and Partner Center API capabilities.

### Find an indirect provider

You can search the official list of [Microsoft indirect providers](https://partner.microsoft.com/membership/cloud-solution-provider/find-a-provider) to find an indirect provider.

After your enroll as an indirect reseller, a link to indirect providers appears in the left navigation bar at Partner Center. As an indirect reseller, you'll establish a relationship with an indirect provider who can handle your billing, purchase products for your customers, and provide support infrastructure.

Different indirect providers offer different support and services, so you should evaluate the providers in your area to determine which ones best meet your needs. Generally, most providers will:

- Provide you with technical training and assistance.
- Help you market your products and services.
- Manage your financing and credit terms.

To learn more working with indirect providers, read [Learn how to partner with indirect providers in the Cloud Solution Provider program](indirect-reseller-tasks-in-partner-center.md)

### Accept a partnership invitation from your indirect provider

When you find an indirect provider to partner with, establish a partnership with that indirect provider in Partner Center. The indirect provider that you select will send you a partnership invitation link in email that will take you to their invitation in Partner Center.

To accept a partnership invitation:

- Have someone with Global admin permissions sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and follow the  link in the invitation.

After you accept the invitation, the provider's name appears in your indirect provider list.

### Acquire new customers as an indirect reseller

Both you and your indirect provider must have reseller relationships with customers. These reseller relationships enable you to manage a customer's subscriptions and services on their behalf.

To acquire a new customer who has an existing Azure AD tenant, invite the customer to establish a reseller relationship with both you and your provider at the same time.

To create an indirect reseller invitation, use the following steps:

1. Select **Indirect providers** from the Partner Center left navigation bar.

2. Select **Invite new customers** to invite a customer to establish a reseller relationship with both you and the indirect provider at the same time.

   Your provider must have a reseller relationship with your customer. That relationship enables them to submit orders on your customer's behalf when the customer wants to buy new subscriptions or add new licenses to existing subscriptions.

3. On the next page, review the draft email message.

   You can open the draft message in email, or you can copy the message to your clipboard and paste it into an email message.

   You can edit the text in the email to say what you need, but be sure to include the link. (The link is personalized to connect the customer directly to both your account and your provider's account.)

4. Select **Done**.

5. After the customer authorizes you and your provider to be their resellers of record, you'll have administrator permissions to manage their subscriptions, licenses, and users on their behalf. Your indirect provider will be able to submit orders on their behalf.
6. To manage the customer's account, services, users, and licenses, expand the customer's record by selecting the down arrow near their name.

Unlike direct-bill partners, indirect resellers can't create Azure AD tenants for their new customers in Partner Center. Your provider will create the tenant and specify you as the indirect reseller for this customer. Doing so ensures that the customer appears in your customer list in Partner Center.

> [!NOTE]
>You cannot use your direct-bill capability to create purchases for customers you acquire as an indirect reseller.

### Manage your direct-bill customers and your indirect reseller customers

You manage direct-bill customers and indirect reseller customers differently.

#### Things you won't do as an indirect reseller (direct-bill customers)

- Purchase or create orders for products.
- View customer subscriptions.
- Manage customer order history.
- Bill customers directly.
- View or download CSP price lists from Partner center.
- Use the sandbox and Partner Center API functionality for storefront integration.
- Add a new customer record in Partner Center.

#### Things you can do as an indirect reseller

- Request that your indirect provider order products for your customers.
- Manage customers' licenses and users.
- Create service requests on behalf of your customers.
- View customer analytics.

#### To identify customers that you acquired as a direct-bill partner

1. In Partner Center, select **Customers**.

2. Select a customer to view their details.

   - If the customer is one you acquired as a direct-bill partner, you'll see options to **add** or **view products**, and you'll see their subscriptions.

   - If the customer has an indirect reseller relationship with you, those options won't be available.

### Move your direct-bill customers to your indirect provider

Your indirect provider can't submit orders or existing subscription transfers for your existing direct-bill customers until they have a reseller relationship with them.

To establish the reseller relationship between your indirect provider and your existing direct-bill customer, you can:

- Use the [reseller relationship extension](#using-the-reseller-relationship-extension)
- [Send an indirect reseller invitation to a direct-bill customer](#send-an-indirect-reseller-invitation-to-a-direct-bill-customer)

#### Using the reseller relationship extension

You can use the *reseller relationship extension* to establish a reseller relationship between your existing direct-bill customers and your indirect provider.

   > [!IMPORTANT]
   > To avoid confusion and misunderstanding, you are contractually obliged by your partner agreement to inform and obtain consent from a direct-bill customer before you use the reseller relationship extension to establish a reseller relationship between an existing direct-bill customer and an indirect provider.

Before using the reseller relationship extension, consider that:

- The reseller relationship extension is only available to direct-bill partners who are transitioning to become indirect resellers and have completed the [indirect reseller enrollment](#get-started).

- You can only use the reseller relationship extension with existing direct-bill customers. It can't be used with [indirect reseller customers](#acquire-new-customers-as-an-indirect-reseller).

- You can only select an indirect provider from whom you've [accepted a partner invitation](#accept-a-partnership-invitation-from-your-indirect-provider).

- A copy of the bill-to information that you have for a customer is available to the indirect provider.

    > [!NOTE]
    > By using the reseller relationship extension, you consent to sharing the bill-to information that you have for a customer with your indirect provider.

     You can access bill-to information by accessing the **Account** page for the customer in Partner Center.

- Your indirect provider won't be provided with [delegated administration privileges](customers-revoke-admin-privileges.md) to the customer tenant. If your indirect provider requires delegated administration privileges, you must send an indirect reseller invitation to the customer instead.

- After the reseller relationship is established, the indirect provider appears as a CSP partner to the customer on the **Partner Relationships** page in [Microsoft 365 Admin Center](https://admin.microsoft.com/AdminPortal/Home#/partners) and [Microsoft Store for Business](/microsoft-store/work-with-partner-microsoft-store-business).

To use the reseller relationship extension on an existing customer tenant, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) as an Admin agent and select **Customers**.

2. Select an existing customer and select its **Quick links** icon to expand the summary view of the customer.

3. Under **Indirect providers**, select **Transfer customer on an indirect provider**.

    :::image type="content" source="media/direct/direct5-1.png" lightbox="media/direct/direct5-1.png" alt-text="Screenshot of transferring a customer to an indirect provider in Partner Center.":::

4. In the dialog box that appears, select the indirect provider that you want to have reseller relationship with the customer.

5. Select **Save and continue**.

6. Verify that the selected indirect provider is displayed in **Indirect providers**.

    :::image type="content" source="media/direct/direct5-2.png" lightbox="media/direct/direct5-2.png" alt-text="Screenshot in Partner Center in which the selected indirect provider is listed.":::

### Send an indirect reseller invitation to a direct-bill customer

Your indirect provider can't submit orders for your existing direct-bill customers until they have a reseller relationship with them. To establish the reseller relationship between your existing customers and your indirect provider, invite the customer using an indirect reseller invitation.

To send an indirect reseller invitation to a customer:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) as an Admin agent and select **Customers**.

2. Select **Invite new customers** to invite a customer to establish a reseller relationship with both you and the indirect provider at the same time.

   The provider must have a reseller relationship with your customer. The relationship enables them to submit orders on your customer's behalf when the customer wants to buy new subscriptions or add new licenses to existing subscriptions.

    :::image type="content" source="media/direct/direct6.png" lightbox="media/direct/direct6.png" alt-text="Screenshot in Partner Center showing a list of indirect providers and selecting 'Invite new customers' for one of those providers.":::

3. Review the draft email message that appears on the next page.

   You can open the draft message in email, or you can copy the message to your clipboard and edit the text to say what you need. Be sure to include the link because it's personalized to connect the customer directly to both your account and your provider's account.

4. Select **Done**.

   After the customer authorizes you and your provider to be their resellers of record, you'll have administrator permissions to manage their subscriptions, licenses, and users on their behalf. Your indirect provider will be able to submit orders on their behalf.

5. To manage the customer's account, services, users, and licenses, expand the customer's record by selecting the down arrow near their name.

#### Microsoft Customer Agreement

> [!IMPORTANT]
> All customers, existing and new, must sign the [Microsoft Customer Agreement](confirm-customer-agreement.md) (MCA) for transitioning customers.

|If your customer: |Required action: |
|---------|---------|
|Hasn't accepted the MCA yet | Work with your indirect provider to have the customer [accept the Microsoft Customer Agreement](confirm-customer-agreement.md).       |
|Has accepted the MCA with you through partner attestation    |  The acceptance won't be retained. Work with your indirect provider to [update the customer's acceptance in Partner Center](confirm-customer-agreement.md#attest-for-existing-customers).       |
|Has accepted the MCA with you through the Microsoft 365 Admin Center | No action is required. The acceptance will be retained when the reseller relationship is established with the indirect provider. |

### Transfer existing direct-bill subscriptions to your indirect provider

Under the CSP indirect model, indirect resellers don't have billing relationships with Microsoft. Instead, indirect resellers obtain subscriptions for their customers through their indirect providers.

While transitioning from direct-bill partner to indirect reseller, you must transfer any subscriptions that you have as a direct-bill partner to your indirect provider. You can use *self-serve subscription transfer* in Partner Center to do so.

See [Considerations](#considerations-regarding-subscription-transfers) at the end of this article for details of and requirements for subscription transfers.

#### Having both direct-bill and indirect reseller tenants is recommended

A partner can apply for both direct CSP and indirect reseller using a single tenant. However, if an indirect reseller enrolled as a direct CSP that overrides the indirect reseller feature, which means that partner loses indirect reseller access.

Therefore, *we highly recommend having two separate tenants* (one for direct-bill and another for indirect reseller). Otherwise, the features of the other program will be overridden by design.

Also, provide a time frame for how long a partner can take to transfer their customers and subscriptions from indirect reseller to direct-bill before they lose access as an indirect reseller.

#### Prerequisites for self-serve subscription transfer

- *Self-serve subscription transfer* is only available to transitioning partners who have completed the indirect reseller enrollment using their existing direct-bill partner tenants.

- The transitioning partner must move the customer to an indirect provider before transferring subscriptions associated with a given customer.

- Customers must have [accepted the Microsoft Customer Agreement through the Indirect Provider](#microsoft-customer-agreement).

> [!IMPORTANT]
> Transfer subscriptions is not available for New Commerce Experiences license-based subscriptions. Partners that need to transfer New Commerce subscriptions between partners will need to ensure their current partner's subscription does not auto-renew after it's term and then acquire the subscription from the new partner.

### How to use self-serve subscription transfer

Self-serve subscription transfer is a four-step process (described in detail in the following sections), in which:

1. [The transitioning partner creates a subscription transfer request.](#step-1-transitioning-partner-creates-a-transfer-request)

   The request contains one or more existing subscriptions associated with the same customer and is addressed to an indirect provider.

2. [The indirect provider reviews and accepts (or rejects) the transfer request.](#step-2-indirect-provider-accepts-the-transfer-request)

3. [The indirect provider verifies that the transfer request is complete.](#step-3-indirect-provider-verifies-the-transfer-request-is-complete)

4. [The transitioning partner verifies that the transfer request is complete.](#step-4-transitioning-partner-verifies-that-the-transfer-request-is-complete)

> [!NOTE]
> You can also use [Partner Center API/SDK](/partner-center/develop/manage-customers) to transfer the existing subscriptions to your indirect provider. To learn more, read the following articles in the [Partner Center developer documentation](/partner-center/develop/).
>
> - [Get a customer's subscriptions transfer eligibility](/partner-center/develop/get-customer-s-subscriptions-transfer-eligibility)
> - [Create a customer's transfer](/partner-center/develop/create-a-transfer)
> - [Withdraw a customer's transfer](/partner-center/develop/withdraw-a-transfer)
> - [Accept a customer's transfer](/partner-center/develop/accept-a-transfer)
> - [Reject a Customer's transfer](/partner-center/develop/reject-a-transfer)
> - [Get a customer's transfers](/partner-center/develop/get-all-of-a-customer-s-transfers)
> - [Get transfer details by ID](/partner-center/develop/get-transfer-by-id)

#### Step 1: Transitioning partner creates a transfer request

To create a transfer request as the transitioning partner:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) as an Admin agent and select **Customers**.

2. Select the customer you want and select the **Quick links** icon to expand the summary view of the customer.

3. Under **Indirect providers**, confirm that the intended indirect provider is listed.

4. Select **View Subscriptions**.

5. In the **Subscriptions** page, look for **Subscription Transfer**.

6. Under **Subscription Transfer**, select **Request subscription transfer**.

7. In the transfer request dialog, select one or more subscriptions to be transferred.

    :::image type="content" source="media/direct/direct9.png" lightbox="media/direct/direct9.png" alt-text="Screenshot of a Create Transfer Request.":::

8. Select **Create**.

9. An active subscription transfer request will appear under **Subscription Transfer**.

10. Inform your indirect provider that you've created a subscription transfer request for them.

#### Step 2: Indirect provider accepts the transfer request

To review and accept a transfer request as the indirect provider:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) as an Admin agent or Sales agent and select **Customers**.

2. Select the customer you want and select the **Quick links** icon to expand the summary view of the customer.

3. Under **Indirect resellers**, confirm that the transitioning partner is listed.

4. Select **View Subscriptions**.

5. In the **Subscriptions** page, look for **Subscription Transfer**.

6. Under **Subscription Transfer**, select the transfer request to review.

7. Select **Accept** or **Reject**, as appropriate.

8. Wait for the transfer request to complete.

#### Step 3: Indirect provider verifies the transfer request is complete

To verify that the transfer request is complete as the indirect provider, use the following steps:

1. After the transfer request is completed successfully, the indirect provider verifies that they can see the subscriptions appear under **Subscriptions**.

2. The indirect provider informs the transitioning partner.

#### Step 4: Transitioning partner verifies that the transfer request is complete

To verify that the transfer request is complete, the transitioning partner should:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) as an Admin agent or Sales agent and select **Customers**.

2. Select the customer you want, and select the **Quick links** icon to expand the summary view of the customer.

3. Select **View Subscriptions**.

4. On the **Subscriptions** page, look for **Subscription Transfer**.

5. Verify that the transfer request is marked as **Complete**.

6. Verify that the subscriptions no longer appear as active in the **Subscriptions** page:

   - If it's an Azure subscription (MS-AZR-0145P), it will no longer be listed.

   - If it's a license-based subscription (Microsoft 365, Dynamics, Intune), it will be listed with a state of **Suspended**.

   :::image type="content" source="media/direct/direct13.png" lightbox="media/direct/direct13.png" alt-text="Screenshot in Partner Center of a suspended subscription.":::

### Considerations regarding subscription transfers

This section describes various details and requirements of subscription transfers.

- **Subscription ID will be different after transfer** if it's an Azure subscription (MS-AZR-0145P). It will also have an Azure Subscription ID, which is retained from the previous owner, and will appear in the Azure management portal.

- **The same subscription cannot be referenced by multiple transfer requests.** After you've created a transfer request, you can't create more transfer requests with the same subscription until the first request is canceled. This restriction  applies to existing subscriptions.

- **Add-ons for license-based subscriptions must be transferred along with their base subscription.** If you pick an existing subscription with one or more add-ons when creating a transfer request, the add-ons are included in the transfer request automatically.

- **License count changes to a subscription will not be reflected in an existing transfer request.** After you've created a transfer request that includes an existing subscription, you should avoid updating the license quantity of the subscription (or associated add-ons). If you do so, the new quantity won't be reflected in the transfer request. After the indirect provider accepts the transfer request, the resultant subscription will have the old quantity. If you want the new quantity to be transferred to the indirect provider, you must cancel the existing transfer request and recreate a new one.

- **Not all purchases can be transferred using self-served subscription transfer.** You can only transfer Microsoft 365 subscriptions and Azure PAYG subscriptions (MS-AZR-0145P) using this feature. Other purchases, including Azure plans, Azure Reserved Instances, term-based Subscriptions, and SaaS subscriptions for Azure Marketplace aren't supported. You'll see a reason why a subscription can't be transferred on the **Submit transfer request** page. To transfer these subscriptions, you'll need to [cancel the existing subscription](create-a-new-subscription.md#cancel-a-subscription) and purchase a new offer for the customer through the indirect provider.

  - A credit will be applied to your next monthly invoice for any advance charges paid when you [cancel traditional license-based subscriptions](create-a-new-subscription.md#cancel-traditional-license-based-subscriptions), minus the prorated amount for the days used. Proration is calculated daily.

  - [Cancelling new commerce license-based subscriptions](create-a-new-subscription.md#cancel-new-commerce-license-based-subscriptions) must be done within 72 hours. Cancelling after 72-hours window results in no credits or refunds.

   > [!NOTE]
   > Changes to Azure offer availability in CSP related to the new commerce experience do not affect this transition scenario. You can continually transfer Azure PAYG subscriptions ([MS-AZR-0145P](https://go.microsoft.com/fwlink/p/?linkid=2164140)) to an indirect provider.

- **Subscription transfers cannot be tested using the sandbox environment.**

## Enroll for indirect reseller incentives

After you've successfully enrolled as an indirect reseller on your existing direct-bill partner tenant, you'll receive an invitation to enroll for indirect reseller incentives within 30 days. The invitation is based on the partner Microsoft AI Cloud Partner Program account that is currently associated with your CSP partner tenant. The invitation is sent to the email address associated with the partner Microsoft AI Cloud Partner Program account.

You're also eligible to enroll for direct-bill incentive programs with that same partner tenant. You must manage the programs separately.

## Next steps

- [Additional information about becoming an indirect reseller](https://assetsprod.microsoft.com/csp-directbill-to-indirect-transition.pdf)
- [CSP direct partner new requirements](direct-partner-new-requirements.md)
- [Restricted direct-bill capabilities](restricted-direct-bill-capabilities.md)
