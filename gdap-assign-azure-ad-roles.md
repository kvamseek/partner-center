---
title: Grant granular permissions to security groups
ms.topic: article
ms.date: 06/06/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: How to assign Azure AD roles approved by customer for GDAP.
author: kvamseek
ms.author: vamseekk
---

# Grant granular permissions to security groups

**Appropriate roles**: Global admin | User management admin | Admin agent

You can assign customer-approved, Azure Active Directory (Azure AD) roles to security groups.

You can then grant those security groups granular delegated admin privileges (GDAP).

## Prerequisites

Partners should first set up the security group.

- Sign in to the [Azure portal](https://portal.azure.com/).
- [Create the new security group](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal).
- [Add a user to the security group](/azure/active-directory/fundamentals/active-directory-groups-members-azure-portal).

## Grant permissions to security groups

To grant permission to security groups, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

   :::image type="content" source="media/gdap/gdap-give-customers-rel.png" lightbox="media/gdap/gdap-give-customers-rel.png" alt-text="Screenshot depicting customer admin relationships page.":::

2. Select the customer you want to manage, then select **Admin relationships**, and then select the specific admin relationship you want to change.

   :::image type="content" source="media/gdap/gdap-admin-rel-contoso.png" lightbox="media/gdap/gdap-admin-rel-contoso.png" alt-text="Screenshot depicting admin relationship details page.":::

3. Under **Security groups**, select **Add/remove groups**.
4. On the **Security groups** panel, select the security groups that you want to grant permissions.

   :::image type="content" source="media/gdap/gdap-admin-rel-contoso-helpdesk.png" lightbox="media/gdap/gdap-admin-rel-contoso-helpdesk.png" alt-text="Screenshot depicting admin relationship helpdesk details page.":::

5. Select **Save**.

   The security group now appears in the **Security groups** section.
6. Select the newly added security group, which opens the **Select Azure AD roles** side panel.
7. Choose the Azure AD roles you want to assign to the security group for that admin relationship.

   The Azure AD roles that you assign enable the users in the security group to administer services.

   :::image type="content" source="media/gdap/gdap-admin-rel-contoso-sec.png" lightbox="media/gdap/gdap-admin-rel-contoso-sec.png" alt-text="Screenshot depicting admin relationship details security group page.":::

8. Select **Save** from side panel.
9. Select **Done**.

   You can remove or add more security groups and Azure AD roles.

   All the users assigned to the security group can now administer services from their **Service management** page.

   :::image type="content" source="media/gdap/gdap-service-management.png" lightbox="media/gdap/gdap-service-management.png" alt-text="Screenshot depicting a customer service management page.":::

## Dynamics 365 delegated admins

Delegated administrators:

- Aren't visible in a customer's Azure AD user list
- Can't be managed by a customer's internal admin

However, when a delegated admin logs into a Dynamics 365 environment on behalf of a customer, they're automatically created as a user inside the Dynamics 365 environment. That means that the actions performed by a delegated admin, such as posting documents, are logged in Dynamics 365 and associated with their ID in the partner's Azure AD.

The internal admin can see which changes are made by delegated admin, and which partner a specific user works for, but they can't see the user's name or other customer content.  

## Next steps

- [Least privileged roles by task](gdap-least-privileged-roles-by-task.md)
- [How to terminate a relationship - for partners](gdap-partner-terminate.md)
- [How to terminate a relationship - for customers](gdap-customer-terminate.md)


