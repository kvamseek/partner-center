---
title: GDAP bulk migration tool FAQ
ms.topic: article
ms.date: 5/24/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: GDAP bulk migration tool FAQ.
author: kvamseek
ms.author: vamseekk
---

# GDAP bulk migration tool FAQ

**Appropriate roles**: Global admin | User management admin | Admin agent | Sales agent

[!INCLUDE [Important - Azure AD Graph is deprecated](./developer/includes/azure-ad-graph-notice.md)]

## Where can I find another source that describes the latest known issues and their status?

See [GitHub - PartnerCenter-GDAPTransition · GitHub Issues](https://github.com/microsoft/PartnerCenter-GDAPTransition/issues)

## Who can perform the operations in the partner organization?

The write operations can be performed by AdminAgents.

## What is the consent that is requested when authenticating for the first time?

There are two one-time consents to be provided by the Global Admin of the partner tenant in order to allow the GDAP bulk migration tool client app to be able to request access tokens to perform a set of operations.

In both the cases, check "Consent on behalf of your organization".

- Consent for permissions for partner center APIs

   :::image type="content" source="media/gdap/consent-1.png" alt-text="Screenshot of consent form for APIs.":::

- To be able to read security groups from the partner's tenant using Graph API

   :::image type="content" source="media/gdap/consent-2.png" alt-text="Screenshot of consent form for Graph.":::

## Will partners be required to provide the name of the relationship for each of the customers?

Yes, partners need to provide a unique name for each relationship with the customers who are going to be part of the list. The maximum length is 50 characters, and it must be unique for that partner otherwise the relationship won't be created.

## For relationship creation and security group-role assignment operations, how much time do I have to wait before they get activated?

Typically, it may take up to five minutes before getting updated from 'Approved' to 'Active' for creating relationships and assignment operations.

## Where can I see the complete list of roles that can be set up in a GDAP relationship?

You can refer to [permissions reference](/azure/active-directory/roles/permissions-reference) for a complete list of role templates that can be used in the setup file `ADRoles.csv` during relationship creation and security group assignments.

## How can I get more details about errors before contacting for support?

If you need to contact support for anything related to the tool, send the log file found at `GBM\Logs`.

## Why are the security group-role assignments failing and the error log shows bad request?

Either the role configured in the GDAP relationship isn't an active role in the customer tenant or the roles specified in the `securitygroups.csv` mappings aren't part of the GDAP relationship request because they weren't configured in the `ADRoles.csv` file.

## What is the data that is shown in the audit logs when the tool runs?

Along with existing attributes of the partner user, there's a new attribute introduced 'ApprovedBy' in 'Granular Admin Relationship Approved' whose value will be 'Partner' for partner-led approval. For regular customer approval, the value is 'Customer'.

## What is the maximum number of relationships this tool can support for upgrade?

The tool has been tested with up to 1,000 relationships at a time. It has also been tested with about 4,000 security group assignment requests. After completing the assignments, the background process will take a few minutes to refresh from Approved to Active.

## I made an incorrect GDAP role assignment by mistake. Can I update my GDAP relationships?

The tool doesn't support updating GDAP role assignments. To update the assignments, you need to go to the [**Microsoft Partner Center** > **Customers** > **Administer**](https://partner.microsoft.com/commerce/granularadminaccess/list), find the customer, terminate the incorrect relationships and then run the tool again with updated role assignments.

## Can I remove a DAP relationship after I'm done upgrading all of my relationships to GDAP?

Yes, you may go ahead and retire the DAP relationship.

## I don't want my relationships to expire in the next three years. Can I provide expiration up to three years as an exception?

Currently, the GDAP relationship tenure is set at a maximum up to 730 days (two years). It can't be extended beyond this period.

## What is the recommended next step if the conditional access policy set by the customer blocks all external access including CSPs access (AOBO) to the customer's tenant?

Customers can now exclude CSPs from conditional access policy so that partners can run no consent GDAP bulk migration tool to transition to GDAP without getting blocked.

**Include users**

This list of users typically includes all of the users an organization is targeting in a Conditional Access policy.

The following options are available to include when creating a Conditional Access policy:

- Select users and groups
  - Guest or external users (preview)
    - This selection provides several choices that can be used to target Conditional Access policies to specific guest or external user types and specific tenants containing those types of users. There are several different types of guest or external users that can be selected, and multiple selections can be made:
      - Service provider users, for example a Cloud Solution Provider (CSP)
    - One or more tenants can be specified for the selected user type(s), or you can specify all tenants.

**External partner access**

Conditional Access policies that target external users may interfere with service provider access, for example granular delegated admin privileges. For more information, see [Introduction to granular delegated admin privileges (GDAP)](gdap-introduction.md). For policies that are intended to target service provider tenants, use the **Service provider user** external user type available in the **Guest or external users** selection options.

:::image type="content" source="media/gdap/conditional-access-policy-1.png" alt-text="Screenshot of CA policy UX targeting guest and external user types from specific Azure AD organizations.":::

**Exclude users**

When organizations both include and exclude a user or group, the user or group is excluded from the policy, as an exclude action overrides an include in policy.

The following options are available to exclude when creating a Conditional Access policy:

- Guest or external users
  - This selection provides several choices that can be used to target Conditional Access policies to specific guest or external user types and specific tenants containing those types of users. There are [several different types of guest or external users that can be selected](/azure/active-directory/external-identities/authentication-conditional-access#conditional-access-for-external-users), and multiple selections can be made:
    - Service provider users, for example a Cloud Solution Provider (CSP)
  - One or more tenants can be specified for the selected user type(s), or you can specify all tenants.

:::image type="content" source="media/gdap/conditional-access-policy-2.png" alt-text="Screenshot of CA policy.":::

For more information, see the following:

- [Graph API Experience: Beta API with the new external user type information](/graph/api/resources/conditionalaccessguestsorexternalusers)
- [Conditional access policy](/azure/active-directory/conditional-access/concept-conditional-access-users-groups)
- [Conditional access external users](/azure/active-directory/external-identities/authentication-conditional-access#assigning-conditional-access-policies-to-external-user-types-preview)

## Will running the GDAP Bulk migration tool cause a new Service Principal to be added on the customer's tenant?

Yes, "**Partner Customer Delegated Admin Offline Processor**" creation is necessary for the GDAP access assignment to go through in the GDAP workflow. This creation occurs after the acceptance of the GDAP Relationship goes into the "approved" state. This offline processor is created while using the bulk migration tool and during the normal GDAP flow where the service principal access assignment gets mapped between partner security group and customer roles. For more details, see [Verify first-party Microsoft applications in sign-in reports](/troubleshoot/azure/active-directory/verify-first-party-apps-sign-in).

## How do I open a UTF-8 CSV file in Excel without misconversion of characters in Japanese and Chinese language for both Mac and Windows?

To open a UTF-8 CSV file in Excel on Windows without misconversion of Japanese or Chinese characters, use the following steps:

1. Open Excel, search "Get Data From Text" to open a wizard when you want to open a CSV file.
2. Go to the location of the CSV file, that you want to import.
3. Choose Delimited, set the character encoding to 65001: Unicode (UTF-8) from the dropdown list.
4. Check that My data has headers. You have to use it because the first row of CSV file has column names.
5. Select next to display the second step of Text Import Wizard.
6. Because our data is separated by commas, set the delimiter to a comma.
7. Select next to move to the third step.
8. Select the General column and then Finish.
9. Keep the default values inside the Import Data window and select OK.

To open a UTF-8 CSV file in Excel on a Mac without misconversion of Japanese or Chinese characters, refer to the article [Import data from a CSV, HTML, or text file](https://support.microsoft.com/office/import-data-from-a-csv-html-or-text-file-b62efe49-4d5b-4429-b788-e1211b5e90f6).

## Troubleshooting guidance

### Why am I shown 900309: Access has been blocked by Conditional Access Policy, when accessing a customer's tenant?

Partners accessing a customer's tenant with Conditional Access Policy enabled are presented with the following:
`Status Code: 403`
`Code: 900309`
`Message: Access has been blocked by Conditional Access policies. The access policy does not allow token issuance.`

- Learn more at [What is the recommended next step?](#what-is-the-recommended-next-step-if-the-conditional-access-policy-set-by-the-customer-blocks-all-external-access-including-csps-access-aobo-to-the-customers-tenant).

- Also see [Azure conditional access policy](/azure/active-directory/conditional-access/concept-conditional-access-users-groups).

## Why are existing partner tokens no longer working for license management calls and I get a message 900316: Partner token isn't allowed in license management calls?

With the Azure AD Graph licensing API deprecated, when a Partner uses a legacy partner token, we can't generate the MS Graph exchange token.
`Status Code: 400`
`Code: 900316`
`Message: Partner token is not allowed in license management calls. Please call with Partner Access Token`

- Learn more at [Enable application model](/partner-center/developer/enable-secure-app-model#get-access-token).

## The process can't access the file 'C:\Users\masidd\Desktop\DemoJul11\GBM\GDAPBulkMigration\operations\customers.csv' because it's being used by another process.

During any operation if the process is reading or writing to a specific file, and the file is open, you see this error. Close the csv/json file and retry the operation.

## GDAP relationship name already exits.

This error means that the relationship name specified for that customer in `GBM\GDAPBulkMigration\operations\customers.csv` already exists for either the given customer or another customer's relationship. This error means that the name isn't globally unique. You must retry with a new name after the current operation is completed for other customer relationships.

## Access assignment already exists.

This error can be displayed when executing the option to "Create Security Group-Role Assignment(s)" if a security group has already been added to the GDAP relationship with a given set of roles.

## Please make sure your sign-in credentials are MFA enabled.

The error message means that the logged in user doesn't have MFA (Azure multifactor authentication) enabled. It's necessary to enable this because all GDAP APIs enforce MFA.

## Please check input setup for customers and ADRoles.

This error message means that one or more inputs in the input files under the 'operations' folders (`ADRoles.csv` or `securitygroups.csv`) haven't been configured properly.

It can also occur if the Azure AD role configured in the relationship isn't activated in the customer tenant.

## Failed to create. The customer doesn't exist, or DAP relationship is missing.

This error message means that the customer isn't mapped to the partner or the DAP relationship is missing or has been removed.

## GDAP relationship is already created but User doesn't have permissions to approve a relationship.

The GDAP relationship already exists but there are no active relationships and the partner user hasn't been assigned to a role that can approve the relationship for the customer.

## Proxy Server: Your organization has a proxy server, which prevents internet access without authorization.

The build might fail due to failure accessing the NuGet server. Update the `nuget.config` file as follows:

1. Identify the proxy server setting for their organization and update the `nuget.config` under working folder with the following.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
      <packageSources>
            <clear />
            <add key="nuget" value="https://api.nuget.org/v3/index.json" />
      </packageSources>
      <config>
      <add key="http_proxy" value="http://YOUR_PROXY URL " />
      </config>
      <activePackageSource>
            <add key="All" value="(Aggregate source)" />
      </activePackageSource>
</configuration>
```

2. If the GDAP API access is blocked by the proxy server add the following line to `GBM/AppSettings.cs`:

```csharp
HttpClient.DefaultProxy = new WebProxy("your proxy server url", true, null, System.Net.CredentialCache.DefaultNetworkCredentials);
```

:::image type="content" source="media/gdap/code-proxy-setting.png" alt-text="Screenshot of app console proxy settings.":::

## Next steps

- [Upgrade DAP relations to GDAP in bulk (no consent required)](gdap-bulk-migration-tool.md)


