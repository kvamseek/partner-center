---
title: About leads
ms.topic: article
ms.service: partner-dashboard
ms.subservice: partnercenter-referrals
description: Use Partner Center to respond to leads and manage new, existing, and closed leads. Learn how to get more leads in the future.
author: pragneMS
ms.author: pragne
ms.date: 08/24/2023
ms.custom: engagement-fy23
---

# Learn about leads

**Appropriate roles**: Business profile admin | Referrals admin

> [!NOTE]
> The Leads page has a toggle for trying out the new view. Turning it on, will show you the new view in the Grid and details page as well. 
> For information about the page interactions - **Grid view**, see the [Referrals user guide](referrals-user-guide.md).

Microsoft sends millions of leads to its partners every year to help them to build their businesses. This article explains the leads you get from your customers and how to act on them.

## Types of leads

There are two types of leads: *profile leads* and *offer leads*.

- **Profile leads**: You receive *profile leads* when you [create a business profile](create-a-marketing-profile.md) for your company. The business profile you create helps you to be visible to prospective customers, to other partners, and to Microsoft sellers on the [AppSource](https://appsource.microsoft.com/marketplace/partner-dir) webpages. All the requests that originate from a profile listing on the AppSource page are available in the Partner Center **Referrals** workspace in the **Leads** section.

- **Offer leads**: You receive *offer leads* when you publish offers through the [commercial marketplace](/azure/marketplace/overview). Customers can browse offers that are listed on Microsoft marketplaces, such as [AppSource](https://appsource.microsoft.com), [Azure Marketplace](https://azuremarketplace.microsoft.com/), and [Azure portal marketplace](https://portal.azure.com/#view/Microsoft_Azure_Marketplace/MarketplaceOffersBlade/selectedMenuItemId/home). When they express an intent to acquire an offer, a lead is generated.

## Classifications of leads

Leads are classified as *marketing-qualified*, *sales-qualified*, or *customer inquiries*.

- **Marketing-qualified leads** are leads that are sent to your company by Microsoft employees who received customer requests through one of various marketing channels.

- **Sales-qualified leads** are leads that are sent to you by Microsoft sellers who gather the requirements from a customer and are helping them find the right partner to solve a customer problem. Sales-qualified leads aren't the same as [*co-sell opportunities*](manage-co-sell-opportunities.md), in which a Microsoft sales representative is actively engaged with the partner and customer until the deal closes.

- **Customer inquiries** are leads that originate directly from customers. You receive a customer inquiry when a company searches and finds your company profile or an offer description page and fills out a form stating the need and the contact details.

## Navigating leads

There are three parts of the [**Leads**](https://partner.microsoft.com/dashboard/opportunities/referral/leads) section of the **Referrals** workspace in Partner Center:

- **Marketplace leads** are customer inquiries originating from either the business profiles or offer pages on AppSource, Azure portal, or Azure Marketplace.

- **Qualified leads** are *Marketing qualified* and *Sales qualified* leads.

- **Favorites** are leads that you marked as favorites in the **Marketplace leads** or **Qualified leads** tabs.
  
  You can mark any lead as a favorite by selecting the heart icon on the lead in the list view. You can remove the lead from favorites by selecting the same icon again.

## Contact validation for Marketplace leads

The email addresses and phone numbers of Marketplace offer leads are validated to verify that they can be contacted. Validated contact information helps you prioritize which leads to reach out to and helps to ensure that your sales efforts are effective.

When you view a lead on the **Marketplace Leads** tab, you can see indicators of a valid phone number and valid email address:

:::image type="content" source="media/manage-leads/valid-contacts.png" alt-text="Screenshot of a marketplace offer lead in Partner Center with highlighted indicators that the phone number and email address are valid.":::

*Quick-copy icons* are handy shortcuts that can help to avoid typos when calling or emailing someone:

:::image type="content" source="media/manage-leads/quick-copy-icons.png" alt-text="Screenshot of a marketplace offer lead in Partner Center with quick copy icons highlighted.":::

You can also filter for leads that have valid email and phone numbers, as shown below. Filtering can help your outreach teams engage with customers more effectively, either with automated emails or direct phone calls.

:::image type="content" source="media/manage-leads/filter-validity.png" alt-text="Screenshot of filtering and sorting leads in Partner Center, with the email-validity sorting and phone validity sorting options highlighted.":::

Email addresses and domain names that are known to generate spam are marked as shown in the following image. They're also marked when you select the lead to view the details.

:::image type="content" source="media/manage-leads/spam-warnings.png" alt-text="Screenshot of a lead in Partner Center with spam warnings highlighted.":::

## Exporting leads

You can export leads from the **Referrals** workspace in Partner Center by using the **Export** button at the right top corner of the page.

:::image type="content" source="media/manage-leads/export-leads.png" alt-text="Screenshot of the Leads screen in Partner Center with the Export button highlighted.":::

If you have filters applied, the exported file will only have the filtered list of leads.

Other columns in the display indicate email and phone validity, so you can upload only valid contacts into your CRM systems for your sales teams.

The exported leads file has a field named `LeadCreationDateTime` that indicates when the exported leads were created.

## Responding to a lead

Every lead has a lifecycle. This section identifies the stages of that lifecycle—[*received*](#received-stage), [*accepted*](#accepted-stage), and [*archived*](#archived-stage)—and the actions that you can take at each stage.

> [!IMPORTANT]
> Marketplace leads that are generated when a customer selects calls-to-action (such as **Get it now**, **Free trial**, or **Test drive**) do not require any action from partners. These leads are informational and intended to help partners reach out to customers for cross-sell and up-sell opportunities. These leads are available for a period of 6 months for the partners to access and leads older than 6 months will be archived. 

### Received stage

At the *received* stage, you've received a new lead, either directly from a customer or from a Microsoft employee. Review the details, and feel free to contact the customer if you want to learn more about their business needs.

At the received stage, you can accept or decline a referral.

- **Accept**: When you accept a deal, enter a name for the deal, the estimated value, team members and the estimated purchase time frame. You should also provide information in the  **Notes** field to explain more about what the customer is looking for. You can optionally enter the marketing campaign ID that resulted in the respective lead and your CRM ID for your reference, and you can add more contacts from your company. When you're finished, select **Next**. We'll move the referral to the **next stage**, which means you plan to actively engage with the customer to address their need. We'll also use this information to help you find similar deals in the future.
- **Decline**: When you decline a deal, select the reason you're declining it, add any notes you'd like to include, and then select **Close**. The lead is then archived **Declined** and the customer is notified to choose a different partner.
- **Expired**: If you don't respond to a lead within 14 days, it's archived as **Expired**, and either Microsoft or the partner who sent you the opportunity are notified. Expired leads don't display contact information.

> [!TIP]
> A customer can explicitly request that interested partners contact them directly. When that happens, you'll see an alert with a flame icon at the top of the page. We strongly recommend that you contact the customer as quickly as possible to improve your chances of winning the deal. After 72 hours, the referral continues to be active, but the icon and message change. You should still contact the customer if you're interested in pursuing the referral.

### Filtering leads

Filters make it easier to get to a focused set of leads. This section describes each of the filters you can use.

| **Filter name** | **Description** |
|---------------|---------|
|**Call-to-action**| The call-to-action configured during the offer publish flow.<br>Possible values are *Get it now*, *Free Trial*, *Test drive,* and *Contact me*.|
|**Country**| Country/region selected by the customer when they gave consent for a partner to contact them|
|**Customer name**| Name of the customer company|
|**Lead source**| Name of the marketplace from which the lead originated.<br>Possible values are *AppSource*, *Azure Marketplace*, and *Azure portal*.|
|**Lead type**| The type of the lead.<br>*Offer* leads are generated for offers published through commercial marketplace.<br>*Profile* leads are generated for business profiles published in the referrals workspace|
|**Lead quality**| The conversion probability of the lead.<br>*High* denotes a higher chance of lead getting converted to a subscription.<br>*Low* denotes a potential spam lead.|
|**Status**| Life cycle status of the referral. Applicable only for *Profile* leads and *Contact me* leads in the *Offer* leads space.|
|**Email validity** | *Valid* implies that an email inbox exists. *Invalid* implies that it's a fake email address. Other statuses are *Spam* or *Unknown*. The *Email validity* filter is applicable only to *Offer* leads.|
|**Phone validity** | *Valid* implies that the phone number is reachable and registered. Other statuses are *Invalid* or *Unknown*. The *Phone validity* filter is applicable only to *Offer* leads.|

### Accepted stage

As you work to close a deal, if you want to change any of the information you've provided for an accepted referral, select **Edit**. You can then update the deal name, estimated purchase date, Team members, estimated value, notes, CRM ID, or the marketing campaign ID.  You can also select **Add your employees** to provide the name, phone number, and email addresses of any more people who are working on the deal.

When you're finished, mark the deal **Won** or **Lost**, so it can be archived accordingly.

### Archived stage

*Archived* is the last stage, which all the opportunities eventually reach. You can't take action on archived leads, but you can view their status: **Won**, **Lost**, **Declined**, or **Expired**.

## Email notifications

contact listed on the business profile in Partner Center receive email notifications when there are new leads received for your marketplace offers or your profile listing. These leads are delivered either as individual emails if you have a low volume of leads or in a digest format if you get more than 10 leads in a day. You can review these leads in Partner Center and respond to your customers quickly.

The following workflow shows how email is sent to partners from the Partner Center referrals system for new partner inbound referrals.

:::image type="content" source="media/referrals/noti-workflow.png" lightbox="media/referrals/noti-workflow.png" alt-text="Image showing the logic of how emails are sent to partners for new inbound referrals.":::

Additionally, we do show these details as recommended actions in the Action center panel (notifications icon on the top right corner) in Partner Center. We recommend that you check these actions often to be responsive to your leads.

*Note: Email notifications are only sent for 'Contact me' type of leads right now.*

## Considerations with leads

- *Microsoft doesn't verify the identity of referrals or whether the interest of referrals is legitimate*. Microsoft only verifies that you can contact the individual or company being referred in accordance with the details provided.

- Referrals shouldn't be construed as an endorsement by Microsoft of the company or individual being referred. It is your sole responsibility to take any actions necessary and appropriate to safeguard your company from fraud resulting from a referral.

## How to get more profile leads

Here are some tips to help you get more, appropriate referrals:

- **Choose keywords and preferences in your [business profile](create-a-marketing-profile.md) that represent your unique expertise and business model**. Remove keywords that could generate referrals you're not interested in. If you're not interested in dealing with businesses of a certain size, update that preference.
- **Review your contact information in your [business profile](create-a-marketing-profile.md) for each location**. Make sure your team gets incoming alerts.
- **Respond quickly to referrals**. When you respond in a timely fashion to incoming requests, we increase your visibility in future customer search results. Make sure your team responds quickly with your intent.
- **Be choosy about which deals you accept**. We monitor the types of deals that you accept and decline and use that information to help find you similar deals. Accepting deals that aren't a good fit doesn't improve your search results and could affect the quality of the leads you receive.
- **Report estimated deal sizes, closing dates, and the final status of your deals, whether won or lost**. We use that information to continue to provide you with quality referrals.

## Next steps

- [Leads enrichment insights](leads-enrichment-insights.md)
- [Leads FAQ](leads-FAQ.yml)
- [Manage co-sell opportunities](manage-co-sell-opportunities.md)
- [Get the co-sell connector for Dynamics 365 CRM](connector-dynamics.md)
- [Get the co-sell connector for Salesforce CRM](connector-salesforce.md)


