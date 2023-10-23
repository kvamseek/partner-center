---
title: Link a PartnerID for Azure performance PAL or DPOR 
ms.topic: how-to
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Link a PartnerID for Azure performance - PAL or DPOR.
author: preetisgit
ms.author: presharm
ms.date: 10/27/2022
---

# Link a PartnerID with PAL or DPOR

**Appropriate roles**: Account admin

> [!NOTE]
> The Microsoft Partner Network is now called the Microsoft AI Cloud Partner Program.

Microsoft partners provide services that help customers achieve business and mission objectives using Microsoft products. Partners need access to the customer's environment when acting on behalf of the customer in order to manage, configure, and support Azure services.

You can link to a PartnerID in one of the following ways.

- **Partner Admin Link (PAL)** is used for modern commerce platform (Azure plan) subscriptions. It enables Microsoft to identify and recognize partners who drive Azure customer success. Microsoft can attribute influenced and Azure consumed revenue to your organization based on the account's permissions (Azure role) and scope (subscription, resource group, resource). PAL tracking capabilities are automated and don't require partner input.

- **Digital Partner of Record (DPOR)** is used for Enterprise Agreement (EA) subscriptions. It associates servicing partners to a Microsoft cloud subscription. It's the online capability to attach a partner to a customer's Microsoft online subscription. DPOR benefits the customer, the partner, and Microsoft. DPOR also enables partners to help customers optimize their usage for desired business outcomes. If a customer moves from EA to the modern commerce platform, DPOR status doesn't move with them.

> [!NOTE]
> If a subscription is moved from Enterprise Agreement to modern commerce platform, the PartnerID is not transferred.

If you encounter problems with the following procedures, contact [Azure Support](https://azure.microsoft.com/support/options).

## Get access from your customer

Before you link your PartnerID, your customer must give you access to their Azure resources by using one of the following options:

- **Guest user**: Your customer can add you as a guest user and assign any Azure roles. For more information, see [Add guest users from another directory](/azure/active-directory/external-identities/what-is-b2b).

- **Directory account**: Your customer can create a user account for you in their own directory and assign any Azure role.

- **Service principal**: Your customer can add an app or script from your organization in their directory and assign any Azure role. The identity of the app or script is known as a *service principal*.

- **Azure Lighthouse**: Your customer can delegate a subscription (or resource group) so that your users can work on it from within your tenant. For more information, see [Azure delegated resource management](/azure/lighthouse/concepts/azure-delegated-resource-management).

> [!WARNING]
> The role assignment you create might give you highly privileged access to the customer's environment. Ensure you follow good practices for managing privileged accounts.

## Link to a PartnerID with PAL

Use linking to a PartnerID with PAL for the modern commerce (Azure plan) platform subscriptions.

When you have access to the customer's resources, use the Azure portal, PowerShell, or the Azure CLI to link your PartnerID (PartnerID) to your user ID or service principal. Link the PartnerID in each customer tenant.

### Use the Azure portal to link to a new PartnerID

1. Go to [Link to a PartnerID](https://portal.azure.com/#blade/Microsoft_Azure_Billing/managementpartnerblade) in the Azure portal.

2. Sign in to the [Azure portal](https://portal.azure.com).

3. Enter the Microsoft PartnerID. The PartnerID is the [Microsoft AI Cloud Partner Program](https://partner.microsoft.com/) ID for your organization. Be sure to use the **Associated PartnerID** shown on your partner profile. It’s typically known as your Partner Location Account MPN ID.

   :::image type="content" source="media/pal-partner-id.png" alt-text="Screenshot that shows link to a PartnerID page.":::

4. To link a PartnerID for another customer, select **Switch directory**. Under Switch directory, select your directory or use Advanced filter.

   :::image type="content" source="media/pal-partner-id-switch-directory.png" alt-text="Screenshot of switch directory.":::

### Use PowerShell to link to a new PartnerID with PAL

1. Install the [Az.ManagementPartner](https://www.powershellgallery.com/packages/Az.ManagementPartner/) PowerShell module.

2. Sign in to the customer's tenant with either the user account or the service principal. For more information, see [Sign in with PowerShell](/powershell/azure/authenticate-azureps).

   ```powershell
   C:\> Connect-AzAccount -TenantId XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
   ```

3. Link to the new PartnerID. The PartnerID is the PartnerID for your organization. Use the **Associated PartnerID** shown on your partner profile.

   ```powershell
   C:\> new-AzManagementPartner -PartnerId 12345
   ```

   **Get the linked PartnerID**

   ```powershell
   C:\> get-AzManagementPartner
   ```

   **Update the linked PartnerID**

   ```powershell
   C:\> Update-AzManagementPartner -PartnerId 12345
   ```

   **Delete the linked PartnerID**

   ```powershell
   C:\> remove-AzManagementPartner -PartnerId 12345
   ```

### Use the Azure CLI to link to a new PartnerID

Use the following steps to link to a new PartnerID with the Azure command-line interface (CLI).

1. Install the Azure CLI extension.

   ```powershell
   C:\ az extension add --name managementpartner
   ```

2. Sign in to the customer's tenant with either the user account or the service principal. For more information, see [Sign in with the Azure CLI](/cli/azure/authenticate-azure-cli).

   ```powershell
   C:\ az login --tenant <tenant>
   ```

3. Link to the new PartnerID. The PartnerID is the [Microsoft AI Cloud Partner Program](https://partner.microsoft.com/) ID for your organization.

   ```powershell
   C:\ az managementpartner create --partner-id 12345
   ```

   **Get the linked PartnerID**

   ```powershell
   C:\ az managementpartner show
   ```

   **Update the linked PartnerID**

   ```powershell
   C:\ az managementpartner update --partner-id 12345
   ```

   **Delete the linked PartnerID**

   ```powershell
   C:\ az managementpartner delete --partner-id 12345
   ```

### Frequently asked questions about PAL association

#### Who can link the PartnerID with PAL association?

Any user from the partner organization who manages a customer's Azure resources can link the PartnerID to the account.

#### Can a PartnerID be changed after it's linked with PAL association?

Yes. A linked PartnerID can be changed, added, or removed.

#### What if a user has an account in more than one customer tenant?

The link between the PartnerID and the account is made for each customer tenant. Link the PartnerID in each customer tenant.

However, if you're managing customer resources through Azure Lighthouse, you should create the link in your service provider tenant, using an account that has access to the customer resources. For more information, see [Link your PartnerID to track your impact on delegated resources](/azure/lighthouse/how-to/partner-earned-credit).

#### Can other partners or customers edit or remove the link to the PartnerID?

The link is associated at the user account level. Only you can edit or remove the link to the PartnerID. The customer and other partners can't change the link to the PartnerID.

#### Which PartnerID should I use for the PAL association if my company has multiple?

Be sure to use the **Associated PartnerID** shown in your partner profile.

#### Where can I find influenced revenue reporting for linked PartnerID?

Cloud product performance reporting is available to partners in Partner Center at [My Insights dashboard](https://partner.microsoft.com/membership/reports/myinsights). You need to select Partner Admin Link as the partner association type.

#### Why can't I see my customer in the reports?

You can't see the customer in the reports for one of the following reasons:

- The linked user account doesn't have [Azure role-based access control (Azure RBAC)](/azure/role-based-access-control/overview) on any customer Azure subscription or resource.

- The Azure subscription where the user has [Azure role-based access control (Azure RBAC)](/azure/role-based-access-control/overview) access doesn't have any usage.

#### Does link PartnerID work with Azure Stack?

Yes. You can link your PartnerID for Azure Stack.

#### How do I link my PartnerID if my company uses [Azure Lighthouse](/azure/lighthouse/overview) to access customer resources?

For Azure Lighthouse activities to be recognized, you must associate your PartnerID with at least one user account that has access to each of your onboarded subscriptions. You must do so in your service provider tenant rather than in each customer tenant.

For simplicity, we recommend creating a service principal account in your tenant, associating it with your PartnerID, and granting it access to every customer you onboard with an [Azure built-in role that is eligible for partner earned credit](azure-roles-perms-pec.md). For more information, see [Link your PartnerID to track your impact on delegated resources](/azure/lighthouse/how-to/partner-earned-credit).

#### How do I explain Partner Admin Link (PAL) to my customer?

Partner Admin Link (PAL) enables Microsoft to identify and recognize those partners who are helping customers achieve business objectives and realize value in the cloud. Customers must first provide a partner access to their Azure resource. Once access is granted, the partner's PartnerID (PartnerID) is associated. This association helps Microsoft understand the ecosystem of IT service providers and to refine the tools and programs needed to best support our common customers.

#### What data does PAL collect?

The PAL association to existing credentials provides no new customer data to Microsoft. It simply provides the telemetry to Microsoft where a partner is actively involved in a customer's Azure environment. Microsoft can attribute influenced and Azure consumed revenue from customer environment to partner organization based on the account's permissions (Azure role) and scope (Management Group, Subscription, Resource Group, Resource) provided to the partner by customer.

#### Does PAL association affect the security of a customer's Azure Environment?

PAL association only adds partners' PartnerID to the credential already provisioned. It doesn't alter any permissions (Azure role) or provide extra Azure service data to the partner or Microsoft.

## Link to a PartnerID with DPOR

Linking to a PartnerID with Digital Partner of Record (DPOR) is used for Enterprise Agreement (EA) subscriptions.

DPOR associates servicing partners to a Microsoft cloud subscription. It's an online capability to attach a partner to a customer's Microsoft online subscription. DPOR benefits the customer, the partner, and Microsoft. DPOR enables partners to help customers optimize their usage for desired business outcomes.

- Partners must be added as the DPOR each time a new subscription is sold, regardless of whether their customer is new or existing.

- Microsoft policy is that only the customer can designate a DPOR for their subscriptions.

### Add a DPOR to your subscription

Use the following instructions to add a Digital Partner of Record to your subscription.

1. Sign in on the [Azure portal](https://portal.azure.com).

2. Select **Subscriptions** then the relevant subscription where you'll add a partner as DPOR.

3. Select **Partner Information** and  enter the partner's PartnerID.

4. Select **Validate ID**.

   The name of the partner you're adding as DPOR will appear on the UI.

5. Select **Save partner**.

   A notification will tell you the partner information changed. It might take some time for the portal to reflect this new information. If you don't see it in a few minutes, refresh the page.

   :::image type="content" source="media/dpor-confirmation.png" alt-text="Screenshot of confirmation of DPOR.":::

### Frequently asked questions for Digital Partner of Record (DPOR) association

#### What is the benefit of adding a DPOR to my subscription?

The following are the **customer** benefits of adding the DPOR to the subscription.

- Control of which specific partner you wish to designate for online subscription access and benefits
- Flexibility to change or remove a partner, as desired
- Enhanced support and engagement from partner and Microsoft
- Optimized usage and consumption of services, as supported by designated partners
- Improved partner discoverability

The following are the benefits to you, the **partner**.

- Cloud Competency attainment
- Incentives designation, as approved by your customer preference
- Closer engagement with Microsoft technical, marketing, and account teams
- Improved customer discoverability
- Microsoft visibility to your end-customer preference as selected and/or designated

#### Who can attach a partner of record?

The administrator role, also known as the "owner," is the only role within the tenant or account that can attach a partner of record. Service admins, coadmins, and partners who have been designated as delegated admins can't change the partner of record.

#### When should I add a partner of record to my Azure subscriptions?

We recommend assigning a partner of record to Azure subscriptions immediately. This capability is also enabled for Microsoft 365, Dynamics 365, Business Central, Intune, and Enterprise Mobility Suite subscriptions in the admin portal for those services.

#### Once a DPOR has been assigned, can it be changed? Is there a limit to the number of changes possible?

DPOR designation can be changed, added, and removed as many times as customers wish by following these steps:

1. Sign in to the [Azure portal](https://portal.azure.com).

2. Go to the  **Partner Information** screen and select the delete icon.

3. Select **Yes** when asked to confirm that you want to remove current partner information.

#### Can there be more than one DPOR assigned to a subscription at the same time?

No, there can be only one DPOR designated on any single subscription at a time.

#### What customer data will a partner be able to see as DPOR?

Partners with DPOR association to customer Azure subscriptions can access the following customer data.

- Customer ID and customer name
- Customer's consumption/usage data
- Subscription ID and name
- Key subscription attributes such as start and end dates
- Aggregated metered consumption/seat usage data
- DPOR association date
- Aggregated details of Azure services and seat-based workloads being used

## Next steps

- [Partner Center Insights](partner-center-insights.md)
