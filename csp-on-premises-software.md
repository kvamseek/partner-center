---
title: Sell on-premises software through CSP
ms.topic: how-to
ms.date: 06/30/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Learn how partners in the CSP program can buy, manage, sell, and cancel on-premises software subscriptions on behalf of customers in Partner Center.
author: migolova
ms.author: migolova
---

# Sell on-premises software through the Cloud Solution Provider (CSP) program

**Appropriate roles**: Admin agent | Global admin

As a CSP, you can sell on-premises software through Partner Center in addition to Open, EA, and other programs.

On-premises software in CSP supports a smooth transition to the cloud by introducing on-premises software in a cloud-focused program. And selling on-premises software brings you to every purchase scenario as you provide a single platform to transact all Microsoft products.

This business model makes it easy to procure, manage, and price on-premises software for your customers, allowing you to focus on winning business with an expanded portfolio of IT management value-added solutions.

While ensuring the best overall customer value with on-premises software licensing options, we've also made the business model as partner-friendly as possible. Straightforward licensing of on-premises software in CSP means cost predictability and a streamlined sales process for you.

## Buy software subscriptions on behalf of customers

To purchase software subscriptions on behalf of a customer, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Select a customer from the list.

3. From the customer's detail page, select **Add products**, and then follow the on-screen instructions to create and pay for your order.

> [!NOTE]
> For more information, see this [guide to ordering and fulfillment through Partner Center](https://partner.microsoft.com/resources/detail/guide-to-ordering-and-fulfillment-through-partner-center-pdf).

## Activate and manage software subscriptions

After you purchase a software subscription, you or your customer need to download it. (You can also cancel an order within seven days and receive a pro-rated credit. ).

- *Customers* use the *Microsoft 365 Admin Center* to see product keys and download information. The *Global admin* role is required.

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
> In CSP, we fulfill downgrade rights to the previous versions. Perpetual product licensing rights allow us to downlevel the product as per n-1 or n-2 policy for the majority of the products.

## Move a customer's on-premises license from VL to CSP with no downtime

Even though KMS keys aren't available in CSP, you can still move your customer's on-premises licenses from volume licensing (VL) to CSP and prevent downtime caused by a purchasing channel switch.

KMS distributes licenses to clients, and those licenses usually remain active for 180 days before a device tries to renew the activation. That means a device will be activated and will run for some time before any issues arise.

- If a customer deploys a new multiple activation key (MAK) during the 180 day period, either manually or with a script (using `slmgr.vbs`), there will be no downtime.
- If a customer *doesn't* deploy the new MAK during the 180-day period and tries to renew the license later, the device could become limited or blocked for some functionality until it's reactivated.

   For more information, see [Activate clients running Windows 10 (Windows 10) - Windows Deployment](/windows/deployment/volume-activation/activate-windows-10-clients-vamt#key-management-service-activation-renewal).

   For assistance with this type of deployment, you can submit a [Technical Presales and Deployment services](./technical-benefits.md#submit-technical-presales-and-deployment-services-request) request.

## Cancel a purchase

Use the following procedure to cancel a purchase. Once the cancellation is complete, the software key will be revoked.

### Considerations when canceling a software subscription

- You must be an *Admin agent* to cancel a purchase.
- Before you start the cancellation process, make sure you have the following information:
  - The customer's *name*, *tenant GUID*, or *domain name*
  - *Order ID* or *Subscription ID*
  - Refund reason
  - Amount requested

To cancel a software purchase, use the following steps:

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home) and select **Customers**.

2. Select a customer from the list.

3. On the customer's details page, select **Software**.

   You'll see a list of all the software you've purchased.

4. Locate the software you want to cancel, and select **Cancel**.

   The **Report a problem with Partner Center** page opens.

5. Under **Details**, in the **Type of problem** list, select **CSP Purchase/Refund on behalf of customers**.

6. Fill in the **Impact** and **Title** fields.

7. In the **Description** field, provide the following:
    - The customer tenant GUID or domain name
    - Order ID or Subscription ID
    - Refund reason
    - Amount requested

8. In the **Contact** field, enter your name, email address, and phone number.

9. If you need to attach a file for any reason, select **Add files**. (This step is optional.)

10. When you're finished, select **Submit**.
