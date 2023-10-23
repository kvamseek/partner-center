---
title: How to create and sell offers to education customers
description: Learn how to create an education customer to sell offers to them in Partner Center. This article also includes confirming verification status for your education customer.
ms.topic: how-to
ms.date: 09/16/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
author: jischulz
ms.author: jischulz
ms.custom: engagement-fy23
---

# Create and sell offers to education customers in Partner Center

**Appropriate roles**: Global admin | Admin agent | Sales agent

This article explains how to create an education customer in Partner Center, so you can sell education offers to them.

It also describes how to view verification status and resubmit a verification request if necessary.

**Education offers are available for license-based services and perpetual software** such as Microsoft 365, Dynamics, and Intune. They aren't available for other offers, such as software subscriptions or Azure products.

## Create an education customer

> [!IMPORTANT]
> Microsoft verifies every newly created education customer tenant to ensure that they are qualified for education offers. To prevent delays caused by this verification process, be sure to enter the required information accurately and completely. For example, you can use an accreditation certificate or document from the governing body or a letter from the department, ministry, or board of education attesting academic eligibility.

To create an education customer, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Select **Add a customer**.

3. From the **Special qualifications** dropdown, select **Education**.

4. Enter account information as required.  Key information for the verification process includes:

   - **Company name**: Enter the legal entity name. (Required for verification)
   - **Country/region and Address lines**: Enter the entity's full mailing address. (Required for verification).
   - **Email address**:  Enter the entity's email address (which can't be a free or on.microsoft.com email address). (Required for verification)
   - **Education Segment**: Enter the entity's educational segment. (Required for verification)
   - **Customer contact information** (Required for verification)
   - **Primary domain name**: Enter a name similar to the company name with no spaces or special characters, for example *contosoforedu* for *Contoso Elementary School*. This information is used to create the customer's account and email addresses and can't be changed later.
   - **Education website**: Enter an official website for the entity. This information help to expedite the vetting process.

5. When you're finished, select **Review**.

   :::image type="content" source="media/sell-to-education-customers/education-account-info.png" lightbox="media/sell-to-education-customers/education-account-info.png" alt-text="Screenshot of company account info page in Partner Center.":::

   After you select **Review**, you'll receive an **InReview** status if the information submitted is valid.

    :::image type="content" source="media/sell-to-education-customers/create-review.png" alt-text="Screenshot of the Confirmation page with customer account information in Partner Center."lightbox="media/sell-to-education-customers/create-review-expanded.png":::

### Confirm verification of your education customer's educational status

To confirm your education customer's verification status, use the following step:

- On the customer's **Account** page, view **Special qualification status**.

Examples of customer status in **Special qualifications**:

- If the customer passed verification, **Special qualifications** says **Education**.

   :::image type="content" source="media/sell-to-education-customers/education-passed-vetting.png" lightbox="media/sell-to-education-customers/education-passed-vetting.png" alt-text="Screenshot of an Account page in Partner Center when education verification was successful.":::

- If the customer's status is *in review*, **Special qualifications** says **in Review since (date)**.

    :::image type="content" source="media/sell-to-education-customers/in-review.png" alt-text="Screenshot of an Account page in Partner Center when an education customer is in review." lightbox="media/sell-to-education-customers/in-review-expanded.png":::

- If the customer information failed verification, **Special qualifications** says **Not an education customer**.

   :::image type="content" source="media/sell-to-education-customers/fail-reason.png" alt-text="Screenshot of an Account page in Partner Center when education verification wasn't successful." lightbox="media/sell-to-education-customers/fail-reason-expanded.png":::

- If the customer wasn't tagged as an eduction customer, **Special qualifications** says **None**.

   :::image type="content" source="media/sell-to-education-customers/account-one.png" alt-text="Screenshot of an Account page in Partner Center when an education customer isn't tagged as such." lightbox="media/sell-to-education-customers/account-one-expanded.png":::

## Correct the customer account information

If your customer information failed the initial verification, you can correct the information and resubmit it using the information in the following sections.

- You must have Global admin privileges to update a customer's information.

- You must update the information at the Microsoft 365 portal because this data can't be updated at Partner Center.

To correct customer account information, use the following steps:

   On the **Account** page, you'll see the statement, *Not an education customer*.

1. Refresh your browser to reset the page.

   The **Update** button appears, and the **Special qualifications status** is set to **None**.

2. Select **Update**.

3. On the **Service Management** page, select **Office 365**.

   You're redirected to the Microsoft 365 Admin Center on a new tab of your browser. You might be required to sign in.

4. Select **Settings**.

5. Select the **Organization profile** tab at the top of the screen and then **Organization information**.

   You can now update the customer details.

6. Select **Save changes** at the bottom of the sidebar.

## Resubmit the customer information for verification

To resubmit the customer information for verification, use the following steps:

1. Go to your Partner Center tab and to the customer **Account** page.

2. Refresh the browser and verify that the **Company** page was updated with the new information.

3. Select the **Update** button to request reverification of eduction status.

   If the updated customer details are eligible for education offers, you'll see the **Special qualifications** updated to **Education**.

   If you still see **Not an Education Customer**, contact Support for manual verification.

## Next steps

- [Sell to specialized industries](get-special-pricing-for-offers.md)

- [Add a new customer](add-a-new-customer.md)

- [Sell Minecraft: Education Edition subscriptions to education customers](minecraft-subscriptions.md)
