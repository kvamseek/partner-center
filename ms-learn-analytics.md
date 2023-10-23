---
title: Use Microsoft Learn analytics reports
ms.topic: article
ms.date: 11/09/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-insights
description: Track the learners in your company by using data on individual training, completed modules, completed learning paths, and more.
author: kshitishsahoo
ms.author: ksahoo
---

# Use Microsoft Learn analytics reports

**Appropriate roles**: Global admin | MPN Partner Admin | Executive report viewer | Report viewer

The [Microsoft Learn](/training/) report gives you information on the learners in your company, including the modules they've completed and the learning paths they are on. The report displays the status of each individual learner. Global admins, Executive report viewer, Report viewer and MPN admins for a company can view the data.

## How to read the report

### Summary charts

These charts summarize count and monthly cumulative trends for trained individuals, module completions, and learning paths.

**Trained individuals count**: A count of all distinct learners who have completed at least one module during the selected date range

**Trained individuals trend mini chart**: Month over month cumulative count of the active learners

**Module completions count**: Count of Module completions by the learners in the partner's company during the selected date range.
For example,  if "Module 1" is completed by 15 people, and the "Module 2" has been completed by the same 15 people, the module completions count will be 30. The module completion date should fall in the date range selected.

**Module completions trend mini chart**: Month over month cumulative count of the module completions

**Learning path completions count**: Count of learning path completions by the learners in the partner's company during the selected date range.
For example, if learning path "Path 1" is completed by 20 people, and the learning path "path 2" has been completed by the same 20 people, the learning path completion count will be 40. The learning path completion date should fall within the selected date range.

**Learning path completions trend mini chart**: Month over month cumulative count of the learning path completions

### Trained individuals' monthly trend

This data is the trend of your company's users who have completed a module for the first time in that month.

**X-Axis** is month for the time filter selected.

**Y-Axis** is count of active learners who have registered (first-time completion of a module) during that month. It isn't cumulative.

### Module completions monthly trend

This data is the trend of modules completed by all your company's users during that month. It isn't cumulative.

**X-Axis** is month for the time filter selected.

**Y-Axis** is count of the module completions during that month. It isn't cumulative.

### Learning path completions monthly trend

This data is the trend of learning paths completed by your company's users during that month. It isn't cumulative.

**X-Axis** is month for the time filter selected.

**Y-Axis** is count of module completions in that month. It isn't cumulative.

### Learning path completion tabs

#### Module tab

This tab includes a breakdown of modules completed in your company by top five module names, the product with which the module is associated, and the user role pertinent to the module.

- Module completions donut chart: breakdown of the module completions (count displayed in the summary section) by the module names. The number displayed in the center of the chart is the total modules completed.

- Completions by role: breakdown of the module completions by the role of the module. If a module is associated with multiple roles, then each of the roles is added to the count of module completions. The number displayed in the center of the chart is the number of distinct roles for the module completions.

- Completions by product: breakdown of the module completions by the product the module is mapped to. If a module is associated with multiple products, then each of the products is added to the count of module completions. The number displayed in the center of the chart is the number of distinct products for the module completions.

#### Learning path tab

This tab includes a breakdown of learning paths completed in your company by top five module names; the product the learning path is mapped to; and the role pertinent to this learning path.

- Learning paths completions donut chart: breakdown of the learning path completions (count displayed in the summary section) by name.

- Completions by role: breakdown of the learning paths completions by the role. If a module is associated with multiple roles, each of the roles is added to the count of module completions.

- Completions by product: breakdown of the learning paths completions by the Product to which the learning path is mapped. If a module is associated with multiple products, then each of the products is added to the count of module completions.

### Completions by learning individuals

This lists the trained users in your company and details of their completed modules and learning paths.

Microsoft Learn identifies learners with a User Object ID. Under the **Modules tab**, all learners are sorted by the modules completed. They're displayed with their Microsoft Learn username, Object ID, and modules count. You can search using username.

Under the **Learning paths tab** all learners sorted by learning paths completed, are displayed with the learner display name, Object ID, and module count.

To get a learner's details using the User Object ID:

1. Sign in to [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer ). (You must be the global admin of your company's Azure AD tenant.)

2. Copy the user object ID to the area highlighted (`https://graph.microsoft.com/v1.0/users/a9633ad7-c8dc-4587-b119-0bc286b0711f`) in Graph Explorer.

## Frequently asked questions

### I'm unable to see my company's Learn details

   This report is available to partners who have an account in Partner Center. If you're still in Partner Membership Center, you'll not be able to see this report.

   > [!IMPORTANT]
   > Partner Membership Center (PMC) was retired in May 2022. For more information on the PMC program's retirement, [see here](partner-membership-center-retirement-faq.md).

### Who in my company can view this report?

   The global admin, the MPN admin, the executive report viewer and the report viewer can view the report.

### How can I make sure all our users associate their Microsoft Learn accounts with their Partner Center account?

   *After the global admin adds a new user*, that user must go to [Microsoft Learn](/training/) to link their Azure Active Directory (AD) corporate account or work account with their Microsoft Learn account. Doing so ensures that the Insights Learning tab shows the right courses and skills.

   The user needs to:

   1. Sign in to [Microsoft Learn](/training/).
   2. Select their profile picture, then select **My profile**.
   3. Select **Settings**.
   4. Under **Account management**, add their work account under **Linked accounts**.

### Can I see all the company's users who sign in to Microsoft Learn with an MSA account in this report?

   Currently, the best way to do this is to add these users to your Azure AD tenant and then add them to Partner Center so that they can associate their Microsoft Learn account through **My profile** in Partner Center.

   For users who only use their MSA account for training, soon the Microsoft Learn team will enable them to associate their work email with their Microsoft Learn profile.

## Next steps

- For more reports, see [Partner Center Insights](partner-center-insights.md).

> [!NOTE]
> You can download the raw data powering this report from the Download Reports section in the Insights dashboard. [Learn More](insights-download-reports.md)
