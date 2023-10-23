---
title: Available Azure services in Azure CSP
description: This article discusses the Azure services that are and aren't available in the Azure Cloud Solution Provider (CSP) program.
ms.topic: article
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
author: brentserbus
ms.author: brserbus
ms.date: 02/28/2022
---

# Azure services available in the Azure Cloud Solution Provider (CSP) program

**Appropriate roles**: Admin agent | Billing admin | Global admin | Helpdesk agent | Sales agent | User management admin

## Available Azure services in Azure CSP

This article lists the Azure services that are and aren't available in the Azure Cloud Solution Provider (CSP) program. It also discusses service availability in the national clouds [Microsoft Azure Germany](https://azure.microsoft.com/overview/clouds/germany/) and [Microsoft Azure Government](https://azure.microsoft.com/overview/clouds/government/).

> [!NOTE]
> [Azure China](https://www.azure.cn/) is not available in the Azure CSP program.

## Global Cloud

All services based on Azure Resource Manager model are available in CSP Program.  Non-Azure Resource Manager services such as classic deployment model services aren't available in CSP program.

## CSP-Specific Service Configurations

The following services require special configurations in CSP:

- [StorSimple](/azure/storsimple/storsimple-partner-csp-overview)

- [Azure Active Directory Domain Services](/azure/active-directory-domain-services/active-directory-ds-csp)

- [Azure Time Series Insights](https://azure.microsoft.com/services/time-series-insights/) Only users from the customer tenant can access data in their Time Series Insights environment. Partners can manage their customer's Time Series Insights environment by default, but if they need access to the data in it, they must be added to the customer tenant.

- Management Certificates for authenticating Azure SDK libraries via certificate aren't supported in CSP model.  Utilize Azure AD service principal authentication and the Azure.Identity library instead.  Reference [Authenticate with the Azure SDK for .NET](/dotnet/azure/sdk/authentication)

## Visual Studio Marketplace

You can now purchase the items listed below from Visual Studio Marketplace, except for third-party extensions.

- [Azure DevOps](https://www.visualstudio.com/team-services/)

- [Visual Studio subscriptions](https://www.visualstudio.com/subscriptions/)

- [Xamarin University training](https://marketplace.visualstudio.com/items?itemName=ms.xamarin-university)

## Azure Marketplace items in Azure CSP

Not all Azure Marketplace items are currently available in Azure CSP subscriptions.

- Microsoft-based Azure services: These services are available. Review the previous table and comments.

- Bring your own license (BYOL) items: These items are available. A full list of BYOL-enabled Azure Marketplace items is available on the [Azure Marketplace BYOL page](https://azuremarketplace.microsoft.com/marketplace/apps?filters=byol).

- Pay-As-You-Go third-party Azure Marketplace items: These items are available if the provider has published to the CSP channel. For more information, see [Sell subscriptions to Azure Marketplace products](csp-commercial-marketplace-overview.md).

- Citrix XenApp Essentials: Partners can purchase XenApp Essentials for customers in CSP. For more information, see the following Citrix blog- [Distribution of XenApp Essentials now available through Microsoft Cloud Solution Provider Channel](https://www.citrix.com/blogs/2018/02/01/xenapp-essentials-now-available-through-microsoft-cloud-solution-provider-channel/).

## National clouds

The following table displays a regularly updated list of the available first-party Azure products, services, and features for CSP in national clouds.

| Azure product, service, or feature | US Government | Germany |
| ------ | :-----------: | :-----------: |
|  **Compute**  |    |    |
|  Virtual Machines  |  X  |  X  |
|  Cloud Services  |    |    |
|  Virtual machine scale sets  |  X  |  X  |
|  Functions  |    |    |
|  Azure Container Service  |    |    |
|  **Networking**  |    |    |
|  Azure DNS  |    |    |
|  Content Delivery Network  |    |    |
|  Traffic Manager  |    |    |
|  ExpressRoute  |  X  |  X  |
|  Virtual Network  |  X  |  X  |
|  Load Balancer  |  X  |  X  |
|  VPN Gateway  |  X  |  X  |
|  Application Gateway  |  X  |  X  |
|  Network Watcher  |  X  |  X  |
|  **Storage**  |    |    |
|  Storage  |  X  |  X  |
|  Backup  |  X  |  X  |
|  StorSimple  |    |  X  |
|  Site Recovery  |  X  |  X  |
|  Data Lake Store  |    |    |
|  Managed Disks  |  X  |  X  |
|  **Web + Mobile**  |    |    |
|  App Service  |  X  |  X  |
|  App Service on Linux  |    |  X  |
|  API Management  |  X  |    |
|  Content Delivery Network  |    |    |
|  Media Services  |  X  |  X  |
|  Notification Hubs  |  X  |  X  |
|  Azure Search  |    |    |
|  Logic Apps feature of Azure App Service  |    |    |
|  **Containers**  |    |    |
|  App Service  |  X  |  X  |
|  App Service on Linux  |    |  X  |
|  Batch  |  X  |  X  |
|  Container Registry  |    |    |
|  Container Instances  |    |    |
|  Service Fabric  |  X  |  X  |
|  Container Service  |    |    |
|  **Databases**  |    |    |
|  SQL Database  |  X  |  X  |
|  Azure Cosmos DB  |  X  |  X  |
|  SQL Data Warehouse  |  X  |  X  |
|  Redis Cache  |  X  |  X  |
|  SQL Server Stretch Database  |  X  |  X  |
|  Azure Database for MySQL  |    |    |
|  Azure Database for PostgreSQL  |    |    |
|  **Data + Analytics**  |    |    |
|  Databricks  |    |    |
|  HDInsight  |  X  |  X  |
|  Stream Analytics  |    |  X  |
|  Data Factory  |    |    |
|  Log Analytics  |  X  |    |
|  Data Catalog  |    |    |
|  Data Lake Store  |    |    |
|  Data Lake Analytics  |    |    |
|  Azure Analysis Services  |    |    |
|  Power BI Embedded  |    |    |
|  **AI + Cognitive Services**  |    |    |
|  Machine Learning  |    |  X  |
|  Azure Bot Service  |    |    |
|  Cognitive Services  |    |    |
|  Azure Batch AI  |    |    |
|  **Internet of Things**  |    |    |
|  IoT Hub  |  X  |  X  |
|  IoT Central  |    |    |
|  Machine Learning  |    |  X  |
|  Stream Analytics  |    |  X  |
|  Event Hubs  |  X  |  X  |
|  Location-Based Services  |    |    |
|  Notification Hubs  |  X  |  X  |
|  Time Series Insights  |    |    |
|  **Enterprise Integration**  |    |    |
|  StorSimple  |  X  |    |
|  API Management  |    |    |
|  Event Grid  |    |    |
|  Data Factory  |    |    |
|  Service Bus  |  X  |  X  |
|  Data Catalog  |    |    |
|  SQL Server Stretch Database  |    |  X  |
|  Logic Apps feature of Azure App Service  |    |    |
|  **Security + Identity**  |    |    |
|  Azure Active Directory  |  X  |  X  |
|  Azure Active Directory B2C  |    |    |
|  Multifactor authentication  |    |    |
|  Azure Active Directory Domain Services  |    |    |
|  Key Vault  |  X  |  X  |
|  Defender for Cloud  |  X  |  X  |
|  **Developer Tools**  |    |    |
|  Visual Studio Team Services  |    |    |
|  Application Insights  |    |    |
|  DevTest Labs  |    |    |
|  Visual Studio App Center  |    |    |
|  Xamarin University  |    |    |
|  **Monitoring + Management**  |    |    |
|  Advisor  |    |    |
|  Backup  |  X  |  X  |
|  Site Recovery  |  X  |  X  |
|  Scheduler  |  X  |  X  |
|  Automation  |  X  |  X  |
|  Log Analytics  |  X  |    |
|  Azure Monitor  |    |    |
|  Azure-Managed Applications  |    |    |
|  Azure Migrate  |    |    |
|  Management Groups  |    |

## Next steps

- [Learn](/azure/cloud-solution-provider/overview/partner-center-overview) about the available capabilities for Azure in Partner Center.

- [Create](/azure/cloud-solution-provider/customer-management/create-new-customer) your first customer in Azure CSP, and deploy Azure services.
