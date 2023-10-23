---
title: Partner earned credit troubleshooting guide
ms.topic: article
ms.date: 01/25/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-billing
ms.custom: has-azure-ad-ps-ref
description: Learn how to solve invoice issues and other problems with partner earned credit (PEC).
author: sourishdeb
ms.author: sodeb
---

# Partner earned credit troubleshooting guide

**Appropriate roles**: Global admin | User management admin | Admin agent | Billing admin | Sales agent

## Troubleshooting common scenarios

With the Azure new commerce experience, partners can receive discounts through partner earned credit (PEC) for services managed. PEC is only granted to partners with eligible permissions. Find out [who is eligible for PEC, how it's calculated, and how it's paid out](partner-earned-credit-explanation.md).

This article provides basic troubleshooting guidance if PEC isn't granted.

### Prerequisites

If you have issues with PEC, such as access or missing information, start by checking the following items.

> [!NOTE]
> Only indirect providers and direct-bill partners are eligible to earn PEC.

- Make sure you're looking at the G (new commerce experience) invoice and recon file. Azure plan and PEC aren't shown on the D (Legacy) invoice or recon file.

- Confirm that your Microsoft AI Cloud Partner Program agreement is active.

- Confirm that your offer is eligible. (Legacy Azure offers, Azure Reserved Instances, Azure Savings Plans, Azure SPOT VMs, and third-party products aren't eligible.)

- Confirm that you (or the indirect reseller set as reseller of record on the Azure plan) have a valid Administer on Behalf of (AOBO) or Azure role-based access control (Azure RBAC) role for the subscription/resource group/resource. Alternatively:
  - If you're using Azure Lighthouse, ensure that [your PartnerID has been linked with at least one user account](/azure/lighthouse/how-to/partner-earned-credit). Also check that it has access to that customer's subscription/resource group.
  - If you're using an Azure RBAC association, ensure that the user has an eligible role for PEC and Azure RBAC set in each customer tenant context.

- See if the customer has removed your AOBO permissions. The permissions were set by default when the Azure plan was provisioned. If they've been removed, see [Reinstate admin privileges for a customer's Azure Cloud Solution Provider (CSP) subscriptions](reinstate-csp.md).

- Confirm that you have admin access for the entire day.

- Confirm that you're reviewing the correct columns in your reconciliation files. For more info see [Azure plan billing: About your invoice reconciliation file](./azure-plan-billing.md).

### Multipartner scenarios

For PEC, it's only important that the transacting partner has set any of the available permission options. For the indirect model, it could be the provider, or the reseller, or both.

Another Partner setting additional AOBO or other permissions and setting additional Azure RBAC for users with Azure RBAC permissions won't affect PEC for the transacting Partner.

See the following table. MPN1 is an indirect provider, MPN2 is the indirect reseller linked to the transaction as reseller of record, and MPN3 is another CSP partner (direct or another indirect reseller):

|**Transacting partner (BillTo)**   |**Azure RBAC (for user or Lighthouse with PEC-eligible role)**   |**AOBO (PEC-eligible role)**   |**PEC**   |
|-----------------|:------------------|:------------------|:------------------|
|MPN1 |MPN1 |N/A |Yes|
|MPN1 |N/A |MPN1 |Yes|
|MPN1 |MPN2 |N/A |Yes|
|MPN1 |N/A |MPN2 |Yes|
|MPN1 |MPN3 |MPN1 |Yes|
|MPN1 |MPN1 |MPN3 |Yes|
|MPN1 |MPN1 |MPN2 |Yes|
|MPN1 |MPN2 |MPN1 |Yes|
|MPN1 |MPN2 |MPN3 |Yes|
|MPN1 |MPN3 |MPN2 |Yes|
|MPN1 |MPN3 |N/A |No|
|MPN1 |N/A |MPN3 |No|
|MPN1 |N/A |N/A |No|
|MPN1 |MPN3 |MPN3 |No|

### Azure subscription transfers

When a partner [transfers an Azure subscription from or to another partner](transfer-azure-subscriptions-under-azure-plan.md), no permissions are changed for this transfer.

Therefore, if AOBO or another permission model was used before the transfer, with permissions set for the old "transacting partner," the permissions will still point to the old partner after the transfer. But now, another partner becomes the "transacting partner."

For any Azure subscription transfers, it's advisable that the new target partner adds permissions, such as Azure RBAC, before the transfer. They can safely do that without affecting the PEC of the old partner until the transfer.

### PartnerID updates

Partner Center allows you to [change the PartnerID associated with your CSP enrollment](update-your-partner-profile.md#update-your-partnerid-associated-with-your-csp-account). Updating the PartnerID to another Microsoft AI Cloud Partner Program location ID within the same Microsoft AI Cloud Partner Program global organization (another Microsoft AI Cloud Partner Program location ID under the same Microsoft AI Cloud Partner Program global ID) doesn't affect PEC.

When the PartnerID is changed to a location ID in a different Microsoft AI Cloud Partner Program organization, however, PEC might be affected. In this instance, and when PEC turns out to be missing, we recommend contacting support (mention that you recently remapped your CSP enrollment to a different Microsoft AI Cloud Partner Program org).

## How to verify AOBO permissions

When a partner creates an Azure Plan subscription for a customer, AOBO is set in the form of a "foreign principal. The foreign principal inherits owner permissions on the Azure subscription. The AOBO permissions mean that a certain group in the CSP Partner Center tenant (Admin Agents) will inherit [those permissions](customers-revoke-admin-privileges.md#delegated-admin-privileges-in-azure-ad).

The foreign principal, as seen in the Azure portal, doesn't include details about which group it maps to in the specific partner tenant.

When you view the foreign principal in the Azure portal, it shows a partner name, such as *"Foreign Principal for 'Contoso' …"*, but *"Contoso"* is only the display name of the Azure AD tenant of the partner, and it's not unique.

:::image type="content" source="media/billing/pec-troubleshoot-non-unique.png" alt-text="Non-unique display names.":::

Using AZ PowerShell or Azure CLI is required to verify with 100% certainty that the AOBO is set correctly, pointing to the correct group in the correct CSP tenant.

### Step 1 - Identify the objectIDs of the agent groups of the transacting partner

- **Via Azure portal**: Partners can sign in to the Azure portal in their own tenant and search for the respective groups in **Azure Active Directory > Groups**. The ObjectID is displayed to the right of the group name.

:::image type="content" source="media/billing/pec-groups-object-id.png" alt-text="Getting object ID from the Azure portal interface.":::

- **Via PowerShell**: Start PowerShell (either [local PowerShell](/powershell/scripting/windows-powershell/install/installing-windows-powershell) or [Azure Cloud Shell](/azure/cloud-shell/overview)).

Before using Azure Cloud Shell, you'll need to set up a storage account. This account will incur a small monthly cost in the Azure subscription available in the tenant context. You can delete the share after the steps that follow.

Make sure you have the following modules installed and updated to the newest version:

- [AzureAD module](/powershell/module/azuread/?view=azureadps-2.0&preserve-view=true)
- [AZ PowerShell module](/powershell/azure/new-azureps-module-az?view=azps-6.6.0&preserve-view=true) (not required for Cloud Shell)

If needed, use the following `cmdlets` from PowerShell windows to install these modules:

```powershell
Install-Module -Name AzureAD -Force
```

```powershell
Install-Module -Name Az -AllowClobber -Force
```

First, connect to the Partner Center tenant with your Partner Center user account and get the objectIDs of the AdminAgents and HelpdeskAgents group:

```powershell
Connect-AzureAD -TenantDomain CSPtenantname.onmicrosoft.com
```

Sign in with your Partner Center credentials:

:::image type="content" source="media/billing/shell-pc-account.png" alt-text="Shell example of Partner Center connection.":::

Query the information about the Agent Groups:

```powershell
Get-AzureADGroup | Where-Object { $_.DisplayName.Endswith('Agents') }
```

The `ObjectID` of the groups will be displayed along with their names:

:::image type="content" source="media/billing/shell-pc-groups.png" alt-text="Shell example of ObjectID of groups.":::

> [!NOTE]
> If you do not get a result, make sure you have connected to your Partner Center account.

> [!NOTE]
> Indirect resellers won't see a SalesAgents group. This step only needs to be done one time, since AOBO in each customer tenant will use the same IDs.

### Step 2 - Compare ObjectIDs to the ones used by the foreign principal

It's important to use the TenantID as the value for the tenant parameter (rather than the tenant domain name) with a user account that either:
      - has access to multiple directories/tenants, such as your Partner Center user account, or
      - has been added as guests to multiple tenants.

Therefore, you need the TenantID for the given customer.

- **Via Azure portal**: You can get the TenantID easily from the customer list in Partner Center. The tenantID is labeled "Microsoft ID":

  :::image type="content" source="media/billing/customer-list-tenant-id.png" alt-text="Microsoft ID as tenantId.":::

- **Via PowerShell**: Connect to the customer's Azure subscription with valid credentials. The credentials should have permission to read the Azure subscription and AzureAD of the customer tenant:

   ``` powershell
   Connect-AzAccount -Tenant $CustomerTenantID
   ```

  - Read role assignments for the Foreign Principal of the customer's Azure subscriptions:

   ``` powershell
   Get-AzRoleassignment | ? {$_.DisplayName -like "Foreign*"}
   ```

   :::image type="content" source="media/billing/role-assignment.png" alt-text="Shell example role assignment.":::

  - The resulting ObjectID should match the ObjectID of either the AdminAgent or HelpDeskAgent group identified in Step 1.

### Summary

Every aspect needs to match up to receive PEC via AOBO:

- The customer's Azure subscription has a foreign principal with eligible Azure RBAC role assignment.
- The ObjectID of the group used by the foreign principal refers to the ObjectID of either the AdminAgent or HelpdeskAgent group in the partner tenant.
- "Partner tenant" means the direct bill partner tenant. In the indirect model, it means the indirect provider or indirect reseller partner tenant.

### Sample scripts

This section contains sample scripts that can help gather the information across multiple subscriptions and store them in a .CSV file. These scripts are meant as examples and provided as-is without support. Though the scripts don't make modifications in the setup, they should be thoroughly tested, and customization might be required for the concrete partner/customer scenario.

- **Listing AOBO details for a single customer**: This example uses Azure AD and Azure PowerShell modules.

``` powershell
### Install-Module -Name AzureAD -Force ###
### Install-Module -Name Az -AllowClobber -Force ###
### Variables ####
$CSVname = "c:tempAOBOchecker.csv"
$CustomertenantId = ""
### Get Agent-Groups Object IDs and write to CSV - This step needs to be done with a Partner Center User ###
Connect-AzureAD -TenantDomain $PartnerTenantDomain
$Headers = "GroupName`tObjectID`tPartnerTenantName`tPartnerTenantID" >>$CSVname
$PartnerTenant = Get-AzureADTenantDetail
$groups = Get-AzureADGroup | Where-Object { $_.DisplayName.Endswith('Agents') }
ForEach ($Group in $Groups)
{
$NewLine = $Group.DisplayName + "`t" + $Group.ObjectID + "`t" + $PartnerTenant.DisplayName + "`t" + $PartnerTenant.ObjectID
$NewLine >>$CSVname
}
### Get list of Azure Subscriptions for a customer, get list of Foreign Principals and add them to the same CSV ###
Clear-AzContext -Scope CurrentUser -Force
Connect-AzAccount -Tenant $CustomertenantId
$CustomerTenant = Get-AzureADTenantDetail
$CustomerTenantSubscriptions = Get-AzSubscription -TenantId $CustomertenantId
ForEach ($Subscription in $CustomerTenantSubscriptions)
{
$Roles = Get-AzRoleassignment -Scope /subscriptions/$Subscription | ? {$_.DisplayName -like "Foreign*"}
ForEach ($Role in $Roles)
{
$NewLine = $CustomerTenant.Domain + "`t" + $CustomerTenant.CustomerId + "`t" + $Subscription.Id + "`t" + $Role.DisplayName + "`t" + $Role.ObjectID + "`t" + $Role.RoleDefinitionName
$NewLine >>$CSVname
}
}
```

- **Listing AOBO details for multiple customers**: This code is for illustration purposes only.
  - Get a list of all subscriptions of CSP customers and all foreign principals and identify if there's a mismatch. This code can also be used to gather information for support.
  - Check which Azure subscriptions (Azure Plan Entitlements) have been sold and which are accessible with the current credentials.
  - For indirect resellers, this script works as well. But all subscriptions would have the note "not sold" even if they're the partner of record for this sale.

``` powershell
### Note - below examples use interactive login experience and aren't suitable for production use ###
### See https://learn.microsoft.com/partner-center/develop/enable-secure-app-model#powershell for info on how to authenticate to each customer tenant silently using secure app model ###
### Below examples use AzureAD, AZ and Partner Center PowerShell modules ###
### Install-Module -Name AzureAD -Force ###
### Install-Module -Name Az -AllowClobber -Force ###
### Install-Module -Name PartnerCenter -Force ###
### Variables ####
$PartnertenantDomain = "xyz.onmicrosoft.com"
$PartnerTenantID = ""
$CSVname = "c:tempAOBOchecker.csv"
### Get Agent-Groups Object IDs and write to CSV ###
Connect-AzureAD -TenantDomain $PartnerTenantDomain
$Headers = "GroupName`tObjectID`tPartnerTenantName`tPartnerTenantID" >>$CSVname
$PartnerTenant = Get-AzureADTenantDetail
$groups = Get-AzureADGroup | Where-Object { $_.DisplayName.Endswith('Agents') }
ForEach ($Group in $Groups)
{
$NewLine = $Group.DisplayName + "`t" + $Group.ObjectID + "`t" + $PartnerTenant.DisplayName + "`t" + $PartnerTenant.ObjectID
$NewLine >>$CSVname
}
### Get list of CSP Customers, get List of Azure Subscriptions, get list of Foreign Principals and add them to the same CSV ###
Connect-PartnerCenter -TenantID $PartnertenantID
$Customers = Get-PartnerCustomer
$Headers = "`r`nCustomerTenantName`tCustomerTenantID`tSubscriptionId`tForeignPrincipalName`tObjectID`tAzureRBACRole`tTimeChecked`tNotes`tCredentialsUsedForAccessCheck" >>$CSVname
Foreach ($customer in $Customers)
{
$AzurePlanId = Get-PartnerCustomerSubscription -CustomerId $Customer.CustomerId | ? {$_.OfferName -eq "Azure Plan"}
if ($AzurePlanID -eq $null)
{
Write-Host "Customer $($Customer.Name) does not have Azure Plan"
}
else
{
$AzurePlanSubscriptionsSold = Get-PartnerCustomerAzurePlanEntitlement -CustomerId $Customer.CustomerId -SubscriptionId $AzurePlanId.SubscriptionId
}
Clear-AzContext -Scope CurrentUser -Force
Connect-AzAccount -Tenant $Customer.CustomerId
$CurrentUser = Get-azcontext
$CustomerTenantSubscriptionsAccessible = Get-AzSubscription -TenantId $Customer.CustomerId
$SoldAndAccessibleSubscriptions = $AzurePlanSubscriptionsSold | Where {$CustomerTenantSubscriptionsAccessible -Contains $_}
$SoldButNotAccessibleSubscriptions = $AzurePlanSubscriptionsSold | Where {$CustomerTenantSubscriptionsAccessible -notcontains $_}
$NotSoldButAccessibleSubscriptions = $CustomerTenantSubscriptionsAccessible | Where {$AzurePlanSubscriptionsSold -notcontains $_}
ForEach ($Subscription in $SoldAndAccessibleSubscriptions)
{
$Roles = Get-AzRoleassignment -Scope /subscriptions/$Subscription | ? {$_.DisplayName -like "Foreign*"}
ForEach ($Role in $Roles)
{
$CurrentTime = Get-Date -format "dd-MMM-yyyy HH:mm:ss"
$NewLine = $Customer.Domain + "`t" + $Customer.CustomerId + "`t" + $Subscription.Id + "`t" + $Role.DisplayName + "`t" + $Role.ObjectID + "`t" + $Role.RoleDefinitionName + "`t" + $CurrentTime + "`t" + "Access with current credentials and sold as CSP Partner" + "`t" + $CurrentUser.Account.Id
$NewLine >>$CSVname
}
}
ForEach ($Subscription in $SoldButNotAccessibleSubscriptions)
{
$CurrentTime = Get-Date -format "dd-MMM-yyyy HH:mm:ss"
$NewLine = $Customer.Domain + "`t" + $Customer.CustomerId + "`t" + "N/A" + "`t" + "N/A" + "`t" + "N/A" + "`t" + "N/A" + "`t" + $CurrentTime + "`t" + "Sold via CSP, but no access with current credentials" + "`t" + $CurrentUser.Account.Id
$NewLine >>$CSVname
}
ForEach ($Subscription in $NotSoldButAccessibleSubscriptions)
{
$Roles = Get-AzRoleassignment -Scope /subscriptions/$Subscription | ? {$_.DisplayName -like "Foreign*"}
ForEach ($Role in $Roles)
{
$CurrentTime = Get-Date -format "dd-MMM-yyyy HH:mm:ss"
$NewLine = $Customer.Domain + "`t" + $Customer.CustomerId + "`t" + $Subscription.Id + "`t" + $Role.DisplayName + "`t" + $Role.ObjectID + "`t" + $Role.RoleDefinitionName + "`t" + $CurrentTime + "`t" + "Access with current credentials, but not sold as CSP Partner" + "`t" + $CurrentUser.Account.Id
$NewLine >>$CSVname
}
}
}
```

- The output of this script can then be formatted like this:

   :::image type="content" source="media/billing/output-format.png" lightbox="media/billing/output-format.png" alt-text="Output format example.":::

## How to verify Azure Lighthouse permissions and Azure PAL

Like AOBO, [Azure Lighthouse](/azure/lighthouse/concepts/cross-tenant-management-experience) allows groups of users in the (partner) management tenant to inherit delegated permissions in the customer's Azure subscription. The difference is that it allows for  more granular definition of groups and permission levels than AOBO.

For this permission model, it's easier to verify if it has been correctly set using the Azure portal UI. Only the partner can provide complete verification that the Azure Lighthouse setup is correct.

The following steps describe how to identify for which customers the Azure RBAC role permissions have been permanently delegated, and to which groups. Then, you can check if the user having the Azure RBAC association is a member of those groups.

### Step 1 – Check Lighthouse delegations on customers

Verify that applicable delegations are using PEC-eligible Azure RBAC roles.

- Open [Azure portal](https://portal.azure.com) (with a user from the partner's management tenant). Then search for "Lighthouse" and select **My customers**.

   :::image type="content" source="media/billing/azure-services-lighthouse.png" alt-text="Azure services Lighthouse example.":::

- Within the customer overview, choose **Delegations** on the left side. Doing so opens the list of resources (Subscriptions or Resource groups) where delegated access has been provided:

   :::image type="content" source="media/billing/delegations.png" alt-text="Delegations page.":::

- Open the delegations in the right column under "Role Assignments" to see which user group in the partner/management tenant inherits each kind of permissions (see "Role" column). You can also see if those permissions are permanent (see "Access Type" column):

   :::image type="content" source="media/billing/role-assignments-delegations.png" alt-text="Role assignments page":::

### Step 2 – Check group membership

Select the display name of the group. Do so opens the group details. Select "Members" to control which user has Azure RBAC set and is member of the respective group:

   :::image type="content" source="media/billing/group-memberships.png" alt-text="Group membership.":::

### Step 3 – Check if user has set up Azure PAL

Only the user who has set Azure PAL can check the Azure PAL assignment; no other admin user can do so. See *How do I explain Partner Admin Link (PAL) to my customer?* in [Link an Azure account to a PartnerID](/azure/cost-management-billing/manage/link-partner-id#frequently-asked-questions) for more information on how the user can verify if Azure PAL has been set, either via UI or PowerShell.

> [!NOTE]
> Azure PAL should use an PartnerID that is part of the same Microsoft AI Cloud Partner Program organization that is the transacting partner for this Azure subscription. In the indirect model, that can either be the PartnerID of the provider or the specific reseller attached to this sale.

### Step 4 - Check for time-bound group assignments

Because group membership might not be permanent, check if the group was enabled for privileged access management. Look where "Privileged access" on the left side under "Activity" in the group settings. If true, check if the user has an active assignment and the time frame for this assignment.

> [!NOTE]
> Because the assignment "end time" is when a user is automatically removed from the group, PEC would be lost for users who had Azure RBAC set. Similarly, PEC would only be granted after the assignment "start time."

:::image type="content" source="media/billing/privilege-access-group.png" alt-text="Privilege access group.":::

## How to verify individual user assignment and Azure PAL

In some cases, it might be more suitable to work with individual user accounts having permissions on Azure subscriptions. These accounts can be guest user accounts (from any tenant) or user accounts created in the customer tenant or service principals.

When using individual user accounts as a vehicle to earn PEC, the check involves just reviewing the assigned permissions in Azure subscription management for the user, and verifying the user has set Azure RBAC correctly. When a service principal is used, the checking of Azure RBAC needs to happen via PowerShell.

### Step 1 – Review permissions in Azure subscription management

- Open the [Azure portal](https://portal.azure.com). Make sure you're signed in as a user that has Azure RBAC role with at least read access to the subscription in question.

- Search for "Subscriptions" in the search bar to open subscription details:

  :::image type="content" source="media/billing/subscription-details.png" alt-text="Subscription details page.":::

- Go to "Access Control (IAM)" in the subscription details. Then select "Role assignments" to review users that have access on a subscription level and if the "Role" column shows PEC-eligible Azure RBAC roles. If permissions have been set on a resource group level, the same "Access Control (IAM)" view is also available within a resource group.

> [!NOTE]
> Permissions can also be granted to a group of users where the group membership of the user that has Azure RBAC set would need to be verified as well.

:::image type="content" source="media/billing/access-control.png" alt-text="Access control.":::

### Step 2 – Ensure permissions are permanent and that no Deny assignments apply

Although it may look like users have access, their permissions might still be temporary or blocked via Deny assignments.

Using the Privileged Identity Management (PIM) Azure RBAC role assignment might be time bound. Although you might see users with permission, they might only exist for a short time. To verify that the Azure RBAC role assignment is permanent, check the PIM administration in Azure portal. Specifically, check where Azure resources in the subscription are being managed by PIM policies, and if the user is subject to any policies.

:::image type="content" source="media/billing/not-managed-by-pim.png" alt-text="Azure subscription isn't managed via PIM.":::

Also, the list of permissions might show the user has permissions on the subscription, but there might be Deny assignments that still block the user from accessing something. In "Access Control (IAM)" select the **Deny** assignment tab to see if Deny assignments apply:

:::image type="content" source="media/billing/deny-assignments.png" alt-text="Deny assignments.":::

> [!NOTE]
> For completeness, partners should also verify that on resource groups no Deny assignments exist within the subscription.

### Step 3 – Check if user has set up Azure PAL

Only the user who has set up Azure PAL can check the Azure PAL assignments; no other admin user can do so. For more information on how the user can verify Azure PAL has been set, see [Link an Azure account to a PartnerID](/azure/cost-management-billing/manage/link-partner-id#:~:text=Partner%20Admin%20Link%20%28PAL%29%20enables%20Microsoft%20to%20identify,Microsoft%20Partner%20Network%20ID%20%28MPN%20ID%29%20is%20associated).

> [!NOTE]
> Azure PAL should use an PartnerID that is part of the same Microsoft AI Cloud Partner Program organization that is the transacting partner for this Azure subscription. In the indirect model, this can either be the PartnerID of the provider or the PartnerID of the reseller attached to this sale.

## Next steps

- [Partner earned credit - overview](partner-earned-credit.md)
- [Roles, permissions for partner earned credit](azure-roles-perms-pec.md)
