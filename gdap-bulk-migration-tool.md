---
title: GDAP bulk migration tool
ms.topic: how-to
ms.date: 5/24/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Get an overview and instructions on using the bulk migration tool for granular delegated admin privileges (GDAP).
author: kvamseek
ms.author: vamseekk
---

# GDAP bulk migration tool

**Appropriate roles**: Global admin | User management admin | Admin agent | Sales agent

The tool for bulk migration of delegated admin privileges (DAP) to granular delegated admin privileges (GDAP) enables partners to create new GDAP relationships with implied customer consent. Implied customer consent means there's a pre-existing, active (accessed) or inactive (not accessed in the last 90 days) DAP relationship between the Cloud Solution Provider (CSP) and a customer.

The bulk migration tool has the following features:

- It's an open-source .NET console tool that uses an open-source .NET SDK.
- It supports comma-separated (.csv) and JSON (.json) file formats for setting up data for migration.
- No code changes are required, and it can be opened with a .NET command.
- Code is extensible and can be enhanced if partners need it to be.
- Extensive logging can help troubleshoot issues.

This tool is for direct bill partners, indirect providers, and indirect resellers transacting through the CSP program.

## Prerequisites

- Automatic approval of a GDAP relationship works only if there's an active or inactive DAP between the partner and the customer.
- Partner accounts must be enabled for multifactor authentication (MFA) because all GDAP APIs now enforce MFA. You can add MFA by following the instructions in [Mandating MFA for your partner tenant](partner-security-requirements-mandating-mfa.md).
- To build and run the GDAP bulk migration tool, you must have the [.NET 6.0 SDK](https://dotnet.microsoft.com/download/dotnet/6.0) installed on the host machine.
- Download the [GDAP bulk migration tool source](https://github.com/microsoft/PartnerCenter-GDAPTransition) from GitHub. Extract the files into a local working folder. After you finish, you should have a folder named *.\PartnerCenter-GDAPTransition-main\GBM*.

   :::image type="content" source="media/gdap/bulk-migration-tool.png" alt-text="Screenshot of the button for downloading the GDAP bulk migration tool.":::

- The partner tenant should have onboarded the GDAP enterprise app ID that represents the resource `https://api.partnercustomeradministration.microsoft.com`. This process is documented in [List delegated admin customers](/partner-center/develop/list-delegated-admin-customers) (the first two steps) and in [Bulk migration tool FAQ](gdap-bulk-migration-tool-faq.md).
- The partner tenant admin must provide consent on behalf of the organization for the tool to be able to call GDAP APIs and perform operations.
- The GDAP app service principal is required. The GDAP bulk migration tool attempts to add this principal on your behalf. If you see the error in the following image, the current user doesn't have Global Administrator privileges, which are required for adding the GDAP app service principal. After the GDAP app service principal is added, any user in the AdminAgents security group can run the tool.

   :::image type="content" source="media/gdap/prerequisites-app-service.png" alt-text="Screenshot of a dialog that says a user needs admin approval.":::

   Selecting **Return to the application without granting consent** generates the following error in the tool.

   :::image type="content" source="media/gdap/prerequisites-console.png" alt-text="Screenshot of a console with a prerequisite error." lightbox="media/gdap/prerequisites-console.png":::

- Ensure that the relationship names for creating GDAPs are unique. The relationship name is unique for every partner tenant, but the customer tenant could have the same relationship names from different partners.

  | Customer  | Partner  | GDAP relationship name |
  |-----------|----------|------------------------|
  | C1        | P1       | R1                     |
  | C1        | P2       | R1                     |

## Starting the GDAP bulk migration tool

To run the tool, open a command prompt, change the directory into the folder *./GBM*, and enter `dotnet run`. After the build (if necessary) finishes, you're prompted to select the file format that you prefer the tool to use during downloads and execution: JSON or CSV. Enter the number that corresponds to your choice.

:::image type="content" source="media/gdap/console-file.png" alt-text="Screenshot of a console with file options.":::

After you select your preferred file format, the main menu appears.

:::image type="content" source="media/gdap/console-menu.png" alt-text="Screenshot of a console with a menu of operations.":::

The following sections provide an overview of the operations on the menu.

### Download operations

- `Download eligible customers list`: This operation retrieves all the customers who have an active or inactive DAP account. You must modify this file before running operation 7, `Create GDAP Relationship(s)`.
- `Download eligible customers for very large list (compressed format)`: Like the preceding operation, this one is saved in a GZIP file format. This operation is suitable for any CSP that has 300 customers or more.
- `Download Example Azure AD Roles`: This operation creates an example file named *ADRoles* (.csv or .json) that you can use when you're creating the GDAP relationship. Modify this file and include only the roles that should be assigned to the GDAP relationship. You'll use this modified file when you're running operation 7, `Create GDAP Relationship(s)`, and operation 9, `Create Security Group-Role Assignment(s)`.
- `Download Partner Tenant's Security Group(s)`: This operation retrieves all the current Azure Active Directory (Azure AD) security groups. Modify this file to include only the security groups that will be associated with the GDAP relationships. You'll use this modified file when you're running operation 9, `Create Security Group-Role Assignments`.
  
  Users must be added to security groups separately, which is not in the scope of this tool.
- `Download existing GDAP relationship(s)`: This operation retrieves all the current GDAP relationships, along with their statuses. Review this file to understand any anomalies that might be present and to help in troubleshooting errors. (This download operation isn't required.)

### GDAP relationship operations

- `One flow generation`: This operation executes operation 7, `Create GDAP Relationship(s)`, followed by operation 9, `Create Security Group-Role Assignment(s)`.
- `Create GDAP Relationship(s)`: This operation uses the modified customer list and the Azure roles file that you downloaded by using operation 1 (`Download eligible customers list`) and operation 3 (`Download Example Azure AD Roles`) to create the GDAP relationship.
- `Refresh GDAP Relationship status`: The creation of the GDAP relationships isn't synchronous, so the tool might return before all the back-end processing is completed. Periodically running the tool updates the status of the GDAP relationships. Don't proceed until all status codes have been updated to an `Active` status.

### Operations for provisioning security groups

- `Create Security Group-Role Assignment(s)`: You must associate one or more security groups with one or more roles in the customer tenant that you specified in the GDAP relationship created for customers in operation 7, `Create GDAP Relationship(s)`. You can add users to the security groups beforehand or add them later to grant access to the customers' environment for administration, which is outside the scope of this tool.
- `Refresh Security Group-Role Assignment status`: The assignment of the security groups isn't synchronous, so the tool might return before all the back-end processing is completed. Periodically running the tool updates the status of the bulk migration session.

### Update and delete operations

- `Update Security Group-Role Assignment(s)`: You can update the security group assignment done in operation 9, `Create Security Group-Role Assignment(s)`, by updating the file *accessAssignment_update* generated in the folder *GDAPBulkMigration\\operations\\accessAssignment*. The specific task is to change `RoleDefinitionIds` from the column `CommaSeparatedRoles`.

  The only roles that you can update are those that you originally configured in the corresponding GDAP relationship (via *securityGroup.csv* and *ADRoles.csv*).

  You can refresh the status of the security group updates by using operation 10, `Refresh Security Group-Role Assignment status`.

- `Delete Security Group-Role Assignment(s)`: You can completely remove a role access assignment for a security group by copying the records from *accessAssignment.csv* or *accessAssignment_update.csv* to *accessAssignment_delete.csv*.

  :::image type="content" source="./media/gdap/access-delete.png" alt-text="Screenshot that shows the CSV files for deleting and updating a role assignment." lightbox="./media/gdap/access-delete.png":::

  You can refresh the status of deleting role access for a security group by using operation 10, `Refresh Security Group-Role Assignment status`.

- `Terminate GDAP Relationship(s)`: You can use the tool for the termination of GDAP relations that are in the `Active` state. Copy GDAP records that you want to delete from *gdapRelationship.csv* to *gdapRelationship_terminate.csv*. This file is created in the same folder (*GDAPBulkMigration\\operations\\gdapRelationship*) and is empty by default.

  The step of copying GDAP records from *gdapRelationship.csv* to the *gdapRelationship_terminate.csv* file must be done manually. The operation to terminate active GDAP relationships invokes a back-end GDAP API request for termination. Termination finishes as soon as the offline processor chooses it for processing.

  You can refresh the status of the GDAP role deletion by using operation 8, `Refresh GDAP Relationship status`. Running operation 8 refreshes all records under the `TerminationRequested` state to `Terminated` as soon as the offline processor processes them.

  :::image type="content" source="./media/gdap/failed-terminate.png" alt-text="Screenshot that shows the CSV files for terminating a GDAP relationship and refreshing status." lightbox="./media/gdap/failed-terminate.png":::

- `DAP Termination(s)`: As part of the ongoing work item to migrate DAP to GDAP, you can use the GDAP bulk migration tool for termination of active and inactive DAP relationships with a customer. You can use the functionality to delete multiple DAP relations in a single batch, which also presents the status of the operation.

  You can copy customer records that you want to remove from *customer.csv* in the *GDAPBulkMigration\\download* folder by using operation 1, `Download eligible customers list`. Then, you can put them in the automatically generated input file *customer_dap_terminate.csv* under *GDAPBulkMigration\\operations*. This process is like the GDAP creation process. The only difference is that you're selecting a customer for DAP termination.

## Bulk migration session

The process steps for migrating customer DAP accounts to GDAP accounts must be in the following order for each batch of customers that you're migrating.

For example, if you have a total of 1,000 customers and a batch size of 300 customers per migration, you can divide your customers into three batches of 300, followed by one batch of 100. For each batch of customers, you execute the first scenario, [creating GDAP relationships](#first-scenario-create-gdap-relationships). You then execute the second scenario, [provisioning security groups](#second-scenario-provision-security-groups).

## Preparation

The `Download operations` section in the GDAP bulk migration tool helps enable and accelerate the migration. All downloaded files are placed in *./GBM/GDAPBulkMigration/downloads*.

:::image type="content" source="media/gdap/downloads-file-explorer.png" alt-text="Screenshot of the folder for downloads in File Explorer." lightbox="media/gdap/downloads-file-explorer.png":::

The following files contain all records for each respective grouping: *ADRoles.csv*, *customers.csv*, and *securityGroup.csv*. You can use them as data sources when you're creating similar files for the migration.

The GDAP bulk migration tool sources its data from *./GBM/GDAPBulkMigration/operations* for each bulk migration session.

:::image type="content" source="media/gdap/file-explorer-operations.png" alt-text="Screenshot of the folder for operations in File Explorer." lightbox="media/gdap/file-explorer-operations.png":::

In the example batch size of 300 customers per session, you would need to create four *customer.csv* files: three with 300 customers, and a final file of 100 customers. You would update the *customer.csv* file in the *operations* folder four times for each session.

> [!IMPORTANT]
> The *ADRoles.csv* and *securityGroup.csv* files should be edited versions of the files that you previously downloaded. They should contain the specific Azure AD roles and security groups that suit your requirements.  In most cases, you edit these files once and leave them as is in the *operations* folder. For more complex scenarios, you might also need to update these files per session.

## Authentication

The first time you execute one of the tool's operations, a browser window asks you to provide the sign-in credentials that you use when signing in to Partner Center. Check the [FAQ](gdap-bulk-migration-tool-faq.md) for the one-time consent that your tenant admin needs to provide.

After successful authentication, the following message appears. Close the browser window and return to the console application.

:::image type="content" source="media/gdap/successful-authentication.png" alt-text="Screenshot of a message about successful authentication.":::

## First scenario: Create GDAP relationships

The process of creating new GDAP relationships requires two input files that must be in a subdirectory named *./GBM/GDAPBulkMigration/operations*.

The *customers* (.csv or .json) file contains the list of customers that will have a new GDAP relationship. This file consists of the following columns:

- `Name`: The unique name, per partner tenant, for the newly created GDAP relationship. Each name has a maximum length of 50 characters and allows alphanumeric characters, dashes, and underscores.
- `PartnerTenantId`: The tenant ID for the customer tenants that will be associated with the newly created GDAP account.
- `CustomerTenantId`: The associated customer tenant.
- `OrganizationDisplayName`: The customer's organization name.
- `Duration`: The number of days (1 to 730) that the GDAP relationship will remain valid.

The following example shows a list of customers in *customers.csv*. The highlighted columns aren't populated during the corresponding operation for downloading a customer list. You must provide them before you run the tool. Or you must provide them as preconfigured default values before downloading.

:::image type="content" source="media/gdap/customers-csv.png" alt-text="Screenshot of a CSV file that contains a list of customers.":::

The *ADRoles* (.csv or .json) file lists the Azure AD roles that will be assigned to the GDAP relationship. This file consists of the following columns:

- `Id`: The unique identifier for the specific Azure AD role you're adding.
- `Name`: The name of the Azure AD role.
- `Description`: A description of the Azure AD role.

The following example shows a list of Azure AD roles in *ADRoles.csv*.

:::image type="content" source="media/gdap/adroles-csv.png" alt-text="Screenshot of a CSV file that contains Azure AD roles.":::

For more information, see [GDAP role guidance](gdap-least-privileged-roles-by-task.md) and [Azure AD built-in roles](/azure/active-directory/roles/permissions-reference).

To create a GDAP relationship:

1. Validate that you properly prepared the *customer.csv* and *ADRoles.csv* files, as described earlier in the [Preparation](#preparation) section.
1. Run operation 7, `Create GDAP Relationship(s)`, by selecting the 7 key and then selecting the Enter key. Answer the confirmation by selecting the Y key.

   :::image type="content" source="media/gdap/console-option-seven.png" alt-text="Screenshot of console operation seven." lightbox="media/gdap/console-option-seven.png":::

1. The output of the GDAP relationships is available in the file *.\GBM\GDAPBulkMigration\operations\gdapRelationship\gdapRelationship.csv*.

   :::image type="content" source="media/gdap/gdap-relationship-csv.png" alt-text="Screenshot of the CSV file that lists GDAP relationships.":::

   The status of the created GDAP relationships starts as `Approved`. Before you continue with the operations for provisioning security groups, you must validate that the status has changed to `Active` for all the GDAP relationships that you created. A server-side process updates the status.

   Update the `gdapRelationship.csv` file by periodically running operation 8, `Refresh GDAP Relationship status`.

You might get an error for GDAP relationships that don't have an `Active` status. You can choose to filter out GDAP relationships that have failed by removing them from the *customers.csv* file, so that only relationships with a status of `Active` are present. You're now ready to move on to operations for provisioning security groups.

Be sure to save any relationships that produced errors for further investigation.

## Second scenario: Provision security groups

1. Identify or create the Azure AD security groups that you plan to associate with the GDAP relationships. A security group is required and is how you grant your employees access to administer your customers' environments.

   The *securityGroup* (.csv or .json) file contains the security groups and roles that you want to assign and associate with the GDAP relationships that you created and activated in the [first scenario](#first-scenario-create-gdap-relationships). This file consists of the following columns:

   - `Id`: The unique ID that's assigned to your security group.
   - `DisplayName`: The friendly name of the security group.
   - `CommaSeparatedRoles`: A list that must contain one or more of the Azure AD role IDs (separated by commas) that you defined in the `ADRoles.csv` file and assigned to the newly created GDAP relationships.

   > [!TIP]
   > You might need to enclose each `CommaSeparatedRoles` value in quotation marks (`""`).

   The following example shows a list of security groups and roles in  *securityGroup.csv*.

   :::image type="content" source="media/gdap/security-group-csv.png" alt-text="Screenshot of the CSV file that lists security groups and roles.":::

1. Validate that you properly prepared the *customer.csv* and *securityGroup.csv* files, as described earlier in the [Preparation](#preparation) section.

1. Run operation 9, `Create Security Group-Role Assignment(s)`, by selecting the 9 key and then selecting the Enter key. Answer the confirmation by selecting the Y key.

   :::image type="content" source="media/gdap/console-option-nine.png" alt-text="Screenshot of console operation nine." lightbox="media/gdap/console-option-nine.png":::

1. The output and status of the creation of the security group role assignments are available in the file *\GDAPBulkMigration\operations\ accessAssignment\accessAssignment.csv*.

   :::image type="content" source="media/gdap/access-assignment-csv.png" alt-text="Screenshot of the CSV file that lists access assignments." lightbox="media/gdap/access-assignment-csv.png":::

   Confirm that the assignment statuses have a value of `Active`. You can update the *accessAssignment.csv* file by periodically running operation 10, `Refresh Security Group-Role Assignment status`.

   :::image type="content" source="media/gdap/console-option-ten.png" alt-text="Screenshot of console operation 10." lightbox="media/gdap/console-option-ten.png":::

1. Repeat the preceding steps for the remainder of your transitions from DAP to GDAP.

### More file details

The *ExistingGdapRelationship* (.csv or .json) file lists all your GDAP relationships. This file consists of the following columns:

- `Id`: The unique identifier of the GDAP relationship.
- `CustomerDelegatedAdminRelationshipId`: The unique identifier that's linked to the customer. It might be blank if you created a generic GDAP relationship request.
- `DisplayName`: The unique GDAP relationship name that you provide.
- `TenantId`: Your tenant ID.
- `DisplayName`: Your customer's name. In some cases, this column might be blank, which is a known issue. The `TenantId` column should always be populated and represent the customer's tenant ID.
- `TenantId`: Your customer's tenant ID.
- `Duration`: The number of days that this relationship will be active.
- `Status`: The status of the relationship: `ApprovalPending`, `Terminated`, `Approved`, or `Active`.
- `CreatedDateTime`: The time when the relationship request was created.
- `ActivatedDateTime`: The time when the relationship request was accepted or activated.
- `LastModifiedDateTime`: The time when the relationship request was last modified.
- `EndDateTime`: The time when the relationship request will end.
- `VersionStamp`: The version number.

### Failed relationship

During GDAP relationship creation, all failed relationships are captured in a separate file: *gdapRelationship_failed.csv* in the folder
*GBM\\GDAPBulkMigration\\operations\\gdapRelationship*. You can directly share this file with the support team for investigation if the error isn't easily correctable or needs investigation.

:::image type="content" source="./media/gdap/relationship-failed.png" alt-text="Screenshot of the CSV file that lists failed relationships." lightbox="./media/gdap/relationship-failed.png":::

The file consists of the following columns:

- `ErrorDetail`: The specific error that the GDAP API returned.
- `Id`: The unique identifier of the GDAP relationship.
- `CustomerDelegatedAdminRelationshipId`: The unique identifier that's linked to the customer.
- `DisplayName`: The unique GDAP relationship name that you provide.
- `TenantId`: Your tenant ID.
- `DisplayName`: Your customer's name.
- `TenantId`: Your customer's tenant ID.
- `Duration`: The number of days that this relationship will be active.
- `Status`: The status of the relationship, such as `ApprovalPending`, `Terminated`, `Approved`, or `Active`.
- `CreatedDateTime`: The time when the relationship request was created.
- `ActivatedDateTime`: The time when the relationship request was accepted or activated.
- `LastModifiedDateTime`: The time when the relationship request was last modified.
- `EndDateTime`: The time when the relationship request will end.

## Third scenario: Delete a DAP relationship

In your migration journey from DAP to GDAP, one of the key steps is to remove existing DAP relationships to minimize your security vulnerability. You can delete DAP relationships by using the Partner Center portal, but it has a limitation of 50 DAP relationships per page. That's not suitable for a big batch.

You can use the GDAP migration tool to delete DAP relationships in batches. The operation to terminate DAP (operation 14, `DAP Termination(s)`) invokes the Partner Center API to remove DAP for the customers listed in the input file *customer_dap_terminate.csv*.

:::image type="content" source="./media/gdap/file-explorer-dap.png" alt-text="Screenshot of the CSV file for DAP termination in File Explorer.":::

The *customer_dap_terminate* (.csv or .json) file has the following format:

- `PartnerTenantId`: Your tenant ID.
- `OrganizationDisplayName`: Your customer's name. In some cases, this column might be blank, which is a known issue. The next column should always be populated and represent the customer's tenant ID.
- `CustomerTenantId`: Your customer's tenant ID.

> [!NOTE]
> You can download the updated customer list by using operation 1, `Download eligible customers list`, to validate the termination of DAP.

The output of this file is generated as *dap_terminated.csv* under *GDAPBulkMigration\\operations\\dapTermination*.

:::image type="content" source="./media/gdap/customer-dap-terminate.png" alt-text="Screenshot of an output CSV file for DAP termination in File Explorer.":::

The *dap_terminated.csv* file contains details of the operation: `CustomerTenantId`, `OrganizationDisplayName`, and `status`. The `status` column indicates the status of the DAP removal operation as `Success` or `Failed`.

:::image type="content" source="./media/gdap/dap-successful-excel.png" alt-text="Screenshot of an example output file for DAP termination.":::

The DAP removal operation uses a Partner Center administration API. A Global Administrator must provide consent for the tool to be granted permission to invoke the API.

:::image type="content" source="./media/gdap/permissions-modal.png" alt-text="Screenshot of a dialog that asks for Global Administrator consent to allow a permissions request.":::

### Updated settings for AppSettings

During the creation of a GDAP relationship, you can use the GDAP bulk migration tool to configure default values in the *AppSettings.json* file located in the *PartnerCenterAdmin-RelationshipBulkMigrationTool-main\\GBM\\Configuration* folder. You can have default values in the GDAP creation file downloaded via operation 1, `Download eligible customers list`. You can also create backups every time you run the tool.

:::image type="content" source="./media/gdap/app-config.png" alt-text="Screenshot of an app configuration file." lightbox="./media/gdap/app-config.png":::

The file includes these items:

- `ReplaceFileDuringUpdate`: If you run the GDAP bulk migration tool to create GDAP relationships by using operation 7 (`Create GDAP Relationship(s)`) or to create assignments by using operation 9 (`Create Security Group-Role Assignment(s)`) on previous sessions to correct errors, with the `ReplaceFileDuringUpdate` flag turned on, the tool automatically creates a backup folder with a time stamp and moves files of the previous session into this folder. It then creates a new empty file for the new session. This way, the context of the previous session isn't lost and can be revisited for analysis as needed.

  :::image type="content" source="./media/gdap/replace-file.png" alt-text="Screenshot of File Explorer contents for replacing a file during update." lightbox="./media/gdap/replace-file.png":::

- `DefaultGDAPName`: You can specify a default format for GDAP relationship names to be used during relationship creation. The column value is populated every time a customer file is downloaded.

  The format parameter `{0}` is the customer's tenant ID.

- `DefaultGDAPDuration`: You can specify a default duration to be used during relationship creation. The column value is populated every time a customer file is downloaded.

### Curated role recommendations for partner types

As part of the default Azure AD roles provided via operation 3 (`Download Example Azure AD Roles`) in the GDAP bulk migration tool, you can specify the partner type and get a recommended set of roles to map for GDAP relationships.

:::image type="content" source="./media/gdap/partner-selection.png" alt-text="Screenshot of partner selection options." lightbox="./media/gdap/partner-selection.png":::

You can still choose any of the roles from [the standard set of roles](/azure/active-directory/roles/permissions-reference) and populate *ADRoles.csv* and create the relationships. The preceding feature is just a recommended set of roles.

## Next steps

- [GDAP migration tool FAQ](gdap-bulk-migration-tool-faq.md)


