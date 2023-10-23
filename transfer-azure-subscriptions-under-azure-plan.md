--- 
title: Transfer Azure subscriptions, reservations, or savings plans (under an Azure plan) to another CSP partner
description: Learn how to change the Cloud Solution Provider program partner associated with a customer's Azure subscriptions under an Azure plan and/or reservations. 
ms.topic: how-to 
ms.service: partner-dashboard 
ms.subservice: partnercenter-customers 
author: brentserbus
ms.author: brserbus
ms.date: 09/14/2023 
--- 

# Transfer a customer's Azure subscriptions or reservations, or savings plans (under an Azure plan) to a different CSP

**Appropriate roles**: Admin agent

This article describes how customers can change their Azure subscriptions, reservations, and/or savings plans from one partner in the Cloud Solution Provider (CSP) program to another, under an Azure plan.

> [!NOTE]
> This article describes transferring **Azure plan new commerce experience subscriptions** from one partner to another. Instructions on transferring Azure legacy subscriptions can be found in the [manual Azure legacy transfer topic](/partner-center/switch-azure-subscriptions-to-a-different-partner).

To switch a customer's Azure subscriptions, reservations, and/or savings plans from a different partner, follow these steps. The current partner, the future partner, and the customer all have steps to complete.

> [!NOTE]
> Only partners who have a direct-billing relationship with Microsoft can access the transition tool. Indirect resellers need to work with their indirect providers to use this transition tool.

The customer needs to communicate with both the current and the future partner before the transition tool can be used. An offline conversation needs to occur to avoid confusion and churn. Partners and customers should understand the following considerations and prerequisites before starting a transition.

## Considerations

- Azure Reserved Instances will move with a subscription to the future partner. After a transfer of upfront paid Reservations, the customer won't be able to cancel or exchange those reservations. If a transferred RI is on monthly payment plan, the next monthly charge would appear on the destination partner's reconciliation file, rather than a prorated amount. The previous monthly charge (in full monthly rate) would appear on the source partner's reconciliation file.
- If you're requesting the transfer of an Azure reserved instance and your billing currency is different than the current partner, the Azure reserved instance will be canceled at the start of the next billing cycle (applicable to reservations not paid upfront). In order to continue service, you need to repurchase the Azure reserved instance. This behavior also applies to savings plan transfers.
- CSP pricing for Azure services under the current partner won't transition.
- If you transfer [previous Azure offer (MS-AZR-0145p)](https://go.microsoft.com/fwlink/p/?linkid=2164140) subscriptions, those Azure subscriptions are simultaneously converted to new Azure offer subscriptions within an Azure plan.
- Support responsibilities for the customer will move to the future partner.
- Billing and invoicing will move to the future partner at time of transfer. This behavior also applies to Savings plan transfers.
- Azure role-based access control (RBAC) isn't affected by transfers.
- Admin on behalf of (AOBO) won't be granted by default to the future partner.
- Third-party Azure Marketplace products transfer as long as the products pass the Azure Marketplace eligibility check.
  - There are no special discounts or regional restrictions.
  - The products aren't subscription based.
  - The future partner should work with the publisher to make sure the publisher is on the allowlist for deployment of the product.
  - If any of these conditions aren't met, the Azure Marketplace products should be canceled. Then the Azure subscriptions should be transferred, and the Azure Marketplace products should be purchased with the new partner.

### Specific for Azure RI transfer

Single scope Reserved Instances appear in the same section as Azure subscriptions, whereas Shared scope Reserved Instances appear in the Reservations section.

:::image type="content" source="media/modernazuretransfers/ri-transfer.png" lightbox="media/modernazuretransfers/ri-transfer.png" alt-text="Screenshot that shows reserved instance transfer.":::

Both active and inactive reservations appear in the transfer wizard, and partners should only select the active ones. Otherwise, the transfer request can't be accepted. A Source partner is allowed to transfer only active Azure subscriptions and RIs (single and shared scope).

The following types of Reserved Instances can be available to select:

- Single scope: These Reserved Instances are associated with Azure subscription and visible when partner selects the chevron next to Azure subscription (Step 2 in the above image).
- Single scope (orphaned Reserved Instances): These Reserved Instances are seen when an Azure subscription is transferred without the associated RI. Orphaned single scope RIs are also visible when the partner selects the chevron next to the Reservations (Step 3).
- Shared scope: Shared scope reservations are independent RIs that are visible when the partner selects the chevron next to the Reservations (Step 3).

The following are the key scenarios and corresponding steps for how a partner may transfer RIs:

- If the Source partner is transferring only an Azure subscription (no active or inactive single or shared scope RIs): The source partner needs to select only Azure subscriptions (select the chevron in Step 1 and ensure no RIs are selected).
- If the Source partner is transferring an Azure subscription and single scope active RIs, Steps 1 and 2 are required: Ensure all inactive, canceled, and deleted single scope RIs are unchecked.
- If the Source partner is transferring an Azure subscription, single scope RIs, and shared scope RIs, Steps 1, 2 and 3 are required: Ensure all inactive, canceled, and deleted single and shared scope RIs are unchecked.

Once a partner has selected all the active Azure subscriptions, reservations, and/or Azure savings plans to transfer, the partner can then select on the "Accept and transfer" button. It's critical partners ensure no inactive, canceled, or deleted items are selected, or the transfer flow can't begin.

## Prerequisites

- The customer notifies the current CSP partner of the intent to transition.
- The future CSP partner works with the customer to ensure the customer needs can be met.
- The future CSP partner establishes a relationship with the customer and purchases an Azure plan before the transition starts.
- The customer signs a Microsoft Customer Agreement with the future CSP partner.
- The future CSP partner signs the Microsoft Partner Agreement before using the transition tool.

> [!NOTE]
> For Azure subscriptions, the self-serve transition tool can be used when the customer's current partner has either the previous Azure offer (MS-AZR-0145p) or the new Azure offer (Azure plan). In either case, when the transfer is complete, the Azure subscriptions will be under an Azure plan with the future partner.

## Customer tasks

To transfer Azure subscriptions, reservations, and/or savings plans (under an Azure plan), the customer must start the process by contacting the current partner. The customer should collect the current partner's company name and Microsoft ID so the future partner can complete the transfer request form on the customer's behalf.

Customers must also identify the Azure subscriptions, reservations, and/or savings plans (under an Azure plan) they want to transfer from the current partner. You can't change partners for Office 365, Enterprise Mobility Suite, or Microsoft Dynamics CRM subscriptions.  

> [!NOTE]
> It's the future partner's responsibility to complete the transfer request form that initiates the transfer process. Microsoft can't intervene on behalf of the customer or the current partner. The customer should plan to work closely with the future and current partners to ensure the transition goes smoothly.

## Future partner tasks

The future partner of the subscription needs to complete a transfer request form from Partner Center to request a subscription transfer:

1. In the left pane of Partner Center, select **Customers**, and then select the customer for whom you want to complete the transfer request.
1. On the customer-specific menu, select **Subscriptions**.
1. On the **Transfer requests** tab, select **Add new request**:

    :::image type="content" source="media/modernazuretransfers/Transferrequestheader.png" lightbox="media/modernazuretransfers/Transferrequestheader.png" alt-text="Screenshot that shows the Transfer requests tab.":::

1. Complete the **New transfer request** form:
    - For one-tier partners:

    :::image type="content" source="media/modernazuretransfers/CompleteTrnasferRequestForm.png" lightbox="media/modernazuretransfers/CompleteTrnasferRequestForm.png" alt-text="Screenshot that shows the New transfer request form.":::

    - For two-tier partners, make sure to specify a reseller ID in the additional entry field **(required)**

1. Select **Send transfer request** > **Send**.
1. Review the transfer request confirmation:

    :::image type="content" source="media/modernazuretransfers/TransferPending.png" lightbox="media/modernazuretransfers/TransferPending.png" alt-text="Screenshot that shows a transfer request confirmation.":::

  > [!NOTE]
  > The future partner can cancel the transfer request by selecting **Cancel request** in the upper-right corner of the window only when the transfer request status is "pending." After the transfer request status is "in progress" or "complete," cancellations aren't possible.

1. Transferring the Azure subscription to the **Future partner** requires the customer to have an existing Azure plan. After the transfer is complete, the future partner may cancel the default subscription that is automatically created when acquiring an Azure plan.

## Current partner tasks

The current partner's Admin agent for the customer receives an email stating that a customer is requesting a transfer of subscriptions:

:::image type="content" source="media/modernazuretransfers/SourceReviewEmail.png" alt-text="Screenshot that shows an email notification of a customer request for transfer.":::

The current partner needs to review and accept the transfer request form from Partner Center to complete the subscription transfer.

> [!NOTE]
> If the current partner doesn't respond within 30 days, the request will expire and the future partner will need to create a new transfer request. The partner cannot remove or cancel the expired transfer request in Partner Center.

1. Take one of the following actions:
   1. Select **Review transfer request** in the email, **OR**
   1. In the left pane of Partner Center, select **Customers**, and then select the customer for whom the transfer request has been submitted.
1. On the customer-specific menu, select **Subscriptions**.
1. On the **Transfer requests** tab, expand the transfer information by selecting the **Transfer request ID** under **Received requests**:

   :::image type="content" source="media/modernazuretransfers/ReviewRequest.png" lightbox="media/modernazuretransfers/ReviewRequest.png" alt-text="Screenshot that shows the Transfer requests tab, as seen by the current partner.":::

1. Review the transfer request. Select the requested Azure subscriptions, reservations, and/or savings plans (Azure plan) to transfer.
   - Before you continue, note:
     - You won't have access to the selected Azure subscriptions, reservations, and/or savings plans (Azure plan).
     - You won't be invoiced for further usage.

1. Select **Accept and transfer** to complete the transfer process:

   :::image type="content" source="media/modernazuretransfers/SelectSubs.png" lightbox="media/modernazuretransfers/SelectSubs.png" alt-text="Screenshot that shows the Review transfer request screen.":::

   - If you have a customer with previous Azure offer subscriptions (MS-AZR-0145p), continue in the same way, choosing the items to transfer and then selecting **Accept and transfer** to complete the transfer process.

1. View the transfer acceptance confirmation.

At this point, an email notifies the future partner, the customer, and the current partner about the accepted transfer request.

After the transition is accepted, the transfer status might remain as "pending" for up to 15 minutes while the system is updated. If this process takes longer, the system keeps trying for three days. If the transfer status remains in "pending" for longer than three days, the partner should submit a service request.

After the transfer is complete, the Azure subscriptions, reservations, and/or savings plans included in the request will appear in the Azure plan of the future partner. They'll no longer be listed with the current partner.

> [!NOTE]
>Indirect providers should inform their indirect resellers that the transfer request has been accepted.

### Managing your transferred customer Azure subscriptions, reservations, and/or savings plans (Azure plan)

Access to existing users, groups, or service principals that were assigned via Azure RBAC isn't affected during the transition. [Azure RBAC](/azure/role-based-access-control/overview) helps your customer manage who has access to Azure resources, what they can do with those resources, and what areas they have access to.

As a new partner, you won't have any RBAC access to your customer's resources after the transfer. Your customer's previous partner retains RBAC access. Work with your customer to understand who has insight into the Azure subscriptions, reservations, and/or savings plans and how to make any needed changes.

Your customer needs to remove Azure RBAC access for the previous partner and add access for you. For more information about providing access, see [What is Azure role-based access control (Azure RBAC)?](/azure/role-based-access-control/overview). For more information about removing access, see [Remove a role assignment](/azure/role-based-access-control/role-assignments-portal#remove-a-role-assignment).

Also, you don't automatically get [Admin on Behalf Of (AOBO)](https://channel9.msdn.com/Series/cspdev/Module-11-Admin-On-Behalf-Of-AOBO) access to your subscriptions and/or reservations. AOBO is necessary so that you can manage your customer's Azure subscriptions and/or reservations. For more information about Azure privileges, see [Obtain permissions to manage a customer's service or subscription](./customers-revoke-admin-privileges.md).

## Next steps

- [Azure RBAC](/azure/role-based-access-control/overview)
- [Obtain permissions to manage a customer's service or subscription](./customers-revoke-admin-privileges.md)
