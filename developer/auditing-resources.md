---
title: Auditing resources
description: Learn about Partner Center API auditing resources, like AuditRecord, that you can use to get a record of Partner Center activity.
ms.date: 6/7/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: vijay-vala
ms.author: vijvala
---

# Auditing resources that help you get a record of Partner Center activity

You can use the following resources with audit operations.

## AuditRecord

Represents a record of an operation performed by a partner user or application.

| Property | Type | Description |
| --- | --- | ---|
| customerId | string | A GUID-formatted string that identifies the customer. |
| customerName | string | The customer name. |
| userPrincipalName | string | The user principal name or user identifier. Typically, this property is an Internet-style login name for a user in an email address format based on Internet standard RFC 822. |
| applicationId | string | A string that identifies the application that performed the operation. |
| resourceType | string | The type of resource acted upon by the operation. Possible values: `customer`, `customer_user`, `order`, `subscription`, `license`, `third_party_add_on`, `mpn_association`, `transfer`, `application`, `application_credential`, `partner_user`, `partner_relationship`, `partner_customer_dap`, `customer_directory_role`, `referral`, `software_key`, `software_download_link`, `spending_limit`, `invoice`, `agreement`, `partner_customer_relationship`, `self_serve_policy`, `granular_admin_relationship`, `granular_admin_access_assignment`, `credit`, `software_page`, `device`, `policy`. |
| resourceOldValue | string | The old value of the resource. |
| resourceNewValue | string | The new value of the resource. |
| operationType | string | The type of operation performed. Possible values: `update_customer_qualification`, `update_subscription`, `upgrade_subscription`, `convert_trial_subscription`, `add_customer`, `update_customer_billing_profile`, `update_customer_partner_contract_company_name`, `update_customer_spending_budget`, `delete_customer` (sandbox integration accounts only), `remove_partner_customer_relationship`, `create_order`, `update_order`, `create_customer_user`, `delete_customer_user`, `update_customer_user`, `update_customer_user_licenses`, `reset_customer_user_password`, `update_customer_user_principal_name`, `restore_customer_user`, `create_mpn_association`, `update_mpn_association`, `update_sfb_customer_user_licenses`, `update_transfer`, `create_partner_relationship`, `register_application`, `unregister_application`, `add_application_credential`, `remove_application_credential`, `create_partner_user`, `update_partner_user`, `remove_partner_user`, `create_self_serve_policy`, `update_self_serve_policy`, `delete_self_serve_policy`,`remove_partner_relationship`,`delete_tip_customer`,`create_related_referral`,`update_related_referral`, `create_referral`, `update_referral`, `get_software_key`, `get_software_download_link`, `increase_spending_limit`, `ready_invoice`, `create_agreement`, `extend_relationship`, `create_transfer`, `dap_admin_relationship_approved`, `dap_admin_relationship_terminated`, `add_user_member`, `remove_user_member`, `granular_admin_relationship_approved`, `granular_admin_relationship_activated`, `granular_admin_relationship_termination_requested`, `granular_admin_relationship_terminated`, `granular_admin_relationship_expired`, `granular_admin_access_assignment_created`, `granular_admin_access_assignment_updated`, `granular_admin_access_assignment_deleted`, `dap_admin_relationship_approved`, `dap_admin_relationship_terminated`, `create_credit`, `update_credit`, `cancel_credit`, `granular_admin_access_assignment_activated`, `software_attestation`, `granular_admin_relationship_cleaned_up`, `update_company_info`, `policy_created`, `policy_updated`, `policy_deleted`, `device_updated`, `devices_update_attempted`, `device_deleted`, `devices_upload_to_new_batch_attempted`, `devices_upload_to_existing_batch_attempted`, `manage_overage`, `dap_admin_relationship_terminated_by_microsoft`, `azure_fraud_event_detected`. |
| operationDate | string in UTC date-time format | The date and time when the operation was performed. |
| operationStatus | string | The status of the operation being audited. Possible values: `succeeded`, `failed`, or `progress`, which means the operation is still in progress. |
| customizedData  | array of objects | Additional information. Each object contains two JSON key-value pairs: the first is `key` and a string value, the second is `value` and a string value. The number of objects in the array depends on the type of operation that was performed. |
| attributes | [ResourceAttributes](utility-resources.md#resourceattributes) | The metadata attributes. |
