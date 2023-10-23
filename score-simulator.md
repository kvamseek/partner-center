---
title: Score simulator
ms.topic: article
ms.date: 03/15/2022
description: Learn about the Solutions Partner program Score simulator
ms.service: partner-dashboard
ms.subservice: partnercenter-insights
author: vivekmohanms
ms.author: vivekmo
---

# Score simulator

**Appropriate roles**: MPN Partner Admin | Global Admin | Executive report viewer (Organizational level)

The [Solutions Partner score simulator](https://partner.microsoft.com/dashboard/insights/mpninsights/solutionspartner?tabName=ScoreSimulator&source=docs) can help you to understand the Solutions Partner program and how its performance can affect scores in the respective solution areas. It can also help with strategic planning and exploration. It's useful for planning the best course of action to take based on the simulated effect that certain actions have on your [partner capability score](partner-capability-score.md).

There are two ways to interact with the Score simulator:

- [Score simulator](#score-simulator)
  - [Recommendations](#recommendations)
  - [Custom selection](#custom-selection)
  - [How it works](#how-it-works)
  - [Assumptions](#assumptions)
  - [Next steps](#next-steps)

> [!NOTE]
>Simulated results are based on approximations. Actual scores are calculated from actual data that considers the criteria of respective solution areas.

## Recommendations

In this view, partners can see the effect of various recommendations.

There are two key actions in this view:

- View the effect of the recommendation on a simulated result.
- Select multiple recommendations to view a combined effect.

:::image type="content" source="media/simulator-recommendation.png" lightbox="media/simulator-recommendation.png" alt-text="Shows the Score simulation recommendation.":::

## Custom selection

In this view, partners can key in customer details that can be finalized in the future.

:::image type="content" source="media/score-customers.png" lightbox="media/score-customers.png" alt-text="Screenshot showing the score simulation customer detail.":::

Multiple customer details can be added to the simulation.

:::image type="content" source="media/customer-detail.png" lightbox="media/customer-detail.png" alt-text="Screenshot showing multiple customer details.":::

Certification details can be added as well.

:::image type="content" source="media/score-certification-details.png" lightbox="media/score-certification-details.png" alt-text="Screenshot showing customer certification details.":::

The simulated result is based on the details entered.

:::image type="content" source="media/simulated-results.png" lightbox="media/simulated-results.png" alt-text="Shows simulated results.":::

You can view changes in the actual value and changes in the score. Use the toggle button on the top of the side panel to show the current score versus the simulated one.

:::image type="content" source="media/value-changes.png" lightbox="media/value-changes.png" alt-text="Shows value changes.":::

## How it works

The score simulator considers the current scorecard as its baseline. Based on input from partners, the simulator evaluates whether there's any effect on the scores given the solution areas requirements.

> [!NOTE]
>Any other Azure service in the **Workloads** dropdown suggests all Azure services are applied to the simulation except for Virtual Machines, Virtual Machine Licenses, Sentinel, Azure Defender, Network Security, Intune, Identity and Access Management.

## Assumptions

- For the security solution area _skilling_ metric, the simulation assumes that partners already have the Microsoft 365 Security Administrator Associate _and_ Azure Security Engineer certifications. Adding at least one of the options leads to an increase in the certified individual count:
  - Microsoft Security Operations Analyst _or_
  - Microsoft Identity and Access Administrator _or_
  - Microsoft Purview Information Protection Administrator
- For the security deployment simulations, customers already have 15 percent of monthly protected users deployed.
- Prerequisites for certifications are not considered a part of simulation. If there is a prerequisite required for a certification (intermediate or advanced), the individual needs to complete it before being considered for the actual certification.

> [!NOTE]
> These results are a simulation. Actual results may vary based on your performance. The results from the simulator tool do not guarantee Solution partner designation.

## Next steps

- [Link a PartnerID for PAL](link-partner-id-for-azure-performance-pal-dpor.md)
- [Link a PartnerID for CSP Tier 1 or 2](connect-with-your-customers.md)
- [Link a PartnerID for CPOR](submit-osa-claim.md)
- [Learn how to improve your score](https://partner.microsoft.com/asset/collection/pci-learn#/)
- [Solutions Partner for all Azure areas](solutions-partner-azure.md)
- [Solutions Partner for Business applications](solutions-partner-business.md)
- [Solutions Partner for Modern work](solutions-partner-modern-work.md)
- [Solutions Partner for Security](solutions-partner-security.md)
