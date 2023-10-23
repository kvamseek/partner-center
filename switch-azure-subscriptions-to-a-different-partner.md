---
title: Transfer Azure subscription to another partner
ms.topic: article
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Learn how to change the Cloud Solution Provider program partner associated with a customer's Azure subscriptions.
author: brentserbus
ms.author: brserbus
ms.date: 05/30/2023
---
# Transfer a customer's Azure subscriptions to a different partner

**Applies to**: Partner Center | Partner Center for Microsoft Cloud for US Government

**Appropriate roles**: Global admin

This article describes how a customer can transfer an Azure subscription from their current Cloud Solution Provider (CSP) to another CSP.

> [!NOTE]
> This article describes transfering Azure **legacy subscriptions** only. As previously announced, CSP partners should be [migrating their Azure subscriptions to Azure plan](/partner-center/azure-plan-transition). Partner transfer steps for Azure plan subscriptions can be found in the [transfer Azure plan subscriptions topic](/partner-center/transfer-azure-subscriptions-under-azure-plan).
> 

The first section, [Transferring an Azure subscription to another partner](#transferring-azure-subscriptions-to-another-partner), describes how a customer can transfer a Microsoft Azure subscription from one Cloud Solution Provider (CSP) to another.

The next section, [Transferring a previous Azure offer subscription without converting it to the Azure plan](#transferring-a-previous-azure-offer-subscription-without-converting-it-to-the-azure-plan), briefly describes how the new Azure plan is being introduced. Then it describes a special case in which some subscriptions to the previous Azure offer can be transferred to another CSP without converting them to the new Azure plan.

The customer, the current service provider, and a new service provider all have [responsibilities when transferring a customer subscription to a new Azure service provider](#responsibilities-when-transferring-a-customer-subscription-to-a-new-azure-service-provider). A customer should plan to work closely with the current partner to make the transition go smoothly.

 High-level information to help Azure subscribers transfer subscriptions to and from CSP partners can be found in [Transfer Azure subscriptions between subscribers and CSPs](/azure/cost-management-billing/manage/transfer-subscriptions-subscribers-csp).

Additional information about how customers can change their Azure subscriptions from one partner to another can be found in [Transfer a customer's Azure subscriptions to a different CSP (under an Azure plan)](./transfer-azure-subscriptions-under-azure-plan.md)

## Prerequisites

- A CSP Partner must have a reseller relationship with a customer before a subscription can be transferred.  For more information, see [How to request a reseller relationship from a customer in Partner Center](./request-a-relationship-with-a-customer.md).
- A partner must be a direct provider or an indirect provider to transfer a subscription.
- Subscriptions associated with the following offerings can't be transferred: Azure plan, Office 365, Enterprise Mobility Suite, and Microsoft Dynamics CRM.
- A customer must be in the same country/region as a partner to transfer a subscription.
- Partners operating in Microsoft Cloud for US Government or Microsoft Cloud Germany must request permission to manage a customer's service or subscription. For more information, see [Obtain permissions to manage a customer's service or subscription](./customers-revoke-admin-privileges.md).

## Transferring Azure subscriptions to another partner

Transferring an Azure subscription from one CSP partner to another is a multistep process that requires actions by the customer, the current partner, and the new partner at various stages. The following table is intended as a sequence diagram to help clarify who does what and when.

### Responsibilities when transferring a customer subscription to a new Azure service provider

|Step  |Customer  |Current partner  |New partner  |
|---------|---------|---------|---------|
|1     |[Customer notifies Microsoft and current partner in writing](#step-1-customer-contacts-current-partner-in-writing)         |         |         |
|2     |         |[Create support ticket to request transfer](#step-2-current-provider-creates-azure-support-ticket-to-request-a-transfer)        |         |
|3     |         |[Send completed transfer form to customer](#step-3-current-partner-completes-transfer-form-and-sends-it-to-the-customer)|         |
|4     |         |[Complete Change of Cloud Solution Provider form](#step-4-current-partner-completes-the-change-of-cloud-solution-provider-form)       |         |
|5     |[Review, sign, & return form](#step-5-the-customer-and-new-partner-review--return-the-form)       |         |[Review, sign, & return form](#step-5-the-customer-and-new-partner-review--return-the-form)         |
|6     |         |[Review form and attach to service request](#step-6-current-partner-reviews-form-and-attaches-it-to-the-service-request)        |         |
|7     |         |         |[Remove old partner from account](#step-7-new-partner-removes-old-partner-from-account)         |
|8     |         |         |[Remove outdated access permissions](#step-8-new-partner-removes-outdated-access-permissions)         |

### Steps for transferring a customer subscription to a new Azure service provider

#### Step 1: Customer contacts current partner in writing

The customer starts the transfer process by notifying both Microsoft and the current CSP Partner in writing (that is, not verbally) of their request to transfer a subscription.

#### Step 2: Current provider creates Azure support ticket to request a transfer

The current partner creates an Azure support ticket to request a subscription transfer.

> [!NOTE]
> It is the current partner's responsibility to create the support ticket that initiates the transfer process. Microsoft does not intervene on behalf of the customer or the new partner.

To create a support ticket to request a transfer, use the following steps:

1. In the Partner Center menu, select **Customers**, select the customer from the list, and then select **Service management**.
1. In the **Support tickets** section, select **New ticket** and then **Microsoft Azure.**
1. In [the Azure portal](https://portal.azure.com/), select **New support request**.
1. In Step 1 of the support request, choose **Subscription management** as the issue type, specify the Subscription ID that you want transferred, and choose **Cloud Solution Provider** as the support plan.
1. In Step 2, select **C-Minimal impact** and choose **Other General Questions** as the problem type.

#### Step 3: Current partner completes transfer form and sends it to the customer

The current partner downloads and complete the [Change of Cloud Solution Provider form](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RWwTWC), signs it, and then sends it to the customer.

#### Step 4: Current partner completes the Change of Cloud Solution Provider form

The current partner completes the [Change of Cloud Solution Provider form](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RWwTWC), signs it, and sends it to the customer.

Among the information needed to complete the *Change of Cloud Solution Provider* form is:

- **Current partner's contact information and Microsoft ID** (which can be found in the Partner Center menu by selecting **Account settings > Organization profile**).
- **Customer's Microsoft ID** (which can be found in the Partner Center menu by selecting **Customers** and then expanding the customer's listing to reveal their Microsoft ID).
- **Subscription ID** to transfer (which can be found which can be found in the Partner Center menu by selecting **Customers** and then expanding the customer's listing, selecting **View Subscriptions**, and then expanding the chosen subscription to reveal the Subscription ID.

#### Step 5: The customer and new partner review & return the form

Working together, the customer and the new partner:

1. Review the form, fill in information about the new partner, and sign it.
1. Confirm that the new customer has a contract agreement in place.
1. Send the form back to the current partner.

#### Step 6: Current partner reviews form and attaches it to the service request

When the current partner receives the form, they:

- Make sure the form includes contact information for both partner admins. (Microsoft Support contacts both admins to verify the transfer.)
- Verify that they have all three signatures, then use the **File Upload** option to attach the completed form to the existing service request. (A Microsoft support engineer contacts them within eight business hours to validate receipt and completion.)

#### Step 7: New partner removes old partner from account

The new partner updates the Azure subscription settings in PowerShell to remove the old partner from the account.

> [!NOTE]
> The first PowerShell cmdlet requires the customer's **Tenant ID**, which appears in Partner Center as the customer's **Microsoft ID**. The procedure that follows describes how to find the customer's Microsoft ID (Tenant ID) for use in the cmdlet.

To find a customer's Microsoft ID (Tenant ID) for use in the `Connect-AzAccount` PowerShell cmdlet:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.
2. Select the customer you want.
3. Select the down arrow to expand the customer's listing. You'll see information about the customer's *Domain name* and the customer's **Microsoft ID**.
4. Use the 16-digit **Microsoft ID** in the PowerShell cmdlet that follows this procedure.

The first PowerShell cmdlet adds the new partner as the reseller on the account:

```powershell
Connect-AzAccount -Tenant 'xxxx-xxxx-xxxx-xxxx'
```

The second cmdlet displays the roles on the account, including previous CSP partners:

```powershell
Get-AzRoleAssignment
```

#### Step 8: New partner removes outdated access permissions

To remove outdated access permissions, use the following steps:

1. In the Partner Center menu, select **Customers**.
1. Locate the customer on the customer list.
1. Double-click the customer's company name. The customer **Subscriptions** page appears.
1. In the customer detail menu, select **Service management**.
1. Under **Microsoft Azure**, select  **Microsoft Azure Management Portal**.

## Transferring a previous Azure offer subscription without converting it to the Azure plan

This section briefly describes how the new Azure plan is being introduced. Then it describes a special case in which some subscriptions to the previous Azure offer can be transferred to another CSP without converting them to the new Azure plan.

> [!NOTE]
> To transfer a customer's Azure subscriptions that were purchased under the previous Azure offer to a new CSP *and convert them to the Azure plan*, (which is the default action), see the previous section [*Transferring an Azure subscription to another partner*](#transferring-azure-subscriptions-to-another-partner), and the article [*Transfer a customer's Azure subscriptions to a different CSP (under an Azure plan)*](./transfer-azure-subscriptions-under-azure-plan.md).

### The Azure plan and the previous Azure offer

Microsoft introduced a new commerce experience, the [Azure plan](./azure-plan-lp.md), in July 2021. To give partners time to incorporate new features with their services and transition customers from the previous Azure offer (MS-AZR-0145p) to the Azure plan, the previous Azure offer continues to be available for a limited time.

The transition from the previous Azure offer to the Azure plan is in three phases:

**Phase 1**: Since the introduction of the Azure plan in July 2021, all new Azure CSP program customers have been placed on the Azure plan. Partners can continue to transact the previous Azure offer with customers who have already purchased it.

**Phase 2**: On February 1, 2022, incentives and partner margin opportunity were removed from the previous Azure offer.

**Phase 3**: In phase 3 (planned for July 31, 2022), any remaining customers on the previous Azure offer will be migrated to the new Azure offer in the CSP program (Azure plan). Any existing Azure partner shared services (APSS) on the previous Azure offer will continue to be available until they're transferred to a different sales motion or until APSS is removed. APSS will eventually be removed from the previous Azure offer and won't be available as part of the new Azure offer (Azure plan).

### Transferring subscriptions without conversion

This section describes the special case of transferring a subscription that was purchased under the previous Azure offer to a new CSP provider, *without converting it to the Azure plan*.

A customer's subscription to the previous Azure offer can be transferred to a new CSP partner without conversion to the Azure plan by using the steps in the previous section, [Transferring Azure subscriptions to another partner](#transferring-azure-subscriptions-to-another-partner), if:

- The previous Azure offer is still available.
- Both the current partner and the new partner have a customer with a subscription to the previous Azure offer.

If only the current partner has a customer with a subscription to the previous Azure offer, the current partner can use the transition tool to move the customer's subscription to the new partner while simultaneously converting it to the new Azure plan.

> [!NOTE]
> Only partners that have a direct-billing relationship with Microsoft can access the transition tool. Indirect resellers need to work with their indirect providers to use the transition tool.

## Next steps

- [Transfer Azure subscriptions](/azure/cost-management-billing/manage/transfer-subscriptions-subscribers-csp)
- [Transfer Azure subscriptions under an Azure plan](transfer-azure-subscriptions-under-azure-plan.md)
- Download the [CSP Subscription Transfer form](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RWwTWC)
- Learn about [multi-partner support](multipartner.md)
- Learn about [multi-channel support](multichannel.md)
