---
title: Import multiple users to a customer account with an Excel-compatible .csv file
ms.topic: how-to
ms.date: 06/06/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: To add multiple users to a customer's account, upload a data file to Partner Center using the comma-separated value (.csv) file format.
author: amitravat
ms.author: amrava
---

# Import multiple users to a customer account with an Excel-compatible .csv file

**Appropriate roles**: Global admin

_You can add users in bulk into Partner Center with the **Upload users** tool._

Use the steps below to add multiple users to a customer's account by modifying and uploading an Excel-compatible comma-separated value file format (.csv).

## Download a copy of the template for the bulk upload tool.

Use the following steps to create your customer file and upload it.

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers** > **Customer list**.
1. Select the customer's **Users and Licenses** tab, then select **Upload users**.

   For pilot users, this appears in a menu bar at the top of the screen:
   :::image type="content" source="./media/users/users-and-licenses-menu-bar.png" alt-text="Screen shot of the Users and licenses menu bar." :::<br>

1. Select **Download template (.csv)**. Follow the prompts to save the Excel-compatible .csv file to your computer.

## Modify the template

On your computer, open the template file, and modify it to meet the following requirements:

- All users must be in the same geographic **Location**.
- You can upload up to 100 records at a time. If you need to add more than 100 users, create and upload additional data files.
- Each user must have a unique email address, appended to the customer's email domains;
- Enter only the data described below, and with the following limitations. Extraneous data will cause the upload to fail.

| **Column name** | **Description**  | **Limitation**  |
|:-------- |:------  |:----- |
| First name  | User's first name (optional field)  | 50-character limit  |
| Last name  | User's last name (optional field)  | 50-character limit  |
| Display name    | Name displayed in the Partner Center (required field)                            | 50-character limit                         |
| Email   | User's business email address at customer company (required field)           | Each user must have a unique email address |
| Status update   | Used to indicate whether the new user record was successfully created | \*\*Leave empty\*\*

## Add the users into Partner Center by uploading the template

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers** > **Customer list**.
1. Select the customer's **Users and Licenses** tab, then select **Upload users**.
1. Browse to the updated template, and select **Open**. The updated template appears in the list of files in the Upload user info section.
1. Next to the uploaded template file, select **Validate**.

   If the file is formatted correctly, Partner Center responds that the file is validated and confirms the number of users in the file.

   Most account creation errors are caused by data file issues, including missing information, malformed or duplicated email addresses, or too many records in the file.

1. After the Partner Center validates the file, select the geographic **Location** for the new users.
1. Select **Save**.
1. Assign licenses to the new users by selecting a service plan to be assigned.
1. Select **Download temporary password information** to download a copy of the user names and temporary passwords for the new accounts.
   > [!IMPORTANT]
   > Be sure to download the file with the temporary passwords now because you won't be able to do it later. New users must sign in to their new account using the temporary password for their new accounts.

   New users are automatically assigned permissions to: **Can use licenses and services**.

## Next steps

- [Give customers permission in Partner Center to buy their own products or services](give-customers-permission.md)
