---
title: Reference architecture diagram 
description: How to create a reference architecture diagram for a solution in the Microsoft commercial marketplace. 
ms.reviewer: stmummer
ms.service: partner-dashboard 
ms.subservice: partnercenter-referrals
ms.topic: reference
author: Saksham-PM
ms.author: sasolanki
ms.date: 08/24/2023
---

# Reference architecture diagram

**Appropriate roles**: Co-sell solution admin

A *reference architecture diagram* is a model of the infrastructure that your Microsoft commercial marketplace solution relies on.

For Azure intellectual property (IP) solutions, the diagram should also show how your solution uses Microsoft's cloud services per the technical requirements of IP co-sell.

A reference diagram isn't intended to assess the quality of an architecture. It's intended to show how your solution uses Microsoft services.

You can create a reference architecture diagram using various tools. However, we recommend Microsoft Visio because it has [Azure Architecture models](/azure/architecture/browse/) that you can use as a helpful starting point.

## Typical components of a reference architecture diagram

Your reference architecture diagram must clearly identify your IP as a solution, application, or service code that is both *deployed on* and *driving consumption of* Microsoft Azure.

Your code must be highly reusable and not depend on extensive customization per deployment.

Typical components of a reference architecture diagram include:

- *Cloud services* that host and interact with your solution, including ones that consume Azure resources
- *Cloud services* used to control security, authentication, and users of your solution
- *Data connections*, *data layers*, and *data services* consumed by your solution
- *User interfaces* and other services that expose the solution to users
- Hybrid or on-premises *connectivity and integrations* or combinations of both.

###### Example reference architecture diagram: vertical industry chatbot

:::image type="content" source="./media/referrals/co-sell-arch-diagram.png" alt-text="This image is an example Co-sell architecture diagram." lightbox="./media/referrals/co-sell-arch-diagram.png":::

The image is an example of a reference architecture diagram. It's a diagram of a vertical industry chatbot that can be integrated with intranet sites to help forecast demand scenarios using a machine learning algorithm. It uses supply-chain and manufacturing-schedule data from various enterprise resource planning (ERP) systems. The bot is designed to address questions about when a salesperson can commit to possible delivery dates for an order.

## Next steps

- [Configure co-sell solution](./co-sell-configure.md)
