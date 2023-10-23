---
title: Managed service resources
description: Managed services are services to which a partner has delegated admin privileges. Partners can provide support for and file service requests on the behalf of their managed services.
ms.date: 06/13/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: migolova
ms.author: migolova
---

# Managed service resources

**Applies to**: Partner Center | Partner Center operated by 21Vianet |  Partner Center for Microsoft Cloud for US Government

Managed services are services to which a partner has delegated admin
privileges. Partners can provide support for and file service requests
on the behalf of their managed services.

## ManagedService

Describes a managed service.

| Property   | Type                | Description                                              |
|------------|---------------------|----------------------------------------------------------|
| Id         | string              | The managed service ID.                                  |
| Name       | string              | The name of the managed service.                         |
| GroupName  | string              | The name of the group to which the service belongs.      |
| Links      | ManagedServiceLinks | The resource links corresponding to the managed service. |
| Attributes | ResourceAttributes  | The metadata attributes corresponding to the agreement.  |

## ManagedServiceLinks

Contains the links that allow the partner with delegated admin
permissions to provide support for the service.

| Property      | Type | Description                 |
|---------------|------|-----------------------------|
| AdminService  | Link | The admin service URI.      |
| ServiceHealth | Link | The service health URI.     |
| ServiceTicket | Link | The service ticket URI.     |
| Self          | Link | The self-URI.               |
| Next          | Link | The next page of items.     |
| Previous      | Link | The previous page of items. |

