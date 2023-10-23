---
title: Margin resources
description: Resources that represent margins. Includes resources for describing the margins.
ms.date: 09/30/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: migolova
ms.author: migolova
---

# Margin resources

Resources that represent available margins. Includes resources for describing a margin.  

Independent Software Vendor (ISV) may create discounts or margins for specific Cloud Solution Providers (CSPs). Below are resources that represent and describe margins.
				
## Margin					
						
Represents an avalable margin for a given CSP.
				
| Name            | Type            | Description                               |
|-----------------|-----------------|-------------------------------------------|
| id              | string          | Unique identifier for the margin.         |
| marginPercentage | number         | A percentage discount applied to the CSP retail price.  |
| productId       | string          | The product ID the margin is available for.   |
| productTitle    | string          | The product title the margin is available for. |
| productType     | string          | The product type the margin is available for.   |
| publisherName   | string          | The name of the ISV who created the margin.  |
| skuId           | string          | The SKU ID the margin is available for.  |
| skuTitle        | string          | The SKU title the margin is available for. |
| startDate       | string          | The start date the margin is available. |
| endDate         | string          | The end date the margin in is available. |
| status          | string          | Status indicting whether the margin is available. |
| statusDate      | string          | The date the status was last updated. |

## Definitions

Different types of artifacts describing margins.					

| Name            | Description          |
|-----------------|----------------------|
| Margin |  Defines an individual margin.  | 	
| MarginSearchResponse |  Defines the margin response data.  | 	
		
## Related documentation

- [Margins in Partner Center overview](../csp-commercial-marketplace-margins.md)
- [Purchase marketplace offers](../csp-commercial-marketplace-purchase.md)
- [Manage marketplace offers](../csp-commercial-marketplace-manage.md)
- [Get a list of margins](get-margins.md)
- [Download a list of margins](download-margins.md)