---
title: Manage locations in your partner account
ms.topic: how-to
ms.date: 04/27/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-account
description: Learn how to add a new location. Learn how PartnerLocationID is used in incentive programs, CSP business, subscriptions, and other transactions.
author: sharath-satish-msft
ms.author: shsatish
---
# Manage your Microsoft AI Cloud Partner Program account locations, and add or delete a location

**Appropriate roles**: Account admin

A Microsoft AI Cloud Partner Program account can be global or local. Each Microsoft AI Cloud Partner Program account has a PartnerID.

- The *global PartnerID* identifies the equivalent of a company's headquarters. It's used for non-transactional activities such as support requests.

- A *location PartnerID* identifies a company subsidiary. It's used to enroll in incentive programs, to transact Cloud Solution Provider (CSP) business, and other business transactions. Payouts are tied to these specific locations.

## Example Microsoft AI Cloud Partner Program account structure and account IDs

In the diagram, Contoso has its company headquarters in the UK, so that's where the business is legally registered. The UK is also the location of Contoso's partner global account (PGA), PartnerID 1234566.

Contoso has subsidiaries in the UK, France, and the United States. Each has its own partner location account (PLA) and PartnerID.

> [!NOTE]
> There is a one-to-one relationship between a CSP tenant and a Microsoft AI Cloud Partner Program location ID.

:::image type="content" source="media/locations/locations1.png" lightbox="media/locations/locations1.png" alt-text="Diagram of an example account structure, with one Partner Global Account and its associated PartnerID, and below that three subsidiary Partner Local Accounts in different countries/regions, each with its own PartnerID.":::

## Add a partner location

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) with a Microsoft AI Cloud Partner Program account that has Global admin or Account admin privileges and select **Settings** gear.

   > [!NOTE]
   > Your Microsoft AI Cloud Partner Program credentials may be different from your CSP credentials.

2. Select the **Account settings** workspace, and then select **Organization profile**.

3. Select **Legal** and then, on the **Partner** tab, select **Business locations** and select **Add location.**

4. Provide the required details, including business name, address, and contact information for the location.

5. Select **Add location** to create a new PartnerID for the location that you can use for CSP transactions and incentives.

   :::image type="content" source="media/manage-locations/legal-biz.png" lightbox="media/legal-biz.png" alt-text="Screenshot of adding a new PartnerLocationID in Partner Center.":::

   > [!IMPORTANT]
   >
   >- After you add a PartnerLocationID in Partner Center, you must contact Partner Support if you want to remove it. For more information about deleting a location, see the next section, [Delete a location PartnerID](#delete-a-partner-location).
   >- Ensure that the enrolling location is a legitimate business entity and at the stated address. Otherwise, the location will not pass the verification process.

## Delete a partner location

To delete a PartnerLocationID from your account, you must contact [Partner Support](https://partner.microsoft.com/dashboard/v2/support/servicerequests/create?stage=2&topicid=1af7f3a0-1757-3543-4b6a-c945c3ad187b).

Before a PartnerLocationID can be deleted, you'll be required to provide written statement saying that you understand that:

- Deleted locations can't be retrieved.
- Anything tied to that PartnerID will no longer be recognized or be active for your company (for example, co-sell solutions or other program enrollments).

## Prerequisites for adding a new account for a CSP business

To add a new CSP business account, start by ensuring that you've fulfilled the prerequisites:

- You must accept the Microsoft Partner Agreement and activate the account.

- You must have a PartnerLocationID in the country/region where you want to do CSP business.

- If you want to enroll as a direct-bill partner, read [Requirements to enroll as a CSP direct-bill partner](direct-partner-new-requirements.md)

- To create a new CSP indirect reseller enrollment, read [Work with indirect providers](indirect-reseller-tasks-in-partner-center.md#get-started).

    > [!NOTE]
    > Remember to sign in with the **new** credentials for the **new** CSP account. Don't use your existing credentials because if you do, Partner Center will recognize you as already having an account.

## View and update your Microsoft AI Cloud Partner Program locations

Use the following steps to view and update your Microsoft AI Cloud Partner Program locations.

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) with your Microsoft AI Cloud Partner Program account credentials (your Microsoft AI Cloud Partner Program credentials may be different from your CSP credentials) and select **Settings** (gear).

2. Select  **Account settings**, then **Organization profile**, and then **Identifiers**.

3. Find the PartnerID with type *Location* that matches the country/region of this CSP account and use it to complete the association.

4. If you can't find the PartnerLocationID that matches the CSP account that you want to use, you can add a new location, which will create a new PartnerID. See [Add a location PartnerID](#add-a-partner-location).

## Add the registration number ID

If you're an indirect provider, direct-bill partner, or indirect reseller and you're doing business with new or existing customers in the following countries/regions, you must provide registration ID numbers for your business. (If the country/region you're doing business in isn't listed below, providing a registration ID is optional).

- Armenia
- Azerbaijan
- Belarus
- Brazil
- Hungary
- India
- Iraq
- Kazakhstan
- Kyrgyzstan
- Moldova
- Myanmar
- Poland
- Russia
- Saudi Arabia
- South Africa
- South Sudan
- Tajikistan
- Thailand
- Türkiye
- Ukraine
- United Arab Emirates
- Uzbekistan
- Venezuela
- Vietnam

For more information, see [Registration ID number information](reg-number-id.md).

## Change the country/region of a partner global account

Use the following steps to change the country/region of the partner global account.

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) with your Microsoft AI Cloud Partner Program account credentials (your Microsoft AI Cloud Partner Program credentials may be different from your CSP credentials) and select **Settings** (gear).

2. Select **Account settings**. On the **Partner** tab, go to **Business locations** and check the list of locations to ensure that the location you want as your legal entity is listed.

3. To add a location, select **Add a location**, and provide the required details, including business name, address, and primary contact for the location that you want to add to your company.

4. Select **Change your country** next to the **Country/region** drop-down list and follow the steps.

    :::image type="content" source="media/manage-locations/legal-business-profile-2.png" lightbox="media/manage-locations/legal-business-profile-2.png" alt-text="Screenshot of the Legal business profile page in Partner Center, which has boxes in which you can fill in address and contact information.":::

5. Select **Save**.

The Microsoft AI Cloud Partner Program global account country/region is changed to the new country or region.

## Next steps

- Learn about the [verification process](verification-responses.md).
