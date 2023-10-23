---
title: Obtain granular admin permissions to manage a customer's service 
ms.topic: how-to
ms.date: 10/23/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: How to obtain granular admin permissions.
author: kvamseek
ms.author: vamseekk
---

# Obtain granular admin permissions to manage a customer's service

**Appropriate roles**: Admin agent

Partners can request granular delegated admin privileges (GDAP) for more granular and time-bound access to their customers' workloads. More granular control addresses customers' security concerns.

## Prerequisites

The following steps must be taken before you can obtain granular admin permissions.

- Sign in to the [Partner Center](https://partner.microsoft.com/dashboard/home) as an Admin agent and then into a partner **Production** account.
- Create a [new customer](add-a-new-customer.md).

   > [!NOTE]
   > Purchasing an Microsoft Entra Premium P2 license is no longer required.

## Request a granular admin relationship with a customer

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Select a customer, then select **Admin relationships**, and then **Request for new relationship**.

   :::image type="content" source="media/gdap/gdap-admin-relationships.png" lightbox="media/gdap/gdap-admin-relationships.png" alt-text="Screenshot depicting customer's admin relationships page in Partner Center.":::

3. On the **Create an admin relationship request**, enter a name in **Admin relationship name** and  a duration in **Duration in days**.
   - **Admin relationship name** must be unique and is visible to the customers in the Microsoft 365 Admin Center.
   - **Duration in days** is the duration after which the granular admin relationship automatically expires.
4. Select **Select Microsoft Entra roles**, which opens a side panel with a list of granular Microsoft Entra roles.

   :::image type="content" source="media/gdap/gdap-request-form.png" lightbox="media/gdap/gdap-request-form.png" alt-text="Screenshot depicting admin relationship request form.":::

5. Select the Microsoft Entra roles to include in the relationship, and then select **Save**.

   - See [GDAP least-privileged roles by task](gdap-least-privileged-roles-by-task.md) for the recommended least-privileged roles for each capability.
   - All the Microsoft Entra roles that you select will appear in the **Requested Microsoft Entra roles** section.
   - You can repeat steps four and five as needed to add or delete roles.

6. Auto extend is set to **No** by default. Select the radio button **Yes** to set the admin relationship to not expire and extend by 6 months.

7. To confirm, select **Finalize request**.

   The permission request email message to be sent to your customer appears in the **Request** box. You can edit the text of the request email message, but don't change the link under **Click to review and accept** because the URL is personalized to link the customer directly to your account.

    :::image type="content" source="media/gdap/gdap-admin-request-confirmation.png" lightbox="media/gdap/gdap-admin-request-confirmation.png" alt-text="Screenshot showing the admin relationship request.":::

8. Select **Done**.

9. Send the email to your customer.

When the customer accepts your request, it appears in the **Granular administration** list on your **Administer** page. Both you and the customer will get a confirmation email notification after approval.

:::image type="content" source="media/gdap/gdap-page.png" lightbox="media/gdap/gdap-page.png" alt-text="Screenshot depicting granular administration page.":::

> [!NOTE]
   > Partners must explicitly [grant granular permissions to security groups](/partner-center/gdap-assign-azure-ad-roles) in the admin relationship to manage customer.

## Next steps

- [Customer approval](gdap-customer-approval.md)
- [Grant granular permissions to security groups](gdap-assign-azure-ad-roles.md)
- [How to terminate relationship - for partners](gdap-partner-terminate.md)
- [How to terminate relationship - for customers](gdap-customer-terminate.md)
