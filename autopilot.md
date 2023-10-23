---
title: Customize a device's out-of-box experience
ms.topic: how-to
ms.date: 01/11/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Before delivering a customer's new device, you can use Windows Autopilot profiles to customize or pre-configure the device's out-of-box experience (OOBE).
author: amitravat
ms.author: amrava
---

# Use Windows Autopilot profiles on new devices to customize a customer's out-of-box experience

**Appropriate roles**: Admin agent | Global admin | Sales agent | User management admin

If you manage customer devices, you might need to customize the out-of-box experience (OOBE) for the customer's users. You can preconfigure new devices with Windows Autopilot profiles before delivering the devices to customers and apply new profiles to devices customers have already purchased.

OEMs have started including a shipping label on the outside of the Autopilot device box that shows the device's **Product Key ID (PKID)**.  This one-dimensional, readable barcode provides downstream partners with a way to register devices for Autopilot without having to unbox the device and harvest the device ID by alternative means.

This article explains how to create and apply Autopilot profiles to devices in Partner Center.

If you're not already familiar with Autopilot, see this [Overview of Windows Autopilot](/windows/deployment/windows-10-auto-pilot).

## Overview

With the Windows Autopilot feature in Partner Center, you can create custom profiles to apply to customer devices. The following profile settings were available at the time this article was published:

- **Skip privacy settings**: This optional Autopilot profile setting enables organizations to not ask about privacy settings during the OOBE process.

- **Disable local admin account creation on the device**: Organizations can decide whether the user setting up the device should have administrator access once the process is complete.

- **Automatically set up device for work or school**: All devices registered with Autopilot will automatically be considered work or school devices, so this question won't be asked during the OOBE process.

- **Skip Cortana, OneDrive, and OEM registration setup pages**: All devices registered with Autopilot will automatically skip these pages during the out-of-box experience (OOBE) process.

- **Skip End User License Agreement (EULA)**: Starting in Windows 10 version 1709, organizations can decide to skip the EULA page presented during the OOBE process. See [Windows Autopilot EULA dismissal](#windows-autopilot-eula-dismissal) below for important information to consider about skipping the EULA page during Windows setup.

The following profile and device management permissions and limitations apply:

- You can continue to manage Autopilot profiles for existing customers with whom you have reseller relationships, even if the customers have removed your delegated administration privileges.

- You can manage existing devices for your customers that you've added.

- You can't manage devices your customer has uploaded to Microsoft Store for Business or the Microsoft Intune Portal.

## Create and manage Autopilot profiles in Partner Center

In Partner Center, you can create Windows Autopilot deployment profiles and apply them to devices.

> [!NOTE]
> Only Admin agents can create and apply profiles.

### Create a new Autopilot profile

To create a new Autopilot profile, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. On the **Customer List**, select a customer.

3. On the customer's detail page, select **Devices**.

4. Under **Windows Autopilot profiles**, select **Add new profile**.

5. Enter the profile's name and description and then configure the OOBE settings. Choose from:

   - Skip privacy settings in setup

   - Disable local admin account in setup

   - Automatically skip pages in setup

      (Includes *Automatically select setup for work or school* and
    *Skip Cortana, OneDrive, and OEM registration setup pages*)

   - Skip end user license agreement (EULA)

       > [!IMPORTANT]
       > See [Windows Autopilot EULA dismissal](#windows-autopilot-eula-dismissal) below for important information to consider about skipping the EULA page during Windows setup.

6. Select **Submit** when finished.

### Apply an Autopilot profile to customer devices

> [!NOTE]
> The following instructions assume that you've already added the customer's devices to Partner Center and that you can access their device list. If you haven't already added the customer's devices, follow the instructions given previously in [Add devices to a customer's account](#add-devices-to-a-customers-account) and then follow the steps below.

After you create an Autopilot profile for a customer, you can apply it to the customer's devices.

To apply an Autopilot profile to customer devices, use the following steps:

1. Select **Customers** from the Partner Center menu and then select the customer you created the Autopilot profile for.

2. On the customer's detail page, select **Devices**.

3. Under **Apply profiles to devices**, select the devices or device groups you want to add profiles to and then select **Apply profile**.
   The profile you applied appears in the **Profile** column.

4. Verify that the profile will be applied successfully to the device.

    a.  Connect a device to the network and power it on.

    b.  Verify that the appropriate OOBE screens (if any) appear.

    c.  When the OOBE process stops, reset the device to its factory default settings to prepare it for a new user.

### Remove an Autopilot profile from a customer's device

To remove an Autopilot profile from a customer's device, use the following steps:

1. Select **Customers** from the Partner Center menu and then select the customer you created the Autopilot profile for.

2. On the customer's detail page, select **Devices**.

3. Under **Apply profiles to devices**, select the devices you want to remove the profile from and then select **Remove profile**.

   > [!NOTE]
   >Removing a profile from a device does not delete the profile from your list. If you want to delete a profile, follow the instructions in [Update or delete an Autopilot profile](#update-or-delete-an-autopilot-profile).

### Update or delete an Autopilot profile

If a customer wants to change the out-of-box experience after you've shipped the devices to them, you can change the profile in Partner Center.

When the customer's device connects to the Internet, it will download the latest profile version during the OOBE process. Also, anytime a customer restores a device to its factory default settings, the device downloads the latest profile version again during the OOBE process.

To update or delete an Autopilot profile, use the following steps:

1. Select **Customers** from the Partner Center menu and then select the customer who wants you to change an Autopilot profile.

2. On the customer's detail page, select **Devices**.

3. Under **Windows Autopilot profiles**, select the profile you need to update. Make the required changes and then select **Submit**.

To delete this profile, select **Delete profile** from the upper right corner of the page.

### Add devices to a customer's account

> [!NOTE]
>Sales agents and Admin agents can add devices to a customer's account.

Before you can apply custom Autopilot profiles to customer devices, you must be able to access the customer's device list.

If you plan to use the OEM name, serial number, and model combination, be aware of these limitations:

- This tuple works only for newer devices (4k hashes, for example) and isn't supported for 128b hashes (RS2 and prior devices).

- The tuple registration is case sensitive, so the data in the file must match the model and manufacturer names ***exactly*** as provided by the OEM provider (hardware provider).

To add devices to a customer's account, use the following steps:

1. Select **Customers** from the Partner Center menu and then select the customer whose devices you want to manage.

2. On the customer's detail page, select **Devices**.

3. Under **Apply profiles to devices**, select **Add devices**.

4. Enter a name for the device list and then select **Browse** to upload the customer's list (in .csv file format) to Partner Center.

    > [!NOTE]
    >You should have received this .csv file with your device purchase. If you didn't receive a .csv file, you can create one yourself by following the steps in [Adding devices to Windows Autopilot](/windows/deployment/windows-autopilot/add-devices#collecting-the-hardware-id-from-existing-devices-using-powershell).

5. Upload the .csv file and then select **Save**.

If you get an error message while trying to upload the .csv file, check the format of the file. You can use the hardware hash only, or the OEM name, serial number, and model (in that column order), or the Windows Product ID. You can also use the sample .csv file provided from the link next to **Add devices** to create a device list.

Your .csv file should look something like this:

> **Device Serial Number,Windows Product ID,Hardware Hash,Manufacturer name,Device model**

> **{serialNumber},,,Microsoft Corporation,Surface Laptop**

> [!NOTE]
> *Manufacturer name* and *Device model* are case-sensitive.

If you don't know which values to use for *Manufacturer name* and *Device model*, you can run the following PowerShell script on the device to gather the correct values:

```powershell
md c:\\HWID

Set-Location c:\\HWID

Set-ExecutionPolicy -Scope Process -ExecutionPolicy Unrestricted

Install-Script -Name Get-WindowsAutoPilotInfo

Get-WindowsAutoPilotInfo.ps1 -OutputFile AutoPilotHWID.csv -Partner -Force
```

## Windows Autopilot EULA dismissal

### IMPORTANT INFORMATION

You can configure customized installations of Windows on devices you manage for your customers by using Windows Autopilot. If authorized to do so by the customer, you can suppress or hide certain setup screens that are normally presented to users when setting up Windows, including the EULA (End User License Agreement) acceptance screen.

By using this function, you agree that suppressing or hiding any screens that are designed to provide users with notice or acceptance of terms means that you have obtained sufficient consent and authorization from your customer to hide terms, and that you, on behalf of your customer (whether an organization or an individual user, as the case may be), consent to any notices and accept any terms that are applicable to your customer. This includes an agreement to the terms and conditions of the license or notice that would be presented to the user if you didn't suppress or hide it using this tool. Your customer may not use the Windows software on those devices if the customer hasn't validly acquired a license for the software from Microsoft or its licensed distributors.
