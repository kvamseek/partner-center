---
title: Merge your partner account with another partner account
description: Learn how companies who are active Microsoft partners in Partner Center can merge their accounts.
ms.topic: article
ms.service: partner-dashboard
ms.subservice: partnercenter-account
author: sharath-satish-msft
ms.author: shsatish
ms.date: 5/16/2023
---

# Merge your partner account with another partner account

**Appropriate roles**: Account admin, Global admin

Two or more companies who are active Microsoft partners and have accounts in Partner Center can merge their accounts.

## What happens when two partners elect to merge their Partner Center accounts

**When two partners merge their accounts:**

- The partner organization who initiates the merger is the partner global account (PGA).

- The invited organization's PGA becomes a location of the initiating company.

- All the locations of the merging account become locations under the PGA.

- When the account merger is complete, you can see the details of both accounts (such as locations and users) within the PGA profile. You can't reverse this process.

- All PartnerIDs for locations are preserved during the consolidation.

- User's roles are brought over. For example, if a user is an *Incentives admin* for a location, they still have that role after the merger and can see the incentives they saw prior to the merger. If a user is a *Referrals admin* for the whole organization, they will still have that role after the merger and can see the referrals across the merged organization.
- Admin rights are extended to the whole organization for admins (Global Admin, Partner Admin, Account Admin, etc.) of both tenants. For example, a Global Admin from the invited organization can assign the Referral Admin role to any user from their tenant to the entire merged organization or PLAs across the merged organization.
- Azure AD tenants and CSP accounts aren't merged and have no effect.

- Published offers and co-sell pipeline data associated with both companies are preserved

### View of merged accounts

:::image type="content" source="media/merge-accounts/account-merge.png" lightbox="media/merge-accounts/account-merge.png" alt-text="Diagram of an initiating account and an accepting account merging.":::

## What to expect if you've been invited to merge your Partner Center account with another Partner Center account

If you decide to accept an invitation to merge accounts:

- Your PartnerIDs (formerly MPN IDs) and locations are merged into the PGA of the partner account that invited you.

- Your users are brought into the merged account with their roles intact.
- Your users with admin roles that extend across your whole organization will gain admin access across the whole merged organization. However, they will only be able to manage users within the tenant they are in.
- Existing benefits and competencies are preserved for both companies after the merger until renewal. At renewal, the accounts are treated as one company and standard renewal rules apply.

- Be sure to activate all the benefits you intend to use, for both accounts, prior to merging and/or your subsequent membership renewal date (see table below).


## Understand the effects on programs and benefits when partners elect to merge accounts

- All existing Solution areas, purchases (such as Solutions Partner designation), and associated benefits are retained during consolidation. This retention means they'll continue to use both bundles of benefits if there is an immediate merger, since they have paid for or acquired these separately.

- The most recent renewal date for Microsoft Action Pack is retained after the merger. For example, if the Action Pack renewal date is June 2020 for company 1 October 2020 for company 2, Microsoft uses the October 2020 date as the renewal date for the merged company.

- During the account merger and until the next renewal, each account retains its Action Pack and/or Solutions Partner benefits and/or legacy gold/silver benefits. At renewal, standard Action Pack and Solutions Partner designation renewal rules apply.

- If both companies have different solution area designations, then the acquiring partner will be awarded with the consolidated solution areas. If Company A is acquiring company B, and company A has two solution areas, company B has two different solution areas, then the merging company A (B got merged into A) will have four solution areas.

- Highest anniversary date for Microsoft Solutions Partner designation will be retained after the merger, provided both the Partners got Solutions Partner badges. (See the table below the Business rules)

- When two accounts are merged, the acquiring account will have all the solution areas that they were qualified for in either of accounts. The benefit bundles for the company that is being acquired will be migrated to the acquirer without any change in the expiry date of benefits.

- Upon renewal, benefits that are included with Solutions Partner attainment are provisioned for the partner global account. Detailed list of scenarios is mentioned in the next section. See the table in the next section for all possible scenarios during renewal.

- All benefits are subject to the Microsoft AI Cloud Partner Program Terms of Participation. (For example, an activated Office 365 E3 token is functional for 12 months after activation.) After a token has been activated for licenses on a tenant, those licenses can't be moved to another tenant.

- The MCP ID associations for both companies are retained and associated with the PGA Partner ID (formerly MPN ID).

- Go-to-market and technical benefits are offered as competency core benefits.

- If your company is in the Azure Expert MSP program, benefits are retained until renewal.

- If your company has earned advanced specializations, they're retained across both accounts.

- Any software assurance vouchers are retained across both accounts.

- There's no effect on DPOR or PAL association. Any associated revenue contributions flow into the new Partner Global Account.

After the merger, it's recommended that you check your bank, and tax information to ensure accuracy.

## Invite a company to merge their Partner Center account with your Partner Center account

To invite a company to merge their Partner Center account with yours, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) as an Account admin for your company and select the **Settings** (gear) icon.

2. Select the **Account settings** workspace.

3. Select **Account merge**.

4. Enter the PartnerID (formerly MPN ID) in the **Partner profile** of the account that you want to invite to merge with you.

   You must use the *partner global* PartnerID (formerly MPN ID). You can't use a location PartnerID (formerly MPN ID).

5. Select **Merge**.

   An invitation to merge is sent to the partner company.

   - If the company *accepts* your invitation, you can initiate the account merger within Partner Center.

   - If the company *rejects* your invitation, they can explain why they rejected the request.

A list of all your account mergers is available in **Merge history**.

### Example of two companies merging accounts

#### Before the merger

- *Contoso, Ltd.* has:

  - A [global PartnerID of *1111111*](https://aka.ms/accountexp/legalInfo)
  - A subordinate [location PartnerID of *2222222*](https://aka.ms/accountexp/legalInfo).
  - An Azure AD tenant of *@contoso.com*
  - A Solutions Partner designation  that expires on October 1, 2023

- *Fabrikam, Inc.* has:
  - A global PartnerID of *3333333*
  - Two subordinate location PartnerIDs of *4444444* and *5555555*
  - An Azure AD tenant of *@fabrikam.com*
  - Two Solutions Partner designations that expire December 1, 2023

#### During the merger

1. *Contoso* buys Fabrikam and goes to Partner Center to initiate a merger request.
2. *Fabrikam* signs into Partner Center and goes to the same page as Contoso did in step 1 to approve Contoso's request.
3. *Contoso* reviews the details of the merger on that same page and provides confirmation to proceed with the account merger.

#### After the merger

After the merger, the company account has the following characteristics:

- A company name of *Contoso*
- A global PartnerID of *1111111*
- Four subordinate location PartnerIDs of *2222222*, *3333333*, *4444444*, and *5555555*
- Two Azure AD tenants (*@contoso.com* and *@fabrikam.com*) that have access to the same Partner Center account
- Two benefits packages:
  - One Solutions Partner benefits package that expires October 1, 2023
  - Two Solutions Partner benefits packages that expire December 1, 2023,
- Three Solutions Partner designations for the merged entity 

Furthermore:

- Fabrikam's admins continue to manage Partner Center roles for @fabrikam.com's users
- Contoso's admins continue to manage Partner Center roles for @contoso.com's users.

- Contoso's and Fabrikam's admins can assign roles for users across all PLAs and the merged PGA account for users from their respective tenants.

- Contoso's admins can only administer Fabrikam's users if they're invited as a guest into Fabrikam's tenant.
- Contoso could decide to ignore the @fabrikam.com tenant and reissue the Fabrikam employees new @contoso.com credentials with new roles and permissions.

## Table of possible scenarios

|      Scenarios     | Just before Merger                                        | At the time of Merger                                             | First renewal post-merger                                                         |    Options               |
|-----------|----------------------------------------------------------------|-----------------------------------------------------------------------|----------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   | **Partner A**                                                  | **Partner B**                                                         | **Membership and anniversary date of merged entity (A+B)**                               | **Benefits purchase options at the time of renewal for merged Partner**                                                                                                                                                                                                                                                                                                                                                         |
| 1a        | Solutions Partner designation with Solutions Partner benefits  | Solutions Partner designation with Solutions Partner benefits         | Solutions Partner designation, AD = Max of two ADs of two Solutions Partner designations |  At the time of renewal, the Partner can only choose the benefits for Solutions Partners.                                                                                                                                                                                                                                                                                                                         |
| 1b        | Solutions Partner designation with Solutions Partner benefits  | Solutions Partner designation with legacy benefits                    | Solutions Partner designation, AD = Max of two ADs of two Solutions Partner designations | Partner can renew the Solutions Partner badge, if they get qualified Partner can opt for Solutions Partner benefits. Partner doesn't get the option to choose legacy gold/silver benefits                                                                                                                                                                                                                                      |
| 1c        | Solutions Partner designation with legacy Benefits             | Solutions Partner designation with Solutions Partner benefits         | Solutions Partner designation, AD = Max of two ADs of two Solutions Partner designations | Partner can renew the Solutions Partner badge, if they get qualified Partner can opt for Solutions Partner benefits. Partner doesn't get the option to choose legacy gold/silver benefits                                                                                                                                                                                                                                      |
| 1d        | Solutions Partner designation with legacy Benefits             | Solutions Partner designation with legacy benefits                    | Solutions Partner designation, AD = Max of two ADs of two Solutions Partner designations | At the time of renewal, the Partner has two options to choose between Solutions Partner benefits or Legacy benefits. If Partner chooses benefits for Solutions Partners, the enrolled Solution areas associated benefit bundles are provided. If the Partner chooses the legacy benefits, then the aggregate of the legacy benefits of both partners (without any duplicates) at the higher level will be provided.      |
| 2a        | Solutions Partner designation with Solutions Partner benefits  | No Solutions Partner designation. Has got legacy Gold/Silver benefits | Solutions Partner designation, AD = AD of Solutions Partner designation of A*           | Partner can renew the Solutions Partner badge. If they get qualified Partner can opt for Solutions Partner benefits. Partner doesn't get the option to choose legacy gold/silver benefits                                                                                                                                                                                                                                      |
| 2b        | Solutions Partner designation with Legacy benefits             | No Solutions Partner designation. Has got legacy Gold/Silver benefits | Solutions Partner designation, AD = AD of Solutions Partner designation of A*           | At the time of renewal, the Partner has two options to choose the benefits between benefits for Solutions Partners or Legacy benefits. If Partner chooses Benefits for Solutions Partners, the enrolled Solution areas associated benefit bundles are provided. If the Partner chooses legacy benefits, then an aggregate of the legacy benefits of both partners (without any duplicates) at the higher level will be provided. |
| 2c        | No Solutions Partner designation. Has got Gold/Silver benefits | Solutions Partner designation with Solutions Partner benefits         | Solutions Partner designation, AD = AD of Solutions Partner designation of B*           | Partner can renew the Solutions Partner badge. If they get qualified Partner can opt for Solutions Partner benefits. Partner doesn't get the option to choose legacy gold/silver benefits                                                                                                                                                                                                                                      |
| 2d        | No Solutions Partner designation; Has got Gold/Silver benefits | Solutions Partner designation with legacy benefits                    | Solutions Partner designation, AD = AD of Solutions Partner designation of B*           | At the time of renewal, partners have two options to choose from, the benefits between benefits for Solutions Partners or legacy benefits. If the partner chooses benefits for Solutions Partners, the enrolled Solution areas associated benefit bundles are provided. If the Partner chooses legacy benefits, then an aggregate of the legacy benefits of both partners (without any duplicates) at the higher level will be provided. |
| 3         | No Solutions Partner designation; Has got Gold/Silver benefits | No Solutions Partner designation; Has got Gold/Silver benefits        | No Solutions Partner designation                                                       | The renewal window opens on Company A legacy Gold/Silver Anniversary date. The partner has only one option to choose the legacy benefits and if the Partner chooses legacy benefits, then an aggregate of the legacy benefits of both partners (without any duplicates) at the higher level will be provided.                                                                                                                       |
| 4         | No Solutions Partner designation; Has got Gold/Silver benefits | None                                                                  | No Solutions Partner designation                                                       | The renewal window opens on Company A legacy Gold/Silver AD;  The partner has only one option to choose the legacy benefits and If the Partner chooses legacy benefits, then an aggregate of the legacy benefits of both partners (without any duplicates) at the higher level will be provided.                                                                                               |
| 5         | NIL                                                            | No Solutions Partner designation; Has got Gold/Silver benefits        | No Solutions Partner designation                                                       | As the company A doesn't have any legacy AD, the renewal window for legacy benefits (aligned with those eligible for partner B) purchase happens with legacy AD date of company B                                                                                                                                                                                                                                              |

*Be sure to activate all the benefits you intend to use, for both accounts, prior to merging and/or your subsequent membership renewal date.

## Next steps

- [Assign users roles and permissions](permissions-overview.md)

- [Verify your partner profile information](update-your-partner-profile.md)

- [Add Azure Partner Shared Services so partners can buy Azure subscriptions for their own use](shared-services.md)


