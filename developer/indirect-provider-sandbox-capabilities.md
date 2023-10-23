---
title: CSP Indirect provider capabilities in the Sandbox
description: Indirect providers can create indirect resellers in the Sandbox for test purposes.
ms.date: 6/30/2022
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: JulCsc
ms.author: shishir
---

# CSP Indirect provider sandbox capabilities for creating Indirect reseller accounts 

**Appropriate roles**: Indirect provider

CSP Indirect Providers can create a CSP Indirect Reseller Sandbox account via through their own Tier 2 Sandbox account in Partner Center.


## Prerequisites 

Partner Center Indirect Provider (Tier 2) sandbox credentials. The sandbox scenario supports authentication with both the standalone App and App+User credentials. 
 

## Sandbox Indirect Provider – Create Sandbox Indirect Reseller using the Partner Center user interface 

 This is a Sandbox-only feature that allows Sandbox Indirect Providers the ability to create a Sandbox Indirect Reseller account through the Partner Center.

The following scenarios are what Indirect providers can do for indirect resellers in Sandbox through the Partner Center user interface: 

1. CSP Indirect Providers can create a CSP Indirect Reseller Sandbox account through their own Tier 2 Sandbox account in Partner Center.
2. CSP Indirect Resellers can view customer by Indirect Providers. 

1. CSP Indirect Resellers can manage the customer account using delegated admin permissions.

1. CSP Indirect Providers can invite CSP Indirect Resellers.
 
1. CSP Indirect Providers can delete a CSP Indirect Reseller Sandbox account through their own Tier 2 Sandbox account in Partner Center.

    a.	When Sandbox Indirect Provider deletes the relationship with Sandbox Indirect Reseller, check if the Indirect Reseller has any other relationship with other providers. If so, only the relationship with that specific Indirect provider will be removed.

    c. If that is the only relationship for the Indirect Reseller, then the Indirect Reseller will be deleted.

1. CSP Indirect Providers can delete a CSP Indirect Reseller.

    a. This is a Sandbox-only feature that allows Sandbox Indirect Providers the ability to delete Sandbox Indirect Resellers.
     
1. Prerequisites for deleting a Sandbox Indirect Reseller:

    1. Suspend the subscriptions for each customer of Sandbox Indirect Reseller.

    1. Delete all customers of Indirect Reseller.

1. Limit of five Sandbox Indirect Resellers allowed per Sandbox Indirect Provider. Once the Sandbox Indirect reseller is deleted, the quota will be reset.

### Prerequisites

- Limit of five Sandbox Indirect Resellers allowed per Sandbox Indirect Provider. 

- Same PartnerID can be used to create multiple Indirect Reseller Sandbox accounts if PartnerID country/region and Indirect Reseller Sandbox country/region are same. If you have a test PartnerID available, you can use it, or you can get a list of PartnerIDs through our [Yammer channel]( https://www.yammer.com/cloudpartnercommunity/#/files/929991598080 ). If you don’t have access to Yammer, Yammer will ask you to request access.
 
- Only 75 customers are allowed per Sandbox Indirect Provider

## Create CSP Indirect Reseller Sandbox account

1. Sign into Partner Center via your Tier 2 Sandbox account. 

2. Navigate to Indirect Resellers from the left menu. 

3. Select the **Add Reseller Sandbox** button. 

4. Fill the account enrollment form. It's self-explanatory but remember you are creating a Sandbox account for an Indirect Reseller. 
This account won't undergo vetting and will be activated as soon as you finish the account enrollment.  

5. Once the account is created, you will get the Global Admin credentials for the Indirect Reseller sandbox account on the portal. Remember to save it immediately,  otherwise, you won't be able to sign in as an Indirect Reseller Sandbox. 

6. Sign out and sign in again to Partner Center using the new credentials for Indirect Reseller Sandbox. Explore the capabilities you can do as an Indirect Reseller. Some things are:  

    - Manage profiles  

    - Manage users and roles 

    - Manage Indirect Providers 

    - Manage CSP Sandbox customers 

    - Manage relationships
    
     
## Sandbox Indirect Provider – Delete Sandbox Indirect Reseller using the Partner Center user interface

 This is a Sandbox only feature that allows Sandbox Indirect Providers an ability to delete an existing Sandbox Indirect Reseller account via Partner Center. 

### Prerequisites to delete sandbox Indirect reseller:

An existing CSP Indirect Reseller Sandbox account associated with your own CSP Indirect Provider Tier-2 Sandbox account.  
 

## Delete CSP Indirect Reseller Sandbox account

1. Sign into Partner Center using your Tier 2 Sandbox account. 

2. Navigate to Indirect Resellers from the left menu. 

3. Select the **Delete Reseller Sandbox** link next to the Indirect Reseller Sandbox account you want to delete. The Indirect Reseller Sandbox account will be permanently deleted and cannot be recovered. 

## API references

- [Create Indirect Reseller](create-indirect-reseller-in-sandbox.md)
- [Delete Indirect Reseller](delete-indirect-reseller-in-sandbox.md)
