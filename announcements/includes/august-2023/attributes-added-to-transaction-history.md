---
title: include file
ms.topic: include
author: deeparamani
ms.author: deramani
ms.date: 08/09/2023
---

## Attributes added to default Transaction history template

_On August 7, 2023, we added the ability to see more reconciliation details in the default transaction history template._

- **Date**: August 9, 2023
- **Workspace**: Payouts
- **Impacted audience**: Incentive user, Incentive admin, and Account owner for Marketplace

New attributes are visible on the right side of the default Transaction history template. These attributes show transaction history going back to October 1, 2021. These attributes show more reconciliation details. The newly introduced attributes and their definitions are listed in the following table. You can also access these new details through the Partner Center API.


| **Attribute Name**                                                      | **Description**                                                                                                                                                                                                                                                             | **Applicability**                                                                                                                                                    |
| ---------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| solutionArea                                                           | High level product categorization, for example, Azure, ModernWork and Security.                                                                                                                                                                                                     | For Microsoft Commerce Incentives only. Available from October 2021.                                                                                                 |
| partnerRole                                                            | Categorization of the kind of engagement. Examples include build intent, transact, deploy and use.                                                                                                                                                                                       | For Microsoft Commerce Incentives only. Available from October 2021.                                                                                                 |
| partnerAssociation                                                     | Type of relationship partner has to a customer, for example, reseller, PAL.Contributor. In the event a partner is a PAL.Owner or PAL.Contributor this attribute shows PAL.Contributor.                                                                                           | For all incentive, store and marketplace programs. Available from October 2021.                                                                                      |
| earningParticipantId<br>earningParticipantIdType<br>earningParticipantName | Partner identity in the transact relationship                                                                                                                                                                                                                               | For all incentive, store and marketplace programs. Useful when multiple transacting partner IDs are mapped into a single enrollment ID. Available from October 2021. |
| quantityType                                                           | Indicates the type of quantity. For example, MAU (monthly active users), Seats                                                                                                                                                                                                                             | For all incentive programs only. Available from October 2021.                                                                                                        |
| quantityAlt                                                            | Alternate quantity value                                                                                                                                                                                                                                                    | Optionally available for incentive programs. For example, Modern Work usage. Available only from October 2023.                                                           |
| quantityAltType                                                        | Alternate quantity unit, for example, PAU (Paid available units)                                                                                                                                                                                                                     | Optionally available for incentive programs, for example, for Modern Work usage. Available only from October 2023.                                                           |
| compensableUnits                                                       | Compensable Units are calculated by subtracting the Prior HWM (High Water Mark) at the start of the month by Tenant/workload from the paid seats at the end of the month by Tenant/workload. For example, Compensable units by tenant and workload= Paid seats – Prior HWM. | Applicable for Microsoft Commerce Incentives – Modern Workplace Usage and Online Advisor. Available only from October 2023.                                          |

#### Next steps

Refer to the complete list of attributes available in the [Transaction history report download schema](../../../transaction-history.md#transaction-history-download).
