---
title: Microsoft-led transition from DAP to GDAP
ms.topic: article
ms.date: 07/17/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Microsoft-led transition from delegated administrative privileges (DAP) to Granular delegated administrative privileges (GDAP) 
author: kvamseek
ms.author: vamseekk
---

# Microsoft-led transition from DAP to GDAP

**Appropriate roles**: All users interested in Partner Center

Microsoft is assisting Jumpstart partners who haven't already begun transitioning from delegated access protocols (DAP) to granular delegated access protocols (GDAP). This assistance helps partners reduce security risks by moving towards accounts that use security best practices including using time-limited, minimum-rights security contracts.

## How the Microsoft-led transition works  

1. Microsoft automatically creates a GDAP relationship with eight default roles.
1. Roles are automatically assigned to predefined Cloud Solution Provider (CSP) security groups.
1. After 30 days, DAP is removed.

## Schedule

Microsoft began the DAP to GDAP transition on May 22, 2023. There's a blackout period in June. The transition will resume after July.  

## Who qualifies for Microsoft-led transition?

This table shows a high-level summary:

|DAP Enabled|GDAP Relationship Exists|GDAP Relationship in “Pending approval” state |GDAP Relationship Terminated/Expired| Microsoft-led transition Eligibility|
|-----------|------------------------|----------------------------------------------|------------------|--------------------|
|Yes  |No   |N/A  |N/A  |Yes  |
|Yes  |Yes  |No   |No   |No   |
|Yes  |Yes  |Yes  |No   |No†  |
|Yes  |Yes  |No   |Yes  |No†  |
|No   |Yes  |No   |No   |No†  |
|No   |No   |No   |Yes  |No   |

If you have already created a GDAP relationship, then Microsoft won't create a GDAP relationship as part of the Microsoft-led transition. Instead, the DAP relationship will be removed in July 2023.

You may qualify to be part of the Microsoft-led transition in any of the following scenarios:

- You’ve created a GDAP relationship, and the relationship is in a **Pending approval** state. This relationship will be cleaned out after three months.
- † You may qualify if you’ve created a GDAP relationship, but the GDAP relationship has expired. This depends on how long the relationship has been expired:
  - If the relationship was expired less than 365 days ago, then a new GDAP relationship won't be created.
  - If the relationship was expired more than 365 days ago, then the relationship is removed.
  
## Will there be a disruption to customers after the Microsoft-led transition?

Partners and their business are unique. Once the GDAP relationship is created through the Microsoft-led transition tool, GDAP takes precedence over DAP.

Microsoft recommends that partners test and create new relationships with the required roles that are missing in the Microsoft-led transition tool. Create GDAP Relationship with roles based on your use cases and business requirements in order to ensure smooth transition from DAP to GDAP.

## What Azure AD roles does Microsoft assign when a GDAP relationship is created using the Microsoft-led transition tool?  

- **Directory readers**: Can read basic directory information. Commonly used to grant directory read access to applications and guests.
- **Directory writers**: Can read and write basic directory information. Commonly used to grant access to applications. This role isn't intended for users.
- **Global Reader**: Can read everything that a Global Administrator can, but not update anything.
- **License administrator**: Can manage product licenses on users and groups.
- **Service support administrator**: Can read service health information and manage support tickets.
- **User administrator**: Can manage all aspects of users and groups, including resetting passwords for limited admins.
- **Privileged role administrator**: Can manage role assignments in Azure AD and all aspects of Privileged Identity Management (PIM).
- **Helpdesk administrator**: Can reset passwords for nonadministrators and helpdesk administrators.
- **Privileged authentication administrator**: Can access, view, set, and reset authentication method information for any user (admin or nonadmin).

## Which Azure AD Roles are automatically assigned to which predefined CSP security groups as part of Microsoft-led transition?  

**Admin Agents Security Group:**  

- **Directory readers**: Can read basic directory information. Commonly used to grant directory read access to applications and guests.
- **Directory writers**: Can read and write basic directory information; for granting access to applications, not intended for users.
- **Global Reader**: Can read everything that a Global Administrator can, but not update anything.
- **License administrator**: Can manage product licenses on users and groups.
- **User administrator**: Can manage all aspects of users and groups, including resetting passwords for limited admins.
- **Privileged role administrator**: Can manage role assignments in Azure AD and all aspects of Privileged Identity Management (PIM).
- **Privileged authentication administrator**: Can access, view, set, and reset authentication method information for any user (admin or nonadmin).
- **Service support administrator**: Can read service health information and manage support tickets.
- **Helpdesk administrator**: Can reset passwords for nonadministrators and Helpdesk administrators.

**Helpdesk Agents Security Group**:  

- **Service support administrator**: Can read service health information and manage support tickets.
- **Helpdesk administrator**: Can reset passwords for nonadministrators and helpdesk administrators.

## How long is the new GDAP Relationship?

The GDAP relationship created during Microsoft-led transition is for one year.

## Will customers know when Microsoft creates the new GDAP relationship as part of DAP to GDAP transition or remove DAP?  

No. All emails that would normally go to customers as part of the GDAP transition are suppressed.

## How will I know when Microsoft creates a new relationship as part of DAP to GDAP transition?  

Partners won't receive notifications when the new GDAP relationship is created during the Microsoft-led transition. We've suppressed these types of notifications during the transition, because sending an email for each change could create a huge volume of email. You can check the audit logs to see when the new GDAP relationship is created.

## Opt out of the Microsoft-led transition

To opt out of this transition, you can either create a GDAP relationship, or remove your existing DAP relationships.

## Can I use the bulk tool to create GDAP relationships after the Microsoft-led transition?  

Yes, partners can use the bulk tool to create GDAP relationships without customer consent as long as the DAP relationship isn't removed.

## When will the DAP relationship be removed?

Thirty days after the GDAP relationship is created, Microsoft will remove the DAP relationship. If you have already created a GDAP relationship, Microsoft will remove the respective DAP relationship in July 2023.

## Access the Azure portal after the Microsoft-led transition

If the partner user is part of the Admin Agent Security Group, or the user is part of a security group such as **Azure Manager** that is nested within the **Admin Agent Security Group** (Microsoft-recommend best practice), then the partner user will be able to access Azure portal using the least privilege **Directory Reader** role. The Directory-Reader role is one of the default roles for the GDAP relationship that is created by Microsoft-led transition tool. This role is automatically assigned to the Admin Agent security group as part of Microsoft-led transition from DAP to GDAP.

| Scenario  |DAP Enabled  | GDAP Relationship Exists  | User assigned Admin Agent role  | User added to Security Group with Admin Agent membership  | Directory Reader role auto assigned to Admin Agent Security Group   |User can access Azure subscription  |
|------|-------------|---------------------------|---------------------------------|--------------------------------------------|----------------------------------------------------------------------|-----------|
|1  |Yes  |Yes  |No  |Yes  |Yes  |Yes  |
|2  |No   |Yes  |No  |Yes  |Yes  |Yes  |
|3  |No   |Yes  |Yes |Yes  |Yes  |Yes  |

For scenarios 1 and 2, where the user-assigned admin agent role is “No”, the partner user membership changes to **Admin Agent** role once they're part of the **Admin Agent Security Group (SG)**. This behavior isn't a direct membership but derived by being part of **Admin Agent SG** or a security group nested under the **Admin Agent SG**.

## After the Microsoft-led transition, how do new partner users get access to Azure portal?

See [Workloads supported by granular delegated admin privileges (GDAP)](./gdap-supported-workloads.md) for Azure best-practices. You can also reconfigure your existing partner user’s security groups to follow the recommended flow:

:::image type="content" source="./media/gdap/gdap-azure-portal.png" alt-text="Diagram showing the relationship between partner and customer using GDAP.":::

## See the new GDAP relationship

When a new GDAP relationship is created with the Microsoft-led transition tool, you'll find a relationship with the name ```MLT_(First 8 digits of Partner Tenant)_(First 8 digits of Customer Tenant)_(8-digit random number)```. The number ensures that the relationship is unique in both your tenant and the customer tenant. Example GDAP relationship name: "```MLT_12abcd34_56cdef78_90abcd12```".

### See the new GDAP relationship in Partner Center Portal

From the Partner Center portal, open the **Customer** workspace, and select the **Admin relationship** section, and select the customer.

:::image type="content" source="media/gdap/admin-relationship-section.png" alt-text="Screenshot of the Admin Relationships screen in Partner Center. The list shows admin relationships with the customer that are currently active, expired, or terminated, including a single entry, MLT_abc123_def456." lightbox="media/gdap/admin-relationship-section.png":::

From here, you can find the Azure AD roles, and find which Azure AD roles are assigned to the **Admin Agents** and **Helpdesk Agents** security groups.

:::image type="content" source="media/gdap/azure-ad-roles.png" alt-text="Screenshot of a sample Admin Relationship that has the name MLT_abc123_def456. The list shows admin relationships with the customer that are currently active, expired, or terminated." lightbox="media/gdap/azure-ad-roles.png":::

Select the down arrow in the **Details** column to see the Azure AD roles.

:::image type="content" source="media/gdap/azure-ad-security-groups.png" alt-text="Screenshot of the customer's view of the Admin Relationship screen, with the Security Groups details visible." lightbox="media/gdap/azure-ad-security-groups.png":::

### Where will customers find the new GDAP Relationship created through the Microsoft-led transition in Microsoft Admin Center (MAC) Portal?

Customers can find the Microsoft-led GDAP relationship in the **Partner Relationship** section in the **Settings** tab.

:::image type="content" source="media/gdap/microsoft-admin-center-portal-gdap.png" alt-text="Screenshot of the Microsoft 365 admin center. In the Settings tab, the Granular delegated administrative privileges (GDAP) show one partner relationship, with the name MLT_abc123_def456." lightbox="media/gdap/microsoft-admin-center-portal-gdap.png":::

## Audit logs in the customer tenant

The following screenshot shows what the Audit logs in the customer tenant look like after the GDAP relationship is created through Microsoft-led transition:

:::image type="content" source="media/gdap/audit-logs.png" alt-text="Screenshot of what the Audit logs in the customer tenant look like after the GDAP relationship is created through Microsoft-led transition:" lightbox="media/gdap/audit-logs.png":::

## How do Audit Logs look in Partner Center Portal for MS Led created GDAP Relationship?

The following screenshot shows what the Audit logs in the Partner Center portal look like after the GDAP relationship is created through Microsoft-led transition:

:::image type="content" source="media/gdap/audit-log-partner-center.png" alt-text="Screenshot of the Customer Azure portal, with the fictitious customer: Trey Research selected. Audit logs show the date, service area, Category, Activity, Status, Target, and Initiated by." lightbox="media/gdap/audit-log-partner-center.png":::

## What are the Azure Active Directory GDAP service principals that are created in the customer's tenant?

| Name	| Application ID
|--------|--------|
| Partner customer delegated administration	| 2832473f-ec63-45fb-976f-5d45a7d4bb91
| Partner customer delegated admin offline processor	| a3475900-ccec-4a69-98f5-a65cd5dc5306
| Partner Center Delegated Admin Migrate | b39d63e7-7fa3-4b2b-94ea-ee256fdb8c2f

In this context, "first-party" means that consent is implicitly provided by Microsoft at API call time and the OAuth 2.0 Access Token is validated on each API call to enforce role or permissions for the calling identity to managed GDAP relationships.

The 283* Service Principal sets up the XTAP "service provider" policy and prepares permissions to allow expiration and role management. Only the GDAP SP may set or modify the XTAP policies for Service Providers.

The a34* identity is required for the entire lifecycle of the GDAP relationship and will be automatically removed at the time the last GDAP relationship ends. The a34* identity's primary permission and function is to manage XTAP policies and access assignments. A customer admin shouldn't attempt to manually remove the a34* identity. The a34* identity implements functions for trusted expiration and role management. The recommended method for a customer to view or remove existing GDAP relationships is via the admin.microsoft.com portal.

The b39* service principal is required for the approval of a GDAP relationship which are being migrated as part of Microsoft led Transition. The b39* Service Principal has permission to set up the XTAP "service provider" policy and add service principals in the customer tenants for migrating GDAP relationships only. Only the GDAP SP may set or modify the XTAP policies for Service Providers.

## Conditional access policies

Microsoft will create a new GDAP relationship, even if you have a conditional access policy in place. The GDAP relationship is created in an **Active** state.

The new GDAP relationship doesn't bypass the existing conditional access policy that a customer has set up. The conditional access policy continues, and the partner continues to have a similar experience as a DAP relationship.

In some cases, though the GDAP relationship is created the Azure Active Directory roles aren't added to security groups by Microsoft-led transition tool due to certain conditional access policies set by customers. In such cases, please work with the customer to complete the setup. See how customers can [exclude CSPs from conditional access policy](./gdap-faq.md#exclude-csps).

## Global Reader role added to Microsoft Led Transition GDAP

"Global Reader" role has been added to MS Led created GDAP in the May after receiving feedback from partners in June 2023. Starting July 2023 all MS Led created GDAPs will have Global Reader role making it 9 Azure AD roles in total.

## Next steps

- [GDAP FAQ](gdap-faq.md)
- [GDAP migration FAQ](./gdap-migration-faq.md)
