---
title: Relationships resources
description: Describes resources related to relationships.
ms.date: 6/17/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
ms.author: tugu
author: TusharGupta-pm
---

# Relationships resources

Describes resources related to relationships.

## PartnerRelationship

Represents a relationship between two partners.

| Property         | Type                                                           | Description                                                                                                                                    |
|------------------|----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| id               | string                                                         | The partner identifier. The partner identifier specifies the tenant id of the partner who is in the recipient (from) side of the relationship. |
| location         | string                                                         | The location of the partner.                                                                                                                   |
| partnerId            | string                                                         | The identifier of the partner.                                                                                 |
| name             | string                                                         | The name of the partner.                                                                                                                       |
| relationshipType | string                                                         | The type of relationship.                                                                                                                      |
| state            | string                                                         | The state of the relationship (for example `active`).                                                                                                 |
| attributes       | [ResourceAttributes](utility-resources.md#resourceattributes) | The metadata attributes.                                                                                                                       |

## RelationshipRequest

Provides the URL by which a customer can establish a relationship with a
partner.

| Property   | Type                                                           | Description                   |
|------------|----------------------------------------------------------------|-------------------------------|
| url        | string                                                         | The relationship request URL. |
| attributes | [ResourceAttributes](utility-resources.md#resourceattributes) | The metadata attributes.      |
