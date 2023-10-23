---
title: Detect and respond to security alerts
description: Understand Azure fraud notification and detect and respond to security alerts.
ms.topic: article
ms.service: partner-dashboard
ms.subservice: partnercenter-account
author: vijay-vala
ms.author: vijvala
ms.date: 09/27/2023
---

# Detect and respond to security alerts

**Appropriate roles**: Admin agent

**Applies to**: Partner Center  Direct Bill and Indirect Providers

Starting from May 2023, you can subscribe to a new security alert for detections related to unauthorized party abuse and account takeovers. This security alert is one of the many ways Microsoft provides the data you need to secure your customer's tenants.

> [!IMPORTANT]
> As a partner in the Cloud Solution Provider (CSP) program, you're responsible for your customers' Azure consumption, so it's important that you're aware of any anomalous usage in your customer’s Azure subscriptions. Use Microsoft Azure security alerts to detect patterns of fraudulent activities and misuse in Azure resources to help reduce your exposure to online transaction risks.  Microsoft Azure security alerts don't detect all types of fraudulent activities or misuse, so it's critical that you use additional methods of monitoring to help detect anomalous usage in your customer’s Azure subscriptions. To learn more, see [Managing nonpayment, fraud, or misuse](./non-payment-fraud-misuse.md) and [Managing customer accounts](non-payment-fraud-misuse.md#manage-customer-accounts).

**Action required:** With monitoring and signal awareness, you can take immediate action to determine whether the behavior is legitimate or fraudulent. If necessary, you can suspend affected [Azure resources](/azure/cost-management-billing/manage/cancel-azure-subscription) or [Azure subscriptions](./azure-plan-manage.md#cancel-an-azure-subscription) to mitigate an issue.

Make sure that the [preferred email address for your Partner Admin Agents](./security-contact.md#update-security-contact-information-for-your-csp-partner-tenant) is up-to-date, so they can be notified along with the security contacts.

## Subscribe to security alert notifications

You can subscribe to various partner notifications based on your role.

Security alerts notify you when your customer's Azure subscription shows possible anomalous activities.

### Get alerts by email

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Notifications** (bell).
1. Select [My preferences](./action-center-overview.md#preferences).
1. Set a preferred email address if you haven't already done so.
1. Set the preferred language for the notification if you haven't already done so.
1. Select **Edit** next to **Email notification preferences**.
1. Check all boxes relating to **Customers** in the **Workspace** column. (To unsubscribe, unselect the transactional section under customer workspace.)
1. Select **Save**.

We send security alerts when we detect possible security alert activities or misuse in some of your customers' Microsoft Azure subscriptions. There are three types of emails:

- **Daily summary of unresolved security alerts** (count of partners, customers and subscriptions impacted by various alert types)
- **Near real-time security alerts**. To get a list of Azure subscriptions that have potential security concerns, see [Get fraud events](./developer/get-fraud-events.md).
- **Near real-time security advisory notifications**. These notifications provide visibility into the notifications sent to the customer when there's a security alert.

CSP direct bill partners can see additional alerts for activities, for example: anomalous compute usage, crypto mining, Azure Machine Learning usage and service health advisory notifications.

### Get alerts through a webhook

Starting from January 2023, partners can register to a webhook event: ```azure-fraud-event-detected``` to receive alerts for resource change events. To learn more, see [Partner Center webhook events](./developer/partner-center-webhooks.md).

### See and respond to alerts through the Security Alerts dashboard

Starting from May 2023, CSP partners can access the Partner Center [Security Alerts dashboard](https://partner.microsoft.com/dashboard/commerce2/insights/security/alerts) to detect and respond to alerts. To learn more, see [Respond to security events with Partner Center Security Alerts dashboard](security-alerts-dashboard.md).

### Get alert details through API

As of May 2023, CSP partners can use the FraudEvents API to get additional detection signals using X-NewEventsModel. With this model, you can get new types of alerts as they're added to the system, for example, anomalous compute usage, crypto mining, Azure Machine Learning usage and service health advisory notifications. New types of alerts will be added with limited notice, because threats are also evolving. If you use special handling through the API for different alert types, monitor these APIs for changes:

  - [Get fraud events](./developer/get-fraud-events.md#rest-request-with-the-x-neweventsmodel-header)
  - [Update fraud event status](./developer/update-fraud-events-status.md#rest-request-with-the-x-neweventsmodel-header)

## What to do when you receive a security alert notification

The following checklist provides suggested next steps for what to do when you receive a security notification.

- Check to make sure the email notification is valid. When we send security alerts, they're sent from **Microsoft Azure**, with the email address: ```no-reply@microsoft.com```. Partners only receive notification from Microsoft.
- When you're notified, you can also see the email alert in the Action Center portal. Select the bell icon to see the Action Center alerts.
- Review the Azure subscriptions. Determine whether the activity in the subscription is legitimate and expected, or whether the activity may be due to unauthorized abuse or fraud.
- Let us know what you found, either through the Security Alerts dashboard or from the API. To learn more about using the API, see [Update fraud event status](./developer/update-fraud-events-status.md). Use the following categories to describe what you found:
  - **Legitimate** - The activity is expected or a false positive signal.
  - **Fraud** - The activity is due to unauthorized abuse or fraud.
  - **Ignore** - The activity is an older alert and should be ignored. To learn more, see [Why are partners receiving older Security Alerts?](#why-are-partners-receiving-older-azure-security-alerts).

## What additional steps can you take to lower the risk of compromise?

- Enable multifactor authentication (MFA) on your customer and partner tenants. Accounts that have permissions to manage customers' Azure subscriptions need to be MFA compliant. To learn more, see [Cloud Solution Provider security best practices](csp-security-best-practices.md#require-multifactor-authentication) and [Customer security best practices](customer-security-best-practices.md).
- Set up alerts to monitor your Azure role-based access control (RBAC) access permissions on customers' Azure subscriptions. To learn more, see [Azure plan - Manage subscriptions and resources](azure-plan-manage.md#confirm-that-you-have-admin-access).
  - Audit permission changes on your customers' Azure subscriptions. Review the [Azure Monitor activity log](/azure/azure-monitor/essentials/activity-log?tabs=powershell) for Azure subscription-related activity.
- Review spending anomalies against your spending budget in [Azure cost management](/azure/cost-management-billing/costs/quick-acm-cost-analysis).
- Educate and work with the customers to reduce the unused quota to prevent the damage allowed on the Azure subscription: [Quotas overview - Azure Quotas](/azure/quotas/quotas-overview).
  - Submit request to manage Azure quota: [How to create an Azure support request - Azure supportability](/azure/azure-portal/supportability/how-to-create-azure-support-request)
  - Review the current quota usage: [Azure Quota REST API Reference](/rest/api/reserved-vm-instances/quotaapi)
  - If you're running critical workloads that require high capacity, consider [on-demand capacity reservation](/azure/virtual-machines/capacity-reservation-overview) or [Azure reserved virtual machine instances](https://azure.microsoft.com/pricing/reserved-vm-instances/)

## What should you do if an Azure subscription has been compromised?

Take immediate action to protect your account and data. Here are a few suggestions and tips to quickly respond and contain a potential incident to reduce its impact and overall business risk.

**Remediating compromised identities** in a cloud environment is crucial for ensuring the overall security of cloud-based systems. Compromised identities can provide attackers with access to sensitive data and resources, making it essential to take immediate action to protect the account and data.

- Immediately change credentials for:

  - Tenant admins and RBAC access on Azure Subscriptions [What is Azure role-based access control (Azure RBAC)?](/azure/role-based-access-control/overview)
  - Follow the password guidance. [Password policy recommendations](/microsoft-365/admin/misc/password-policy-recommendations)
  - Ensure all the tenant admins and RBAC owners have [MFA registered and enforced](./csp-security-best-practices.md#require-multifactor-authentication)
- Review and verify all global admin user password recovery emails and phone numbers within Azure Active Directory. Update them if necessary. [Password policy recommendations](/microsoft-365/admin/misc/password-policy-recommendations)
- Review which users, tenants, and subscriptions are at risk within the [Azure portal](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/UsersAtRisk).
  - Investigate the risk by going to Azure Active Directory to review Identity Protection’s [Risk Reports](/azure/active-directory/identity-protection/howto-identity-protection-investigate-risk#risky-users). To learn more, see [Investigate risk Azure AD identity protection](/azure/active-directory/identity-protection/)
  - [License Requirements for Identity Protection](/azure/active-directory/identity-protection/overview-identity-protection#license-requirements)
  - [Remediate risks and unblock users](/azure/active-directory/identity-protection/howto-identity-protection-remediate-unblock)
  - [User experiences with Azure AD Identity Protection](/azure/active-directory/identity-protection/concept-identity-protection-user-experience)
- Review the [Azure Active Directory Sign-in logs](/azure/active-directory/reports-monitoring/concept-all-sign-ins) on the customer tenant to see unusual sign-in patterns around the time when the security alert is triggered.

After the malicious actors have been evicted, **clean the compromised resources**. Keep a close eye on the impacted subscription to make sure there's no further suspicious activity. It's also a good idea to regularly review your logs and audit trails to ensure that your account is secure.

- Check for any unauthorized activity in the [Azure Activity Log](/azure/azure-monitor/essentials/activity-log?tabs=powershell), for example, changes to our billing, usage for [unbilled commercial consumption line items](./developer/get-invoice-unbilled-consumption-lineitems.md), or configurations.
- Review spending anomalies against the customer's spending budget in [Azure cost management](/azure/cost-management-billing/costs/quick-acm-cost-analysis).
- Disable or delete any compromised resources:
  - Identify and evict the threat actor: [Use Microsoft and Azure security resources to help recover from systemic identity compromise](/azure/security/fundamentals/recover-from-identity-compromise).
  - Check the [Azure Activity Log](/azure/azure-monitor/essentials/activity-log?tabs=powershell) any subscription-level changes.
  - Deallocate and remove any resources created by unauthorized party. Watch [How to keep your Azure subscription clean | Azure Tips and Tricks](https://youtu.be/EigjR891PIM) (video)
  - You can cancel the customers' Azure subscriptions through [this API](/rest/api/partner-center/azure-spending/cancel-an-azure-entitlement) or through the Partner Center portal.
  - Contact Azure support immediately and report the incident
  - Clean up storage after the event: [Find and delete unattached Azure managed and unmanaged disks - Azure Virtual Machines](/azure/virtual-machines/windows/find-unattached-disks)

Preventing account compromise is easier than recovering from it. Therefore, it's important to **strengthen your security posture**.

- Review the quota on the customers Azure subscriptions and submit the request to reduce the unused quota. For more information, see [Reduce Quota](/rest/api/reserved-vm-instances/quotaapi).
- Review and implement the [Cloud Solution Provider security best practices](csp-security-best-practices.md).
- Work with your customers to learn and implement the [Customer security best practices](customer-security-best-practices.md).
- Make sure **Defender for Cloud** is [turned on](/azure/defender-for-cloud/concept-cloud-security-posture-management#defender-cspm-plan-options) (There's a free tier available for this service).

## More tools for monitoring

- [Set up alerts from the Azure portal](/azure/azure-monitor/alerts/alerts-create-new-alert-rule?tabs=metric)
- [Set an Azure spending budget for customers](./set-an-azure-spending-budget-for-your-customers.md)

## How to prepare your end customers

Microsoft sends notifications to Azure subscriptions, which go to your end customers. Work with your end customer to ensure that they can act appropriately and are alerted of various security issues within their environment:

- Set up **usage alerts** with **[Azure Monitor](/azure/azure-monitor/alerts/alerts-create-new-alert-rule?tabs=metric)** or **Azure Cost management**.
- Set up [**Service Health Alerts**](/azure/service-health/service-health-overview#service-health-events) to be aware of other notifications from Microsoft about security and other related issues.
- Work with your organization's Tenant Admin (if this isn't managed by the Partner) to enforce increased security measures on your tenant (see the following section).

### Additional information for protecting your tenant

- Review and implement [operational security best practices for your Azure assets](/azure/security/fundamentals/operational-best-practices).
- **Enforce [Multi-Factor Authentication](/azure/security/fundamentals/identity-management-best-practices#enforce-multi-factor-verification-for-users)** to strengthen your identity security posture.

- **Implement risk policies and alerting for High Risk users and sign-ins:** [What is Azure Active Directory Identity Protection?](/azure/active-directory/identity-protection/overview-identity-protection).

If you suspect unauthorized usage of your or your customer's Azure subscription, engage [Microsoft Azure Support](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview) so Microsoft can help expedite any other questions or concerns.

If you have specific questions regarding Partner Center, submit a support request in Partner Center. For more information: [Get support in Partner Center](./report-problems-with-partner-center.md).

## Check security notifications under Activity logs

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select the settings (gear) icon on top right corner, then select the **Account settings** workspace.
1. Navigate to **Activity logs** on the left panel.
1. Set the **From** and **To** dates in the top filter.
1. In **Filter by Operation Type**, select **Azure Fraud Event Detected**.
   You should be able to see all security alerts  Events detected for the selected period.

## Why are partners receiving older Azure security alerts?

Microsoft has been sending Azure Fraud alerts since December 2021. However, in the past, alert notification was based on opt-in preference only, where partners had to opt in to receive notice. We’ve changed this, so partners should resolve all fraud alerts (including old alerts) that are open.Follow the [Cloud Solution Provider security best practices](./csp-security-best-practices.md) to secure your and your customers’ security posture.

Microsoft is sending the daily fraud summary (this is the count of partners, customers and subscriptions impacted) if there's an active unresolved fraud alert within the last 60 days.

## Why am I not seeing all the alerts?

Security alert notifications are limited to detecting patterns of certain anomalous actions in Azure. Security alert notifications don't detect and aren't guaranteed to detect all anomalous behaviors. It's critical that you use other methods of monitoring to help detect anomalous usage in your customer's Azure subscriptions, such as monthly Azure spending budgets. If you have noticed an alert that is significant and is a false negative, reach out to [Partner Center Support](report-problems-on-behalf-of-a-customer.md) and provide the following information:

- Partner Tenant ID
- Customer Tenant ID
- Subscription ID
- Resource ID
- Impact start and impact end dates

## Next steps

- Integrate with the [Security Alerts API and register a webhook](./developer/get-fraud-events.md).
