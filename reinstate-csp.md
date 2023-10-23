---
title: Reinstate admin privileges for Azure CSP
ms.topic: how-to
ms.date: 8/1/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Learn how to help customers reinstate a partner's admin privileges so the partner can help manage a customer's Azure Cloud Solution Provider (CSP) subscriptions.
author: kvamseek
ms.author: vamseekk
---

# Reinstate admin privileges for a customer's Azure CSP subscriptions

**Appropriate roles**: Global admin | Admin agent

As a Cloud Solution Provider (CSP) program partner, your customers often rely on you to manage their Azure usage and their systems. You must have admin privileges to help them. If you don't already have admin privileges, you can work with your customer to reinstate them.

## Admin privileges for Azure in the CSP program

Some admin privileges are granted automatically when you establish a reseller relationship with a customer. Others must be granted to you by a customer.

There are two levels of admin privileges for Azure in CSP:

- **Tenant-level admin privileges** (that is, *delegated admin privileges*) give you access to your customers' tenants. This delegated access allows you to perform administrative functions, such as adding and managing users, resetting passwords, and managing user licenses.

   You get tenant-level admin privileges when you establish CSP reseller relationships with customers.
- **Subscription-level admin privileges** give you complete access to your customers' Azure CSP subscriptions. This access allows you to provision and manage their Azure resources.

   You get subscription-level admin privileges when creating Azure CSP subscriptions for your customers.

## Reinstate your CSP admin privileges: your actions

You and your customer each have actions to perform to reinstate your CSP admin privileges. This section describes the actions for *you* to take.

To reinstate your CSP admin privileges, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. On the **Customer List**, select **Request a reseller relationship**.

3. For the **Delegated Admin Privileges** check box:
   - Leave the check box selected to establish the relationship *with* delegated administrator privileges.
   - Clear the check box to establish the relationship *without* delegated administrator privileges.

   :::image type="content" source="media/reinstate-csp/create-relationship-request.png" alt-text="Screenshot from the 'Create a relationship request' page in Partner Center.":::

4. Review the draft email invitation.

   - Select **Open in email** to open the draft invitation in your default email application.
   - Select **Copy to clipboard** to copy and paste the invitation into an email message.

    > [!IMPORTANT]
    >You can edit the text in the draft email message, but *be sure to include the personalized link* because it links the customer directly to your account.

5. Select **Done**.

6. Send the email invitation to your customer.

    > [!NOTE]
    >To be able to accept the request, the person in your customer's organization must be a *Global admin* of your customer's tenant.

   - Your customer selects the link they received in the email. The link takes them to *Microsoft Admin Center* where they can accept your invitation.

   - After the customer accepts your invitation, they'll appear on your **Customers** page in Partner Center, and you'll be able to provision and manage the service for the customer from there.

7. After your customer approves the reseller relationship invitation using the link provided, connect to the partner tenant to get the `object ID` of the AdminAgents group.

   ```powershell
   Connect-AzAccount -Tenant "Partner tenant"
   # Get Object ID of AdminAgents group
   Get-AzADGroup -DisplayName AdminAgents
   ```

8. Ensure that your customer has:

   - The role of **owner** or **user access administrator**
   - Permissions to create role assignments at the subscription level

## Reinstate your CSP admin privileges: customer actions

This section describes the *customer's* actions to reinstate your CSP admin privileges.

To complete reinstating your CSP admin privileges, your customer uses PowerShell or the Azure CLI to perform the following steps:

1. Your customer uses PowerShell to update the `Az.Resources` module.

    ```powershell
    Update-Module Az.Resources
    ```

2. Your customer connects to the tenant in which the CSP subscription exists.

   ```powershell
   Connect-AzAccount -TenantID "<Customer tenant>"
   ```

   ```azurecli
   az login --tenant <Customer tenant>
   ```

3. Your customer connects to the subscription.

   This step is applicable *only* if the user has role assignment permissions over multiple subscriptions in the tenant.

   ```powershell
   Set-AzContext -SubscriptionID "<CSP Subscription ID>"
   ```

   ```azurecli
   az account set --subscription <CSP Subscription ID>
   ```

4. Your customer creates the role assignment.

   ```powershell
   New-AzRoleAssignment -ObjectID "<Object ID of the AdminAgents group from step 7 of your actions section>" -RoleDefinitionName "Owner" -Scope "/subscriptions/<CSP subscription ID>" -ObjectType "ForeignGroup"
   ```

   ```azurecli
   az role assignment create --role "Owner" --assignee-object-id <Object ID of the AdminAgents group from step 4> --scope "/subscriptions/<CSP Subscription Id>" --assignee-principal-type "ForeignGroup"
   ```

Instead of granting owner permissions at the *subscription* level, they can be granted at the *resource group* or *resource* level:

- At the **resource group** level

   ```powershell
   New-AzRoleAssignment -ObjectID "<Object ID of the AdminAgents group from step 4>" -RoleDefinitionName Owner -Scope "/subscriptions/<SubscriptionID of CSP subscription>/resourceGroups/<Resource group name>" -ObjectType "ForeignGroup"
   ```

   ```azurecli
   az role assignment create --role "Owner" --assignee-object-id <Object ID of the AdminAgents group from step 4> --scope "/subscriptions/<CSP Subscription Id>/resourceGroups/<Resource group name>" --assignee-principal-type "ForeignGroup"
   ```

- At the **resource** level

   ```powershell
   New-AzRoleAssignment -ObjectID "<Object ID of the AdminAgents group from step 4>" -RoleDefinitionName Owner -Scope "<Resource URI>" -ObjectType "ForeignGroup"
   ```

   ```azurecli
   az role assignment create --role "Owner" --assignee-object-id <Object ID of the AdminAgents group from step 4> --scope "<Resource URI>" --assignee-principal-type "ForeignGroup"
   ```

### Troubleshooting the customer steps

If your customer is unable to complete the preceding steps, suggest the following command and provide the resulting `newRoleAssignment.log` file to Microsoft for further analysis:

```powershell
New-AzRoleAssignment -ObjectId <principal ID> -RoleDefinitionName "Owner" -Scope "/subscriptions/<customer subscription>" -ObjectType "ForeignGroup" -Debug > newRoleAssignment.log
```

## Reinstate your CSP admin privileges: PowerShell catchall procedure

If the steps in the preceding sections don't work, or if you get errors when attempting them, try the following "catchall" procedure to reinstate admin rights for your customer:

```powershell
Install-Module -Name Az.Resources -Force -Verbose
Import-Module -Name Az.Resources -Verbose -MinimumVersion 4.1.1
Connect-AzAccount -Tenant <customer tenant>
Set-AzContext -SubscriptionId <customer subscriptions>
New-AzRoleAssignment -ObjectId <principal ID> -RoleDefinitionName "Owner" -Scope "/subscriptions/<customer subscription>" -ObjectType "ForeignGroup"
```

If the "catchall" procedure fails at `Import-Module`, try the following steps:

- If the import fails because the module is in use, restart the PowerShell session by closing and reopening all windows.
- Check the version of `Az.Resources` with `Get-Module Az.Resources -ListAvailable`.
  - If version 4.1.1 isn't in the available list, you must use `Update-Module Az.Resources -Force`.
- If an error states that `Az.Accounts` must be a specific version, update that module as well, replacing `Az.Resources` with `Az.Accounts`. You must then restart the PowerShell session.

## Next steps

- [Manage subscriptions and resources under the Azure plan](azure-plan-manage.md)
