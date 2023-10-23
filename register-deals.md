---
title: Register your deals
ms.topic: article
ms.date: 05/13/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-referrals
description: When you register a deal you've won in Partner Center, it helps Microsoft provide you with more opportunities in the future.
author: sudharocks
ms.author: spadmanabhan
---

# Register deals you've won in Partner Center

**Appropriate roles**: Referrals admin

You can register deals that you've won in Partner Center by providing additional information about the contract. The information helps Microsoft to provide you with more opportunities in the future.

> [!IMPORTANT]
> **After July 1, 2023** Once you are transacting on the commercial marketplace, deal registration will no longer be required for marketplace transactions for co-sell eligible Azure solutions. Deal registration will still be required for transactions both within and outside of the commercial marketplace to impact Partner Reported Azure Consumed Revenue (PRACR). Please note only partners who have met the requirements for top tier benefits are eligible to participate in PRACR. 

There are two paths that lead to deal registration:

- You've created a new deal in the **Co-sell opportunities** section, and your deal meets the criteria for deal registration.
- You want to report a closed *ISV Connect* deal that wasn't co-sold with Microsoft.

> [!NOTE]
> **Solution Assessment** deals are **not** eligible for deal registration.

To register deals using the co-sell deal path, use the following step:

- In the **Referrals** workspace, select the **Co-sell opportunities** tab.

  Existing deal registrations that are in review, and deal registrations that are in the closed state (approved or rejected), are available in the same section.

To register deals using the **ISV Connect deals** path, use the following step:

- In the **Referrals** workspace, select the **ISV Connect deals** tab.

  If there's co-sell opportunity associated with the ISV Connect deal, the link to initiate the ISV Connect deal registration is available in the respective opportunity.
  
  If you must register a new ISV Connect deal without any corresponding co-sell opportunity, you can initiate that from **ISV Connect deals**.

> [!IMPORTANT]
> Wait 72 hours after creating an eligible deal before marking it *Won*. If you mark the deal as won earlier than that, the registration might be rejected.

## Deal registration eligibility

To be eligible for co-sell deal registration, a referral must meet all the following criteria:

- The deal type must be either co-sell or partner-led. (You have chosen to allow Microsoft sellers to view this deal.)
- The deal value is greater than or equal to USD25,000. (Currency conversion is based on the monthly [exchange rates](https://www.reuters.com/markets/currencies) published by Reuters.)
- The customer account selected for the deal is managed by Microsoft. (That is, the customer account is with a company with which the Microsoft sales team has an existing relationship.)
- There is at least one Azure IP co-sell eligible solution in the deal.
- The status of the deal is *won*.
- If the deal type is *co-sell*, Microsoft must have either accepted the invitation or marked the deal as won. You can see the Microsoft status by looking at the Microsoft card below your deal details.

Deal registration eligibility is always shown below the deal progress. After you mark the deal as won, a **Register now** button appears at the bottom of the screen.

The only criterion for registering an ISV Connect deal is that the value of the deal must be greater than USD5,000.

Eligibility for deal registration is always shown below the deal progress. After you mark the deal as won, along with the **Register now** button, the following banner is displayed at the top of the deal: **Registration for Business Applications ISV Connect is required on this sale**.

> [!NOTE]
> If the deal registration banner doesn't appear in the deal progress bar for your deal, the deal doesn't meet all the requirements.

You can register a deal immediately after marking the deal as won, or do so later by using the deal lifecycle **Register now** button.

After the deal is registered, you can view the progress of the deal validation from the same lifecycle. If any action is required by your company, messages displayed in the deal lifecycle view notify you what to is needed.

A deal goes into a closed state when deal validation is complete.

## Co-sell deal registration


> [!IMPORTANT]
> You have 60 days from the date a contract is signed to register a co-sell deal.
>
> (All dates are in Coordinated Universal Time (UTC).

To register a Co-sell deal, use the following steps:

1. Select **Register** at the bottom of the screen.

2. Enter the required information for registering the deal on the registration form.

The following table provides details about the fields on the registration form.

|**Field name**|**Mandatory?**|**Validations (if any)**|**Description**|
|-----|---|---|-------|
|Is marketplace transaction?|Yes|No|This information is required to understand whether the customer is purchasing the solution included in the referral from a Microsoft marketplace. Selecting **Yes** enables the simplified marketplace deal registration. These deals are automatically validated (similar to non-marketplace deals) if they meet the criteria.|
|Estimated marketplace transaction date|Depends|No|This field is mandatory if the selection for the first question (*Is marketplace transaction?*) is **Yes**. The information provided in this field helps Microsoft to automate transactions in the marketplace to a specific referral. You can then proceed to provide other details.|
|Will the solution be deployed on Azure?|Yes|No|Registration is applicable only for solutions deployed on Azure. If the selection for this question is **Others**, you're prompted to close the deal without registration.|
|Is this contract a perpetual contract?|Yes|No|If the contract between the partner and customer is perpetual, the total contract value entered in the registration form is spread over a six-year period to determine the annual contract value. Registration is allowed only if the annual contract value is greater than USD25,000.|
|Total contract value|Yes|Yes. Annual contract value calculated from this value should be greater than USD25,000.|This value should include software and services but not hardware cost.|
|Solution value|Yes|Yes. Solution value should be less than or equal to the total contract value.|Total contract value, less any non-recurring implementation fee. If renewing, increase the solution value by the amount for the renewal period, and extend the end date.|
|Contract signed date|Yes|Yes. This field can be a date, which is at most 60 days in the past. The date value can't be in the future. The date should be on or after referral creation date and the Microsoft invitation date, whichever is latest.|The date on which contract has been signed with the customer and is mentioned in the contract with the customer.|
|Contract start date|Yes|Yes. This field can be a date, which is at most 90 days in the past. It can be earlier than the contract signed date.| The date from which the customer started using the solution mentioned in the referral.|
|Contract end date|Depends|Yes. This date can't be earlier than the contract start date.| This field isn't required for perpetual contracts. It's required for non-perpetual contracts. For perpetual contracts, the end date is deemed to be six years from the contract start date for annual contract value calculations.|
|Tenant type|Yes|No|This field indicates if the solution in the referral is deployed on the  customer or partner tenant.|
|Pricing model|Yes|No| This information specifies whether or not the pricing model is pay-as-you-go.|

### Pay-as-you-go deals

*Pay-as-you-go* deals qualify for the Azure IP co-sell eligibility if the same customer's payments to the same partner, for the same solution, equal or exceed USD25,000 in one year.

To register a pay-as-you-go deal in Partner Center, use the following step:

- Indicate that the deal is pay-as-you-go in the pricing model.

  This information moves the deal to the *Review Pending* state, because pay-as-you-go deals don't qualify for automated validation.  

Here's additional information about pay-as-you-go deals:

- The deal must be shared before the first contract or invoice date.  
- When you register, set the sign date and start date as the date of the first invoice, and the end date as the date of the last (or most recent) invoice.
- The contract signing date can be up to one year after the referral creation date or the Microsoft invitation date, whichever is latest.
- You should only reach out for a one-time-only update to a previously registered pay-as-you-go deal (within the same fiscal year) when the total contract value (TCV) of the deal exceeds USD1 million. A revalidation is required. Revalidations across fiscal years aren't accepted.
- A previously approved deal that isn't identified as pay-as-you-go can't be revalidated for adjusting to a higher TCV.

### States for the co-sell deal registration

The following table shows the states that the deal registration can have, the meaning of each of those states, and the possible next states.

|**State**|**Meaning**|**Next states**|
|----|------|-----|
|Registration(Pending)|This deal is eligible for registration and can be registered using the steps listed above in Co-sell deal registration[#Co-sell-deal-registration] |Approved, Review(Pending)|
|Approved|The deal meets the requirements and has been approved automatically.|Review(Pending), Closed|
|Review(Pending)|The deal is being reviewed by the review team for the correctness of the registration details. A deal can be selected for additional review by Microsoft for different reasons such as duplicates etc.|Review(Passed), Review(Failed), Action required|
|Action required|The review team has sent the deal back for editing, with relevant comments to the partners.|Review(Pending)|
|Review(Passed)|The review team has successfully reviewed the deal registration details and approved the registration.|Closed|
|Review(Failed)|The registration failed validation during review. Partners learn of the reasons for failure via a banner in Partner Center.|Closed|
|Marketplace Validation(Pending)|The deal is being validated by the review team.|Action required, Closed|
|Marketplace Validation(Passed)|The review team has successfully validated the transaction details and approved the registration.|Closed|
|Marketplace Validation(Failed)|The registration failed validations while checking for the marketplace transaction. Partners learn of the reasons for failure via a banner in Partner Center.|Closed|

### Eligibility for automatic approval

Most deals are eligible for automatic approval. The following circumstances represent the exclusions from automatic approval, in which deals are instead moved to the *Review(Pending)* state for manual review by the Microsoft review team:

- The annual contract value is greater than USD1 million.
- There are multiple partners involved in the same referral.
- The pricing type is pay-as-you-go.

> [!IMPORTANT]
> Registrations that are automatically approved can be selected for further review by the Microsoft review team. If a registration is selected during this process, you are notified by email and a banner in Partner Center. No action is required unless the review team sends back the registration and moves the state to *Action required*.

## Azure IP co-sell deal registration exception process

Partners can request an exception related to Azure IP co-sell deal registrations if they encounter issues during referrals management in Partner Center.

> [!NOTE]
> In case of deal registration rejections, partners can request for an exception within a period of **60 days from the date of initial registration.**

A request for an exception can be made in two cases:

- A referral that is marked as won and isn't eligible for Azure IP Co-sell deal registration because of a programmatic check failure.
- A referral for which deal registration is in progress or a decision has been made by the deal validation team. For example, the deal registration is in a failed state due to a validation failure during the review process.

In both cases, partners are presented with an option to request an exception at Partner Center. A link to **Request Exception** is available in the bottom right corner of the screen. The link is visible only for deals in the *Closed* state. (It can be any of the substatuses, *Won*, *Lost*, or *Error*, of the referral.)

### Exception request guidelines

- Provide a detailed business justification on why the deal should receive an exception.
- For pre-registration exception requests, provide all contract dates (signed, start and end dates).
- If there is a tooling error blocking the deal registration process, please specify this and include any relevant support ticket numbers opened with other teams.
- For re-registrations, please reference the old deal ID (referral ID) and state that this new registration is to replace the old one.
- To make updates to approved deals, share specific information on fields that needs updating, the new values, and relevant business justification.

**Only one exception request per Referral is allowed. The decision of the exception request on the exception is final and binding, the support team will not be able to help with any further changes.** It is in your best interest to explain clearly why an exception should be granted for a request. Partners can explain their cases with up to 5,000 characters when creating an exception request. **The exception council can take up to 14 working days to make a decision about whether to validate a request from a partner, based on the evidence presented**. The validation team may contact the partner to gather more evidence before granting or rejecting an exception.

A decision by the exception council can't be overridden by support, so support teams can't help if an exception request is rejected. **Please don't create support requests for cases in which an exception request has been rejected by the exception council**.

The following deal registration fields may be updated via the Azure IP Co-sell deal registration exception process.

|Field name|Change request scenario|
|----|------|
|Is this a perpetual contract|Each of these fields is eligible for the deal registration exception process. If approved via the exception process the deal will be re-opened and the partner will be responsible for making the changes within a timely manner following program guidelines.|
|Total contract value|Same as above|
|Contract signed date|Same as above|
|Contract start date|Same as above|
|Contract end date|Same as above|


> [!NOTE]
> Any change request to contract details will be subject to a standard POE verification. These changes are **not** allowed if the deal is validated through an DCF form exception.

The following fields are *not* eligible for change requests via the Azure IP Co-sell deal registration exception process and will be rejected.  

|Field name|Mitigation (if any)|
|----|------|
|Tenant type|Changes to tenant type are **not** allowed. The partner cannot re-create the Referral with a different tenant type. Any re-registration of deal will result in rejection as it is program policy that tenant change requests will not be supported in any matter.|
|Will the solution be deployed on Azure|Only Azure solutions are eligible for IP Co-sell benefits. No mitigation.|
|Solution Value|A new referral will need to be created.  Once done, an exception request will need to be entered to address the contract sign date requirement.  Please reference the original referral ID.|
|Estimated Marketplace transaction date|A new referral will need to be created.  Once done, an exception request will need to be entered to address the contract sign date requirement.  Please reference the original referral ID.|
|Customer Account|A new referral will need to be created.  Once done, an exception request will need to be entered to address the contract sign date requirement.  Please reference the original referral ID.|
|Is a Marketplace Transaction|A new referral will need to be created.  Once done, an exception request will need to be entered to address the contract sign date requirement.  Please reference the original referral ID.|
|Pricing Model|A new referral will need to be created.  Once done, an exception request will need to be entered to address the contract sign date requirement.  Please reference the original referral ID.|

### Post exception approval process

If an exception is approved, partners are presented with the following options as next steps:

- If the referral was originally not eligible for registration and an exception is approved, the partner gets the option to register the deal for Azure IP co-sell.
- If the Azure IP co-sell deal registration is in a failed state and an exception is approved, the partner can edit the details of the registration with the correct information. They can then resubmit to the deal validation team to review the details.

In both cases, some of the programmatic validations related to the dates are relaxed so that the partner can enter the correct data per the contract documents.

## ISV Connect deal registration

You can initiate this type of registration from the banner at the top of the deal progress bar.

There are two scenarios for which ISV Connect deal registration is required:

- The solution in the referral has only the Biz Apps standard or premium incentive status

  In this scenario, you select the banner to register the ISV Connect deal. You can fill in all the details, like the experience that you're already familiar with. After registration, you also have a link to go to the registered ISV Connect deal from the co-sell opportunity.

- The solution in the referral has both the IP co-sell eligibility and a Biz Apps standard or premium incentive.

  In this scenario, you select the banner to register the ISV Connect deal. You do so in addition to the co-sell deal registration that you do in the co-sell opportunity page. If the co-sell deal has been registered, the details for the ISV Connect are pre-filled. If you register the ISV Connect deal prior to registering the co-sell deal, it's a good idea to complete the co-sell deal registration first to avoid having to enter the data twice.

> [!NOTE]
> If the contract start date is earlier than the contract signed date in the co-sell deal registration, the ISV Connect deal contract start date is filled in with the contract signed date.

## Activate licenses

The remaining sections of this article provide details about license activation in Partner Center.

### Register ISV Connect deal using the Deal Registration tab

There are two ways to register an ISV Connect deal. Both ways require that the solution being registered has an ISV Connect *Standard* or *Premium* tag.

- Select **+ Report Closed ISV Connect deal** to register directly using the [Deal Registration](https://partner.microsoft.com/dashboard/deals/actionrequired) tab.

  Use this method for any deal that didn't originate from a co-sell referral, opportunity, or lead.

  The registration page is used for the ISV Connect program specifically, and results in an invoice or invoices, per the ISV Connect program addendum.

  :::image type="content" source="media/isv/report-closed-isv-connect-deal.png" alt-text="Screenshot that shows where you can report a closed ISV Connect deal in Partner Center.":::

- Select the **Register Now** button that appears in the co-sell deal progress indicator if the solution is eligible and has the ISV Connect *Standard* or *Premium* tag.

  This second way to register an ISV Connect deal is via a co-sell referral after it has been won.

  > [!NOTE]
  > The registration is for an ISV Connect solution, and results in an invoice or invoices.

  :::image type="content" source="media/isv/cosell-opportunities.png" alt-text="Screenshot that shows where you can see co-sell opportunities.":::

Both ways bring you to the **Deal Registration** form. This form requires the following information:

- **Customer details**: Company name, country, city, and state.
- **Solution**: Choose from a list of ISV Connect *Standard* or *Premium* tagged solutions. If no solutions exist, check whether the offer is tagged correctly.
- **Total contract value and currency**: This information includes software and service fees, but no hardware.
- **Solution value and currency**: Generally, this information is the total contract value, less any non-recurring implementation fees. (See the ISV Connect addendum for full details).
- **Solution deployment (Azure or other)**: If the solution won't be deployed on Azure, choose **Other**.
- **Solution consumption (customer or partner tenant)**: Will the consumption of the solution run on the partner or customer tenant? If it's a customer tenant, then a customer tenant ID is mandatory (it's a GUID, such as `x0xxx10-00x0-0x01-0xxx-x0x0x01xx100`). For more information, see [How to find your Azure Active Directory tenant ID](/azure/active-directory/fundamentals/how-to-find-tenant).
- **Contract date details**: This information refers to the date the contract was signed, the date the contract starts (which must be the day the contract was signed, or after), and the date the contract ends.
- **Partner contact information**: First name, last name, phone number, and email address.

:::image type="content" source="media/isv/closed-deal-form.png" alt-text="Screenshot that shows the form where you can enter information to report a closed ISV deal.":::

### Invite a customer when it's a new ISV relationship

When an eligible ISV Connect deal has been registered, you see **Manage Licenses** at the top of the registered deal.

:::image type="content" source="media/isv/manage-licenses.png" alt-text="Screenshot that shows the form where you can manage licenses for an ISV Connect deal.":::

To invite a customer when it's a new ISV relationship, use the following steps:

1. Select **Manage Licenses**.
2. In Partner Center, under the **Submitted** filter, select the **In Progress** tab.

   You see the deal there.
3. Provide the customer and tenant when the **Manage Licenses** pane appears.

   The dropdown list shows all of the customer-consented ISV relationships that Microsoft is aware of. Choose the customer for which this deal has been registered.

4. If a customer relationship doesn't exist yet, select **+ Invite a new customer to consent**.

   :::image type="content" source="media/isv/invite-new-customer.png" alt-text="Screenshot that shows the form where you can invite a new customer to consent.":::

   When you select **+ Invite a new customer to consent**, you see a link on the page that you can copy and send to the customer Billing admin or the Global admin. When customers access this link, they're taken to *admin.microsoft.com*, where they can accept and authorize the relationship.

   :::image type="content" source="media/isv/license-management.png" alt-text="Screenshot that shows the License Management form.":::

### Activate licenses for new deals

When a customer has been established and chosen in the dropdown list, you can start adding plans from your offer and assigning several licenses to each plan.

1. Select **+ Add a plan** to add plans from the offer.
2. Select **Update licenses** at the bottom after the plans and the number of licenses per plan are populated.
  
     The **Update licenses** button appears dimmed until you choose:
   - A customer
   - At least one plan
   - Any number of licenses greater than zero

> [!NOTE]
> You can't edit the customer field after you've populated the form and selected **Update licenses**. After licenses are added on this page, they're immediately available in the *admin.microsoft.com* site, for customers to manage and assign to employees.

:::image type="content" source="media/isv/activate-licenses.png" alt-text="Screenshot that shows the Manage licenses form.":::

### Manage licenses in existing deals

To increase or reduce the number of licenses on each plan, use the following steps:

1. Enter the new number of licenses you want for each plan.

   For example:

   - If Plan 1 has 30 licenses and you want to add 10, change the number for the plan to 40.
   - If you want to remove all licenses for a plan, select the trashcan, rather than entering zero.
2. Select **Update licenses** after you've made all your updates.
