---
title: Partner Center webhook events
description: Learn how to test and use Webhook events to note when subscriptions and other events change in Partner Center.
ms.date: 10/17/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: vijay-vala
ms.author: vijvala
---

# Partner Center webhook events

**Applies to**: Partner Center | Partner Center operated by 21Vianet |  Partner Center for Microsoft Cloud for US Government

Partner Center webhook events are resource change events delivered in the form of HTTP POSTs to a registered URL. To receive an event from Partner Center, you host a callback where Partner Center can POST the event. The event is digitally signed so you can validate that it was sent from Partner Center.

For information on how to receive events, authenticate a callback, and use the Partner Center webhook APIs to create, view, and update an event registration, see [Partner Center Webhooks](partner-center-webhooks.md).

## Supported Events

Partner Center supports the below webhook events.

### Test Event

This event allows you to self-onboard and test your registration by requesting a test event and then tracking its progress. You can see the failure messages that are being received from Microsoft while trying to deliver the event. This only applies to "test-created" events and data older than seven days is purged.

> [!NOTE]
>A throttle limit of 2 requests per minute is enforced when posting a test-created event.

#### Properties

| Property                  | Type                               | Description                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| EventName                 | string                             | The name of the event. In the form {resource}-{action}. For this event, the value is **test-created**.                                          |
| ResourceUri               | URI                                | The URI to get the resource. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/webhooks/v1/registration/validationEvents/{{CorrelationId}}" |
| ResourceName              | string                             | The name of the resource that triggers the event. For this event, the value is **test**.                                  |
| AuditUri                  | URI                                | (Optional) The URI to get the audit record, if it exists. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}" |
| ResourceChangeUtcDate     | string in the UTC date-time format | The date and time when the resource change occurred.                                                         |

#### Example

```json
{
    "EventName": "test-created",
    "ResourceUri": "http://api.partnercenter.microsoft.com/webhooks/v1/registration/validationEvents/{{CorrelationId}}",
    "ResourceName": "test",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2017-11-16T16:19:06.3520276+00:00"
}
```

### Subscription Updated Event

This event is raised when the specified subscription changes. A Subscription Updated event is generated when there is an internal change in addition to when changes are made through the Partner Center API.  This event is only generated when there are commerce level changes, for example, when the number of licenses are modified and when the state of the subscription changes. It won't be generated when resources are created within the subscription.

> [!NOTE]
>There is a delay of up to 48 hours between the time a subscription changes and when the Subscription Updated event is triggered.

#### Properties

| Property                  | Type                               | Description                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| EventName                 | string                             | The name of the event. In the form {resource}-{action}. For this event, the value is **subscription-updated**.                                  |
| ResourceUri               | URI                                | The URI to get the resource. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/webhooks/v1/customers/{{CustomerId}}/subscriptions/{{SubscriptionId}}" |
| ResourceName              | string                             | The name of the resource that triggers the event. For this event, the value is **subscription**.                          |
| AuditUri                  | URI                                | (Optional) The URI to get the audit record, if it exists. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}" |
| ResourceChangeUtcDate     | string in the UTC date-time format | The date and time when the resource change occurred.                                                         |

#### Example

```json
{
    "EventName": "subscription-updated",
    "ResourceUri": "http://api.partnercenter.microsoft.com/webhooks/v1/customers/{{CustomerId}}/subscriptions/{{SubscriptionId}}",
    "ResourceName": "subscription",
    "AuditUri": "https://api.partnercenter.microsoft.com/v1/auditrecords/{{AuditId}}",
    "ResourceChangeUtcDate": "2017-11-16T16:19:06.3520276+00:00"
}
```

### Threshold Exceeded Event

This event is raised when the amount of Microsoft Azure usage for any customer exceeds their usage spending budget (their threshold). For more information, see  [Set an Azure spending budget for your customers/partner-center/set-an-azure-spending-budget-for-your-customers).

#### Properties

| Property                  | Type                               | Description                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| EventName                 | string                             | The name of the event. In the form {resource}-{action}. For this event, the value is **usagerecords-thresholdExceeded**.                                  |
| ResourceUri               | URI                                | The URI to get the resource. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/webhooks/v1/customers/usagerecords" |
| ResourceName              | string                             | The name of the resource that triggers the event. For this event, the value is **usagerecords**.                          |
| AuditUri                  | URI                                | (Optional) The URI to get the audit record, if it exists. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}" |
| ResourceChangeUtcDate     | string in the UTC date-time format | The date and time when the resource change occurred.                                                         |

#### Example

```json
{
    "EventName": "usagerecords-thresholdExceeded",
    "ResourceUri": "https://api.partnercenter.microsoft.com/v1/customers/usagerecords",
    "ResourceName": "usagerecords",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2018-02-17T00:05:39.5485487+00:00"
}
```

### Referral Created Event

This event is raised when the referral is created.

#### Properties

| Property                  | Type                               | Description                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| EventName                 | string                             | The name of the event. In the form {resource}-{action}. For this event, the value is **referral-created**.                                  |
| ResourceUri               | URI                                | The URI to get the resource. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/engagements/v1/referrals/{{ReferralID}}" |
| ResourceName              | string                             | The name of the resource that triggers the event. For this event, the value is **referral**.                          |
| AuditUri                  | URI                                | (Optional) The URI to get the audit record, if it exists. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}" |
| ResourceChangeUtcDate     | string in the UTC date-time format | The date and time when the resource change occurred.                                                         |

#### Example

```json
{
    "EventName": "referral-created",
    "ResourceUri": "https://api.partnercenter.microsoft.com/engagements/v1/referrals/{{ReferralID}}",
    "ResourceName": "referral",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2018-02-17T00:05:39.5485487+00:00"
}
```

### Referral Updated Event

This event is raised when the referral is updated.

#### Properties

| Property                  | Type                               | Description                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| EventName                 | string                             | The name of the event. In the form {resource}-{action}. For this event, the value is **referral-updated**.                                  |
| ResourceUri               | URI                                | The URI to get the resource. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/engagements/v1/referrals/{{ReferralID}}" |
| ResourceName              | string                             | The name of the resource that triggers the event. For this event, the value is **referral**.                          |
| AuditUri                  | URI                                | (Optional) The URI to get the audit record, if it exists. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}" |
| ResourceChangeUtcDate     | string in the UTC date-time format | The date and time when the resource change occurred.                                                         |

#### Example

```json
{
    "EventName": "referral-updated",
    "ResourceUri": "https://api.partnercenter.microsoft.com/engagements/v1/referrals/{{ReferralID}}",
    "ResourceName": "referral",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2018-02-17T00:05:39.5485487+00:00"
}
```

### Related Referral Updated Event

This event is raised when the related referral is updated.

#### Properties

| Property                  | Type                               | Description                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| EventName                 | string                             | The name of the event. In the form {resource}-{action}. For this event, the value is **related-referral-updated**.                                  |
| ResourceUri               | URI                                | The URI to get the resource. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/engagements/v1/referrals/{{ReferralID}}" |
| ResourceName              | string                             | The name of the resource that triggers the event. For this event, the value is **referral**.                          |
| AuditUri                  | URI                                | (Optional) The URI to get the audit record, if it exists. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}" |
| ResourceChangeUtcDate     | string in the UTC date-time format | The date and time when the resource change occurred.                                                         |

#### Example

```json
{
    "EventName": "related-referral-updated",
    "ResourceUri": "https://api.partnercenter.microsoft.com/engagements/v1/referrals/{{ReferralID}}",
    "ResourceName": "referral",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2018-02-17T00:05:39.5485487+00:00"
}
```

### Related Referral Created Event

This event is raised when the related referral is created.

#### Properties

| Property                  | Type                               | Description                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| EventName                 | string                             | The name of the event. In the form {resource}-{action}. For this event, the value is **related-referral-created**.                                  |
| ResourceUri               | URI                                | The URI to get the resource. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/engagements/v1/referrals/{{ReferralID}}" |
| ResourceName              | string                             | The name of the resource that triggers the event. For this event, the value is **referral**.                          |
| AuditUri                  | URI                                | (Optional) The URI to get the audit record, if it exists. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}" |
| ResourceChangeUtcDate     | string in the UTC date-time format | The date and time when the resource change occurred.                                                         |

#### Example

```json
{
    "EventName": "related-referral-created",
    "ResourceUri": "https://api.partnercenter.microsoft.com/engagements/v1/referrals/{{ReferralID}}",
    "ResourceName": "referral",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2018-02-17T00:05:39.5485487+00:00"
}
```

### Granular Admin Relationship Approved Event

This event is raised when the Granular Delegated Admin Privileges are approved by the customer tenant.

#### Properties

| Property                  | Type                               | Description                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| EventName                 | string                             | The name of the event. In the form {resource}-{action}. For this event, the value is **granular-admin-relationship-approved**.                                  |
| ResourceUri               | URI                                | The URI to get the resource. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/granularAdminRelationships/{{RelationshipID}}" |
| ResourceName              | string                             | The name of the resource that triggers the event. For this event, the value is **GranularAdminRelationship**.                          |
| AuditUri                  | URI                                | (Optional) The URI to get the audit record, if it exists. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}" |
| ResourceChangeUtcDate     | string in the UTC date-time format | The date and time when the resource change occurred.                                                         |

#### Example

```json
{
    "EventName": "granular-admin-relationship-approved",
    "ResourceUri": "https://partner.microsoft.com/granularAdminRelationships/{{RelationshipID}}",
    "ResourceName": "GranularAdminRelationship",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2018-02-17T00:05:39.5485487+00:00"
}
```

### Granular Admin Relationship Activated Event

This event is raised when the Granular Delegated Admin Privileges is created and active for the customer to approve.

#### Properties

| Property                  | Type                               | Description                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| EventName                 | string                             | The name of the event. In the form {resource}-{action}. For this event, the value is **granular-admin-relationship-activated**.                                  |
| ResourceUri               | URI                                | The URI to get the resource. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/granularAdminRelationships/{{RelationshipID}}" |
| ResourceName              | string                             | The name of the resource that triggers the event. For this event, the value is **GranularAdminRelationship**.                          |
| AuditUri                  | URI                                | (Optional) The URI to get the audit record, if it exists. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}" |
| ResourceChangeUtcDate     | string in the UTC date-time format | The date and time when the resource change occurred.                                                         |

#### Example

```json
{
    "EventName": "granular-admin-relationship-activated",
    "ResourceUri": "https://partner.microsoft.com/granularAdminRelationships/{{RelationshipID}}",
    "ResourceName": "GranularAdminRelationship",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2018-02-17T00:05:39.5485487+00:00"
}
```

### Granular Admin Relationship Terminated Event

This event is raised when the Granular Delegated Admin Privileges is either terminated by the partner/customer tenant.

#### Properties

| Property                  | Type                               | Description                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| EventName                 | string                             | The name of the event. In the form {resource}-{action}. For this event, the value is **granular-admin-relationship-terminated**.                                  |
| ResourceUri               | URI                                | The URI to get the resource. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/granularAdminRelationships/{{RelationshipID}}" |
| ResourceName              | string                             | The name of the resource that triggers the event. For this event, the value is **GranularAdminRelationship**.                          |
| AuditUri                  | URI                                | (Optional) The URI to get the audit record, if it exists. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}" |
| ResourceChangeUtcDate     | string in the UTC date-time format | The date and time when the resource change occurred.                                                         |

#### Example

```json
{
    "EventName": "granular-admin-relationship-terminated",
    "ResourceUri": "https://partner.microsoft.com/granularAdminRelationships/{{RelationshipID}}",
    "ResourceName": "GranularAdminRelationship",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2018-02-17T00:05:39.5485487+00:00"
}
```

### Granular Admin Relationship Expired Event

This event is raised when the Granular Delegated Admin Privileges is expired.

#### Properties

| Property                  | Type                               | Description                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| EventName                 | string                             | The name of the event. In the form {resource}-{action}. For this event, the value is **granular-admin-relationship-expired**.                                  |
| ResourceUri               | URI                                | The URI to get the resource. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/granularAdminRelationships/{{RelationshipID}}" |
| ResourceName              | string                             | The name of the resource that triggers the event. For this event, the value is **GranularAdminRelationship**.                          |
| AuditUri                  | URI                                | (Optional) The URI to get the audit record, if it exists. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}" |
| ResourceChangeUtcDate     | string in the UTC date-time format | The date and time when the resource change occurred.                                                         |

#### Example

```json
{
    "EventName": "granular-admin-relationship-expired",
    "ResourceUri": "https://partner.microsoft.com/granularAdminRelationships/{{RelationshipID}}",
    "ResourceName": "GranularAdminRelationship",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2018-02-17T00:05:39.5485487+00:00"
}
```

### Granular Admin Access Assignment Created Event

This event is raised when the Granular Delegated Admin Privileges access assignment is created by the partner. Partners can assign customer-approved Azure Active Directory (Azure AD) roles to specific security groups.

#### Properties

| Property                  | Type                               | Description                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| EventName                 | string                             | The name of the event. In the form {resource}-{action}. For this event, the value is **granular-admin-access-assignment-created**.                                  |
| ResourceUri               | URI                                | The URI to get the resource. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/granularAdminRelationships/{{RelationshipID}}/accessAssignments/{{AssignmentID}}" |
| ResourceName              | string                             | The name of the resource that triggers the event. For this event, the value is **GranularAdminAccessAssignment**.                          |
| AuditUri                  | URI                                | (Optional) The URI to get the audit record, if it exists. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}" |
| ResourceChangeUtcDate     | string in the UTC date-time format | The date and time when the resource change occurred.                                                         |

#### Example

```json
{
    "EventName": "granular-admin-access-assignment-created",
    "ResourceUri": "https://partner.microsoft.com/granularAdminRelationships/{{RelationshipID}}/accessAssignments/{{AssignmentID}}",
    "ResourceName": "GranularAdminAccessAssignment",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2018-02-17T00:05:39.5485487+00:00"
}
```

### Granular Admin Access Assignment Activated Event

This event is raised when the Granular Delegated Admin Privileges access assignment is activated by the partner once the Azure AD roles are assigned to specific security groups.

#### Properties

| Property                  | Type                               | Description                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| EventName                 | string                             | The name of the event. In the form {resource}-{action}. For this event, the value is **granular-admin-access-assignment-activated**.                                  |
| ResourceUri               | URI                                | The URI to get the resource. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/granularAdminRelationships/{{RelationshipID}}/accessAssignments/{{AssignmentID}}" |
| ResourceName              | string                             | The name of the resource that triggers the event. For this event, the value is **GranularAdminAccessAssignment**.                          |
| AuditUri                  | URI                                | (Optional) The URI to get the audit record, if it exists. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}" |
| ResourceChangeUtcDate     | string in the UTC date-time format | The date and time when the resource change occurred.                                                         |

#### Example

```json
{
    "EventName": "granular-admin-access-assignment-activated",
    "ResourceUri": "https://partner.microsoft.com/granularAdminRelationships/{{RelationshipID}}/accessAssignments/{{AssignmentID}}",
    "ResourceName": "GranularAdminAccessAssignment",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2018-02-17T00:05:39.5485487+00:00"
}
```

### Granular Admin Access Assignment Updated Event

This event is raised when the Granular Delegated Admin Privileges access assignment is updated by the partner.

#### Properties

| Property                  | Type                               | Description                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| EventName                 | string                             | The name of the event. In the form {resource}-{action}. For this event, the value is **granular-admin-access-assignment-updated**.                                  |
| ResourceUri               | URI                                | The URI to get the resource. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/granularAdminRelationships/{{RelationshipID}}/accessAssignments/{{AssignmentID}}" |
| ResourceName              | string                             | The name of the resource that triggers the event. For this event, the value is **GranularAdminAccessAssignment**.                          |
| AuditUri                  | URI                                | (Optional) The URI to get the audit record, if it exists. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}" |
| ResourceChangeUtcDate     | string in the UTC date-time format | The date and time when the resource change occurred.                                                         |

#### Example

```json
{
    "EventName": "granular-admin-access-assignment-updated",
    "ResourceUri": "https://partner.microsoft.com/granularAdminRelationships/{{RelationshipID}}/accessAssignments/{{AssignmentID}}",
    "ResourceName": "GranularAdminAccessAssignment",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2018-02-17T00:05:39.5485487+00:00"
}
```

### Granular Admin Access Assignment Deleted Event

This event is raised when the Granular Delegated Admin Privileges access assignment is deleted by the partner.

#### Properties

| Property                  | Type                               | Description                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| EventName                 | string                             | The name of the event. In the form {resource}-{action}. For this event, the value is **granular-admin-access-assignment-deleted**.                                  |
| ResourceUri               | URI                                | The URI to get the resource. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/granularAdminRelationships/{{RelationshipID}}/accessAssignments/{{AssignmentID}}" |
| ResourceName              | string                             | The name of the resource that triggers the event. For this event, the value is **GranularAdminAccessAssignment**.                          |
| AuditUri                  | URI                                | (Optional) The URI to get the audit record, if it exists. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}" |
| ResourceChangeUtcDate     | string in the UTC date-time format | The date and time when the resource change occurred.                                                         |

#### Example

```json
{
    "EventName": "granular-admin-access-assignment-deleted",
    "ResourceUri": "https://partner.microsoft.com/granularAdminRelationships/{{RelationshipID}}/accessAssignments/{{AssignmentID}}",
    "ResourceName": "GranularAdminAccessAssignment",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2018-02-17T00:05:39.5485487+00:00"
}
```

### Reseller Relationship Accepted by Customer Event

This event is raised when a customer accepts a reseller relationship.

#### Properties

| Property                  | Type                               | Description                                                                                 |
|---------------------------|------------------------------------|---------------------------------------------------------------------------------------------|
| 	EventName	| 	string	| 	The name of the event. In the form {resource}-{action}. For this event, the value is **reseller-relationship-accepted-by-customer**.  |
| 	ResourceUri	| 	URI	| 	The URI to get the resource. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{CustomerId}"   |
| 	ResourceName	| 	string	| 	The name of the resource that triggers the event. For this event, the value is **customer**.    |
| 	AuditUri	| 	URI	| 	(Optional) The URI to get the audit record, if it exists. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}"  |
| 	ResourceChangeUtcDate	| 	string in the UTC date-time format	| 	The date and time when the resource change occurred.	| 

#### Example

```json
{
  "EventName": "reseller-relationship-accepted-by-customer",
  "ResourceUri": "https://api.partnercenter.microsoft.com/v1/customers/4b2a6e33-8791-4386-bd2b-0d55baf25039",
  "ResourceName": "Customer",
  "AuditUri": "https://api.partnercenter.microsoft.com/auditactivity/v1/auditrecords/60d5c4bb-f78a-4200-a002-953d7cc1f5f8_4b2a6e33-8791-4386-bd2b-0d55baf25039_resellerrelationshipacceptedbycustomer_638331855840159088",
  "ResourceChangeUtcDate": "2023-10-18T00:26:24.0159088+00:00"
}
```

### Dap Admin Relationship Terminated By Microsoft Event

This event is raised when Microsoft terminates DAP between the Partner and Customer tenant when DAP is inactive for more than 90 days.

#### Properties

| Property                  | Type                               | Description                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| EventName                 | string                             | The name of the event. In the form {resource}-{action}. For this event, the value is **dap-admin-relationship-terminated-by-microsoft**.                                  |
| ResourceName              | string                             | The name of the resource that triggers the event. For this event, the value is **PartnerCustomerDap**.                          |
| AuditUri                  | URI                                | (Optional) The URI to get the audit record, if it exists. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}" |
| ResourceChangeUtcDate     | string in the UTC date-time format | The date and time when the resource change occurred.                                                         |

#### Example

```json
{
    "EventName": "dap-admin-relationship-terminated-by-microsoft",
    "ResourceName": "PartnerCustomerDap",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2018-02-17T00:05:39.5485487+00:00"
}
```
### Dap Admin Relationship Approved Event

This event is raised when DAP between the Partner and Customer tenant is approved.

#### Properties

| Property                  | Type                               | Description                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| EventName                 | string                             | The name of the event. In the form {resource}-{action}. For this event, the value is **dap-admin-relationship-approved**.                         |
| ResourceName              | string                             | The name of the resource that triggers the event. For this event, the value is **PartnerCustomerDap**.                          |
| ResourceUri               | string                             | NA Not available |
| AuditUri                  | URI                                | (Optional) The URI to get the audit record, if it exists. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}" |
| ResourceChangeUtcDate     | string in the UTC date-time format | The date and time when the resource change occurred.                                                         |

#### Example

```json
{
    "EventName": "dap-admin-relationship-approved",
    "ResourceName": "PartnerCustomerDap",
    "AuditUri": null,
    "ResourceUri": null,
    "ResourceChangeUtcDate": "2018-02-17T00:05:39.5485487+00:00"
}
```

### Dap Admin Relationship Terminated

This event is raised when DAP between the Partner and Customer tenant is terminated.

#### Properties

| Property                  | Type                               | Description                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| EventName                 | string                             | The name of the event. In the form {resource}-{action}. For this event, the value is **dap-admin-relationship-terminated**.                      |
| ResourceName              | string                             | The name of the resource that triggers the event. For this event, the value is **PartnerCustomerDap**.                         |
| ResourceUri               | string                             | NA Not available |
| AuditUri                  | URI                                | (Optional) The URI to get the audit record, if it exists. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}" |
| ResourceChangeUtcDate     | string in the UTC date-time format | The date and time when the resource change occurred.                                                         |

#### Example

```json
{
    "EventName": "dap-admin-relationship-terminated",
    "ResourceName": "PartnerCustomerDap",
    "AuditUri": null,
    "ResourceUri": null,
    "ResourceChangeUtcDate": "2018-02-17T00:05:39.5485487+00:00"

}
```
### Azure Fraud Event Detected Event

This event is raised when the Parter tenant has any Azure Fraud event detected for any of their customer tenants. Partners are required to take action to resolve the fraud.

#### Properties

| Property                  | Type                               | Description                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| EventName                 | string                             | The name of the event. In the form {resource}-{action}. For this event, the value is **azure-fraud-event-detected**.                                  |
| ResourceUri               | URI                                | The URI to get the resource. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/v1/fraudEvents?SubscriptionId={{subscriptionId}}&EventStatus={{eventStatus}}" |
| AuditUri                  | URI                                | (Optional) The URI to get the audit record, if it exists. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}" |
| ResourceChangeUtcDate     | string in the UTC date-time format | The date and time when the resource change occurred.                                                         |

#### Example

```json
{
    "EventName": "azure-fraud-event-detected",
    "ResourceUri": "https://api.partnercenter.microsoft.com/v1/fraudEvents?SubscriptionId={{subscriptionId}}&EventStatus={{eventStatus}}",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2018-02-17T00:05:39.5485487+00:00"
}
```

### Invoice Ready Event

This event is raised when the new invoice is ready.

| Property                  | Type                               | Description                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| EventName | string | The name of the event. In the form {resource}-{action}. For this event, the value is **invoice-ready**. |
| ResourceUri | URI | The URI to get the resource. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{{InvoiceId}}" |
| ResourceName | string | The name of the resource that triggers the event. For this event, the value is **invoice**. |
| AuditUri |  URI | (Optional) The URI to get the audit record, if it exists. Uses the syntax: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}") |
| ResourceChangeUtcDate | string in the UTC date-time format | The date and time when the resource change occurred. |

#### Example

```json
{
    "EventName": "invoice-ready",
    "ResourceUri": "https://api.partnercenter.microsoft.com/v1/invoices/{{InvoiceId}}",
    "ResourceName": "invoice",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2018-02-17T00:05:39.5485487+00:00"
}

```
