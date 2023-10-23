---
title: Assign Azure subscriptions to customers
ms.topic: how-to
ms.date: 07/31/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Learn how to assign Azure subscriptions to your customers in Partner Center and how to enable customers to manage their own subscriptions.
author: migolova
ms.author: migolova
---

# Assigning Azure subscriptions to customers in Partner Center

**Appropriate roles**: Global admin | Sales agent

## Assign Azure subscriptions to your customers

To assign an Azure subscription to a customer, use the following steps:

1. In **Partner Center**, select **Customers** and then locate the customer you want to manage.

2. Select the down arrow at the end of the row to expand the customer's record and then select **Microsoft Azure Management Portal**.

   You're directed to the [Azure portal](https://portal.azure.com/) where you can manage the customer's subscriptions.

3. At the Azure portal, select **Subscriptions**.

4. Select the subscription you want to assign and then select **Access Control**.

5. Select **Add** to add a user to the subscription.

   After you add the user to the subscription, you can assign the user a role and the account to which the user will have access.

## Enable customers to manage their Azure subscriptions

After you create a Microsoft Azure subscription for a customer, you can enable them to manage the subscription. To enable, you must sign in the customer's Microsoft Azure Management portal.

To enable customers to manage their Azure subscriptions, use the following steps:

1. Open the customer's Azure portal by expanding the customer's listing in your customer list or selecting the customer's name and then selecting **Microsoft Azure Management Portal**.

   > [!NOTE]
   > If you are prompted to log onto the Azure portal, you may not have delegated administrative privileges. Select **Request a relationship** to invite the customer to identify you as their Partner of Record. After the customer accepts your invitation, you are automatically granted delegated administrative privileges.

2. In the Azure portal, open the customer's subscriptions list and select the customer's Azure subscription.

3. Assign a role to any of the customer's users so that they can create and manage resources under their subscription.

## Next steps

- [How CSP partners can sell subscriptions to customers](customer-subscriptions.md)

- [How to obtain permissions to manage a customer's service or subscriptions](customers-revoke-admin-privileges.md)
