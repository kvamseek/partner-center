---
title: Report problems on behalf of a customer
ms.topic: how-to
ms.date: 9/23/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-support
description: Learn when to escalate a customer service problem to Microsoft and how to file a support ticket for different types of Microsoft services.
author: jgray42
ms.author: juliegray
---

# Report a service problem on behalf of a customer - including when and how to do so

**Applies to**: Partner Center | Partner Center for Microsoft Cloud for US Government

**Appropriate roles**: See [GDAP role guidance](./gdap-least-privileged-roles-by-task.md)

If your customer has a service problem you can't resolve, you as an Advisor, Indirect Reseller, CSP Direct or Indirect Provider (Disti, CSP Tier II) can [file a support ticket for the customer](report-problems-on-behalf-of-a-customer.md).

Service requests should be filed through Partner Center. They're available for Azure, Microsoft Office 365, Microsoft Dynamics CRM Online, and Enterprise Mobility Suite. As a partner participating in the Cloud Solution Provider program, you can expect your major issues to receive priority for a response.

Support for your own partner tenant isn't included as part of the CSP support benefit. However, Office 365, Microsoft Dynamics CRM Online, and Enterprise Mobility Suite don't charge a separate support subscription fee for partners or customers. Azure does charge a fee but if you're entitled to Signature Cloud Support or other Microsoft AI Cloud Partner Program benefits, you can use those benefits to pay that fee. This benefit applies to all partners participating in the Cloud Solution Provider program, whether paid or during a trial period. Billing and subscription management support is also included as a free component of this package.

## Perform administrative tasks for your customers

As a Cloud Solution Provider (CSP) partner, you have Delegated Admin Privileges that give you access to your customers' environments. These privileges provide you with the ability to directly support, configure, and manage your customers' subscriptions.

In Partner Center, you can:

- View customer service health.
- View customer service incidents.

1. From the **Partner Center** menu, select **Customers**. Choose your customer from the list.
2. In the customer menu, select **Service management**.
3. In the **Administer services** section, choose the service you need to work in to open the management portal for the service.
4. If you find a problem with a customer's account, like services being down or a degraded experience, start by checking the service health. See Check service health.
5. To escalate an ongoing problem to Microsoft, file a service request. See Report problems on behalf of a customer.

### How quickly will I get an initial response?

Initial response times depend on the severity of the incident submitted. The severity of an issue is determined by your indication of business impact when you submit a service request.

Initial response times for **technical break-fix incidents**:

| **Impact** | **Severity**                                                                                             | **Time for initial response \*** |
| ---------- | -------------------------------------------------------------------------------------------------------- | -------------------------------- |
| Critical   | A: Significant loss or degradation of services. Production services down.                                | Two hours                        |
| Moderate   | B: Moderate loss or degradation of services. Production services partially affected.                     | Four hours                       |
| Minimal    | C: Minimal loss or degradation of services. Services still available or nonproduction services affected. | Eight hours                      |

**Initial response times are for English-speaking support only. Local language support is provided during business hours. For incidents that fall within the boundaries of the support entitlement but aren't considered break-fix incidents, the initial response time may be up to one business day.*

### Submit a service request in Microsoft Azure

> [!IMPORTANT]
> Indirect resellers and/or Advisors can't open support requests on customer's behalf in the Azure portal, even if they have a support contract. A support request can only be created by the provider of the Azure Subscription (either CSP Direct or Indirect Provider) in this particular case.

To submit a service request for a customer in Microsoft Azure:

1. Select **New support request**.

2. Enter the required information in the request.

   - In the **Basics** section, be sure to select **Cloud Solution Provider** in the **Support plan** field.

   - In the **Contact** information section, enter *your* contact information, not your customer's information.

3. Select **Create**.

4. Later, you can review your customer's service requests at the Microsoft Azure portal by selecting **Manage support requests**.

**Submit a support request in Microsoft Azure when you don't have administrator permissions for the customer*

### Create a service request in Office 365, Enterprise Mobility Suite, and Microsoft Dynamics CRM Online

To create a service request in Office 365, Enterprise Mobility Suite, and Microsoft Dynamics CRM Online:

1. In the **Create a service request** section, choose the appropriate support category.

   (You might need to select **More...** to view more articles.)

2. Complete the service request form and select **Submit**.

   > [!TIP]
   > Be sure to enter *your* contact information on the form, not your customer's.

3. Later, review your customer's service requests by going to the Microsoft 365 admin center and selecting **See all support tickets**.

### Support for commercial marketplace products

Microsoft doesn't provide product support for commercial marketplace products. You need to contact the independent software vendor (ISV) who published the product to get support.

To find an ISV's contact info:

1. On the **Marketplace** page, select the product that you need help with.

2. On the product's page, you find support contact info. This information might be in one or more of the following forms:

    - A link to a support entry point on the ISV's website
    - A support email address
    - A support contact phone number

### What happens if I sign into  Azure or Microsoft 365 admin center portals and bypass Partner Center?

When you sign into [Microsoft Azure](https://ms.portal.azure.com/#home) or [Microsoft 365 admin center](https://admin.microsoft.com/adminportal/home?#/homepage) portals directly, you're viewing those experiences in your own context, not a customer's context. For that reason, the only time you should sign-in to the Microsoft Azure portals directly is when you're a creating a service request for your own subscriptions.

Your CSP program support entitlement doesn't provide support for your own partner subscription. Because of this limitation, you need to provide your valid support plan entitlement when you create a service request that concerns your own partner subscription. Examples include Microsoft AI Cloud Partner Program contract ID, Premier, or an Azure support plan. For more information, see the Azure Support FAQ.
