---
title: Azure VM sizing for maximum reservation usage
description: Learn how to size a virtual machine to your customers' computing needs when you buy Microsoft Azure reservations for them.
ms.topic: how-to
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
author: brentserbus
ms.author: brserbus
ms.date: 01/11/2023
---

# Microsoft Azure VM sizing for maximum reservation usage

**Appropriate roles**: Admin agent | Sales agent

This article explains how to size a virtual machine (VM) to your customers' computing needs when you buy Microsoft Azure reservations for them.

> [!NOTE]
> This article applies only to partners in the Cloud Solution Provider (CSP) program. Customers using other types of subscriptions (such as pay-as-you-go, individual, Microsoft Customer Agreement, or Enterprise Agreement subscriptions) should read the Azure documentation [Save with Azure reservations](/azure/cost-management-billing/reservations/save-compute-costs-reservations) instead.

## Determine the VM size for a customer's Azure reservation

When buying Microsoft Azure reservations on behalf of your customers, choose a VM sized to meet the customer's computing needs.

The following sections describe how you can get VM sizing information using:

- [Azure utilization API](#get-vm-sizing-information-using-the-azure-utilization-api)
- [Microsoft Azure portal](#get-vm-sizing-information-using-the-microsoft-azure-portal)
- [Azure PowerShell](#get-vm-sizing-information-using-microsoft-azure-powershell)
- [Azure Resource Manager (ARM) API](#get-vm-sizing-information-using-the-azure-resource-manager-arm-api)

> [!IMPORTANT]
>To correctly identify the type and size of VM to buy on behalf of your customer, you must use one of the methods described in the following sections because the VM series type is not correctly displayed in Partner Center reconciliation files.

After you buy a reservation, the reservation discount is applied automatically to virtual machines matching the attributes and quantity of the reservation. You don't need to assign the reservation to a VM.

Reservation discounts don't apply to classic or promotional VMs.

___

### Get VM sizing information using the Azure utilization API

To get VM sizing information using the Azure utilization API, use the following step:

- Use the value for `ServiceType` attribute from `additionalInfo` in the API response.

For more information, see [Get a customer's utilization records for Azure](./developer/get-a-customer-s-utilization-record-for-azure.md) in the [Partner Center API](./developer/index.yml).

___

### Get VM sizing information using the Microsoft Azure portal

To get VM sizing information using the Microsoft Azure portal, use the following steps:

1. In Partner Center, go to your **Customers** page.

2. Find the customer who wants to buy Azure VM reservations and then select the down arrow to expand the customer's information.
3. Select **Microsoft Azure Management Portal** to open the customer's record in the Azure portal.

4. Select **Virtual machines** from the portal menu and then select the VM for which you want to buy a reservation.

5. On the VM's detail page, find the size and region information, as shown in the following illustration. Use that information to purchase the reservation in Partner Center.

   :::image type="content" source="media/azure-usage/vm-details.png" lightbox="media/azure-usage/vm-details.png" alt-text="Screenshot showing size and region information on detail page.":::

___

### Get VM sizing information using Microsoft Azure PowerShell

To get VM sizing information using Microsoft Azure PowerShell, use the following steps:

Use the information in the following image to get the location and size of the VM for which you want to buy a reservation.

:::image type="content" source="media/azure-usage/azure-powershell.png" lightbox="media/azure-usage/azure-powershell.png" alt-text="Screenshot of VM location, size, and other information in PowerShell.":::

___

### Get VM sizing information using the Azure Resource Manager (ARM) API

To get VM sizing information using the ARM API, use the following steps:

1. Using the ARMClient or the ARM APIs, call the ARM client for the VM for which you want to buy a reservation.

   `/subscriptions/<Subscription ID>/resourceGroups/<Resource group name>/providers/Microsoft.Compute/virtualMachines/<VM Instance Name>?api-version=2017-12-01`

2. The call returns the values for **vmSize** and **location**, as shown in the following images.

    :::image type="content" source="media/azure-usage/arm-api-size.png" lightbox="media/azure-usage/arm-api-size.png" alt-text="Screenshot showing vmSize using the Azure Resource Manager.":::
    :::image type="content" source="media/azure-usage/arm-api-location.png" lightbox="media/azure-usage/arm-api-location.png" alt-text="Screenshot showing location using the Azure Resource Manager.location value.":::

## Verify Azure VM usage and reservation discount

After you purchase an Azure Reserved VM instance on behalf of a customer, the discount for paying for VM space in advance is automatically applied to the virtual machines that match the attributes and quantity of the customer's reservation.

You can verify the customer's reservation usage and see which virtual machines the reservation discounts are applied using:

- [Microsoft Azure portal](#verify-the-customers-reservation-usage-in-the-microsoft-azure-portal)
- [Azure utilization API](#verify-the-customers-reservation-usage-with-the-azure-utilization-api)

Instructions for using each of these methods are in the following sections.

> [!NOTE]
> Only the Azure utilization API shows the virtual machine to which the discount is being applied.

### Verify the customer's reservation usage in the Microsoft Azure portal

To verify the customer's reservation usage in the Microsoft Azure portal, use the following steps:

1. In Partner Center, go to your **Customers** page.

2. Find the customer whose reservation discount and usage you want to verify and then select the down arrow to expand the customer's information.
3. Select **Microsoft Azure Management Portal** to open the customer's record in the Azure portal.
4. Select **Reservations** from the portal menu and then select the reservation for which you want to check usage.
5. On the **Overview** page, check the reservation's utilization graph, which shows how much of the reservation was applied to virtual machines.

    - If the reservation's utilization is 100%, your customer is getting all the possible savings that the reservation purchase can provide.

    - If the reservation's usage is 0%, the discount isn't being applied to any virtual machine.

    - If the reservation's usage is between 1% and 99%, there are unused benefits.

   To avoid unused benefit, determine the correct size VM to support the customer's computing needs before making the purchase.

    > [!NOTE]
    > Utilization data may be delayed by up to 8 hours.

### Verify the customer's reservation usage with the Azure utilization API

> [!NOTE]
> Only the Azure utilization API shows the virtual machine to which the discount is being applied.

You can use the Azure utilization API get reservation usage data. Use that data to see which VMs the discount is applied to and verify that the customer is getting the reservation discount.

Compare Example A to Example B to see how to verify a customer's reservation usage.

:::image type="content" source="media/azure-usage/azure-utilization-api.png" lightbox="media/azure-usage/azure-utilization-api.png" alt-text="Reservation usage examples.":::

- `reservationId` identifies the Azure reservation that was used to apply the discount to the VM.
- `consumptionMeter` is the `MeterId` for the VM that has the reservation discount applied to it.
- `ReservationMeter` shows $0 cost because the reservation discount was applied.

For more information, see [Get a customer's utilization records for Azure](/partner-center/develop/get-a-customer-s-utilization-record-for-azure) in the [Partner Center API](/partner-center/develop/).

> [!IMPORTANT]
>Software costs, such as Microsoft Windows Server, are not included in the price of a VM reservation and appear as separate line items in the order record and on your invoice. However, if a customer has the Azure Hybrid Use Benefit, software costs are not applied. For more information, see [Windows software costs not included with Reserved Instances](/azure/billing/billing-reserved-instance-windows-software-costs).

## Next steps

|**For information about**   |**Read this**    |
|:-----------------------------|:-----------------|
|Azure reservations in CSP overview  | [Sell Microsoft Azure Reserved VM Instances](azure-reservations.md)
|Purchasing Azure reservations for your customers in Partner Center   | [Buy Azure reservations](azure-reservations-buying.md)
|Managing Azure reservations in Partner Center | [Managing Azure reservations in Partner Center](azure-reservations-manage.md)
|Purchasing Azure reservations in the Azure portal | [Prepay for virtual machines with Azure Reserved VM Instances](/azure/virtual-machines/windows/prepay-reserved-vm-instances) in the Azure Help |
|Managing Azure reservations in the Azure portal   | [Manage reserved VM instances](/azure/billing/billing-manage-reserved-vm-instance) in the Azure Help  |
|Purchasing Azure reservations using the Partner Center API | [Purchase Azure Reserved VM Instances](/partner-center/develop/purchase-azure-reservations) in the Partner Center developer documentation   |
|Giving customers permission to buy their own Azure reservations from a subscription you purchased for them. | [Give customers permission to buy their own Azure reservations](give-customers-permission.md)   |