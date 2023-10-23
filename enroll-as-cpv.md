---
title: Enroll as a Control Panel Vendor
description: Learn how to enroll as a Control Panel Vendor (CPV) in Partner Center so you can better integrate CSP partner systems with Partner Center APIs.
ms.topic: article
ms.service: partner-dashboard
ms.subservice: partnercenter-enroll
author: sharath-satish-msft
ms.author: shsatish
ms.date: 02/22/2022
---
# Enroll as a Control Panel Vendor to help integrate CSP partner systems with Partner Center APIs

**Appropriate roles**: Global admin

A Control Panel Vendor (CPV) is an independent software vendor who develops applications for use by Cloud Solution Provider (CSP) partners to enable them to integrate their systems with Partner Center APIs.

A Control Panel vendor *isn't* a CSP Partner with direct access to the Partner Center or to Partner Center APIs.

Whether you're a current Control Panel Vendor (CPV) or a new CPV who wants to work with Microsoft partners, Microsoft requires you to enroll in Partner Center to register your applications and support Cloud Solution Provider partners.

To create an account, you can use an existing CSP partner tenant, an existing CPV tenant, or you can create a new tenant as part of the onboarding process. If you choose to use an existing CSP tenant, you must create separate multi-tenant applications and register them in Partner Center for CPV activities.

> [!NOTE]
>An application can't be registered as both a CSP and a CPV application.

After you enroll in Partner Center and register your applications, you get access to the Partner Center APIs.

If you need a sandbox account, contact Microsoft through a Microsoft Support request. (If you already have a sandbox account, you can continue using it. You won't need a new sandbox.)

Review the [Microsoft Control Panel Vendor agreement](https://go.microsoft.com/fwlink/?linkid=2055198)

## Requirements to be a CPV

To become a CPV, you must:

- Have a tenant created in the same country/region as your CPV business. For example, if you want to enroll as a CPV for US-based CSP customers, your tenant must be in the same region. To create a new tenant, [follow these steps](/azure/active-directory/fundamentals/active-directory-access-create-new-tenant).

- Have a PartnerLocationID to associate with the tenant. If you don't have one, you can add one by following the steps at [Manage locations in your partner account](manage-locations.md).

After you fulfill the preceding requirements, follow the steps in [Enroll in the Partner Center CPV program](https://aka.ms/cpv-enroll) to enroll as a CPV.

Business vetting and approval usually take a week or two after you submit an enrollment request.

After your business is vetted and approved, the enrollment state of your application will be **Qualified**. You must sign in at the portal and accept the agreement to change the state of your application to **Active**.

## Working in Partner Center

After you've enrolled as a Partner Center Control Panel Vendor and accepted the CPV agreement, you can:

- Manage multi-tenant applications (that is, add applications to Azure portal, and register and unregister applications in Partner Center).

    > [!NOTE]
    >CPVs must register their applications in Partner Center to get them authorized for Partner Center APIs. Just adding applications to the Azure portal alone does not authorize CPV applications for Partner Center APIs.

- View and manage your CPV profile.

- View and manage your users who need access to CPV capabilities. Global admin is the only role a CPV can have.

## Next steps

- [Add more tenants to your Partner Center account](multi-tenant-account.md)
- Read our previous announcements in [Yammer](https://www.yammer.com/cloudpartnercommunity/#/threads/show?threadId=1186179663) to find out more about requirements.
- Watch the recorded [readiness webinar](https://www.yammer.com/cloudpartnercommunity/#/files/162858123).
- Get help from the Partner Center security guidance [Yammer group](https://www.yammer.com/cloudpartnercommunity/#/threads/inGroup?type=in_group&feedId=15700370&view=all)
