---
title: Roles, permissions for partner earned credit
ms.topic: article
ms.date: 11/08/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-billing
description: Learn about the roles and permissions for partners to be able to earn partner earned credit (PEC). (These roles differ from roles to work in Partner Center.)
author: sourishdeb
ms.author: sodeb
---

# Roles and permissions required to receive partner earned credit

The following roles map to permissions levels that determine whether a partner is eligible for partner earned credit (PEC).

> [!IMPORTANT]
>These roles and permissions are not the same as the roles and permissions a user needs to work in Partner Center.

|**Role**   |**Description**   |**PEC eligible**   |
|-----------------|:------------------|:--------------|
|Owner  |You manage everything, including access to resources.|Yes|
|Contributor |You manage everything except granting access to resources.|Yes|
|Reader|You can view everything, but not make any changes|No|
|ACRDelete|acr delete|Yes|
|ACRImageSigner|acr image signer|Yes|
|ACRPull|acr pull|Yes|
|AcrPush|acr push|Yes|
|AcrQuarantineReader|acr quarantine data reader|No|
|AcrQuarantineWriter| acr quarantine data writer|Yes|
|API Management Service Contributor|Can manage service and the APIs|Yes|
|API Management Service Operator Role|Can manage service but not the APIs|Yes|
|API Management Service Reader Role|Read-only access to service and APIs|No|
|Application Insights Component Contributor|Manages Application Insights components|Yes|
|Application Insights Snapshot Debugger|Gives user permission to view and download debug snapshots collected with the Application Insights Snapshot Debugger. These permissions aren't included in the Owner or Contributor roles.|Yes|
Automation Job Operator | Create and Manage Jobs using Automation Runbooks. | Yes |
Automation Operator | Automation Operators are able to start, stop, suspend, and resume jobs | Yes |
Automation Runbook Operator | Read Runbook properties - to be able to create Jobs of the runbook. | Yes |
Avere Contributor | Can create and manage an Avere vFXT cluster. | Yes |
Avere Operator | Used by the Avere vFXT cluster to manage the cluster | Yes |
Azure Event Hubs Data Owner | Allows for full access to Azure Event Hubs resources. | Yes |
Azure Event Hubs Data Receiver | Allows receive access to Azure Event Hubs resources. | Yes |
Azure Event Hubs Data Sender | Allows send access to Azure Event Hubs resources. | Yes |
Azure Kubernetes Service Cluster Admin Role | List cluster admin credential action. | Yes |
Azure Kubernetes Service Cluster User Role | List cluster user credential action. | Yes |
Azure Maps Data Reader (Preview) | Grants access to read map related data from an Azure maps account. | No |
Azure Service Bus Data Owner | Allows for full access to Azure Service Bus resources. | Yes |
Azure Service Bus Data Receiver | Allows for receive access to Azure Service Bus resources. | Yes |
Azure Service Bus Data Sender | Allows for send access to Azure Service Bus resources. | Yes |
Azure Stack Registration Owner | Lets you manage Azure Stack registrations. | Yes |
Backup Contributor | Lets you manage backup service, but can't create vaults and give access to others | Yes |
Backup Operator | Lets you manage backup services, except removal of backup, vault creation and giving access to others | Yes |
Backup Reader | Can view backup services, but can't make changes | No |
Billing Reader | Allows read access to billing data | No |
BizTalk Contributor | Lets you manage BizTalk services, but not access to them. | Yes |
Blockchain Member Node Access (Preview) | Allows for access to Blockchain Member nodes | Yes |
Blueprint Contributor | Can manage blueprint definitions, but not assign them. | Yes |
Blueprint Operator | Can assign existing published blueprints, but can't create new blueprints. NOTE: this only works if the assignment is done with a user-assigned managed identity. | Yes |
CDN Endpoint Contributor | Can manage CDN endpoints, but can't grant access to other users. | Yes |
CDN Endpoint Reader | Can view CDN endpoints, but can't make changes. | No |
CDN Profile Contributor | Can manage CDN profiles and their endpoints, but can't grant access to other users. | Yes |
CDN Profile Reader | Can view CDN profiles and their endpoints, but can't make changes. | No |
Classic Network Contributor | Lets you manage classic networks, but not access to them. | Yes |
Classic Storage Account Contributor | Lets you manage classic storage accounts, but not access to them. | Yes |
Classic Storage Account Key Operator Service Role | Classic Storage Account Key Operators are allowed to list and regenerate keys on Classic Storage Accounts | Yes |
Classic Virtual Machine Contributor | Lets you manage classic virtual machines, but not access to them, and not the virtual network or storage account they're connected to. | Yes |
Cognitive Services Contributor | Lets you create, read, update, delete and manage keys of Cognitive Services. | Yes |
Cognitive Services Data Reader (Preview) | Lets you read Cognitive Services data. | No |
Cognitive Services User | Lets you read and list keys of Cognitive Services. | No |
Cosmos DB Account Reader Role | Can read Azure Cosmos DB account data. See DocumentDB Account Contributor for managing Azure Cosmos DB accounts. | No |
Cosmos DB Operator | Lets you manage Azure Cosmos DB accounts, but not access data in them. Prevents access to account keys and connection strings. | Yes |
CosmosBackupOperator | Can submit restore request for a Cosmos DB database or a container for an account | Yes |
Cost Management Contributor | Can view costs and manage cost configuration (for example, budgets, exports) | Yes |
Cost Management Reader | Can view cost data and configuration (for example, budgets, exports) | No |
Data Box Contributor | Lets you manage everything under Data Box Service except giving access to others. | Yes |
Data Box Reader | Lets you manage Data Box Service except creating order or editing order details and giving access to others. | No |
Data Factory Contributor | Create and manage data factories, and child resources within them. | Yes |
Data Lake Analytics Developer | Lets you submit, monitor, and manage your own jobs but not create or delete Data Lake Analytics accounts. | Yes |
Data Purger | Can purge analytics data | Yes |
DevTest Labs User | Lets you connect, start, restart, and shut down your virtual machines in your Azure DevTest Labs. | Yes |
DNS Zone Contributor | Lets you manage DNS zones and record sets in Azure DNS, but doesn't let you control who has access to them. | Yes |
DocumentDB Account Contributor | Can manage Azure Cosmos DB accounts. Azure Cosmos DB is formerly known as DocumentDB. | Yes |
Event Grid EventSubscription Contributor | Lets you manage Event Grid event subscription operations. | Yes |
Event Grid EventSubscription Reader | Lets you read Event Grid event subscriptions. | No |
HDInsight Cluster Operator | Lets you read and modify HDInsight cluster configurations. | Yes |
HDInsight Domain Services Contributor | Can Read, Create, Modify and Delete Domain Services related operations needed for HDInsight Enterprise Security Package | Yes |
Intelligent Systems Account Contributor | Lets you manage Intelligent Systems accounts, but not access to them. | Yes |
Key Vault Contributor | Lets you manage key vaults, but not access to them. | Yes |
Lab Creator | Lets you create, manage, delete your managed labs under your Azure Lab Accounts. | Yes |
Log Analytics Contributor | Log Analytics Contributor can read all monitoring data and edit monitoring settings. Editing monitoring settings includes adding the VM extension to VMs, reading storage account keys to be able to configure collection of logs from Azure Storage, creating and configuring Automation accounts, adding solutions, and configuring Azure diagnostics on all Azure resources. | Yes |
Log Analytics Reader | Log Analytics Reader can view and search all monitoring data as well as and view monitoring settings, including viewing the configuration of Azure diagnostics on all Azure resources. | No |
Logic App Contributor | Lets you manage logic apps, but not change access to them. | Yes |
Logic App Operator | Lets you read, enable, and disable logic apps, but not edit or update them. | Yes |
Managed Application Operator Role | Lets you read and perform actions on Managed Application resources | Yes |
Managed Applications Reader | Lets you read resources in a managed app and request JIT access. | No |
Managed Identity Contributor | Create, Read, Update, and Delete User Assigned Identity | Yes |
Managed Identity Operator | Read and Assign User Assigned Identity | Yes |
Management Group Contributor | Management Group Contributor Role | Yes |
Management Group Reader | Management Group Reader Role | No |
Monitoring Contributor | Can read all monitoring data and edit monitoring settings. See also Get started with roles, permissions, and security with Azure Monitor. | Yes |
Monitoring Metrics Publisher | Enables publishing metrics against Azure resources | Yes |
Monitoring Reader | Can read all monitoring data (metrics, logs, etc.). See also Get started with roles, permissions, and security with Azure Monitor. | No |
Network Contributor | Lets you manage networks, but not access to them. | Yes |
New Relic APM Account Contributor | Lets you manage New Relic Application Performance Management accounts and applications, but not access to them. | Yes |
Reader and Data Access | Lets you view everything but doesn't let you delete or create a storage account or contained resource. It also allows read/write access to all data contained in a storage account via access to storage account keys. | Yes |
Redis Cache Contributor | Lets you manage Redis caches, but not access to them. | Yes |
Resource Policy Contributor (Preview) | (Preview) Backfilled users from EA, with rights to create/modify resource policy, create support ticket and read resources/hierarchy. | Yes |
Scheduler Job Collections Contributor | Lets you manage Scheduler job collections, but not access to them. | Yes |
Search Service Contributor | Lets you manage Search services, but not access to them. | Yes |
Security Admin | In Defender for Cloud only: Can view security policies, view security states, edit security policies, view alerts and recommendations, dismiss alerts and recommendations | Yes |
Security Manager (Legacy) | Security Manager is a legacy role. Use Security Administrator instead | Yes |
Security Reader | In Defender for Cloud only: Can view recommendations and alerts, view security policies, view security states but can't make changes | No |
Site Recovery Contributor | Lets you manage Site Recovery service except vault creation and role assignment | Yes |
Site Recovery Operator | Lets you failover and failback but not perform other Site Recovery management operations | Yes |
Site Recovery Reader | Lets you view Site Recovery status but not perform other management operations | No |
Spatial Anchors Account Contributor | Lets you manage spatial anchors in your account, but not delete them | Yes |
Spatial Anchors Account Owner | Lets you manage spatial anchors in your account, including deleting them | Yes |
Spatial Anchors Account Reader | Lets you locate and read properties of spatial anchors in your account | No |
SQL DB Contributor | Lets you manage SQL databases, but not access to them. Also, you can't manage their security-related policies or their parent SQL servers. | Yes |
SQL Managed Instance Contributor | Lets you manage SQL Managed Instances and required network configuration, but can't give access to others. | Yes |
SQL Security Manager | Lets you manage the security-related policies of SQL servers and databases, but not access to them. | Yes |
SQL Server Contributor | Lets you manage SQL servers and databases, but not access to them, and not their security -related policies. | Yes |
Storage Account Contributor | Permits management of storage accounts. Provides access to the account key, which can be used to access data via Shared Key authorization. | Yes |
Storage Account Key Operator Service Role | Permits listing and regenerating storage account access keys. | Yes |
Storage Blob Data Contributor | Read, write, and delete Azure Storage containers and blobs. To learn which actions are required for a given data operation, see Permissions for calling blob and queue data operations. | Yes |
Storage Blob Data Owner | Provides full access to Azure Storage blob containers and data, including assigning POSIX access control. To learn which actions are required for a given data operation, see Permissions for calling blob and queue data operations. | Yes |
Storage Blob Data Reader | Read and list Azure Storage containers and blobs. To learn which actions are required for a given data operation, see Permissions for calling blob and queue data operations. | No |
Storage Blob Delegator | Get a user delegation key, which can then be used to create a shared access signature for a container or blob that is signed with Azure AD credentials. For more information, see Create a user delegation SAS. | Yes |
Storage File Data SMB Share Contributor | Allows for read, write, and delete access in Azure Storage file shares over SMB | Yes |
Storage File Data SMB Share Elevated Contributor | Allows for read, write, delete and modify NTFS permission access in Azure Storage file shares over SMB | Yes |
Storage File Data SMB Share Reader | Allows for read access to Azure File Share over SMB | No |
Storage Queue Data Contributor | Read, write, and delete Azure Storage queues and queue messages. To learn which actions are required for a given data operation, see Permissions for calling blob and queue data operations. | Yes |
Storage Queue Data Message Processor | Peek, retrieve, and delete a message from an Azure Storage queue. To learn which actions are required for a given data operation, see Permissions for calling blob and queue data operations. | Yes |
Storage Queue Data Message Sender | Add messages to an Azure Storage queue. To learn which actions are required for a given data operation, see Permissions for calling blob and queue data operations. | Yes |
Storage Queue Data Reader | Read and list Azure Storage queues and queue messages. To learn which actions are required for a given data operation, see Permissions for calling blob and queue data operations. | No |
Support Request Contributor | Lets you create and manage Support requests | Yes |
Traffic Manager Contributor | Lets you manage Traffic Manager profiles, but doesn't let you control who has access to them. | Yes |
User Access Administrator | Lets you manage user access to Azure resources. | Yes |
Virtual Machine Administrator Login | View virtual machines in the portal and sign in as administrator | Yes |
Virtual Machine Contributor | Lets you manage virtual machines, but not access to them, and not the virtual network or storage account they're connected to. | Yes |
Virtual Machine User Login | View virtual machines in the portal and sign in as a regular user. | Yes |
Web Plan Contributor | Lets you manage the web plans for websites, but not access to them. | Yes |
Website Contributor | Lets you manage websites (not web plans), but not access to them | Yes |

## Next steps

- [Partner earned credit - an overview of how it works in the new commerce experience in CSP](partner-earned-credit.md)
