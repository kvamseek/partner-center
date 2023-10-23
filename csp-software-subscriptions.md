---
title: Sell software subscriptions through CSP
ms.topic: how-to
ms.date: 06/30/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Learn how partners in the CSP program can use Partner Center to buy, manage, sell, and cancel Azure reserved instances and server subscriptions for customers.
author: denysseD
ms.author: DenysseDiaz
#content note: Azure Reservations unavailable markets list current as of November 30 2019.
---

# Sell software subscriptions through the Cloud Solution Provider (CSP) program

**Appropriate roles**: Admin agent | Global admin

With [Azure Reservations](/azure/cost-management-billing/reservations/save-compute-costs-reservations) and Server Subscriptions (subscriptions to Windows Server and SQL Server), partners in the CSP program can better address the fast-growing customer demand for more cost-effective solutions to support highly predictable and persistent cloud workloads.

You can acquire, provision, and manage Azure Reservations and Server Subscriptions on behalf of commercial customers through Partner Center and the Azure portal by taking advantage of the *[Azure Hybrid Benefit](/windows-server/get-started/azure-hybrid-benefit)*.

The Azure Hybrid Benefit helps you get more value from your Windows Server licenses and save up to 40 percent on virtual machines.

You can use the Azure Hybrid Benefit with *Windows Server Datacenter* and *Windows Server Standard* licenses with Software Assurance. Depending on the edition, you can convert or reuse your licenses to run Windows Server virtual machines in Azure and pay a lower base compute rate (Linux virtual machine rates, for example).

## Markets in which Azure Reservations aren't available

> [!IMPORTANT]
> Azure Reservations are *not* available in the following markets:
>
> |A to Gi   | Gr to Pal  | Pap to Z |
> |--------------------------------|-----------------------------------|------------------------------------------|
> | Aland Islands     | Greenland     | Papua New Guinea     |
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

## Buy software subscriptions on behalf of customers

To purchase software subscriptions on behalf of a customer, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Select a customer from the list.

3. From the customer's detail page, select **Add products**, and then follow the on-screen instructions to create and pay for your order.

   Commercial pricing excludes tax, except for Australia and Brazil.

## View software subscriptions

- Software subscriptions purchased on or after October 14, 2021:
  - Are returned by the *Get Subscriptions* API
  - Appear on the **Subscriptions** page for a customer
  - Appear on  the **Software** page

- Software subscriptions  are returned by the *Get Orders* API, regardless of the date they were purchased.

- Software subscriptions purchased *before* October 14, 2021:
  - Are *not* returned by the *Get Subscriptions* API.
  - Do *not* appear in the **Subscriptions** page

## Activate and manage software subscriptions

After you purchase a software subscription, you or your customer need to download it. (You can also cancel an order within seven days and receive 100% credit).

- [*Customers* use the *Microsoft 365 Admin Center*](#server-subscription-downloads-and-license-keys-are-available-for-customers-through-microsoft-365-admin-center) to see product keys and download information. The *Global admin* role is required.

- *Partners* use *Partner Center* to see product keys and download information. The *Admin agent* role is required to get a link to keys and downloads.

To download software and get software keys and links, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Select a customer from the list.

3. From your customer's detail page, select **Software**.

   A list of all the software you've purchased on behalf of the customer appears.

4. Select the product **Version**, **Language**, and **Bit**, and then select **Get keys and downloads**.

5. Select **Get Key** to display the 32-digit product in a pop-up dialog box that you can copy and send to the customer.

6. Select **Download** to download the software bits.

7. Select **Copy Link** if you want to send the customer a link to the bits download.

> [!IMPORTANT]
> Software keys are valuable and highly sought-after intellectual property, so it's important to understand the risks associated with copying links and downloading software.
For more information, download the [*Partner Center New Commerce Operations Guide*](https://partner.microsoft.com/resources/detail/partner-center-new-commerce-operations-guide-pdf) (sign-in required) and read *Using Partner Center to obtain customer software downloads and license keys*.

> [!NOTE]
> CSP purchases are activated with a multiple activation key (MAK). Key management service (KMS) keys are not allowed, even upon request.

## Move a customer's on-premises license from VL to CSP with no downtime

Even though KMS keys aren't available in CSP, you can still move your customer's on-premises licenses from volume licensing (VL) to CSP and prevent downtime caused by a purchasing channel switch.

KMS distributes licenses to clients, and those licenses usually remain active for 180 days before a device tries to renew the activation. That means a device will be activated and will run for some time before any issues arise.

- If a customer deploys a new multiple activation key (MAK) during the 180 day period, either manually or with a script (using `slmgr.vbs`), there will be no downtime.
- If a customer *doesn't* deploy the new MAK during the 180-day period and tries to renew the license later, the device could become limited or blocked for some functionality until it's reactivated.

   For more information, see [Activate clients running Windows 10 (Windows 10) - Windows Deployment](/windows/deployment/volume-activation/activate-windows-10-clients-vamt#key-management-service-activation-renewal).

   For assistance with this type of deployment, you can submit a [Technical Presales and Deployment services](./technical-benefits.md#submit-technical-presales-and-deployment-services-request) request.

## Server subscription downloads and license keys are available for customers through Microsoft 365 Admin Center

Your customers can get CSP server subscription license keys and downloads from Microsoft 365 Admin Center.

To see their CSP server subscription license keys and downloads, customers must go to **Microsoft 365 Admin Center** > **Billing** > **Your products** > **Software** tab.

## View software key access and software download activity

For auditing or compliance purposes, you may need to check a list of users who have either accessed server subscription software keys or downloaded server subscription software.

> [!NOTE]
> You must be a *Global administrator*, *Account admin*, *Referral admin*, or *Marketing content admin* to see these activity logs.

To check users who have accessed server subscription software keys or downloaded server subscription software, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select the **Settings** (gear) icon.

2. Select **Account settings**, and then select **Activity log**.

3. Enter the date range for the activity you want to see.

   The activity log displays a list of users who have accessed software keys or downloaded software during the time you specified.

## Software subscriptions autorenew by default

*Autorenewal* is intended to simplify software renewal for partners and their customers.

Software subscriptions:

- Autorenew by default if they were purchased on or after October 14, 2021.
- Expire on the date that was indicated at time of purchase if they were purchased before October 14, 2021 (that is, they don't autorenew).

To switch autorenewal on or off, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Select a customer from the list.

3. Select a subscription and then switch **Auto-renew** on or off.

4. Select **Submit**.

## Manage billing frequency

Along with specifying the *duration* of a software subscription, partners can also specify the *billing frequency* of some software subscriptions, splitting large payments into several smaller charges paid over the term of the subscription. Doing so puts more expensive services within the reach of smaller businesses by reducing cash-flow pressure.

As of October 22, 2021:

- Three-year product SKUs are available with annual or triennial (every three years) billing.
- *Windows Remote Desktop Server CAL 2022* is available with monthly billing.

You can see the billing plans that are available on the review screen at Partner Center prior to purchasing.

To set billing frequency, select a billing cycle of *Monthly,* *Annual*, or *Triennial*, depending on customer needs and the billing plans that are available for the software subscriptions you're buying.

## Canceling a software subscription

### Seven-day subscription cancellation window

You can cancel a software subscription within the first seven days of any term and receive a prorated refund (except where otherwise required by law).

Cancellation isn't available after seven days. If you don't cancel a subscription, you're billed for the full term even if the customer stops paying for or using the subscription (applicable to any billing plan).

### Considerations when canceling a software subscription

- You must be an *Admin agent* to cancel a purchase.
- *RedHat* and *SUSE* software plans can't be canceled or exchanged. To learn more, see [Prepay for Azure software plans](/azure/virtual-machines/linux/prepay-suse-software-charges).
- You might be notified of the following information when you attempt to cancel a subscription:
  - The cancellation window end date and time
  - Whether you've already passed the cancellation window and can no longer cancel the subscription
- Before you start the cancellation process, make sure you have the following information:
  - The customer's *name*, *tenant GUID*, or *domain name*
  - The *friendly name or ID* of the software subscription that you want to cancel
- For information about canceling a software subscription using the Partner Center API, see [Cancel software purchases](/partner-center/develop/cancel-software-purchases).

To cancel a software subscription, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.
2. Select a customer from the list.
3. Select the subscription that you want to cancel.
4. In the **Status** section, select **Cancel Subscription**.

   A dialog box appears.

5. Select **Yes, cancel** to acknowledge that you have read the message in the dialog box and to confirm your intent to cancel the software subscription.
6. Select **Submit**.

## Canceling perpetual software

### 30-day perpetual software cancellation window

You can cancel a perpetual software purchase within 30 days of the purchase date and not be charged an early termination fee. You can't cancel a perpetual software purchase after 30 days.

### Considerations when canceling perpetual software

- Before you start the cancellation process, make sure you have the following information:

  - The customer's *name*, *tenant GUID*, or *domain name*
  - The *name of the product you want to cancel*
  - The *order ID*
- The following information might appear when you attempt to cancel a subscription:
  - How many days remain for you to cancel the order
  - Whether you've already passed the cancellation window and can no longer cancel the order

- You might be given a link to a *[Customer support request](#cancel-a-purchase-with-a-customer-support-request)* if we need more information about your cancellation request.

> [!IMPORTANT]
> A message confirming your cancellation appears when you cancel an order. However, *there may be a delay of up to 15 minutes* before the cancellation appears on the Partner Center.

To cancel perpetual software, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Select a customer from the list, then select **Software** to see a list of software purchased for the customer.

3. Locate the software purchase that you want to cancel and select **Cancel**.

   A dialog box appears.

4. From the **Order number** drop-down list, select the order ID number that you want to cancel. (You can learn more about an order or an order ID number from the customer's **Order history** page.)

5. Select the checkbox to acknowledge that you have read the important message concerning cancellation.

6. Select **Submit** to cancel your purchase.

   If you want to cancel multiple orders, perform steps three through five again for each order ID number.

### Post-cancellation details

After you cancel a purchase:

- All related software keys and download links are revoked. This revocation means you and your customer can no longer use the software keys and download links for the canceled purchase.
- You and your customer are responsible for discontinuing the use of all canceled software. You're also responsible for uninstalling the canceled software and removing any related software downloads and links.

- The canceled item will still appear on the customer's software details page, but the activation key won't be available.

- A 100% credit for the canceled order will appear on your next monthly invoice.

### Cancel a purchase with a customer support request

If you tried to cancel a software purchase at Partner Center but were told to provide more information in a customer support request, the following steps might help you:

1. Select the **Customer support request** link from the **Cancel purchase** window.

   The **Report a problem with Partner Center** page opens.

2. Under **Details**, in the **Type of problem** list, select **CSP Purchase/Refund on behalf of customers**.

3. Enter the **Impact** and **Title** information.

4. In **Description**, provide the following information:

    - *Customer tenant GUID* or *domain name*
    - *Order ID* or *Subscription ID*
    - *Refund reason*
    - *Amount requested*

5. In **Contact**, enter your *name*, *email address*, and *phone number*.

6. If you need to attach a file for any reason, select **Add files**. (This step is optional.)

7. When you're finished, select **Submit**.

## Next steps

- [Use Partner Center to sell customers subscriptions to commercial marketplace products](sell-marketplace-products.md)
- [Assigning Azure subscriptions to customers in Partner Center](assign-azure-subscriptions.md)
