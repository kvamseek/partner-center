---
title: Solution Assessment deals for Partner Center referrals 
ms.topic: article
ms.date: 08/24/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-referrals
description: Solution Assessment deals for Partner Center referrals, includes creating, responding a solution assessment opportunity
author: sudharocks
ms.author: spadmanabhan
---

# Create and manage Solution Assessments in Partner Center

 **Appropriate roles**: Referrals admin | Referrals user

Solution assessment deals are assessment types that an eligible partner can select based on the customer need. You can work with partners who are vetted by the solution assessments business team to assess the technology needs of customers who are using or planning to use Microsoft technologies.

## Create a Solution Assessment deal

To create a solution assessment deal, follow the process for creating an opportunity on Partner Center by selecting the **New deal** button in the **Co-sell opportunities** tab.

### Select your customer

Select the customer for a specific deal. Enter their location and start typing the name. The suggestion box will show recommendations based on the search criteria. Since many companies have more than one business entity in the same location, you may see multiple results. If you're not sure which to choose, you can confirm which DUNS Number belongs to your customer. Be sure to select the exact match for the customer with whom you're working.

After you select **Select the customer**, you'll be prompted to enter the name, phone number, and email address for the person who's your main point of contact for this deal. These details are optional and are required only if you're planning to invite Microsoft sales to help you with the engagement. Select **Next**.

> [!IMPORTANT]
> Be sure that you have obtained the customer's consent to provide their contact information to Microsoft for the deal. We may use this information to contact the customer directly.

### Add customer contact

Provide the mandatory contact information for the main contact of the opportunity by entering the required information of customer name, phone number, email, and notes for the Microsoft solution assessment specialist.

### Deal details

Enter the details of the current deal. The fields defined below can change as you actively work with the customer to close the deal.

| **Field name** | **Mandatory/optional** | **Details** |
|-------------|--------|-------|
|**Deal name** | Mandatory | The friendly name to identify your deal at a later point of time. |
|**Location**| Mandatory | The Microsoft AI Cloud Partner Program (formerly MPN) location scope of the referral. Referral users with this location scope can view the referrals if they're part of the team. Referral admins and referral admins with global scope can view the referrals irrespective of the location. Location can't be edited after creating the referral.|
|**Estimated value** | Mandatory | The value of the deal based on the information available while creating the deal.|
|**Estimated close date**| Mandatory| The date by which you expect to close the deal with the customer. |
|**CRM ID**| Optional | Tag the deal with the ID of the opportunity in your respective CRM for tracking purpose.|
|**Marketing campaign ID**| Optional | Capture the marketing campaign that resulted in the deal. This information can help you track the ROI of a campaign if you tag all the deals originating from the campaign with the same ID.|
|**Notes**| Required | Update all the latest information to provide visibility to other employees from your company working on the same deal or trying to understand the current state of the deal. You can also use this entry as a communication on record for discussions between Microsoft sellers/other partners with your company.|

### Add team members

After adding the deal details, add the employees that will be working on this specific deal. You'll need to enter the name, phone number, and email address of the employee. These details are mandatory, and you need to have at least one contact with all the details entered for you to create a deal. These details can be changed even after creating a deal. Recent contacts from your previous deals are shown on the right side for you to quickly add them to the deal.

### Add solutions

In this section, select the Solution type as **Solution Assessment** and add a solution assessment type to the opportunity. *Add solutions* is a required section where you must add only one solution assessment type to create a deal. You can make changes to the deal details but not the solution details after creating a deal.

> [!IMPORTANT]
> Only one assessment type can be selected for a solution assessment deal and no other solutions can be added. Once a solution assessment is selected, the partner has to choose the location for which the assessment is being created. This is needed for correct incentive payouts.

After you've provided the solution information, select **Next**.

Select the **Consent** box, then select **Create Deal** button to complete the deal creation process.

The newly created solution assessment deal will be available in the outbound opportunity tab with a Solution Assessment label. You can filter all the Solution Assessments deals using the filter option and selecting the Deal Type as Solution Assessment.

## Respond to a solution assessment opportunity

Each solution assessment opportunity moves through a lifecycle of its own.

### Received stage

In this stage, if you've received a new Co-sell opportunity either from a Microsoft seller or from other partners in the Microsoft Co-sell ecosystem, review the details, and feel free to contact the customer if you want to learn more about their business needs. You can take two actions in this stage. accept or decline the referral:

- **Accept:** Enter a name for the deal, edit the estimated deal value, and the estimated purchase timeframe based on your review. Once you established the contact with the customer, you should provide info in the **Notes** field to explain more about what the customer is looking for. You can optionally enter your CRM ID here (for your reference only), the marketing campaign ID that resulted in the respective opportunity, and add contacts from your company who will be working on this deal.

- When you're finished, select **Next**. We'll move the referral to **the next stage**, which means you plan to actively engage with the customer to address their need. We'll also use this information to help you find similar deals in the future.

- **Decline**: Select the reason you're declining the deal and add any notes you'd like to include, then select **Close deal**. We'll archive it as **Declined** and notify either Microsoft or the partner who sent you this opportunity.

- If you don't respond within the allotted time (currently 14 days), we'll archive it as **Expired** and notify either Microsoft or the partner who sent you this opportunity.

### Accepted stage

Work to close the deal with the customer. If you want to change any of the information you've provided for an accepted referral, select **Edit** and update the deal name, estimated purchase date, estimated value, notes, CRM ID, and the marketing campaign ID. You can also select **Add your team** to provide the name, phone number, and email addresses of any more people who are working on the deal. Solutions can't be edited based on the customer need.

All the deals you have created are in the **Accepted** stage by default.

After you start working on the deal, you can provide the details of the progress that you're making by marking the sales stages in the deal lifecycle. There are four stages in the deal lifecycle apart from the initial acceptance or creation and the final won or lost stages, as mentioned below. Providing these details is optional, but you're highly encouraged to share them to get stage-appropriate help from Microsoft sales representatives in a Co-sell deal.

:::image type="content" source="media/pscmigration/solution-assessment-sale-stages.png" alt-text="Image showing the deal lifecycle where the sale stage can be marked.":::

> [!NOTE]
> Marking sales stage is **mandatory** for solution assessment deals. **Won** button will be enabled only after all the sales stages are marked as complete by the partner.

This table showing the sales stages and the corresponding percentages for solution assessments deals as determined by the Partner Center referrals system.

|**Sales stage name**|**Sales stage percentage**|**Definition of sales stage**|
|:----|:-----|:-----|
|Created|10%|Creating a solution assessment deal.|
|Accepted|10%|Accepting a solution assessment deal.|
|Secure customer LOE|20%||
|Collect data|40%||
|Prepare assessment report|60%||
|Present to customer|80%||
|Won|100%|Marking the deal as won.|

When you're finished, you can take one of the two actions, which are marking the deal as **Won** or **Lost** to report the outcome.

This is how Partner Center recognizes the deal sales stages and will automatically map the stages of your company to these standard stages if you're passing these values using the API. If you're using the Partner Center web portal, the percentages as shown in the table are used to mark the sales stages.

### Deal Registration Stage

For certain eligible solutions, after you select **Won**, you'll be asked to provide additional information to register your deal. Microsoft will review the info you provide here and may ask for more details during the review process. For more information, see [Register your deals.](register-deals.md)

### Closed stage

*Closed* is the final stage for all opportunities. You can view all the deals that are in **won, lost, declined**, and **expired** in the closed stage. There are no actions that you can take in this stage.

## Next steps

- [Solution Assessment FAQ](chip-faq.yml)

- [Solution Assessment eligibility](chip-solutions-assessment-eligible.md)

