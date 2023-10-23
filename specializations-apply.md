---
title: Apply for specializations
ms.topic: how-to
ms.service: partner-dashboard
ms.subservice: partnercenter-membership
description: Strengthen your business profile in the Microsoft partner directory. Learn how to use Partner Center to apply for and earn advanced specializations.
author: pavankumarMSFT
ms.author: vgandhikota
ms.date: 07/11/2023
---

# Use Partner Center to apply for specializations and check their status

**Appropriate roles**: Global admin | MPN Partner Admin

This article describes how to use Partner Center to:

- Apply for a [specialization](./specializations.md).
- Complete the required steps and validations for a specialization, including specializations that require an audit or customer references.
- Track your progress toward attaining a specialization.

To learn more about the benefits of specializations and what's required to attain them, see [Microsoft AI Cloud Partner Program specializations](https://partner.microsoft.com/membership/advanced-specialization).

## Prerequisites for specializations

To qualify for a specialization, you must first fulfill certain prerequisites, such as earning [a Solutions Partner designation](introduction-to-pcs.md) in a related area. Then you can apply for the specialization in Partner Center and complete the required steps and Microsoft validations.

## Use Partner Center to apply for specializations and track your progress

Much of the process for applying for a specialization is available at **Membership > Specializations** in Partner Center.

> [!NOTE]
> Only users with the *MPN Partner admin* or *Global admin* user roles for their organization's Microsoft partner account have access to the **Membership > Specializations** section.

### Access the specializations area and track your status

To access specializations and track your status, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) as an MPN Partner admin or Global admin and select **Membership**.
1. Select **Specializations** and then select the area you're interested in:
   - *Azure*
   - *Modern work*
   - *Security*
   - *Business applications*
1. Select the name of a specialization to see requirements and steps, your status, and links to further steps and resources.
   - You can return to the **Membership > Specializations** area of Partner Center to check your progress toward attaining an advanced specialization.
   - After you've completed all the requirements for a specialization, you can check to see if your status has changed to *Active* for the specialization you chose. *Active* status automatically enables an advanced specialization tag on your business profile. This profile is visible to all customers trying to [find a solution provider](https://www.microsoft.com/solution-providers/home).

## Complete an audit or include customer references

To earn a specialization, you must earn an aligned [Solutions Partner designation](introduction-to-pcs.md) and fulfill other prerequisites unique to that specialization.

To earn some specializations, you must also:

- [Complete an audit with a third-party auditor](#complete-an-audit-with-a-third-party-auditor)
- [Provide customer references](#provide-customer-references)

Both tasks can be performed in Partner Center.

### Specializations that don't require an audit or customer references

Specializations that don't require an audit or customer reference include:

- Microsoft Low Code Application Development
- Small and Midsize Business Management
- Sales 
- Service 
- Finance 
- Supply Chain
- Intelligent Automation
- Business Intelligence

### Specializations that require an audit with a third-party auditor

Specializations that require an audit from a third-party auditor include:

- Analytics on Microsoft Azure
- Build and Modernize AI Apps with Microsoft Azure 
- Data Warehouse Migration to Microsoft Azure
- Kubernetes on Microsoft Azure
- Infra and Database migration to Microsoft Azure
- Microsoft Azure Virtual Desktop
- Migrate Enterprise Applications to Microsoft Azure 
- AI and Machine Learning on Microsoft Azure
- Hybrid Cloud Infrastructure with Microsoft Azure Stack HCI
- Microsoft Azure VMware Solution
- DevOps with GitHub on Microsoft Azure
- Networking Services in Microsoft Azure
- SAP on Microsoft Azure

#### Complete an audit with a third-party auditor

In addition to fulfilling a specialization's prerequisites, you must pass a *scheduled audit* to earn some specializations.

To schedule an audit, follow these steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) as an MPN Partner admin or Global admin and select **Membership**.
1. Select **Specializations**, and then select *Azure*.
1. Select the name of a specialization, for example, *Modernization of Web Applications to Microsoft Azure*.
   - The prerequisites for the specialization appear.
1. Select **Schedule audit**.
   - The **Schedule audit** button isn't available and your status is **Not started** until you meet all the prerequisites on the page.
   - After you meet all the prerequisites and complete the audit, your status changes to **Active**.

### Specializations that require customer references

In addition to fulfilling prerequisites, you must also provide customer references to earn some specializations.

Specializations that require customer references include:

- Adoption and Change Management
- Calling for Microsoft Teams
- Custom Solutions for Microsoft Teams
- Meetings and Meeting Rooms for Microsoft Teams
- Modernize Endpoints
- Teamwork Deployment
- Identity and Access Management
- Threat Protection
- Information Protection and Governance
- Cloud Security

#### Provide customer references

To provide customer references in Partner Center, follow these steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) as an MPN Partner admin or Global admin and select **Membership**.
1. Select **Specializations**, and then select an area you're interested in:
   - *Modern work*
   - *Security*
1. Select the name of the specialization.
   - The prerequisites for the specialization appear. As an example, for the *Meetings and Meeting Rooms for Microsoft Teams* specialization, in addition to a Solutions Partner designation, certifications and a performance requirement, you must also provide three customer references that demonstrate your ability to deploy and manage.
      - Until you meet all the prerequisites and provide customer references, your status is **Not Started**.
      - After you meet all the prerequisites and provide the required references, your status changes to **Active**.

## How Azure consumption revenue is calculated for each specialization

Partner-to-customer associations include:

- [Digital Partner of Record](./link-partner-id-for-azure-performance-pal-dpor.md) association with a customer
- CSP direct-bill partner or CSP indirect reseller for a customer
- [Partner Admin Link (PAL)](/azure/cost-management-billing/manage/link-partner-id) association with a customer

Not counted toward the specialization is Azure consumption revenue (ACR) from subscriptions to the following types of offers:

- Trial
- Benefits programs
- Support
- Internal

### Azure consumption revenue fields

| Field name | Field description |
|-------------|----------------------|
| Service Level 1 | Highest level at which Azure services are bundled. See [Directory of Azure Cloud service](https://azure.microsoft.com/services/). |
| Service Level 2 | Second-highest level Azure Services based, for example [Pricing overview - How Azure pricing works](https://azure.microsoft.com/pricing/) |
| Service Level 3 | Third-highest level Azure Services based, for example [Pricing - Linux virtual machines](https://azure.microsoft.com/pricing/details/virtual-machines/linux/) |
| Service Level 4 | Fourth-highest level Azure Services based, for example [Pricing - Linux virtual machines](https://azure.microsoft.com/pricing/details/virtual-machines/linux/) |
| Service Group 2 | Grouping of Azure services according to a service category |
| Service Group 3 | Grouping of Azure services according to a service subcategory |
| Service Influencer | Grouping of Azure services mapped to a specific consumption activity |
| Compute OS | Compute Operating System |
| Compute Core Software | Compute Core Software |

#### Azure consumption revenue filters for specialization

- Data Warehouse Migration to Microsoft Azure
  - Azure Synapse Analytics ACR: Service Level 2 = Azure Synapse Analytics
- Kubernetes on Microsoft Azure
  - Azure Kubernetes Service (AKS) ACR: Service Influencer = AKS, AKS-Engine
  - Azure RedHat OpenShift ACR: Service Group 3 = ARO, Service Level 2 = All except "Unknown"
- Microsoft Azure Virtual Desktop
  - Microsoft Azure Virtual Desktop ACR: Service Influencer = NATIVE AVD
- Modernization of Web Applications to Microsoft Azure
  - Azure App Service ACR: Service Level 1 = Compute and Service Level 2 = Azure App Service
    - Azure Spring Cloud ACR:
      - ACR Adjustment Type = N/A
      - Service Group 2 = App Dev
      - Service  Group 3 = Spring Cloud
      - Service Level 2 = All except "Unknown"
- Analytics on Microsoft Azure
  - Azure Synapse Analytics ACR: Service Level 2 = Azure Synapse Analytics
  - Data Lake ACR:   Service Group 3 = Azure Data Lake
  - Databricks  ACR:  Service Group3 = Databricks
  - Azure Data Factory ACR: Service Level 2 = Azure Data Factory, Azure Data Factory v2
- Hybrid Cloud Infrastructure with Microsoft Azure Stack HCI
  - Azure Stack HCI ACR: Service Level 2 = Azure Stack HCI
- Microsoft Azure VMware Solution
  - Azure VMware Solutions (AVS) ACR: Service Level 4 = Azure VMware Solution, Azure VMware Solution by CloudSimple, Azure VMware Solution by Virtustream, Specialized Compute Azure VMware Solution
- AI and Machine Learning on Microsoft Azure
  - AI ACR: Service Group 2 = AI
- Build and Modernize AI Apps with Microsoft Azure 
  - Azure Kubernetes Service (AKS) ACR: Service Group3 = AKS
  - Azure RedHat OpenShift ACR: Service Group 3 = ARO
  - Azure Spring AppsACR: Service Group3 = Azure Spring cloud
  - Azure Cosmos DB: Service Group 3 = Cosmos DB
  - Azure database for Postgresql: Service Group 3 = PGSQL
  - Azure Cognitive Services: Service Group 3 = Cognitive Services
  - Azure Machine Learning: Service Group 3 = Azure Machine Learning
  - Azure Open AI service: Service Group 3 = Applied AI Services 
- Infra and Database migration to Microsoft Azure
  - Windows ACR:
    - ACR Adjustment Type = N/A, Compute Core SW = Core,
    - Compute OS = WINDOWS THEN Compute OS Attribute = WINDOWS, UNKNOWN or Compute OS = LINUX THEN Compute OS Attribute = WINDOWS-AHUB
      - Service Level 2= Cloud Services, Container Instances, Container Registry, Specialized Compute, Virtual Machines, Virtual Machines Licenses
    - SQL Database (DB) ACR: Service Group 3 = SQLDB
    - SQL Managed Instance (MI) ACR: Service Group 3 = SQL DB MI
    - SQL VM ACR: Service Group 3 = SQL on IaaS, SQL on IaaS VM  
  - Linux Virtual Machines (VM)ACR:
    - Option 1:
      - ACR Adjustment Type= N/A, Service Level 2 = Virtual Machines, Compute OS= Linux, Compute OS Attribute = Non-Windows, UNKNOWN, Windows
      - Service Level 4 =  All EXCEPT Cloud Services MS Series, Virtual Machines MS Series, Virtual Machines MS Series Windows, Virtual Machines MSv2 Series, Virtual Machines MSv2 Series Windows, MS Series Dedicated Host, MSv2 Series Dedicated Host
    - Option 2: only require filters on Service Level 4, other fields like Compute OS/Compute OS Attributes aren't required
      - Service Level 4 = Red Hat Enterprise Linux, Red Hat Enterprise Linux with HA, SUSE Linux Enterprise Server Basic, SUSE Linux Enterprise Server for HPC Priority, SUSE Linux Enterprise Server for HPC Standard, SUSE Linux Enterprise Server Priority, SUSE Linux Enterprise Server Standard
    - Azure Database (DB) for MariaDB ACR: Service Level 1 = Databases and Service Level 2 = Azure Database for MariaDB
    - Azure DB for MySql ACR: Service Level 1 = Databases and Service Level 2 = Azure Database for MySQL and MySQL Database on Azure
    - Azure DB for PostgreSQL ACR: Service Level 1 = Databases and Service Level 2 = PostgreSQL
    - Azure COSMOS DB ACR: Service Level 1 = Databases Level 2 = Cosmos DB
- Threat Protection
  - Microsoft Sentinel ACR: Service Level 4 = Sentinel
- Cloud Security
  - Hybrid Environment XDR and Network Security ACR: Service Level 4 = Microsoft Defender for SQL, Microsoft Defender for container registries, Microsoft Defender for Kubernetes, Microsoft Defender for Storage, Application Gateway WAF v2, WAF Application Gateway, Azure Active Directory B2C, Azure Active Directory Domain Services, Azure Active Directory for External Identities, Azure Bastion, Azure DDOS Protection, Azure Firewall, Azure Firewall Manager, Azure Front Door Service, Microsoft Defender for IoT, Azure Dedicated HSM, Key Vault, Network Watcher, Microsoft Defender for App Service, Microsoft Defender for servers, Sentinel
- SAP on Microsoft Azure
  - SAP Workloads ACR: Service Level 4 = Cloud Services MS Series, Virtual Machines MS Series, Virtual Machines MS Series Windows, Virtual Machines MSv2 Series, Virtual Machines MSv2 Series Windows, MS Series Dedicated Host, MSv2 Series Dedicated Host, SAP HANA on Azure Large Instances,SAP Cloud Platform Alert Notification, SAP Cloud Platform Extension Factory - Kyma Runtime,SAP Cloud Platform Integration Suite - Additional Messages, SAP Cloud Platform Integration Suite - Standard Edition, SAP Cloud Platform Transport Management, SAP Edge Services, SAP Embrace API Management,SAP Embrace Application Logging, SAP Embrace Application Runtime, SAP Embrace Bandwidth, SAP Embrace Business Application Studio, SAP Embrace Business Rules, SAP Embrace Cloud Integration, SAP Embrace Credential Store, SAP Embrace Custom Domain, SAP Embrace Data Intelligence, SAP Embrace Enterprise Messaging, SAP Embrace Extension Factory, serverless runtime, SAP Embrace HANA Cloud, SAP Embrace Identity Authentication, SAP Embrace Job Scheduler, SAP Embrace MACC, SAP Embrace Mobile Services,SAP Embrace Object Store Service, SAP Embrace Open Connectors, SAP Embrace Portal, SAP Embrace Process Visibility, SAP Embrace Web Analytics, SAP Embrace Workflow, SAP HANA Service, SAP Web IDE, BareMetal Infrastructure, Virtual Machines MdSv2 Series, Virtual Machines MdSv2 Series Windows

### Data freshness

_Performance_ is typically refreshed by the 20th of every month. However, there may be more minor data refreshes throughout the month.

_Skilling_ subcategories are typically refreshed within 10 days after certification is complete.

## Next steps

- [Specializations, their benefits, and unique requirements](./specializations.md).
- [Attaining Solutions Partner designations](./introduction-to-pcs.md).