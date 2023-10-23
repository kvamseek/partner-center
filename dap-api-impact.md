---
title: Partner Center APIs DAP-to-GDAP transition
ms.date: 11/29/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
ms.topic: article
description: This article describes the impact on APIs when going from DAP to GDAP.
author: Saneesha21
ms.author: salingal
---

# Partner Center APIs DAP-to-GDAP transition

**Appropriate roles**: All Partner Center users

APIs affected by the transition from DAP to GDAP are detailed below. Return to this document to see updates in impact and parity with GDAP.

[!INCLUDE [Important - Azure AD Graph is deprecated](./developer/includes/azure-ad-graph-notice.md)]

## APIs affected by the transition

| API | DAP removal impact | GDAP parity |
|--|--|--|
| [GetAssignedLicensesAsync](/partner-center/develop/check-which-licenses-are-assigned-to-a-user) | CSP Partners won't be</br> able to get licenses of the given customer user | Partners can use any one of the below roles.</br>Directory Reader,</br>Directory Writer,</br>User Admin,</br>License Admin |
| [GetSubscribedSkus](/partner-center/develop/get-a-list-of-available-licenses) | CSP Partners won't be</br> able to view the licenses available for a given customer tenant. | Partners can use any one of the below roles.</br>Directory Reader,</br>Global Reader,</br>User Admin,</br>License Admin |
|[AssignUserLicensesAsync](/partner-center/develop/assign-licenses-to-a-user)| CSP Partners won't be</br> able to assign licenses to the customer users | Partners can use any one of the below roles.</br>Directory Writer,</br>User Admin,</br>License Admin |
| [Get DirectoryRoles](/partner-center/develop/get-user-roles-for-a-customer) | No impact | Directory Reader​ |
| [GetCustomerDirectoryRoleUserMembers](/partner-center/develop/get-user-roles-for-a-customer) | CSP Partners won't be</br> able to get Directory roles User Members for a customer | Partners can use any one of the below roles.</br>Directory Reader,</br>Global Reader,</br>Directory Writer,</br>Privileged Role Admin |
| [AddUserMember](/partner-center/develop/set-user-roles-for-a-customer) | CSP Partner won't be</br> able to add a customer user to a given directory role | Privileged Role Admin |
| [RemoveUserMember](/partner-center/develop/remove-customer-user-from-a-role) | CSP Partner won't be</br> able to remove a customer user from a given directory role | Privileged Role Admin |
| [GetCustomerUsersAsync](/partner-center/develop/get-a-list-of-all-user-accounts-for-a-customer) | CSP partner user won't be</br> able to view/get the details of all the users in the customer tenant | Partners can use any one of the below roles.</br>Directory Reader,</br>Global reader,</br>User Admin |
| [GetCustomerUserDetailsAsync](/partner-center/develop/get-a-user-account-by-id) | CSP Partner won't be</br> able to view/get the details about a user in customer tenant | Partners can use any one of the below roles.</br>Directory Reader,</br>Global reader,</br>User Admin |
| [GetUserDirectoryRolesAsync](/partner-center/develop/get-user-roles-for-a-customer) | CSP Partner won't be</br> able to view/get the directory roles which the customer user is part of. | Partners can use any one of the below roles.</br>Directory Reader,</br>Global reader,</br>User Admin |
| [CreateCustomerUserAsync](/partner-center/develop/create-user-accounts-for-a-customer) | CSP Partner won't be</br> able to create new users in customer tenant | Partners can use any one of the below roles.</br>Directory Writer,</br>User Admin |
| [DeleteCustomerUserAsync](/partner-center/develop/delete-user-accounts-for-a-customer) | CSP Partner won't be</br> able to delete users in customer tenant | User Admin |
| [UpdateCustomerUserAsync](/partner-center/develop/update-user-accounts-for-a-customer) | CSP Partner won't be</br> able to update properties of a user in customer tenant. (Don't use this API to reset passwords, look for the new ResetPassword API for GDAP) | Partners can use any one of the below roles.</br>Directory Writer,</br>User Admin |
| ResetPassword (no API docs available) | CSP partners won't be</br> able to reset the passwords of users in customer tenant | User Admin / Privileged Authentication Admin to reset password for license management users</br>Privileged Authentication Admin to reset password for all other users |
| [Get all service requests for a customer](/rest/api/partner-center/provide-support/get-all-service-requests-for-a-customer) | Unable to view support</br>tickets for the customer | Any role that supports microsoft.office365.supportTickets</br>/allEntities/allTasks or microsoft.azure.supportTickets</br>/allEntities/allTasks</br>[Permissions reference](/azure/active-directory/roles/permissions-reference) |
| [Get the customer service requests by ID](/rest/api/partner-center/provide-support/get-the-customer-service-requests-by-id) | Unable to view support</br>tickets for the customer | Any role that supports microsoft.office365.supportTickets</br>/allEntities/allTasks or microsoft.azure.supportTickets</br>/allEntities/allTasks</br>[Permissions reference](/azure/active-directory/roles/permissions-reference) |
| [GetSubscribedSku](/rest/api/partner-center/manage-customer-accounts/get-subscribed-skus) | Partner won't be </br>able to see all the available licenses on customer tenant across different channels. | Partners can use any one of the below roles.</br>Directory Reader,</br>Global reader |
| [Update Qualification](/rest/api/partner-center/manage-customer-accounts/update-customer-qualification) | DAP isn't required for accessing this API | No GDAP Role Required |
| [Get Customer ID](/partner-center/develop/get-a-customer-by-id) | The following attributes</br> won't return:</br>CustomDomain, CompanyProfileEmail, CompanyProfileAddress. In order for partners to get the CustomDomain/CompanyProfileEmail</br>/CompanyProfileAddress partners need to call Graph API (Details will be added soon) | Directory Reader |
| [GetCustomerCompanyProfile](/partner-center/develop/get-a-customer-s-company-profile) | The following attributes</br> won't return:</br>CustomDomain, CompanyProfileEmail, CompanyProfileAddress.</br>In order for partners to get the CustomDomain/CompanyProfileEmail</br>/CompanyProfileAddress partners need to call Graph API (Details will be added soon) | Directory Reader |
| [Get Upgrades](/partner-center/develop/transition-a-subscription) | CSP partners won't be able to see if they're eligible for upgrades with license transfer.  | Partners can use any one of the below roles.</br>Directory Reader, Global reader |
| [Get Transition Eligibilities](/partner-center/develop/transition-a-new-commerce-subscription#get-transition-eligibilities) | CSP partners won't be able to see if they are eligible for transitions with license transfer.  | Partners can use any one of the below roles.</br> Directory Reader,</br>Global reader</br>Note: While this API is available for legacy and NCE, GDAP is only required for legacy.  |
| [Upgrade](/partner-center/develop/transition-a-subscription) | CSP partners won't be able to conduct a license transfer during an upgrade. | Directory Reader or Global reader (upgrade only) </br> Directory Writer (upgrade with license transfer)  |
| [Create Transition](/partner-center/develop/transition-a-new-commerce-subscription#post-transition) | CSP partners won't be able to conduct a license transfer during transition. | Directory Reader or Global reader (transition only) </br>Directory Writer (transition with license transfer) </br> Note: While this API is available for legacy and NCE, GDAP is only required for legacy.  |
| [Get Provisioning Status by Subscription by ID](/partner-center/develop/get-subscription-provisioning-status) |CSP Partners won't be able to see the provisioning status for their subscriptions. | Partners can use any one of the below roles.</br>Directory Reader,</br>Global reader |

## Next steps

- [Partner security requirements](partner-security-requirements.md)
- [Granular delegated admin privileges (GDAP) introduction](gdap-introduction.md)
- [Monitoring administrative relationships and self-service DAP removal](dap-monitor-self-serve-removal.md)
- [GDAP role guidance](gdap-least-privileged-roles-by-task.md)
