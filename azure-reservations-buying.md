---
title: Buy Microsoft Azure reservations for customers
description: Learn how to buy or purchase Azure reservations on behalf of your customers in Partner Center. Also lists markets where Azure reservations are unavailable.
ms.topic: how-to
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
author: iragulati1
ms.author: iragulati
ms.date: 08/23/2023
#acrolinx note: Spelling exceptions for 1) Reference to UI option, Microsoft Azure Management portal; 2) Reference to Åland Islands.
---

# Buy Microsoft Azure reservations on behalf of your customers

**Appropriate roles**: Admin agent | Sales agent

This article explains how to buy Azure reservations on behalf of your customers in Partner Center. It also identifies markets where Azure reservations are unavailable.

- This article applies only to partners in the Cloud Solution Provider (CSP) program.
- Customers using other types of subscriptions—such as, pay-as-you-go, individual, Microsoft Customer Agreement, or Enterprise Agreement subscriptions)—should  read [Save with Azure reservations](/azure/cost-management-billing/reservations) instead.

## Before you begin

> [!IMPORTANT]
> Review the following information before you buy Azure reservations on behalf of your customers.

- Azure reservations aren't available in all markets. To see a list of unavailable markets, see [Azure reservations—unavailable markets](#azure-reservationsunavailable-markets) at the end of this article.
- If you want customers to be able to buy their own Azure reservations from a prior Azure subscription you purchased for them, see [Give customers permission to buy their own Azure reservations](give-customers-permission.md#give-customers-permission-to-buy-their-own-azure-reservations).

- If your customer has signed the Microsoft Customer Agreement, you must purchase Azure reservations under the Azure plan.
  - For more information, see:
    - [Confirm customer acceptance of the Microsoft Customer Agreement](confirm-customer-agreement.md))
    - [Purchase the Azure plan for customers and access the latest Azure services](purchase-azure-plan.md).

- Customers must already have an active Azure subscription before you can purchase reservations on their behalf

- Software subscription costs (such as SQL Database or SUSE Linux software) aren't included in Azure reservation prices

- Commercial pricing from Microsoft to you doesn't include taxes (unless your location is Brazil, where the commercial price to you does include taxes).

- Sales agents and Help Desk agents need explicit access to the Azure subscription to:
  - Buy or manage a subscription in the Azure portal on behalf of the customer.
  - Make exchanges and refunds on behalf of the customer.
  - File support requests on behalf of the customer.

- If you're an indirect provider and you buy Azure reservations through the Azure portal, the Partner of Record (indirect reseller) is inherited from the Azure CSP subscription that you select.

- The Partner of Record for Azure reservations can't be changed post-purchase. You can cancel the existing reservation and purchase a new one with the new Partner of Record.

- If a customer wants to transfer an Azure subscription from Direct or EA to CSP, reservations don't get transferred.

## Purchase Azure reservations

> [!NOTE]
> If you want customers to be able to buy their own Azure reservations from a prior Azure subscription you purchased for them, see [Give customers permission to buy their own Azure reservations](give-customers-permission.md).

To buy Microsoft Azure reservations on behalf of your customers in Partner Center, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. On the **Customers** page, find the customer who wants to purchase Azure reservations and then select the down arrow to expand that customer's row.

3. Select **Add products** and then select **Azure**.

    a. Choose the customer's market segment from the **Segment** list.

    b. Choose **Reservations** from the product **Type** list.

    c. Choose the type of reservation the customer wants from the **Reservations type** list.

4. Choose the customer's subscription you want to add Azure reservations to from the **Customer subscription** list.

   > [!IMPORTANT]
   > Azure reservations must be associated with an active Azure subscription. If the customer doesn't already have an active Azure subscription, you can select **Azure** to add one.

5. Use the filters to find Azure reservations on virtual machines that meet your customer's requirements.

6. After you find the reservations you want to buy, enter the number of reserved instances the customer needs in **Quantity** and then select **Add to cart**.

7. Repeat steps 5 and 6 until you've added all the necessary items to the order and then select **Review** to verify that your order is correct.

   On the **Review your orders** page, you can:

    - Verify or change the reserved instances quantity.

    - Select the reservation's scope. The reservation's scope can cover one subscription or multiple subscriptions (shared scope).
      - If you scope the reservation to a single subscription, the reservation discount is applied to that subscription only.
      - If you select **Shared**, the reservation discount is applied to any subscriptions within the customer's billing context.

      > [!NOTE]
      > If you opt to limit the reservation's scope to a single Azure subscription, you might need to increase the subscription's vCPU quota. To increase the subscription's vCPU quota, create a support request in the Azure portal by following the instructions at [Increase regional vCPU quotas](/azure/azure-supportability/resource-manager-core-quotas-request).

      > [!NOTE]
      > If your customer is under the Azure plan, **Scope** will be set to **Shared** at time of purchase. That scope can be changed later.

    - If you're a provider partner, select the reseller that you want to associate with the product.

    - If your Azure reservation does support the Billing plan option, you can select monthly billing from the dropdown menu.
    - If your Azure reservation doesn't support the Billing plan option, billing frequency defaults to *one-time billing*.

8. Select **Buy** to purchase the order.
  
   The details of your order, including your order number, are displayed on the **Confirm** page.

9. Select **Done** to go to your **Order history** page.

10. To manage the customer's reservation in the Azure portal, find the customer on your **Customers** page and then select the down arrow to expand the customer's row. Select **Microsoft Azure Management Portal** to open the customer's record in the Azure portal.

## Azure reservations—unavailable markets

> [!IMPORTANT]
> Azure reservations **are not** available in the following markets:
>
> **Unavailable markets (in alphabetical order)**
>
> |A to Gi   | Gr to Pal  | Pap to Z |
> |--------------------------------|-----------------------------------|------------------------------------------|
> | Åland Islands     | Greenland     | Papua New Guinea     |
> | American Samoa     | Grenada     | Pitcairn Islands     |
> | Andorra     | Guadeloupe     | Reunion     |
> | Anguilla     | Guam     | Saba   |
> | Antarctica     | Guernsey     | Saint Barthélemy   |
> | Antigua and Barbuda       | Guinea     | Saint Lucia   |
> | Aruba       | Guinea-Bissau     | Saint Martin   |
> | Azerbaijan       | Guyana     | Saint Pierre and Miquelon   |
> | Benin     | Haiti       | Saint Vincent and the Grenadines     |
> | Bhutan     | Heard Island and McDonald Islands       | Samoa     |
> | Bonaire     | Isle of Man     | San Marino     |
> | Bouvet Island     | Jan Mayen     | São Tomé and Príncipe   |
> | British Indian Ocean Territory       | Jersey     | Seychelles   |
> | British Virgin Islands     | Kiribati       | Sierra Leone   |
> | Burkina Faso     | Kosovo     | Sint Eustatius     |
> | Burundi     | Laos     | Sint Maarten     |
> | Cambodia     | Lesotho     | Solomon Islands     |
> | Central African Republic     | Liberia     | Somalia     |
> | Chad     | Madagascar     | South Georgia and South Sandwich Islands     |
> | China     | Malawi     | South Sudan     |
> | Christmas Island     | Maldives     | St Helena, Ascension, Tristan da Cunha     |
> | Cocos (Keeling) Islands     | Mali     | Suriname     |
> | Comoros     | Marshall Islands     | Svalbard     |
> | Congo     | Martinique     | Swaziland     |
> | Congo (DRC)     | Mauritania     | Timor-Leste   |
> | Cook Islands     | Mayotte     | Togo   |
> | Djibouti     | Micronesia     | Tokelau   |
> | Dominica     | Montserrat     | Tonga   |
> | Equatorial Guinea     | Mozambique     | Turks and Caicos Islands   |
> | Eritrea     | Myanmar     | Tuvalu   |
> | Falkland Islands     | Nauru     | U.S. Outlying Islands   |
> | French Guiana     | New Caledonia     | Vanuatu   |
> | French Polynesia     | Niger     | Vatican City   |
> | French Southern Territories     | Niue     | Wallis and Futuna   |
> | Gabon     | Norfolk Island     | Yemen   |
> | Gambia     | Northern Mariana Islands     |    |
> | Gibraltar     | Palau       |    |

## Next steps

|**For information about**:   |**Read this**:    |
|:-----------------------------|:-----------------|
|Azure reservations in CSP  | [Sell Microsoft Azure Reserved Instances](azure-reservations.md) |
|Managing Azure reservations in Partner Center | [Managing Azure reservations in Partner Center](azure-reservations-manage.md)
|Determine the correct VM size and verify customer VM usage   |[VM sizing for maximum Azure reservation usage](azure-usage.md)   |
|Purchasing Azure reservations using the Partner Center API | [Purchase Azure Reserved VM Instances](/partner-center/develop/purchase-azure-reservations) in the Partner Center developer documentation   |
|Giving customers permission to buy their own Azure reservations  | [Give customers permission to buy their own Azure reservations](give-customers-permission.md)  |
