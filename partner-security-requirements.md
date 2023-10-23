---
title: Partner security requirements
ms.topic: article
ms.date: 10/13/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-account
description: Introduces partner security requirements to enable multifactor Authentication (MFA) and adopt the Secure Application Model framework - Account settings workspace.
author: vijay-vala
ms.author: vijvala
---

# Security requirements for using Partner Center or Partner Center APIs

**Appropriate roles**: All Partner Center users

As an advisor, control panel vendor, or Cloud Solution Provider (CSP) partner, you have decisions to make regarding authentication options and other security considerations.

Privacy safeguards and security for you and your customers are among our top priorities. We know that the best defense is prevention and that we're only as strong as our weakest link. That's why we need everyone in our ecosystem to ensure appropriate security protections are in place.

## Mandatory security requirements

The CSP program allows customers to buy Microsoft products and services through partners. In accordance with their agreement with Microsoft, partners are required to manage the environment for and provide support to the customers they sell to.

Customers who buy through this channel place their trust in you as a partner because you have high-privilege admin access to the customer tenant.

Partners who don't implement the mandatory security requirements won't be able to transact in the CSP program or manage customer tenants using delegated admin rights. In addition, partners who don't implement the security requirements might put their participation in programs at risk.

The terms associated with the partner security requirements have been added to the Microsoft Partner Agreement. The Microsoft Partner Agreement (MPA) is updated periodically, and Microsoft recommends that all partners check back regularly. As it relates to Advisors, the same contractual requirements will be in place.

All partners are required to adhere to [security best practices](./csp-security-best-practices.md) so they can secure partner and customer environments. Adhering to these best practices helps mitigate security issues and remediate security escalations, ensuring the customer's trust isn't compromised.

To protect you and your customers, we require that partners to take the following actions immediately:

- [Enable MFA for all user accounts](#enable-mfa-for-all-user-accounts-in-your-partner-tenant)
- [Adopt the Secure Application Model framework](#adopt-the-secure-application-model-framework)

### Enable MFA for all user accounts in your partner tenant

You must enforce MFA on all user accounts in your partner tenants. Users must be challenged by MFA when they sign in to Microsoft commercial cloud services or when they transact in the Cloud Solution Provider program through Partner Center or via APIs.

MFA enforcement follows these guidelines:

- Partners who use Microsoft-supported Microsoft Azure Active Directory (Azure AD) multifactor authentication. For more information, see [Multiple ways to enable Azure AD MFA](/azure/active-directory/fundamentals/concept-fundamentals-mfa-get-started) (**MFA supported**)
- Partner who implemented any third-party MFA and part of the exception list can still access Partner Center and APIs with exceptions but can't manage customer using DAP/GDAP (no exceptions allowed)
- If the partner's organization was previously granted an exception for MFA, users who manage customer tenants as part of the CSP program must have enabled Microsoft MFA requirements before March 1, 2022. Failure to comply with MFA requirements may result in the loss of customer tenant access.
- Learn more about [mandating multifactor authentication (MFA) for your partner tenant](./partner-security-requirements-mandating-mfa.md).

### Adopt the Secure Application Model framework

All partners integrating with Partner Center APIs must adopt the [Secure Application Model framework](/partner-center/develop/enable-secure-app-model) for any app and user auth model applications.

> [!IMPORTANT]
> We strongly recommend that partners implement the Secure Application Model for integrating with a Microsoft API, such as Azure Resource Manager or Microsoft Graph, or when leveraging automation such as PowerShell using user credentials, to avoid any disruption when MFA is enforced.

These security requirements help protect your infrastructure and safeguard your customers' data from potential security risks such as identify theft or other fraud incidents.

## Other security requirements

Customers trust you, as their partner, to provide value-added services. It's imperative that you take all security measures to protect the customer's trust and your reputation as a partner.

Microsoft continues to add enforcement measures so that all the partners are required to adhere to and prioritize the security of their customers. These security requirements help protect your infrastructure and safeguard your customers' data from potential security risks, such as identify theft or other fraud incidents.

The partner is responsible for ensuring they're adopting the principles of zero trust, specifically the following.

### Delegated Admin Privileges (DAP)

Delegated admin privileges (DAP) provide the capability to manage a customer's service or subscription on their behalf. The customer must grant the partner administrative permissions for that service. Since the privileges provided to the partner to manage the customer are highly elevated, Microsoft recommends that all partners [remove inactive DAPs](./dap-monitor-self-serve-removal.md). All partners managing the customer tenant using Delegated Admin Privileges should remove inactive DAP from the [Partner Center](https://partner.microsoft.com/dashboard/home) to prevent any impact on the customer tenant and their assets.

For more information, see the [Monitoring administrative relationships and self-service DAP removal guide](./dap-monitor-self-serve-removal.md), the [Delegated administration privileges FAQ](./dap-faq.md), and the [NOBELIUM targeting delegated administrative privileges guide](https://www.microsoft.com/security/blog/2021/10/25/nobelium-targeting-delegated-administrative-privileges-to-facilitate-broader-attacks/).

Additionally, DAP will be deprecated soon. We strongly encourage all partners who are actively using DAP to manage their customer tenants and move towards a least privilege [Granular Delegated Admin Privileges model](./gdap-least-privileged-roles-by-task.md) to securely manage their customers' tenants.

### Transition to least privilege roles to manage your customer tenants

Because DAP will be deprecated soon, Microsoft highly recommends moving away from the current DAP model (which gives Admin agents standing or perpetual Global admin access) and replacing it with a fine-grained delegated access model. The fine-grained delegated access model reduces security risks to customers and the effects of those risks on them. It also gives you control and flexibility to restrict access per customer at the workload level of your employees who are managing your customers' services and environments.

For more information, see the [Granular delegated admin privileges (GDAP) overview](./gdap-introduction.md), information on [least-privileged roles](./gdap-least-privileged-roles-by-task.md), and the [GDAP FAQ](./gdap-faq.md)

### Watch for Azure fraud notifications

As a partner in the CSP program, you're responsible for your customer's Azure consumption, so it's important that you're aware of any potential cryptocurrency mining activities in your customers' Azure subscriptions. This awareness enables you to take immediate action to determine whether the behavior is legitimate or fraudulent and, if necessary, suspend the affected Azure resources or Azure subscription to mitigate the issue.

For more information, see [Azure fraud detection and notification](./azure-fraud-notification.md).

### Sign up for Azure AD Premium Plan 2

All Admin Agents in the CSP tenant should strengthen their cybersecurity by implementing  [Azure AD Premium Plan 2](https://partner.microsoft.com/resources/detail/cybersecurity-with-azure-ad-pdf), and take advantage of the various capabilities to strengthen your CSP tenant. Azure AD Premium Plan 2 provides extended access to sign-in logs and premium features such as Azure AD Privileged Identity Management (PIM) and risk-based Conditional Access capabilities to strengthen security controls.

### Adhere to CSP security best practices

It's important to follow all CSP best practices for security. Learn more at [Cloud Solution Provider security best practices](./csp-security-best-practices.md).

## Implementing multifactor authentication

To comply with the partner security requirements, you must implement and enforce MFA for each user account in your partner tenant. You can do this one of the way following ways:

- Implement [Azure Active Directory (Azure AD) security defaults](/azure/active-directory/conditional-access/concept-conditional-access-security-defaults). See more in the next section, [Security defaults](#security-defaults).

- Purchase Azure Active Directory Premium for each user account. For more information, see [Plan an Azure AD multifactor authentication deployment](/azure/active-directory/authentication/howto-mfa-getstarted).

### Security defaults

One of the options that partners can choose to implement MFA requirements is to enable security defaults in Azure AD. Security defaults offer a basic level of security at no extra cost. Review how to enable MFA for your organization with Azure AD and the key considerations below before enabling security defaults.

- Partners who already adopted baseline policies need to take action to transition to security defaults.

- Security defaults are the general availability replacement of the preview baseline policies. After a partner enables the security defaults, they can't enable baseline policies.

- With security defaults, all policies are enabled at once.

- For partners who use [conditional access](/azure/active-directory/conditional-access/concept-conditional-access-policy-common), [security defaults aren't available](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults#disabling-security-defaults).

- Legacy authentication protocols are blocked.

- The Azure AD Connect synchronization account is excluded from security defaults and won't be prompted to register for or perform multifactor authentication. Organizations shouldn't use this account for other purposes.

For detailed information, see [Overview of Azure AD multifactor authentication for your organization](/azure/active-directory/authentication/concept-mfa-get-started) and [What are security defaults?](/azure/active-directory/conditional-access/concept-conditional-access-security-defaults).

> [!NOTE]
> Azure AD security defaults is the evolution of the baseline protection policies simplified. If you have already enabled the baseline protection policies, then it is highly recommended that you enable [security defaults](/azure/active-directory/conditional-access/concept-conditional-access-security-defaults).

## Implementation frequently asked questions (FAQ)

Because these requirements apply to all user accounts in your partner tenant, you need to consider several things to ensure a smooth deployment. For example, identify user accounts in Azure AD that can't perform MFA, and applications and devices in your organization that don't support modern authentication.

Before performing any action, we recommend that you complete the following validations.

### Do you have an application or device that doesn't support the use of modern authentication?

When you enforce MFA, legacy authentication use protocols such as IMAP, POP3, SMTP, and others are blocked because they don't support MFA. To address this limitation, use the [app passwords](/azure/active-directory/authentication/howto-mfa-mfasettings#app-passwords) feature to ensure that the application or device will still authenticate. Review the [considerations for using app passwords](/azure/active-directory/authentication/howto-mfa-mfasettings#considerations-about-app-passwords) to determine if they can be used in your environment.

### Do you have Office 365 users with licenses associated with your partner tenant?

Before implementing any solution, we recommend that you determine which versions of Microsoft Office users in your partner tenant are using. There's a chance your users will experience connectivity issues with applications like Outlook. Before enforcing MFA, it's important to ensure that you're using Outlook 2013 SP1, or later, and that your organization has modern authentication enabled. For more information, see [Enable modern authentication in Exchange Online](/exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online).

To enable modern authentication for devices running Windows that have Microsoft Office 2013 installed, you must create two registry keys. See [Enable Modern Authentication for Office 2013 on Windows devices](/office365/admin/security-and-compliance/enable-modern-authentication).

### Is there a policy preventing any of your users from using their mobile devices while working?

It's important to identify any corporate policy that prevents employees from using mobile devices while working because it will influence what MFA solution you implement. There are solutions, such as the one provided through the implementation of [Azure AD security defaults](/azure/active-directory/conditional-access/concept-conditional-access-security-defaults), that only allow the use of an authenticator app for verification. If your organization has a policy preventing the use of mobile devices, then consider one of the following options:

- Deploy a time-based one-time base password (TOTP) application that can run on secure system.

### What automation or integration do you have to use user credentials for authentication?

Enforcement of MFA for each user, including service accounts, in your partner directory, can affect any automation or integration that uses user credentials for authentication. So it's important that you identify which accounts are being used in these situations. See the following list of sample applications or services to consider:

- Control panel used to provision resources on behalf of your customers

- Integration with any platform that is used for invoicing (as it relates to the CSP program) and supporting your customers

- PowerShell scripts that use the Az, AzureRM, Azure AD, MSOnline, and other modules

The preceding list isn't comprehensive, so it's important that you perform a complete assessment of any application or service in your environment that uses user credentials for authentication. To contend with the requirement for MFA, you should implement the guidance in the [Secure Application Model framework](/partner-center/develop/enable-secure-app-model) where possible.

## Accessing your environment

To better understand what or who is authenticating without being challenged for MFA, we recommend that you review sign-in activity. Through Azure Active Directory Premium, you can use the sign-in report. For more information about this subject, see [Sign-in activity reports in the Azure Active Directory portal](/azure/active-directory/reports-monitoring/concept-sign-ins). If you don't have Azure Active Directory Premium, or if you're looking for a way obtain this sign-in activity through PowerShell, then you'll need to use the [Get-PartnerUserSignActivity](/powershell/module/partnercenter/get-partnerusersigninactivity) cmdlet from the [Partner Center PowerShell](https://www.powershellgallery.com/packages/PartnerCenter/) module.

## How the requirements are enforced

If your partner's organization was previously granted an exception for MFA, then users who manage customer tenants as part of the CSP program must have enabled Microsoft MFA requirements before March 1, 2022. Failure to comply with MFA requirements may result in the loss of customer tenant access.

Partner security requirements are enforced by Azure AD, and in turn Partner Center, by checking for the presence of the MFA claim to identify that MFA verification has taken place. Since November 18, 2019, Microsoft has activated more security safeguards (previously known as "technical enforcement") to partner tenants.

Upon activation, users in the partner tenant are requested to complete MFA verification when performing any admin on behalf of (AOBO) operations, accessing the Partner Center, or calling Partner Center APIs. For more information, see [Mandating multifactor authentication (MFA) for your partner tenant](partner-security-requirements-mandating-mfa.md).

Partners who haven't met the requirements should implement these measures as soon as possible to avoid any business disruptions. If you're using Azure Active Directory multifactor authentication or Azure AD security defaults, you don't need to take any other actions.

If you're using a third-party MFA solution, there's a chance that the MFA claim may not be issued. If this claim is missing, Azure AD won't be able determine if the authentication request was challenged by MFA. For information on how to verify that your solution is issuing the expected claim, read [Testing the Partner Security Requirements](/powershell/partnercenter/test-partner-security-requirements).

> [!IMPORTANT]
> If your third-party solution does not issue the expected claim, you will need to work with the vendor who developed the solution to determine what actions should be taken.

## Resources and samples

See the following resources for support and sample code:

- [Partner Center Security Guidance Group community](https://www.microsoftpartnercommunity.com/t5/Partner-Center-Security-Guidance/ct-p/partner-center-security-guidance): The Partner Center Security Guidance Group community is an online community where you can learn about upcoming events and ask any questions that you might have.
- [Partner Center .NET Samples](https://github.com/microsoft/partner-center-dotnet-samples): This GitHub repository contains samples that were developed using .NET that demonstrate how you can implement the Secure Application Model framework.
- [Partner Center Java Samples](https://github.com/microsoft/partner-center-java-samples): This GitHub repository contains samples that were developed using Java that demonstrate how you can implement the Secure Application Model framework.
- [Partner Center PowerShell - multifactor authentication](/powershell/partnercenter/multi-factor-auth): This multifactor authentication article provides details on how to implement the Secure Application Model framework using PowerShell.
- [Features and licenses for Azure AD multifactor authentication](/azure/active-directory/authentication/concept-mfa-licensing)
- [Plan an Azure Active Directory multifactor deployment](/azure/active-directory/authentication/howto-mfa-getstarted)
- [Testing the Partner Security Requirements using PowerShell](/powershell/partnercenter/test-partner-security-requirements?view=partnercenterps-3.0&preserve-view=true)

## Next steps

- [Mandating multifactor authentication (MFA) for your partner tenant](partner-security-requirements-mandating-mfa.md)
